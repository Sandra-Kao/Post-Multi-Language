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
我自己手上的專案中做多國語的方式有兩種，前端 i18n 跟 後端 Resource。

#### 前端 i18n
有些相對靜態的頁面或專案，非常適合用前端技術實作，共同或重複的各種版型的容器，只要提換上相對峙的內容到指定位置即可。
![image](https://user-images.githubusercontent.com/63223781/123188266-51767000-d4ce-11eb-85ac-ac2ba9eaac70.png)
![image](https://user-images.githubusercontent.com/63223781/123188523-bfbb3280-d4ce-11eb-8763-58bb1ac8baea.png)




