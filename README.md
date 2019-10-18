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
	> OpenSerial 打开串口
	> WriteSerialByte 写入数据
	> ReadSerial 读取数据
	> ReadSerialString 读取数据（字符串）
	> writeThenRead 读写串口
	> resetParam 重设参数
	> CloseSerial 关闭串口
	> clearPortBuf 清除缓存
