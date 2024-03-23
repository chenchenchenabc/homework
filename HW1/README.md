# HW1.[Deep Learning]

### 此題所學
得知colab有提供GPU使用(但每天有使用量限制),故最終決定以colab實做作業,作業中了解了使用keras建立CNN模型的步驟分為1.準備數據 2.建立模型架構 3.編譯模型 4.訓練模型 5.評估模型 6.使用模行進行預測,也粗略的知道了1.Learning_Rate 2.Batch_size 3.Optimizer 4.Dense_Layer_Units 5.Data Augmentation 會對training過程與結果造成那些影響。

### 簡短心路歷程
剛開始以自建模型的方式去training,嘗試調整以上五種參數,過程中產生over_ fitting與under_fitting的情況(最好情況:accuracy約97%,valid_accuracy約70%)但因為不斷嘗試很容易達到Colab的GPU使用量上限,經過幾次嘗試後決定以網路上推薦用來對圖形辨別的Xception模型當作bass_model去做fine turning,最終在圖形資料生成器加入horizontal_flip進行資料增強時對訓練有很大的提升,accuarcy與valid_accuracy皆約99%,雖然成效很好但訓練一次非常耗時,最終調整過新增的全連接層節點數與batch_size後看起來並沒有降低準確率,且訓練速度也快了一些,另外也有注意到在訓練model時是不用將圖片以numpy方式儲存的,而使用模型時會以numpy方式儲存大量圖片,原因為訓練model時使用的ImageDataGenerator會負責將圖片轉為模型可接受的張量格式,故不需以numpy方式存取圖片。

### 前置作業
###### 1.將所有第一題中的檔案解壓縮至新的資料夾命名為"70_dog"
###### 2.將"Testing set.zip"解壓縮至新的資料夾命名為"70_dog_testing_set"並移入"70_dog"資料夾內
###### 3.此時"70_dog"資料夾內會有"70_dog_testing_set"、"test"、"train"、"valid"、"dog.csv"共四個檔案夾、一個.csv檔
###### 4.將"70_dog"與"作業一_Deep_learning.ipynb"上傳至google雲端硬碟中的"我的雲端硬碟"
###### 5.(若第一次使用colab)在雲端硬碟頁面點選左上角"新增"->"更多"->"連結更多應用程式"搜尋"colaboratory"後安裝,對想開起的檔案(.ipynb檔)點右鍵"選擇開啟工具"->"Google Colaboratory"
###### 6.執行程式前可在colab介面點擊左上角"編輯"內的"筆記本設定"有免費提供的GPU可使用

### 若不在colab上執行,則須更改程式內以下路徑至各資料存放路徑
### (需注意:# 依指定路徑儲存模型、# 載入模型 應為相同路徑)
###### (程式區塊二)的"# 定義圖片資料路徑"、"# 依指定路徑儲存模型"
###### (程式區塊三)的"# 載入模型"、"# 輸入testing資料"、"# 將結果儲存至test_data.xlsx"


### 程式大致流程
#### (程式區塊一)
###### 1.授權colab對雲端硬碟進行存取  

#### (程式區塊二,此區塊產生訓練模型並儲存)
###### 2.程式會從"70_dog"中的train、valid、test中找到指定品種作為訓練資料
###### 3.以Xception為bass做fine turning
###### 4.將訓練好的model存於"70_dog"內新增的"fine turning"資料夾  


#### (程式區塊三,此區塊載入訓練好的模型做testing)
###### 5.載入經過fine turning的模型並輸入testing資料
###### 6.將預測結果以.xlsx檔輸出至"70_dog"內的"fine turning"資料夾

