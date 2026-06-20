## ADDED Requirements

### Requirement: Create matches with two-sided team composition
The system SHALL allow users to create matches by selecting which small groups form each side (隊伍).

#### Scenario: Create a standard match
- **WHEN** user selects one or more groups for Side 1 and one or more groups for Side 2, and confirms
- **THEN** a new match SHALL be saved with those group assignments

#### Scenario: Single large group on one side
- **WHEN** a group with 6 members (e.g., X) is assigned as the only group on one side
- **THEN** that single group SHALL constitute a full team for that side

#### Scenario: Two groups combine into a team
- **WHEN** two 3-person groups are assigned to the same side (e.g., A + C)
- **THEN** those two groups form a combined 6-person team for that match

### Requirement: Round label
Each match SHALL support an optional round label (輪次, e.g., "第一輪", "第二輪") to group related matches together for display.

#### Scenario: Label a batch of matches
- **WHEN** user sets a round label when creating a match
- **THEN** the match SHALL display under that label in the schedule and history views

### Requirement: Match list view
The system SHALL display all created matches in schedule order, grouped by round label when present.

#### Scenario: View schedule
- **WHEN** user opens the schedule panel
- **THEN** matches SHALL be listed with their round label, team compositions, and current score status (pending or recorded)
