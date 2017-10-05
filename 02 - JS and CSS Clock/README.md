# Day 02 - JavaScript + CSS 類比時鐘

初始源碼已經給出 HTML 結構，時鐘的三個指針分別用三個 `div` 表示，顯示鐘面和指針的 CSS 樣式也已寫好，只要再使用 JavaScript 更新指針狀態即可。

## 重點想法

1. 時鐘指針的樣式：旋轉
2. 將目前時間換算成旋轉角度
3. 每秒定期更新指針角度

### 涉及到的 CSS 屬性和 JS 方法

* `transform-origin`: 預設基準點為元素中心，要換到指針端點 (鐘面軸心)
* `transform: rotate()`: 用來旋轉指針
* `transition`: 指針移動的效果
* `transition-timing-function`：可用來調整指針移動的方式 (e.g. 連續、跳動...)
* `setInterval(callback, period)`：定期更新指針角度

### 實作過程

#### CSS 部分

1. 調整旋轉的軸心

    ```css
    transform-origin: 100%;    // 或者可以用 right
    ```

2. 調整指針轉動時的過渡效果

    ```css
    transition: all 0.5s;
    ```

3. 調整指針轉動時的運動模式

    ```css
    transition-timing-function: cubic-bezier(0.69, 0.53, 1, 2.06);
    ```

#### JS 部分

1. 利用 `setInterval` 每隔一秒呼叫更新指針旋轉角度
2. 使用 `new Date()` 取得目前時間，將時分秒轉換成 degree 角度
3. 更換指針的 `transform` 樣式
