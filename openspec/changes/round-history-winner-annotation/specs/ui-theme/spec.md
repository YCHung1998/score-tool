## ADDED Requirements

### Requirement: Round winner style
The system SHALL provide a `.round-winner` CSS class for displaying the winning unit summary with a visually distinct but subtle style consistent with the Apple warm-neutral palette.

#### Scenario: Winner line appearance
- **WHEN** a round has a winner
- **THEN** the winner summary SHALL use the Apple blue accent color (`#0071e3`) at reduced opacity to remain readable without dominating the layout

### Requirement: Round tie style
The system SHALL provide a `.round-tie` CSS class for displaying tie results using a neutral muted style.

#### Scenario: Tie line appearance
- **WHEN** a round is a tie
- **THEN** the tie summary SHALL use the secondary text color (`#86868b`) to de-emphasize the result
