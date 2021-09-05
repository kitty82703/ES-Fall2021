# 嵌入式系統 - 實作1

## 1-1 在TinkerCAD開一個新的Circuit, 加上一個外部的LED, 並且ON (亮) 1秒, OFF(滅) 1秒
### 電路圖
![image](https://user-images.githubusercontent.com/89329256/131238297-480570e7-5b0d-44f3-862a-fa1f91fbf553.png)
### 程式碼(圖片)
![image](https://user-images.githubusercontent.com/89329256/131239891-b1ed5e67-f865-4076-801f-b432324896db.png)

## 1-2 在TinkerCAD開一個新的Circuit, 分別使甪R, G, B三種顏色的LED, ON (亮) 0.5秒, OFF(滅) 0.5秒
### 電路圖
![image](https://user-images.githubusercontent.com/89329256/131240011-c1bd3878-f255-4184-88f9-e84a71a80b5e.png)
### 程式碼(圖片)
![image](https://user-images.githubusercontent.com/89329256/131240022-abfcf4db-0db2-4034-847d-250f93398258.png)

## 1-3 在TinkerCAD開一個新的Circuit, 分別使甪R, G, B三種顏色的LED, 讓LED ON, OFF的順序為R >> G >> B >> G >> R .... 無限循環.
### 電路圖
![image](https://user-images.githubusercontent.com/89329256/131240289-4c45c08c-b40c-4194-a6b5-b59f62ff4316.png)
### 程式碼
```
// C++ code
//
/*
  This program blinks pin 13 of the Arduino (the
  built-in LED)
*/

void setup()
{
  pinMode(13, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(9, OUTPUT);
}

void loop()
  {
    // turn the LED on (HIGH is the voltage level)
    digitalWrite(13, HIGH);
    delay(500);
  	digitalWrite(13, LOW);
  	delay(500);
  	
  	digitalWrite(11, HIGH);
    delay(500);
  	digitalWrite(11, LOW);
  	delay(500);

  	digitalWrite(9, HIGH);
    delay(500);
  	digitalWrite(9, LOW);
  	delay(500);
  
  	digitalWrite(11, HIGH);
    delay(500);
  	digitalWrite(11, LOW);
  	delay(500);
}
```
