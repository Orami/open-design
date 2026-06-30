# SUPERCOMPUTE UI Kit — Applied Interface

This is a composed UI kit demonstrating the Terminal Dossier design system as a product-like surface. It renders a SUPERCOMPUTE operator dashboard with sidebar navigation, agent fleet status, and a Condor trade agent chat interface.

## Structure

```
ui_kits/app/
├── index.html           # Browser entry — loads React, Babel, CSS, composes App
├── README.md            # This file
└── components/
    ├── App.jsx          # Root shell — tab switching, wallet state, HUD corners
    ├── Sidebar.jsx      # Collapsible nav with all 20 pages, wallet connect trigger
    ├── AssistantsList.jsx  # Agent fleet grid with status badges
    ├── ChatArea.jsx     # Message thread display (auto-scroll, user + agent)
    ├── MessageBubble.jsx # Individual message component
    ├── InputBar.jsx     # Chat input with Enter-to-send
    └── WalletModal.jsx  # Multi-wallet connect overlay (simulated connection)
```

## Usage

Open `index.html` in a browser. The page is self-contained — React, ReactDOM, and Babel are loaded from unpkg, and design tokens come from `../../colors_and_type.css`.

For development with hot reload, serve the directory with any static server:

```bash
cd ui_kits/app
python3 -m http.server 8080
```

## Component Roles

| Component | Role | Source basis | Interactive |
|---|---|---|---|
| `Sidebar` | Collapsible nav — all 20 pages across 3 tiers, wallet trigger | `components/Sidebar.tsx` | Collapse/expand, hover states |
| `AssistantsList` | Agent fleet grid — name, role, description, status | `components/AgentFleet.tsx` | Status toggle (click online/observer) |
| `ChatArea` | Message thread — renders user + agent messages, auto-scroll | `components/AgentChat.tsx` | Auto-scroll on new message |
| `MessageBubble` | Single message — user or agent variant with timestamp | `components/AgentChat.tsx` | — |
| `InputBar` | Chat input — textarea + send button, Enter to send | `components/AgentChat.tsx` | Type, send, clear |
| `WalletModal` | Multi-wallet connect overlay with simulated connection | `components/ConnectWallet.tsx` | Open, select wallet, connect animation |
| `App` | Root shell — tab navigation (Terminal / Fleet / Chat), wallet state | `components/Layout.tsx` | Tab switch, wallet open/close |

## Interactions

- **Tab switching**: Terminal / Fleet / Chat tabs in the main area — click to switch
- **Wallet connect**: Click "// Connect" in sidebar or "Connect Wallet" in hero → modal opens → select a wallet → simulated 1.2s connection → shows address
- **Chat**: Type in the input bar, press Enter or click → message appears in thread → random agent response follows
- **Sidebar collapse**: Click →/← button to toggle between full (220px) and icon (60px) modes
- **Agent status**: Click status badge on any agent card to toggle online ↔ observer

## Design Notes

- All components use CSS custom properties from `colors_and_type.css`
- No component-specific CSS — all styling via design system tokens
- HUD corners bracket the main content area (signature Terminal Dossier element)
- CRT scanlines and vignette are applied globally
- Agent status uses semantic colors: online (green), observer (gold)
- Chat uses monospace for agent messages, inherit for user messages
- Sidebar lists all 20 prototype pages organized by tier (public/member/admin)

## Source Basis

These components are extracted from the live SUPERCOMPUTE codebase at `SupercomputeA/Master_Main`. See `source_examples/` for the original TypeScript implementations.
