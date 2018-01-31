## 什麼是 REST/RESTful ?
Representational State Transfer，簡稱 REST，它是一種網路架構風格，近幾年來 REST 的概念已經被實作在大型網路系統中，而在 Web Service 中使用 REST 概念被實作出來的 API 就簡稱為 RESTful API 他是使用 HTTP 的協定完整定義 Web Service 在 HTTP Request 的各種流程。
![rest](https://www.openprogrammer.info/wp-content/uploads/2015/01/restful.gif)

[圖片來源](https://www.openprogrammer.info/2015/01/06/how-to-build-a-restful-service-java-8-sparkjava-in-five-minutes/)

### HTTP Request 方法
HTTP 本身就是 REST 的實作，所謂的 [HTTP Request](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Methods) 定義了八種請求方法分別為：

- [GET](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET)
  - 此方法只能向指定的資源要求取得資料，並不會更動到內部資源
- HEAD
  - HEAD 跟 GET 方法類似只差別在它並不會回傳你所請求的資源在 body 上，只回傳 HTTP header
- [POST](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST)
  - 向指定的資源提交資料
- [PUT](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT)
  - 向指定資源位置提交更新內容
- [DELETE](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE)
  - 向指定資源位置請求刪除內容
- CONNECT
  - HTTP/1.1協議中預留給能夠將連接改為管道方式的代理服務器
- OPTIONS
  - 此方法可使服務器傳回該資源所支持的所有 HTTP 請求方法
- TRACE
  - 回顯服務器收到的請求，主要用於測試或診斷

### REST 傳輸的要求
經由 [wiki](https://zh.wikipedia.org/wiki/%E5%85%B7%E8%B1%A1%E7%8A%B6%E6%80%81%E4%BC%A0%E8%BE%93) 定義 REST 風格最重要的架構約束有六個:
1. 客戶-服務器（Client-Server）
    - 客戶端和服務器結構
2. 無狀態（Stateless）
    - 連接協議具有無狀態性
3. 緩存（Cache）
    - 能夠利用Cache機制增進性能
4. 統一接口（Uniform Interface）
    - 一致性的操作界面
5. 分層系統（Layered System）
    - 層次化的系統
6. 按需代碼（Code-On-Demand，可選） 
    - 例如 JavaScript

### RESTful API 的安全性
我們設計 API 時，要保證 RESTful API 的安全性，原因是 PUT 或 DELETE 其實並不安全在沒有權限認證下任何人都可以存取此方法，總不能輕易地隨意讓一位陌生人來更動你的資料對吧？因此若安全性沒有做足容易就成為駭客攻擊的對象。

* 基本流程如下：

  會員機制(帳號密碼) -> 服務端驗證成功並取得一組 API token -> 使用此組 token 訪問 API 資源

### RESTful API 的 URI 命名

1. URL root: https://example/api/
2. 建議 URI components 都用小寫
3. URI 使用名詞而不是動詞，且建議使用複數

- BAD
  - /getProducts
  - /listOrders
  - /getProductsById?orderId=1

- GOOD
  - GET => /products    (回傳所有產品)
  - POST =>  /products   (新增產品)
  - GET =>  /products/4  (取得單筆產品)
  - PUT =>  /products/4  (修改單筆筆產品)
  - DELETE =>  /products/4  (刪除單筆產品)

## 何謂 MVC ?
MVC 一種軟體架構模式，把系統分成三個種核心，分別為:Model, View, Controller，這三個套用在 Web 分別為前端 HTML+CSS (View)，後端 API 資料庫(Model)，控制後端資料庫的接口 JavaScript (Controller)

- Model
  - 後端資料庫進行運作
- View 
  - 前端畫面與邏輯顯示
- Controller
  - 處理控制流程和回應，以路由以傳遞資料為主

### MVC 架構優點
優點如下:
- 有例於團隊開發
- 程式方便管理
- 程式擴充性高
- 使程式結構更加直覺
- 可讀性高

## 結論
本篇文章解釋了 RESTful API 定義與規範，可以讓開發者了解其功能性，此外建立良好的 MVC 架構有助於日後程式開發的茁壯，直覺、簡單、快速才是一個良好的 API 設計。


文章同時發表於：https://andy6804tw.github.io/2017/12/17/restful-mvc-intro/