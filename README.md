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

# Serial port API
* OpenSerial 
* WriteSerialByte 
* ReadSerial 
* ReadSerialString 
* WriteThenRead 
* ResetParam 
* CloseSerial 
* clearPortBuf 

* * *
### OpenSerial
| Function prototype | void OpenSerial(String dev, int brd) throws SecurityException，IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Open serial port: data bit, 8bit; stop bit, 1; no parity bit; |
| Parameter Description  | String dev,Serial port number; |
| Parameter Description  | int brd,Baud rate; |
| Return value | None |

### OpenSerial
| Function prototype | void OpenSerial(String device, int baudrate, int databit,int stopbit, int crc) throws SecurityException, IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Open serial port: data bit, 8bit; stop bit, 1; parity bit; |
| Parameter Description  | String dev,Serial port number; |
| Parameter Description  | int brd,Baud rate; |
| Parameter Description  | int databit; |
| Parameter Description  | int stopbit; |
| Parameter Description  | int crc; |
| Return value | None |
* * *
### Get file handle
| Function prototype | public int getFd() |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Get the file handle, after opening the serial port successfully |
| Return value | int,Open the file handle of the serial port; |
* * *
### ReadSerial
| Function prototype | byte[] ReadSerial(int fd, int len, int delay) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Read the data returned by the serial port; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | int len, Read maximum length; |
| Parameter Description  | 	int delay, Maximum blocking delay; |
| Return value | byte[] Serial data |
### ReadSerial
| Function prototype | byte[] ReadSerial(int fd, int len) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Read the data returned by the serial port; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | int len, Read maximum length; |
| Return value | byte[] Serial data |
* * *
### ReadSerialString
| Function prototype | String [] ReadSerial(int fd, int len, int delay) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Read the serial port data, return String, the encoding format is utf8/gbk; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | int len, Read maximum length; |
| Return value | String Serial data |
* * *
### WriteThenRead 
| Function prototype | byte[] writeThenRead(int fd, byte[] buf, int count, int delay, int brd, int bit, int stop, int crc) throws SecurityException, IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Read/write serial port at the same time, it is not recommended; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | int len, Read maximum length; |
| Parameter Description  | 	int delay, Maximum blocking delay; |
| Return value | byte[] Serial data |
### WriteThenRead 
| Function prototype | byte[] writeThenRead(int fd, byte[] buf, int count, int delay, int brd, int bit, int stop, int crc) throws SecurityException, IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Read/write serial port at the same time, it is not recommended; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | int len, Read maximum length; |
| Parameter Description  | 	int delay, Maximum blocking delay; |
| Return value | byte[] Serial data |
* * *
### ReadSerial
| Function prototype | int WriteSerialByte(int fd, byte[] str) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Write data through the serial port; |
| Parameter Description  | int fd, Serial port handle; |
| Parameter Description  | byte[] str,Data to be written; |
| Return value | int, return status >=0|
* * *
### ResetParam
| Function prototype | void resetParam(int fd, int baudrate, int databit,int stopbit, int crc) throws SecurityException, IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Reset serial port parameters; |
| Parameter Description  | int fd, File handle; |
| Parameter Description  | int baudrate, Baud rate; |
| Parameter Description  | int databit; |
| Parameter Description  | int stopbit; |
| Parameter Description  | int crc; |
| Return value | None |
### ResetParam(Baud rate)
| Function prototype | void resetParam(int fd, int baudrate) throws SecurityException, IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Reset serial port parameters; |
| Parameter Description  | int fd, File handle; |
| Parameter Description  | int baudrate, Baud rate; |
| Return value | None |
* * *
### ClearPortBuf
| Function prototype | void clearPortBuf(int fd) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | clear cache; |
| Parameter Description  | int fd, Serial port handle; |
| Return value | None |
* * *
### CloseSerial
| Function prototype | void CloseSerial(int fd) |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Close the serial port fd; |
| Parameter Description  | int fd, Serial port handle; |
| Return value | None |
* * *

# DeviceControl(GPIO) API
* Constructor
* Power-on
* Set gpio
* Power off

* * *
### DeviceControl.PowerType
| Type | Description |
| :----------------: |:-------------------------------------------------------------------------:|
| MAIN | Motherboard control(KT40/KT50/KT55/KT80); |
| EXPAND | Back clip control(EM55); |
| MAIN_AND_EXPAND | Motherboard & Back Clip Control（KT55+EM55); |
| NEW_MAIN | Motherboard control(SD55/SD60/SD80/SD100); |
| EXPAND2 | Back clip control(SK80) |
| MAIN_AND_EXPAND2 | Motherboard & Back Clip Control（SK80) |
| GAOTONG_MAIN | Qualcomm |
* * *
### Constructor
| Function prototype | DeviceControl(PowerType power_type, int… gpios) throws IOException |
| :----------------: |:-------------------------------------------------------------------------:|
| Functional description | Device power-on control; |
| Parameter Description  | PowerType power_type,Select the type of device; |
| Parameter Description  | int… gpios,The motherboard parameters are in front and the back clip parameters are in the back; |
| Return value | DeviceControl; |
### Constructor(Qualcomm)
* * *
* Code example
```Motherboard(KT) opens multiple GPIOs;
  {
        try {
                DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.MAIN, 93, 94);
                deviceControl.PowerOnDevice();
                deviceControl.PowerOffDevice();
            } catch (IOException e) {
            e.printStackTrace();
            }
  }
```
* * *
```Mtherboard(SD) opens multiple GPIOs;
  {
        try {
                DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.NEW_MAIN, 16, 46);
                deviceControl.PowerOnDevice();
                deviceControl.PowerOffDevice();
            } catch (IOException e) {
            e.printStackTrace();
            }
  }
```
* * *
```Back clip(EM55) opens multiple GPIOs;
  {
        try {
                DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.EXPAND, 1, 2, 3);
                deviceControl.PowerOnDevice();
                deviceControl.PowerOffDevice();
            } catch (IOException e) {
            e.printStackTrace();
            }
  }
```
* * *
```Back clip(SK80) opens multiple GPIOs;
  {
        try {
                DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.EXPAND2, 1, 2, 3);
                deviceControl.PowerOnDevice();
                deviceControl.PowerOffDevice();
            } catch (IOException e) {
            e.printStackTrace();
            }
  }
```
* * *
```Motherboard & Back Clip(KT55+EM55) Open Multiple GPIOs;"93" is the main board, and "1, 2, 3" is the back clip;
  {
   try {
            DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.MAIN_AND_EXPAND, 93, 1,2,3);
            deviceControl.PowerOnDevice();
            deviceControl.PowerOffDevice();
        } catch (IOException e) {
            e.printStackTrace();
        }
  }
```
* * *
```Motherboard & Back Clip(SK80) Open Multiple GPIOs;"93" is the main board, and "1, 2, 3" is the back clip;
  {
   try {
            DeviceControl deviceControl = new DeviceControl(DeviceControl.PowerType.MAIN_AND_EXPAND2, 93, 1,2,3);
            deviceControl.PowerOnDevice();
            deviceControl.PowerOffDevice();
        } catch (IOException e) {
            e.printStackTrace();
        }
  }
```


