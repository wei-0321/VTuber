# VTuber

(摘要)


# 簡介

介紹投影片 : 


展示 :





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
- Python版本 >= 3.8
- CUDA toolkit版本 >= 11.1

所需python套件：
- Pytorch(torch)版本 >= 1.9.0 
- scipy
- wxPython
- PyQt5
- numpy 
- opencv(cv2)
- Pillow(PIL)
- scikit-image(skimage)
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
