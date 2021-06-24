# Visual Studio Extension - ResXManager <img src="https://tomenglert.gallerycdn.vsassets.io/extensions/tomenglert/resxmanager/1.53.4233.0/1620293971563/Microsoft.VisualStudio.Services.Icons.Default" alt="ResXManager" width="40" height="40" border=".1" />

## Abstract

專案中對於多國語言程式開發( Internationalization, i18n )在不同團隊有不同的做法，最簡單二分法分類是前端/後端渲染的翻譯。
前後端分工的效能已直以來爭吵不休，都各有定論 ，沒有說一定是哪一種方式比較優秀，端站自己專案和團隊開發者順手的程度而定。

#### Client-Side-Rendering (CSR) 前端渲染
在前端框架(Vue.js, React.js, Angular.js ...)和前後端分離觀念盛行後，Single-Page-Application (SPA) 帶領了前端翻譯技術的進步。
透過前端畫面存取預先載入的靜態格式多國語翻譯文件(json, yaml ...)，利用前端渲染在容器上指定的 tag 位置。

#### Server-Side-Rendering (SSR) 後端渲染
後端翻譯的做法盛行已久，不同的程式架構也許有各式各樣做法的衍生。
透過伺服器存取翻譯文件(DB, Json, Api ...)，並將所有頁面資訊連同翻譯資料送回用戶請求端。


值得注意的是，有時候其實可以前後端部份混用，(雖然理想上不建議，但沒有一個長久運行維護下的專案是理想的)，但也要小心挑選的工具。
由某CEO分享的前後端搭配不協調的[案例](https://www.topsinfosolutions.com/blog/server-side-rendering-boost-performance-user-experience/ "暗指 React.js 較 Angular.js 能配合自己的後端選染")。

## 多國語言程式開發案例分享
我自己手上的專案中做多國語的方式有兩種，前端 i18n 跟 後端 Resource File。

#### 前端 i18n
有些相對靜態(或說單純)的頁面或專案，非常適合用前端技術實作。
只要換上相對應的文案內容到指定位置即可。

我目前手上的專案是用 Vue.js 開發，共同或重複的各種版型的容器，只要寫一次就能無限重複利用。
既然是前端專案，當然會選用前端多國語技術選染文字啦。
這個專案是用跟 Vue.js 互相配合的 [Vue-i18n](https://kazupon.github.io/vue-i18n/introduction.html "Vue-i18n 的官方網站")，

只要在畫面上 ``` @import``` Vue-i18n，搭配指定形式 tag ```$t{ }```，就能做到輸入 ```$t{"login"}``` 變成 ```登入```。
這部份各大前端框架已經說很多了，只要關鍵字搜尋 "Vue.js i18n" 就不多贅述。

而維護的文檔可能會長這樣。

![image](https://user-images.githubusercontent.com/63223781/123192965-7e2e8580-d4d6-11eb-9c82-e4301ab9eeff.png)
![image](https://user-images.githubusercontent.com/63223781/123188523-bfbb3280-d4ce-11eb-8763-58bb1ac8baea.png)

#### 後端 Resource File
我手上的另個專案是選用 .Net MVC + Vue.js 開發，頁面要做多國語的時候是選用類似 [MVCL pattern](https://webocreation.com/blog/code-flow-request-response-mvcl-pattern-opencart/ "MVCL pattern 出自 OpenCart 一書") 的架構，以 MVC Resource File 的形式處理字串，前端就用 Razor 選染文字。

