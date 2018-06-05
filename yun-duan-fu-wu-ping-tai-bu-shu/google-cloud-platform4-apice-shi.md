## 本文你將會學到
- 使用 git 將專案引入到 VM 虛擬機中
- 在 VM 上測試執行API

## 前言
昨天已經將 Cloud SQL 部署完成了，今天就來驗收整個成果吧！

## 執行VM個體
在左邊的選單目錄中進入 `Compute Engine > VM執行個體`，進入後點選 `在瀏覽器視窗中開啟`。

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247Z8teYwtZhp.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247Z8teYwtZhp.png)

#### 1. clone 專案至 VM

>若先前已經 clone 此專案的讀者可以直接跳到步驟二

將專案 `git clone` 下來，之後進入該專案資料夾，進入後再輸入 `npm install` 把node_modules下載回來，基本上就是這三步驟將 GitHub 上的專案移下載至 VM 中。

```bash
#把專案下載到VM
git clone https://github.com/andy6804tw/RESTful_API_start_kit.git
#進入專案資料夾
cd RESTful_API_start_kit
#把node_modules下載回來
npm install
```

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247wlqFYjIzRR.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247wlqFYjIzRR.png)

#### 2.進入主分支

>步驟一完成的讀者可以直接跳到步驟三

若先前已 clone 此專案的讀者，先進入該專案底下的資料夾，之後再進入 `master` 主分支，隨後鍵入 `npm install` 確保所有的 node.js 套件已安裝。

```bash
cd RESTful_API_start_kit
git checkout master
npm install
```

#### 3. 建立 dotenv 環境變數
我們使用 linux 指令中的 `cp` 將一個環境變數 `.example.env` 範本複製一份新的並命名為 `.env`

```bash
cp .example.env .env
```

#### 4. 修改 `.env` 內容
使用 vim 編輯模式進入 `.env` 隱藏檔裡，把 `MYSQL_HOST` 修改成自己 GCP 中雲端資料庫(Cloud SQL) 所提供的連線 IP 位址。

```bash
vim .env
```

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247D6Fmf5SGwy.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247D6Fmf5SGwy.png)
![https://ithelp.ithome.com.tw/upload/images/20180120/20107247rkuE8DBwUg.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247rkuE8DBwUg.png)

#### 5. deploy 專案並執行
使用 `webpack` 後會自己產生一個 dist 資料夾，最後再鍵入 `npm run start` 來執行它。

```bash
webpack
npm run start
```

執行成功後在瀏覽器輸入 `[外部 IP]:3000/api/article`

![https://ithelp.ithome.com.tw/upload/images/20180120/20107247v3Tjk70Rla.png](https://ithelp.ithome.com.tw/upload/images/20180120/20107247v3Tjk70Rla.png)

## 結語
雲端服務的設定大約到這部分，其實 GCP 裡面有非常多的東西可以玩，可以慢慢地摸索，若各位想了解更多我有機會可以多寫。


文章同時發表於：https://andy6804tw.github.io/2018/01/21/gcp-tutorial(4)/