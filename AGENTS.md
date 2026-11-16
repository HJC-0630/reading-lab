## 6. 進階互動規範：橫向滾動藝廊 (Horizontal Scroll Gallery)
* **設計目標**：首頁主視覺應呈現橫向排列的精選書單，支援使用者以滑鼠滾輪或觸控板流暢地向右/向左橫向瀏覽（Horizontal Snap Scrolling）。
* **視覺層次**：
  * 封面容器需設定為彈性盒子（Flexbox）或網格（Grid），並啟用 `overflow-x: auto`。
  * 為了達到流暢的滑動感，需加入 `scroll-snap-type: x mandatory` 與子元素的 `scroll-snap-align: center`。
  * 隱藏預設醜陋的捲動軸（Scrollbar），保持極簡美感。
* **卡片互動**：維持點擊翻轉（Flip Effect）機制，正面展示精裝書封，背面展示深度摘要與金句。