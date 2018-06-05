## 本文你將會學到
- 了解 JWT 和 Bearer Token 的關係與 OAuth 2.0
- 了解 HTTP Authentication 中有哪些 schemes
- 客戶端向後端出示API Token的三種方式
- Authenticate 的 API Error 錯誤訊息

<img src="https://i.ytimg.com/vi/CPbvxxslDTU/maxresdefault.jpg">
[圖片來源](https://www.youtube.com/watch?v=CPbvxxslDTU)


## JWT 和 Bearer Token 的關係
要存取某 API 時，若要身份驗證則在 JWT 前面加上字符串 `Bearer` 再放到 HTTP 請求的 Header 中，這個值就是 `Bearer Token`，至於為什麼要這樣做？ HTTP 的認證「Authorization」方案有許多種格式，而 Bearer 就是其中一種且被定義在 Header 中的驗證方案，通常搭配於 JWT 上，Resource server 是資源服務器，即後端存放用戶生成的 API Token 的服務器。 Authorization server 的意思是認證服務器，即後端專門用來處理認證的服務器在我們系列實作是使用 JWT 機制，這些東西都是由 [OAuth 2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html) 中所定義出來的，在定義中說明了 Client 如何取得 Access Token 的方法，在這篇文章稍微提到就好若要完整解釋可能就是另一個領域了，在這系列文中就不多贅述，本篇只會說明基本使用方法跟注意事項。

**Authentication schemes：**
- Basic [(RFC 7617)](tools.ietf.org/html/7617)
- Bearer [(RFC 6750)](https://tools.ietf.org/html/rfc6750)
- Digest [(RFC 7616)](https://tools.ietf.org/html/rfc7616)
- HOBA [(RFC 7486)](https://tools.ietf.org/html/rfc7486)
- [Mutual](https://tools.ietf.org/html/draft-ietf-httpauth-mutual-11)
- [AWS4-HMAC-SHA256](https://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-auth-using-authorization-header.html)

[參考](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

## 客戶端向後端出示 API Token 的方式
客戶端(Client)向後端(Server)出示 API Token 的方式分為三種。

#### 1. 放在 HTTP Header 裡面
此方法為 Resource Server 資源服務器，為本系列文中所實作的方式，使用 GET 請求方式並將 API Token 放在 Header 裡。

```bash
GET /api/article/personal HTTP/1.1
Host: localhost:3000
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJfaWQiOjEsInVzZXJfbmFtZSI6IkFuZHkxMCIsInVzZXJfbWFpbCI6ImFuZHlAZ21haWwuY29tIn0sImV4cCI6MTUxNTczODUxOSwiaWF0IjoxNTE1NzM3NjE5fQ.CLPeXhcxl2mdsL6-sUNFHFYABkTxmzx3YxEPyNih_FM
```

![https://ithelp.ithome.com.tw/upload/images/20180114/20107247ankhTWE8bF.png](https://ithelp.ithome.com.tw/upload/images/20180114/20107247ankhTWE8bF.png)


#### 2. 放在 Request Body 裡面
此方法也有人用，選擇 POST 請求方式並把 API Token 放在 Body 裡傳送，本系列文中的 新增、修改內容都是使用此方式傳值。

```bash
POST /api/article/personal HTTP/1.1
Host: localhost:3000
Content-Type: application/x-www-form-urlencoded
token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJfaWQiOjEsInVzZXJfbmFtZSI6IkFuZHkxMCIsInVzZXJfbWFpbCI6ImFuZHlAZ21haWwuY29tIn0sImV4cCI6MTUxNTczODUxOSwiaWF0IjoxNTE1NzM3NjE5fQ.CLPeXhcxl2mdsL6-sUNFHFYABkTxmzx3YxEPyNih_FM
```

![https://ithelp.ithome.com.tw/upload/images/20180114/20107247c35pHcinNq.png](https://ithelp.ithome.com.tw/upload/images/20180114/20107247c35pHcinNq.png)

#### 3. 放在 URI 裡(Query Parameter)
通常不建議這種方式因為你的資訊會被暴露在前端使用者上，雖然是亂碼但還是會被有心時是利用的風險，但還是有被使用的時候，像[中央氣象局](https://opendata.cwb.gov.tw/usages)的 API ，開發者必須先註冊後取得授權碼 API Token 後再將 API Token 放到網址上進行 Open Data 的存取，他這樣做也是有用意存在，畢竟它提供的每支 API 都是 GET 形式。

![https://ithelp.ithome.com.tw/upload/images/20180114/20107247Mf5XSS7bCD.png](https://ithelp.ithome.com.tw/upload/images/20180114/20107247Mf5XSS7bCD.png)

## Authenticate 的 API Error 錯誤訊息
API Token 的驗證通常會遇到三個 HTTP Status Code 分別為 400 客戶端參數錯誤、401 登入失敗、403 權限不夠，這些都是 Resource Server 向 Client 端提示認證不過與拒絕存取的方式，幫各位整理以下表格：

|	Status Code | 說明 |
|------------- | ------------- |
|`400` (Bad Request) | 遇到無法解讀 Request 的情況。|
|`401` (Unauthorized) | API Token 過期、無法解讀、或其他 Access Token 不合法的情況。|
|`403` (Forbidden) | 尚未提供 Bearer Token ，即資源服務器(Resource server) 找無資訊。|

## 總結
Authorization 是用戶認證是後端最重要的一環，這邊最後整理幾項後端開發者必須去注意到的安全性問題，首先是盡量別把 API Token 外露在前端瀏覽器上以免被有心人士修改與攻擊例如儲存在 Cookie 中，且並全程使用 HTTPS 安全協定，最後將 API Token 設為有時效性的確保每次資料為最新狀態，當然還有更多安全的防護機制本系列文中沒詳細提到，像是偵測時間內 IP 位置多次請求 API Token 或是偵測到有不合法的存取行為......等，總之後端是整個專案中的心臟，所有想得到的問題都必須一一的去克服。

- API Token 顯示給用戶
- 全程使用 HTTPS 安全協定
- 不要把 API Token 存在 Cookie
- 定義有時效性的 API Token

文章同時發表於：https://andy6804tw.github.io/2018/01/14/get-personal-article(3)/


實作內容基本上就暫時到這邊，若各位還想繼續聽哪部分或是覺得哪裡不清楚需要再深入解釋的地方可以跟我說我可以再另外做番外篇哦 ＝）
接下來的內容就要進入最後的部署部分了(撒花