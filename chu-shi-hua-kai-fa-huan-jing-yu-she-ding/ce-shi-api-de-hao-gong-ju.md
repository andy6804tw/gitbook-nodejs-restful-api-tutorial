## 本文你將會學到
- 了解Postman能拿來做啥
- 使用Postman來測試API
- 安裝JSONView插件

## 前言
當你寫好一支 API 時要馬上測試看看你寫的是否能夠正常運作，GET 比較好處理直接在瀏覽器輸入路徑就能立即觀看結果，那當你要 POST(新增)、PUT(修改)、DELETE(刪除)時該怎麼辦呢？總不會要自己寫個表單輸入資料再用 ajax、axios、fetch 之類的請求方式將資料送出吧！？那這樣就太麻煩又沒效率了！所以我今天就來介紹各位如何利用 Postman 來測試你的 API。

## Postman 能做什麼？
Postman 他是一個能夠模擬 HTTP Request 的工具能夠讓你簡單快速的測試你的 API 新增、刪除、修改和取得資料，此工具內建包含很多 HTTP 的請求方式，例如常見的的 GET(取得)、POST(新增)、PUT(修改)、DELETE(刪除)，Postman 他是一個 Chrome 的擴充套件你可以在商店取得，此外他們也出了桌面版有興趣可以到他們[官網](https://www.getpostman.com/)看看。

![https://ithelp.ithome.com.tw/upload/images/20171230/20107247QChDByxCqc.png](https://ithelp.ithome.com.tw/upload/images/20171230/20107247QChDByxCqc.png)

### 安裝
首先你先安裝 Chrome 並且取得帳戶登入狀態，接著再到 Chrome線上應用程式商店搜尋 [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=zh-TW) 來安裝它。

![img](https://imgur.com/lDCvo3P.jpg)

### 測試

安裝後即可開啟應用程式，就來立即測試吧！我這邊提供一個環境保護署的即時空氣品質 [API](http://opendata2.epa.gov.tw/AQI.json)，直接複製網址到 Postman 的網址列上並選擇 GET 方法點選右邊 Send，最後結果就會回傳到 Body 以及其他資訊像是狀態碼 200 表示成功、回傳時間、Headers 狀態資訊......等都可以在 Postman 上一覽無遺，此外你可以選擇回傳格式像是 JSON、XML 等格式。

最後來介紹其他功能，左邊的 History 可以查看你測試的歷史，旁邊的 Collections 是將你的測試 API 儲存的地方你可以將他們建立資料夾分類，並且可以將整個資料夾匯出與匯入，最右邊的 Save 可以將你現在的資料做儲存。

![https://ithelp.ithome.com.tw/upload/images/20171230/20107247KI8UW8cNcB.png](https://ithelp.ithome.com.tw/upload/images/20171230/20107247KI8UW8cNcB.png)


## 其他 Chrome 擴充套件推薦
### JSONView
這邊我要介紹一個套件就是 JSONView 他能夠將你網頁呈現出來的 JSON 格式做漂亮的排版顯示，個人覺得很方便推薦給大家，一樣在Chrome線上應用程式商店搜尋 [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc) 就可以找到它囉，安裝後打開[API](http://opendata2.epa.gov.tw/AQI.json)看看結果。

![https://ithelp.ithome.com.tw/upload/images/20171230/20107247vyRRMUbNK3.png](https://ithelp.ithome.com.tw/upload/images/20171230/20107247vyRRMUbNK3.png)

- 安裝前

![https://ithelp.ithome.com.tw/upload/images/20171230/20107247IktQFANtAo.png](https://ithelp.ithome.com.tw/upload/images/20171230/20107247IktQFANtAo.png)

- 安裝後

![https://ithelp.ithome.com.tw/upload/images/20171230/20107247C6v5uxje4c.png](https://ithelp.ithome.com.tw/upload/images/20171230/20107247C6v5uxje4c.png)

文章同時發表於：https://andy6804tw.github.io/2017/12/30/postman-jsonview-intro/