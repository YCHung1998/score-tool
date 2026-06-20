## Context

The app is a single-file `index.html` with four bottom-tab sections (名單, 計分, 排名, 紀錄). There is no onboarding, tooltip, or help text anywhere. New users must discover the workflow by trial and error. Adding a static help screen is a low-risk, self-contained change.

## Goals / Non-Goals

**Goals:**
- Add a fifth "說明" (Help) tab to the bottom nav
- Provide clear, concise Chinese-language step-by-step instructions for every major feature: adding players, creating groups, entering round scores, reading rankings, exporting and importing data
- Explain the ranking rule (wins first, then score differential) so organizers understand the output
- Mobile-friendly layout (same card/section style as existing tabs)

**Non-Goals:**
- Interactive tutorial or coach-mark overlays
- Multi-language support (English translation)
- Server-side rendering or external help documentation
- Changes to data model, localStorage, or ranking logic

## Decisions

**1. Fifth tab vs modal**  
Added as a permanent fifth tab (說明) rather than a modal/drawer, so it is always reachable from the nav bar and doesn't require dismissal. Consistent with existing UX pattern. No extra JS complexity.

**2. Static HTML content, no dynamic generation**  
Help content is hardcoded HTML inside the tab `<div>`. The content never changes at runtime, so there is no need to generate it from data. Simplest possible approach for a single-file app.

**3. Chinese language**  
All instruction text is in Traditional Chinese to match the existing UI labels and the target audience (competition organizers in a Chinese-language context).

**4. Section-per-tab structure**  
Help is organized into sections matching the four existing tabs plus a "Ranking Rules" section, so users can find help that corresponds to wherever they are in the app.

## Risks / Trade-offs

- [Nav bar now has 5 tabs → may feel crowded on narrow phones] → Use smaller font or icon+label layout; existing tabs already use short 2-char labels so a 5th fits without overflow
- [Help content goes stale if features change] → Content is colocated in `index.html`; any feature change PR should update the help text at the same time
