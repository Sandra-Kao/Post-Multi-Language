
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


### [專案2] 後端 Resource File
我手上的另個是 .Net MVC + Vue.js 專案，頁面要做多國語的時候是選用類似 [MVCL pattern](https://webocreation.com/blog/code-flow-request-response-mvcl-pattern-opencart/ "出自 OpenCart 一書") 的架構，以 [MVC Resource File](https://www.ryadel.com/en/setup-a-multi-language-website-using-asp-net-mvc/ "Set up Resource File") 的形式[儲存和處理字串](https://www.c-sharpcorner.com/article/asp-net-mvc-using-resource-files-to-manage-string-constants/ "MS 官方文件")，前端就用 @Razor 語法糖選染文字。

#### MVC Resource File
這是 Resource File 檔案打開之後的樣子，就像一份 DB table，
只是每個頁面，每個語系，分別都是不同的table。

![image](https://user-images.githubusercontent.com/63223781/123208613-066e5400-d4f2-11eb-9777-1052a2c11ebe.png)

#### HTML
以 Razor 渲染 Resource File 儲存的文字

![image](https://user-images.githubusercontent.com/63223781/123196843-35c69600-d4dd-11eb-8425-e2a373a5ad13.png)


### 插件推薦
#### Visual Studio Extension - ResXManager <img src="https://tomenglert.gallerycdn.vsassets.io/extensions/tomenglert/resxmanager/1.53.4233.0/1620293971563/Microsoft.VisualStudio.Services.Icons.Default" alt="ResXManager" width="20" height="20" border=".1" />

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
這樣就可以先把 HTML 文字洞挖好，然後隨時可以提供 User Excel檔。只要翻譯完，就算只有部分翻譯，也成馬上匯入上線！



## [Back to Home >](/Post-Multi-Language.md)
