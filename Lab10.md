# 嵌入式系統 - 實作10: AI最經典火紅的應用之人臉偵測實作

## Lab 10-1: 虛擬人臉數據取得

### 虛擬人造人臉1
![image](https://user-images.githubusercontent.com/89329256/144732330-3e66594b-8f97-4b74-ace6-2ee410a96b00.png)

### 虛擬人造人臉2
![image](https://user-images.githubusercontent.com/89329256/144732343-20262dd6-5f9c-4d39-83f2-25f8a18bec7a.png)

## Lab 10-2 OpenCV電腦視覺入門

### 程式碼
````python
#206: 在圖片上畫二條交錯的紫紅色的對角線，寬度為 5 px (0,0在最左上角)
import numpy as np
# 建立一張 256x256 的 RGB 圖片（0黑色）
img = np.zeros((256, 256, 3), np.uint8) #np.zeros建立0矩陣
# 將圖片用淺灰色 (200, 200, 200) 填滿
img.fill(200)
# 在圖片上畫一條紫紅色的對角線，寬度為 5 px (0,0在最左上角)
# cv2.line(影像, 開始座標, 結束座標, 顏色, 線條寬度)
cv2.line(img, (0, 0), (255, 255), (255, 0, 255), 5)
cv2.line(img, (255, 0), (0, 255), (255, 0, 255), 5)
# 顯示圖片
cv2_imshow(img)
````
### 顯示結果
![image](https://user-images.githubusercontent.com/89329256/144732514-a2d577be-cee1-42f8-91f3-6625ad190370.png)


