## Context

All styles live in a single `<style>` block inside `index.html`. There are no CSS variables, no external stylesheets, and no preprocessor — values are hardcoded throughout. The current palette uses iOS-style blues (`#007aff`) on pure white, which reads as generic mobile-web rather than the warmer, more considered Apple aesthetic.

## Goals / Non-Goals

**Goals:**
- Define a complete Apple-classic token set (colors, shadows, radii, type sizes) and apply it throughout the single `<style>` block
- Achieve the "warm neutral + one accent" look: warm white (`#fafaf8`) page background, stone-gray (`#f5f5f0`) card surfaces, titanium borders (`#d4d4c8`), classic Apple blue (`#0071e3`) accent only
- Card elevation: a single soft shadow layer (`0 1px 3px rgba(0,0,0,0.08), 0 4px 12px rgba(0,0,0,0.04)`) — no heavy drop shadows
- Tab bar: warm white with a hairline top border in titanium; active tab in classic Apple blue
- Buttons: primary in `#0071e3` (not `#007aff`), secondary in stone gray, danger in the classic Apple red (`#ff3b30`) — same hue, slightly desaturated presence
- Typography: use `-apple-system, 'SF Pro Text', BlinkMacSystemFont` stack; tighten label weight hierarchy (section labels at 600, card titles at 600, body at 400)

**Non-Goals:**
- CSS custom properties / variables (would require refactor of all existing inline styles too)
- Dark mode support
- Any layout or structural changes
- Any JavaScript changes

## Decisions

**1. Warm white page background (`#fafaf8`) instead of pure `#f2f2f7`**  
Apple's classic Mac aesthetic uses a very slightly warm off-white rather than the cooler iOS system gray. This is the single biggest shift away from "generic mobile" and toward "Mac-like warmth."

**2. Card background `#f5f5f0` (stone) instead of `#ffffff`**  
Pure white cards on a white-ish background loses the classic Mac window depth. Using a warm stone for cards against a warm white page creates the gentle layering effect without heavy shadows.

**3. Single accent color: `#0071e3`**  
This is the Apple.com "buy button" blue — slightly cooler and more saturated than the iOS `#007aff`, but without the harshness of a neon. It reads "Apple classic" immediately. No secondary accents.

**4. Soft two-layer shadow on cards**  
`0 1px 3px rgba(0,0,0,0.08), 0 4px 12px rgba(0,0,0,0.04)` — close shadow for edge definition, far shadow for lift. Combined opacity stays below 0.12 total, which is the Apple HIG threshold for "material, not dramatic."

**5. Border radius stays at `12px` for cards, `10px` for inputs**  
Current values already match Apple HIG. No change needed.

## Risks / Trade-offs

- [Warm card background may reduce contrast for text on low-brightness screens] → Stone gray `#f5f5f0` still provides sufficient contrast for `#1c1c1e` body text (contrast ratio ~17:1)
- [Replacing every hardcoded color is tedious and error-prone in a single file] → All color replacements are systematic find-and-replace operations; the task list groups them by element type to reduce miss risk
