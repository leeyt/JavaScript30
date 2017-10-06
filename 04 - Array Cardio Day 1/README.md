# Day 04 - Array Cardio 1

這一部分主要是熟悉 `Array` 的幾個基本方法，其中有兩個 (`filter`, `map`) 是 ES5 就有定義的迭代方法。這些迭代方法都有一個特點，就是會對陣列的每一項目都套用指定函數，根據使用的迭代方法的不同，而有不同的回傳結果。

初始源碼有事先定義一個 `inventor` 陣列，內含測試資料。基於這個陣列，可以練習一下 `Array` 的各個方法，執行結果可以打開瀏覽器的開發工具 Console 查看。

## 題目

1. 篩選 16 世紀 (1500~1599) 出生的發明家
2. 顯示發明家的全名
3. 按造出生年份從古至今進行排序
4. 計算全體發明家總共活了多少歲
5. 按造壽命長短進行排序
6. 篩選出維基百科巴黎大道含有某詞句的條目
7. 按造姓氏對一組人名進行排序 (姓氏, 名字)
8. 統計出陣列中各個項目出現的次數

## 相關知識

### [Array.protoype.filter()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

過濾方法會利用傳入的布林函數，檢查陣列項目是否符合條件，符合條件的項目才會留下來。

```javascript
array.filter(item => predicate(item));
```

### [Array.prototype.map()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

映射方法則會將陣列的每個元素，套用傳入的函數，將回傳值組成另一個陣列。

```javascript
array.map(item => convert(item));
```

### [Array.prototype.sort()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

預設情況下，陣列排列會以字串形式進行升序排列。但 `sort()` 也可傳入一個比較兩個元素的函數。

```javascript
array.sort((a, b) => compare(a, b));

// compare(a, b) 回傳 -1 假如 a 排在 b 之前
// compare(a, b) 回傳 +1 假如 a 排在 b 之後
```

### [Array.prototype.reduce()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

可視為累加器，在便利陣列元素的過程中，統整出一個最終值。

```javascript
array.reduce(callback, initialValue);
let callback =
  function(accumulator, currentItem, currentIndex, array) {
    ...
  };
```

### [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

示範視頻中是直接到維基網頁，打開 Console 執行 JavaScript 擷取出適當網頁元素轉成陣列進行分析。

但是 Fetch API 可直接將網頁抓回來，再做後續的分析。

```javascript
fetch(url, { method: 'GET' })
  .then(response => response.text())
  .then(text => {
    const parser = new DOMParser();
    const content = parser.parseFromString(text, 'text/html');
    ...
  })
```
