## MODIFIED Requirements

### Requirement: App overview wireframe card
The system SHALL display a visual overview of all 6 tabs at the top of the 說明 (Help) panel, implemented as HTML/CSS styled phone-frame mockups. The fourth mockup SHALL reflect the tab rename from 排名 to 戰績.

#### Scenario: Overview card visible on help tab
- **WHEN** user opens the 說明 tab
- **THEN** the first card SHALL show styled CSS phone-frame mockups for all 6 panels

#### Scenario: CSS rendering instead of monospace
- **WHEN** the overview is rendered
- **THEN** it SHALL use HTML div elements with CSS styling — NOT `<pre>` blocks or monospace fonts

#### Scenario: Fourth mockup labelled 戰績 not 排名
- **WHEN** the wireframe overview card is rendered
- **THEN** the fourth phone-frame mockup SHALL show 戰績 in the tp-header and 📊 戰績 in the tp-label (not 排名)

#### Scenario: Each panel labelled
- **WHEN** a panel mockup is shown
- **THEN** it SHALL include the tab name and a one-line description of its purpose below the frame
