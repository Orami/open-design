---
name: supercompute-terminal-dossier
description: SUPERCOMPUTE Terminal Dossier design system — dark navy, gold signal, teal environment. Extracted from SupercomputeA/Master_Main. Use for all SUPERCOMPUTE web artifacts.
user-invocable: true
---

# SUPERCOMPUTE Terminal Dossier Design System

Agent-usable skill entry for the SUPERCOMPUTE design system. This system is extracted from the live codebase at `SupercomputeA/Master_Main` and is the canonical visual language for all SUPERCOMPUTE web artifacts.

## What's inside

This package contains the complete SUPERCOMPUTE Terminal Dossier design system, extracted from the live codebase at `SupercomputeA/Master_Main`:

| Path | Purpose | Source basis |
|---|---|---|
| `DESIGN.md` | Canonical design rules — color, type, spacing, layout, components, voice, anti-patterns | `DESIGN.md` (repo root), `styles/globals.css` |
| `colors_and_type.css` | Single source of truth CSS custom properties — import into every artifact | `styles/globals.css`, `DESIGN.md` color blocks |
| `preview/` | Reviewable HTML cards: colors, typography, spacing, components, brand assets | All预览 cards reference source components |
| `ui_kits/app/` | Applied interface kit — modular React components composed into a product-like surface | `components/Layout.tsx`, `components/Sidebar.tsx`, `components/AgentChat.tsx` |
| `source_examples/` | High-signal original component snapshots from the source codebase | `components/Sidebar.tsx`, `components/Layout.tsx`, `components/AgentChat.tsx`, `components/KGChat.tsx`, `components/entity-map/EntityMapChat.tsx` |
| `assets/` | Preserved brand assets | `public/SupercomputeLogo.png`, `public/admin/assets/favicon-eb31bc17.svg` |
| `build/` | Runtime build assets with original filenames | `public/SupercomputeLogo.png`, `public/admin/assets/favicon-eb31bc17.svg` |
| `README.md` | Package guide with Preview Manifest and reuse workflow | This file |

## Source context

This design system is evidence-backed. Every token was extracted from the following files in `SupercomputeA/Master_Main`:

- **Repository**: https://github.com/SupercomputeA/Master_Main
- **Read method**: git-clone (this-device, 47 snapshot files)
- **Evidence note**: `context/github/SupercomputeA-Master_Main.md`
- **Key source files**:
  - `DESIGN.md` (repo root) — canonical color palette, typography scale, spacing grid, component patterns, voice rules, forbidden list
  - `styles/globals.css` — layout shell (`.sidebar`, `.main`, `.hud-corner`, `.vignette`), CRT scanlines (`body::before`/`after`), all utility classes (`.sheet-row`, `.agent-card`, `.fleet-stat`, etc.)
  - `components/Layout.tsx` — app shell: flex layout with sidebar + main + HUD corners + vignette overlay
  - `components/Sidebar.tsx` — nav groups (`learn`, `build`, `economy`, `community`), active state with gold left border, `ConnectWallet` footer
  - `components/Hero.tsx` — `.hero` section with `.status-dot`, `.hero-title em`, `.hero-kicker`, `.hero-meta`
  - `components/AgentChat.tsx` — floating trigger (56×56 gold square), chat window (360×480), message thread, `Esc/Enter` keyboard shortcuts
  - `components/KGChat.tsx` — knowledge graph assistant with RAG-powered `@nodeLabel` source badges
  - `components/entity-map/EntityMapChat.tsx` — entity map chat with `TYPE_COLORS` for node types, node selection
  - `components/entity-map/constants.ts` — `TYPE_COLORS`, `TYPE_SHAPES`, `DEFAULT_GRAVITY`, `GRID_SIZE`
  - `components/ConnectWallet.tsx` — wallet connect with ENS resolution, Neynar profile, admin/member role badge
  - `components/AgentFleet.tsx` — 4-column `.fleet-stat` grid + 2-column `.agent-card` grid with `.agent-status.online/observer`

## When to use this skill

- Building any SUPERCOMPUTE web artifact (landing, dashboard, deck, admin UI, marketing page, knowledge graph UI)
- The user mentions "supercompute", "terminal dossier", "hermes terminal", or asks for the SUPERCOMPUTE look
- Designing for a dark-native Web3 / operator interface with gold signal accents
- The active design system is "site supercompute moc overview Design System"
- Building chat interfaces for AI agents (Condor, Hermes, Quanta)

## How to use

1. **Read `DESIGN.md` first** — it is the canonical rules document. Every token, pattern, and rule comes from there. The "Source Context" table maps each section to the exact source file that backs it.
2. **Import `colors_and_type.css`** in your artifact's `<link>` or inline it in a `<style>` block. Never invent new tokens — all values are from the source codebase.
3. **Read `preview/` cards** to see real component examples before building:
   - `preview/colors-primary.html` — palette swatches from `DESIGN.md`
   - `preview/typography-specimens.html` — display/body/mono from `DESIGN.md`
   - `preview/components-buttons.html` — from `styles/globals.css` `.btn` classes
   - `preview/spacing-radius.html` — source component examples from `AgentChat.tsx`, `AgentFleet.tsx`, `ConnectWallet.tsx`, `DialogueEngine.tsx`
4. **Copy `source_examples/`** patterns when you need original implementation reference (e.g., `source_examples/components/Sidebar.tsx` for nav group structure).
5. **For chat/workspace surfaces**, compose from `ui_kits/app/components/` — `App.jsx`, `Sidebar.jsx`, `AssistantsList.jsx`, `ChatArea.jsx`, `InputBar.jsx`, `MessageBubble.jsx`. The entry point `ui_kits/app/index.html` loads React and renders the composed `App` component.
6. **Bind tokens to `:root`** when using a framework that overrides defaults.
7. **Run the audit** before shipping: `"$OD_NODE_BIN" "$OD_BIN" tools connectors design-system-package-audit --path . --fail-on-warnings`

## Design system highlights

These highlights are grounded in source evidence from `SupercomputeA/Master_Main`:

- **Palette**: Deep navy (`#060912` → `#1a2235`), gold signal (`#c9a33a` / `#e8c87a`), teal environment (`#00d4b8`). Source: `DESIGN.md` color blocks + `styles/globals.css` `:root`.
- **Type**: Phosphate Bold display, IBM Plex Sans body, IBM Plex Mono data/labels. Source: `DESIGN.md` typography section.
- **Spacing**: 8px base grid, `--space-1` (4px) through `--space-10` (128px). Source: `DESIGN.md` spacing section.
- **Signature elements**: HUD corner brackets (`.hud-corner` from `globals.css`), CRT scanlines (`body::before`/`after`), 1px gold hairlines (`--color-border`), `//` terminal comment prefix (`.label` class). Source: `styles/globals.css`.
- **Component pattern**: Border-gap grids (`gap: 1px` + parent `border: 1px solid`), sharp 2px radius (`.card::before` corner accent), no rounded pills. Source: `globals.css` `.sheet-row`, `DESIGN.md` card section.
- **Voice**: Direct, technical, no fluff. "Operator" not "user". Uppercase labels with `letter-spacing: 0.1875rem`. Source: `DESIGN.md` voice section + `CLAUDE.md` writing rules.
- **Forbidden**: Light mode, Inter/Roboto display fonts, rounded cards >4px, purple gradients, generic emoji icons, invented metrics. Source: `DESIGN.md` "What Is Forbidden" section.
