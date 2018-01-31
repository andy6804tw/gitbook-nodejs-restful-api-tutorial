# 從無到有，打造一個漂亮乾淨俐落的 RESTful API 

## 前言

哈囉大家好～今年是我第一次參與鐵人賽活動，想藉由這次機會，將我在這一年所學貢獻出來，和大家一起學習，此外為何我會選擇這個主題呢？主要原因是在工作實習部分負責 Node.js API 的撰寫，在這一年中學習到許多新知所以想就由這次鐵人賽寫出一系列網頁後端教學，帶給想進入網頁後端但不知如何下手的人，在 30 天的文章中我會從最基礎的編輯器推薦、語言選擇、環境建置、框架介紹、自動化部署、資料庫架設、到一個簡單的部落格貼文 API 範例實作，若時間允許的話還會介紹Google Cloud Platform 伺服器的架設，內容看似很多很豐富但這也是給我自己一個挑戰，最後希望帶給各位讀著滿滿的 大 收 穫！

## 此系列文章適合誰?

- 了解 JavaScript 是什麼的人(不熟也沒關係)
- 有聽過 Node.js 但不太熟悉做方式
- 想快速開發一個漂亮的 API
- 知道 MySQL 是什麼

## 系列文章內容

- 開發環境建置
- Node.js 介紹
- JavaScript 介紹
- MVC 框架與 REST 名詞介紹
- 選用 Express 做為框架
- 以簡單例子實作 API
- 資料庫架設(MySQL)
- API 測試與發布

## 開發環境
- Visual Studio Code (建議)

需要準備的工具有 [Visual Studio Code](https://code.visualstudio.com/) 當然你也可以用你熟悉的開發環境例如 ： [Sublime](https://www.sublimetext.com/) 、 [Atom](https://atom.io/)、[Vim](http://www.vim.org/)。

## 寫作格式
本系列文章使用了以下的風格作為撰寫風格:

##### 1. 採 Airbnb 寫作風格
Airbnb 開發團隊在撰寫 JavaScript 部分規定了大量的寫作風格與規範並開源給各位使用，所以作者在開發上也採取這套規範。
##### 2. 駝峰式命名法
- 小駝峰式命名法（lower camel case）：
  
  第一個單字以小寫字母開始，第二個單字的首字母大寫，例如：firstName、lastName。


## 歡迎交流

這系列文章同時會發布在我的[部落格](https://andy6804tw.github.io/)

由於文章都是趁下班時間寫，所以內容難免有錯別字，如果對於文中有任何疑慮或有錯誤也歡迎指正，互相學習～


## 關於作者（Author）

[@andy6804tw](https://github.com/andy6804tw)

## 版權許可（License）

本著作係採用[創用 CC 姓名標示-非商業性-相同方式分享 4.0 國際 授權條款](http://creativecommons.org/licenses/by-nc-sa/4.0/)授權.

![](https://kdchang.gitbooks.io/react101/content/cc-by-nc-sa.png)

本授權條款允許使用者重製、散布、傳輸以及修改著作，但不得為商業目的之使用。若使用者修改該著作時，僅得依本授權條款或與本授權條款類似者來散布該衍生作品。使用時必須按照著作人指定的方式表彰其姓名。



## 關鍵字（Keywords）

Node.js

