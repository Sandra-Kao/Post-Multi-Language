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



### [Conflix] Vue.js component with Razor
在一個 MVC + Vue.js 的專案架構下，就會出現前端渲染的技術混用或是技術衝突的情形。在 HTML 上遇到 Razor 跟 Vue.js 打架的時候，這時候身為開發者難道只能選邊站嗎?

## Introduction
在 Vue.js 中是以 template 定義 component 的 HTML。
``` javascript
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})
```
但在 ``` template: ``` 中只支援 JavaScript 語法，而無法塞入 Razor 語法糖做多國語翻譯。![image](https://user-images.githubusercontent.com/63223781/123211203-b1344180-d4f5-11eb-90e5-bda55593f408.png)

## Method
為了要讓2種前端技術可以好好相處，所以這邊建議可以改寫一下 Vue.js 的 template，將 js 的部分 跟 HTML 的拆開維護。
1. js 寫在 js 檔裡面
2. js 的 template 寫在 HTML，這邊需要做3件事。
  2-1. 以 ``` <script></script> ```標籤包住 HTML
  2-2. 給予指定 ```id="pagination-wrapper"```
  2-3. 標記類型為type="text/x-template"
``` javascript
// js
  template: `#pagination-wrapper`
```

``` HTML
<!-- MVC HTML -->
  <script type="text/x-template" id="pagination-wrapper">
        <div class="pagination-wrapper clearfix">
            <div class="pagination">
                <ul>
                    <li :class="{ disabled : isCssPreArrowDisabled }">
                        <a @@click.prevent="onClickGoToPrePage()"><i class="far fa-chevron-left"></i></a>
                    </li>
                    <li v-for="page in paginate" :class="{ active : isCssPaginateActive(page), disabled : isCssPaginateDisabled(page) }">
                        <a @@click.prevent="onClickPaginate">{{ isPaginateNan(page) }}</a>
                    </li>
                    <li :class="{ disabled : isCssNextArrowDisabled }">
                        <a @@click.prevent="onClickGoToNextPage()"><i class="far fa-chevron-right"></i></a>
                    </li>
                </ul>
            </div>
            <div class="page-input" v-if="isShowGoToPageInput">
                <input type="number" v-model="inputPageIndex" @@change="onChangePaginate()">
                <span><a @@click.prevent="onChangePaginate()">Go</a></span>
            </div>
        </div>
    </script>
```
## [Back to Home >](/Post-Multi-Language.md)
