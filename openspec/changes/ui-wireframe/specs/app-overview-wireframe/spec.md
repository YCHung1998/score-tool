## ADDED Requirements

### Requirement: App overview wireframe card
The system SHALL display a visual wireframe overview of all 6 tabs at the top of the 說明 (Help) panel.

#### Scenario: Wireframe visible on help tab
- **WHEN** user opens the 說明 tab
- **THEN** the first card SHALL show ASCII wireframe layouts of all 6 panels

#### Scenario: Monospace font alignment
- **WHEN** wireframe is rendered
- **THEN** it SHALL use a `<pre>` block with monospace font so box-drawing characters align correctly

#### Scenario: Each panel labelled
- **WHEN** a panel wireframe is shown
- **THEN** it SHALL include the tab name and a one-line description of its purpose
