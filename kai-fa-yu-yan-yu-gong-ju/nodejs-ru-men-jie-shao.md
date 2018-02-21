## 何謂 Node.js
Node.js 是以 JavaScript 語言為基礎，是一個開放的原始碼 (Open Source) 的應用程式框架 (Application Framework)。

![node](https://camo.githubusercontent.com/dfe125b1579e723de45a206328df7e0705ed9f9f/68747470733a2f2f6e6f64656a732e6f72672f7374617469632f696d616765732f6c6f676f732f6e6f64656a732e706e67)

Node.js 是一個高效能、易擴充的網站應用程式開發框架 (Web Application Framework)。它誕生的原因，是為了讓開發者能夠更容易開發高延展性的網路服務，不需要經過太多複雜的調校、效能調整及程式修改，就能滿足網路服務在不同發展階段對效能的要求。在眾多後台語言中，選擇 Node.js 的原因有以下幾點：

 - 可自己寫 web server
 - 高效能「非同步IO」不會延遲等待
 - 低耗能(需要時再取得資源)
 - 第三方模組支援
 - 以 JavaScript 語言為基底，入門簡單
 
#### 1. 安裝 Node.js

先到官網安裝 [Node.js](https://nodejs.org/en/) ，這裡有兩個版本分別為穩定版和最新版，這可以具你的喜好安裝，作者是安裝最新的版本。

若要檢查 Node.js 是否正確安裝，可以使用以下的指令：
```
node -v
```

#### 2. 第一支 Node.js 程式

作者是使用 VS Code 來做開發，各位可以使是自己喜歡的編譯器來實作，編譯器來實作，首先開啟資料夾新增一個 index.js 的檔案，這支檔案就來實作我們第一個 web server。

```js
//透過http模組啟動web server服務
const http = require('http') 

const server = http.createServer(function (req, res) {
  //設定回應為text文件，並回應 Hello World!
  res.writeHead(200,{'Content-Type':'text/plain'})
  res.end('Hello World!')
})

//設定服務監聽localhost:3000(127.0.0.1/:3000)
server.listen('3000', function () {  
  console.log('server start on 3000 port')
})

```
之後在終端機輸入 node index.js 啟動檔案

![https://ithelp.ithome.com.tw/upload/images/20171213/20107247hUxVDyCpfZ.png](https://ithelp.ithome.com.tw/upload/images/20171213/20107247hUxVDyCpfZ.png)

顯示出來 console.log 的內容了！ 接著試著在網頁上輸入 localhost:3000 你會發現你寫的 Hello world 回應在網頁上了。

![https://ithelp.ithome.com.tw/upload/images/20171213/20107247UgfSkr27VN.png](https://ithelp.ithome.com.tw/upload/images/20171213/20107247UgfSkr27VN.png)

## 總結

在開發上為了減低開發時間以及提升效率，所以 Node.js 延伸出很多框架供使用者做開發，例如: 被官方認同的 Express 框架、Sails.js (node.js mvc)、Koa、Socket Stream ......等



文章同時發表於：https://andy6804tw.github.io/2017/12/13/node-tutorial/
