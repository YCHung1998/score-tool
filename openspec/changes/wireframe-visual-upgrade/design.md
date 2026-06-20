## Context

現有的「App 結構總覽」卡片使用 6 個 `<pre class="wireframe-pre">` 區塊加 ASCII 框線字元。在中文字型下框線字元常因字寬不一而錯位，整體視覺風格也與 Apple HIG 主題脫節，無法傳達精美感。

此次將 ASCII wireframe 全面替換為 HTML/CSS styled 迷你手機框架 mockup，讓說明頁的「結構總覽」與整體 UI 風格一致，且在所有裝置上字元對齊無虞。

## Goals / Non-Goals

**Goals:**
- 6 個分頁各有一個迷你手機框架 mockup，水平排列可捲動
- mockup 用純 CSS div/span 繪製，不依賴任何外部 library 或 SVG
- 配色完全使用現有 Apple HIG palette，seamlessly 融入說明頁
- 移除所有 `<pre>` wireframe 及其 CSS

**Non-Goals:**
- 不加點擊互動（點 mockup 不跳轉到對應 tab）
- 不做真實的截圖或 iframe 嵌入
- 不引入任何 npm 套件或外部 CSS 框架

## Decisions

### Decision 1: 水平捲動容器 (`overflow-x: auto` + `scrollbar-width: none`)

每個 mockup 約 140px 寬，6 個共約 924px（含 gap），手機螢幕（375px）放不下全部。

**採用方案**：`display: flex; overflow-x: auto; scrollbar-width: none;`，使用者左右滑動即可瀏覽全部 6 個分頁。

**捨棄方案**：Grid 2×3 換行 — 每個 mockup 必須縮到 ≈ 160px 高才能塞下，細節會看不清楚。

### Decision 2: phone frame 以純 CSS div 繪製

**採用方案**：`.tp-frame` 用 `border-radius: 14px; border: 2px solid #d4d4c8; box-shadow` 模擬手機外框；內部用灰色 `.tp-row` 小方塊代表 input / list-item / button 等 UI 元素。

**捨棄方案**：SVG 手機外框 — SVG 雖然精準，但與 HTML 結構分離，維護較麻煩；且小尺寸下細節反而不清楚。

### Decision 3: 用色塊語義分層，而非文字標籤

在 140px 寬的 mockup 內，文字難以辨認。改用顏色語意：
- `#d4d4c8`（border gray）= 一般資料列 / 分隔線
- `#fff` + `border: 1px solid #d4d4c8` = input 框
- `#0071e3`（accent blue）= 按鈕 / 高亮 nav dot / 勝者標記
- `#f5f5f0`（card bg）= 內部 card 區塊

### Decision 4: 底部 nav bar 以 6 個小方塊表示，當前分頁標藍

每個 mockup 的 `.tp-nav` 區塊放 6 個 `.tp-dot`，對應分頁的那個 dot 設為 `.active`（藍色）。這樣使用者一眼就能對應「這個 mockup 代表哪個分頁」。

## CSS 結構

```
.tab-overview          水平捲動容器，flex row，隱藏 scrollbar
  .tab-preview         單一分頁預覽包裝 (flex-shrink:0, w:140px)
    .tp-frame          手機框架 (圓角, 陰影, overflow hidden)
      .tp-header       深色 header bar (分頁名稱)
      .tp-body         卡片區域佈局 (pad 8px, flex column gap)
        .tp-card       灰色背景小卡 (border-radius 6px)
          .tp-row      UI 元素色塊 (高度 6–10px, 各種 modifier)
          .tp-badge    徽章/按鈕模擬 (inline-block, accent color)
      .tp-nav          底部 6 格 nav bar
        .tp-dot        nav dot (.active = blue)
    .tp-label          分頁名稱標題 (12px 600)
    .tp-desc           功能說明 (10px gray)
```

## Risks / Trade-offs

- **極窄裝置（< 320px）**：mockup 框架可能被裁切 → Mitigation: `.tab-overview` 設 `padding-left/right: 4px`，保留視覺邊距
- **色塊過於抽象**：使用者需要看 `.tp-label` 才能理解每個 mockup 代表什麼 → Mitigation: 標題放在 frame 下方，字型夠大（12px）

## Migration Plan

1. 移除 `<style>` 中的 `.wireframe-pre`、`.wireframe-section` 規則
2. 新增 `.tab-overview`、`.tab-preview`、`.tp-*` CSS 規則
3. 在 `#panel-help` 的「App 結構總覽」卡片中，移除全部 `<div class="wireframe-section">` 和 `<pre>` 區塊
4. 插入 `.tab-overview` HTML 結構含 6 個 `.tab-preview`
5. 手動瀏覽器驗證：說明頁外觀、水平捲動、其他頁面不受影響
