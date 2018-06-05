## 本文你將會學到
- 使用GCP建立Cloud SQL雲端資料庫
- 本機建立雲端資料庫連線

## 前言
GCP 有提供雲端 MySQL 資料庫的服務，且提供的資料庫基礎架構讓在任何位置執行的應用程式都能使用，你可以放心的將將資料庫交給 Google 管理不需要額外的自己架 Server 資料庫，官方提供第一代及第二代 SQL 兩者差別在於計價方式，有興趣的讀者可以到[官方](https://cloud.google.com/sql/?hl=zh-tw)看看說明。

## 建立Cloud SQL

### 建立執行個體
在左側選單找到儲存空間SQL點擊進去，首次進入系統會要求你建立一個新的 SQL執行個體，我們這邊選擇 MySQL資料庫引擎並使用第二代，輸入執行個體id、root密碼、區域，若想省錢的可以選擇美洲地區，此外為了方便個人習慣將密碼與本機MySQL密碼相同，建立完成後進入到整個資料庫的主控台其中他會給你一組 IPv4 位址，此 IP 要記住之後要利用資料庫管理介面(Sequel pro)從本機來做連線。

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247raHFSMbhtc.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247raHFSMbhtc.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/20107247xRHKdovBSc.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247xRHKdovBSc.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/20107247qRGRKLPuEL.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247qRGRKLPuEL.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/20107247j9n8aajlh4.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247j9n8aajlh4.png)

### 新增資料庫容器
建立好執行個體後就來新增一個雲端資料庫取名為 `Community` 並且設定授權的網路，此設定的用意是要開啟某IP存取此雲端資料庫的權限，這邊設置兩個IP一個是昨日所建立的 GCP VM 的外部 IP，另一個為你電腦本機的 IP 位址，這樣的話這兩個 IP 位址就有權限存取 GCP 的雲端資料庫內容了。

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247P1cE3ggnB0.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247P1cE3ggnB0.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/201072472JKc7mDoJM.png](https://ithelp.ithome.com.tw/upload/images/20180120/201072472JKc7mDoJM.png)

### 匯出本機資料庫的 SQL 檔
由於要將雲端資料庫建立資料庫欄位，總不可能手動的一個一個慢慢建立，最快的方法就是引入sql檔直接利用sql語法來建立資料表，所以這邊要教你如何從本機資料庫匯出sql，首先開啟你的資料庫管理介面將原本的本機上的資料庫做匯出產出sql檔，這邊以 Sequel 做示範，`File > Export` 即可將所有資料表匯成一個sql檔。

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247Y5VwO6uUWC.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247Y5VwO6uUWC.png)

### 本機建立雲端資料庫連線
重新開啟資料庫管理介面並建立一個新連線，其中 Host 填上我們剛剛所建立的 Cloud SQL 所提供的 IPv4 位址，Username 填上 `root`、Password 填上當時雲端資料庫所設的密碼、Database 填上剛雲端資料庫所建立的容器 `Community` 完成後點擊連線，連線成功後就能將原有的sql檔引入進來了 `File > import`，匯入成功後你會發現原來本機端的資料庫整個複製一份過來了。

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247WCugvzl2CM.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247WCugvzl2CM.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/20107247FbbY61X440.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247FbbY61X440.png)


## 結論
實作到今天我們已經完成了GCP的虛擬機與雲端資料庫的建置了～
明天我們就來驗收兩邊的成果吧！


文章同時發表於：https://andy6804tw.github.io/2018/01/20/gcp-tutorial(3)/
