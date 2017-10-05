# Day 03 - Update CSS Variables with JavaScript

利用 CSS3 變數指定圖片的內邊距、模糊度和背景顏色，就可讓 JavaScript 透過更新 CSS 變數值，動態更改樣式。

## 涉及觀念

* `:root`: 用以選擇根元素 (i.e. `html`)
* `--var`: 特殊屬性名稱，用以定義 CSS 變數
* `var(--name)`：CSS 方法，用以取得變數值
* `filter: blur(??px)`：套用 CSS 模糊濾鏡
* `input` 事件: 輸入值變更中和確定變更都會觸發
* `dataset`：元素所定義的 `data-` 屬性，會收集在這個 map 中
* `HtmlElement.style.setProperty(name, value)`：用來更改 CSS 變數值

## 實作過程

### CSS 部分

1. 宣告 CSS 變數

    > 變數必須宣告在某個元素底下，定義在 `:root` 就變成全域變數

2. 使用 CSS 變數作為屬性值

### JS 部分

1. 取得頁面的 `input` 元素
2. 監聽每個 `input` 元素的輸入事件，一旦輸入變更，就更新相對應的 CSS 變數值
3. 事件處理函數中，要注意數字有時需要加上 'px' 單位才是合法 CSS 屬性值

## 基礎知識

1. `NodeList` 和 `Array` 的區別

    可以觀察 `prototype` 中所定義的方法。`NodeList` 僅有 `forEach()`、`keys()`、`values` 少數方法；`Array` 提供的方法較多，像是 `map()`、`push()`...

2. HTML5 自行定義的 data 屬性

    HTML5 可以為元素添加自行定義的屬性，只要使用 `data-` 作為屬性名稱的前綴詞。在 JavaScript 中，就可以透過元素的 `dataset` 屬性來取得 name-value 配對。

3. CSS 變數

    這是 CSS3 新提出的規格，目前只有 IE11 不支援，其他瀏覽器的最新版本都已經支援。

4. `:root` 偽元素

    HTML 文件的根元素，一般來說指的是 `<html>`，可用以定義 CSS 全域變數。

5. CSS 濾鏡：`filter`

    這個屬性提供了一些濾鏡特效

## 問題點

1. 如何處理有後綴的參數值

    使用 `data-sizing` 設定後綴，然後使用 `dataset` 取出

2. 如何在 JavaScript 中，更改 CSS 變數值

    先取得定義 CSS 變數的元素，然後呼叫 style 的 setProperty()。`:root` 元素可由 `document.documentElement` 取得。
