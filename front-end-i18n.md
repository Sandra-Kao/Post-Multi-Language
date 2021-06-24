### [專案1] 前端 i18n

有些相對靜態(或說單純)的頁面或專案，非常適合用前端技術實作。
只要換上相對應的文案內容到指定位置即可。

我目前手上的專案是用 Vue.js 開發，共同或重複的各種版型的容器，只要寫一次就能無限重複利用。

既然這個專案是前端專案，當然會選用前端多國語技術啦

這邊使用跟 Vue.js 互相配合的 [Vue-i18n](https://kazupon.github.io/vue-i18n/introduction.html "Vue-i18n 的官方網站")套件渲染文字。

### Vue-i18n

只要在畫面上 ``` @import``` Vue-i18n，搭配指定形式 tag ```$t{ }```，就能做到

輸入

```HTML javascript
<div id="app">
  <p>{{ $t("member.login") }}</p>
</div>
``` 

執行輸出變成 
```HTML
<div id="app">
  <p>登入</p>
</div>
``` 

這部份各大前端框架已經說很多了，只要關鍵字搜尋 "Vue.js i18n" 就可以找到很多文章，這邊不多贅述。

而維護的文檔可能會長這樣。
英文

![image](https://user-images.githubusercontent.com/63223781/123192965-7e2e8580-d4d6-11eb-9c82-e4301ab9eeff.png)

繁中

![image](https://user-images.githubusercontent.com/63223781/123188523-bfbb3280-d4ce-11eb-8763-58bb1ac8baea.png)

----------------

### Tips, Conflix and Solution
1. 在 MVC 中使用 Vue.js 的語法縮寫的時候，可以將 ``` v-click="method1" ``` 寫成 ``` @@="method1" ```，原本官方文件事只給一個 @，但在 MVC 上 @ 會跟 Razor 衝突。
2. 使用 Vue.js 的 component 撰寫 HTML 無法引用 Razor 的衝突，[詳細說明和解法](/[Conflix]-vue.js-component-with-razor.md)。

## [Back to Home >](/Post-Multi-Language.md)
