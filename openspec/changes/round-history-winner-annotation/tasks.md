## 1. CSS

- [x] 1.1 Add `.round-winner` class: font-size 12px, color `#0071e3`, margin-top 6px
- [x] 1.2 Add `.round-tie` class: font-size 12px, color `#86868b`, margin-top 6px

## 2. Helper Function

- [x] 2.1 Add `computeRoundResult(roundScores)` function above `renderRankings()` that returns `{ tie: boolean, winnerName: string|null, diff: number }`
- [x] 2.2 In the helper, build unit scores using same group-merging logic as `computeRankings()`
- [x] 2.3 Determine winner: if exactly one unit has the max score → winner; else tie
- [x] 2.4 Resolve winner display name: if winner unit is a group → group name; else player name
- [x] 2.5 Compute diff: max score minus second-highest unit score (or max score if only one unit)

## 3. Round History Renderer

- [x] 3.1 In `renderRankings()`, call `computeRoundResult(scores)` for each round
- [x] 3.2 Build result HTML: tie → `<div class="round-tie">⚖️ 平手，此場無勝者</div>`; winner → `<div class="round-winner">🏆 ${winnerName} 勝　差分 +${diff}</div>`
- [x] 3.3 Append result HTML after `scoreLines` in the `.round-item` template

## 4. Verification

- [ ] 4.1 Open browser, run a 3-player scenario with one tie round and verify both winner annotation and tie annotation render correctly
- [ ] 4.2 Verify group winner shows group name (not individual members)
- [ ] 4.3 Confirm the displayed diff matches the diff shown in the rankings table
