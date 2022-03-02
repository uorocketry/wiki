> WARNING: The RPi to Arduino functionality is mostly complete for now. However, the implementation is fairly different from what is described here. This document needs to be updated to reflect the current implementation.


<!-- vim-markdown-toc GFM -->

* [Overview](#overview)
	* [Goals](#goals)
* [Communication](#communication)
	* [Communication Stack](#communication-stack)
	* [Protobuf Messages](#protobuf-messages)
		* [ArduinoIn](#arduinoin)
			* [Ping](#ping)
			* [Servo](#servo)
			* [Digital](#digital)
			* [Reset](#reset)
			* [PingFailsafeReset](#pingfailsafereset)
		* [ArduinoOut](#arduinoout)
			* [Acknowledgement](#acknowledgement)
			* [Error](#error)
			* [ArduinoInfo](#arduinoinfo)
			* [ResetEvent](#resetevent)
	* [Example Communication](#example-communication)
		* [Servo and Pin Control](#servo-and-pin-control)
		* [Unexpected Arduino Reset](#unexpected-arduino-reset)

<!-- vim-markdown-toc -->

# Overview

Due to limitations to the RPi GPIO, it has been decided to use an Arduino (here called Arduino proxy) for general pin input/output operations. However, having a flexible and reliable communication between the two devices is not quite trivial. This document gives an overview of how the RPi and Arduino communicate together.

## Goals
Here are the following main goals of the RPi-Arduino communication and the Arduino proxy itself:
- Reliable: Possible to detect if a message has been transmitted successfully.
- Flexible: Possible to control extra pins without flashing again the Arduino.
- Safe: Checks should be put in place to assure the correct command is executed. Moreover, the Arduino should go in a safe configuration if the RPi becomes unresponsive.
- Verbose: The RPi should know as much as possible about what is happening on the Arduino. For example, if the Arduino encounters an error, it should tell the RPi about it.

# Communication

## Communication Stack

The communication stack consists of a few components all working together to reliably send messages between the two devices.

First, we use serial for the physical link.

Second, we need an actual format to send the messages across. For simplicity and flexibility purposes, [Protocol Buffers](https://developers.google.com/protocol-buffers) is used.

Next, we need to have a way to detect errors that would be happening during the transmission. While serial does offer some basic checks with a parity bit, it could be good to have a bit more error checking. Adding a small 16 bit [CRC](https://en.wikipedia.org/wiki/Cyclic_redundancy_check) should be enough for detecting most common errors in the transmission.

Finally, because serial only send streams of bytes, we need to be able to combine those bytes into packets. For this, we use [COBS](https://en.wikipedia.org/wiki/Consistent_Overhead_Byte_Stuffing) to provide packet framing. This allows to use the 0x0 byte to separate each of the packets.

All together, here is how the communication stack looks:
![](images/Arduino_Comm_Stack.png)

Or, another way to look at it:
![](images/Arduino_Comm_Stack_2.png)

## Protobuf Messages

Please look at the repo for the latest Protobuf definitions. This section will simply go over the major aspects of the messages.

### ArduinoIn

The `ArduinoIn` message encapsulates any messages sent from the RPi to the Arduino. It consists of two fields:
  - `messageId`: A randomly generated id which will allow the Arduino to send a confirmation back to the RPi to confirm the message has been received. Also allows the Arduino to ignore message it already received..
  - `data`: A `oneof` field containing the actual message to be sent across. It could be a ping, a command to set a servo to a certain value, etc.

The Arduino will sent an acknowledgement message for every message it receives. While this may not be strictly needed for all messages (say a ping), it simplifies the whole protocol.

#### Ping
The RPi sends a ping message every second to the Arduino. 

If the Arduino doesn't receive a ping for 10 seconds, it will fall back to a safe configuration. When that happens, the `pingFailsafeTriggered` flag will be set in the `ArduinoInfo` message.

#### Servo
The RPi needs to first send a `ServoInit` message to the Arduino. This will initialize the servos and also contains the safe value to fallback to. `ServoControl` messages are used to control the initialized servo.

#### Digital
The RPi needs to first send a `DigitalInit` message to the Arduino. This will initialize the digital pin and also contains the safe value to fallback to. `DigitalControl` messages are used to control the initialized digital pins.

#### Reset
The RPi is able to reset the Arduino by sending a `Reset` message. This message is sent anytime the rocket-code starts, and allows to make sure the Arduino is in a clear state before proceeding. Once the reset is done, the Arduino will send a `ResetEvent` message to indicate it is now ready to be initialized.


#### PingFailsafeReset
A `PingFailsafeReset` can be set to reset the `pingFailsafeTriggered` flag in case it ever gets triggered.

### ArduinoOut

The `ArduinoOut` message encapsulates any messages sent from the Arduino to the RPi. It only consist of one field:
  - `data`: A `oneof` field containing the actual message to be sent across.

#### Acknowledgement
The `ACK` message is sent for every message the Arduino receives. It only data it contains is the `messageId` of the received message. 

#### Error
The `Error` message is sent anytime the Arduino encounters a unexpected situation. It consists of the error message, along with the error level (WARNING, FATAL).

#### ArduinoInfo
The `ArduinoInfo` message is sent every 5 seconds to the RPi. The message contains:
  - `sessionId`: This id should be randomly generated every time the Arduino starts (i.e. generated in the `setup()`).
  - `pingFailsafeTriggered`: Set if the ping failsafe has been triggered. Can be reset by sending a `PingFailsafeReset` command.

The intended use of this message is to allow the RPi to detect if the Arduino did an unexpected reset. If so, the RPi will be able to reinitialize the appropriate pins on the Arduino.

#### ResetEvent
The `ResetEvent` message is sent right at the end of the `setup()` function of the Arduino. It contains the current `sessionId`. This allows the RPi to know that the Arduino is in a fresh state and able to be initialized.

## Example Communication

### Servo and Pin Control
Here is an example of the intended communication flow between the RPi and the Arduino to setup a servo and digital pin:
  1. rocket-code is started.
  2. A `Reset` message is sent to the Arduino.
  3. Once the reset is done, the Arduino sends a `ResetEvent` to the RPi.
  4. When the RPi receives the `ResetEvent`, it will send a `ServoInit` message and a `DigitalInit` message.
  5. Anytime the RPi needs to control the servo, send a `ServoControl` message.
  6. Anytime the RPi needs to control the pin, send a `DigitalControl` message.

### Unexpected Arduino Reset
Here is now an example of an unexpected Arduino reset:
  1. All the steps of [Servo and Pin Control](#Servo_and_Pin_Control) are followed.
  1. The RPi saved the `sessionId` when it received the `ResetEvent` in step 1.
  2. For some reason, the Arduino (but not the RPi) resets.
  3. Again, for some reason, the RPi doesn't receive the `ResetEvent` message.
  4. When the Arduino sends the next `ArduinoInfo` message, the RPi detects that the `sessionId` doesn't match.
  5. RPi send a `Reset` message.
  6. When the RPi receives the `ResetEvent`, it stores the new `sessionId`.
  7. The `ServoInit` and `DigitalInit` messages are sent again.
