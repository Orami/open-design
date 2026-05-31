# Design System Inspired by SUPERCOMPUTE — Terminal Dossier

> Category: Fintech & Crypto
> Sovereign Web3 infrastructure. Deep navy, brass-gold, terminal-mono. Flat sheets, CRT layers, HUD brackets.

## 1. Visual Theme & Atmosphere

SUPERCOMPUTE's Terminal Dossier is a **CLI-native design language** — the visual equivalent of a hardened operator's terminal session. Every pixel earns its place. Nothing decorative, nothing ornamental.

The canvas is deep navy (`#0a1330`) — not pure black, not electric blue, but the color of a submarine sonar screen at 200 meters. Text renders in JetBrains Mono at `14px / 1.7` leading, giving every page a teletype feel with modern readability.

Three fixed CRT layers sit behind all content:
- A **dot-grid** (`body::before`, `z:0`) — 56×56px radial dots at 3% white, like an old terminal's shadow mask
- **Scanlines** (`body::after`, `z:1`) — 1px/3px repeating horizontal lines at 18% black, mix-blend-mode multiply, 55% opacity
- A **vignette** (`.vignette`, `z:1`) — radial darkening at edges, transparent at center to 35% black at edges

Four **HUD corner brackets** (`.hud-corner`, `z:250`) — 28×28px, 2px brass-yellow (`#E0BE3F`), pinned to viewport corners. They shrink to 22px below 900px. These are the only decorative elements on the page.

Cards are **flat sheets** — `rgba(255,255,255,.02)` background, `1px solid rgba(244,236,216,.10)` border, **zero border-radius**. No shadows on body content. Hover = border-color shift + `translateY(-1px)`.

The version badge (`.version-tag`, `z:260`) sits at bottom-right, clearing the HUD bracket: `BUILD · design-system @ <sha> · <time>`, brass-yellow text on translucent navy, 1px brass border.

**Key Characteristics:**
- JetBrains Mono everywhere — no sans-serif, no serif, no script
- Navy ground (#0a1330) with brass-gold (#C9A33A) accent — warm metal on cold electronics
- Flat sheets with 0 radius — Terminal Dossier has no rounded corners
- CRT signature layers (dot-grid, scanlines, vignette) on every page
- HUD corner brackets — the only decoration
- Brass hairlines (`rgba(201,163,58,.30)`) for elevated borders
- Mono-blue (#6FA3E5) body text — less contrast than cream, reads as secondary
- Hover transitions use border-color shift + translateY, never shadows
- `// command --flag` eyebrow pattern with brass blink caret

## 2. Color Palette & Roles

### Primary — Terminal Dossier
| Token | Value | Role |
|---|---|---|
| `--site-bg` | `#0a1330` | Page background, every surface |
| `--gold-warm` | `#C9A33A` | Heading accent, primary CTA, active states |
| `--gold-warm-2` | `#b8902c` | Gold pressed/hover |
| `--cream` | `#F4ECD8` | Display text, headings |
| `--mono-blue` | `#6FA3E5` | Body text, secondary annotations |
| `--hud-yellow` | `#E0BE3F` | HUD brackets, status pill borders |

### Surface Layers
| Token | Value | Role |
|---|---|---|
| `--surface-0` | `#0a1330` | Base (same as site-bg) |
| `--surface-1` | `#0d1f3d` | Elevated sheet / hover |
| `--surface-2` | `#0a1e3d` | Card surface |
| `--border` | `#1E3A5F` | Standard hairline |
| `--border-warm` | `rgba(201,163,58,.30)` | Brass hairline (elevated) |

### Identity Moments Only
| Token | Value | Use |
|---|---|---|
| `--pink` | `#F472B6` | Logo gradient stop, AuthOverlay accent ring, school progress fill |
| `--cyan` | `#38BDF8` | Logo gradient stop (legacy) |
| `--violet` | `#7c3aed` | Logo ring |

These are **never** used for: page backgrounds, body text, default CTAs, section accents.

### Status
| Token | Value |
|---|---|
| `--success` | `#4ade80` |
| `--warning` | `var(--gold-warm)` |
| `--danger` | `#ef4444` |

### On-Dark Alphas
`--white-90` · `--white-70` · `--white-55` · `--white-35` · `--white-12` · `--white-08` · `--white-04`

## 3. Typography & Font Stack

**JetBrains Mono** is the only font family on shipped pages.

| Role | Size | Weight | Letter-spacing | Color |
|---|---|---|---|---|
| Display (hero) | `clamp(1.9rem, 4.5vw, 3.4rem)` | 700 | `-.5px` | `--cream` |
| H1 | `1.6rem` | 700 | — | `--cream` |
| H2 | `1.35rem` | 700 | — | `--cream` |
| H3 | `1.1rem` | 700 | — | `--cream` |
| Body | `14px` | 400 | `.3px` | `--cream` or `--mono-blue` |
| Mono label | `10px` | 500 | `.15em` uppercase | `--gold-warm` |
| Mono eyebrow | `13px` | 400 | normal | `--mono-blue` |
| Small | `9px` | 500 | `.1em` uppercase | `--mono-blue` |

**Text patterns:**
- **Eyebrows**: `// command --flag` — lowercase mono, brass gold, with blinking ASCII caret
- **Headlines**: Sentence case mono, single accent phrase in `--gold-warm`
- **Body**: Sentence case mono, `--mono-blue` with `--cream` bold
- **SUPERCOMPUTE wordmark**: All caps, letter-spaced, never hyphenated

## 4. Spacing & Layout Grid

**4px scale:**
```
--s-1: 4px    --s-2: 8px    --s-3: 12px
--s-4: 16px   --s-5: 20px   --s-6: 24px
--s-8: 32px   --s-10: 40px  --s-12: 48px
```

| Context | Value |
|---|---|
| Section padding | `96px 0` |
| Hero padding | `80px 0 120px` |
| Sidebar width (`--nav-w`) | `220px` |
| Topbar height (`--topbar-h`) | `52px` |
| Body default | `14px / 1.7 line-height / .3px letter-spacing` |
| Content max-width | `1100px` |

**Responsive breakpoint: `900px`**
- Sidebar collapses to `60px` (icon-only)
- Grids go single-column
- HUD brackets shrink to `22px`
- Main padding: `48px` → `32px 20px`

**Breakpoint: `520px`**
- Hero actions column-stack
- Sheet rows go single-column
- Project grid single-column

## 5. Component Patterns & States

### Buttons (`.cmd-btn`)
Terminal command-style buttons. Lowercase monospace label with `//` prefix.
- **Solid** (`.cmd-btn.solid`): `--gold-warm` background, `--site-bg` text, brass border. Primary action.
- **Ghost** (`.cmd-btn.ghost`): Transparent background, `--mono-blue` text, `--border` hairline. Hover: `--gold-warm` border and text.
- Hover: `translateY(-1px)`, border-color shift. Never shadow.

### Connect Button (`.btn-connect`)
Block-width, brass fill, `// CONNECT` label. Hover: 85% opacity. No border radius.

### Sheets (`.sheet`, `.sheet-row`)
Flat dossier tables. 1px `--border` outer + row dividers. Rows: `40px num / 1fr body / auto price`. Hover: `--surface-1` background.

### Project Grid (`.proj-grid`, `.proj-cell`)
2-column grid with 1px brass interior lines. Cells: `24px` padding, status tag (`--gold-warm` border), name, detail line (`--mono-blue`).

### Agent Fleet (`.fleet-summary`)
4-column stat tiles. Row with large numbers and mono labels. Agent cards: 2-column grid with name/status pill and description.

### Staking (`.stake-grid`)
4-column stat tiles, large values in `--gold-warm`.

### Forms & Inputs
No border radius. Focus: `--gold-warm` 1px solid. Labels: mono, uppercase, `--mono-blue`.

### Status Pills
Brass-yellow / success / danger 1px border, transparent fill, mono label. Never solid fill.

### Prompts & Caret
Eyebrow pattern: `// prompt --flag` with a blinking ASCII block caret (`▌` or `█`). Blink animation: `@keyframes blink { 0%,100% {opacity:1} 50% {opacity:0} }`.

### States (General)
- **Idle / Default**: Brass hairline, transparent fill
- **Hover**: `--gold-warm` border, `translateY(-1px)`, gated under `@media(hover:hover)and(pointer:fine)`
- **Active / Selected**: `--gold-warm` text + border
- **Disabled**: `--mono-blue` at 40% opacity
- **Error**: `--danger` border
- **Loading / Pending**: Pulsing `--gold-warm` dot

## 6. Motion & Animation

### Duration Tokens
| Token | Value | Use |
|---|---|---|
| `--t-fast` | `.15s ease` | Button press, hover |
| `--t-base` | `.20s ease` | Navigation, transitions |
| `--t-slow` | `.60s ease` | Page mount |
| `--t-spring` | `1.2s cubic-bezier(.34, 1.56, .64, 1)` | Progress fills, special |

### Rules
- Hard cap on UI animation: **300ms**
- Exits faster than entrances
- `transition: all` forbidden — always specify properties
- `ease-in` forbidden — feels sluggish
- Animate `transform` + `opacity` only — never `padding`, `margin`, `height`, `width`
- Entry: `scale(0.95)` → `scale(1)` (never from `scale(0)`)
- `prefers-reduced-motion` override required for any animation > 0ms
- Same enter/exit speed forbidden (exits faster)

### Curves
- Strong ease-out: `cubic-bezier(0.23, 1, 0.32, 1)` — button hovers, page mounts, scaling
- Strong ease-in-out: `cubic-bezier(0.77, 0, 0.175, 1)` — on-screen movement
- iOS drawer: `cubic-bezier(0.32, 0.72, 0, 1)` — slide-in panels

### Hover Gate
All hover effects must be gated:
```css
@media (hover: hover) and (pointer: fine) {
  .element:hover { /* ... */ }
}
```

## 7. Voice & Tone

### Voice
- **Pragmatic consulting firm.** Calm, expert, services-first.
- "We've shipped 14 of these. Here's the playbook." — NOT "Stop manually managing your Web3 community."
- "We" = the company. "You" = the reader.
- Numbers as proof: `13 years` not `over a decade`. `$200` not `affordable`. `0 incidents` not `secure`.

### Forbidden Phrases
- "Cyborg Agency"
- "platform" (as self-description)
- "Stop manually managing…" or any retail/yield-tourist framing
- Pricing claims dressed as guaranteed returns

### Casing
- **SUPERCOMPUTE** wordmark — all caps, letter-spaced
- Eyebrows — `// path` or `// command --flag` lowercase mono with brass caret
- Headlines — sentence case mono, single accent phrase in `--gold-warm`
- Body — sentence case mono

## 8. Brand & Logo Usage

### SUPERCOMPUTE Wordmark
- All caps, letter-spaced, never hyphenated
- Font: Phosphate Solid on the SC logo mark; JetBrains Mono everywhere else
- Never outlined, never gradient-filled, never on a photo background

### SC Logo
- Pink-to-gold gradient ring — legitimate identity moment (only use for logo)
- 50% border-radius
- `drop-shadow(0 0 16px rgba(201,163,58,.30))` glow — only shadow in the system
- Logo gradient stops: `--pink` → `--gold` (legacy gold)

### Co-Branding
- SUPERCOMPUTE + LACC: both logos in footer, equal sizing
- SUPERCOMPUTE + partner logos: ordered left-to-right by engagement level

### Version Badge
- Bottom-right, clears HUD bracket
- Format: `BUILD · branch @ sha · time`
- Auto-injected by `npm run sync`

## 9. Anti-Patterns & Red Flags

### Visual — Never
- White card backgrounds over the navy body
- Rounded corners on sheets, buttons, or inputs (pill chips excepted: `--r-pill: 999px`)
- Shadows on body content (SC logo glow is the exception)
- Gradient-filled text
- Purple gradients anywhere
- Pink (`#F472B6`) as a primary CTA color (identity moments only)
- Price ticker at top of home page
- Protocol-logo soup as a hero proof element
- Nested cards ("cardocalypse")
- `ease-in` on UI animations
- `transition: all` — always specify properties
- `scale(0)` entry — start at `scale(0.95)`
- Animating `padding`/`margin`/`height`/`width`
- Bare `:hover` without `@media(hover:hover)and(pointer:fine)` gate
- Animation > 300ms on UI
- Missing `prefers-reduced-motion` override

### Font — Never
- Inter, Phosphate (except SC logo), Caveat, Oswald, Courier Prime
- Any non-mono font on shipped pages
- Italic serif h1 over a pill-chip uppercase eyebrow

### Copy — Never
- "Cyborg Agency" (anywhere on shipped surfaces)
- "platform" as a self-description
- "Stop manually managing your Web3 community"
- Retail/yield-tourist framing
- Pricing claims dressed as guaranteed returns

### Architectural — Never
- Same enter/exit speed (exits must be faster)
- Z-index conflicts: content at 2, HUD at 250, overlays at 300+
- `!important` in CSS
- Hard-coded hex values where `var(--...)` exists
- Missing mobile collapse at 900px
