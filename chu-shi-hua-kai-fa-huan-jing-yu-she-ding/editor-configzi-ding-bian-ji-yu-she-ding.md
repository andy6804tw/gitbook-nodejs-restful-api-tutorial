## 前言
在團隊開發中勢必要有一個寫 code 規範來應付日漸膨脹的專案，除非你是單打獨鬥，保持的個人統一的規格，畢竟人多手雜每個人的開發環境與習慣都不太一樣，使用的編輯器也五花八門，像是今年很流行的 [Visual Studio Code](https://code.visualstudio.com/) 或是 [Sublime Text](https://www.sublimetext.com/) 與 [Atom](https://atom.io/)，你永遠不確定你的開發團隊善於哪個 IDE 雖然團隊有硬性制定一個明文的規範，但若是規範上百條的標準時豈不是要慢慢閱讀與檢查嗎？

![img](https://www.masterzendframework.com/images/posts/consistent-editing-with-editorconfig.jpg)
[圖片來源](https://www.masterzendframework.com/consistent-editing-with-editorconfig/)

## 介紹 Editor Config

若有以上問題這時 Editor Config 就是大家統一格式的好插件，Editor Config 可以橫跨許多 IDE 編輯器你只要在你的專案資料夾中加入 `.editorconfig` 你可以很快的開始設定專案中檔案的風格，包含像是縮排、tab 的寬度以及 EOL 字元，只要編輯器安裝此插件認得 `.editorconfig` 這支檔案就會自動套用了。

`.editorconfig` 是一個 INI 格式的檔案，是由 section 跟 properties 組成的設定格式，下列來做個名詞解釋：

- section 作用域
  - 是被套用的檔案路徑跟副檔名，例如.py .jc .java 格式檔
  - 舉例來說若要指定專案目錄底下的所有 .js 檔與 .py 檔可以輸入 `[*.{js,py}]`

- properties 屬性值
  - 簡單來說就是規範值，下面舉兩個例子
  - indent_style：tab為hard-tabs，space為soft-tabs
  - insert_final_newline：設為true表示文件以一個換行結尾，false反之。

## 支援的 IDE

- JetBrain’s IDEs, including PhpStorm, and 
- WebStorm
- BBEdit
- Atom
- Sublime Text
- GitHub
- Emacs & Vim
- Brackets
- Coda
- Eclipse & NetBeans
- gEdit, jEdit, & Notepad++
- textmate
- Visual Studio
- Xcode

## 安裝插件
這邊用 Visual Studio Code 來做示範，到擴充插件地方搜尋edit config 下載這兩個，第一個是讓你 IDE 可以讀取到 `.editorconfig` 檔，第二個是 `.editorconfig` 檔的產生器在專案目資料夾下按下預設熱鍵 (Ctrl + Shift + P or Cmd + Shift + P) 系統會在資料夾建立此檔案

![https://ithelp.ithome.com.tw/upload/images/20171225/20107247w3bwLOYDad.png](https://ithelp.ithome.com.tw/upload/images/20171225/20107247w3bwLOYDad.png)

## 自定義規範
以下是我的 `.editorconfig` ，各位可以參考看看

```
# http://editorconfig.org
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

# Use 4 spaces for the Python files
[*.py]
indent_size = 4
max_line_length = 80

# The JSON files contain newlines inconsistently
[*.json]
insert_final_newline = ignore

# Minified JavaScript files shouldn't be changed
[**.min.js]
indent_style = ignore
insert_final_newline = ignore

# Makefiles always use tabs for indentation
[Makefile]
indent_style = tab

# Batch files use tabs for indentation
[*.bat]
indent_style = tab

[*.md]
trim_trailing_whitespace = false
```

最後官方也有提供更多的說明與設定技巧有興趣可以去琢磨一下
- [EditorConfig](http://editorconfig.org/)
- [EditorConfig Properties](https://github.com/editorconfig/editorconfig/wiki/EditorConfig-Properties)
- [Projects Using EditorConfig](https://github.com/editorconfig/editorconfig/wiki/Projects-Using-EditorConfig)


文章同時發表於：https://andy6804tw.github.io/2017/12/25/EditorConfig-plugin/