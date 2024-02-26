---
tags:
  - css
  - frontend
---
Modern solution for colour, which should now be used by default instead of RGB or HSL, due few great benefits.
- `L` is perceived lightness 0% to 100%, **perceived** means it has consistent lightness according to human perception
- `C` is chroma, from grey to most saturated colour
- `H` is the hue angle 0 to 360
- Optionally as last parameter it is possible to provide alpha e.g. `oklch(0% 0 0 / 50%)` which will result in alpha `50%`

Benefits:
- Predictable lightness simplifies contrast a11y, e.g. in HSL hue change could also change lightness which can result in unreadable text. OKLCH has consistent lightness across all colours
- Human readable
- Easier colour modifications and palette generation

# Links
- https://evilmartians.com/chronicles/oklch-in-css-why-quit-rgb-hsl
- Harmony palette (original provided by evil martians) https://www.figma.com/community/file/1287828769207775946/harmony-accessible-ui-color-palette
- Extended harmony palette (more vivid + additional colours) https://www.figma.com/community/file/1299736936313704224