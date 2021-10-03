# Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output
### 利用 pinMode() 設定編號 7 腳位( SIG )為數位輸出，設定為 LOW (i.e., digitalWrite(tPin, LOW);) 維持 2us，目的為將超音波模組設定 **RESET**。
### 將編號 7 腳位 (SIG) **設定為 HIGH，並維持10us，觸發超音波模組**。最後將編號7腳位 (SIG) 設定為 LOW (此時仍為OUTPUT )後，接著將編號 7 腳位設定為 INPUT 準備接收模組回傳的脈波訊號。
![image](https://user-images.githubusercontent.com/89329256/135738316-3862ea65-2602-4cc7-94a3-5788b8f1f959.png)
![image](https://user-images.githubusercontent.com/89329256/135738378-62004a62-8784-478d-ab7d-8f8e341748db.png)

# Lab 3-2: 超音波感測器 + LED (紅色LED:亮<70cm, 緑色LED: 亮>270cm, 藍色LED:亮, 介於70cm ~ 270cm之間) + RS232 Output

![image](https://user-images.githubusercontent.com/89329256/135739687-71871def-8e9a-4c10-b62e-31c64230db5d.png)

## 程式碼
````C
const int Red = 12;
const int Green = 8;
const int Blue = 10;

int inches = 0;

int cm = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void changeLedColor(int type){
  switch (type){
    case 1://red
    analogWrite(Red,255);
    analogWrite(Green,0);
    analogWrite(Blue,0);
    break;
    case 2://green
    analogWrite(Red,0);
    analogWrite(Green,255);
    analogWrite(Blue,0);
    break;
    case 3://blue
    analogWrite(Red,0);
    analogWrite(Green,0);
    analogWrite(Blue,255);
    break;
  }
}

void setup()
{
  Serial.begin(9600);

}

void loop()
{
  // measure the ping time in cm
  cm = 0.01723 * readUltrasonicDistance(7, 7);

  if(cm <70)
  {
    changeLedColor(1);
  }
  else if(cm>= 270)
  {
    changeLedColor(2);
  }
  else if(cm>= 70&& cm<270)
  {
    changeLedColor(3);
  }
  
  // convert to inches by dividing by 2.54
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.println("cm");
  delay(100); // Wait for 100 millisecond(s)
}
````

# Lab 3-3: Arudino常用的C語言程式介紹與實作
![image](https://user-images.githubusercontent.com/89329256/135739987-072f3921-8570-41ee-9886-5e71a0e7103c.png)

## 程式碼
````C
int RLED = 13;
int GLED = 11;


int result, result2, result3;
String d0 = "****** 9X9 Table ******";
String d1, d2, d3;
void setup()
{
  pinMode(RLED, OUTPUT);   // Configure PIN13
  pinMode(GLED, OUTPUT);   // Configure PIN11
  
  Serial.begin(9600);

}

void loop()
{
  int aa = 0;

  Serial.println(d0); 
  
  digitalWrite(RLED, HIGH);
  analogWrite(GLED, aa); 
  
  for (int i=1;i<=9; i=i+3){
    for (int j=1;j<=9; j++){
      
      result = i*j;
      result2 = (i+1)*j;
      result3 = (i+2)*j;
      
      d1 = String(String(i) + "X" + String(j) + "=" + String(result));
      d2 = String(String(i+1) + "X" + String(j) + "=" + String(result2));
      d3 = String(String(i+2) + "X" + String(j) + "=" + String(result3));
      
      Serial.println(d1 + ", " + d2 + ", " + d3);


       
      aa+=1;
      
      delay(100);
    } // loop j
    analogWrite(GLED, aa*3); 
    Serial.println("");
  } // loop i

  digitalWrite(RLED, LOW);
  analogWrite(GLED, 255); 
  delay(2000);	
  analogWrite(GLED, 0);
}
````
