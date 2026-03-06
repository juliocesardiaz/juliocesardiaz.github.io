# Nim Game — Visual Redesign Brief

Redesign the Game of Nim's look-and-feel to match the aesthetic of juliocdiaz.com.

---

## Design System Reference

### Color Palette

Use these exact CSS custom properties (copy them into a `:root` block):

```css
:root {
  --black:     #0A0A0A;   /* default background */
  --bone:      #F0EBE3;   /* primary text, labels */
  --concrete:  #2A2826;   /* secondary surfaces, panels, code blocks */
  --dim:       #635E59;   /* secondary/muted text, timestamps */

  --teal:      #00F0B5;   /* active state, highlights, selected items */
  --blue:      #0038FF;   /* primary action buttons */
  --red:       #FF0A0A;   /* danger, back navigation, spot accents */
  --yellow:    #FFD900;   /* graphic interruptions, warnings */
  --pink:      #FF0090;   /* headers, bars */
}
```

### Fonts

Load both of these from Google Fonts:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&family=IBM+Plex+Sans:wght@300;700&display=swap" rel="stylesheet">
```

- **Body / UI text:** `'IBM Plex Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif`
  weight 300 (light) for body, 700 (bold) for headings
- **Numbers, scores, counters, any monospaced readout:** `'IBM Plex Mono', monospace`

---

## Specific Style Rules

### Background & Ground
```css
html { background: #0A0A0A; }
body {
  background: #0A0A0A;
  color: #F0EBE3;
  font-family: 'IBM Plex Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
  font-weight: 300;
}
```

### Headings
```css
h1, h2, h3 {
  font-family: 'IBM Plex Sans', sans-serif;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #F0EBE3;
}
```

### Buttons
- Primary / take-turn action: `background: #0038FF; color: #F0EBE3;`
- Hover: `background: #00F0B5; color: #0A0A0A;`
- Destructive / restart: `background: transparent; color: #FF0A0A; border: 1px solid #FF0A0A;`
- No border-radius — use sharp (0) or at most 2px corners to keep the look angular and graphic.

### Game Board / Nim Piles
- Container background: `#2A2826` (Wet Concrete) — gives a panel feel against the black ground.
- Active / selected tokens/sticks: accent with `#00F0B5` (Spectral Teal).
- Removed/inactive tokens: `#635E59` (dim mid-tone).
- Winning highlight or "you win" state: `#FFD900` (Broadcast Yellow).

### Score / Status Text
- Use `'IBM Plex Mono'` for any numeric counters, move counts, or turn indicators.
- Muted/secondary labels (e.g. "Round", "Turn"): `color: #635E59;`
- Active player indicator: `color: #00F0B5;`
- AI/opponent indicator: `color: #FF0090;`

### Links & Navigation
```css
a { color: #F0EBE3; text-decoration: none; }
a:hover { color: #00F0B5; }
```

### Spacing & Layout
- Give the game container generous padding: at least `4rem 2rem` on mobile, `4rem 6rem` on desktop.
- Max content width: `65ch` to `960px` depending on the layout.
- Prefer clean whitespace over decorative borders. Use color contrast rather than lines to separate sections.

---

## Tone & Feel

The site has a stark, graphic, almost editorial quality — think art-world minimalism meets signal/warning aesthetics. Key principles:

- **Dark ground, bone text** — always. Never use a white background.
- **No gradients.** Flat color only.
- **No drop shadows.** Use color and spacing to create depth.
- **No rounded corners** (or keep them at 2px max).
- **Uppercase headings** with wide letter-spacing.
- Detonation colors (teal, blue, red, yellow, pink) are used sparingly as accents — they are meant to stand out against the dark ground, not fill large areas.

---

## Checklist for the Agent

- [ ] Replace all background colors with `#0A0A0A` (black) or `#2A2826` (concrete for panels)
- [ ] Replace all text colors with `#F0EBE3` (bone) or `#635E59` (dim for secondary)
- [ ] Replace fonts with IBM Plex Sans (body) and IBM Plex Mono (numbers/code)
- [ ] Style buttons using the blue/teal/red palette above
- [ ] Highlight active game elements in `#00F0B5` (teal)
- [ ] Show win/end-state in `#FFD900` (yellow)
- [ ] Remove any gradients, shadows, or rounded corners
- [ ] Ensure headings are uppercase with letter-spacing
- [ ] Add `font-weight: 300` to body text
