## Context

This is a greenfield web app for competition score tracking. No existing codebase. Target users are competition organizers using mobile devices at events. Data needs to persist across sessions without requiring a server or account.

**Constraints:**
- No backend infrastructure (keep it deployable as a static site or standalone HTML file)
- Must work on mobile browsers
- Data portability: users should be able to save/export records as text files

## Goals / Non-Goals

**Goals:**
- Fast score entry during a competition
- Correct ranking: wins first, then total winning-score-differential as tiebreaker
- Player groups: linking two players means their score entry is auto-mirrored
- Persistent history that survives page reloads
- Ability to export records as a txt file and clear history

**Non-Goals:**
- Multi-device sync or real-time collaboration
- Authentication or user accounts
- Complex tournament bracket management
- Server-side storage

## Decisions

### D1: Vanilla JS + single HTML file vs. framework

**Decision**: Single-file HTML/CSS/Vanilla JS app.

**Rationale**: The feature set is small and self-contained. A framework adds build tooling and complexity without meaningful benefit at this scale. A single `.html` file can be opened directly in a browser or served from any static host, and is trivially shareable.

**Alternative considered**: React/Vue SPA — ruled out because it requires a build step and increases deployment friction for non-technical organizers.

### D2: Storage — localStorage vs. txt file download

**Decision**: Use `localStorage` as the primary persistence layer, with an export-to-txt function for backup/portability.

**Rationale**: `localStorage` is universally supported and requires zero UI friction for normal use (auto-save on every change). txt export lets users keep a human-readable archive and re-import on a new device if needed.

**Alternative considered**: IndexedDB — more capable but overkill for this data volume and harder to debug.

### D3: Ranking algorithm implementation

**Decision**: Pure JS function: sort players descending by (win count, then total winning-score-differential).

- Per match: if `playerScore > opponentScore`, player wins and earns `playerScore - opponentScore` differential points.
- Ranking: primary key = total wins (desc), secondary key = sum of winning differentials (desc).

### D4: Player grouping

**Decision**: A "group" is a named set of players whose scores are entered once and applied to all members automatically.

- Stored as a mapping `{ groupId: [playerId, ...] }`.
- When recording a match result for any group member, the app applies the same result to all members in the group.
- Groups are configured in a player/group setup screen before scoring begins.

## Risks / Trade-offs

- **localStorage cleared by browser** → User loses history. Mitigation: prompt user to export txt after each session; offer import from txt.
- **No input validation on scores** → Garbage data if user miskeys. Mitigation: numeric-only inputs with basic range checks.
- **Group mirroring may be surprising** → If A and D are grouped, entering A's score silently updates D. Mitigation: show a visual indicator on grouped players and confirm before applying.
- **Single-file approach limits testability** → No unit test harness out of the box. Mitigation: keep ranking logic in a pure function that can be copy-pasted to a test environment if needed.

## Migration Plan

No migration needed — greenfield. Deployment: host the `.html` file on any static site (GitHub Pages, Netlify) or distribute directly as a file.
