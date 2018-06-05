## 本文你將會學到
- 了解 Google Cloud Platform 
- 開通一年的$300美元試用額度帳戶

## 前言
Google Cloud Platform 簡稱寫為 GCP，在日後文章內容都以 GCP 縮寫來表示，GCP 是 Google 推出的雲端平台服務，並且提供的300美元試用額度試用期限為一年，並且提供多項服務，包含運算（Compute）、儲存裝置（Store）、大數據（Big Data）、API、機器學習（Ｍachine Learning）、運用與工具（Management Tools）等類別的重要服務，重點是免費試用所有功能聽到這邊是不是有點心動呢？

## 類似的服務
用過 AWS 與 GCP 差異比較的的是，GCP 在台灣設有主機資料中心，在連線品質上相對的比較穩定，另外在計費上也不太相同，用起來 GCP 會比較省一點(ps.可能每個人使用習慣不同計費也不同)，不過在 GCP 使用上你用量越多續用時會給你比較多的折扣，詳細的可以參閱 GCP 的[計費](https://cloud.google.com/pricing/?hl=zh-tw)方式。

- 亞馬遜(AWS)
- 微軟(Azure)
- 甲骨文(Oracle)
- Rackspace

## 一覽 GCP 所有服務
GCP的服務主要分為以下幾類。

![img](https://i0.wp.com/markoinsights.com/wp-content/uploads/2016/11/understanding-cloud-with-google-cloud-platform-20-1024.jpg?w=1024)

[圖片來源](http://markoinsights.com/2016/11/11/google-cloud-update/)

## Data Center & Cloud Regions
這幾年 Google 也積極的建立 Data Center 像這幾年在台灣的彰濱工業區也設立了一個亞洲區的資料中心，不必再辛苦的去跟其他區域共用也拖慢了速度，這也算是一個使用 GCP 的誘因，目前在全球設立據點分為北美洲、南美洲、歐洲、亞洲與澳洲，當然若你想省錢可以選擇離你越遠的主機位置相對地連線效能就會降低，若想了解更多的可以看[官方](https://cloud.google.com/compute/docs/regions-zones/?hl=zh_TW&_ga=2.238227972.-583342444.1512617592#available)詳細說明裡面還有個地區主機的規格可以參考。

- North America
  - Council Bluffs, Iowa, USA(*4)
  - The Dalles, Oregon, USA(*3)
  - Ashburn, Virginia, USA(*3)
  - Moncks Corner, South Carolina, USA(*3)
- South America
  - São Paulo, Brazil(*3)
- Europe
  - St. Ghislain, Belgium(*3)
  - London, U.K.(*3)
  - Frankfurt, Germany(*3)
- Asia
  - Mumbai, India(*3)
  - Jurong West, Singapore(*3)
  - 台灣彰化(*3)
  - Tokyo, Japan(*3)
- Astralia
  - Sydney, Australia(*3)

## 申請免費試用
申請時會先要你選擇填選地區，之後會要在你填入帳戶類型、稅務資訊、地址與金融卡或信用卡卡號，這些都為必填，放心在適用的期間都不會被扣到帳戶裡任何一毛錢，一年後適用期結束也不會自動幫你扣款而是會先幫你停用目前的主機，雖然說是一年300美元任你試用但還是有些[限制](https://cloud.google.com/free/docs/always-free-usage-limits)。

![https://ithelp.ithome.com.tw/upload/images/20180118/20107247bHPZhUA4Vc.png](https://ithelp.ithome.com.tw/upload/images/20180118/20107247bHPZhUA4Vc.png)


![https://ithelp.ithome.com.tw/upload/images/20180118/20107247iLpkRiDyVc.png](https://ithelp.ithome.com.tw/upload/images/20180118/20107247iLpkRiDyVc.png)

## 結論
題外話 Google 自家的 Firebase 也推出 hosting 的服務，也可以很簡單的方式把靜態網頁部屬到到 Firebase 上，並且能夠擁有 https 加密協定，甚至還可以綁定自己的網址，只能說 Google 太強大了！總之天下沒有白吃的午餐若 GCP 的試用期到了還是得乖乖付錢囉。

文章同時發表於：https://andy6804tw.github.io/2018/01/18/gcp-tutorial(1)/