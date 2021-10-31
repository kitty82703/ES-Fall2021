# Lab 6-1 用16X2 LCD 顯示器來顯示4X4鍵盤輸入的數字 (0, 1, 2, .., 9), 若輸入的字數≥16則換到下一列, 若兩皆滿, 則清除劃面重新由Row=0, Col=0開始, 細節請參考以下Demo.

## 電路圖

![image](https://user-images.githubusercontent.com/89329256/139567118-8b568f16-7727-4710-9177-765b38870fbe.png)


## 程式碼

````C

// For Embedded System course, VNU, Fall 2021 

#include <Keypad.h>
#include <LiquidCrystal.h>
// 5:RS, 4:E, 3:DB4, 2:DB5, A4:DB6, A5: DB7
// LCD若只顯示文字，只須使用4-bit模式即可 (LCD腳位DB0, DB1, DB2, DB3就不用接了。)
LiquidCrystal lcd(5, 4, 3, 2, A4, A5);

const byte ROWS = 4; // 4列數(橫的)
const byte COLS = 4; // 4行數(直的)
char keys[ROWS][COLS] = {
  {'1','2','3','A'},
  {'4','5','6','B'},
  {'7','8','9','C'},
  {'*','0','#','D'}
};

byte rowPins[ROWS] = {A0, A1, 11, 10}; //定義列的腳位
byte colPins[COLS] = {9, 8, 7, 6}; //定義行的腳位

int LCDCol = 0;
int LCDRow = 0;

Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS, COLS );

void setup(){
   Serial.begin(9600);
   lcd.begin(16, 2);
   lcd.setCursor(LCDCol, LCDRow);
   }
  
void loop(){

  char key = keypad.getKey();
  
  if (key){
    
    Serial.println(key);
           
    
    if ( LCDCol > 15  )
    {   
     ++LCDRow; // Move to the 2nd row
      
      if (LCDRow>1)
      { LCDRow=0; LCDCol = 0 ;  lcd.clear(); } // clear and move back the 1st row
   
    LCDCol = 0 ;
    }
         
    lcd.setCursor (LCDCol, LCDRow); 
    
       lcd.print(key);
    
    ++LCDCol;
    
  }
}

````

# Lab 6-2 分享一個你最喜歡的實作 (電路即可)到你的GitHub
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
