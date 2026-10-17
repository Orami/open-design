---
name: "Supercompute — Immersion Skins"
category: DesignSystems
surface: web
version: 1.0.0
colors:
  background: "#0a1330"
  foreground: "#f4ecd8"
  accent: "#c9a33a"
  surface: "#0d1f3d"
  muted: "#9fb2d0"
  border: "#1e3a5f"
  success: "#4ade80"
  warning: "#e0be3f"
  error: "#dc2626"
---

# Supercompute — Immersion Skins

The design system behind the Supercompute OS: one master skin, and forks of it
that we sell as Immersion NFTs. This document is the system of record for the
**skin layer** — how a skin is built, what it may change, and how one is branded.

Two sibling sources, and which wins:

| Source | What it is | Authority |
| --- | --- | --- |
| `SupercomputeA/supercompute-immersion` | the static-HTML desk design — `supercompute-skin.css`, 13 screens, the dock tiles and typefaces | **visual source of truth** |
| `SupercomputeA/immersion` | the React implementation this describes | the running app |

When this document and `supercompute-skin.css` disagree, **the CSS wins**. This
document describes the *skin system* built around it, which that repo does not
cover.

---

## 1. What a skin is

A skin is a **design language**, applied as `data-skin` on `<html>`. Nothing in
the component stylesheet knows which skin is active: every colour, radius, bevel,
border width, font and metric is read from a semantic `--ui-*` layer that each
skin populates.

> **A skin is not an Immersion.** An Immersion is the DAO starter kit NFT that
> initialises an instance of the chassis (ERC-6551 token-bound account). A skin
> *fork* is what a starter kit ships with: the School starter kit ships the
> School skin. The two words are not interchangeable.

### Lineage

| Skin | Role | State |
| --- | --- | --- |
| `supercompute` | **master** | ours. The default, and what every fork derives from |
| `poolsuite` | origin | where the desk language came from. Kept as-is |
| `school` | fork | green ground, white ink, gold accent |
| `club-manager` | fork | deep burnt-orange ground, white ink, gold accent |
| `dossier` | legacy | an earlier DesignDesk derivation. Superseded; kept for comparison |

Only the master sits on `:root`, so a surface with no `data-skin` renders the
master. Every fork declares `forksFrom`, so lineage is data rather than prose.

---

## 2. The fork contract — one file

A fork overrides the **raw palette only**. That is load-bearing, not a style
preference.

`supercompute.css` defines the semantic layer as aliases:

```css
--ui-canvas: var(--navy);
--ui-text:   var(--cream);
--ui-accent: var(--gold);
--ui-border: var(--border);
```

Custom properties substitute **lazily** — at the point of use, not the point of
definition — so redefining `--navy`, `--cream`, `--gold` and `--border` on
`<html>` changes every `--ui-*` value that aliases them. A fork therefore
inherits the entire structure for free:

- 1px hairlines · 2px radii · 32px menu bar · 68px dock
- the two-tone bevel · the CRT field and scanlines
- the type stack (JetBrains Mono everywhere, Phosphate on wordmark surfaces)

**Adding a fork means adding one token block and nothing else.** If a fork ever
needs a structural change, that is a design decision to raise — not a quiet
addition to a skin file.

---

## 3. The palette a skin may override

Nineteen raw tokens, grouped the way they are reasoned about.

### Ground
| Token | Master | Role |
| --- | --- | --- |
| `--navy` | `#0a1330` | canvas |
| `--surface` | `#0d1f3d` | cards and panels |
| `--elevated` | `#0a1e3d` | modals, dropdowns, popovers |
| `--well` | `#0c1730` | deepest surface |
| `--nested` | `#0f1c33` | nested surfaces |

### Ink
| Token | Master | Role |
| --- | --- | --- |
| `--cream` | `#f4ecd8` | display and body text |
| `--muted` | `#9fb2d0` | secondary text and metadata |
| `--info` | `#6fa3e5` | tertiary — **a role, not a second accent** |
| `--dim` | `#47597a` | disabled, placeholders |

### Accent
| Token | Master | Role |
| --- | --- | --- |
| `--gold` | `#c9a33a` | the primary affordance |
| `--gold-hover` | `#d8b658` | hover |
| `--gold-active` | `#a8862c` | pressed |
| `--gold-bg` | `#1c2340` | ghost background |
| `--gold-line` | `rgba(201,163,58,.45)` | the brass rule |

### Rules
| Token | Master | Role |
| --- | --- | --- |
| `--border` | `#1e3a5f` | structural hairline |
| `--hair` | `#16233d` | secondary hairline |

### Signals
| Token | Master | Role |
| --- | --- | --- |
| `--hud` | `#e0be3f` | HUD brackets, alerts |
| `--live` | `#4ade80` | live / published / ok |
| `--fault` | `#dc2626` | errors, destructive |

### Structural switches — the only three a fork may move

| Switch | Options | Effect |
| --- | --- | --- |
| `density` | canon · comfortable · compact | padding, rhythm, base type size |
| `borders` | canon · hairline · none | border width |
| `radius` | canon · 0 · 2 · 4 | corner radius. **Capped at 4px. No pills** |

Everything else — bar heights, dock size, the bevel, the CRT field, the type
stack — belongs to the master. A fork that could reshape the shell would stop
being a fork of one system.

---

## 4. Layers, in order

```
master structure   →   skin palette   →   forged skin   →   personal knobs
```

1. **Master structure** — hairlines, radii, bars, bevel, field, type. Inherited.
2. **Skin palette** — one of the lineage above, or a fork's token block.
3. **Forged skin** — a runtime skin. See §5.
4. **Personal knobs** — accent, ground, density, type, borders, radius, HUD,
   atmosphere, bevel. Held per browser, **never published**. These stack on top
   of whatever skin is active.

### Verified values

| | master | school | club-manager | poolsuite |
| --- | --- | --- | --- | --- |
| canvas | `#0a1330` | `#0b2a1e` | `#2a1408` | `#f6d5d5` |
| text | `#f4ecd8` | `#ffffff` | `#ffffff` | `#000000` |
| accent | `#c9a33a` | `#c9a33a` | `#c9a33a` | `#fb278d` (live only) |
| border | 1px `#1e3a5f` | 1px `#1f5540` | 1px `#5c3418` | 1px `#000000` |
| radius | 2px | 2px | 2px | 2px (0 default) |
| menubar / dock | 32 / 68px | 32 / 68px | 32 / 68px | 32 / 40px |

---

## 5. Forged skins — runtime data

A skin can be created without touching a repository. That matters because a
Virtuals agent manages Immersion NFTs alongside the operator, so a skin must be
**data, not a file a developer commits**.

A forged skin applies by writing CSS custom properties **inline on `<html>`** and
setting `data-skin` to the master, so structure resolves and the palette
overrides. Inline declarations outrank the stylesheet, so no CSS file is touched.

- **It may change:** the palette, and the three structural switches.
- **It may not change:** free-form geometry.
- **Precedence:** choosing a built-in skin clears a forged overlay, otherwise the
  inline properties would keep winning.
- **Storage:** `localStorage`, per browser. Export as a portable JSON payload.

A forged skin carries `version`, `forgedAt` and the skin itself, so a payload can
travel between operators, or be emitted by an agent.

---

## 6. Branding — the Franchisee's charter

The **Franchisee** role holds an Immersion charter: it owns the community's
culture, and therefore its branding. Three fields on every skin are theirs:

| Field | Where it appears |
| --- | --- |
| `mark` | boot plate, dock |
| `wordmark` | boot plate, desk wallpaper |
| `handle` | boot plate, desk wallpaper |

The boot plate and the wallpaper read all three from the active skin, so an
Immersion boots wearing **its own** identity. This was a real defect once: the
boot plate hardcoded the Supercompute mark and `SUPERCOMPUTE.ETH`, so a School or
Club Immersion booted as somebody else.

**We offer all of this through the Supercompute skin**, so the umbrella name
stays present on every fork: the `handle` renders on both the boot plate and the
wallpaper. A school Immersion reads `SCHOOL DAO` over `SUPERCOMPUTE.ETH` — their
identity, our provenance.

Every skin currently points at the Supercompute mark, because no community has
supplied its own. That is deliberate: the field exists and is the Franchisee's to
set, and nothing is invented in its place.

---

## 7. Names

We sell the NFT. The name is either bought through us or the operator already
holds it with ENS. Encoded as `nameProvenance`:

| Value | Meaning |
| --- | --- |
| `issued` | bought through us |
| `brought` | the operator's own ENS |

Set per buyer by the Immersion builder. It is data, not a token.

---

## 8. Posture rules

- **1px hairlines.** Structure is drawn with rules, never with fills or tints
  alone.
- **2px radii, capped at 4px.** No pills except status dots and avatar circles.
- **Elevation by colour contrast**, not shadow. No `box-shadow` except the live
  status-dot glow.
- **Two-tone bevel, never a blur.** `inset 1px 1px 0 cream-10`,
  `inset -1px -1px 0 rgba(0,0,0,.45)`.
- **Gold is scarce** — at most two accents per screen.
- **CRT field is global.** The dot grid and scanlines are background layers;
  never apply them to individual cards.
- **Monospace numerics** in every data display.
- **`//` is the only sanctioned section label.**

### Type

| Role | Face | Notes |
| --- | --- | --- |
| Display | `Phosphate` (`fonts/PhosphateSolid.ttf`) | **wordmark surfaces only.** Uppercase |
| Body / UI | `JetBrains Mono` 400/500/700 | everything else |
| Code | `SFMono-Regular` stack | code blocks, terminal output |

Self-hosted. No font CDN.

---

## 9. Surfaces

The desk is an operating system, not a page. A menu bar is pinned top, a dock
bottom; windows float between them.

| Region | Height | Notes |
| --- | --- | --- |
| Menu bar | 32px | ruled with the brass line, carries the brand mark |
| Window title bar | 32px | the desk's own dock tile as a crest |
| Controls | 26px | |
| Dock | 68px | one centred beveled strip of 66px icon+label tiles |

---

## 10. Honesty rules

These are part of the system, not incidental manners.

- **Zero and unknown are different answers.** A count reads `0` only when the
  source answered zero; otherwise the surface says the read failed and names the
  source.
- **No feed beats a plausible number.** Empty states say so. Where a capability
  needs infrastructure that does not exist, it renders `not wired`.
- **No invented addresses or metrics.** A placeholder address is never
  substituted; an unverified resolver renders as its literal placeholder.
- **A signature is not zero-knowledge.** Do not let a label claim more than the
  mechanism does.

---

## 11. Changing the system

```
DesignDesk / this document  →  wiki  →  OpenDesign copy  →  consumer apps
```

Never the reverse. A consumer app does not become a second source of truth, and
no app forks the tokens.

**Adding a fork:** one token block in `src/styles/skins/`, one entry in
`SKIN_DEFS` with `role: 'fork'` and `forksFrom: 'supercompute'`, one `@import`.
Nothing else.

**Audit:** grep consumer repos for raw hexes that should be tokens; confirm body
is JetBrains Mono and Phosphate is wordmark-only; confirm no app declares its own
colours.
