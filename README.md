# SpeedataPortHelper Instructions

## This source code is suitable for KT series (android 5.1/6.0) & SD series (6.0/8.1)

# How to quote your own Android project?

## Android Studio

### Add the following to the project's build.gradle
```
	allprojects {
        repositories {
            ...
            maven { url 'https://jitpack.io' }
        }
    }
```

### Add the following in the build:gradle of Module:app
```
    dependencies {
        implementation 'com.github.SpeedataG:Device:1.6.8'
    }
```

# API
* OpenSerial 
* WriteSerialByte 
* ReadSerial 
* ReadSerialString 
* writeThenRead 
* resetParam 
* CloseSerial 
* clearPortBuf 

* * *
### OpenSerial
| FUNCTION PROTOTYPE | void OpenSerial(String dev, int brd) throws SecurityException，IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| FUNCTION PROTOTYPE | void OpenSerial(String dev, int brd) throws SecurityException，IOException |
| FUNCTION PROTOTYPE DESCRIPTION | Open serial port: data bit, 8bit; stop bit, 1; no parity bit; |
| PARAMETER DESCRIPTION | String dev,Serial port number; |
