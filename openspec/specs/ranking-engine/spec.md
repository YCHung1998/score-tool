## Purpose

Defines requirements for calculating and displaying player rankings based on win count and winning-score differentials as a tiebreaker.

## Requirements

### Requirement: Rank players by win count
The system SHALL rank players primarily by the total number of matches they have won, with more wins placing a player higher.

#### Scenario: Player with more wins ranks higher
- **WHEN** the ranking is calculated
- **THEN** a player with 3 wins is ranked above a player with 2 wins regardless of score differentials

### Requirement: Break ties with winning-score differential
The system SHALL use the sum of winning-score differentials as a tiebreaker when two or more players have the same number of wins.

A winning-score differential for a single match is defined as: `player_score - opponent_score` for matches the player won. Only winning matches contribute to this sum.

#### Scenario: Same wins, higher differential wins tiebreak
- **WHEN** two players have the same number of wins
- **THEN** the player with the higher total winning-score differential is ranked higher

#### Scenario: Example ranking
- **WHEN** Player A has wins with differentials [6, 6, 3] (total 15), Player B has wins with differentials [2, 3] (total 5), and Player C has wins with differentials [1, 10] (total 11)
- **THEN** the ranking is: 1st A, 2nd C, 3rd B

### Requirement: Display live ranking
The system SHALL display the current player rankings in real time, updating automatically whenever a score is entered or edited.

#### Scenario: Ranking updates on score entry
- **WHEN** the user enters or edits any match score
- **THEN** the ranking table updates immediately without requiring a manual refresh

#### Scenario: Ranking shows win count and differential
- **WHEN** the ranking is displayed
- **THEN** each player's row shows their name, total wins, and total winning-score differential

### Requirement: Handle players with no wins
The system SHALL include players with zero wins in the ranking, sorted below all players with at least one win, ordered by winning-score differential (all zero for players with no wins).

#### Scenario: Zero-win players appear at the bottom
- **WHEN** the ranking is displayed and some players have no wins
- **THEN** those players appear below all players who have at least one win
