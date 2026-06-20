## Why

The current UI uses generic mobile-web conventions that feel utilitarian. Restyling with Apple's classic design language — warm whites, stone grays, precise typography, and subtle depth — makes the tool feel considered and pleasant to use without borrowing the glassy gradients or neon accents that make apps feel "AI-generated".

## What Changes

- Replace the flat blue-on-white palette with Apple's classic warm-neutral system: warm white backgrounds, stone/titanium gray surfaces, and the classic Apple blue (`#0071e3`) as the sole accent
- Add subtle window-like card elevation (light box shadows, slightly warmer border tones) to give depth without heavy drop shadows
- Refine typography sizing and weight hierarchy to match Apple's HIG spacing and label conventions
- Soften interactive states (buttons, focus rings, active tabs) to feel tactile rather than stark
- No gradients, no glow effects, no AI-aesthetic purples or teals — strictly the Apple neutral + blue system

## Capabilities

### New Capabilities
- `ui-theme`: Visual design system (color palette, elevation, typography scale) applied consistently across all UI elements

### Modified Capabilities
<!-- No spec-level behavioral requirements are changing — this is a visual-only restyle -->

## Impact

- `index.html` (CSS `<style>` block): All color values, shadows, border radii, font sizes, and spacing tokens updated
- No JavaScript changes; no data model changes; no feature additions or removals
- No breaking changes to functionality
