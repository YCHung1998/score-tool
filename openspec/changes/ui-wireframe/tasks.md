## 1. 新增 CSS 樣式

- [x] 1.1 在 `<style>` 區塊新增 `.wireframe-pre` 樣式：`font-family: 'Menlo', 'Courier New', monospace; font-size: 11px; overflow-x: auto; background: #f5f5f0; padding: 12px; border-radius: 6px; line-height: 1.4;`

## 2. 插入 wireframe 總覽卡片

- [x] 2.1 在 `#panel-help` 的第一個 `.card` 之前插入新卡片，標題「App 結構總覽」
- [x] 2.2 卡片內加入 6 個分頁的 wireframe `<pre class="wireframe-pre">` 區塊（依 design.md 中的 ASCII art）
- [x] 2.3 每個 wireframe 前加 `<h4>` 標題（含分頁 emoji + 名稱 + 一行說明）
- [x] 2.4 各 wireframe 區塊之間以 `.wireframe-section` margin 分隔

## 3. 手動驗證

- [ ] 3.1 打開說明 tab，確認 wireframe 卡片出現在最上方
- [ ] 3.2 在窄視窗（< 375px）確認 `<pre>` 水平捲動不破版
- [ ] 3.3 確認其餘說明內容不受影響
