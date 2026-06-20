## ADDED Requirements

### Requirement: Help tab is always accessible
The app SHALL include a dedicated Help tab (說明) in the bottom navigation bar, accessible at all times regardless of the current active tab.

#### Scenario: Help tab appears in nav bar
- **WHEN** the app loads
- **THEN** a "說明" tab is visible in the bottom navigation alongside the existing four tabs

#### Scenario: Switching to help tab
- **WHEN** the user taps the "說明" tab
- **THEN** the help content panel is displayed and the other tab panels are hidden

### Requirement: Help content covers all major features
The help screen SHALL contain instructional text organized into sections that correspond to each major area of the app: player roster, score entry, rankings, and history/export.

#### Scenario: Roster instructions visible
- **WHEN** the user views the help tab
- **THEN** they can see step-by-step instructions for adding players and creating groups

#### Scenario: Score entry instructions visible
- **WHEN** the user views the help tab
- **THEN** they can see instructions for selecting a round and entering scores, including how group mirroring works

#### Scenario: Ranking rules explained
- **WHEN** the user views the help tab
- **THEN** they can see an explanation of the ranking rule: more wins ranks higher; ties are broken by total score differential

#### Scenario: Export and import instructions visible
- **WHEN** the user views the help tab
- **THEN** they can see instructions for exporting data to a file and importing it back

### Requirement: Help content is in Traditional Chinese
All help text SHALL be written in Traditional Chinese to match the existing app UI language.

#### Scenario: Language consistency
- **WHEN** the user reads the help tab
- **THEN** all instructional text is in Traditional Chinese with no mixed-language content

### Requirement: Help tab is mobile-friendly
The help content layout SHALL be readable and navigable on a mobile screen without horizontal scrolling.

#### Scenario: No horizontal overflow
- **WHEN** the help tab is displayed on a screen narrower than 400px
- **THEN** all text and sections fit within the viewport width and scroll vertically only
