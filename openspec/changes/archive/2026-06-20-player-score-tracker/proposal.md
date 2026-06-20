## Why

Competition organizers need a simple, mobile-friendly web tool to record and rank player scores per match, with persistent storage so records can be reviewed or cleared across sessions. No such tool exists for this use case today.

## What Changes

- New web app that lets users input players and per-match scores
- Ranking engine: sort players by wins first, then by total winning-score-differential as a tiebreaker
- Player grouping: link players together so their scores are automatically mirrored (no duplicate entry)
- Persistent storage via local text-based files (accessible on mobile and desktop browsers)
- Ability to view historical records and clear them when no longer needed

## Capabilities

### New Capabilities

- `player-roster`: Manage the list of players and optional group bindings between them
- `match-scoring`: Record per-match scores for each player and compute win/loss per match
- `ranking-engine`: Calculate and display player rankings based on wins and winning-score differentials
- `score-history`: Persist, browse, and clear historical scoring records

### Modified Capabilities

<!-- None — this is a greenfield project -->

## Impact

- New standalone web app (HTML/CSS/JS or lightweight framework)
- No backend required; storage via browser localStorage or downloadable/importable txt files
- Mobile-first UI for easy on-the-go score entry
