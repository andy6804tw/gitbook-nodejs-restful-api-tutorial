## 介紹 Visual Studio Code
打造一個方便的開發環境，為什麼我會選擇它呢？原因在於 Visual Studio Code 有強大的編輯功能，因為是開源的專案所以更新速度頻繁擴充套件的資源也很豐富，而且內建終端機與版本控制整個開發過程在同一個視窗就能完成。市面上的編輯器有很多例如： [Visual Studio Code](https://code.visualstudio.com/)、[Sublime Text](https://www.sublimetext.com/)、[Atom](https://atom.io/)、[vim](https://vim.sourceforge.io/download.php)、[Notepad++](https://notepad-plus-plus.org/zh/) ......等，各位可以依據自己的喜好安裝一個自己適合的編輯環境。

Visual Studio Code 由 2015 年微軟所開發的一個開源軟體，它同時支援 Windows、Linux 和 macOS 作業系統的開源文字編輯器。它支援偵錯，內建了Git 版本控制功能，同時也具有開發環境功能，例如代碼補全、代碼片段、代碼重構等。


## 安裝
Visual Studio Code 多種作業系統首先到[官網](https://code.visualstudio.com/)下載安裝，此外若有遇到 bug 你可以到他們的 [GitHub](https://github.com/Microsoft/vscode/) 提交 issues 就會很快地被處理囉！當然也可以許願，最近看到 Atom 更新了[遠端共筆](https://teletype.atom.io/) (Code together in real time with Teletype) 的功能，近期也有人在 VS Code issues 上許願希望這功能可以趕快出來一定方便，說個題外話聽說終端機 (Terminal) 功能就是台灣人上去許願出來的。

![https://ithelp.ithome.com.tw/upload/images/20171212/20107247Y9iCjYilpp.png](https://ithelp.ithome.com.tw/upload/images/20171212/20107247Y9iCjYilpp.png)

## 環境設定
#### 1. Path安裝code指令
這個指令設定是結合電腦內建的終端機，在終端機輸入 `code .` 就會自動幫你把資料夾專案開啟，首先在鍵盤按下 `command + shift + p` 再輸入 path 點選第一個就設定完成囉！之後你就可以在終端機移入你要開啟的資料夾再鍵入 `code .` 系統就會自動幫你開啟該目錄專案在 VS Code 上了。

![https://ithelp.ithome.com.tw/upload/images/20171212/20107247D5WmgkONkP.png](https://ithelp.ithome.com.tw/upload/images/20171212/20107247D5WmgkONkP.png)

#### 2. config設定
在畫面左上角點選 `喜好設定 => 設定` 或是點選快速鍵 `command + ,` 也能快速叫出設定檔，開啟之後如下圖，左邊為全部的設定參數查詢，若有需要更改可以點選左邊的一支筆做編輯，此時右邊的畫面就是你自己客製化的設定檔了，他使以 json 格式做編輯，在這邊你可以依據你喜好填入你的設定值，下面我也分享我自己的設定可以直接貼上，其中最推薦 autoSave 他會自動幫你儲存檔案不需再手動的存檔，以及 formatOnPaste 當你複製貼上網路上的程式碼時難免會跑版格式，此設定就是幫你貼上時自動排版你的程式碼。

![https://ithelp.ithome.com.tw/upload/images/20171212/20107247v41Nj2iS3g.png](https://ithelp.ithome.com.tw/upload/images/20171212/20107247v41Nj2iS3g.png)

```js
{
    "workbench.iconTheme": "vscode-icons", // 要先下載vscode-icons套件(後面會提到)
    "editor.fontSize": 13, // 字體大小
    "editor.tabSize": 2, // 一個tab的空白間隔
    "files.autoSave": "afterDelay", // 自動儲存檔案
    "editor.formatOnPaste": true, // 貼上程式碼時會自動幫你排版
    "files.insertFinalNewline": true // 儲存檔案時在其結尾插入最後一個新行
}
```

## 擴充套件推薦
這邊介紹幾個實用的擴充插件：
- EditConfig
  - 團隊自定義編輯環境格式的插件
- ESLint
  - 編輯器會自動幫你檢查 coding style，需搭配 `.eslintrc` 檔
- Git Lens
  - 版控紀錄，一目了然誰在什麼時間點修改檔案
- Path intellisense
  - 輸入 `/` 編輯器會自動查詢該目錄底下建議路徑
- Preview on Web Server
  - 前端開發時預覽的好幫手
- vscode-icons
  - 幫你 VS Code 檔案與資料夾 icon 美化

![https://ithelp.ithome.com.tw/upload/images/20171212/20107247ERjjnCYeWV.png](https://ithelp.ithome.com.tw/upload/images/20171212/20107247ERjjnCYeWV.png)

#### vscode-icons 啟用
這邊先講 vscode-icons 如何設定，其餘插件可以先安裝好，後面文章會逐一教你如何使用，vscode-icons 下載後請選擇上方工具列 `前往 => 命令選擇區` 或是鍵盤按下 `command + shift + p` 輸入 `icon` 並點選第一個命令啟用。

![https://ithelp.ithome.com.tw/upload/images/20171212/201072476L6pMwnLKP.png](https://ithelp.ithome.com.tw/upload/images/20171212/201072476L6pMwnLKP.png)

![https://ithelp.ithome.com.tw/upload/images/20171212/20107247D5tjUkUP6s.png](https://ithelp.ithome.com.tw/upload/images/20171212/20107247D5tjUkUP6s.png)


文章同時發表於：https://andy6804tw.github.io/2017/12/12/vscode-tutorial/