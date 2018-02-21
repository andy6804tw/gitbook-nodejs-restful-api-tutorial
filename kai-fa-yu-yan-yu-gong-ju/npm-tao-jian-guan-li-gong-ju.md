## 何謂 npm
npm 全名為 Node Package Manager，是 Node.js 的套件（package）管理工具，npm 可以讓 Node.js 的開發者，直接利用、擴充線上的第三方套件庫（packages registry），加速軟體專案的開發。

![npm](https://juststickers.in/wp-content/uploads/2014/08/NPM.jpg)

這邊舉個例子假如我想使用 Google 的 Firebase 第三方函式庫，直接在終端機輸入 `npm install firebase` npm 就會直接幫你建好 Firebase 的環境了，如下：

```
npm install firebase
```

#### 1. 安裝 npm

安裝 Node.js 會自動內建 npm，所以還沒安裝 Node.js 的讀者可以參考上一篇內容。

若要檢查 Node.js 是否正確安裝在你本機中，可以在終端機輸入以下的指令：

```
node -v
```

若要檢查 npm 是否正確安裝在你本機中，可以在終端機輸入以下的指令：

```
npm -v
```

#### 2. 初始化專案

首先在你本機目錄下新增一個空的資料夾，再用 Visual Studio Code 打開資料夾與內建終端機

![https://ithelp.ithome.com.tw/upload/images/20171214/20107247kaQKlTLvrJ.png](https://ithelp.ithome.com.tw/upload/images/20171214/20107247kaQKlTLvrJ.png)

再來就是初始化你的專案囉 `npm init -y` ， -y 的意思就是省略一些提問快速初始化，若還是不了解可以用 `npm init` 試試就知道了！ 

```
npm init -y
```

![https://ithelp.ithome.com.tw/upload/images/20171214/20107247j1baeZ1Qn6.png](https://ithelp.ithome.com.tw/upload/images/20171214/20107247j1baeZ1Qn6.png)

初始化完成後你會發現資料夾多了一個叫 package.json 的檔案，它是一種 CommonJS 規定用來描述包的文件，是一個包含 json 格式的說明文件，裡面可以定義相依的相關套件以及應用程式的資訊，簡單來說這隻檔案裡面會存你安裝什麼套件以及一些相關程式設定，你把這檔案分享給別人他再 `npm install` 就會把你原本所安裝的套件安裝回來了，下篇文章再介紹各位另一個取代 npm 的好工具，筆者目前開發中也經常使用，它叫 yarn。


文章同時發表於：https://andy6804tw.github.io/2017/12/14/npm-tutorial/

 
