## Why

目前「App 結構總覽」卡片用 ASCII `<pre>` 框線呈現，在不同裝置上字元對齊不穩定、視覺層次差，且與整體 Apple HIG 設計風格脫節。改用 HTML/CSS 樣式化迷你手機框架，讓說明頁更精美、一目瞭然。

## What Changes

- 移除 `#panel-help` 中的 6 個 `<pre class="wireframe-pre">` ASCII wireframe 區塊及相關 CSS
- 新增「App 結構總覽」視覺化卡片：6 個並排的迷你手機外框 mockup，以水平捲動容器呈現
- 每個 mockup 包含：深色 header bar（顯示分頁名稱）、用色塊代表各 UI 區塊的 card 佈局、底部 6 格 nav bar（當前分頁高亮為藍色）
- 每個 mockup 下方有分頁名稱標題與一行功能說明
- 配色延用現有 Apple HIG palette（#fafaf8、#0071e3、#1d1d1f）

## Capabilities

### New Capabilities

- `visual-tab-overview`: 以 HTML/CSS 手機外框 mockup 取代 ASCII wireframe，水平捲動展示全部 6 個分頁的版型預覽

### Modified Capabilities

- `app-overview-wireframe`: 需求從「ASCII 框線」升級為「HTML/CSS 樣式化 mockup」，視覺實現方式改變

## Impact

- `index.html`：移除 `.wireframe-pre`、`.wireframe-section` CSS 及所有 `<pre>` wireframe DOM；新增 `.tab-overview`、`.tab-preview`、`.tp-*` CSS 樣式族群與對應 HTML 結構
- 純 HTML/CSS 改動，不影響任何 JS 邏輯或資料模型
