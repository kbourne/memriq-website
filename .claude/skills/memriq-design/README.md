# Memriq Design System

**An AI‑native holding company. A design system built for operators.**

Memriq is a holding company that spawns and operates portfolio businesses composed of AI agents. The current surface is a **CAO (Chief AI Officer) dashboard** used to oversee agents, decisions, and escalations across the portfolio. Later surfaces will include customer apps and marketing sites for the portfolio companies — ~14 of them, including:

- **Labs** — software development
- **Studios** — marketing
- **Growth** — sales
- **Vault** — finance
- **Counsel** — legal
- plus vertical‑specific companies

This system is the **parent chassis**. It is deliberately generic so each portfolio company can inherit the bones and apply its own accent palette, voice, and product‑specific component extensions later. Today, only the Memriq parent brand is defined here.

---

## Design targets & neighbors

- **Linear** — density, keyboard‑first, tight tracking, restraint
- **Vercel** — hard edges, monospaced numerals, engineered feel
- **Anthropic Console** — calm, premium, generous spacing
- **Stripe Dashboard** — data legibility, sober chrome

Dark‑mode is the native experience. Light‑mode reaches parity but is secondary.

## Sources provided

- `assets/logos/memriq-mark.svg` is the **active production logo** — a 5‑node Constellation M (nodes = agents, edges = MessageBus, emergent M = the whole system). It is the settled mark.
- `uploads/memriq_logo2.png` was a glossy 3D placeholder included with the brief. Color reference only — not the production logo.
- Earlier mark explorations (Peaks + swoosh, Diamond M, Orbit‑first) are preserved under `assets/logos/_archived/` for reference; sub‑brands may inherit from one of those later but no shipping surface uses them.
- No codebase, Figma, or slide decks were attached. The brief itself is the source of truth.

---

## Index of this system

Root files:

| File | Purpose |
|---|---|
| `README.md` | This document. Start here. |
| `SKILL.md` | Agent Skill manifest — makes this system invocable from Claude Code. |
| `colors_and_type.css` | Core tokens: palette ramps, semantic vars, type scale, radii, shadow, motion. Import this once at the root of any artifact. |

Folders:

| Folder | Contents |
|---|---|
| `assets/logos/` | Memriq Constellation mark, wordmark, white, black variants, and favicon / app‑icon set. Archived alternates live in `_archived/`. |
| `assets/motifs/` | Constellation set: `node.svg` / `node-violet.svg` / `node-magenta.svg`, `edge.svg`, `m-path-hero.svg`. |
| `fonts/` | Documentation on fonts (we load from Google Fonts — see caveats). |
| `preview/` | Cards that power the Design System tab. Not production components. |
| `ui_kits/cao_dashboard/` | The CAO Dashboard UI kit (components, screens, interactive prototype). |

---

## Content fundamentals

Memriq speaks like a seasoned operator talking to another operator. The CAO user is **not** a consumer — they are a decision‑maker reviewing a fleet of autonomous agents. Copy is calm, specific, and assumes competence.

**Voice**

- **Operator‑to‑operator.** Never cute. Never marketing‑coded inside the product. Marketing surfaces can be slightly more expressive but never whimsical.
- **Second person, sparingly.** Prefer labels and nouns over sentences. "Escalations" not "Your escalations." "Needs review" not "These need your review."
- **System‑as‑narrator for agents.** Agent output speaks in third person about itself when logging: `Drafted 3 replies. 1 flagged for review.` — not "I drafted…". In agent message bubbles (conversational mode) first person is fine.
- **No emoji** in product UI. Status is communicated via shape, color, and typography. Marketing may use a single Constellation **node** as an emphasis glyph; that is the only exception.
- **No exclamation marks.** Ever. Even for success states.

**Casing**

- **Sentence case** for buttons, labels, page titles, nav items. `Open portfolio`, not `Open Portfolio`.
- **UPPER CASE** reserved for eyebrows, tag labels, and 2–4‑char status pills: `LIVE`, `IDLE`, `ESC`, `BLOCKED`. Always tracked at `0.08em`.
- **Proper case** for product/company names: `Memriq`, `Labs`, `Vault`.
- **Code/IDs/agent names** in mono: `agent_vault_reconcile_v3`.

**Number & time conventions**

- Numbers are **tabular** (mono or `font-variant-numeric: tabular-nums`) whenever they appear in tables, metrics, or logs. They must not shift width as they tick.
- Money: `$12,480.00` with trailing zeros unless rounded context is clear.
- Time: `14:32` 24‑hr inside logs; `2h ago` relative elsewhere; absolute timestamps on hover.
- Ranges use en‑dash: `9:00–17:00`.

**Tone examples**

| Don't | Do |
|---|---|
| `Oops! Something went wrong 😬` | `Request failed. 502 from upstream.` |
| `Great job! Your agent finished!` | `Run complete — 12 items processed.` |
| `Click here to review your pending items` | `3 pending review` |
| `We couldn't connect to the server` | `No connection. Retrying in 5s.` |
| `Welcome back! What would you like to do today?` | `Good afternoon, Sarah.` |
| `Your AI assistant is thinking...` | `Reasoning…` |

**Microcopy patterns**

- Empty states: one short sentence + one action. `No escalations. You're clear.`
- Destructive confirms: name the object and the consequence. `Archive agent "vault‑reconcile"? Its open runs will be cancelled.`
- Inline loading: `Loading…` (ellipsis char, not three periods). Never spinner‑only without a label in dense UI.
- Log lines start with a verb in past tense: `Authorized`, `Dispatched`, `Queued`, `Failed`.

---

## Visual foundations

**Overall feel.** Dark, spacious, engineered. The UI is almost entirely monochrome — it reads as *black with a precise cyan accent.* Color is information, not decoration. The magenta→cyan gradient exists but is rationed: it earns its place in the logo, the top of the hero, and on exactly one CTA per view at most.

### Color

- **Backgrounds stack in three layers.** `#0A0A12` (app bg) → `#13131C` (surface/card) → `#181824`+ (menus, popovers). The jumps are small on purpose; elevation comes from a hairline border and a subtle inset highlight, not a big shadow.
- **Borders do the heavy lifting.** `#1F1F2E` at rest, `#2A2A3D` for strong separation, a `rgba(255,255,255,0.03)` inset on elevated surfaces to suggest a lit top edge.
- **Cyan `#22D3EE` is THE interactive color.** Primary buttons, focus rings, links, live indicators, the "I am happening right now" heartbeat. Use it and only it for primary actions.
- **Violet `#7C3AED`** is the agent/AI chrome color — agent bubbles, agent labels, the "something learned" tint. Never for user actions.
- **Magenta `#B14BFF`** only appears inside the brand gradient, never as a flat fill.
- **Semantic status** (success green, warn amber, error rose, info cyan) are tuned for dark: mid‑brightness solids for fills, 10–15% alpha of the same for backgrounds, lighter tint for foreground on those backgrounds.

### Type

- **Geist** everywhere for prose and UI. Weights 400 / 500 / 600 are the workhorses; 300 for display, 700 sparingly. Tracking is slightly tight (`-0.01em` body, `-0.02em` display) — this is the signature.
- **JetBrains Mono** for anything that is data, code, logs, agent output, IDs, timestamps in dense tables. Tabular figures are non‑negotiable for numbers in tables.
- **Base size is 14px** for UI density (matches Linear/Stripe). Prose surfaces step up to 15–17px. Display starts at 40px and only goes larger in marketing.
- **No other fonts.** Not "here's Inter as a fallback for flair." The fallback stack is system sans for resilience, not taste.

### Spacing

- 4px base unit. Dense UI lives on the 4/8/12 triplet. Generous layouts use 24/32/48. Marketing breathes at 64/96.
- Forms use **12px vertical gap, 8px inside inputs** — the Linear rhythm. Tables use **8px row padding**, never more than 12.

### Radius

- **3px** for chips/pills inside dense UI. **5px** for inputs and buttons. **8px** for cards and panels. **12px** for modals. **999px** for status dots, avatars, capsule badges only. Nothing else should be a full pill.
- Radii are intentionally modest. "Squared but not sharp" — the opposite of the friendly‑rounded consumer look.

### Elevation & shadows

- **Dark mode uses borders + inset highlights** more than drop shadows. When shadow is used, it's `0 4px 12px rgba(0,0,0,0.5)` with a `1px inset rgba(255,255,255,0.03)` to define the top edge.
- **Glow is a special‑purpose tool.** Primary CTA hover, focus rings, and live‑state indicators get a cyan glow (`0 0 24px #22D3EE33`). Never on body content.

### Backgrounds

- **No background imagery** in product UI. The app is flat. The hero of the marketing surface uses a single `radial-gradient` of the brand colors at very low alpha, nothing more.
- **No grain, no noise, no textures.** If you find yourself reaching for SVG noise, stop. The precision IS the texture.
- **No hand‑drawn illustrations.** The approved decorative vocabulary is the **Constellation set** in `assets/motifs/`:
  - **Node** (`node.svg` / `-violet` / `-magenta`) — the atomic glyph. Cyan = endpoint / live state, violet = secondary / agent, magenta = primary / active. Use as bullet accents, status dots, count chips, map pins.
  - **Edge** (`edge.svg`) — a node‑to‑node connector in the brand gradient. Use as section dividers, progress tracks, step‑flow indicators, or animated as a loading state. Never as decorative card borders.
  - **M‑path** (`m-path-hero.svg`) — the whole constellation enlarged, with scattered distant nodes. Secondary graphic element only: marketing heroes, splash and empty states, signup / onboarding / spawn flows. Never under product UI (tables, forms, code). Keep its alpha contribution ≤ 12% — the content must lead.

### Hover & press

- **Hover:** a 4–5% lightening of the surface (`#13131C` → `#181824`), never an opacity change on the element itself (opacity shifts feel sloppy at this polish level).
- **Press:** a 100ms scale to `0.98` on primary buttons only; everything else just darkens one step.
- **Focus:** double ring — 2px of `--bg` then 2px of `--cyan-400`. This gives the ring a gap from the element and keeps it crisp on any surface.
- **Disabled:** 40% opacity AND `pointer-events: none` AND muted text. All three.

### Borders

- Always 1px. Never 2px except on focus rings.
- Default border is `--border` (`#1F1F2E`). Hover states step to `--border-strong`. Error state is `--error` at full opacity.
- **Gradient borders are allowed** on exactly one element per view — usually a hero card or a signature CTA. Implemented via `padding: 1px; background: var(--gradient-brand); > inner surface`.

### Transparency & blur

- **Used rarely.** The top navbar gets a `backdrop-filter: blur(12px)` with `rgba(10,10,18,0.7)` for a subtle floating effect when the content scrolls underneath. Modal scrims are `rgba(0,0,0,0.6)` with no blur — we want modal focus, not a pretty frosted look.
- Tooltips and popovers are **solid** `--surface-2`, never translucent. Legibility > cuteness.

### Imagery (when used)

- **Cool, desaturated, premium.** If product screenshots or portfolio photography are needed, target a cyan‑leaning color cast, ~85% saturation max, subtle grain only if the source has it organically.
- **No stock photography.** Placeholder blocks are better than bad stock.

### Motion

- Default `180ms cubic-bezier(0.16, 1, 0.3, 1)` — a subtle ease‑out. This is on every interactive hover, modal enter, toast slide.
- **No bounces, no springs** in product UI (except spring on the hero gradient orb in marketing, if used). This is a serious product; bouncy animation undercuts the positioning.
- **Fades are short** (120ms) so keyboard power‑users don't feel dragged behind.
- **Live indicators pulse** — 2s breathing animation on the cyan dot, 30–60% opacity range. This is the ONLY looping animation in the product UI.

### Layout rules

- **Sidebar: 240px fixed.** Collapsible to 56px (icon‑only).
- **Navbar: 52px fixed**, sticky top, backdrop‑blurred.
- **Content has no max‑width in tables** — they use all available space. Reading surfaces cap at 720–800px. Marketing hero caps at 1120px inner, 1400px outer.
- **12‑column grid** for marketing, no grid for product (explicit flex/grid per section).

### Cards

- Border: `1px solid var(--border)`. Radius: `8px`. Background: `var(--surface)`. Inset highlight: `0 0 0 1px rgba(255,255,255,0.03) inset`. Shadow: none by default; `--shadow-md` only on floating elements (menus, popovers, modals).
- Interactive cards get a `border-color` hover to `--border-strong` and a 100ms transition. Nothing else.

### Protection gradients & capsules

- **Capsule badges** are used for tags, agent status, counts. Always with tabular digits when numeric. Background tint = semantic color at 12–18% alpha; foreground = the lighter "fg" variant of that color.
- No protection gradients needed — we're dark‑mode native; imagery is rare.

### Accessibility notes

- Minimum contrast target is **WCAG AA** on `--fg-2` against `--surface`. `--fg-muted` is reserved for secondary text ≥13px.
- Focus rings always visible on keyboard nav; never removed, only styled.
- Live/pulsing animations respect `prefers-reduced-motion`.

---

## Iconography

Memriq uses **[Lucide](https://lucide.dev)** as the system icon library. Rationale:

- Stroke‑based, `1.5px` weight — matches the engineered feel.
- Huge coverage, permissive MIT license, drop‑in CDN available.
- The de‑facto choice at Linear, Vercel, and similar products — so the visual vocabulary is already familiar to our audience.

**Delivery.** Link from CDN in prototypes and product:

```html
<script src="https://unpkg.com/lucide@latest/dist/umd/lucide.min.js"></script>
<i data-lucide="activity" class="icon"></i>
<script>lucide.createIcons();</script>
```

Or use `lucide-react` in production. This is a **substitution**: no custom icon font was provided. Flagged in Caveats.

**Rules**

- **16px** default in dense UI, **20px** in buttons/nav, **24px** in section headers, **32–40px** in empty states. Stroke stays 1.5px at every size — we do not thicken strokes when scaling up.
- Icons inherit `currentColor`. Never hard‑code icon color unless it is semantic (an error icon tinted with `--error`).
- **Pair icon with label** whenever possible. Icon‑only buttons must have a tooltip.
- **No emoji** in product chrome. Zero. The only allowed glyphs outside Lucide are the **Constellation motifs** (`assets/motifs/node*.svg`, `edge.svg`, `m-path-hero.svg`) and the typographic **en‑dash / em‑dash / ellipsis**.

**Agent status glyphs** — use shape, not color alone:

- `● LIVE` (filled dot, cyan, pulsing)
- `◐ RUNNING` (half circle, cyan)
- `○ IDLE` (stroked dot, muted)
- `▲ ESCALATED` (triangle, warning)
- `■ BLOCKED` (square, error)

These are literal Unicode glyphs set in Geist — they render consistently and read at small sizes.

---

## Fonts

- **Geist** and **JetBrains Mono** are both **self‑hosted** as variable fonts from `fonts/` via `@font-face` in `colors_and_type.css`.
  - `Geist-VariableFont_wght.ttf` — weights 100–900
  - `JetBrainsMono-VariableFont_wght.ttf` — weights 100–800 (roman)
  - `JetBrainsMono-Italic-VariableFont_wght.ttf` — weights 100–800 (italic)
- The CSS fallback stack (system sans + system mono) is engineered so a font failure never produces a visible layout shift.

---

## Caveats & what to iterate on

1. **Logo is settled.** The Constellation mark (5 nodes, M‑path edges, faint orbital arc) is the production logo — it maps directly to the product architecture: nodes = agents, edges = MessageBus, emergent M = the whole system. Earlier explorations (Peaks + swoosh, Diamond M, Orbit‑first) are archived under `assets/logos/_archived/` and are no longer in active use; one of them may later anchor a sub‑brand. The glossy 3D PNG in `uploads/` was reference only.
2. **Fonts are fully self‑hosted** as variable fonts in `fonts/`. No CDN font requests.
3. **Icons are Lucide (CDN), not a custom set.** Flagged.
4. **Only the CAO Dashboard UI kit is built** per scope (Memriq parent only). Portfolio‑company kits (Labs, Studios, Vault, etc.) will inherit this chassis later.
5. **Light mode is specified but not exhaustively exercised.** The tokens are there (`.light` class on `<html>`), but every component was designed dark‑first. Please flag screens where you need light parity preview and I'll render them.
6. **No real data.** Agent names, escalations, and log lines in the UI kit are realistic fiction. Swap with real fixtures when you have them.

**Please help me iterate:**
- **Is the content voice** (operator‑to‑operator, no emoji, no exclamation marks) calibrated right for the CAO?
- **Which portfolio company do you want to brand next** — Labs, Vault, Studios?
- **Any specific CAO dashboard screens missing** from the kit that you need for internal demos?
