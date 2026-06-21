## ADDED Requirements

### Requirement: Visual tab overview with CSS phone mockups
The system SHALL display a horizontal scrollable row of 6 styled CSS phone-frame mockups in the 說明 tab, each representing one navigation tab, replacing any ASCII text wireframe.

#### Scenario: Mockups visible on help tab
- **WHEN** the user opens the 說明 tab
- **THEN** the first card SHALL show 6 mini phone-frame mockups in a horizontally scrollable container

#### Scenario: Each mockup shows the correct tab
- **WHEN** a mockup is rendered
- **THEN** it SHALL include a dark header bar with the tab name, colour-block card rows representing that tab's main UI sections, and a 6-dot bottom nav bar with the matching dot highlighted in #0071e3

#### Scenario: Horizontal scroll on narrow screens
- **WHEN** the screen width is less than the total mockup row width
- **THEN** the container SHALL scroll horizontally without breaking page layout, and the scrollbar SHALL be hidden

#### Scenario: No ASCII pre blocks
- **WHEN** the visual mockups are rendered
- **THEN** there SHALL be no `<pre>` blocks or monospace ASCII wireframe content anywhere in the App 結構總覽 card

#### Scenario: Design palette matches app
- **WHEN** the mockups are rendered
- **THEN** they SHALL use the app's existing Apple HIG colours: #fafaf8 background, #0071e3 accent, #1d1d1f header, #f5f5f0 card surface

### Requirement: Mockup label and description
Each phone mockup SHALL have a short label and one-line description rendered below the frame in the same palette as the rest of the help tab.

#### Scenario: Label visible below frame
- **WHEN** a mockup is rendered
- **THEN** its tab name (with emoji) is displayed in 12px semi-bold below the phone frame, followed by a 10px grey description line
