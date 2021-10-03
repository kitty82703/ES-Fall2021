# 會呼吸的RGB LED,  按鍵控制, 狀態輸出 

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (2021-09-05)
![image](https://user-images.githubusercontent.com/89329256/132114191-d47c63cb-a07b-41d8-a6be-8d4cd34c556b.png)

## 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2), (2021-09-05)
![image](https://user-images.githubusercontent.com/89329256/132115015-18f6ad55-9864-4e7b-9a6e-94e090c0fffe.png)
### 程式碼
````C
int red = 11;
int blue = 10;
int green = 9;

void setup()
{
  pinMode(red, OUTPUT);
  pinMode(green, OUTPUT);
  pinMode(blue, OUTPUT);
}

void loop()
{

  analogWrite(red,255);
  analogWrite(green,0);
  analogWrite(blue,0);
  delay(1000);
  analogWrite(red,0);
  analogWrite(green,255);
  analogWrite(blue,0);
  delay(1000);
  analogWrite(red,0);
  analogWrite(green,0);
  analogWrite(blue,255);
  delay(1000);
  
}
````
## 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動3), (2021-09-05)
![image](https://user-images.githubusercontent.com/89329256/132972381-ec923665-59f6-4e16-9674-9b5175b4cd6e.png)

### 程式碼
````C
int R = 9;
int G = 10;
int B = 11;

int DR = 2;
int DG = 4;
int DB = 7;

void setup()
{
  pinMode(13, OUTPUT); // pin 13
  
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
  
  pinMode(DR, OUTPUT);
  pinMode(DG, OUTPUT);
  pinMode(DB, OUTPUT);   
}

void loop()
{
  // digitalWrite: 2 state (i.e., 0, 1) Only
  digitalWrite(13, 1); // LED @ pin 13, ON
  
  delay(1000); 
  
  digitalWrite(DR, 1);
  digitalWrite(DG, 0);
  digitalWrite(DB, 0);
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 1);
  digitalWrite(DB, 0);  
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 0);
  digitalWrite(DB, 1);  
  delay(1000);

  digitalWrite(13, 0); // OFF
  digitalWrite(DR, 0); // OFF
  digitalWrite(DG, 0); // OFF
  digitalWrite(DB, 0); // OFF  
  delay(1000);
  
  // analogWrite: The brightness can be adjusted with 256 levels
  for (int i = 0; i<= 255; i++)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10);
  } // from dark to bright 

  for (int i = 255; i>= 0; i--)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10); // 10ms = 0.01s
  }  // from bright to dark
  delay(1000);
}
````
## 實作2-4 analogRead(), 1024解析度 (i.e.,10-bit): 可變電阻 + 序列監視器與輸出; 當你改變可變電阻的阻值(e.g., 10K-ohm)時，序列監視器輸出的數值有什麼改變? 數值又有什麼意義呢? 
![image](https://user-images.githubusercontent.com/89329256/132972302-e5169092-1c21-435a-91d7-55a538c31c7c.png)

### 程式碼
````C
int sensorValue = 0;

void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);

}

void loop()
{
  // read the input on analog pin 0:
  sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
  delay(10); 
}
````

## 實作2-5: 按下按鍵, Green LED亮 & Red LED滅; 放開按鍵, Green LED滅 & Red LED亮. 想要再深入的同學可以試試喔. (思考方向: digitalRead(), digitalWrite(): 按鍵 +序列輸出 + LED), (互動5) (2021-09-19) 

![image](https://user-images.githubusercontent.com/89329256/135738928-2440b688-1c9a-443d-aac3-aa85b47a9c2f.png)

### 程式碼
```C
int ledPinG = 13 ;
int ledPinR = 8 ;
int buttonPin = 2 ;
void setup()
{
  pinMode(ledPinG, OUTPUT);
  pinMode(ledPinR, OUTPUT);
  pinMode(buttonPin, INPUT);
  Serial.begin(11500);

}

void loop()
{ 
Serial.print(digitalRead(buttonPin)) ;
  if(digitalRead(buttonPin) == 1)
  {
    digitalWrite(ledPinR, LOW);
    digitalWrite(ledPinG, HIGH);
  }
  else{
  digitalWrite(ledPinR, HIGH);
  digitalWrite(ledPinG, LOW);
  }
}
```
