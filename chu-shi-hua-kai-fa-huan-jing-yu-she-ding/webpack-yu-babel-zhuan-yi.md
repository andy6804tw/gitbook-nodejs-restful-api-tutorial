## 事前準備
今天要繼續實作的程式是延續 [[Day-12] 深入浅出 ESLint 與實作](https://ithelp.ithome.com.tw/articles/10193060) 的專案繼續實作，想跟著今天的實作可以先下載下面的整包程式，記得要先 yarn install 將整個依賴的軟體安裝回來。

程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V1.0

## 什麼是 Webpack ?
[Webpack](https://zh.wikipedia.org/wiki/Webpack) 是一個開源的打包工具。Webpack 提供了開發缺乏的模組化開發方式，將各種靜態資源視為模組，並從它生成優化過的程式碼。 Webpack 可以從終端、或是更改 webpack.config.js 來設定各項功能。 要使用 Webpack 前須先安裝 [Node.js](https://nodejs.org/en/)。

下圖是官方所提供的流程圖，Webpack 可以載入你所需要的 loader 並將這些打包在一起例如 js、css 只要有安裝 loader 解析器和設定好路徑就能輕鬆打包了。

![webpack](https://webpack.github.io/assets/what-is-webpack.png)

[圖片來源](https://webpack.github.io/)

## Webpack 與 Grunt 和 Gulp
其實這些東西類似不過還是有區別的不能與 Webpack 混為一體，原因是 Webpack 是將你的各種 assets 打包在一起，形成模組，而後兩者就是 Task Runner，你可以在 build process 中建立很多的任務。這篇[文章](https://survivejs.com/webpack/appendices/comparison/)分別介紹各種打包工具有興趣可以看看，寫得非常清楚。

## 使用教學

#### 1. 建立新資料夾並初始化專案
首先我們先利用 `yarn init -y` 初始化資料夾將會產出 `package.json` 檔，這支檔案是掌管整個轉案的檔案所有資訊包括使用什麼套件都詳細記錄在這邊。

```
yarn init -y
```
由於我是下載最新版本的 node.js 所以他有黃字警告我，版本可能不相容但沒關係若有問題還是可以用 `npm` 去代替操作，若還沒下載的朋友建議勸下載穩定版的 node.js。

![https://ithelp.ithome.com.tw/upload/images/20171223/20107247xjvbteHwzK.png](https://ithelp.ithome.com.tw/upload/images/20171223/20107247xjvbteHwzK.png)

#### 2. 安裝 Webpack 與 babel

這邊要下載這些套件，babel 的作用就是將你的程式轉換為瀏覽器所看的懂的語法，雖然 ES6 出了一陣子了但各家瀏覽器所資源的程度都不一所以目前還是要用babel來轉譯。

- webpack
- webpack-node-externals
- babel-preset-env 
- babel-plugin-transform-object-rest-spread
- babel-core
- babel-loader 

下列兩道指令我把 webpack 和 babel 分開安裝一方面好閱讀也好理解，安裝後再到 `package.json` 檢查看有沒有沒全部安裝完成，最後你會發現資料夾多了， `node_modules` 的資料夾安裝的套件都會集中在這裡。

```
yarn add -D webpack webpack-node-externals

yarn add -D babel-preset-env babel-plugin-transform-object-rest-spread babel-core babel-loader 
```



#### 3. 建立設定檔
安裝完成後我們就來新增設定檔指令打包路徑，首先建立一個 `webpack.config.js` 的檔案將以下程式碼貼上，這裡來稍微解說一下程式容。

- entry
  - 為你的程式進入點
- output 分為三個參數
  - path： 也就是打包後的路徑，這邊設定會產出一個 dist 資料夾，打包後的東西就儲存在這裡
  - filename: 打包後的檔名，這邊設定只產出一個檔案名為 `[name].bundle.js` ，其中這裡的 `[name]` 來自於 entry 的 `index` 名字會同步，當然你也可以自行命名
  - libraryTarget: 這邊使用 commonjs2 的解析，bundle 最終會以 module.exports 導出整個bundle模塊
- module
  - 這邊就是設定你用了哪些 babel 解析器與相關規則設定

```js
/* webpack.config.js ： Webpack 的設定檔 */

const nodeExternals = require('webpack-node-externals');
const path = require('path');

module.exports = {
  target: 'node',
  externals: [nodeExternals()],
  entry: {
    'index': './src/index.js',
  },
  output: {
    path: path.join(__dirname, 'dist'),
    filename: '[name].bundle.js',
    libraryTarget: 'commonjs2',
  },
  module: {   //設定你的檔案選項
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: 'babel-loader'
      },
    ],
  },
}
```

#### 4.建立快捷鍵

在 `package.json` 中有個參數設定叫 `scripts` 他是設定專案執行的快捷鍵，修改 package.json 中加入指令。
```js
"scripts": {
    "build": "webpack -w",
    "build:prod": "webpack -p",
    "start": "nodemon dist/index.bundle.js"
  }
```
使用方法：
```
yarn build
yarn build:prod
yarn start
```

當然你要手動打雙引號內的指令也行，因為你鍵入 `yarn build` 他會自動幫你檢查是否有 build 的 script 並執行 `webpack -w`，簡單來說 `package.json` 的 `scripts` 就是幫你的指令簡化並作代號呼叫執行。

#### 5.建立一個檔案並測試

到這邊環境都建置完成啦～接下來就來測試，首先來建立一個 src 的資料夾並新增 `index.js` 的檔案，可以用其他名字嗎？答案是不行還記得先前 `webpack.config.js` 設定進入點嗎，當時就是指定 index 這支檔案並且在 src 目錄下，除非你改名兩邊要同步才行哦！

這支檔案各位應該不陌生前幾篇文章有出現過 XD

```js
//透過http模組啟動web server服務
const http = require('http')

const server = http.createServer(function (req, res) {
  //設定回應為text文件，並回應 Hello World!
  res.writeHead(200, { 'Content-Type': 'text/plain' })
  res.end('Hello World!')
})

//設定服務監聽localhost:3000(127.0.0.1/:3000)
server.listen('3000', function () {
  console.log('server start on 3000 port')
})

```

完成後就來真正測試囉～

第一步： 先鍵入 `yarn build` ，這個動作會啟動 `webpack -w` w 代表的是 watch 就是值持續監聽有變動時會同步更新，看見綠綠一片恭喜你成功囉！

![https://ithelp.ithome.com.tw/upload/images/20171223/20107247nSvRmxOzfA.png](https://ithelp.ithome.com.tw/upload/images/20171223/20107247nSvRmxOzfA.png)

第二步： 使用 Visual Studio Code 的使用者可以在終端機 ＋ 新增另一個終端機(原本的不用關)，並鍵入 `yarn start`，這個動作會啟動 `nodemon dist/index.bundle.js` 也就是執行打包後的檔案囉！ 若不知道或還沒安裝 nodemon 的朋友請先看看[下一篇](https://ithelp.ithome.com.tw/articles/10193307)文章裡面有安裝教學。

![https://ithelp.ithome.com.tw/upload/images/20171223/201072470VSg20CiK2.png](https://ithelp.ithome.com.tw/upload/images/20171223/201072470VSg20CiK2.png)
 
 成功後會發現 conelog 出 `server start on 3000 port` ，這時就開啟瀏覽器輸入 `localhost:3000` 來看看結果囉！

![https://ithelp.ithome.com.tw/upload/images/20171223/201072476gCWbmOEjI.png](https://ithelp.ithome.com.tw/upload/images/20171223/201072476gCWbmOEjI.png)

## 結語
最後各位可能有個疑問那就是 `build:prod` 是什麼還沒用到欸？ 這個指令是跟 `build:prod` 一樣差別在於壓縮，各位可以試試看會發現喘出來的 `index.bundle` 變成只有一行而且檔案確實也變小了，這道指令適合在開發成產品成產品時來使用。

![https://ithelp.ithome.com.tw/upload/images/20171223/20107247zyf0MszTmH.png](https://ithelp.ithome.com.tw/upload/images/20171223/20107247zyf0MszTmH.png)

範例程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V2.0.0

文章同時發表於：https://andy6804tw.github.io/2017/12/23/webpack-tutorial/
