---
title: Data Format for 2020 October-Sky Launch
description: 
published: true
date: 2022-03-02T22:46:12.776Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:32:39.718Z
---

# Data format for the radio
* (Boolean)islogging 
* (uint64_t)timeStamp; 
* (float)Xangle; 
* (float)Yangle; 
* (float)Zangle; 
* (float)XangleAcc; 
* (float)YangleAcc; 
* (float)ZangleAcc; 
* (double)gpsLatitude; 
* (double)gpsLongitude; 
* (double)gpsAltitude; 
* (float)barometricAltitude; 
* (float)velocityN; 
* (float)velocityE; 
* (float)velocityD; 
* (float)filteredXacc; 
* (float)filteredYacc; 
* (float)filteredZacc; 
* (int)solutionStatus; 
* (uint16_t)currentStateNo; 
\r\n 

***

# Data format for the Raspberry Pi
* timeStamp
* currentState.sbg.roll
* currentState.sbg.pitch
* currentState.sbg.yaw
* currentState.sbg.rollAccuracy
* currentState.sbg.pitchAccuracy
* currentState.sbg.yawAccuracy
* currentState.sbg.gpsLatitude
* currentState.sbg.gpsLongitude
* currentState.sbg.gpsAltitude
* currentState.sbg.barometricAltitude
* currentState.sbg.relativeBarometricAltitude
* currentState.sbg.velocityN
* currentState.sbg.velocityE
* currentState.sbg.velocityD
* currentState.sbg.filteredXaccelerometer
* currentState.sbg.filteredYaccelerometer
* currentState.sbg.filteredZaccelerometer
* currentState.sbg.solutionStatus
* currentState.currentStateNo
* currentState.sbg.gpsPosStatus
* currentState.sbg.gpsPosAccuracyLatitude
* currentState.sbg.gpsPosAccuracyLongitude
* currentState.sbg.gpsPosAccuracyAltitude
* currentState.sbg.NumSvUsed (we logged this as a raw byte in the file. It needs to be post processed to convert it into ascii)
* currentState.sbg.velocityNAccuracy
* currentState.sbg.velocityEAccuracy
* currentState.sbg.velocityDAccuracy
* currentState.sbg.latitudeAccuracy
* currentState.sbg.longitudeAccuracy
* currentState.sbg.altitudeAccuracy
* currentState.sbg.pressureStatus
* currentState.sbg.barometricPressure
* currentState.sbg.imuStatus
* currentState.sbg.gyroX
* currentState.sbg.gyroY
* currentState.sbg.gyroZ
* currentState.sbg.temp
* currentState.sbg.deltaVelX
* currentState.sbg.deltaVelY
* currentState.sbg.deltaVelZ
* currentState.sbg.deltaAngleX
* currentState.sbg.deltaAngleY
* currentState.sbg.deltaAngleZ
\n