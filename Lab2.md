# 會呼吸的RGB LED,  按鍵控制, 狀態輸出 

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (2021-09-05)
![image](https://user-images.githubusercontent.com/89329256/132114191-d47c63cb-a07b-41d8-a6be-8d4cd34c556b.png)

## 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2), (2021-09-05)
![image](https://user-images.githubusercontent.com/89329256/132115015-18f6ad55-9864-4e7b-9a6e-94e090c0fffe.png)
```
// C++ code
//
/*
  This program blinks pin 13 of the Arduino (the
  built-in LED)
*/
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
```
## 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動3), (2021-09-05)
