## Why

各場紀錄只顯示原始分數，沒有標示哪個單位獲勝、差分是多少、或該場是否為平手。用戶無法從紀錄直接追蹤排名的計算來源，導致排名結果「看起來」與紀錄不符。

## What Changes

- 在「各場紀錄」每場底部加上一行勝負摘要
- 有唯一最高分：顯示勝者名稱與差分（例如「🏆 組合 2 勝　差分 +1」）
- 平手（最高分並列）：顯示「⚖️ 平手，此場無勝者」
- 勝者摘要使用與排名引擎完全相同的單位邏輯（group 視為一個單位）

## Capabilities

### New Capabilities

- `round-result-display`: 每場紀錄附帶勝負結果與差分的視覺摘要

### Modified Capabilities

- `ui-theme`: 新增 `.round-winner` 與 `.round-tie` 樣式（僅新增規則，不改變現有行為）

## Impact

- `index.html`：`renderRankings()` 函式中各場紀錄的 HTML 渲染邏輯
- `index.html`：`<style>` 區塊新增兩個 CSS class
- 不影響資料結構、計分邏輯、匯出格式
