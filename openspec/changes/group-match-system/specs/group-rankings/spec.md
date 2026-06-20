## ADDED Requirements

### Requirement: Compute per-group standings
The system SHALL compute a ranking table for all small groups based on their match participation.

#### Scenario: Group wins accumulate across matches
- **WHEN** a group's team wins a match (group appears on the winning side)
- **THEN** that group's win count SHALL increment by 1

#### Scenario: Score differential accumulates
- **WHEN** a group's team wins a match
- **THEN** the match's score differential (winning score − losing score) SHALL be added to that group's cumulative differential

#### Scenario: Group on losing side
- **WHEN** a group's team loses a match
- **THEN** the group's loss count SHALL increment and no differential is added

#### Scenario: Groups not in any match
- **WHEN** a group has not been assigned to any match
- **THEN** the group SHALL appear in rankings with 0 wins and +0 differential

### Requirement: Ranking sort order
Groups SHALL be ranked: wins descending, then cumulative score differential descending, then alphabetically by group name for ties.

#### Scenario: Different win counts
- **WHEN** Group A has 2 wins and Group B has 1 win
- **THEN** Group A SHALL rank above Group B

#### Scenario: Equal wins, different differentials
- **WHEN** Group A and Group B both have 1 win, but A has differential +5 and B has +2
- **THEN** Group A SHALL rank above Group B

### Requirement: Ranking table display
The ranking table SHALL show: rank, group name, member list, wins, losses, score differential.

#### Scenario: Full standings view
- **WHEN** user opens the rankings panel
- **THEN** all groups SHALL appear in ranked order with win/loss/diff columns visible
