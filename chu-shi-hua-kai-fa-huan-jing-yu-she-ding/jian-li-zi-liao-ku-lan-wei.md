## 本文你將會學到
- 如何建立資料庫
- 如何建立資料表
- 如何建立資料表欄位 

## 前言
這篇文章終於開始要帶大家實作一個小專案啦！還記得一開始有提到要教各位做一個簡易的部落格貼文 API 現在就正式開始囉，前面幾週花了很多時間建立基礎與設定環境是為了讓大家可以有個從零開始的基礎，這幾週所提到的觀念接下來的實作中都會派上用場，若遇到不懂或不熟悉的可以再回去看看前幾篇文章囉。

## 使用 Sequel Pro 建立資料庫
#### 1. 建立資料庫(Database)
前幾篇文章已經教你如何下載與安裝 Sequel Pro ，環境設定好了那就開始建立資料庫與欄位囉！首先我們是要做一個部落格貼文 API 那我們就建立一個名為 `Community` 的 Database，點選左上角的 `Choose Database -> Add Database` 輸入資料庫名稱與選擇文字編碼的方式，這邊選擇萬國碼 `UTF-8` 這樣資料才能被接受儲存中文字。

![https://ithelp.ithome.com.tw/upload/images/20171231/20107247UxcGMk87KH.png](https://ithelp.ithome.com.tw/upload/images/20171231/20107247UxcGMk87KH.png)
![https://ithelp.ithome.com.tw/upload/images/20171231/20107247WsiDFMH0cr.png](https://ithelp.ithome.com.tw/upload/images/20171231/20107247WsiDFMH0cr.png)

#### 2. 建立資料表(table)
一個部落格貼文一定會有文章以及用戶，所以我們就分別建立文章 (Article) 與 用戶(User) 的資料表(table)，新增的方式點選介面最左下角的 `+` 號來新增 table 分別建立 Article 與 User。

![https://ithelp.ithome.com.tw/upload/images/20171231/20107247ofDDBFR1NU.png](https://ithelp.ithome.com.tw/upload/images/20171231/20107247ofDDBFR1NU.png)

##### 文章(Article)   

文章的欄位分別有主鍵 `文章id(article_id)` 以及外來鍵 `用戶id(user_id)` 對應到用戶這樣才能知道是誰發的文，此外還有 `文章標題(article_title)`、`文章標籤(article_tag)`、`文章內容(article_content)`、`文章發佈時間(article_created_time)`、`文章更新時間(article_updated_time)`，這邊要特別注意的是發佈與更新時間的型態要設為 `datetime` 時間格式，並且 `article_created_time` 在 `Default` 預設值位置要填上 `CURRENT_TIMESTAMP` 代表系統會自動寫入你當時的時間戳記，另外 `article_updated_time` 在 `Extra` 的欄位要選擇 `on update CURRENT_TIMESTAMP` 表示系統會自動寫入你變動資料的時間。               

|欄位     |型態   |備註  |
| --- | ----- | ---- |
|article_id|int(11)|文章id
|user_id|int(11)|用戶id
|article_title|varchar(255)|文章標題
|article_tag|varchar(255)|文章標籤
|article_content|text|文章內容
|article_created_time|datetime|文章發佈時間
|article_updated_time|datetime|文章更新時間

![https://ithelp.ithome.com.tw/upload/images/20171231/20107247QDSzrMTG04.png](https://ithelp.ithome.com.tw/upload/images/20171231/20107247QDSzrMTG04.png)

##### 用戶(User)  

用戶的欄位分別有主鍵`用戶id(user_id)`、`用戶姓名(user_name)`、`用戶信箱(user_mail)`、`用戶密碼(user_password)`、`用戶新增時間(user_created_time)`、`用戶更新時間(user_updated_time)`，這邊要一樣要注意的是發佈與更新時間的型態要設為 `datetime` 時間格式，並且 `user_created_time` 在 `Default` 預設值位置要填上 `CURRENT_TIMESTAMP` 代表系統會自動寫入你當時的時間戳記，另外 `user_updated_time` 在 `Extra` 的欄位要選擇 `on update CURRENT_TIMESTAMP` 表示系統會自動寫入你變動資料的時間。               

|欄位     |型態   |備註  |
| --- | ----- | ---- |
|user_id|int(11)|用戶id
|user_name|varchar(255)|用戶姓名
|user_mail|varchar(255)|用戶信箱
|user_password|varchar(255)|用戶密碼
|user_created_time|datetime|用戶新增時間
|user_updated_time|datetime|用戶更新時間

![https://ithelp.ithome.com.tw/upload/images/20171231/20107247kMvMhTFmN6.png](https://ithelp.ithome.com.tw/upload/images/20171231/20107247kMvMhTFmN6.png)

文章同時發表於：https://andy6804tw.github.io/2017/12/31/create-table/
