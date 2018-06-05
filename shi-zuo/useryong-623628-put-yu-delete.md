## 本文你將會學到
- 如何修改資料庫一筆用戶資料
- 如何刪除資料庫一筆用戶資料
- 使用Postman測試PUT與DELETE

## 前言
這篇文章是 User 的第二部份實作修改和刪除，這幾天的內容比較複雜也許會比較難吸收若還是不了解的讀者歡迎在底下留言問題，我會很樂意地幫你解答哦！

## 事前準備
今天要繼續實作的程式是延續 [[Day-26] (實作)User用戶(GET與POST)](https://ithelp.ithome.com.tw/articles/10196004) 的專案繼續實作，想跟著今天的實作可以先下載下面的整包程式，記得要先 `yarn install` 將整個依賴的軟體安裝回來。

程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V9.0.0

## 修改user

#### user.module.js

傳入值 `insertValues` 是使用者要修改的資料為一個物件 Object 型態，這個變數是由 `user.controller.js` 傳過來的，此外旁邊多了一個 `userId` 這個就是你要修改的 id 用在 WHERE 語句供修改哪筆資料。

```js
// user.module.js
...略
/* User PUT 修改 */
const modifyUser = (insertValues, userId) => {
  return new Promise((resolve, reject) => {
    connectionPool.getConnection((connectionError, connection) => { // 資料庫連線
      if (connectionError) {
        reject(connectionError); // 若連線有問題回傳錯誤
      } else { // User資料表修改指定id一筆資料
        connection.query('UPDATE User SET ? WHERE user_id = ?', [insertValues, userId], (error, result) => {
          if (error) {
            console.error('SQL error: ', error);// 寫入資料庫有問題時回傳錯誤
            reject(error);
          } else if (result.affectedRows === 0) { // 寫入時發現無該筆資料
            resolve('請確認修改Id！');
          } else if (result.message.match('Changed: 1')) { // 寫入成功
            resolve('資料修改成功');
          } else {
            resolve('資料無異動');
          }
          connection.release();
        });
      }
    });
  });
};
...略
```

#### user.controller.js
`user_id` 為要被修改的用戶 id，這邊使用 `req.params` 方式將網址上的 id 參數讀取下來(例如:http://127.0.0.1:3000/api/user/1 )後面的1代表就是你要修改的 id 值。

```js
// user.controller.js
import userModule from '../modules/user.module';
...略
/* User PUT 修改 */
const userPut = (req, res) => {
  // 取得修改id
  const userId = req.params.user_id;
  // 取得修改參數
  const insertValues = req.body;
  userModule.modifyUser(insertValues, userId).then((result) => {
    res.send(result); // 回傳修改成功訊息
  }).catch((err) => { return res.send(err); }); // 失敗回傳錯誤訊息
};
...略
```

#### user.route.js
路由檔案就是要指定你的路徑，因為是修改所以使用 put 請求，此外你會發現他的路徑跟 GET 與 POST 不一樣，原因我們必須要在 api 網址上取得修改的 id 當然你也可以利用 `req.body` 傳遞參數取得 id 值。

```js
// user.route.js
import userCtrl from '../controllers/user.controller';
...略
/** 修改 User 值組 */
router.route('/:user_id').put(userCtrl.userPut);
...略
```

#### PUT測試
將程式碼 `yarn build` 再 `yarn start` 後，開啟Postman在網址列輸入 `http://127.0.0.1:3000/api/user/1` 並選擇 PUT 請求方式，接下來是要放入修改的內容，`Body > raw > 選擇 JSON(application/json)`，將所有要修改的資料寫成 JSON 格式在下面空白處如下圖，最後再點選 Send 送出，修改成功後會有成功的字串，此時代表你成功了修改資料庫的內容，若你輸入的id有誤下面訊息也會提供你錯誤的線索像是查無此id。

```json
{
	"user_id":1,
	"user_name":"10程式中",
	"user_mail":"andy@gmail.com",
	"user_password":"1010"
}
```

![https://ithelp.ithome.com.tw/upload/images/20180106/201072472YR3r6mrpv.png](https://ithelp.ithome.com.tw/upload/images/20180106/201072472YR3r6mrpv.png)
![https://ithelp.ithome.com.tw/upload/images/20180106/20107247bKwv3lsTkC.png](https://ithelp.ithome.com.tw/upload/images/20180106/20107247bKwv3lsTkC.png)


## 刪除user

#### user.module.js
刪除作法也跟修改差不多也是要有傳入 id 名為 userId 的參數，使用 `DELETE` 刪除資料表 user 內的某一筆值組。

```js
// user.module.js
...略
/* User  DELETE 刪除 */
const deleteUser = (userId) => {
  return new Promise((resolve, reject) => {
    connectionPool.getConnection((connectionError, connection) => { // 資料庫連線
      if (connectionError) {
        reject(connectionError); // 若連線有問題回傳錯誤
      } else { // User資料表刪除指定id一筆資料
        connection.query('DELETE FROM User WHERE user_id = ?', userId, (error, result) => {
          if (error) {
            console.error('SQL error: ', error);// 資料庫存取有問題時回傳錯誤
            reject(error);
          } else if (result.affectedRows === 1) {
            resolve('刪除成功！');
          } else {
            resolve('刪除失敗！');
          }
          connection.release();
        });
      }
    });
  });
};
...略
```

#### user.controller.js
這邊主要是接收刪除的 id 利用 `req.params.user_id` 儲存到變數 `userId` 中，最後再丟入 module 內的 `deleteuser` 刪除函式執行的帶回傳。

```js
// user.controller.js
import userModule from '../modules/user.module';
...略
/* User  DELETE 刪除 */
const userDelete = (req, res) => {
  // 取得刪除id
  const userId = req.params.user_id;
  userModule.deleteUser(userId).then((result) => {
    res.send(result); // 回傳刪除成功訊息
  }).catch((err) => { return res.send(err); }); // 失敗回傳錯誤訊息
};
...略
```

#### user.route.js
加上刪除的路徑並使用 `delete` 請求方式，跟修改的路徑一樣。

```js
import userCtrl from '../controllers/user.controller';

...略
router.route('/:user_id')
  .put(userCtrl.userPut) /** 修改 User 值組 */
  .delete(userCtrl.userDelete); /** 刪除 User 值組 */

export default router;
```

#### 刪除測試
將程式碼 `yarn build` 再 `yarn start` 後，開啟Postman在網址列輸入 `http://127.0.0.1:3000/api/user/1` 並選擇 DELETE 請求方式，完成後按下 Send 送出後即可發現有刪除成功訊息。

![https://ithelp.ithome.com.tw/upload/images/20180106/20107247vzX272W3BG.png](https://ithelp.ithome.com.tw/upload/images/20180106/20107247vzX272W3BG.png)


範例程式碼：https://github.com/andy6804tw/RESTful_API_start_kit/releases/tag/V10.0.0

文章同時發表於：https://andy6804tw.github.io/2018/01/06/user-api-tutorial(2)/
