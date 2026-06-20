## ADDED Requirements

### Requirement: Enter scores for each match
The system SHALL allow users to input the score for each side of a match.

#### Scenario: Record a match result
- **WHEN** user enters Side 1 score and Side 2 score for a match and saves
- **THEN** the match result SHALL be stored and the winner determined by the higher score

#### Scenario: Tie scores
- **WHEN** both sides have equal scores
- **THEN** the system SHALL record the match as a draw (no winner)

#### Scenario: Edit a previously recorded match
- **WHEN** user updates the scores for a match that already has a result
- **THEN** the new scores SHALL overwrite the previous result and rankings SHALL update

### Requirement: Score validation
Scores SHALL be non-negative integers.

#### Scenario: Invalid score input
- **WHEN** user enters a non-integer or negative value
- **THEN** system SHALL display an error and prevent saving

### Requirement: Score differential display
The system SHALL display the score differential for each completed match (winning side score minus losing side score).

#### Scenario: Differential shown in match history
- **WHEN** a match has been scored
- **THEN** the record SHALL show both raw scores and the differential
