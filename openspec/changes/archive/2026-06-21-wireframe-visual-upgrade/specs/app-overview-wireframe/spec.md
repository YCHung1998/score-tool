## MODIFIED Requirements

### Requirement: App overview wireframe card
The system SHALL display a visual overview of all 6 tabs at the top of the 說明 (Help) panel, implemented as HTML/CSS styled phone-frame mockups rather than ASCII text wireframes.

#### Scenario: Overview card visible on help tab
- **WHEN** user opens the 說明 tab
- **THEN** the first card SHALL show styled CSS phone-frame mockups for all 6 panels (replacing the previous ASCII `<pre>` blocks)

#### Scenario: CSS rendering instead of monospace
- **WHEN** the overview is rendered
- **THEN** it SHALL use HTML div elements with CSS styling — NOT `<pre>` blocks or monospace fonts

#### Scenario: Each panel labelled
- **WHEN** a panel mockup is shown
- **THEN** it SHALL include the tab name and a one-line description of its purpose below the frame
