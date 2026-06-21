## Context

導覽列按鈕目前結構為：SVG icon + 純文字標籤。要加入英文副標題，需要將文字節點包成兩個 `<span>` 並新增對應 CSS，同時在多個地方更新「排名」→「戰績」的文案。

## Goals / Non-Goals

**Goals:**
- 6 個 nav 按鈕各增加一行英文副標題
- 排名 tab 中文標籤、頁面標題、wireframe mockup 同步改為「戰績」
- 視覺層次清晰：中文大、英文小灰字

**Non-Goals:**
- 不改變任何 JS 邏輯或資料模型
- 不改變 TAB_TITLES 以外的其他中文 UI 文字（例如面板內的 `<h2>` 標題保持「小組排名」等）

## Decisions

### Decision: `<span class="nav-label">` + `<span class="nav-sublabel">`

每個 nav button 的文字改為兩個 span 堆疊：

```html
<button onclick="switchTab('roster', this)" id="nav-roster">
  [SVG]
  <span class="nav-label">名單</span>
  <span class="nav-sublabel">Roster</span>
</button>
```

**nav button 已是 `flex-direction: column`**，span 元素自然換行堆疊，不需改動 flex 方向。

**捨棄方案**：用 `::after` pseudo-element — 無法對每個按鈕設定不同文字，維護性差。

### Decision: `.nav-sublabel` 樣式

```css
.nav-label    { display: block; font-size: 10px; }
.nav-sublabel { display: block; font-size: 8px; color: #86868b; line-height: 1.1; margin-top: 1px; }
```

- `display: block` 確保各自佔一行
- `font-size: 8px` 在手機上夠小不搶眼，但仍可閱讀
- 顏色 `#86868b` 與現有 empty state、description text 保持一致

### Decision: 只改 TAB_TITLES.rankings，不改面板內容

`TAB_TITLES.rankings` 從 `'排名'` → `'戰績'`，影響範圍僅頂部 `<h1>` 標題。面板內的 `<h2>小組排名</h2>` 保持不變（描述的是功能內容，而非 tab 名稱）。

## English label mapping

| Tab ID   | 中文（主標） | English（副標）|
|----------|------------|--------------|
| roster   | 名單        | Roster       |
| schedule | 賽程        | Schedule     |
| score    | 計分        | Score        |
| rankings | 戰績        | Battle Record|
| history  | 紀錄        | Records      |
| help     | 說明        | Guide        |

## Risks / Trade-offs

- **Nav bar 高度增加**：加入 8px 英文副標後，nav button 約增加 10px 高度 → Acceptable，iOS Safari 底部安全區已有 padding，不影響 safe area
- **極小字（8px）在低 PPI 裝置可能模糊** → Mitigation: 實際測試，如有問題可調至 9px
