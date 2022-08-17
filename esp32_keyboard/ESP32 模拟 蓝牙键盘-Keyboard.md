# ESP32 模拟 蓝牙键盘-Keyboard

## 1.简介

现在乐鑫已经推出了 ESP32-S3，此款芯片支持了USB模拟功能，再加上它的蓝牙键盘模拟功能，我们很容易只做一款蓝牙+USB+WIFI的客制化键盘

## 2.硬件平台

安信可 **NODEMCU-32S** 开发板：

![](\esp32_keyboard\img\p1.jpg)

## 3.软件平台

**Arduino (1.8.10)**   或   **VScode** 环境下 **PlatformIO** 插件

## 4.库文件

### 4.1 ESP32_BLE_Arduino

ESP蓝牙驱动库，地址：[GitHub - nkolban/ESP32_BLE_Arduino: The library source for the ESP32 BLE support for Arduino.](https://github.com/nkolban/ESP32_BLE_Arduino)

### 4.2 ESP32-BLE-Keyboard

ESP32键盘模拟库，依赖于ESP32_BLE_Arduino这个库，地址：[GitHub - T-vK/ESP32-BLE-Keyboard: Bluetooth LE Keyboard library for the ESP32 (Arduino IDE compatible)](https://github.com/T-vK/ESP32-BLE-Keyboard)

## 5.示例程序

```c++
/**
 * 时间：2020/5/18
 * 作者：刘泽文
 * 功能：使用ESP32的蓝牙功能模拟蓝牙键盘
 */
#include <BleKeyboard.h>
#include <WiFi.h>
 
BleKeyboard bleKeyboard("ESP32蓝牙键盘","Espressif",100);//其中“ESP32蓝牙键盘”为键盘名称；"Espressif"为制造商
 
void setup() {
  Serial.begin(115200);
  Serial.println("Starting BLE work!");
  bleKeyboard.begin();
}
 
void loop() {
  if(bleKeyboard.isConnected()) {
    //多媒体测试
    Serial.println("Sending Play/Pause media key...");
    bleKeyboard.write(KEY_MEDIA_PLAY_PAUSE);
 
    delay(1000);
 
    //Ctrl+Alt+Delete任务管理器，并进行锁屏操作
    Serial.println("Sending Ctrl+Alt+Delete...");
    bleKeyboard.press(KEY_LEFT_CTRL);
    bleKeyboard.press(KEY_LEFT_ALT);
    bleKeyboard.press(KEY_DELETE);
    delay(100);
    bleKeyboard.releaseAll();
 
    //输入密码并开机
    Serial.println("下面填入你的开机密码↓");
    bleKeyboard.print("--你的开机密码，注意大小写--");
    delay(100);
    Serial.println("Enter");
    bleKeyboard.write(KEY_RETURN);
  }
  Serial.println("Waiting 5 seconds...");
  delay(5000);
}
```

## 6.配对&测试

给你的ESP32开发板插上电，打开你的笔记本电脑->打开蓝牙->添加蓝牙或设备->鼠标、键盘类，你将会看到名为“ESP32蓝牙键盘”的设备，点击即可连接。然后打开你电脑上的音乐软件播放歌曲。

接下来，你的笔记本将会一直重复 停止播放音乐+锁屏+解锁+开始播放音乐 的操作~，如果想停下，请直接关闭笔记本的蓝牙，或拔掉开发板。

## 7.提升部分

使用旋转编码器控制电脑、手机、平板的音量

![](\esp32_keyboard\img\p2.jpg)

```c++
#include <ESP32Encoder.h>
#include <BleKeyboard.h>
#include <Wire.h>
 
//按键配置
#define EC11_A_PIN 13
#define EC11_B_PIN 14
#define EC11_K_PIN 27
 
BleKeyboard bleKeyboard;
ESP32Encoder encoder;
 
void setup()
{
  Serial.begin(115200);
 
  ESP32Encoder::useInternalWeakPullResistors = UP;
  encoder.attachSingleEdge(EC11_A_PIN, EC11_B_PIN);
 
  bleKeyboard.begin();
 
  pinMode(EC11_K_PIN, INPUT_PULLUP);
}
 
int lastEncoderValue = 0;
void loop()
{
  if (lastEncoderValue != encoder.getCount())
  {
    int now_count = encoder.getCount();
    if (bleKeyboard.isConnected())
    {
      if (now_count > lastEncoderValue)
      {
        bleKeyboard.write(KEY_MEDIA_VOLUME_DOWN);
      }
      else
      {
        bleKeyboard.write(KEY_MEDIA_VOLUME_UP);
      }
    }
    lastEncoderValue = now_count;
    Serial.print("Encoder value: ");
    Serial.println(lastEncoderValue);
  }
 
  if (digitalRead(EC11_K_PIN) == LOW)
  {
    delay(5);
    if (digitalRead(EC11_K_PIN) == LOW)
    {
      if (bleKeyboard.isConnected())
      {
        bleKeyboard.write(KEY_MEDIA_PLAY_PAUSE);
      }
    }
    while (digitalRead(EC11_K_PIN) == LOW)
      ;
  }
}
```

*注意：*ESP32_BLE_Arduino库在0.4.7及以上时会报错，把这个库回滚到0.4.1就好了