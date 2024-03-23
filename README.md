# HW1.[Deep Learning]

### 此題所學
得知colab有提供GPU使用(但每天有使用量限制),故最終決定以colab實做作業,作業中了解了使用keras建立CNN模型的步驟分為1.準備數據 2.建立模型架構 3.編譯模型 4.訓練模型 5.評估模型 6.使用模行進行預測,也粗略的知道了1.Learning_Rate 2.Batch_size 3.Optimizer 4.Dense_Layer_Units 5.Data Augmentation 會對training過程與結果造成那些影響。

### 簡短心路歷程
剛開始以自建模型的方式去training,嘗試調整以上五種參數,過程中產生over_ fitting與under_fitting的情況(最好情況:accuracy約97%,valid_accuracy約70%)但因為不斷嘗試很容易達到Colab的GPU使用量上限,經過幾次嘗試後決定以網路上推薦用來對圖形辨別的Xception模型當作bass_model去做fine turning,最終在圖形資料生成器加入horizontal_flip進行資料增強時對訓練有很大的提升,accuarcy與valid_accuracy皆約99%,雖然成效很好但訓練一次非常耗時,最終調整過新增的全連接層節點數與batch_size後看起來並沒有降低準確率,且訓練速度也快了很多,另外也有注意到在訓練model時是不用將圖片以numpy方式儲存的,而使用模型時會以numpy方式儲存大量圖片,原因為訓練model時使用的ImageDataGenerator會負責將圖片轉為模型可接受的張量格式,故不需以numpy方式存取圖片。

### 前置作業
###### 1.將所有第一題中的檔案解壓縮至新的資料夾命名為"70_dog"
###### 2.將"Testing set.zip"解壓縮至新的資料夾命名為"70_dog_testing_set"並移入"70_dog"資料夾內
###### 3.此時"70_dog"資料夾內會有"70_dog_testing_set"、"test"、"train"、"valid"、"dog.csv"共四個檔案夾、一個.csv檔
###### 4.將"70_dog"上傳至google雲端硬碟中的"我的雲端硬碟"
###### 5.(若第一次使用colab)在雲端硬碟頁面點選左上角"新增"->"更多"->"連結更多應用程式"搜尋"colaboratory"後安裝,對想開起的檔案(.ipynb檔)點右鍵"選擇開啟工具"->"Google Colaboratory"
###### 6.執行程式前可在colab介面點擊左上角"編輯"內的"筆記本設定"有免費提供的GPU可使用


### 程式大致流程
(程式區塊一)
###### 1.授權colab對雲端硬碟進行存取

(程式區塊二,此區塊產生訓練模型並儲存)
###### 2.程式會從"70_dog"中的train/valid/test中找到指定品種作為訓練資料
###### 3.以Xception為bass做fine turning
###### 4.將訓練好的model存於"70_dog"內新增的"fine turning"資料夾

(程式區塊三,此區塊載入訓練好的模型做testing)
###### 5.載入經過fine turning的模型並輸入testing資料
###### 6.將預測結果以.xlsx檔輸出至"70_dog"內的"fine turning"資料夾





# HW2.(1)[Hill Climbing]

### 此題所學
得知hill climbing algo主要結構為1.初始解 2.評估函數 3.鄰近解生成 4.選擇最優解 5.終止條件

### 各結構方法
###### 1.初始解部分採取完全隨機選取,若取超過capacity則由評估函數處理
###### 2.評估函數以超過capacity時profit為0來算出總profit即可 
###### 3.hill_climbing鄰近解生成在網路上查到有翻轉物品狀態的方式,判斷很適合用來解knapsack問題
###### 4.鄰近解與初始解相比取profit較大者
###### 5.迭代100次

### 簡短心路歷程
在經過多次嘗試後發現在此題中初始解的選取是最影響迭代次數的關鍵,但為了避免因各種問題的最佳解不同(eq.最佳解為全取或只取其中一件物品)而導致我的hill_climbing可能有特別的取物傾向,故仍維持以全隨機方式選擇初始解,而我選擇以"翻轉物品選取狀態"可以保證在無限次的迭代中一定可以找到最佳解,然而在無特別取物傾向的情況下,我認為此類型題目在相同問題規模下以hill_climbing似乎無法穩定在100次內迭代至最佳解

# HW2.(2)[Genetic Algo]

### 此題所學
得知genetic algo主要結構為1.初始化群體 2.適應度函數 3.選擇最優解 4.交叉與突變

### 各結構方法
###### 1.初始解群體部分採取完全隨機選取,若超過capacity則由適應度函數處理,發現若population_size取太大會一下子就找到最佳解而失去此演算法意義 
###### 2.適應度函數以超過capacity時profit為0來算出總profit即可 
###### 3.選profit最大的 
###### 4.交叉方式為隨機取兩父帶中的同一點做截斷後交叉接合,突變方式同hill_climbing的翻轉方式

### 簡短心路歷程
大致了解這個演算法後,覺得很像小時候常玩的猜幾A幾B的遊戲,優先以猜得最準的幾次去做交叉並適當的突變能更好得猜出答案,經過調整population_size後能穩定的以不快也不慢的速度收斂至最佳解,覺得在knapsack problem中以genetic algo來解是非常合適的,可以有效的過濾許多不良的猜測,也因為起始點多而大大的降低只找到區域最佳解的機率



### 前置作業
###### 1.將作業二的四個txt檔p06_c、p06_p、p06_s、p06_w放入新的資料夾命名為"Meta-heuristic Algorithm"
###### 2.將"Meta-heuristic Algorithm"上傳至google雲端硬碟中的"我的雲端硬碟"

### 程式流程

(程式區塊一)
###### 1.授權colab對雲端硬碟進行存取
###### 2.考慮到未來函數使用時程式更方便理解並減少數據誤植發生可能,故選擇以矩陣方式合併存取weight與profit

(程式區塊二,此區塊實作Hill_Climbing)
###### 3.設定評估函數,目的為取得不超過capacity的最大profit
###### 4.設定hill_climbing函數,生成初始解與鄰近解,鄰近解採隨機翻轉一個物品選取狀態並與最佳解做比較
###### 5.執行hill_climbing並繪出圖片

(程式區塊三,此區塊實作Genetic_Algo)
###### 6.設定基因演算法參數,定義適應度函數、初始化群體、交叉操作與突變操作
###### 7.設定genetic_algo函數,不斷讓profit較大的父代做交叉並讓子代有10%機率突變
###### 8.執行genetic_algo並繪出圖片
