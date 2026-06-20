## ADDED Requirements

### Requirement: Page uses Apple warm-neutral background
The page background SHALL use a warm off-white (`#fafaf8`) rather than a cool system gray, producing the characteristic warmth of classic Apple interfaces.

#### Scenario: Background color applied
- **WHEN** the app loads
- **THEN** the `body` background is warm off-white, not pure white or cool gray

### Requirement: Cards use stone surface with soft elevation shadow
Card components SHALL use a warm stone background (`#f5f5f0`) with a two-layer soft box shadow, creating gentle depth without dramatic drop shadows.

#### Scenario: Card surface and shadow visible
- **WHEN** a card is rendered on the page
- **THEN** its background is stone gray and it has a subtle lift shadow (`0 1px 3px rgba(0,0,0,0.08), 0 4px 12px rgba(0,0,0,0.04)`)

### Requirement: Single accent color is classic Apple blue
The sole interactive accent color throughout the app SHALL be `#0071e3` (Apple.com blue). No secondary accent colors (no teals, purples, or gradients) SHALL appear.

#### Scenario: Primary button uses classic Apple blue
- **WHEN** a primary action button is rendered
- **THEN** its background is `#0071e3` and no other accent color appears in the UI

#### Scenario: Active tab indicator uses classic Apple blue
- **WHEN** a nav tab is in the active state
- **THEN** its label and icon color is `#0071e3`

### Requirement: Borders use warm titanium tone
All dividing lines, input borders, and card separators SHALL use a warm titanium gray (`#d4d4c8`) rather than a cool neutral, maintaining tonal consistency with the warm background.

#### Scenario: Input field border color
- **WHEN** an input field is in its default (unfocused) state
- **THEN** its border color is warm titanium, not a cool gray

### Requirement: Typography uses SF Pro system font stack
The font stack SHALL be `-apple-system, 'SF Pro Text', BlinkMacSystemFont, 'Segoe UI', sans-serif`, ensuring SF Pro is used on Apple devices and a close system fallback on others.

#### Scenario: Font renders as SF Pro on macOS/iOS
- **WHEN** the app is viewed in Safari on macOS or iOS
- **THEN** body text renders in SF Pro Text
