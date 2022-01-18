# VTuber

由於新冠肺炎(Covid-19)疫情造成生活型態的改變，部分日常互動、甚至上班上課都經由視訊進行，大家越來越習慣在線上互動，而這也使得「宅」經濟加速發展，直播產業等非接觸經濟變得更加興盛，其中虛擬網紅(VTuber)帶來的經濟效益更是驚人。但傳統VTuber在臉部特徵的偵測上需要靠昂貴且笨重的器材輔助，除此之外，虛擬人物的繪製與創建對於沒有美學基礎的人來說也是較為困難的。基於此，本專題實作出一個只需透過網路攝影機(Webcam)就能進行VTuber應用的系統。透過深度學習技術中的生成對抗網路(Generative Adversarial Networks, GANs)並使用我們特殊處理過後的資料集訓練過後就能生成出虛擬人物頭像，可以讓不會繪畫的人也能夠創造自己喜歡的虛擬人物。再搭配人臉辨識技術，將網路攝影機即時抓取的真人人臉特徵與GANs生成出來的虛擬人物頭像進行同步，最後整合成一個便於使用的圖形使用者介面。此系統可以降低成為VTuber的門檻，也有助於日後VTuber的相關應用，並豐富大家的日常生活。

# 簡介

介紹投影片 : 
[簡報投影片.pptx](https://github.com/wei-0321/VTuber/files/7856617/3.pptx)


展示 :

經過特殊前處理過後的動漫人物臉部資料集

![image](https://user-images.githubusercontent.com/71260071/149194671-b2df1c8b-fa2b-405b-81eb-6d3708c9217f.png)

使用這些資料即來訓練StyleGAN3模型，利用訓練完的模型可以產生出逼真的動漫人物形象

![image](https://user-images.githubusercontent.com/71260071/149194347-ba5aa912-9360-4df3-b97e-6fe24e670ffd.png)

能夠透過網路攝影機將使用者所選擇的動漫人物與真實人臉做同步

![image](https://user-images.githubusercontent.com/71260071/149194354-ec1cd503-fe90-44da-af03-7cecca5085ba.png)


# 系統架構
![image](https://user-images.githubusercontent.com/71260071/149192610-314efcba-3d16-4dd7-9486-00c49064643c.png)

# 功能
- 使用生成對抗網路即時生成虛擬人物，供使用者選擇喜愛的人物並儲存。
- 能夠利用網路攝影機達到真實人臉與虛擬人物同步的效果。
- 將整個功能包裝圖形使用者介面，方便使用者做使用。

# 未來展望
- 同步的準確度待加強，如眼睛、各種表情的偵測。
- 介面運作流程優化 (UX) => 頁面跳轉、資源的使用與釋放。
- 	移植到網頁或是行動裝置上。

# 需求
硬體：搭載NVIDIA顯示卡的電腦(建議配備為RTX30系列的顯卡)

軟體

所需環境：
- Python 版本 >= 3.8
- CUDA toolkit版本 >= 11.1

所需python套件：
- Pytorch (torch) 版本 >= 1.9.0 
- scipy
- wxPython
- PyQt5
- numpy 
- opencv (cv2)
- Pillow (PIL)
- scikit-image (skimage)
- pymatting
- hsh
- imutils
- matplotlib
- io 
- Dlib 
- Ninja  

# 使用方法
1.開啟 git bash. 

2.更改目錄到您想要下載此專案的位置 
```
> cd (your directory)
```
3.下載此專案 
```
> git clone https://github.com/wei-0321/VTuber.git
```
4.Change the diretory to this repository.
```
> cd VTuber
```
5.Execute the program.
```
> python GUI.py
```

# 專案目錄結構
```
(路徑)                                 (相關描述)
VTuber            	                  專案資料夾
│
├ GUI.py                               整合PYQT介面與所有用到的套件、函數的程式碼， 為主程式碼
│
├ anime_character                      使用者儲存的虛擬人物資料夾 
│  │ 
│  ├ XXX.png
│  │ 
│  ├ ...(略)
│
├ dnnlib                               StyleGAN相關套件的資料夾
│  │ 
│ (略)
│
├ torch_utils                          StyleGAN相關套件的資料夾
│  │ 
│ (略)
│
├  ui                                  介面相關資料夾
│  │ 
│  ├ layout                            含介面外觀設計的程式碼
│  │ 
│  ├ controller                        含操作介面用的程式碼
│
├  packages                            包含各種套件的資料夾       	
│  │
│  ├ __init__.py                               
│  │
│  ├ connect_avatar.py                 將真實人臉與虛擬人物同步的程式碼
│  │
│  ├ process.py                        進行後處理的程式碼(去背、動漫人臉區域置中)
│  │
│  ├ anime_face_detect                 動漫人臉偵測套件
│  │ 
│  ├ remove_background                 去背套件(含MODnet、U2net)
│  │ 
│  ├ gan                               生成對抗網路套件
│  │ │
│  │ ├ anime_avatar_maker              隨機生成虛擬人物頭像(StyleGAN)
│  │ │
│  │ ├ condition_anime_avatar_maker    條件式生成虛擬人物頭像(ACGAN)
│  │ 
│  ├ human_face_recognition            真實人臉偵測套件
│  │
│  ├ talking_head_anime                動漫人物姿態變換套件
│  │
│  ├ webcam_correction                 網路攝影機校正套件
│  │
```
