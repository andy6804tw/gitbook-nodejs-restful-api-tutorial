## 本文你將會學到
- 了解 forever 運作原理
- 使用 forever 讓 API 不間斷運行

## forever是什麼？
我們一般運行 Node.js 程式都是執行 npm 來運行程式，為了開發方便延伸出 nodemon 自動重新載入程式，但這都有一個問題就是萬一程式運行中拋出例外掛掉了怎麼辦？因此就有了 forever 讓 Node.js 永不停止的運行即使遇到錯誤崩潰他也能夠及時偵測重新啟動，它的功能包括啟動、停止、重啟我們的 app 應用，使用時機通常是正式產品上架發佈到雲端主機為了怕程式崩潰而導致系統無法正常運作所以才會使用 forever 讓程式不間斷運行。

## 安裝forever

將 forever 安裝在全域環境下方便每次呼叫執行

```bash
yarn add global forever
```

## 基本指令

#### 1. 啟動程式
使用 `forever start [程式位置]` 來執行程式，建立後他會告訴你一個 processing 正在運行中。

```bash
forever start  dist/index.bundle.js
```

![https://ithelp.ithome.com.tw/upload/images/20180117/20107247E5cyC9qJJE.png](https://ithelp.ithome.com.tw/upload/images/20180117/20107247E5cyC9qJJE.png)

在瀏覽器輸入 `http://localhost:3000/` 確實有在運作。

![https://ithelp.ithome.com.tw/upload/images/20180117/20107247QejfTZT4rQ.png](https://ithelp.ithome.com.tw/upload/images/20180117/20107247QejfTZT4rQ.png)

#### 2. 監聽並自動重啟
這個指令是會偵測你的程式若有變動他會馬上重新 reload 並重新執行程式，有點類似 nodemon，其中 w 代表 watch 的意思。

```bash
forever start -w  dist/index.bundle.js
```

#### 3. 顯示所有運行的狀態
在終端機輸入 `forever list` 可以立即查詢程式的運行狀態，並且同時會把運行資訊寫在本機 `/.forever` 資料夾底下的 log 。

```bash
forever list
```

![https://ithelp.ithome.com.tw/upload/images/20180117/20107247DWESEkGhV2.png](https://ithelp.ithome.com.tw/upload/images/20180117/20107247DWESEkGhV2.png)

#### 4. 重新載入程式
forever 不是萬能的也有會掛掉的時候，所以者時就可以 `forever restart [程式位置]` 重新來啟動他。

```bash
forever restart dist/index.bundle.js
```

![https://ithelp.ithome.com.tw/upload/images/20180117/20107247ugbqRS5ZB1.png](https://ithelp.ithome.com.tw/upload/images/20180117/20107247ugbqRS5ZB1.png)

#### 5. 關閉已啓動的程式
若要中斷 forever 運作輸入 `forever stop [程式位置]`，就能立即中止程式執行。

```bash
forever stop dist/index.bundle.js
```

![https://ithelp.ithome.com.tw/upload/images/20180117/20107247diEY5HC78v.png](https://ithelp.ithome.com.tw/upload/images/20180117/20107247diEY5HC78v.png)

#### 6. 關閉所有已啓動的程式
輸入 `forever stopall` 即可停止所有 forever 背景所有的監聽排程。

```bash
forever stopall
```

## 結論
forever 對產品上線時來說是一個很方便的工具，因為即使程式掛掉系統還是能夠維持正常運行，但它並不是萬能的！所以有時候不能太依賴它就曾經發生過程式掛掉後就盪在那的慘案＝（


文章同時發表於：https://andy6804tw.github.io/2018/01/17/api-forever/
