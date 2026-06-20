## ADDED Requirements

### Requirement: Add player to roster
The system SHALL allow the user to add a named player to the roster before scoring begins.

#### Scenario: Add a new player
- **WHEN** the user enters a player name and confirms
- **THEN** the player appears in the roster list and is available for score entry

#### Scenario: Duplicate player name rejected
- **WHEN** the user attempts to add a player with a name that already exists in the roster
- **THEN** the system SHALL display an error and not add the duplicate

### Requirement: Remove player from roster
The system SHALL allow the user to remove a player from the roster when no scores have been recorded for that player.

#### Scenario: Remove player with no scores
- **WHEN** the user removes a player who has no match records
- **THEN** the player is deleted from the roster

#### Scenario: Remove player with existing scores blocked
- **WHEN** the user attempts to remove a player who has at least one match record
- **THEN** the system SHALL prevent removal and display a warning

### Requirement: Create player group
The system SHALL allow the user to bind two or more players into a named group so their match scores are automatically mirrored.

#### Scenario: Create a group
- **WHEN** the user selects two or more players and assigns them to a group
- **THEN** the group is saved and those players are marked as grouped in the roster view

#### Scenario: Player can only belong to one group
- **WHEN** the user attempts to add a player who already belongs to a group to a different group
- **THEN** the system SHALL reject the action and display an error

### Requirement: View roster
The system SHALL display all players and their group memberships in the roster screen.

#### Scenario: Roster shows groups
- **WHEN** the user opens the roster screen
- **THEN** each player is listed with a visual indicator showing which group (if any) they belong to
