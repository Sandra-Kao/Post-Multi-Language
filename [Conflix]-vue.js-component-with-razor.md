
--------------
目錄:

  1. [Home](/Post-Multi-Language.md)
  
  2. [Case Study](/Post-Multi-Language.md#多國語言程式開發案例分享)
  
      1.  [Front-End i18n](/front-end-i18n.md)
    
          1. [Tips, Conflix and Solution](/front-end-i18n.md#tips-conflix-and-solution)
      
          2. [[Conflix] Vue.js component with Razor](%5BConflix%5D-vue.js-component-with-razor.md)
      
      2. [Back End Resource File](/back-end-resource-file.md)
    
          1. [Visual Studio Extension - ResXManager](/back-end-resource-file.md#visual-studio-extension---resxmanager-)

--------------

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
