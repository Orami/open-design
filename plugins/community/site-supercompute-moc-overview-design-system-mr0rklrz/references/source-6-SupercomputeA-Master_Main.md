# GitHub Design Evidence: SupercomputeA/Master_Main

Source: https://github.com/SupercomputeA/Master_Main
Read method: git-clone
Local clone method: git clone
Ref: default branch
Repository paths discovered: 242
Snapshot files written: 47

## Intake Status

- This-device intake was used through local git or GitHub CLI.

## README (README.md)

```md
# SUPERCOMPUTE · Web3 Platform

Sovereign AI-native platform on Base Chain — NewsDesk intelligence, DeFi operations, consulting, and principled Web3 education.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Cloudflare Stack                        │
├─────────────────────────────────────────────────────────────┤
│  Workers (API)  │  D1 (SQLite)  │  KV (Sessions)  │  R2 (Storage)  │
│  Pages (Frontend)  │  Access (Auth)  │  Durable Objects  │
└─────────────────────────────────────────────────────────────┘
```

## Quick Start

### Prerequisites

- Node.js 18+
- npm or yarn
- Cloudflare account (`wrangler` CLI)

### 1. Install Dependencies

```bash
npm install
```

### 2. Local Development

```bash
# Serve static files locally
npx serve public

# Or use any local server
python -m http.server 8080
```

### 3. Validate Build

```bash
bash validate.sh
```

### 4. Deploy

```bash
# Deploy to Cloudflare Pages
npx wrangler pages deploy public --project-name=artifact-main
```

## CI/CD Setup

### GitHub Actions (Automatic Deploy)

1. **Add Secrets** to your GitHub repo:
   - Go to: Settings → Secrets and variables → Actions
   - Add:
     - `CLOUDFLARE_API_TOKEN` - Your Cloudflare API token
     - `CLOUDFLARE_ACCOUNT_ID` - Your Cloudflare account ID

2. **Push to main** - Deploys automatically

### What CI/CD Does

- ✅ Validates HTML structure
- ✅ Checks required files exist
- ✅ Scans for code issues
- ✅ Deploys to Cloudflare Pages on main branch
- ✅ Runs on every PR and push

## Project Structure

```
/supercompute
├── .github/workflows/ci-cd.yml  # CI/CD pipeline
├── validate.sh                   # Build validation script
├── wrangler.toml                # Cloudflare config
├── package.json                 # Scripts
├── schema.sql                  # D1 database schema
│
├── public/                     # Static assets (deployed)
│   ├── Supercompute.html     # Main SPA
│   ├── sc.css               # Styles
│   ├── sc-app.jsx           # React components
│   └── siwe-client.js       # SIWE auth client
│
└── src/                       # Cloudflare Worker source
    ├── worker.js             # Main entry
    └── api/                  # API routes
        ├── auth.js          # SIWE auth
        ├── articles.js     # NewsDesk API
        ├── staking.js       # Staking API
        └── agents.js        # Agent fle
...
```

## Source Evidence Inventory

### Product docs and manifests

Use these to understand product purpose, dependency stack, scripts, and public naming.

- package.json -> `context/github/SupercomputeA-Master_Main/files/package.json` (source)

### Brand assets and icons

Preserve source build/runtime paths: files under `build/` should be copied back into root `build/` with their original filenames, while non-build logos, avatars, or wordmarks can be copied into `assets/`. Reflect the preserved files in `preview/brand-assets.html`.

- public/admin/assets/favicon-eb31bc17.svg -> `context/github/SupercomputeA-Master_Main/files/public/admin/assets/favicon-eb31bc17.svg` (source)
- public/SupercomputeLogo.png -> `context/github/SupercomputeA-Master_Main/files/public/SupercomputeLogo.png` (binary asset)

### Theme, tokens, and styling

Extract concrete color, typography, spacing, radius, shadow, and theme-variable values from these files.

- components/entity-map/constants.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/constants.ts` (source)
- DESIGN.md -> `context/github/SupercomputeA-Master_Main/files/DESIGN.md` (source)
- pages/token.tsx -> `context/github/SupercomputeA-Master_Main/files/pages/token.tsx` (source)
- styles/globals.css -> `context/github/SupercomputeA-Master_Main/files/styles/globals.css` (source)
- src/utils/siwe.js -> `context/github/SupercomputeA-Master_Main/files/src/utils/siwe.js` (source)
- src/utils/wallet.js -> `context/github/SupercomputeA-Master_Main/files/src/utils/wallet.js` (source)
- components/NeynarOnboarding.module.css -> `context/github/SupercomputeA-Master_Main/files/components/NeynarOnboarding.module.css` (source)

### App shell and navigation

Use these to recreate the product frame, navigation density, sidebars, window chrome, and layout rhythm.

- components/Layout.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Layout.tsx` (source)
- components/Sidebar.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Sidebar.tsx` (source)

### Chat and input surfaces

Use these for the applied UI-kit surface and interaction model when the product includes chat or composer flows.

- functions/api/auth/message.js -> `context/github/SupercomputeA-Master_Main/files/functions/api/auth/message.js` (source)
- components/AgentChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/AgentChat.tsx` (source)
- components/entity-map/EntityMapChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapChat.tsx` (source)
- components/KGChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/KGChat.tsx` (source)

### Other design evidence

Inspect these only after the primary design evidence above has been used.

- components/Web3Provider.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Web3Provider.tsx` (source)
- pages/index.tsx -> `context/github/SupercomputeA-Master_Main/files/pages/index.tsx` (source)
- .claude/CLAUDE.md -> `context/github/SupercomputeA-Master_Main/files/.claude/CLAUDE.md` (source)
- CHANGELOG.md -> `context/github/SupercomputeA-Master_Main/files/CHANGELOG.md` (source)
- CLAUDE.md -> `context/github/SupercomputeA-Master_Main/files/CLAUDE.md` (source)
- components/About.tsx -> `context/github/SupercomputeA-Master_Main/files/components/About.tsx` (source)
- components/AgentFleet.tsx -> `context/github/SupercomputeA-Master_Main/files/components/AgentFleet.tsx` (source)
- components/ConnectWallet.tsx -> `context/github/SupercomputeA-Master_Main/files/components/ConnectWallet.tsx` (source)
- components/DialogueEngine.tsx -> `context/github/SupercomputeA-Master_Main/files/components/DialogueEngine.tsx` (source)
- components/entity-map/EntityMapCanvas.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapCanvas.tsx` (source)
- components/entity-map/EntityMapDetailPanel.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapDetailPanel.tsx` (source)
- components/entity-map/EntityMapNarrative.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapNarrative.tsx` (source)
- components/entity-map/EntityMapPath.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapPath.tsx` (source)
- components/entity-map/EntityMapTimeline.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapTimeline.tsx` (source)
- components/entity-map/EntityMapToolbar.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapToolbar.tsx` (source)
- components/entity-map/index.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/index.tsx` (source)
- components/entity-map/types.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/types.ts` (source)
- components/entity-map/useEntityMap.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/useEntityMap.tsx` (source)
- components/entity-map/usePhysicsEngine.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/usePhysicsEngine.ts` (source)
- components/entity-map/utils.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/utils.ts` (source)
- components/FarcasterFeed.tsx -> `context/github/SupercomputeA-Master_Main/files/components/FarcasterFeed.tsx` (source)
- components/FiatRamp.tsx -> `context/github/SupercomputeA-Master_Main/files/components/FiatRamp.tsx` (source)
- components/Footer.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Footer.tsx` (source)
- components/Hero.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Hero.tsx` (source)
- components/KnowledgeGraph.tsx -> `context/github/SupercomputeA-Master_Main/files/components/KnowledgeGraph.tsx` (source)
- components/NeynarOnboarding.tsx -> `context/github/SupercomputeA-Master_Main/files/components/NeynarOnboarding.tsx` (source)
- components/Projects.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Projects.tsx` (source)
- components/School.tsx -> `context/github/SupercomputeA-Master_Main/files/components/School.tsx` (source)
- components/Services.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Services.tsx` (source)
- components/ShopifyStorefront.tsx -> `context/github/SupercomputeA-Master_Main/files/components/ShopifyStorefront.tsx` (source)
- components/Staking.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Staking.tsx` (source)


## Files Inspected

- public/admin/assets/favicon-eb31bc17.svg -> `context/github/SupercomputeA-Master_Main/files/public/admin/assets/favicon-eb31bc17.svg` (1179 bytes, git-clone)
- public/SupercomputeLogo.png -> `context/github/SupercomputeA-Master_Main/files/public/SupercomputeLogo.png` (226951 bytes, git-clone, binary asset)
- components/entity-map/constants.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/constants.ts` (1638 bytes, git-clone)
- DESIGN.md -> `context/github/SupercomputeA-Master_Main/files/DESIGN.md` (7271 bytes, git-clone)
- package.json -> `context/github/SupercomputeA-Master_Main/files/package.json` (1614 bytes, git-clone)
- pages/token.tsx -> `context/github/SupercomputeA-Master_Main/files/pages/token.tsx` (7815 bytes, git-clone)
- styles/globals.css -> `context/github/SupercomputeA-Master_Main/files/styles/globals.css` (20889 bytes, git-clone)
- src/utils/siwe.js -> `context/github/SupercomputeA-Master_Main/files/src/utils/siwe.js` (2063 bytes, git-clone)
- src/utils/wallet.js -> `context/github/SupercomputeA-Master_Main/files/src/utils/wallet.js` (1686 bytes, git-clone)
- components/Layout.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Layout.tsx` (1062 bytes, git-clone)
- components/Sidebar.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Sidebar.tsx` (3063 bytes, git-clone)
- components/Web3Provider.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Web3Provider.tsx` (500 bytes, git-clone)
- functions/api/auth/message.js -> `context/github/SupercomputeA-Master_Main/files/functions/api/auth/message.js` (1437 bytes, git-clone)
- pages/index.tsx -> `context/github/SupercomputeA-Master_Main/files/pages/index.tsx` (7059 bytes, git-clone)
- .claude/CLAUDE.md -> `context/github/SupercomputeA-Master_Main/files/.claude/CLAUDE.md` (3411 bytes, git-clone)
- CHANGELOG.md -> `context/github/SupercomputeA-Master_Main/files/CHANGELOG.md` (1643 bytes, git-clone)
- CLAUDE.md -> `context/github/SupercomputeA-Master_Main/files/CLAUDE.md` (4138 bytes, git-clone)
- components/About.tsx -> `context/github/SupercomputeA-Master_Main/files/components/About.tsx` (1667 bytes, git-clone)
- components/AgentChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/AgentChat.tsx` (7529 bytes, git-clone)
- components/AgentFleet.tsx -> `context/github/SupercomputeA-Master_Main/files/components/AgentFleet.tsx` (2443 bytes, git-clone)
- components/ConnectWallet.tsx -> `context/github/SupercomputeA-Master_Main/files/components/ConnectWallet.tsx` (2869 bytes, git-clone)
- components/DialogueEngine.tsx -> `context/github/SupercomputeA-Master_Main/files/components/DialogueEngine.tsx` (8404 bytes, git-clone)
- components/entity-map/EntityMapCanvas.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapCanvas.tsx` (16591 bytes, git-clone)
- components/entity-map/EntityMapChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapChat.tsx` (7300 bytes, git-clone)
- components/entity-map/EntityMapDetailPanel.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapDetailPanel.tsx` (5971 bytes, git-clone)
- components/entity-map/EntityMapNarrative.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapNarrative.tsx` (6104 bytes, git-clone)
- components/entity-map/EntityMapPath.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapPath.tsx` (4441 bytes, git-clone)
- components/entity-map/EntityMapTimeline.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapTimeline.tsx` (4149 bytes, git-clone)
- components/entity-map/EntityMapToolbar.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/EntityMapToolbar.tsx` (3751 bytes, git-clone)
- components/entity-map/index.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/index.tsx` (2722 bytes, git-clone)
- components/entity-map/types.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/types.ts` (1377 bytes, git-clone)
- components/entity-map/useEntityMap.tsx -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/useEntityMap.tsx` (8604 bytes, git-clone)
- components/entity-map/usePhysicsEngine.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/usePhysicsEngine.ts` (3639 bytes, git-clone)
- components/entity-map/utils.ts -> `context/github/SupercomputeA-Master_Main/files/components/entity-map/utils.ts` (5960 bytes, git-clone)
- components/FarcasterFeed.tsx -> `context/github/SupercomputeA-Master_Main/files/components/FarcasterFeed.tsx` (3617 bytes, git-clone)
- components/FiatRamp.tsx -> `context/github/SupercomputeA-Master_Main/files/components/FiatRamp.tsx` (10455 bytes, git-clone)
- components/Footer.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Footer.tsx` (1764 bytes, git-clone)
- components/Hero.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Hero.tsx` (1466 bytes, git-clone)
- components/KGChat.tsx -> `context/github/SupercomputeA-Master_Main/files/components/KGChat.tsx` (14928 bytes, git-clone)
- components/KnowledgeGraph.tsx -> `context/github/SupercomputeA-Master_Main/files/components/KnowledgeGraph.tsx` (17288 bytes, git-clone)
- components/NeynarOnboarding.module.css -> `context/github/SupercomputeA-Master_Main/files/components/NeynarOnboarding.module.css` (3675 bytes, git-clone)
- components/NeynarOnboarding.tsx -> `context/github/SupercomputeA-Master_Main/files/components/NeynarOnboarding.tsx` (4858 bytes, git-clone)
- components/Projects.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Projects.tsx` (1603 bytes, git-clone)
- components/School.tsx -> `context/github/SupercomputeA-Master_Main/files/components/School.tsx` (1818 bytes, git-clone)
- components/Services.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Services.tsx` (1450 bytes, git-clone)
- components/ShopifyStorefront.tsx -> `context/github/SupercomputeA-Master_Main/files/components/ShopifyStorefront.tsx` (8356 bytes, git-clone)
- components/Staking.tsx -> `context/github/SupercomputeA-Master_Main/files/components/Staking.tsx` (1856 bytes, git-clone)

## Binary Assets Preserved

- public/SupercomputeLogo.png -> `context/github/SupercomputeA-Master_Main/files/public/SupercomputeLogo.png`

## Design-Relevant Excerpts

### public/admin/assets/favicon-eb31bc17.svg

```
<svg viewBox="0 0 32 32" fill="#EC4815" xmlns="http://www.w3.org/2000/svg">
  <path d="M18.6466 14.5553C19.9018 13.5141 20.458 7.36086 21.0014 5.14903C21.5447 2.9372 23.7919 3.04938 23.7919 3.04938C23.7919 3.04938 23.2085 4.06764 23.4464 4.82751C23.6844 5.58738 25.3145 6.26662 25.3145 6.26662L24.9629 7.19622C24.9629 7.19622 24.2288 7.10204 23.7919 7.9785C23.355 8.85496 24.3392 17.4442 24.3392 17.4442C24.3392 17.4442 21.4469 22.7275 21.4469 24.9206C21.4469 27.1136 22.4819 28.9515 22.4819 28.9515H21.0296C21.0296 28.9515 18.899 26.4086 18.462 25.1378C18.0251 23.8669 18.1998 22.596 18.1998 22.596C18.1998 22.596 15.8839 22.4646 13.8303 22.596C11.7767 22.7275 10.4072 24.498 10.16 25.4884C9.91287 26.4787 9.81048 28.9515 9.81048 28.9515H8.66211C7.96315 26.7882 7.40803 26.0129 7.70918 24.9206C8.54334 21.8949 8.37949 20.1788 8.18635 19.4145C7.99321 18.6501 6.68552 17.983 6.68552 17.983C7.32609 16.6741 7.97996 16.0452 10.7926 15.9796C13.6052 15.914 17.3915 15.5965 18.6466 14.5553Z"/>
  <path d="M11.1268 24.7939C11.1268 24.7939 11.4236 27.5481 13.0001 28.9516H14.3511C13.0001 27.4166 12.8527 23.4155 12.8527 23.4155C12.1656 23.6399 11.3045 24.3846 11.1268 24.7939Z"/>
</svg>

```

### components/entity-map/constants.ts

```ts
import type { EntityNodeType, NodeShape, GravityConfig } from "./types"

export const TYPE_COLORS: Record<string, string> = {
  protocol: "#10b981",
  token: "#fbbf24",
  agent: "#ff6b35",
  concept: "#a855f7",
  person: "#60a5fa",
  term: "#3b82f6",
  date: "#94a3b8",
  event: "#f97316",
  narrative: "#c084fc",
  image: "#22d3ee",
  officer: "#f59e0b",
  incident: "#0ea5e9",
  misconduct: "#ef4444",
  department: "#8b5cf6",
  complaint: "#06b6d4",
  member: "#60a5fa",
  default: "#64748b",
}

export const TYPE_SHAPES: Record<string, NodeShape> = {
  protocol: "circle",
  token: "circle",
  agent: "circle",
  concept: "circle",
  person: "circle",
  term: "roundedRect",
  date: "diamond",
  event: "hexagon",
  narrative: "arrow",
  image: "square",
  officer: "circle",
  incident: "hexagon",
  misconduct: "diamond",
  department: "square",
  complaint: "roundedRect",
  member: "circle",
  default: "circle",
}

export const TYPE_LABELS: Record<string, string> = {
  protocol: "Protocol",
  token: "Token",
  agent: "Agent",
  concept: "Concept",
  person: "Person",
  term: "Term",
  date: "Date",
  event: "Event",
  narrative: "Narrative",
  image: "Image",
  officer: "Officer",
  incident: "Incident",
  misconduct: "Misconduct",
  department: "Department",
  complaint: "Complaint",
  member: "Member",
}

export const DEFAULT_GRAVITY: Required<GravityConfig> = {
  damping: 0.85,
  repulsion: 4000,
  attraction: 0.006,
  centerForce: 0.003,
  edgeWeightMultiplier: 1.5,
}

export const GRID_SIZE = 40
export const BASE_NODE_RADIUS = 8
export const MAX_CONNECTION_BONUS = 10
export const CONNECTION_RADIUS_FACTOR = 1.2

```

### DESIGN.md

```
# DESIGN.md — SUPERCOMPUTE Design System
> Locked. Read before touching any frontend file. This is law.

## Identity
**SUPERCOMPUTE** — Hermes Terminal Aesthetic  
Sovereign AI-native platform. Liberation technology. Not extraction machinery.  
Visual identity: **operator terminal meets Solarpunk resistance**.  
Every page should feel like a command interface built for a just future.

## Core Aesthetic: Hermes Terminal
- Dark navy backgrounds. Gold signal. Teal environment.
- Fine 1px lines. Phosphate Solid for display. Monospace for data.
- Controlled density — no empty decorative space, no clutter.
- Every element earns its place.

---

## Color Palette

```css
:root {
  /* Primary */
  --color-bg-primary:    #0a0f1e;   /* Deep navy — page background */
  --color-bg-secondary:  #111827;   /* Slightly lighter — card backgrounds */
  --color-bg-tertiary:   #1a2235;   /* Elevated surfaces */

  /* Signal (Gold) */
  --color-gold:          #e8c87a;   /* Primary CTA, headings, key data */
  --color-gold-dim:      #b89a4a;   /* Secondary gold, borders */
  --color-gold-glow:     rgba(232, 200, 122, 0.15); /* Glow effects */

  /* Environment (Teal) */
  --color-teal:          #00d4b8;   /* Links, active states, KG nodes */
  --color-teal-dim:      #007a6b;   /* Secondary teal */
  --color-teal-glow:     rgba(0, 212, 184, 0.12);

  /* Text */
  --color-text-primary:  #f0ebe0;   /* Body copy — warm white, not pure white */
  --color-text-secondary:#9ca3af;   /* Secondary text, metadata */
  --color-text-muted:    #4b5563;   /* Disabled, placeholders */

  /* Accent */
  --color-sienna:        #c4622d;   /* Warnings, alerts */
  --color-sage:          #6b8f71;   /* Success states */

  /* Borders & Lines */
  --color-border:        rgba(232, 200, 122, 0.2);  /* Gold hairline — default border */
  --color-border-teal:   rgba(0, 212, 184, 0.2);    /* Teal hairline */
  --color-border-subtle: rgba(255, 255, 255, 0.06); /* Subtle panel borders */
}
```

---

## Typography

```css
/* Display — Headings, hero text, nav brand */
font-family: 'Phosphate Solid', 'Phosphate', impact, sans-serif;
letter-spacing: 0.05em;
text-transform: uppercase;

/* Body — Paragraphs, descriptions */
font-family: 'IBM Plex Sans', 'Space Grotesk', system-ui, sans-serif;
font-weight: 400;
line-height: 1.6;

/* Data / Code — Metrics, addresses, timestamps, terminal output */
font-family: 'IBM P
...
```

### package.json

```json
{
  "name": "supercompute",
  "version": "1.1.0",
  "description": "QUANTA - Sovereign Compute Platform on Base Chain",
  "type": "module",
  "scripts": {
    "dev": "tinacms dev -c \"wrangler dev\"",
    "tina:dev": "tinacms dev -c \"next dev\"",
    "tina:build": "tinacms build",
    "build": "npx esbuild src/worker.js --bundle --outfile=dist/worker.js --format=esm --platform=neutral --target=es2020 --minify",
    "next:build": "npx next build",
    "full:build": "npx tinacms build && npx next build",
    "deploy": "wrangler pages deploy out --project-name=supercompute",
    "deploy:staging": "wrangler pages deploy out --project-name=supercompute --branch staging --commit-dirty=true",
    "db:create": "wrangler d1 create supercompute",
    "db:push": "wrangler d1 execute supercompute --local --file=./schema.sql",
    "db:push:prod": "wrangler d1 execute supercompute --file=./schema.sql --env production",
    "preview": "wrangler pages project . --preview"
  },
  "dependencies": {
    "@cloudflare/workers-types": "^4.20250430.0",
    "@tanstack/react-query": "^5.100.11",
    "@tinacms/cli": "^2.3.1",
    "fs-extra": "^11.3.5",
    "neo4j-driver": "^6.0.1",
    "next": "^16.2.6",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "tinacms": "^3.8.1",
    "viem": "^2.48.11",
    "wagmi": "^3.6.15"
  },
  "devDependencies": {
    "@types/node": "^25.9.1",
    "@types/react": "^19.2.15",
    "@types/react-dom": "^19.2.3",
    "esbuild": "^0.24.0",
    "typescript": "^6.0.3",
    "wrangler": "^4.0.0"
  },
  "packageManager": "yarn@1.22.22+sha1.ac34549e6aa8e7ead463a7407e1c7390f61a6610"
}
```

### pages/token.tsx

```tsx
import type { GetStaticProps } from "next"
import Link from "next/link"
import Layout from "../components/Layout"
import Footer from "../components/Footer"
import { getAllProjects, type Project } from "../lib/content"

export const getStaticProps: GetStaticProps = async () => {
  const projects = await getAllProjects()
  return { props: { projects } }
}

export default function Token({ projects }: { projects: Project[] }) {
  const projectTokens = projects.filter(p => p.tokenSymbol)
  const totalTVL = projects.reduce((sum, p) => {
    const n = Number((p.tvl || "0").replace(/[^0-9.]/g, "")) || 0
    const isM = (p.tvl || "").toLowerCase().includes("m")
    const isK = (p.tvl || "").toLowerCase().includes("k")
    return sum + n * (isM ? 1_000_000 : isK ? 1_000 : 1)
  }, 0)
  const totalRaised = projects.reduce((sum, p) => sum + (p.raised || 0), 0)
  const totalInvestors = projects.reduce((sum, p) => sum + (p.investors || 0), 0)

  return (
    <Layout title="SUPERCOMPUTE · $SCOM Token">
      <section className="hero" id="token">
        <div className="hero-kicker">
          <div className="status-dot" />
          <span className="label">// token</span>
        </div>
        <h1 className="display-xl hero-title">
          $SCOM<br /><em>TOKEN</em>
        </h1>
        <p className="hero-sub">
          Builder coin on Base Chain. Rewards stakers from protocol revenue.
          Live Q3 2026. Stake to earn a share of trading fees.
        </p>
        <div className="hero-meta">
          <div className="meta-item">
            <div className="label-sm">// Network</div>
            <div className="val">Base L2</div>
          </div>
          <div className="meta-item">
            <div className="label-sm">// Est. APY</div>
            <div className="val">~12%</div>
          </div>
          <div className="meta-item">
            <div className="label-sm">// Launch</div>
            <div className="val">Q3 2026</div>
          </div>
        </div>
      </section>

      <section className="section">
        <div className="section-header">
          <div className="label">// ecosystem</div>
          <div><h2 className="display-md">Ecosystem Stats</h2></div>
        </div>
        <div style={{ display: "grid", gridTemplateColumns: "repeat(4, 1fr)", gap: 1, background: "var(--border)", border: "1px solid var(--border)" }}>
          <div style={{ 
...
```

### styles/globals.css

```css
/* ═══════════════════════════════════════════════════════════════════════════
   SUPERCOMPUTE — Next.js Publishing App
   Terminal Dossier design system. Single token source: colors_and_type.css
   (cloned from SupercomputeA/DesignDesk). Site-specific aliases + layout
   shell below. No orphan hex values.
   ═══════════════════════════════════════════════════════════════════════════ */

@import url('./colors_and_type.css');

/* ─── Site-specific aliases (canonical vars take precedence when used) ─── */

:root {
  /* Convenience aliases for legacy class names in this layout shell */
  --bg:        var(--site-bg);
  --fg:        var(--cream);
  --accent:    var(--gold-warm);
  --muted:     var(--mono-blue);

  /* Site-specific surfaces (sidebar, elevated rows) */
  --surface-0: #0a1330;
  --surface-1: #0d1f3d;
  --surface-2: #0a1e3d;

  /* Terminal Dossier hairlines */
  --border:      #1E3A5F;
  --border-warm: rgba(201, 163, 58, 0.30);

  /* Tertiary accent (PROTOCOL_EVAL category, etc.) */
  --teal: #1a535c;
}

/* ─── BASE ──────────────────────────────────────────────────────────────── */

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scrollbar-gutter: stable; height: 100%; }

body {
  font-family: var(--font-mono);
  font-size: var(--fs-14);
  line-height: 1.7;
  letter-spacing: .3px;
  background: var(--site-bg);
  color: var(--cream);
  min-height: 100vh;
  height: 100vh;
  overflow: hidden;
  -webkit-font-smoothing: antialiased;
  position: relative;
}

::selection { background: var(--gold-warm); color: var(--site-bg); }

/* ─── CRT effect (non-negotiable per brief, z-index law) ──────────────── */

body::before {
  content: ''; position: fixed; inset: 0; z-index: 0; pointer-events: none;
  background-image:
    linear-gradient(0deg,  rgba(255,255,255,.030) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.030) 1px, transparent 1px);
  background-size: 56px 56px;
}

body::after {
  content: ''; position: fixed; inset: 0; z-index: 1; pointer-events: none;
  background: repeating-linear-gradient(
    0deg,
    rgba(0,0,0,.18) 0,
    rgba(0,0,0,.18) 1px,
    transparent 1px,
    transparent 3px
  );
  mix-blend-mode: multiply; opacity: .65;
}

.vignette {
  position: fixed; inset: 0; z-index: 1; pointer-events: none;
  background: radial-gradient(ellipse at center, transparent 55%, rgba(0,0,0,.55) 100%
...
```

### src/utils/siwe.js

```js
// src/utils/siwe.js — Sign-In with Ethereum (EIP-4361) — Pure JS implementation
// Compatible with Cloudflare Workers (no external deps)

const DOMAIN = 'supercompute.eth';
const URI = 'https://supercompute.eth';
const VERSION = '1';
const CHAIN_ID = 8453; // Base Mainnet

export function generateSiweMessage(address, nonce, statement = 'Sign in to SUPERCOMPUTE Web3 Platform') {
  const expirationTime = new Date(Date.now() + 24 * 60 * 60 * 1000).toISOString();

  return [
    `${DOMAIN} wants you to sign in with your Ethereum account.`,
    '',
    `URI: ${URI}`,
    `Version: ${VERSION}`,
    `Chain ID: ${CHAIN_ID}`,
    `Nonce: ${nonce}`,
    `Expiration Time: ${expirationTime}`,
    '',
    statement,
  ].join('\n');
}

export function generateNonce() {
  const array = new Uint8Array(32);
  crypto.getRandomValues(array);
  return Array.from(array, b => b.toString(16).padStart(2, '0')).join('');
}

// Simple keccak256 for addresses (simplified - uses Web Crypto API)
async function keccak256(message) {
  const msgBuffer = new TextEncoder().encode(message);
  const hashBuffer = await crypto.subtle.digest('SHA-256', msgBuffer);
  return Array.from(new Uint8Array(hashBuffer))
    .map(b => b.toString(16).padStart(2, '0'))
    .join('');
}

// Verify address matches (basic checksum validation)
export function isValidAddress(address) {
  if (!address || !address.startsWith('0x')) return false;
  if (address.length !== 42) return false;
  return /^0x[0-9a-fA-F]{40}$/.test(address);
}

// Parse SIWE message for display
export function parseSiweMessage(message) {
  const lines = message.split('\n');
  const result = {};
  
  for (const line of lines) {
    const idx = line.indexOf(': ');
    if (idx > -1) {
      result[line.slice(0, idx)] = line.slice(idx + 2);
    }
  }
  
  return result;
}

// Format wallet address for display
export function formatAddress(address, short = true) {
  if (!address) return '';
  if (short && address.length > 10) {
    return `${address.slice(0, 6)}...${address.slice(-4)}`;
  }
  return address;
}
```

### src/utils/wallet.js

```js
// src/utils/wallet.js — Wallet connection helpers for frontend
// Use window.ethereum (MetaMask, Rabby, Coinbase Wallet, etc.)

export async function connectWallet() {
  if (!window.ethereum) {
    throw new Error('No wallet detected. Install MetaMask or another wallet.');
  }

  const accounts = await window.ethereum.request({ 
    method: 'eth_requestAccounts' 
  });
  
  return accounts[0];
}

export async function getChainId() {
  if (!window.ethereum) return null;
  
  const chainId = await window.ethereum.request({ 
    method: 'eth_chainId' 
  });
  
  return parseInt(chainId, 16);
}

export async function switchChain(chainId) {
  if (!window.ethereum) return;
  
  const chains = {
    8453: 'base',      // Base Mainnet
    84532: 'base-sepolia', // Base Sepolia
    1: 'ethereum',
    11155111: 'sepolia',
  };
  
  const chainName = chains[chainId];
  if (!chainName) return;
  
  try {
    await window.ethereum.request({
      method: 'wallet_switchEthereumChain',
      params: [{ chainId: `0x${chainId.toString(16)}` }],
    });
  } catch (err) {
    // Chain not added, user rejected
    console.log('Switch chain error:', err);
  }
}

export function signMessage(message) {
  return window.ethereum.request({
    method: 'personal_sign',
    params: [message, window.ethereum.selectedAddress],
  });
}

export function onAccountsChanged(callback) {
  if (!window.ethereum) return;
  
  window.ethereum.on('accountsChanged', (accounts) => {
    callback(accounts[0] || null);
  });
}

export function onChainChanged(callback) {
  if (!window.ethereum) return;
  
  window.ethereum.on('chainChanged', (chainId) => {
    callback(parseInt(chainId, 16));
  });
}
```

### components/Layout.tsx

```tsx
import Head from "next/head"
import Sidebar from "./Sidebar"
import AgentChat from "./AgentChat"
import type { ReactNode } from "react"

export default function Layout({ children, title = "SUPERCOMPUTE · Web3 built for liberation" }: { children: ReactNode; title?: string }) {
  return (
    <>
      <Head>
        <title>{title}</title>
        <meta name="description" content="One operator, hands-on Web3 consulting on Base Chain since 2013." />
      </Head>
      <AgentChat />
      <div style={{ display: "flex", minHeight: "100vh" }}>
        <Sidebar />
        <main className="main">
          {/* HUD corners bracket the main content area (per Terminal Dossier spec) */}
          <div className="hud-corner embed tl" />
          <div className="hud-corner embed tr" />
          <div className="hud-corner embed bl" />
          <div className="hud-corner embed br" />
          {children}
        </main>
      </div>
      {/* Full-viewport vignette (z-index 1) — sits above CRT scanlines */}
      <div className="vignette" />
    </>
  )
}

```

### components/Sidebar.tsx

```tsx
import Link from "next/link"
import { useRouter } from "next/router"
import ConnectWallet from "./ConnectWallet"
import pkg from "../package.json"

interface NavItem {
  href: string
  label: string
  external?: boolean
}

interface NavGroup {
  label?: string
  items: NavItem[]
}

const groups: NavGroup[] = [
  {
    items: [
      { href: "/", label: "Home" },
      { href: "/about", label: "About" },
    ],
  },
  {
    label: "learn",
    items: [
      { href: "/school", label: "School" },
    ],
  },
  {
    label: "build",
    items: [
      { href: "/projects/browse", label: "Projects" },
      { href: "/projects/solar-punk", label: "Solar Punk" },
      { href: "/consulting", label: "Consulting" },
      { href: "/knowledge-graph", label: "Knowledge Graph" },
    ],
  },
  {
    label: "economy",
    items: [
      { href: "/token", label: "$SCOM Token" },
      { href: "/staking", label: "Staking" },
      { href: "/storefront", label: "Storefront" },
    ],
  },
  {
    label: "community",
    items: [
      { href: "/social", label: "Social" },
      { href: "https://supercompute.newsdesk.app", label: "NewsDesk ↗", external: true },
    ],
  },
]

function isActive(href: string, current: string): boolean {
  if (href === "/") return current === "/"
  return current === href || current.startsWith(href + "/")
}

export default function Sidebar() {
  const router = useRouter()
  const current = router.asPath.split("#")[0].split("?")[0]

  return (
    <aside className="sidebar">
      <div className="sidebar-top">
        <img src="/SupercomputeLogo.png" alt="SUPERCOMPUTE" className="sidebar-logo" />
        <div className="logo-text-group">
          <Link href="/" className="logo">SUPERCOMPUTE</Link>
          <span className="logo-sub">// v{pkg.version}</span>
        </div>
      </div>

      <nav className="sidebar-nav">
        {groups.map((group, gi) => (
          <div key={gi} className="nav-section" style={{ marginTop: gi === 0 ? 0 : 14 }}>
            {group.label && <div className="nav-section-label">{group.label}</div>}
            {group.items.map(item => {
              const active = !item.external && isActive(item.href, current)
              const linkProps = item.external
                ? { href: item.href, target: "_blank", rel: "noopener noreferrer" }
                : { href: item.href }
              const LinkComponent = it
...
```

### components/Web3Provider.tsx

```tsx
"use client"

import { WagmiProvider } from "wagmi"
import { QueryClient, QueryClientProvider } from "@tanstack/react-query"
import { wagmiConfig } from "../lib/web3"
import type { ReactNode } from "react"

const queryClient = new QueryClient()

export default function Web3Provider({ children }: { children: ReactNode }) {
  return (
    <WagmiProvider config={wagmiConfig}>
      <QueryClientProvider client={queryClient}>
        {children}
      </QueryClientProvider>
    </WagmiProvider>
  )
}

```

### functions/api/auth/message.js

```js
import { isValidAddress, json } from '../auth.js';
export async function onRequest({ request, env }) {
  const url = new URL(request.url);
  const nonce = url.searchParams.get('nonce');
  const address = url.searchParams.get('address');
  if (!nonce || !address) return json({ error: 'nonce and address required' }, 400);
  if (!isValidAddress(address)) return json({ error: 'Invalid address' }, 400);
  if (env?.CACHE) {
    const stored = await env.CACHE.get(`siwe:nonce:${nonce}`);
    if (!stored) return json({ error: 'Invalid or expired nonce' }, 400);
    // Verify nonce is bound to this address (if bound)
    if (stored !== 'pending') {
      try {
        const data = JSON.parse(stored);
        if (data.address && data.address !== address.toLowerCase()) {
          return json({ error: 'Nonce belongs to a different address' }, 400);
        }
      } catch {}
    }
  }
  const now = new Date(Date.now() + 10 * 60 * 1000).toISOString();
  const message = [
    'supercompute.io wants you to sign in with your Ethereum account.',
    '',
    'URI: https://supercompute.io',
    'Version: 1',
    'Chain ID: 8453',
    `Nonce: ${nonce}`,
    `Expiration Time: ${now}`,
    '',
    'Sign in to SUPERCOMPUTE Web3 Platform',
  ].join('\n');
  // Store the exact message for later verification
  if (env?.CACHE) {
    await env.CACHE.put(`siwe:msg:${nonce}`, message, { expirationTtl: 600 });
  }
  return json({ message });
}

```


## Package Files Materialized

- `source_examples/components/Layout.tsx`
- `source_examples/components/Sidebar.tsx`
- `source_examples/functions/api/auth/message.js`
- `source_examples/components/AgentChat.tsx`
- `source_examples/components/entity-map/EntityMapChat.tsx`
- `source_examples/components/KGChat.tsx`

## Next Design-System Work

- Use these source paths and snapshots as evidence before writing `DESIGN.md`.
- Convert the inventory above into a Claude Design-style package: `README.md`, `SKILL.md`, `colors_and_type.css`, `preview/colors-*`, `preview/typography-specimens.html`, `preview/spacing-*`, `preview/components-*`, `preview/brand-assets.html`, `ui_kits/app/`, and preserved `assets/`, `build/`, or `fonts/` when evidence exists.
- `ui_kits/app/index.html` must be a browser-reviewable component entry: load `../../colors_and_type.css`, load or import at least three files from `ui_kits/app/components/`, and mount the composed UI through ReactDOM/Babel or compiled browser-ready JavaScript. Do not duplicate a static HTML mock when modular component files exist.
- `ui_kits/app/components/App.jsx` (or equivalent app shell) must compose source-backed role components such as Sidebar, AssistantsList, ChatArea, InputBar, and MessageBubble, not merely list their filenames.
- Claude-style UI-kit entry skeleton for direct JSX kits:
  - `<script src="https://unpkg.com/react@18.3.1/umd/react.development.js"></script>`
  - `<script src="https://unpkg.com/react-dom@18.3.1/umd/react-dom.development.js"></script>`
  - `<script src="https://unpkg.com/@babel/standalone@7.29.0/babel.min.js"></script>`
  - `<link rel="stylesheet" href="../../colors_and_type.css">`
  - `<div id="root"></div>`
  - Load role components from `components/*.jsx` with `<script type="text/babel" src="components/ComponentName.jsx"></script>`.
  - Mount with `const { App } = window; const root = ReactDOM.createRoot(document.getElementById("root")); root.render(<App />);`.
- Preserve at least three high-signal source examples outside `context/` under `source_examples/` when reusable component snapshots exist, so future agents can compare generated components against original source structure.
- When a captured asset path begins with `build/`, copy the snapshot back into a root `build/` path with its original filename, such as `context/.../files/build/icon.png` -> `build/icon.png`. Do not satisfy build/runtime icon evidence by only renaming those files into `assets/`.
- Make `preview/brand-assets.html` visibly load preserved asset files from `assets/` or `build/`; do not redraw captured logos/icons as inline placeholders.
- Extract concrete colors, typography, spacing, radius, component behavior, assets, and product tone only when supported by inspected files.
- If evidence is missing or ambiguous, mark that uncertainty instead of inventing tokens.
