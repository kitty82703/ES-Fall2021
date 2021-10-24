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

https://user-images.githubusercontent.com/89329256/138587998-cddff49f-d28d-41ac-9afc-2890d640f173.mp4

## 程式碼

````C
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
int RLED = 9;
int GLED = 8;

void setup() 
{
  lcd.begin(16, 2);
  Serial.begin(9600);	
  pinMode(A1, INPUT); // Read analog voltage level (2^10)

}

void loop() 
{
  int reading = analogRead(A1);  // read analog level level (2^10)
  lcd.setCursor(0,0);  
  lcd.print("TMP Sensor Demo");

  float voltage = (reading/1024.0) * 5.0;
  float tempC = (voltage - 0.5) * 100.0;
  if(tempC<38)
  {
    digitalWrite(RLED, LOW);
    digitalWrite(GLED, HIGH); 
  }
  else
    {
      digitalWrite(RLED, HIGH);
      digitalWrite(GLED, LOW);
    }
  lcd.setCursor(0,1);
  lcd.print("Tmp:");
  lcd.print(tempC);
  lcd.print(" C");
  delay(500);
  lcd.clear();
  Serial.println(reading);
  Serial.println(voltage);  
}
````

