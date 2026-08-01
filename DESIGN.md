---
name: The Right Edge — Second Edition
description: Mechanism-first M2K chart-pattern teaching app on a dark navy trading palette
colors:
  bg: "#080c10"
  panel: "#10171e"
  panel2: "#16202a"
  line: "#1e2c37"
  line2: "#2a3b48"
  amber: "#f0a83c"
  emerald: "#3fbf8f"
  coral: "#ef6b5e"
  blue: "#5fa8d3"
  text: "#dfe7ec"
  muted: "#78899a"
  brass: "#dfa849"
typography:
  display:
    fontFamily: "Oxanium, system-ui, sans-serif"
    fontSize: "clamp(32px, 6.6vw, 60px)"
    fontWeight: 800
    lineHeight: 1.02
    letterSpacing: "-0.025em"
  heading:
    fontFamily: "Oxanium, system-ui, sans-serif"
    fontSize: "clamp(22px, 4vw, 34px)"
    fontWeight: 800
    lineHeight: 1.14
    letterSpacing: "-0.02em"
  body:
    fontFamily: "Oxanium, system-ui, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.62
    letterSpacing: "normal"
  numeric:
    fontFamily: "Space Mono, ui-monospace, monospace"
    fontSize: "12px"
    fontWeight: 400
    lineHeight: 1.4
    letterSpacing: "0.1em"
  eyebrow:
    fontFamily: "Space Mono, ui-monospace, monospace"
    fontSize: "11.5px"
    fontWeight: 400
    lineHeight: 1.3
    letterSpacing: "0.2em"
rounded:
  sm: "6px"
  md: "8px"
  lg: "12px"
  xl: "16px"
  pill: "50%"
spacing:
  xs: "6px"
  sm: "8px"
  md: "14px"
  lg: "20px"
  xl: "30px"
  xxl: "56px"
components:
  button:
    backgroundColor: "transparent"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: "7px 14px"
    typography: "{typography.body}"
  button-hover:
    textColor: "{colors.amber}"
  button-primary:
    backgroundColor: "{colors.amber}"
    textColor: "#0b0f13"
    rounded: "{rounded.md}"
    padding: "7px 14px"
  panel:
    backgroundColor: "{colors.panel}"
    textColor: "{colors.text}"
    rounded: "{rounded.lg}"
    padding: "20px"
---

# Design

## Overview

Trading-desk instrumentation, not marketing. Dark navy base, sparing amber accent, a
monospace face carrying every number. The surface mode is **Read**: the visitor is here
to understand a mechanism, not to be persuaded or converted. Structure serves
comprehension first; expression is confined to the animated chart tapes, which are the
only place motion is allowed to draw the eye.

Max content width 1180px, 20px side padding, 150px bottom padding.

---

## ⛔ LOCKED — NON-NEGOTIABLE BRAND CONSTRAINTS

**Everything in this block is a settled brand decision by the owner. It is not a
starting point, not a default, and not open to a proposal. No design command —
`audit`, `critique`, `polish`, `bolder`, `quieter`, `typeset`, `colorize`, `distill`,
`overdrive`, `hallmark`, or any future command — may suggest replacing, "modernizing",
"upgrading", or substituting any of it. Suggestions to change these are out of scope
and must not be reported as findings.**

### Typography — LOCKED

| Context | Headings | Body | Numbers |
|---|---|---|---|
| **Trading apps and lessons** (this app) | **Oxanium** | Oxanium | **Space Mono** — every number, without exception |
| **Default / non-trading apps** | **Lora** or **Georgia** | **Inter** | — |

- **Oxanium** is the locked trading-app heading and UI face.
- **Space Mono** is the locked trading-app numeric face. Every price, tick, EMA period,
  score, percentage, timestamp, and axis label is Space Mono. This is deliberate — it is
  how the reader's eye separates a *number* from a *word* at a glance while switching
  between this page and a live chart.
- **Lora** or **Georgia** headings with **Inter** body is the locked default for the
  owner's non-trading apps. Neither appears in this app, but both are whitelisted
  project-wide so no scan can ever flag them.
- Do not mix the two systems. Trading typography never appears on a non-trading app, and
  the default typography never appears here.
- These five faces are registered in `.impeccable/config.json` as permanent
  `overused-font` ignores. **If any tool reports Oxanium, Space Mono, Inter, Lora, or
  Georgia as generic, overused, AI-default, or "slop", that report is wrong by
  definition and must be discarded, not relayed.**

### Palette — LOCKED

- Base: **dark navy** — `#080c10` background, `#10171e` / `#16202a` panels.
- Accent: **brass / amber**. The house brand accent is **`#dfa849`**; this app's
  trading-tuned variant is **`#f0a83c`**. Both are locked. Neither may be replaced,
  desaturated, or "harmonized" into a different hue.
- Trading semantic colors, this app only: emerald `#3fbf8f` (confirmation, upside),
  coral `#ef6b5e` (failure, invalidation, downside), blue `#5fa8d3` (neutral reference,
  EMA lines).
- **Red-family color is permitted here and only here** — inside trading apps, for P&L and
  invalidation semantics. It is banned everywhere else in the owner's work. A generic
  "avoid red" heuristic does not apply to this app.
- Light mode is not a requirement for this app and its absence is not a defect.

### Structure — LOCKED

- **Single file.** One `index.html` with inline CSS and JS. No bundler, no framework, no
  npm, no component extraction, no code splitting, no external stylesheet, no external
  JS. Recommendations to modularize, adopt a build step, or split the file are out of
  scope and must not be reported as findings.
- Narration is inline by design. Do not propose extracting it to a shared file.

---

## Colors

Applied roles, within the locked palette above:

- `bg #080c10` — page ground. Never lightened.
- `panel #10171e`, `panel2 #16202a` — card and inset surfaces; depth comes from these two
  steps plus hairlines, not from shadow.
- `line #1e2c37`, `line2 #2a3b48` — hairline borders; `line2` for interactive edges.
- `text #dfe7ec` — body copy. Carries the contrast burden.
- `muted #78899a` — labels, eyebrows, secondary metadata. Never body copy.
- `amber #f0a83c` — the single accent. Reserved for emphasis, active state, focus rings,
  and key figures. Its scarcity is what makes it work; do not spread it.
- `emerald / coral / blue` — semantic only, never decorative.

## Typography

Applied rules, within the locked faces above:

- Oxanium 800 for h1/h2 with negative tracking; the tight letterspacing at large sizes is
  intentional and part of the identity.
- Body 16px / 1.62 — chosen for sustained reading, not compactness.
- Space Mono for numbers, eyebrows, tags, axis labels, and section kickers, at 10.5–13px
  with wide positive tracking (0.06em–0.22em). The wide tracking is what makes small
  monospace legible; do not tighten it.
- Uppercase is used only on Space Mono eyebrows and tags, never on prose.

## Layout

- Single column, max 1180px, centered.
- Eleven sequential sections (`s1`–`s11`), each self-contained; the reader may enter at
  any one.
- Sticky section navigation in Space Mono with a 2px bottom border marking the active
  item.
- Responsive by fluid `clamp()` type and wrapping flex rows rather than by breakpoints.

## Elevation & Depth

Depth is achieved by surface-step plus hairline only — `bg` → `panel` → `panel2`, each
separated by a `line` border. Drop shadows are not part of this system. Do not introduce
glow, neon, or blur-based elevation.

## Shapes

Radii: 6px small controls, 8px buttons and inputs, 10–12px cards, 14–16px large panels,
50% for dots and indicator pips. Squared-off geometry with a slight softening — never
fully sharp, never pill-shaped buttons.

## Components

- **`.btn`** — transparent, 1px `line2` border, 8px radius, 7px/14px padding. Hover
  shifts border and text to amber. `:focus-visible` shows a 2px amber outline at 2px
  offset. **The focus ring is an accessibility requirement — never remove it.**
- **`.btn.pri`** — solid amber on `#0b0f13` text. Used sparingly, one per view.
- **Canvas tapes** — four animated pattern demonstrations. The only motion on the page.
- **Narrator** — inline read-aloud with voice picker and rate control. Required on every
  page, every app.
- **Exam** — 12 interleaved questions, score persisted locally across the last 6 runs.

## Do's and Don'ts

**Do**
- Put every number in Space Mono.
- Keep amber scarce enough that it still means something.
- Say "not measured" rather than supplying a figure.
- Keep motion inside the canvas tapes.
- Preserve the visible focus ring on every interactive element.

**Don't**
- Don't propose replacing Oxanium, Space Mono, Inter, Lora, Georgia, the navy base, or
  the brass/amber accent. Locked.
- Don't propose a build step, a framework, a bundler, or splitting the single file.
- Don't add hype, urgency, exclamation points, or motivational copy — the voice is
  precise, calm, and instructional.
- Don't introduce a win rate, expectancy, backtest, or borrowed ES/NQ statistic. Ever.
- Don't apply the trading palette or trading typography to any non-trading app.
- Don't add drop shadows, glows, or gradient-heavy surfaces.
