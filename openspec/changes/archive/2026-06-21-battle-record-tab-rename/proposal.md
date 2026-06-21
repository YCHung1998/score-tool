## Why

目前六個分頁的導覽列僅有中文標籤，缺乏英文對照，非中文使用者看不懂功能。同時「排名」這個詞較為行政、中性，改為「戰績」更符合競技對抗賽的氛圍，與「battle record」的概念一致。

## What Changes

- 所有 6 個導覽按鈕新增英文副標題（顯示在中文標籤下方，小字灰色）
  - 名單 / Roster
  - 賽程 / Schedule
  - 計分 / Score
  - 戰績 / Battle Record（原「排名」改為「戰績」）
  - 紀錄 / Records
  - 說明 / Guide
- `TAB_TITLES.rankings` 從 `'排名'` 改為 `'戰績'`，使頂部頁面標題同步更新
- 說明頁 wireframe mockup 中的「排名」標籤同步更新為「戰績」

## Capabilities

### New Capabilities

- `bilingual-nav-labels`: 導覽按鈕顯示中英雙語標籤（中文主標 + 英文副標）

### Modified Capabilities

- `app-overview-wireframe`: 排名 mockup 的標籤文字從「排名」改為「戰績」（視覺呈現變更）

## Impact

- `index.html`：
  - `<nav>` 6 個按鈕內的文字節點改為 `<span class="nav-label">` + `<span class="nav-sublabel">`
  - 新增 `.nav-label`、`.nav-sublabel` CSS 規則
  - `TAB_TITLES.rankings` 值從 `'排名'` 改為 `'戰績'`
  - 說明頁 wireframe 中排名 mockup 的 `.tp-header` 和 `.tp-label` 更新
- 純 UI/copy 改動，不影響任何資料邏輯
