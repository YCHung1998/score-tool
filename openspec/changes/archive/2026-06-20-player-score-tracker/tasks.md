## 1. Project Scaffold

- [x] 1.1 Create `index.html` with base structure: header, tab navigation (Roster, Score Entry, Rankings, History), and a main content area
- [x] 1.2 Add inline CSS for mobile-first responsive layout (min-width: 320px, tap-friendly inputs and buttons)
- [x] 1.3 Create `app.js` (or inline `<script>`) with a top-level app state object: `{ players, groups, rounds, currentRound }`
- [x] 1.4 Implement localStorage load/save helpers: `saveState()` and `loadState()` that serialize/deserialize the full app state

## 2. Player Roster

- [x] 2.1 Build the Roster tab UI: player name input, "Add Player" button, and a list rendering all current players
- [x] 2.2 Implement `addPlayer(name)`: validate non-empty, check for duplicates, append to `state.players`, save, re-render
- [x] 2.3 Implement `removePlayer(id)`: block removal if player has any match score records, otherwise delete and save
- [x] 2.4 Build the group management UI: multi-select player list, group name input, "Create Group" button
- [x] 2.5 Implement `createGroup(name, playerIds)`: validate no player is already in another group, save to `state.groups`, re-render roster with group badges

## 3. Match Scoring

- [x] 3.1 Build the Score Entry tab UI: round selector/counter, a score row per player (name label + numeric input), and a "Save Round" button
- [x] 3.2 Implement score input validation: accept only non-negative integers, display inline error on invalid input
- [x] 3.3 Implement group mirroring: when a score input changes for a grouped player, auto-fill the same value into all other group members' inputs and show a "mirrored" badge
- [x] 3.4 Implement `saveRound(roundScores)`: store scores keyed by `{ roundId, playerId }` in `state.rounds`, compute win/loss per player (compare each player's score against all opponents in the round), save state
- [x] 3.5 Implement `editScore(roundId, playerId, newScore)`: update stored score, recompute win/loss for affected round, trigger ranking recalculation, re-render
- [x] 3.6 Add "New Round" button that increments `state.currentRound` and clears the score entry form

## 4. Ranking Engine

- [x] 4.1 Implement `computeRankings()`: pure function that takes `state.players` and `state.rounds`, returns players sorted by (total wins DESC, total winning-score differential DESC)
- [x] 4.2 Build the Rankings tab UI: table with columns — Rank, Name, Wins, Total Differential
- [x] 4.3 Wire `computeRankings()` to re-render the Rankings tab automatically after every score save or edit
- [x] 4.4 Include zero-win players at the bottom of the rankings table

## 5. Score History & Data Portability

- [x] 5.1 Implement `exportTxt()`: serialize full app state (players, groups, all round scores, current rankings) into a human-readable text format and trigger a browser file download as `scores.txt`
- [x] 5.2 Define the txt export format (header, player list, group list, rounds with scores, final ranking) — document the format as a comment in code
- [x] 5.3 Implement `importTxt(file)`: parse an uploaded `.txt` file, validate format, load data into app state, re-render all tabs; show error toast on invalid file
- [x] 5.4 Build the History tab UI: "Export as .txt" button, "Import from .txt" file picker, and "Clear All Data" button
- [x] 5.5 Implement `clearAll()`: show a confirmation dialog, then delete all localStorage data and reset `state` to empty defaults, re-render all tabs

## 6. Polish & Verification

- [x] 6.1 Verify ranking example from task.md: A[6,6,3]=3 wins/15 diff → 1st, C[1,10]=2 wins/11 diff → 2nd, B[2,3]=2 wins/5 diff → 3rd
- [ ] 6.2 Test group mirroring: add two grouped players, enter score for one, confirm the other auto-fills
- [ ] 6.3 Test localStorage persistence: enter data, reload page, confirm all data restored
- [ ] 6.4 Test export → clear → import round-trip: verify imported data matches original
- [ ] 6.5 Test on a mobile browser (or device emulator) for usability: tap targets, input keyboard, layout
