## Context

`renderRankings()` in `index.html` already runs `computeRankings()` which contains the full unit-scoring logic (groups as single units, tie detection, differential). That same logic needs to run a second pass per-round to produce winner annotations for the history display.

Currently the round history loop (lines ~920–938) builds only `scoreLines` (raw scores). There is no per-round winner calculation.

## Goals / Non-Goals

**Goals:**
- Re-use existing unit-scoring logic to compute per-round winner/tie for display
- Add winner name + diff, or tie label, beneath each round's score line
- Style using Apple warm-neutral palette (blue accent for winner, muted grey for tie)

**Non-Goals:**
- Changing the ranking calculation itself
- Adding winner annotation to the export/import format
- Changing data storage or `state.rounds` shape

## Decisions

**Decision: Extract per-round winner logic into a helper function**

Rather than duplicating the unit-score logic inside the history renderer, extract a `computeRoundResult(roundScores)` helper that returns `{ winner: <name|null>, diff: <number>, tie: <boolean> }`. `computeRankings()` and the history renderer both call this helper.

Alternatives considered:
- Inline the logic in the history renderer — rejected, creates duplication risk where history and ranking diverge
- Store winner data on save — rejected, over-engineering for a derived value

**Decision: Show group name for group winners**

When the winning unit is a group, display the group name (e.g. "組合 2") rather than listing members. This matches how rankings display groups, keeping the two sections visually consistent.

**Decision: CSS classes `.round-winner` and `.round-tie`**

Two small classes added to the existing `<style>` block. `.round-winner` uses `#0071e3` (Apple blue) at font-size 12px. `.round-tie` uses `#86868b` (secondary text) at font-size 12px.

## Risks / Trade-offs

- [Risk] `computeRoundResult` duplicates traversal of `state.players` and `state.groups` → Mitigation: both callers already do this per-round; the new helper is minimal and isolated
- [Trade-off] Single-participant rounds show winner with diff = their score vs 0 — edge case but consistent with current ranking engine behavior
