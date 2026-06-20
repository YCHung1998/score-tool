## Why

目前工具有 6 個分頁，新使用者第一次打開時不清楚「要先去哪、做什麼、按什麼順序」，只有「說明」頁有文字說明但沒有視覺空間感。加入各分頁的 ASCII Wireframe，讓使用者一眼看懂整體 UI 結構與操作流程。

## What Changes

- 在「說明」分頁最上方加入一張「App 結構總覽」卡片
- 卡片內以 ASCII wireframe 畫出全部 6 個分頁的版型與主要元素
- 每個分頁 wireframe 附一行中文說明（用途 + 操作方向）
- 使用等寬字體（`<pre>`）確保框線對齊

## Capabilities

### New Capabilities

- `app-overview-wireframe`: 說明分頁頂部的全 6 分頁 ASCII 結構圖

### Modified Capabilities

（無）

## Impact

- `index.html`：`#panel-help` 頂部新增一個 `.card`，內含 `<pre>` wireframe 區塊
- 純 HTML/CSS 改動，不影響任何 JS 邏輯或資料模型
