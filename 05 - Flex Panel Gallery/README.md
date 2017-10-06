# Day 05 - Flex Panels Image Gallery

將上下排列的圖片變成左右排列，點擊圖片會使其展開，同時從圖片上下移入原本隱藏的標語。
點擊已經展開的圖片，圖片會被壓縮，同時該圖片上下的標語再次隱藏。

初始網頁的 DOM 結構：`div.panels` 會包住 5 個 `div.panel`，每個 `div.panel` 又會包住 3 個 `p` 標籤。

初始樣式表中，動畫時間等特性已經設定好，只需要完成不同狀態下的頁面排版以及事件監聽即可。

## 涉及觀念

* `display: flex`
    - `flex-direction`
    - `justify-content`
    - `align-items`
* `transform: translateX()`
* `element.classList.toggle()`
* `transitionend` 事件

## 實作過程

### CSS 部分

CSS3 的 flexbox 是這天挑戰的主要重點，使用 flex 可以讓各個元素按造一定比例分割容器。
在調整版面時，可以先設定邊框以方便查看效果。

1. 將 `.panels` 設置為 `display: flex`，可以讓其成為彈性容器
2. 將每個 `.panel` 的 `flex` 設成 1，可以水平均分 `.panels` 所佔空間。
3. 每個子 `.panel`，也設置為 `display: flex`
4. 控制 `.panel` 的子元素 `<p>` 垂直均分且文字水平置中
5. 使用 `.open` 作為圖片展開的狀態
    - `.panel` 的 `flex: 5`
    - 使用 `transform: translateY()` 控制文字位置

### JS 部分

1. 獲取所有 `.panel`
2. 監聽 `click` 事件，以切換 `.panel` 的 `.open` (觸發 `transition` 效果)

## 相關知識

### [Flexbox](https://developer.mozilla.org/en/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)

#### 針對 Flex items 的特性 (Children)

* `flex-growth`：伸展值
* `flex-shrink`：可接受的壓縮值
* `flex-basis`：元素預設的尺寸值
* `flex`：以上三種值按順序的簡寫

#### 針對 Flex container 的特性 (Parent)

* `display: flex`：將這個元素設置成彈性盒子
* `flex-direction`：主軸方向
    - `row`：橫向
    - `column`：縱向
* `justify-content`：沿著主軸的對齊方式
* `align-items`：沿著側軸的對齊方式
* `align-content`

## 延伸思考

參考方案有個 bug，當快速點擊兩下時，會讓圖片縮小＋上下文字出現。

原意是想要點擊圖片觸發展開效果結束後，才去觸發上下文字移入的過渡效果。
但是第二次點擊會讓圖片再次縮小，但是上下文字移入的觸發卻沒有取消。

[Soyaine](https://github.com/soyaine) 的解法是只用 `.open` 來控制圖片展開＋上下文字移入的過渡效果，但是用 `transition-delay: 0.7s` 將文字部分的過渡效果延遲至圖片展開完成後才開始。
