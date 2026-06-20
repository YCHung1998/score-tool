## Why

New users opening the scoring tool have no guidance on how to use it — there is no onboarding text, help screen, or usage hints. This makes it hard for anyone unfamiliar with the app (e.g., a competition organizer handing it to a volunteer) to get started without asking for help.

## What Changes

- Add a **Help / Usage Guide** tab or modal in the web app explaining how to use each section (Roster, Score Entry, Rankings, History)
- Provide step-by-step instructions covering: adding players, creating groups, entering scores, reading the rankings, and exporting/importing data
- Instructions are inline in the app (no external link needed), mobile-friendly, and always accessible

## Capabilities

### New Capabilities
- `user-guide`: In-app help screen with step-by-step usage instructions covering all four tabs and key features (group binding, scoring, ranking rules, export/import)

### Modified Capabilities
<!-- No existing spec-level requirements are changing -->

## Impact

- `index.html`: Add a new Help tab (or modal/drawer) with static instructional content; update tab navigation to include it
- No data model changes; no localStorage changes
- No breaking changes to existing features
