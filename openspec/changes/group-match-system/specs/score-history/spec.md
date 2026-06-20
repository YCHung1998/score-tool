## MODIFIED Requirements

### Requirement: Match history replaces round score history
The history view SHALL display completed matches grouped by round label, replacing the previous per-player per-round score display.

#### Scenario: View completed matches
- **WHEN** user views the history section of the rankings panel
- **THEN** each completed match SHALL show: round label, team compositions (group names on each side), scores, winner, and differential

#### Scenario: Pending matches shown distinctly
- **WHEN** a match has been created but not yet scored
- **THEN** it SHALL be displayed with a "待計分" (pending) indicator
