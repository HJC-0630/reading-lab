# AGENTS.md - 互動式閱讀知識庫專案規範 (Reading Lab Project Standards)

歡迎來到 **Reading Lab** 專案！本專案是一個採用現代化、模組化設計的個人書單與深度閱讀知識庫。當您（AI）被指派來協助維護、新增書籍內容或調整版型時，**必須嚴格遵守以下專案規範、架構與互動規則**。

---

## 1. 專案核心目的與評分標準
* **核心定位**：打造一個具備高度擴充性、支援分類篩選、即時搜尋、3D 翻轉互動與沉浸式橫向書櫃的個人知識 Wiki。
* **設計原則**：維持乾淨、現代、文青質感（Clean & Modern），注重留白與高質感的視覺呈現（採用 Tailwind CSS）。
* **可延伸性**：確保專案結構具備極佳的模組化，未來新增第 7 本或第 20 本書時，只需複製標準卡片結構即可無縫擴充。

---

## 2. 目錄與檔案結構 (File Structure)
專案採單頁應用（Single-Page Application）與根目錄資源管理架構：
```text
reading-lab/
├── AGENTS.md          # 本規範檔案（AI 專案規則說明書）
├── index.html         # 主網頁（包含完整 HTML、Tailwind CSS、Alpine/Vanilla JS 互動邏輯）
└── (圖片資源)         # 所有書封面圖片必須直接放置於根目錄，與 index.html 同層
    ├── main1_233482.jpg
    ├── getImage.webp
    ├── image_0.jpg
    ├── images.jpeg
    ├── 20230907093113_48.jpg
    └── 86e3a19b-db83-4115-88ab-64c989a92960.jpg
```

---

## 3. 網頁設計風格與視覺規範 (Design Guidelines)
* **色彩配置 (Color Palette)**：
  * 背景色：溫潤暖灰白（`#FAF8F5`）。
  * 強調色：質感琥珀色（Amber-700 / Amber-100）。
  * 文字顏色：深灰柔和色（`#2D3748`）。
* **陰影與動畫**：卡片需帶有精緻的立體陰影（`shadow-xl` / `box-shadow`），且在滑鼠懸停（Hover）時需有輕微浮起（`translateY(-8px)`）的過渡動畫。

---

## 4. 核心互動規範 (Interactive Features)
1. **橫向滾動書櫃藝廊 (Horizontal Scroll Gallery)**：
   * 主視覺區塊須呈現一排橫向排列的精選書籍。
   * 容器需啟用 `overflow-x: auto` 並隱藏捲動軸（`.no-scrollbar`），搭配 `scroll-snap-type: x mandatory` 達到流暢的滑動與對齊體驗。
2. **3D 卡片翻轉 (3D Flip Effect)**：
   * 點擊正面封面圖片時，卡片需沿 Y 軸旋轉 180 度（`rotateY(180deg)`），背面顯示詳細摘要與金句。
3. **即時分類篩選 (Category Filtering)**：
   * 支援依據類別（心理勵志、商業思維、金融投資、生活哲學）動態切換顯示對應書籍。
4. **即時關鍵字搜尋 (Live Search Bar)**：
   * 讀者輸入關鍵字時，系統需即時比對 `data-title` 屬性並過濾顯示結果。
5. **深度心得彈窗 (Modal Popup)**：
   * 卡片背面提供「📖 閱讀完整心得」按鈕，點擊後開啟高畫質彈窗（Modal），展示完整千字讀書筆記。

---

## 5. 新增書籍時的 AI 行為準則 (Rules for AI)
當使用者要求「幫我新增一本書」時，AI 必須嚴格執行以下步驟：

1. **確認圖片資源**：取得新書封面圖片，並確認其放置於根目錄或提供正確檔名。
2. **複製標準卡片 HTML 結構**：在 `index.html` 的 `#book-grid` 容器內插入一組標準的 `<div class="book-card-container snap-center" data-category="..." data-title="...">`。
3. **填入對應資料**：
   * 設定 `<img>` 的 `src` 為正確的圖片檔名。
   * 填入正確的分類、書名、作者、一句話核心介紹、金句引言 (`<blockquote>`) 與 Modal 完整心得函式 (`openModal(...)`)。
4. **維持一致性**：確保新卡片的寬高（`flex: 0 0 280px; height: 440px;`）與互動行為完全符合本規範。