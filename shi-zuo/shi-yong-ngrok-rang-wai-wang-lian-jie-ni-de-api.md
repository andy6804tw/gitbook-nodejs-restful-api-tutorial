## 本文你將會學到
- ngrok運作方式與操作
- 本機分享端口(Port)


## 前言
自己在本機開發時往往需要線上測試 API 或畫面是否能正常連動，或是你的客戶以及開發夥伴需要觀看測試，如何讓所有人連接到我本機的 localhost:3000 呢？以前作法可能是自己申請一個主機然後將所有資料上雲端，但又還沒正式上線不是就多此一舉了還必須額外負擔主機費用，雖然有免費的但每次都要上雲端這個動作也很麻煩，我這邊就分享兩個解決方法。

#### 方法一(在相同內網情況下分享)

方法第一種是利用區網(此方法限定對方和你同時連上同一個網域)，適用的人像是跟你同時在同一個地方的工作夥伴，只要確保對方和你同時連上相同的區網就可以囉！

首先查詢你的電腦 ip 位置， windows 使用者開啟終端機輸入 `ipconfig` 即可查詢你目前 ip 位置，macOS 的使用者可以打開網路偏好設定裡面就有 ip 位置了。

- [ip位置]：[Port]

舉例：
> 192.123.45.6:3000

![https://ithelp.ithome.com.tw/upload/images/20180116/20107247a9689Ds91Y.png](https://ithelp.ithome.com.tw/upload/images/20180116/20107247a9689Ds91Y.png)


#### 方法二(使用第三方軟體 ngrok)

ngrok 做為一個轉發的伺服器，他可以把外界的請求轉發到你指定的 Port，使用的背景原理是連接到 [ngrok](https://ngrok.com/product) 雲端伺服器，將你本機指定的地址公開，再將由 ngrok 一串公開的網址來存取內容。他的優點是快速而且還提供了 https 的服務讓你使用上更安全，甚至你還可以設置密碼保護。

![img](https://ngrok.com/static/img/demo.png)

### 安裝

官方文件與[載點](https://ngrok.com/download)

- windows 用戶

  到官方網站中對應的位元版本下載解壓縮後直接啟動 `ngrok.exe` 即可在終端機上打指令執行，例如啟動並監聽 8080 Port。

  ```bash
  ngrok http 8080
  ```

- macOS 用戶

  有兩種方法可以安裝：

  ##### 1. 官網下載解壓縮包

    使用指令解壓縮
  
  ```bash
  unzip /path/to/ngrok.zip  
  ```

    要在端口 8080 上啟動HTTP通道，請運行下面的命令：

  ```bash
  ./ngrok http 8080
  ```

  ##### 2. 使用 Homebrew 來安裝

    這個方法也是我推薦的，原因是他會直接幫你安裝在全域中，每次執行不用到指定資料夾下執行，就好比 `npm install --global` 一樣，若以下指令無法安裝請在最前面加上 `sudo` 管理者權限下安裝。

  ```bash
  brew cask install ngrok
  ```

   要在端口 8080 上啟動HTTP通道，請運行下面的命令：

  ```bash
  ngrok http 8080
  ```

![https://ithelp.ithome.com.tw/upload/images/20180116/20107247Ov8aV2DDP1.png](https://ithelp.ithome.com.tw/upload/images/20180116/20107247Ov8aV2DDP1.png)

文章同時發表於：https://andy6804tw.github.io/2018/01/16/ngrok-intro/