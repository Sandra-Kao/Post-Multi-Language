# Visual Studio Extension - ResXManager <img src="https://tomenglert.gallerycdn.vsassets.io/extensions/tomenglert/resxmanager/1.53.4233.0/1620293971563/Microsoft.VisualStudio.Services.Icons.Default" alt="ResXManager" width="40" height="40" border=".1" />

## Abstract

專案中對於多國語言程式開發( Internationalization, i18n )在不同團隊有不同的做法，最簡單二分法分類是前端/後端渲染的翻譯。
前後端分工的效能已直以來爭吵不休，都各有定論 ，沒有說一定是哪一種方式比較優秀，端站自己專案和團隊開發者順手的程度而定。

### Client-Side-Rendering (CSR) 前端渲染
在前端框架(Vue.js, React.js, Angular.js ...)和前後端分離觀念盛行後，Single-Page-Application (SPA) 帶領了前端翻譯技術的進步。
透過前端畫面存取預先載入的靜態格式多國語翻譯文件(json, yaml ...)，利用前端渲染在容器上指定的 tag 位置。

### Server-Side-Rendering (SSR) 後端渲染
後端翻譯的做法盛行已久，不同的程式架構也許有各式各樣做法的衍生。
透過伺服器存取翻譯文件(DB, Json, Api ...)，並將所有頁面資訊連同翻譯資料送回用戶請求端。


值得注意的是，有時候其實可以前後端部份混用，(雖然理想上不建議，但沒有一個長久運行維護下的專案是理想的)，但也要小心挑選的工具。
由某CEO分享的前後端搭配不協調的[案例](https://www.topsinfosolutions.com/blog/server-side-rendering-boost-performance-user-experience/ "暗指 React.js 較 Angular.js 能配合自己的後端選染")。

## 多國語言程式開發案例分享
我自己手上的專案中做多國語的方式有兩種，前端 i18n 跟 後端 Resource File。

### [專案1] 前端 i18n
有些相對靜態(或說單純)的頁面或專案，非常適合用前端技術實作。
只要換上相對應的文案內容到指定位置即可。

我目前手上的專案是用 Vue.js 開發，共同或重複的各種版型的容器，只要寫一次就能無限重複利用。
既然是前端專案，當然會選用前端多國語技術選染文字啦。
這個專案是用跟 Vue.js 互相配合的 [Vue-i18n](https://kazupon.github.io/vue-i18n/introduction.html "Vue-i18n 的官方網站")，

只要在畫面上 ``` @import``` Vue-i18n，搭配指定形式 tag ```$t{ }```，就能做到輸入

```HTML javascript
<div id="app">
  <p>{{ $t("member.login") }}</p>
</div>
``` 

變成 
```HTML
<div id="app">
  <p>登入</p>
</div>
``` 

這部份各大前端框架已經說很多了，只要關鍵字搜尋 "Vue.js i18n" 就不多贅述。

而維護的文檔可能會長這樣。

![image](https://user-images.githubusercontent.com/63223781/123192965-7e2e8580-d4d6-11eb-9c82-e4301ab9eeff.png)
![image](https://user-images.githubusercontent.com/63223781/123188523-bfbb3280-d4ce-11eb-8763-58bb1ac8baea.png)

### [專案2] 後端 Resource File
我手上的另個是 .Net MVC + Vue.js 專案，頁面要做多國語的時候是選用類似 [MVCL pattern](https://webocreation.com/blog/code-flow-request-response-mvcl-pattern-opencart/ "出自 OpenCart 一書") 的架構，以 [MVC Resource File](https://www.ryadel.com/en/setup-a-multi-language-website-using-asp-net-mvc/ "Set up Resource File") 的形式[儲存和處理字串](https://www.c-sharpcorner.com/article/asp-net-mvc-using-resource-files-to-manage-string-constants/ "MS 官方文件")，前端就用 @Razor 語法糖選染文字。

#### MVC Resource File
這是 Resource File 檔案打開之後的樣子，就像一份 DB table，
只是每個頁面，每個語系，分別都是不同的table。

![image](https://user-images.githubusercontent.com/63223781/123197236-d1580680-d4dd-11eb-80f2-6729a703c12c.png)

如果你的網站有5個語系，有8頁要翻譯，就會有 5 * 8 = 共 40 個 Resource File 翻譯檔要維護。
操作起來需要一筆筆 key in，會有點辛苦。
所以這邊推薦大家如果也是用 Resource File 做翻譯的話，可以安裝 [ResXManager](https://marketplace.visualstudio.com/items?itemName=TomEnglert.ResXManager "下載位置")
插件。
這個插件的評價一直都滿好的，使用的這幾年來也會隨著 Visual Studio 不斷的版更，還不錯。

![image](https://user-images.githubusercontent.com/63223781/123197748-8c809f80-d4de-11eb-8ee1-df5a50c4fc3f.png)
安裝之後，就能在專案裡面用 ResXManager 來打開剛剛的 Resource File table。

![image](https://user-images.githubusercontent.com/63223781/123197998-f8630800-d4de-11eb-9452-352dc7c3408a.png)

編號1區塊，會協助你做各翻譯檔的篩選。
編號2區塊，就會統整篩選結果，而且會一次呈現出所有的語言對照，不需要每個語言各別打開。
值得一提的是，
可以看到編號3，他還可以讓你匯出/匯入整份 Excel，
  
![image](https://user-images.githubusercontent.com/63223781/123197949-e1bcb100-d4de-11eb-9788-35bdb8eb580b.png)

這樣就可以先把 HTML 文字洞挖好，然後隨時可以提供 User Excel檔。只要翻譯完，就算只有部分翻譯，也成馬上匯入上線！



#### HTML
以 Razor 渲染 Resource File 儲存的文字

![image](https://user-images.githubusercontent.com/63223781/123196843-35c69600-d4dd-11eb-8425-e2a373a5ad13.png)




