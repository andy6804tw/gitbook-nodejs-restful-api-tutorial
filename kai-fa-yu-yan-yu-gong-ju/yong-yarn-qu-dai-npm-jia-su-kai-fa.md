## 何謂 Yarn
[Yarn](https://yarnpkg.com/zh-Hans/) 是一個新的 package 管理器，它替代了 npm 客戶機或其他包管理器的現有工作流，同時保持與 npm 註冊表的兼容性。它具有與現有工作流程相同的功能集，同時運行速度更快，更安全，更可靠，簡單來說用 Yarn 來安裝套件比起 npm 更來得快速！因此我們秉持著學以致用的精神，本系列文章也將全使用 Yarn 來做管理開發。

![yarn](https://yarnpkg.com/assets/og_image.png)

Yarn 是 Facebook 自家團隊與 Exponent、 Google、Tilde 所合作開發的套件管理工具，由於程式套件隨著團隊的規模茁壯，他們在安全性和效能面臨一大考驗，所以他們團隊自己打造全新的解決方案，以一種更加可靠的方式來管理依賴，Yarn 因此就誕生了，它作為 npm 客戶端的替代器，更加快速、可靠、安全。

## Yarn 的運做模式

從[官方](https://code.facebook.com/posts/1840075619545360/Yarn-a-new-package-manager-for-javascript/)的說明文件當中可得知分為三步驟：

- 解析(Resolution)：Yarn首先開始解析依賴包(package.json中的dependencies)然後向註冊表(暫存倉庫)發出請求，並遞迴查詢各層依賴。
- 獲取(Fetching)：接下來，Yarn 會在一個全域的緩存目錄中查找當前所需的包是不是曾經已被下載過了如果還沒有，Yarn 會把這個包的壓縮包拉下來，並把它存放在全域緩存中(global cache)，這樣它下次就可以離線安裝了，無需重複下載。依賴包(package.json)也可以以 tarball 的形式存放到版本控制系統中，以實現完全的離線安裝。
- 鏈接(Linking)：最後，Yarn 會把所需的所有文件從緩存中復製到本機的    node_modules 目錄中，這樣所有東西就鏈接為一個整體了。

## 其他功能

除了安裝變得更加快速和可靠以外，Yarn 還提了如下特性，進一步簡化了依賴管理的工作流程：
- 同时兼容 npm 和 Bower 工作流，支持混用多種註冊表類型。
- 可以限制依赖包的授權類型，並且可以輸出依赖包的授權訊息。
- 暴露一個稳定的 JS API，提供抽象化的日誌訊息(log)在於編譯環境。
- 提供可讀的、最小化的、美觀的 CLI `(英：command-line interface ， 中：命令介面)` 輸出信息。

## 如何安裝

#### macOS用戶
macOS 的用戶要透過 brew 來安裝 yarn，Homebrew 是一款自由及開放原始碼的軟體套件管理系統，用以簡化 Mac OS X系統上的軟體安裝過程。

`apt-get` 是 Linux 上的一個重要的工具，很多軟件的安裝、卸載、更新都會用到它。Homebrew 就是 Mac 上的 `apt-get`。 但是，目前 Mac 上默認是沒有這個工具的。

##### 1. 安裝 Homebrew
這是 [Homebrew](https://brew.sh/) 的官網，想知道詳細內容可以去瞧瞧這裡就不多闡述

開啟終端機輸入以下指令 Install Homebrew
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
若已經安裝過了檢查更新一下，保持最新狀態
```
brew update
```
>ps. 安裝 Homebrew 前先確認是否有安裝 Xcode 若有請先去更新它，因為 Homebrew 是用 Ruby 攥寫並且需要在有 Ruby 環境下使用，然而安裝 Xcode 時會自帶 Ruby 所以 Xcode 也要保持最新狀態

##### 2. 安裝 Yarn

```
brew install yarn
```

若你的電腦本身安裝 Node.js 了可執行下面指令。

```
brew install yarn --without-node
```

若安裝後日後有更新 Yarn 會在命令端提醒警示，這時你可以使用 Homebrew 來完成更新。

```
brew upgrade yarn
```

#### Windows用戶
Windows 用戶安裝方法非常簡單，直接利用 npm 就能裝並且安裝於全域中(global)。

```
npm install yarn --g
```

安裝結束後來測試是否安裝成功！
```
yarn --version
```

## npm 與 Yarn 指令比較

| 回傳值         | 方法名稱          | 說明             |
|---------------|------------------|----------------|
|npm install	 |  yarn install |安裝 json.package 所有依賴
|npm install [package]	| (N/A)	| Yarn不支援直接安裝套件
|npm install --save [package] |	yarn add [paakage] |儲存在 json.package中的dependencies
|npm install --save-dev [package] |	yarn add [paakage] --dev |儲存在 json.package中的devDependencies
|npm install --global [package] |	yarn global add [package] |安裝在電腦全域中
|npm uninstall [package]	|(N/A)|Yarn不支援直接安裝與移除套件
|npm uninstall --save [package]	|yarn remove [package]|移除dependencies某套件
|npm uninstall --save-dev [package]	|yarn remove [package]|移除devDependencies某套件
|rm -rf node_modules && npm install	|yarn upgrade |更新node_modules

這邊列出最常見以及我最常用的指令，若要看更多請看[這裡](https://yarnpkg.com/en/docs/migrating-from-npm)

[Yarn GitHub](https://github.com/yarnpkg/yarn)

文章同時發表於：https://andy6804tw.github.io/2017/12/15/Yarn-tutorial/
