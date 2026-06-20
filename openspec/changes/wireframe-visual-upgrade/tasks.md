## 1. 清理舊 ASCII wireframe CSS

- [x] 1.1 從 `<style>` 移除 `.wireframe-pre` 規則區塊
- [x] 1.2 從 `<style>` 移除 `.wireframe-section` 及 `.wireframe-section h4` 規則區塊
- [x] 1.3 從 `<style>` 移除 `.wireframe-section + .wireframe-section` 規則

## 2. 新增 CSS 樣式族群

- [x] 2.1 新增 `.tab-overview`：`display:flex; gap:16px; overflow-x:auto; padding:4px 4px 12px; scrollbar-width:none;` + `::-webkit-scrollbar { display:none; }`
- [x] 2.2 新增 `.tab-preview`：`flex-shrink:0; width:140px; text-align:center;`
- [x] 2.3 新增 `.tp-frame`：`width:140px; height:240px; background:#fff; border-radius:14px; border:2px solid #d4d4c8; box-shadow:0 4px 16px rgba(0,0,0,0.10); overflow:hidden; display:flex; flex-direction:column;`
- [x] 2.4 新增 `.tp-header`：`background:#1d1d1f; color:#fff; font-size:9px; font-weight:600; padding:7px 8px 5px; letter-spacing:0.3px; flex-shrink:0;`
- [x] 2.5 新增 `.tp-body`：`flex:1; padding:7px; display:flex; flex-direction:column; gap:5px; overflow:hidden;`
- [x] 2.6 新增 `.tp-card`：`background:#f5f5f0; border-radius:5px; padding:5px 6px; display:flex; flex-direction:column; gap:3px;`
- [x] 2.7 新增 `.tp-row`：`height:6px; background:#d4d4c8; border-radius:3px;`
- [x] 2.8 新增 modifier classes：`.tp-row.input { background:#fff; border:1px solid #d4d4c8; height:8px; }` / `.tp-row.short { width:55%; }` / `.tp-row.accent { background:#0071e3; }` / `.tp-row.wide { width:80%; }`
- [x] 2.9 新增 `.tp-badge`：`display:inline-block; height:10px; width:30px; background:#0071e3; border-radius:3px; margin-top:2px;`
- [x] 2.10 新增 `.tp-nav`：`padding:4px 6px; display:flex; justify-content:space-around; border-top:1px solid #e5e5ea; background:#fafaf8; flex-shrink:0;`
- [x] 2.11 新增 `.tp-dot`：`width:18px; height:18px; background:#e5e5ea; border-radius:3px;`
- [x] 2.12 新增 `.tp-dot.active`：`background:#0071e3;`
- [x] 2.13 新增 `.tp-label`：`font-size:12px; font-weight:600; margin:8px 0 2px; color:#1d1d1f;`
- [x] 2.14 新增 `.tp-desc`：`font-size:10px; color:#86868b; margin:0; line-height:1.3;`

## 3. 替換 HTML：移除 ASCII 區塊，插入 CSS mockup

- [x] 3.1 移除「App 結構總覽」卡片內所有 6 個 `<div class="wireframe-section">` 及其 `<pre>` 內容
- [x] 3.2 插入 `.tab-overview` 容器，內含 6 個 `.tab-preview`（依序：名單、賽程、計分、排名、紀錄、說明）
- [x] 3.3 名單 mockup：tp-header「選手名單」、2 張 tp-card（新增選手輸入列、選手列表 + 建立小組）、nav dot 1 active
- [x] 3.4 賽程 mockup：tp-header「賽程」、2 張 tp-card（輸入列 + 兩組 checkbox 列、場次清單列）、nav dot 2 active
- [x] 3.5 計分 mockup：tp-header「計分」、1 張 tp-card（隊名列、分數 input 列 x2、accent 勝者行）、nav dot 3 active
- [x] 3.6 排名 mockup：tp-header「排名」、2 張 tp-card（排名表列 x3、場次結果列 x2）、nav dot 4 active
- [x] 3.7 紀錄 mockup：tp-header「紀錄管理」、2 張 tp-card（示範資料 accent badge、三個 action 按鈕 badge）、nav dot 5 active
- [x] 3.8 說明 mockup：tp-header「使用說明」、2 張 tp-card（Overview 標題列、步驟列 x3）、nav dot 6 active

## 4. 手動驗證

- [ ] 4.1 打開說明 tab，確認 6 個 mockup 以水平捲動列顯示
- [ ] 4.2 在 375px 寬度下，確認可以左右滑動且頁面不出現水平 overflow
- [ ] 4.3 確認每個 mockup 的 header、card 色塊、nav bar 與高亮 dot 正確
- [ ] 4.4 確認其他 5 個 tab 的顯示與功能不受影響
