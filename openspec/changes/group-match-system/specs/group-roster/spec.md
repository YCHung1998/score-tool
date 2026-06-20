## ADDED Requirements

### Requirement: Define named small groups
The system SHALL allow users to create named small groups (小組) that serve as the fundamental unit for competition and ranking.

#### Scenario: Create a group
- **WHEN** user enters a group name and clicks create
- **THEN** a new group SHALL be added to the roster with that name

#### Scenario: Add members to a group
- **WHEN** user assigns player names to a group
- **THEN** those players SHALL be listed as members of that group

#### Scenario: Prevent duplicate group names
- **WHEN** user tries to create a group with a name already in use
- **THEN** system SHALL reject the action with an error message

### Requirement: Group membership display
The system SHALL display each group's member list in the roster view.

#### Scenario: View group members
- **WHEN** user views the roster panel
- **THEN** each group SHALL show its name and member list

### Requirement: Groups are independent of rounds
A group's membership definition SHALL persist across all rounds and matches. New grouping configurations (e.g., E/F/G/H after A/B/C/D) are handled by creating additional groups, not by modifying existing ones.

#### Scenario: Adding round-3 groups alongside existing groups
- **WHEN** user creates groups E, F, G, H with different player compositions for a new rotation
- **THEN** all groups (A through H and X) SHALL coexist in the roster and be available for match assignment
