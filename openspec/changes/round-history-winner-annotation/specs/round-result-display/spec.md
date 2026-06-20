## ADDED Requirements

### Requirement: Round result summary line
Each round in the history display SHALL include a result summary line below the scores showing either the winner and score differential, or a tie indicator.

#### Scenario: Single winner
- **WHEN** a round has exactly one unit (solo player or group) with the uniquely highest score
- **THEN** the result line SHALL display the winner's name and the differential (winner score minus second-highest score)

#### Scenario: Tie round
- **WHEN** a round has two or more units sharing the highest score
- **THEN** the result line SHALL display a tie indicator stating no winner for that round

#### Scenario: Group winner
- **WHEN** the winning unit is a group
- **THEN** the result line SHALL display the group name (not individual member names)

#### Scenario: Only one participant
- **WHEN** only one unit has a score in a round
- **THEN** that unit SHALL be shown as the winner with differential equal to their score (compared to implicit 0)
