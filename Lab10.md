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

## Lab 10-3 人臉辨識實際應用

### 程式碼(1)

```` python

#Lab實作: 試試看使用你自己在網路上找到的團體照, 並且加入你的英文名字1
image = cv2.imread("12053.jpeg")
haar = cv2.CascadeClassifier('haarcascade_frontalface_default.xml') #載入分類器
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)#圖片轉灰階
faces = haar.detectMultiScale(gray) #偵測人臉

for (x,y,w,h) in faces:
    cv2.rectangle(image,(x,y),(x+w,y+h),(0,255,0),2) #畫矩形框 可改框的顏色/線條粗細
#文字 cv2.putText(影像, 文字, 座標, 字型, 大小, 顏色, 線條寬度, 線條種類)
cv2.putText(image, ('Iris by CV2'), (+100,+100), cv2.FONT_HERSHEY_SIMPLEX,
2, (0, 255, 255), 5, cv2.LINE_AA)
plt.figure(figsize=(12,10)) #設定顯示尺寸
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB)) #BGR to RGB
print('找到臉的數量:',len(faces))

````

### 顯示結果

![image](https://user-images.githubusercontent.com/89329256/144733453-a13bb3de-a42d-42c4-a223-29ee2ef306df.png)

### 程式碼(2)

````python

#Lab實作: 試試看使用你自己在網路上找到的團體照, 並且加入你的英文名字2

import cv2
import face_recognition
# %matplotlib inline
import matplotlib.pyplot as plt
image = face_recognition.load_image_file("12053.jpeg") #92
faces = face_recognition.face_locations(image,model='cnn')
print("找到臉的數量=",len(faces))
for (top, right, bottom, left) in faces: #畫矩形框 可改框的顏色/線條粗細
    cv2.rectangle(image, (left, top), (right, bottom), (0, 255, 0), 2)
cv2.putText(image, ('Iris by CV2'), (+100,+100), cv2.FONT_HERSHEY_SIMPLEX,
2, (0, 255, 255), 5, cv2.LINE_AA)
plt.figure(figsize=(12,10))
#plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.imshow(image)
````
### 顯示結果

![image](https://user-images.githubusercontent.com/89329256/144733491-e67ea22a-c077-4316-b012-3968cc05211a.png)
