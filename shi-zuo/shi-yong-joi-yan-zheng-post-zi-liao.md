## 本文你將會學到
- 了解 joi 是什麼
- 使用 joi 來驗證POST資料

## 前言
相信每個人都有使用過 Facebook 那是否還記得註冊時是否要求你輸入姓名、信箱與密碼呢？當你輸入的資訊不符合資料規範時就會挑出警示且叫你修正，如下圖，這種作法相信在各大網站都會做出類似的檢驗來確保你的資料是否遵循規則而不是亂填，那至於圖片所提到的情況是利用前端的方式用正規表示法(Regular Expression )來做檢驗或是 HTML 的 [input pattern](https://www.w3schools.com/tags/att_input_pattern.asp) 來完成資料的驗證，這邊拋出一個問題，想想看那今天有人使用特別方法破解前端把資料硬塞進去豈不是就功虧一簣了！所以後端這邊還是必須保守最後一道防線，當前端傳送資料進來時使用 `joi` 來做資料正規化的驗證。

![https://ithelp.ithome.com.tw/upload/images/20180107/20107247scNx727oPx.png](https://ithelp.ithome.com.tw/upload/images/20180107/20107247scNx727oPx.png)

## 事前準備
今天要繼續實作的程式是延續 [[Day-27] (實作)User用戶(PUT與DELETE)](https://andy6804tw.github.io/2018/01/03/user-api-tutorial(2)/) 的專案繼續實作，想跟著今天的實作可以先下載下面的整包程式，記得要先 `yarn install` 將整個依賴的軟體安裝回來。

程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V10.0.0

## 什麼是 joi?
相信各位一定不陌生先前文章中有出現過，當時是使用在環境變數的驗證，這邊再拿出來複習一下，joi 是一個資料檢查的機制，你可以自己規範 schema 來限制資料格式。

## 使用 joi 來驗證POST資料

#### 1.安裝 joi

若還沒安裝在 Package 的讀者可以先安裝 joi 至 dependencies。

```bash
yarn add joi
```

#### 2.安裝 express-validation

`express-validation` 是 express.js 的其中一個 middleware ，搭配 joi 使用可以再進入路由前先跑去 middleware 做 joi 的驗證若資料無誤就能進去主路由繼續完成工作。

```bash
yarn add express-validation
```

#### 3. 建立 param-validation.js

請將 `param-validation.js` 建立在 `src > config` 資料夾底下，在這個檔案裡面我們就來分別寫 `User` 和 `Article` 的 joi 規則格式為 JSON，前面是欄位名稱後面是驗證的規範，其中比較特別的是 `article_content` 有限定最少字數，`user_mail` 規定要使用信箱格式，最後 `user_password` 是使用正規表示法來定義密碼格式。

```js
// param-validation.js
import Joi from 'joi';

export default {
  // POST /api/article
  createArticle: {
    body: {
      user_id: Joi.number().required(), // 數字＋必填
      article_title: Joi.string().required(), // 字串＋必填
      article_tag: Joi.string().required(), // 字串＋必填
      article_content: Joi.string().min(20).required() // 文章長度至少20字
    }
  },
  // POST /api/user
  createUser: {
    body: {
      user_name: Joi.string().required(), // 字串＋必填
      user_mail: Joi.string().email().trim().required(), // 限定email格式並移除多餘空白
      user_password: Joi.string().regex(/[a-zA-Z0-9]{6,30}$/).required() // 最小長度6最大30，只允許英文大小寫和數字
    }
  }
};
```

#### 4. 在各路由中的 POST 放入 joi middleware
分別在兩個路由(Article、User)的POST中放入 joi 驗證，其中這邊是利用 express 的 middleware 來完成，首先引入 `express-validation`，此外在路由中間放入 `validate()` 中間就是放入你的 joi 驗證的 schema 規則，整個 API 的流程是會先進入 middleware 做 joi 的驗證若有誤後端在 console.log() 會拋出例外訊息，若無誤就會進入 `controller` 繼續寫入資料庫 `module`。

- article.route.js

![https://ithelp.ithome.com.tw/upload/images/20180107/20107247IkZshgTD2X.png](https://ithelp.ithome.com.tw/upload/images/20180107/20107247IkZshgTD2X.png)

- user.route.js

![https://ithelp.ithome.com.tw/upload/images/20180107/20107247UAVtrrTpQV.png](https://ithelp.ithome.com.tw/upload/images/20180107/20107247UAVtrrTpQV.png)

## 測試

- 文章(Article) POST

將程式碼 `yarn build` 再 `yarn start` 後開啟 Postman 在網址列輸入 `localhost:3000/api/article` 並選擇 POST 請求方式，最後放入要寫入的 JSON 格式(故意將 `article_content` 少於20字)。

```json
{
    "user_id": 1,
    "article_title": "Node.js教學",
    "article_tag": "後端",
    "article_content": "歡迎來到此篇教學。"
}
```

可以發現圖中紅色圈起處拋出一個 joi 的錯誤裡面寫到，`article_content` 至少要20個字元。

![https://ithelp.ithome.com.tw/upload/images/20180107/20107247aBXbZrcGB0.png](https://ithelp.ithome.com.tw/upload/images/20180107/20107247aBXbZrcGB0.png)

- 用戶(User) POST

程式碼執行後一樣在 Postman 的網址列輸入 `localhost:3000/api/user` 並選擇 POST 請求方式，最後放入要寫入的 JSON 格式(故意將 `user_mail` 輸入一般字串以及 `user_password` 輸入少於6個字元)。

```json
{
	"user_name":"Andy10",
	"user_mail":"andy",
	"user_password":"0000"
}
```

可以發現圖中紅色圈起處拋出一個 joi 的錯誤提示，內容是說 `user_mail` 並黑一個合法的 email 格式和 `user_password` 不符合正規表示法的規範。

![https://ithelp.ithome.com.tw/upload/images/20180107/201072470cXHRXni8S.png](https://ithelp.ithome.com.tw/upload/images/20180107/201072470cXHRXni8S.png)


範例程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V11.0.0

文章同時發表於：https://andy6804tw.github.io/2018/01/07/post-joi/
