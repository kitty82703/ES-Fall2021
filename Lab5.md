# Lab 5-1 請使用兩個伺服馬達同步從 0 度逐步掃描到 180 度之後再逐步掃描回0度, 每步的間隔時間為50ms (0.05秒)

## 電路圖

![image](https://user-images.githubusercontent.com/89329256/138587207-61bfea63-f23e-43fd-8641-8304a9099ff1.png)

## 程式碼

````C
#include <Servo.h>

int pos = 0;

Servo servo_9;
Servo servo_8;
void setup()
{
  servo_9.attach(9, 500, 2500);
  servo_8.attach(8, 500, 2500);  
}

void loop()
{
// 從 0 到 180 度逐步掃描伺服, 1度/步
  for (pos = 0; pos <= 180; pos += 1) {

    servo_9.write(pos);
    servo_8.write(pos);       

    delay(50); // 等50ms (0.05秒)
  }
  
  for (pos = 180; pos >= 0; pos -= 1) {
// 從 180 到 0 度逐步掃描伺服, 1度/步
    servo_9.write(pos);
    servo_8.write(pos);        

    delay(50); // 等50ms (0.05秒)
  }
}
````
# Lab 5-2 LCD顯示溫度感應器的溫度;若溫度<38 綠LED亮; 若大於38度, 紅色LED亮

## 電路圖



## 程式碼
