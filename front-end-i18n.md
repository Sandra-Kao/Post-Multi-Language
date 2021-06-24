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


[Back to Home >](/Post-Multi-Language.md)
