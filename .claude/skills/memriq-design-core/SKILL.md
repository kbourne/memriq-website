---
name: memriq-design-core
description: Memriq monorepo design-system structural rules. MUST be loaded for ANY UI work — writing, editing, or reviewing components, styles, Tailwind classes, CSS, JSX/TSX, color values, typography, spacing, motion, or visual assets in apps/* or packages/*. Always pair with the brand-specific skill matching the current app's path (memriq-design for command-web; topsway-design for topsway-web; etc.). Defines tokens-as-source-of-truth, spacing/radius/motion rules, voice baseline, accessibility, and the conformance checklist that must pass before any UI change is declared complete.
user-invocable: true
---

# Memriq Design Core — Structural Rules

Structural rules that apply to every Memriq surface. Brand-specific overrides (palette, voice tweaks, logos) live in the matching brand skill.

## Always-on workflow

When working on UI in this monorepo:

1. **Detect the app from the file path** and load the matching brand skill:
   - `apps/command-web/`  → load `memriq-design` (Memriq holdco / CAO console)
   - `apps/topsway-web/`  → load `topsway-design` (currently a stub — see notes there)
   - `apps/braid-site/`   → load `braid-design` (not yet created)
   - `apps/labs-portal/`  → load `labs-design` (not yet created)
   - `apps/mobile/`       → load `labs-design` (shares Labs theme)
   - `apps/command/`      → SKIP, legacy Flutter, do not modify UI
2. Read the brand skill's README for voice and any brand overrides.
3. Apply this skill's structural rules (below).
4. Run `checklist.md` before declaring the task complete.

If a brand skill is empty/stub, ASK THE USER which brand direction to take. Do not fall back to Memriq holdco tokens for portfolio apps.

## Tokens — single source of truth

Tokens live in `packages/design-tokens/<brand>/`. NEVER duplicate hex, font names, or spacing values inside component files. Always import:

```ts
import { colors, spacing, typography } from "@memriq/design-tokens-<brand>";
```

For CSS, import once at root: `@import "@memriq/design-tokens-<brand>/css-vars.css"`.

For Tailwind: extend the brand's `tailwind.preset` in the app's `tailwind.config`.

## Hard structural rules (apply to all brands)

**Spacing.** 4px base unit. Never invent values. Dense UI uses 4/8/12; generous layouts 24/32/48; marketing 64/96. Forms: 12px vertical gap between fields, 8px inside inputs. Tables: 8px row padding (12 max).

**Type.** UI base is 14px. Use semantic type roles (`.t-display`, `.t-h1`–`.t-h4`, `.t-body`, `.t-body-sm`, `.t-eyebrow`, `.t-code`, `.t-log`, `.t-num`) — never raw `font-size`. Numbers in tables/metrics/logs MUST be tabular.

**Radii.** 3 chips · 5 inputs+buttons · 8 cards/panels · 12 modals · 999 ONLY for status dots, avatars, capsule badges. No other element is fully rounded.

**Borders.** Always 1px. Default `var(--border)`. Hover steps to `var(--border-strong)`. Never 2px except on focus rings. Gradient borders allowed on at most one element per view.

**Motion.** Default `180ms cubic-bezier(0.16, 1, 0.3, 1)` (`--dur-base` + `--ease-out`). Fades 120ms. No bounces or springs in product UI. Live indicators may pulse 2s — only looping animation. Respect `prefers-reduced-motion`.

**Focus.** Keyboard focus rings ALWAYS visible. Use `--ring`. Never `outline: none`.

**Hover & press.** Hover lightens the surface one step (never opacity). Press is `scale(0.98)` on primary buttons only. Disabled = 40% opacity AND `pointer-events: none` AND muted text.

**Color usage.** Color = meaning, not decoration. Status uses shape AND color. Agent status glyphs: `● LIVE`, `◐ RUNNING`, `○ IDLE`, `▲ ESCALATED`, `■ BLOCKED`.

## Voice baseline (every brand inherits; brand may add tone)

Sentence case for buttons, labels, page titles, nav. **No emoji** in product UI. **No exclamation marks**, ever. Empty states = one short sentence + one action. Destructive confirms name the object and consequence. Inline loading uses real `…` ellipsis. Log lines start with past-tense verb (`Authorized`, `Dispatched`, `Failed`). Numbers: `$12,480.00`; 24-hr `14:32` in logs; relative `2h ago` elsewhere. See `patterns/voice.md` for examples.

## Iconography

[Lucide](https://lucide.dev) only. `lucide-react` in production. Stroke 1.5px. Sizes: 16 dense / 20 buttons / 24 section headers / 32–40 empty states. Pair with label whenever possible; icon-only buttons require a tooltip.

## Patterns

See `patterns/` for canonical solutions: `buttons.md`, `badges.md`, `forms.md`, `feedback.md`, `data-display.md`, `layout.md`, `motion.md`, `a11y.md`, `voice.md`.

## Before finishing any UI change

Walk `checklist.md`. Every item must pass. Run `scripts/check-tokens.sh <changed-files>`. Fix any failures before declaring done.
