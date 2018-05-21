## 本文你將會學到
- 了解管理 MySQL GUI 有哪些工具
- 下載與安裝 Sequel Pro 或 MySQL Workbench
- 本機與資料庫建立連線

## 有哪些 MySQL GUI 工具
市面上有許多圖像化管理資料庫的軟體像是最傳統的 [phpMyAdmin](https://www.phpmyadmin.net/)、MySQL 自己所推出的 [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)、個人覺得好用但需要付費的 [Navicat](https://www.navicat.com/en/whatsnew) 以及今天要介紹的 [Sequel Pro](http://www.sequelpro.com/)

Sequel Pro 是一款在 mac 上運行 MySQL 資料庫管理的一套圖像化軟體，此外他是開源的所以妳可以免費的使用它，且能夠快速的直接訪問本地和遠程服務器上的MySQL數據庫，那 Windows 的用戶只好安裝 MySQL Workbench 囉。

## macOS 用戶

### 安裝 Sequel Pro

##### 1.下載

首先到[官方](http://www.sequelpro.com/)下載與安裝

![img](https://i.imgur.com/7GtU031.jpg)

##### 2.打開 Sequel Pro 新增連線

打開軟體後我們就建立第一個連線庫吧！請依序地填上連線庫的名稱、主機位置、用戶帳號及密碼，帳號通常預設是 root 密碼就是當時安裝 MySQL 所產生的，主機位置就是自己本機 localhost 也就是 127.0.0.1 ，旁邊的 Test Connection 就是測試看看是否能夠正常連線萬一密碼或設定值輸入錯誤就會發先無法連線的問題哦所以要確認清楚資訊，測試正常連線後點選旁邊的 Save Changes 記住你的登入資訊，最後就 Connect 進入完成連線囉！

![https://ithelp.ithome.com.tw/upload/images/20171229/20107247JzTSXiFjZn.png](https://ithelp.ithome.com.tw/upload/images/20171229/20107247JzTSXiFjZn.png)

## 介紹功能與操作

假如是第一次安裝後打開裡面是空的，這邊我自己建一個簡單的表格向各位說明所有功能，首先紅色框框是選擇你本機端所有的資料庫 Schema 點擊下去第一個選項也可以立即新增一個 Schema ，黃色框框就是你目前的 Schema 有哪些 Table 都會依序陳列在左方最下方為創立資訊，旁邊藍色框框就是你目前 Table 所有欄位設定，在這區域你可以對你的資料表欄位做新增修改移除，右上方綠色框框有非常多功能第一個 Structure 就是你目前資料表的結構，Content 就是你資料表內的所有值組依序地條列出來，Relations 就是你資料庫內的所有關聯，Tiggers 就是你所有資料表的出發程序，Table Info 就是你資料表的一些基本設定像是文字選擇 UTF-8 Unicode ，最後一個 Query 就是可以對你的資料庫做查詢語法。

![https://ithelp.ithome.com.tw/upload/images/20171229/20107247Rpr2BtqUQA.jpg](https://ithelp.ithome.com.tw/upload/images/20171229/20107247Rpr2BtqUQA.jpg)

## Windows 用戶

Windows 用戶請安裝 Workbench。

![https://ithelp.ithome.com.tw/upload/images/20171229/201072475jiBQPPQ07.png](https://ithelp.ithome.com.tw/upload/images/20171229/201072475jiBQPPQ07.png)

文章同時發表於：https://andy6804tw.github.io/2017/12/29/mysql-gui-install/
