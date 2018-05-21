## 何謂 Express
Express 可以說是 Node.js 底下的一個前端 + 後端的框架，也是被官方所認同推薦入門的套件之一，其中包含 MVC Framework( Model–View–Controller)，簡單來說 View 就是前端畫面呈現 HTML + CSS，Model、Controller 為後端 API 搭建資料庫與控制流程，稍後幾篇文章會再深入的名詞解釋這裡就不多贅述。
![express](https://cdn.tutsplus.com/net/uploads/2013/07/express-retina-preview.jpg)
## Express-Generator 快速建置環境

首先此篇文章會先使用 `Express-Generator` 來自動產生環境，之後再從實作中回頭來一一檢視裡面的運作方式。

### 安裝 Express-Generator

這個指令是 Express 的命令工具，他可以很方便的一鍵初始化整個專案，首先 `npm install -g express-generator` 安裝全域中。

```
npm install -g express-generator
```

安裝完成後可以查看版本是否有安裝成功
```
express --version
```

### 初始化專案

安裝完成後就在桌面來初始化建立專案囉，前端的部分有許多模板引擎，模板引擎（Template Engine）是一個將頁面模板和數據結合起來生成 HTML 的工具，有下列幾個:
- --ejs
- --pug 
- --hbs 
- --hogan

建立與初始化資料夾，後面的專案名稱可自行命名，若你未指定模板引擎會自動預設 jade 模板，更多的資訊你可以使用 `express -h` 下去查詢，初始化完成後在左側資料夾內文件按右鍵開啟終端機。
```
express -f 專案名稱
```

![https://ithelp.ithome.com.tw/upload/images/20171216/20107247InVbimd8e4.png](https://ithelp.ithome.com.tw/upload/images/20171216/20107247InVbimd8e4.png)

## install package

初始化完成後必須使用 `npm install` 或 `yarn install` 來安裝 package.json 內所指定的套件，要安裝什麼套件 express-generator 都自動幫你寫好了，由於這些模組都非常的大所以要透過指令去把他安裝回來，之後會產出一個叫 node_modules 的資料夾，總之你可以把 package.json 檔案想成是一個軟體清單，所有會用到的套件都會列在裡面。

![https://ithelp.ithome.com.tw/upload/images/20171216/20107247wCPwPYnkgW.png](https://ithelp.ithome.com.tw/upload/images/20171216/20107247wCPwPYnkgW.png)

## 解析資料夾內容

#### - Tree

```bash
┌── app.js
├── bin
│   └── www  // 程式進入點
├── package-lock.json
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes  // 路由
│   ├── index.js
│   └── users.js
└── views
    ├── error.jade
    ├── index.jade
    └── layout.jade
```

`bin/www` 是整個程式的進入點，點進去你可以發現他的 port 設為 3000 代表 web server 監聽埠號 3000 port，其他相關的 middleware 例如：body-parser、morgan 以及 router 都寫在 `app.js` 中被 www 啟動時所 import 進去，至於前端畫面是 public 與 views 這兩個資料夾管理，今天我們著重在 router 這部分。

![https://ithelp.ithome.com.tw/upload/images/20171216/20107247OmzkUATXNk.png](https://ithelp.ithome.com.tw/upload/images/20171216/20107247OmzkUATXNk.png)

#### - 解析 routes/index.js

我們在這支檔案下加入 `/test` 路徑並傳送文字 `router.get` 是代表建立一個路由並使用 HTTP request methods 中的 get 形式，HTTP request methods 定義非常多個請求方式，下篇文章中就會來詳細介紹，此外 `router.get`中有兩個參數，第一個是子路徑名稱用單引號字串包起來，第二個是一個方法裡面面有三個參數分別為 req(request)接收資料、res(respond)回傳資料以及next。

```js
// index.js
var express = require('express');
var router = express.Router();

/* GET home page. localhost:3000/ */
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Express' });
});

/* GET localhost:3000/test */
router.get('/test', function(req, res, next) {
  res.send('This is localhost:3000/test')
});

module.exports = router;

```

## 執行

修改檔案後就可以使用 `node ./bin/www` 或 `npm start` 來啟動專案了，至於後者指令為什麼可以啟動，你可以查看 package.json 的檔案裡面的 scripts 有設定好指令相對路徑，所以在 package.json 中你可以依據你的習慣設定你自己專屬的快捷鍵。

![https://ithelp.ithome.com.tw/upload/images/20171216/20107247DQcgCToODQ.png](https://ithelp.ithome.com.tw/upload/images/20171216/20107247DQcgCToODQ.png)

```
// 兩者選一都能啟動程式
node ./bin/www
npm start
```

最後你可以到瀏覽器輸入 `localhost:3000` 與 `localhost:3000/test` 來查看內容。

![https://ithelp.ithome.com.tw/upload/images/20171216/20107247xqpB06QOTO.png](https://ithelp.ithome.com.tw/upload/images/20171216/20107247xqpB06QOTO.png)
![https://ithelp.ithome.com.tw/upload/images/20171216/201072476s14uaZPm2.png](https://ithelp.ithome.com.tw/upload/images/20171216/201072476s14uaZPm2.png)

文章同時發表於：https://andy6804tw.github.io/2017/12/16/express-tutorial/
