## 何謂 ESLint ?
ESLint 支援 ES6 與 JSX 語法，具高度設定彈性與擴充性的檢查語法工具，可提供程式開發者在語法上的錯誤警告，此篇教學我所使用的是 Airbnb 的規範，簡單來說 ESLint 就是可以規範整個開發團隊中的 coding style。

![eslint](https://es6.io/images/eslint.png)![airbnb](https://a0.muscache.com/airbnb/static/logos/belo-200x200-4d851c5b28f61931bf1df28dd15e60ef.png)

## 事前準備
還沒安裝的朋友可以先去看以下連結的教學哦！
- 安裝 Visual Studio Code
  - [[Day-2] 安裝 Visual Studio Code 與擴充套件設定](https://ithelp.ithome.com.tw/articles/10191357)
- 安裝 Node.js
  - [[Day-3] Node.js 入門介紹](https://ithelp.ithome.com.tw/articles/10191513)

需要準備的工具有 [Visual Studio Code](https://code.visualstudio.com/) 當然你也可以用你熟悉的開發環境例如 ： [Sublime Text](https://www.sublimetext.com/)、[Atom](https://atom.io/)、[Vim](https://vim.sourceforge.io/download.php)、[Notepad++](https://notepad-plus-plus.org/zh/) ......等。

## 教學

有安裝 yarn 的朋友也可以利用 yarn 來安裝順便練習看看~

#### 1. 初始化node
```bash
 npm init -y
```
這邊會產出一個package.json,這個檔案專門管理node的各種套件

#### 2. 安裝eslint與babel-eslint 
```bash
 npm install eslint babel-eslint --save-dev
```

#### 3. 使用 eslint-airbnb-base
這邊可以參考至 [Airbnb](es6+的eslint-rules) 的GitHub
```bash
 npm install eslint-config-airbnb-base eslint-plugin-import eslint --save-dev
```

#### 4. 建立 `.eslintrc` 檔案並貼上下列程式
```js
{
  "parser": "babel-eslint", //parser: 指的是剖析器，如果你有用babel編譯器，就是設定"babel-eslint"
  "env": {
    "browser": true,
    "node": true
  },
  "extends": "airbnb-base",
  "rules": {
    "semi": [2, "never"],
    "arrow-body-style": ["error", "always"],
    "comma-dangle": ["error", "never"], //該規則強制使用對象和數組文字中的逗號
    "no-console": 0 //關掉console.log()錯誤
  }
}
```
#### 5. 安裝擴充套件

接下來使用 Visual Studio Code 的看過來，請記得到擴充套件內下載 ESLint 的擴充套件才會即時顯示錯誤哦很重要！他主要是會去讀取你剛建立的 `.eslintrc` 檔案若沒安裝這個擴充套件也沒有用，原生系統不會去吃這隻檔案，若使用其他編輯器的使用者也可以到該應用程式下的擴充功能找下載基本上都會有支援像是 [Sublime Text](https://www.sublimetext.com/) 以及 [Atom](https://atom.io/) 都能找到。

![https://ithelp.ithome.com.tw/upload/images/20171222/20107247alrrCQuVLm.png](https://ithelp.ithome.com.tw/upload/images/20171222/20107247alrrCQuVLm.png)

## 結果

最後你可以發現你的程式碼出現紅紅的底線囉！他代表你的程式碼不符合規範哦叫你馬上修正，你可以按下左邊燈泡點選 Fix all 它會一次幫你修正所有對問題，是不是很方便～此外最下面終端機中點選問題可以詳細知道所有的問題，例如要空白、結尾不能有分號、最後一行要換行......等，懶得看也沒關係，他只是提醒你某行程式碼寫這樣不符合規範，程式碼還是可以執行滴別緊張。

![https://ithelp.ithome.com.tw/upload/images/20171222/20107247ODuObnUceE.png](https://ithelp.ithome.com.tw/upload/images/20171222/20107247ODuObnUceE.png)
![https://ithelp.ithome.com.tw/upload/images/20171222/20107247cgMDBG0QTv.png](https://ithelp.ithome.com.tw/upload/images/20171222/20107247cgMDBG0QTv.png)


最後附上程式碼你可以 clone 下來再 `npn install` 或 `yarn install` 就可以執行囉！看過喜歡的話按顆星星讓我知道你～哈 [Source Code](https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V1.0)

裡面分別有兩隻 js 檔 `index.js` 是錯誤並且跳出警示的寫法，`correct.js` 是依照規範修改後正確的寫法你可以相對照看看。


文章同時發表於：https://andy6804tw.github.io/2017/12/22/ESLint-tutorial/

