# Day 01: JavaScript Drum Kit

模擬電子鼓組，使用者在鍵盤上按下 ASDFGHJKL 等按鍵，頁面上與字母對應的樂器按鈕會變大變亮，對應的打擊聲會響起來。

## 重點技巧

1. 鍵盤事件
2. 播放聲音
3. 動畫結束事件

## 基礎語法

1. `const`：宣告一個唯讀的常數，在區塊範圍中，僅能賦值一次。
2. **模板字串 (Template literals)**：字串頭尾用反單引號分隔，字串內可以用 `${expr}` 代換運算式的計算結果。
3. `document.querySelector`: 可使用 CSS 選擇器查詢符合的 HTML 元素
4. `document.querySelectorAll`：回傳結果為 `NodeList`，可採用 `forEach` 方法對其進行遍歷。
5. `addEventListener`：純 JavaScript 用來加入事件處理函數的方法。

## 問題點

### 如何將鍵盤按鍵與頁面按鈕對應起來？

鍵盤按鍵按下時，會觸發 `keydown` 事件，其 `keyCode` 屬性值會與 ASCII 編碼值相同 (對應大寫字母)。

初始頁面中，樂器按鈕 `div` 和音頻 `audio` 標籤中都添加了一個自訂 `data-key` 屬性用以指定對應的鍵碼，如此一來，就可透過 `keyCode` 找到對應的樂器按鈕及音頻。

```javascript
const { keyCode } = event;
const audio = document.querySelector(`audio[data-key="${keyCode}"]`);
const key = document.querySelector(`.key[data-key="${keyCode}"]`);
```

### 如何保證按鍵按住不放時，可以播放出連續打擊聲？

每次播放音頻之前，先將播放時間倒帶回 0 秒。

```javascript
audio.currentTime = 0;
audio.play();
```

### 如何為樂器按鈕添加打鼓動畫效果？

當鍵盤按下時，套用放大加框效果 (`.playing`)，配合  `transition`，就會有動畫效果。

### 如何恢復樂器按鈕樣式？

HTML 元素的屬性值 transition 到最終值時，會觸發 `transitionend` 事件。我們可以監聽這個事件，在每次打鼓動畫效果結束之後，去除相關樣式。

由於樂器按鈕發生 `transitionend` 的樣式屬性不只一個 (`transform`, `border-*-color`, `box-shadow`)，所以添加一個條件判斷，使得去除相關樣式只做一次。

```javascript
function stopPlaying(event) {
  if (event.propertyName !== 'box-shadow') return;

  // this === event.target
  this.classList.remove('playing');
}
```
