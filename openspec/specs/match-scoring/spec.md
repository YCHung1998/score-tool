## Purpose

Defines requirements for recording, validating, and managing match scores across rounds, including automatic win/loss determination and score mirroring for grouped players.

## Requirements

### Requirement: Record match score for a player
The system SHALL allow the user to record the score for a player in a given match round as a non-negative integer.

#### Scenario: Enter a valid score
- **WHEN** the user enters a non-negative integer score for a player in a match
- **THEN** the score is saved and associated with that player and match round

#### Scenario: Invalid score rejected
- **WHEN** the user enters a non-numeric or negative value as a score
- **THEN** the system SHALL reject the input and display a validation error

### Requirement: Determine match win/loss
The system SHALL automatically determine whether a player won or lost each match based on their score versus their opponent's score.

#### Scenario: Higher score wins
- **WHEN** a player's score is greater than their opponent's score in a match
- **THEN** the system SHALL record a win for that player and a loss for the opponent

#### Scenario: Lower score loses
- **WHEN** a player's score is less than their opponent's score in a match
- **THEN** the system SHALL record a loss for that player

#### Scenario: Equal scores result in no win
- **WHEN** both players in a match have the same score
- **THEN** the system SHALL record no win for either player in that match

### Requirement: Auto-mirror scores for grouped players
The system SHALL automatically apply the same score to all members of a group when a score is entered for any one member.

#### Scenario: Score mirrored to group members
- **WHEN** the user enters a score for a player who belongs to a group
- **THEN** the same score is automatically applied to all other players in the group for the same match round

#### Scenario: Visual confirmation of mirroring
- **WHEN** scores are mirrored to group members
- **THEN** the system SHALL display a visible indicator showing which players received the mirrored score

### Requirement: Edit a recorded score
The system SHALL allow the user to edit a previously entered score for a match round.

#### Scenario: Edit score updates result
- **WHEN** the user changes a previously saved score
- **THEN** the win/loss result and any grouped mirrors are recalculated immediately

### Requirement: Input per match round
The system SHALL support recording scores across multiple match rounds, each round tracked separately.

#### Scenario: Multiple rounds recorded
- **WHEN** the user completes a round and starts a new one
- **THEN** each round's scores are stored independently and all rounds contribute to the ranking calculation
