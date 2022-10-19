---
title: Communication
description: 
published: true
date: 2022-10-19T00:59:36.097Z
tags: 
editor: markdown
dateCreated: 2022-10-18T23:51:41.612Z
---

> This is a work in progress

# Overview
Hydra nodes communicate over CAN FD. Any messages are broadcasted over to all nodes in the CAN network, requiring filtering to be done on each node. 

CAN FD is pretty low-level, similar to Ethernet. For any useful communication to happen, some form of protocol must be agreed upon and used by all nodes. CAN FD allows a payload of up to 64 bytes. For Hydra, these are the rough goals of this protocol:
- Allocate unique IDs to each node
- Send sensor data
- Send node status/health
- Send reliable commands between nodes

# ID Allocation
CAN FD allows the choice of an 11-bit identifier or an 29-bit identifier. This identifier must be unique through the CAN network, else collisions can happen.

The ID also doubles as the message priority, with a lower ID representing a higher priority. If two nodes try to send at the same time, the one with the highest ID will back off and allow the other node to send its message.

This ID can also be used to identify the payload type. For Hydra, this will not be done to simplify the payload parsing.

> Should the ID always uniquely identify a specific node? Say, the themperature of the engine is always assigned ID 20, even if we change the board?

# Serialization Format

## Intro
CAN FD allows a payload of up to 64 bytes. To simplify the system, a serialization formation will be used. This will allow to easily convert from some data structure to the CAN payload and vice versa.

Due to the limitations of an embedded system, not many serialization format can be used. The best option seems to be Protocol Buffers with the `nanopb` library. This format can also easily be used across languages. Message formats can also easily be made backward and forward compatible.

<!--
It is worthwhile mentioning that there are two ways to go about the serialization format. One possibility is to have a different message format for every node, and to use the CAN ID to figure out how to parse the message. Another possibility is to have all the nodes use the same message format -->

## Message Format

### Global Message
This is the global message that will wrap all communication. The basic fields found in all message are:
- `source`: ID of the sender
- `destination`: ID of the destination. 0 will be used for broadcast.

```protobuf
message HydraMessage {
  ID source = 1;
  ID destination = 2;
  oneof payload {
    PubSub pubsub = 3;
    Command command = 4;
    CommandAck commandAck = 5;
  }
}
```

### IDs

> Should the ID used in messages be the same for the ID used in the CAN message?

```protobuf
enum ID {
  Broadcast = 0;
  FillCart = 1;
  GroundStation = 2;
  MainValve = 30;
  EngineTemperature = 64;
  ...
}
```

IDs are going to be used to identify the sending and destination nodes. The special ID 0 is used for broadcast.

Using a Protobuf enum allows IDs to easily be shared among any systems that interacts with Hydra.

### PubSub

> How specific should pubsub messages be? e.g.  pressure could have it's `PressureData` message, or just use a generic `ADCData` or `FloatData` message.

```protobuf
message PubSub {
  oneof type {
    PubSubStatus status = 1;
    PubSubSensor sensor = 2;
  }
}

message PubSubStatus {
  bool hasError = 1;
  bool isInitialized = 2;
  oneof message {
    MainStatus main = 3;
    TemperatureStatus temperature = 4;
    ServoStatus servo = 5;
  }
}

message PubSubSensor {
  oneof message {
    TemperatureData temperature = 1;
    PresureData pressure = 2;
  }
}
```

### Command

```protobuf
message Command {
  uint32 id = 1;
  oneof type {
    ShortCommand shortcommand = 2;
    LongCommand longCommand = 3;
  }
}

message ShortCommand {
  oneof comand { StateMachineCommand stateMachine = 1; }
}

message LongCommand {
  oneof command {
    ServoValveCommand servoValve = 1;
    DCValveCommand dcValve = 2;
  }
}

message CommandAck {
  uint32 id = 1;
  bool finalACk = 2;
}
```

- `finalACk`: Should always be set to `true` for a `ShortCommand`. For a `LongCommand`, set to `false` to acknowledge command reception. Set to `true` for acknowledge command completion.


