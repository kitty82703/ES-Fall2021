# Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output
## 利用 pinMode() 設定編號 7 腳位( SIG )為數位輸出，設定為 LOW (i.e., digitalWrite(tPin, LOW);) 維持 2us，目的為將超音波模組設定 **RESET**。
## 將編號 7 腳位 (SIG) **設定為 HIGH，並維持10us，觸發超音波模組**。最後將編號7腳位 (SIG) 設定為 LOW (此時仍為OUTPUT )後，接著將編號 7 腳位設定為 INPUT 準備接收模組回傳的脈波訊號。

