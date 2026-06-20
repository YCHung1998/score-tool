## Context

現有工具的狀態模型以 `players[]` 和 `rounds{}` 為核心，一個選手一個分數。新賽制的核心是「小組」對抗，計分的最小單位是場次（match），結算的最小單位是小組（group）。

這是一次**資料模型的完整替換**，但 UI 框架（單頁 HTML、底部 tab 導航、Apple 色調）保持不變。

## Goals / Non-Goals

**Goals:**
- 新資料模型：groups + matches（取代 players + rounds 的計分角色）
- 賽程建立 UI：選組、設輪次標籤、建立場次
- 計分 UI：每場輸入兩側分數，自動判定勝負
- 排名引擎：依小組跨場次的勝場數 + 分數差
- 匯出 / 匯入新格式
- Players 保留（供小組成員顯示）

**Non-Goals:**
- 不支援賽制樹（單淘汰 / 雙淘汰 bracket）
- 不支援個人選手分數追蹤（移除）
- 不支援即時多人協同編輯

## Decisions

**Decision: 狀態模型設計**

```javascript
state = {
  players: [{ id, name }],          // 個人選手（成員顯示用）
  groups: [{ id, name, playerIds }], // 小組（排名單位）
  matches: [{
    id,
    roundLabel: "第一輪",            // 輪次標籤（可空）
    side1: ["A", "C"],               // side1 的小組 id 列表
    side2: ["X"],                    // side2 的小組 id 列表
    score1: null,                    // side1 分數（null = 未計分）
    score2: null,                    // side2 分數
  }],
  nextPlayerId: 1,
  nextGroupId: 1,
  nextMatchId: 1,
}
```

理由：
- `side1 / side2` 是 group id 陣列，支援任意組合（AC、X、EGH 等）
- `score = null` 表示場次已建立但尚未計分，方便事先規劃賽程
- 小組 id 使用使用者定義的名稱（"A", "B", "X"）作為顯示名，系統內部另有自增 id

**Decision: Tab 結構**

| Tab | 功能 |
|-----|------|
| 名單 | 新增/刪除選手；建立小組並指定成員 |
| 賽程 | 建立場次（選小組 → 設輪次 → 新增）；場次列表 |
| 計分 | 選擇場次 → 輸入兩側分數 → 儲存 |
| 排名 | 小組排名表 + 場次結果清單 |
| 紀錄 | 匯出 / 匯入 / 清除 |

「賽程」取代原「計分」的場次切換邏輯，「計分」改為以場次為單位直接選取輸入。

**Decision: 排名引擎**

```
對每個 group：
  matches.filter(m => m.side1.includes(g.id) || m.side2.includes(g.id))
  → 有分數的場次才計算
  → 決定該 group 在該場次是 side1 還是 side2
  → 若 score1 > score2 且 group 在 side1 → win，diff += score1 - score2
  → 若 score2 > score1 且 group 在 side2 → win，diff += score2 - score1
  → 平手 → draw，不計差分

排序：wins DESC → diff DESC → name ASC
```

**Decision: 匯出格式**

```
GROUP_MATCH_V1
PLAYERS:<id>:<name>,...
GROUPS:<id>:<name>:<p1>+<p2>+...,...
MATCH:<id>:<roundLabel>:<s1groupIds>/<s2groupIds>:<score1>:<score2>
```

score 欄位為 `-` 表示未計分。

## Risks / Trade-offs

- [Risk] 舊有 `SCORE_TRACKER_V1` 匯出檔不相容 → Mitigation: 匯入時偵測格式版本，舊格式顯示明確錯誤訊息
- [Trade-off] 移除個人選手計分：使用舊功能的資料無法遷移 → 此為刻意的功能轉向，舊資料在 localStorage 中保留直到使用者清除
- [Risk] 小組 id 以名稱為主鍵，若使用者用相同名字建立兩個小組會衝突 → Mitigation: 禁止重名小組
