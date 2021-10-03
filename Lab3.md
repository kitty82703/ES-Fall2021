# Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output
### 利用 pinMode() 設定編號 7 腳位( SIG )為數位輸出，設定為 LOW (i.e., digitalWrite(tPin, LOW);) 維持 2us，目的為將超音波模組設定 **RESET**。
### 將編號 7 腳位 (SIG) **設定為 HIGH，並維持10us，觸發超音波模組**。最後將編號7腳位 (SIG) 設定為 LOW (此時仍為OUTPUT )後，接著將編號 7 腳位設定為 INPUT 準備接收模組回傳的脈波訊號。
![image](https://user-images.githubusercontent.com/89329256/135738316-3862ea65-2602-4cc7-94a3-5788b8f1f959.png)
![image](https://user-images.githubusercontent.com/89329256/135738378-62004a62-8784-478d-ab7d-8f8e341748db.png)


# Lab 3-2: 超音波感測器 + LED (紅色LED:亮<70cm, 緑色LED: 亮>270cm, 藍色LED:亮, 介於70cm ~ 270cm之間) + RS232 Output



# Lab 3-3: Arudino常用的C語言程式介紹與實作
