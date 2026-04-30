---
name: memriq-design
description: Memriq holdco brand — the parent chassis for the CAO console (apps/command-web) and any future Memriq-branded surface. MUST be loaded for UI work in apps/command-web/ or any code referencing the Memriq parent brand. Do NOT apply these tokens to portfolio-company apps (topsway-web, braid-site, labs-portal, mobile) — they have their own brand skills. Defines the dark-mode-native, monochrome-with-cyan-accent palette; Geist + JetBrains Mono type; agent/violet chrome; and operator-to-operator voice. Always pair with memriq-design-core.
user-invocable: true
---

# Memriq Brand — CAO Console

## Always pair with `memriq-design-core`

Structural rules (spacing, radii, motion, voice baseline, checklist) live in `memriq-design-core`. Load it first. This skill adds the Memriq-specific palette, typography, and voice.

## Tokens

- TS / Tailwind: `packages/design-tokens/memriq/`
- CSS variables: `packages/design-tokens/memriq/css-vars.css`
- Fonts (self-hosted): `packages/design-tokens/memriq/fonts/`
- Assets (logos, motifs): `packages/design-tokens/memriq/assets/`

## Brand identity

Memriq is the AI-native holding company that operates portfolio businesses composed of agents. The CAO surface is built for an operator overseeing those agents — calm, dense, engineered. Reads as **black with a precise cyan accent**. Color is information, not decoration. Cyan #22D3EE = primary action. Violet #7C3AED = agent/AI chrome. The magenta→cyan gradient is rationed: logo, hero, at most one CTA per view.

Design neighbors: Linear (density, restraint), Vercel (engineered feel), Anthropic Console (calm, premium), Stripe Dashboard (data legibility).

## Brand-only rules (deltas from core)

- **Dark-mode native.** Light mode is opt-in (`<html class="light">`) and reaches parity but is secondary.
- **Voice is operator-to-operator.** See `README.md` for the full tone guide and do/don't table.
- **Agent labels in violet.** Anything that represents an agent (bubble, label, "something learned" tint) uses violet. Never violet for user actions.
- **Magenta is gradient-only.** Never a flat magenta fill.
- **Typography signature.** Geist with `-0.01em` body tracking, `-0.02em` display tracking. JetBrains Mono for data, code, logs, agent IDs, dense-table timestamps.
- **Agent status glyphs**: `● LIVE`, `◐ RUNNING`, `○ IDLE`, `▲ ESCALATED`, `■ BLOCKED`.

## Reference UI

The CAO Dashboard reference UI kit lives at `/Users/keithbourne/development/agentic/Cowork/PROJECTS/MEMRIQ/12_DESIGN/memriq/ui_kits/cao_dashboard/` — use it as a source for component shapes (Button, Badge, Card, StatusDot, Avatar, Kbd, agent bubbles, escalation rows). The Primitives.jsx file is the canonical implementation reference.

## Deep reference

`README.md` in this skill is the full brand bible from Claude Design: design targets and neighbors, full voice rules with examples, content fundamentals, microcopy patterns, layout specifics, and caveats.
