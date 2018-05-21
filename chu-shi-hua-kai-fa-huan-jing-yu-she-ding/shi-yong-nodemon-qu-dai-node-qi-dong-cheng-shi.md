## 什麼是 nodemon？
在我們開發 node.js 時執行程式碼必須都要使用 node 指令來執行程式碼例如：`node index.js` ，但是如果你今天正在開發階段必須一直修修改改並且頻繁地測試內容，豈不是要一直重複著些指令嗎？從今天開始你可以使用 nodemon 的自動化 reload 幫你省去這些不必要麻煩的動作！

[官方](https://nodemon.io/)是這麼解釋的 nodemon 是一個公用程序，它會監視你的程式碼有無的任何更改並自動重新啟動服務，這時只要刷新你的瀏覽器就能看到改動，此外 nodemon 使用 npm 進行安裝，只需使用 nodemon 取代 node 執行你的程式碼，就能輕鬆的開發 node.js。

![nodemon](https://camo.githubusercontent.com/fd1ea21338ceeef34920e44e97d099f3c47a78c3/687474703a2f2f6e6f64656d6f6e2e696f2f6e6f64656d6f6e2e737667)

## nodemon 功能
- 自動重啟應用程式
- 持續偵測你的預設程式
- 默認支持 node＆coffeescript，但是易於運行任何可執行文件（比如python，make等）
- 可以忽略特定文件或目錄
- 觀察指定的目錄資料夾
- 與服務器應用程序或一次運行公用程序和 REPLs 一起使用
- 可在 node 中被存取使用
- 有完整的開源碼分享在 [GitHub](https://github.com/remy/nodemon#nodemon) 上

## 安裝
nodemon 使用 npm 進行安裝當然用 yarn 也可以，你可以安裝在全域也可以安裝在專案的 devDependencies 本機目錄中，以下指令，兩者挑一即可，作者是習慣把常用的安裝一次在全域中，所以會挑選第一種方法。

- 使用 npm 安裝

1. 安裝於全域

```
npm install nodemon -g  
```
2. 安裝於專案資料夾中

```
npm install --save-dev nodemon 
```

- 使用 yarn 安裝

1. 安裝於全域

```
yarn global add nodemon
```
2. 安裝於專案資料夾中

```
yarn add -D nodemon 
```


## 使用
新增一個檔案名為 `index.js` 在裡面可以先隨便寫個 console.log() 好測試，原本執行檔案輸入指令 `node index.js` 現在只要改成 nodemon 即可。

```
nodemon index.js
```

其實你輸入 `nodemon` 也會執行 index.js 這支檔案，因為它會自動抓取預設路徑，但你今天取別的名字時就要根據檔名去執行它囉。

![https://ithelp.ithome.com.tw/upload/images/20171223/201072470FUlksBye3.png](https://ithelp.ithome.com.tw/upload/images/20171223/201072470FUlksBye3.png)

若檔案變動會自動重啟，這時網頁重新整理就會立即看出結果，如果你覺得手動去刷新網頁這個動作也是多餘的太麻煩你可以試試搭配 `gulp-webserver` 來刷新你的網頁，可以參考這個 [GitHub](https://github.com/andy6804tw/gulp_tutorial) 教學。

![https://ithelp.ithome.com.tw/upload/images/20171223/20107247GwpP2UZprk.png](https://ithelp.ithome.com.tw/upload/images/20171223/20107247GwpP2UZprk.png)


文章同時發表於：https://andy6804tw.github.io/2017/12/24/nodemon-tutorial/