# site supercompute moc overview Design System

> Category: Custom
> Surface: web
> Source: [SupercomputeA/Master_Main](https://github.com/SupercomputeA/Master_Main) (git-clone)
> Locked: 2026-06-27

This design system is extracted from the live SUPERCOMPUTE codebase (`SupercomputeA/Master_Main`). All tokens, layout patterns, and component rules below are evidence-backed — derived from `DESIGN.md`, `styles/globals.css`, and production component source in that repository. Do not invent new tokens or override these values without filing a design issue.

## Source Context

| Source file | Role in this system |
|---|---|
| `DESIGN.md` (repo root) | Canonical color palette, typography, spacing, component patterns, voice rules, forbidden list |
| `styles/globals.css` | Layout shell (sidebar, main), CRT effects, HUD corners, all utility classes |
| `components/Layout.tsx` | App shell — flex layout with sidebar + main + HUD corners + vignette |
| `components/Sidebar.tsx` | Navigation groups, active state, wallet connect footer |
| `components/Hero.tsx` | Hero section — kicker, title, subtitle, actions, meta stats |
| `components/AgentChat.tsx` | Chat surface — floating trigger, message thread, input bar |
| `components/KGChat.tsx` | Knowledge graph assistant — RAG-powered chat with source badges |
| `components/entity-map/EntityMapChat.tsx` | Entity map chat — graph query, node selection, source badges |
| `components/entity-map/constants.ts` | KG entity type colors, shapes, gravity config |
| `components/ConnectWallet.tsx` | Wallet connection — ENS resolution, Neynar profile, admin badge |
| `components/AgentFleet.tsx` | Agent fleet — stat summary + agent cards with status |
| `components/Footer.tsx` | Footer — brand, link grid, social, copyright |
| `components/Staking.tsx` | Staking — 4-column stat grid |
| `components/School.tsx` | School — module list + CTA panel |
| `components/Projects.tsx` | Projects — 2-column grid with tags |
| `components/Services.tsx` | Services — consulting layout |
| `components/NeynarOnboarding.tsx` | Neynar onboarding — Farcaster profile |
| `pages/index.tsx` | Publishing home — hero + platform targets + article feed |
| `pages/token.tsx` | Token page — $SCOM with project TVL aggregation |
| `CLAUDE.md` | Agent instructions — deployment rules, naming conventions, priority queue |

**Evidence note**: `context/github/SupercomputeA-Master_Main.md` (git-clone, 47 snapshot files)

---

## 1. Visual Theme & Atmosphere

**SUPERCOMPUTE** is a sovereign AI-native Web3 platform. The visual identity is **"Hermes Terminal"** — operator terminal meets Solarpunk resistance. Every page should feel like a command interface built for a just future.

- Dark navy backgrounds. Gold signal. Teal environment.
- Fine 1px hairlines. Phosphate Bold for display. Monospace for data.
- Controlled density — no empty decorative space, no clutter.
- Every element earns its place.

The product context: a multi-tier web platform (Public / Member / Admin) with token-gated access, knowledge graphs, agent fleet management, NewsDesk publishing, and TradeDesk financial operations. The UI surfaces must communicate competence, sovereignty, and technical precision.

---

## 2. Color

All colors are defined as CSS custom properties in `colors_and_type.css`. Use these tokens — never raw hex values.

### Primary surfaces

| Token | Value | Role |
|---|---|---|
| `--site-bg` | `#060912` | Page background (deepest navy) |
| `--color-bg-primary` | `#0a0f1e` | Standard panel background |
| `--color-bg-secondary` | `#111827` | Card backgrounds |
| `--color-bg-tertiary` | `#1a2235` | Elevated surfaces |
| `--surface-0` | `#0a1330` | Sidebar background |
| `--surface-1` | `#0d1f3d` | Hover state |
| `--surface-2` | `#0a1e3d` | Secondary hover |

### Signal (Gold)

| Token | Value | Role |
|---|---|---|
| `--color-gold` | `#e8c87a` | Primary CTA, headings, key data |
| `--color-gold-dim` | `#b89a4a` | Secondary gold, borders |
| `--color-gold-glow` | `rgba(232,200,122,0.15)` | Glow effects |
| `--gold-warm` | `#c9a33a` | Site-specific warm gold (buttons, accents) |

### Environment (Teal)

| Token | Value | Role |
|---|---|---|
| `--color-teal` | `#00d4b8` | Links, active states, KG nodes |
| `--color-teal-dim` | `#007a6b` | Secondary teal |
| `--color-teal-glow` | `rgba(0,212,184,0.12)` | Glow effects |
| `--teal` | `#1a535c` | Tertiary accent (PROTOCOL_EVAL category) |

### Text

| Token | Value | Role |
|---|---|---|
| `--cream` / `--color-text-primary` | `#f0ebe0` | Body copy — warm white, not pure white |
| `--mono-blue` / `--color-text-secondary` | `#5a7ba8` / `#9ca3af` | Secondary text, metadata |
| `--color-text-muted` | `#4b5563` | Disabled, placeholders |

### Accents

| Token | Value | Role |
|---|---|---|
| `--color-sienna` | `#c4622d` | Warnings, alerts |
| `--color-sage` | `#6b8f71` | Success states |

### Borders

| Token | Value | Role |
|---|---|---|
| `--border` | `#1E3A5F` | Default terminal hairline |
| `--color-border` | `rgba(232,200,122,0.2)` | Gold hairline |
| `--border-warm` | `rgba(201,163,58,0.30)` | Warm gold border |
| `--color-border-teal` | `rgba(0,212,184,0.2)` | Teal hairline |
| `--color-border-subtle` | `rgba(255,255,255,0.06)` | Subtle panel borders |

### Knowledge Graph entity colors

| Token | Value | Entity |
|---|---|---|
| `--kg-protocol` | `#10b981` | Protocol |
| `--kg-token` | `#fbbf24` | Token |
| `--kg-agent` | `#ff6b35` | Agent |
| `--kg-concept` | `#a855f7` | Concept |
| `--kg-person` | `#60a5fa` | Person |
| `--kg-term` | `#3b82f6` | Term |
| `--kg-date` | `#94a3b8` | Date |
| `--kg-event` | `#f97316` | Event |
| `--kg-narrative` | `#c084fc` | Narrative |
| `--kg-image` | `#22d3ee` | Image |
| `--kg-officer` | `#f59e0b` | Officer |
| `--kg-incident` | `#0ea5e9` | Incident |
| `--kg-misconduct` | `#ef4444` | Misconduct |
| `--kg-department` | `#8b5cf6` | Department |
| `--kg-complaint` | `#06b6d4` | Complaint |
| `--kg-member` | `#60a5fa` | Member |
| `--kg-default` | `#64748b` | Default |

---

## 3. Typography

### Font stacks

| Role | Stack |
|---|---|
| **Display** | `'Phosphate', 'Arial Narrow', impact, sans-serif` Bold only — no regular weight |
| **Body** | `'IBM Plex Sans', 'Space Grotesk', system-ui, sans-serif` |
| **Mono / Data** | `'IBM Plex Mono', 'JetBrains Mono', ui-monospace, SFMono-Regular, Menlo, monospace` |

### Usage rules

- **Display** — Headings, hero text, nav brand. Uppercase, letter-spacing `0.05em`.
- **Body** — Paragraphs, descriptions. Weight 400, line-height 1.6.
- **Mono** — Metrics, addresses, timestamps, terminal output, section labels, code. Size `0.85em` relative to body context.

### Type scale

| Token | Size | Usage |
|---|---|---|
| `--text-xs` | 0.75rem (12px) | Labels, badges |
| `--text-sm` | 0.875rem (14px) | Metadata, captions |
| `--text-base` | 1rem (16px) | Body |
| `--text-lg` | 1.125rem (18px) | Lead text |
| `--text-xl` | 1.25rem (20px) | Card titles |
| `--text-2xl` | 1.5rem (24px) | Section headers |
| `--text-3xl` | 1.875rem (30px) | Page headers |
| `--text-4xl` | 2.25rem (36px) | Hero text |

### Display sizes (fluid)

| Class | Clamp | Usage |
|---|---|---|
| `.display-xl` | `clamp(44px, 7vw, 96px)` | Hero headline |
| `.display-lg` | `clamp(26px, 3.5vw, 48px)` | Page title |
| `.display-md` | `clamp(16px, 2vw, 24px)` | Section title |

---

## 4. Spacing

**Base unit: 8px.** All spacing is multiples of 8.

| Token | Value | Usage |
|---|---|---|
| `--space-1` | 4px | Tight gaps |
| `--space-2` | 8px | Inline gaps |
| `--space-3` | 12px | Compact padding |
| `--space-4` | 16px | Standard padding |
| `--space-5` | 24px | Section padding |
| `--space-6` | 32px | Large padding |
| `--space-7` | 48px | Hero padding |
| `--space-8` | 64px | Section vertical |
| `--space-9` | 96px | Large vertical |
| `--space-10` | 128px | Page-level |

### Radius

| Token | Value | Usage |
|---|---|---|
| `--radius-sm` | 2px | Cards (sharp corners — not rounded pill) |
| `--radius-md` | 4px | Inputs, buttons |
| `--radius-lg` | 8px | Chat bubbles, modals |

### Shadows

| Token | Value | Usage |
|---|---|---|
| `--shadow-sm` | `0 1px 3px rgba(0,0,0,0.4)` | Subtle elevation |
| `--shadow-md` | `0 4px 16px rgba(0,0,0,0.6)` | Cards, panels |
| `--shadow-lg` | `0 8px 32px rgba(0,0,0,0.8)` | Modals, chat windows |
| `--shadow-glow` | `0 0 20px var(--color-gold-glow)` | Active states |

---

## 5. Layout & Composition

### Page structure

```
Max content width: 1100px
Sidebar (nav): 220px fixed left
Main content: fluid, padding 48px
Mobile breakpoint: 900px — sidebar collapses to 60px icon rail
Small mobile: 520px — single column everywhere
```

### Grid patterns

- **2-column grid**: `grid-template-columns: repeat(2, 1fr)` — project cards, agent cards
- **3-column grid**: `grid-template-columns: repeat(3, 1fr)` — news cards
- **4-column grid**: `grid-template-columns: repeat(4, 1fr)` — fleet stats, staking cells
- **Border-gap pattern**: `gap: 1px` with `border: 1px solid var(--border)` on parent — creates hairline-separated cells (signature Terminal Dossier pattern)

### Section structure

```html
<section class="section">
  <div class="section-header">
    <div class="label">// section label</div>
    <div><h2 class="display-md">Title</h2></div>
  </div>
  <!-- content -->
</section>
```

### Responsive breakpoints

| Breakpoint | Behavior |
|---|---|
| `> 900px` | Full sidebar + multi-column grids |
| `≤ 900px` | Sidebar collapses to 60px icon rail, grids reduce columns |
| `≤ 520px` | Single column, stacked layouts |

---

## 6. Components

### Buttons

| Class | Behavior |
|---|---|
| `.btn` | Base: mono 11px, uppercase, 0.12rem letter-spacing, border |
| `.btn-primary` | Gold background, navy text |
| `.btn-outline` | Transparent, border hover → gold |
| `.btn-connect` | Full-width gold button (wallet connect) |

### Cards (DATACENTER aesthetic)

```css
.card {
  background: var(--color-bg-secondary);
  border: 1px solid var(--color-border);
  border-radius: 2px;           /* Sharp corners — not rounded pill */
  padding: var(--space-5);
  position: relative;
}
/* Top-left corner accent */
.card::before {
  content: '';
  position: absolute;
  top: -1px; left: -1px;
  width: 12px; height: 12px;
  border-top: 2px solid var(--color-gold);
  border-left: 2px solid var(--color-gold);
}
```

### Sheet (data table)

```html
<div class="sheet">
  <div class="sheet-row">
    <div class="num">01</div>
    <div class="body">Content</div>
    <div class="price">$1,200</div>
  </div>
</div>
```

### Project grid

```html
<div class="proj-grid">
  <div class="proj-cell">
    <div class="proj-tag">CATEGORY</div>
    <div class="proj-name">Project Name</div>
    <div class="proj-detail">Description text</div>
  </div>
</div>
```

### Agent fleet

- 4-column stat summary (`.fleet-stat` + `.fleet-stat-num`)
- 2-column agent cards with name, role, description, status badge
- Status: `.agent-status.online` (green) / `.agent-status.observer` (gold)

### Staking

- 4-column grid (`.stake-grid`)
- Large value display (`.stake-val`) with accent variant

### News grid

- 3-column (`.news-card`)
- Category tag, title, metadata with border-top separator

### School modules

- Left column: module list (`.mod-row` with number, name, duration)
- Right column: CTA panel (`.school-cta`)

### Footer

- 2-column grid: brand + 3-column link grid
- Bottom row: copyright + social links

### Hero section

```html
<section class="hero">
  <div class="hero-kicker">
    <div class="status-dot"></div>
    <span class="label">// operator terminal</span>
  </div>
  <h1 class="display-xl hero-title">LINE<br />LINE<br /><em>EMPHASIS</em></h1>
  <p class="hero-sub">Description text</p>
  <div class="hero-actions"><!-- buttons --></div>
  <div class="hero-meta"><!-- stat items --></div>
</section>
```

### Terminal comment prefix

Section labels use `//` prefix in gold monospace — this is the voice of the interface:

```html
<span class="section-label">// knowledge graph</span>
```

### Status indicators

```css
.status-live    { color: var(--color-teal); }
.status-pending { color: var(--color-gold); }
.status-offline { color: var(--color-text-muted); }
/* Pulse dot for live */
.pulse::before {
  content: '●';
  animation: pulse 2s infinite;
}
```

### HUD corners

4 viewport-pinned brackets in gold. Signature Terminal Dossier element.

```html
<div class="hud-corner tl" />
<div class="hud-corner tr" />
<div class="hud-corner bl" />
<div class="hud-corner br" />
```

### CRT effects (non-negotiable)

- `body::before` — 56px grid overlay at 3% white
- `body::after` — horizontal scanlines, multiply blend, 65% opacity
- `.vignette` — radial gradient darkening edges

---

## 7. Motion & Interaction

### Transitions

| Token | Value | Usage |
|---|---|---|
| `--t-fast` | `0.15s ease` | Buttons, links, nav |
| `--t-med` | `0.25s ease` | Panels, modals |

### Hover states

- Buttons: opacity 0.85 or border-color shift to gold
- Nav links: `background: var(--white-04)`, active gets gold left border
- Cards/panels: `background: var(--surface-1)`
- Footer links: color → gold

### Animations

```css
/* Pulse for status dot */
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.4; }
}

/* Spin for loading */
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
```

### Reduced motion

All animations are subtle (opacity, color). No motion-dependent interactions. Respect `prefers-reduced-motion` for any future animation additions.

---

## 8. Voice & Brand

### Copy style

- Section labels: `// lowercase monospace` in gold
- Status: `LIVE`, `PENDING`, `ARCHIVED` — uppercase, no punctuation
- Dates: ISO-adjacent `2026-06-07` or `Jun 07` — never `June 7th, 2026`
- Addresses: truncated `0x89ac...d0c0` — never full hash in UI
- Version: `v1.1.0` — always lowercase v

### Tone

- Direct, technical, no marketing fluff
- "Operator" not "user"
- "Sovereign" not "empowering"
- Every word must earn its place — no filler

### Capitalization

- Nav items: uppercase (`HOME`, `SCHOOL`, `PROJECTS`)
- Section headers: uppercase display
- Body: sentence case
- Labels: uppercase with wide letter-spacing

---

## 9. Anti-patterns

These are explicitly forbidden:

- ❌ Purple gradients on white backgrounds
- ❌ Inter, Roboto, Arial as display fonts
- ❌ Rounded corners > 4px on cards (sharp 2px is the signature)
- ❌ Generic hero sections with stock illustration style
- ❌ Light mode (this platform is dark-native)
- ❌ Any new color not in this palette without filing a design issue
- ❌ Spinner placeholders in production (`// loading...` is a dev state)
- ❌ Warm beige / cream / peach / pink / orange-brown page backgrounds
- ❌ Generic emoji feature icons (✨ 🚀 🎯)
- ❌ Invented metrics without source
- ❌ Filler copy — "Feature One / Feature Two", lorem ipsum
- ❌ An icon next to every heading
- ❌ A gradient on every background
- ❌ Rounded card with a left coloured border accent (use HUD corner instead)

---

## Source references

- **Repository**: https://github.com/SupercomputeA/Master_Main
- **DESIGN.md**: `context/github/SupercomputeA-Master_Main/files/DESIGN.md`
- **globals.css**: `context/github/SupercomputeA-Master_Main/files/styles/globals.css`
- **Layout.tsx**: `context/github/SupercomputeA-Master_Main/files/components/Layout.tsx`
- **Sidebar.tsx**: `context/github/SupercomputeA-Master_Main/files/components/Sidebar.tsx`
- **Hero.tsx**: `context/github/SupercomputeA-Master_Main/files/components/Hero.tsx`
- **AgentChat.tsx**: `context/github/SupercomputeA-Master_Main/files/components/AgentChat.tsx`
- **KGChat.tsx**: `context/github/SupercomputeA-Master_Main/files/components/KGChat.tsx`
- **EntityMapChat.tsx**: `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapChat.tsx`
- **constants.ts (KG colors)**: `context/github/SupercomputeA-Master_Main/files/components/entity-map/constants.ts`
- **package.json**: `context/github/SupercomputeA-Master_Main/files/package.json`
