# Day 06 - Ajax Type Ahead

在搜尋框中輸入一個關鍵字，迅速過濾出 JSON 資料中含有關鍵字的項目，資料則是載入網頁時非同步從網路中取得。

## 學習重點

* Promise
    - `fecth()`
    - `then()`
    - `json()`
* Array
    - `filter()`
    - `map()`
    - `push()`
    - `join()`
    - ES6 Spread 語法
* RegExp
    - `match()`
    - `replace()`

## 實作要點

1. 宣告一個空陣列，用來存放 JSON 資料
2. 執行 `fetch()` 發出 HTTP 請求
    - 取得回傳的 `Promise` 物件
    - 取得回應的 JSON 資料
    - 存入陣列
3. 取得搜尋輸入框，監聽 `input` 事件
4. 編寫比對輸入的函數
    - 建立正則表達式，表示過濾條件
    - 運用 `filter()` 過濾陣列資料
5. 編寫展示比對結果的函數
    - 取得比對成功的陣列
    - 將關鍵詞用高亮標籤包住
    - 產生 HTML 片段
    - 將 HTML 片段插入 `<ul>` 標籤中

## 相關知識

### [Fetch API](https://developer.mozilla.org/en/docs/Web/API/Fetch_API)

### [ES6 Spread Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

### [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
