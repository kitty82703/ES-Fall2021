# Lab 4-1 用七段顯示器來顯示數字"8"

## 電路圖
![image](https://user-images.githubusercontent.com/89329256/137610662-a06aa6c5-bcdc-437d-99e0-d70e03e7ff15.png)


## 程式碼
````C
void setup()
{
for(int x = 1; x < 9; x++) {
pinMode(x,OUTPUT);
}
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
digitalWrite(1, a);
digitalWrite(2, b);
digitalWrite(3, c);
digitalWrite(4, d);
digitalWrite(5, e);
digitalWrite(6, f);
digitalWrite(7, g);
digitalWrite(8, h);
delay(500);
}

void loop()
{
//    a, b, c, d, e, f, g, h
seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
}
````
# Lab 4-2 如下圖的Demo, 用七段顯示器, 顯示 . →1→ ... → 9 → 0 → 全滅, 狀態改變的間隔時間為0.5秒

## 電路圖

![20211017_122521](https://user-images.githubusercontent.com/89329256/137611326-6d0ac231-c0f3-4516-aecc-a9f19b8e5038.gif)

## 程式碼
````C
void setup()
{
for(int x = 1; x < 9; x++) {
pinMode(x,OUTPUT);
}
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
digitalWrite(1, a);
digitalWrite(2, b);
digitalWrite(3, c);
digitalWrite(4, d);
digitalWrite(5, e);
digitalWrite(6, f);
digitalWrite(7, g);
digitalWrite(8, h);
delay(500);
}

void loop()
{
//    a, b, c, d, e, f, g, h
seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
seg71(0, 1, 1, 0, 0, 0, 0, 1); // 1
seg71(1, 1, 0, 1, 1, 0, 1, 1); // 2
seg71(1, 1, 1, 1, 0, 0, 1, 1); // 3 
seg71(0, 1, 1, 0, 0, 1, 1, 1); // 4
seg71(1, 0, 1, 1, 0, 1, 1, 1); // 5
seg71(1, 0, 1, 1, 1, 1, 1, 1); // 6
seg71(1, 1, 1, 0, 0, 0, 0, 1); // 7
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
seg71(1, 1, 1, 1, 0, 1, 1, 1); // 9
seg71(1, 1, 1, 1, 1, 1, 0, 1); // 0
}

````
# Lab 4-3 LCD顯示"Hello" + 你的英文名字 (e.g., "Hello Horace")

## 電路圖

![image](https://user-images.githubusercontent.com/89329256/138583270-0785d6a2-3726-441e-8c0a-ef52b6a4ff59.png)

## 程式碼

````C
// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("hello, Iris!");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  // print the number of seconds since reset:
  lcd.print(millis() / 1000);
}
````
# Lab 4-4 整合超音波感測器 + LCD: 參考之前的實作, 完成以下任務:
1. **將超音波感測器傳回的距離, 在LCD上面顯示,** 
2. **同時也和之前的實作一樣, 在序列輸出.** 
3. **另外, 當物體的距離小於150cm時, 則亮紅色LED, 否則亮綠色LED**

## 電路圖

![image](https://user-images.githubusercontent.com/89329256/138586172-c7ab1c88-c330-44d4-80a1-f006fbf18c7d.png)

## 程式碼

````C
#include <LiquidCrystal.h>

#define echo 7
#define trig 7
  
float  duration; // time taken by the pulse to return back
float  dd; // oneway distance travelled by the pulse
int RLED = 9;
int GLED = 8;

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  digitalWrite(RLED, OUTPUT);
  digitalWrite(GLED, OUTPUT);
  lcd.begin(16, 2);
}

void loop() {
  time_Measurement();
  dd = duration * 0.01723;   
  lcd.setCursor(0, 0);
  lcd.print("Distance, cm: ");
  lcd.setCursor(0, 1);
  lcd.print(dd);
  
    if (dd < 150) {
    digitalWrite(RLED, HIGH);
    digitalWrite(GLED, LOW);
  } else {
    digitalWrite(RLED, LOW);
    digitalWrite(GLED, HIGH);
  }
}
  
void time_Measurement()
{ //function to measure the time taken by the pulse to return back
    pinMode(trig, OUTPUT);
    digitalWrite(trig, LOW);
    delayMicroseconds(2);  
    digitalWrite(trig, HIGH);
    delayMicroseconds(10);
    digitalWrite(trig, LOW);
    pinMode(echo, INPUT);  
    duration = pulseIn(echo, HIGH);
}
````
