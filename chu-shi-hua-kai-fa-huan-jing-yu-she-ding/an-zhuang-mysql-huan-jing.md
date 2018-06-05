## 本文你將會學到
- 了解資料庫型態
- 如何在自己本機端安裝 MySQL 環境

## 資料庫系統

資料庫系統是由資料庫和資料庫管理系統所組成的，資料庫的定義就是一個儲存資料的電子文件檔案櫃並有長存資料之稱，數據類型分為關聯性資料庫(SQL)以及非關聯性資料庫(MySQL)。

##### 1.關聯性資料庫(SQL)

所謂關聯(Relationship)是指藉由表格(table)之間的關聯性的形式找出資料的方法，常見的類型有以下幾種。

- MySQL
- PostgreSQL
- Microsoft Access
- Microsoft SQL Server
- Google Fusion Tables
- FileMaker
- Oracle數據庫
- Sybase
- dBASE
- Clipper
- FoxPro
- foshub

**以下舉個例子：**

會員(Member)                   

|Id     |Name   |Status  |
| :---: | :-----: | :----: |
|  1    |  Andy  |       1
|  2    |   Jack  |      0
|  3    |   Mary  |      1
|  4    |  Tom    |      1

文章(Article)

|Id     |Uid  |Title  |
|:---: |:----:| :----: |
|  1    |  1  |   Title1
|  2    |  1  |   Title2
|  3    |  2  |   Title3
|  4    |  3  |   Title4
|  4    |  4  |   Title5

**Example 1.** 

查詢會員資料表 Id 是 1, 3, 4 的所有資料

```sql
SELECT * FROM Member WHERE Id IN (1, 3, 4)
```
**Example 2.**

資料表 Article 的 Uid 對應 Member 的 Id，我們要找到所有會員 Status = 1 的文章

```sql
SELECT * FROM Article WHERE Uid IN (SELECT Id FROM Member WHERE Status = 1)
```

##### 2.非關聯性資料庫(NoSQL)

非關聯性資料庫故名意思就是沒有關聯性的他所存在的資料，有分為四大類 Key-Value資料庫、記憶體資料庫、文件資料庫、圖學資料庫，其中最常見的就是一個鍵(key)搭配一個值(value)，Google 的 Firebase Database 就是儲存非關聯性的資料，下面來為各位做整理。

- Key-Value資料庫
  - Google的BigTable
  - Hadoop的HBase
  - Amazon的Dynamo
  - Cassandra
  - Hypertable
- 記憶體資料庫
  - Memcached
  - Redis
  - Velocity
  - Tuple space
- 文件資料庫
  - CouchDB
  - MongoDB
  - Riak
- 圖學資料庫
  - Neo4j
  - InfoGrid
  - AllegroGrph

![https://ithelp.ithome.com.tw/upload/images/20171228/20107247i3HFDugdx4.png](https://ithelp.ithome.com.tw/upload/images/20171228/20107247i3HFDugdx4.png)

想知道更詳細可以參考[這篇](https://www.ithome.com.tw/news/92507)裡面寫得非常詳細。

## 安裝 MySQL

廢話不多說這裡來教各位如何在你的電腦建置 MySQL 環境，macOS 和 Windows 的安裝方式不同所以我分開講，由於我電腦已經安裝過了所以我這邊就只教你如何去安裝他。

##### 1.macOS

mac 的讀者可以到[這裡](https://dev.mysql.com/downloads/mysql/)來下載 MySQL Community Server 點選第一個安裝，安裝後會有個小視窗跳出來像下面這樣，這是你的 MySQL root 密碼要截圖記住，忘記就麻煩了，下一篇教學就會教你如何用圖象化軟體和你的 MySQL 做連線，安裝完成後可以到系統的偏好設定會發現多一個 MySQL 的圖示，點進去可以查看是否有正常運作。

![https://ithelp.ithome.com.tw/upload/images/20171228/20107247Tvb96XZfMd.jpg](https://ithelp.ithome.com.tw/upload/images/20171228/20107247Tvb96XZfMd.jpg)
![https://ithelp.ithome.com.tw/upload/images/20171228/20107247ClhwwuCUEr.png](https://ithelp.ithome.com.tw/upload/images/20171228/20107247ClhwwuCUEr.png)

##### 2.Windows

Windows 的讀者可以到[這裡](https://dev.mysql.com/downloads/windows/installer/)來下載 MySQL Installer 這個安裝檔附有很多安裝包可以自己選擇要安裝哪些套件，其中我們只選擇安裝 MySQL Server 就好，記得安裝之前先依他的只是先行安裝 Visual C++ 才能繼續以下安裝，安裝完成後他會要求你設定名稱與密碼。

![https://ithelp.ithome.com.tw/upload/images/20171228/20107247w8UDmbwnKg.jpg](https://ithelp.ithome.com.tw/upload/images/20171228/20107247w8UDmbwnKg.jpg)

## 結語
今天先到這邊把自己電腦本機端的 MySQL 安裝好，明天將教各位如何使用 GUI 圖像化介面的安裝連線設定，話說在這次鐵人賽幾乎沒有看到搞資料庫的文章，有點可惜本來還想多學些的，不過我這邊會把最基本的觀念帶給各位讀者哦！

文章同時發表於：https://andy6804tw.github.io/2017/12/28/mysql-install/
