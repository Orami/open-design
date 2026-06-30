# SUPERCOMPUTE Terminal Dossier Design System

> **Version**: 1.1.0
> **Source**: [SupercomputeA/Master_Main](https://github.com/SupercomputeA/Master_Main) (git-clone)
> **Category**: Custom design system for Web3 / operator terminal interfaces

---

## Product Overview

SUPERCOMPUTE is a sovereign AI-native Web3 platform built on Base Chain. The design system — **Terminal Dossier** — is the visual language for the entire platform: public marketing pages, member dashboards, admin interfaces, knowledge graph visualizations, and agent chat surfaces.

**Primary UI surfaces:**
- Public landing / marketing pages (Home, About, School, Consulting, Token)
- Member dashboard (Staking, Storefront, Knowledge Graph, Agent Fleet)
- Admin / operations interface
- NewsDesk CMS (separate product, shared design language)
- Agent chat interfaces (Condor trade agent, KG assistant)

**Core capabilities evidenced by source:**
- Web3 wallet connection (SIWE, ENS resolution, Neynar profiles)
- Token-gated access control
- Knowledge graph visualization (force-directed canvas)
- Agent fleet management dashboard
- Multi-platform publishing (X, Farcaster, Lens, Mirror)
- Staking and DeFi operations

---

## Package Contents

```
├── DESIGN.md                    # Canonical design rules (read first)
├── colors_and_type.css          # Single token source — import into every artifact
├── SKILL.md                     # Agent-facing skill entry
├── README.md                    # This file
├── preview/                     # Reviewable HTML cards
│   ├── colors-primary.html      # Primary palette (navy, gold, teal)
│   ├── colors-theme-dark.html   # Dark theme surface tokens
│   ├── typography-specimens.html # Display, body, mono specimens
│   ├── spacing-tokens.html      # Spacing scale and usage
│   ├── spacing-radius.html      # Radius and shadow tokens
│   ├── components-buttons.html  # Button variants
│   ├── components-inputs.html   # Input, textarea, form controls
│   ├── components-cards.html    # Sheet, project card, agent card
│   └── brand-assets.html        # Logo, favicon, brand marks
├── ui_kits/
│   └── app/
│       ├── index.html           # Composed interface entry
│       ├── README.md            # Kit documentation
│       └── components/          # Modular component files
│           ├── App.jsx
│           ├── Sidebar.jsx
│           ├── AssistantsList.jsx
│           ├── ChatArea.jsx
│           ├── InputBar.jsx
│           └── MessageBubble.jsx
├── source_examples/             # Original source component snapshots
│   ├── components/
│   │   ├── Layout.tsx
│   │   ├── Sidebar.tsx
│   │   ├── AgentChat.tsx
│   │   ├── KGChat.tsx
│   │   └── entity-map/EntityMapChat.tsx
│   └── functions/api/auth/message.js
├── assets/                      # Brand assets (logos, icons)
│   └── SupercomputeLogo.png
└── context/                     # Source evidence
    └── github/
        └── SupercomputeA-Master_Main.md
```

---

## Preview Manifest

Each `preview/*.html` card is a focused, self-contained review artifact. Open in the Design System tab to inspect.

| Path | What to inspect | Tokens / components demonstrated |
|---|---|---|
| `preview/colors-primary.html` | Primary palette swatches: navy surfaces, gold signal, teal environment, text tones, accents, borders | `--color-bg-primary`, `--color-gold`, `--color-teal`, `--color-text-*`, `--color-border-*` |
| `preview/colors-theme-dark.html` | Dark theme surface hierarchy: page bg → panel → elevated → hover | `--site-bg`, `--surface-0/1/2`, `--color-bg-secondary/tertiary` |
| `preview/typography-specimens.html` | Display (Phosphate Bold), body (IBM Plex Sans), mono (IBM Plex Mono) with scale specimens | `--font-display`, `--font-body`, `--font-mono`, `--text-xs` through `--text-4xl` |
| `preview/spacing-tokens.html` | 8px base scale visualization, usage patterns | `--space-1` through `--space-10` |
| `preview/spacing-radius.html` | Radius variants and shadow depths | `--radius-sm/md/lg`, `--shadow-*` |
| `preview/components-buttons.html` | All button variants: primary, outline, connect, fleet | `.btn`, `.btn-primary`, `.btn-outline`, `.btn-connect` |
| `preview/components-inputs.html` | Input fields, textareas, search, form layouts | Terminal-style inputs with gold focus |
| `preview/components-cards.html` | Sheet rows, project cells, agent cards, fleet stats | `.sheet-row`, `.proj-cell`, `.agent-card`, `.fleet-stat` |
| `preview/brand-assets.html` | Logo, favicon, brand marks with real asset references | `<img>` references to `assets/SupercomputeLogo.png` |

---

## Reuse Workflow

1. **Start with `DESIGN.md`** — read the full rules before writing any CSS.
2. **Import `colors_and_type.css`** — either `<link rel="stylesheet" href="colors_and_type.css">` or inline the `:root` block.
3. **Copy `source_examples/` patterns** when you need the original implementation reference for layout, navigation, or chat surfaces.
4. **For chat/workspace products**, start from `ui_kits/app/` — the modular components (`Sidebar.jsx`, `ChatArea.jsx`, `InputBar.jsx`, `MessageBubble.jsx`) compose into a full interface via `App.jsx`.
5. **Preview your work** using the `preview/` cards as a checklist — every token you use should appear in at least one card.
6. **Run the audit** before shipping:
   ```bash
   "$OD_NODE_BIN" "$OD_BIN" tools connectors design-system-package-audit --path . --fail-on-warnings
   ```

---

## Design System Highlights

- **Dark-native**: No light mode. Backgrounds range from `#060912` to `#1a2235`.
- **One accent**: Gold (`#c9a33a`) is the primary signal. Teal (`#00d4b8`) is the environment accent. Use gold at most twice per screen.
- **Monospace-first**: The entire UI uses mono for labels, data, and navigation. Display is reserved for hero headlines.
- **Border-gap grids**: `gap: 1px` + parent `border: 1px solid` creates hairline-separated cells — the signature Terminal Dossier pattern.
- **Sharp corners**: 2px radius on cards. No rounded pills.
- **CRT effects**: Scanlines + grid overlay + vignette are non-negotiable atmospheric elements.
- **HUD corners**: 4 gold brackets pinning the content area.

---

## Source References

| Source | Path in context |
|---|---|
| DESIGN.md (canonical) | `context/github/SupercomputeA-Master_Main/files/DESIGN.md` |
| globals.css (tokens + layout) | `context/github/SupercomputeA-Master_Main/files/styles/globals.css` |
| Layout.tsx (app shell) | `context/github/SupercomputeA-Master_Main/files/components/Layout.tsx` |
| Sidebar.tsx (navigation) | `context/github/SupercomputeA-Master_Main/files/components/Sidebar.tsx` |
| Hero.tsx (landing hero) | `context/github/SupercomputeA-Master_Main/files/components/Hero.tsx` |
| AgentChat.tsx (chat surface) | `context/github/SupercomputeA-Master_Main/files/components/AgentChat.tsx` |
| KGChat.tsx (KG assistant) | `context/github/SupercomputeA-Master_Main/files/components/KGChat.tsx` |
| EntityMapChat.tsx | `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapChat.tsx` |
| constants.ts (KG colors) | `context/github/SupercomputeA-Master_Main/files/components/entity-map/constants.ts` |
| package.json (metadata) | `context/github/SupercomputeA-Master_Main/files/package.json` |
