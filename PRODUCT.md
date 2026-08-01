# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

One primary user: an experienced discretionary futures trader learning to read chart
patterns by their underlying auction mechanics rather than by shape recognition.

He is not a beginner. He already knows what a triangle and a flag look like and can
place an order without help. What he is learning is *why* those formations resolve the
way they do — resting orders, inventory imbalance, the vacuum above a shelf — so he can
tell a real break from a false one in real time.

Situation of use: at a desk, before or between sessions, on a monitor, with charts open
in another window. Not on a phone in a waiting room. He reads a section, then goes and
looks at the same thing on a live chart. Sessions are short and repeated, not one long
sitting.

## Product Purpose

A single-page teaching app that explains the mechanism behind a small set of chart
patterns on M2K (micro Russell 2000 futures), on 15-minute, 5-minute, and 2-minute
charts, with entries taken on the 2-minute.

Scope, deliberately narrow and locked: the auction mechanics behind triangle breakouts,
the Liar Bar (mid-bar false break), the 20 EMA bounce, the four-condition close test,
EMA period arithmetic across timeframes, and flag tightness grading. It closes with a
12-question interleaved exam.

Success is not time on page or completion. Success is that the trader can look at a
2-minute chart and say out loud what the resting orders are doing — and can tell when a
break has no mechanism behind it and should be skipped.

## Positioning

Most pattern education teaches recognition: here is the shape, here is the win rate,
take the trade. This app teaches causation and explicitly refuses to supply win rates it
cannot substantiate. That refusal is the position, not a gap in the content.

Second Edition is "the mechanism cut" — same patterns as the first edition, rewritten to
explain *why* each one works.

## Operating Context

- Instrument: **M2K only.** Not MES, not MNQ, not full-size RTY. This is locked
  (2026-07-23) and was enforced by removing every MES/MNQ reference from the app.
- Timeframes: 15-minute and 5-minute for structure, 2-minute for entries.
- The reader alternates between this page and a live NinjaTrader chart. The app is a
  reference he returns to, not a course he completes once.
- A sibling app (`opening-edge-playbook`) carries ES/NQ win rates. Those numbers do not
  transfer to Russell and must never appear here.

## Capabilities and Constraints

- One self-contained `index.html`, roughly 84 KB, inline CSS and JS. **No build step, no
  npm, no package.json, no framework, no bundler.** Single-file is a design decision, not
  an unfinished state. Suggestions to split, bundle, or code-split are out of scope.
- Only external resource: Google Fonts (Oxanium, Space Mono).
- 11 sections, ids `s1`–`s11`.
- Four animated `<canvas>` "tapes": ascending triangle, descending triangle, Liar Bar,
  EMA bounce.
- Inline read-aloud narrator (`#nplay`), voice picker, rate 0.96, one `SPEECH` entry per
  section, cancels on `beforeunload`. Deliberately inline rather than the shared external
  `narrator.js` — do not add an external file here.
- EMA time-machine: `data-tf` buttons for 2 / 5 / 15-minute; `setTM()` is generic, so
  adding a timeframe is a one-line HTML change.
- Exam: 12 questions in a `QS` array; score persists via `Store` (`re2.exam`, last 6 runs).
- Hosting: static, GitHub → Vercel auto-deploy. `netlify.toml` staged for a second host.
- Not yet built: PWA files (manifest, icons, service worker); a "Trade or Skip" chart-
  recognition trainer that existed in v1 and was dropped in v2.

## Brand Commitments

- Name: **The Right Edge — Second Edition.**
- Author of record: Dr. Arnold Shapiro. Content is his clinical-grade standard of care
  applied to trading education.
- Typography and palette are **locked**. See DESIGN.md. They are not open to redesign
  proposals under any command.
- Voice: precise, calm, instructional. Never hype. No exclamation points, no "crush the
  market", no urgency language, no motivational filler. The tone of a careful colleague
  explaining a mechanism at a whiteboard.

## Evidence on Hand

- The app's own worked examples and animated tapes are the demonstration. There is
  nothing else — no testimonials, no customer logos, no case studies, no track record,
  no performance figures.
- **No win rate, expectancy, or backtest number may be introduced anywhere in this app.**
  Fabricating one would be the single worst possible failure here. Where a figure is
  unavoidable the app already labels it honestly:
  - the four-condition close test is "reasoned, not backtested";
  - the 0.25 × ATR(14) threshold is "my judgment call, not a tested figure";
  - no published research measures close-distance-above-EMA on intraday futures.
  That honesty posture is a deliberate product feature. Preserve it exactly.

## Product Principles

1. **Mechanism before pattern.** Every visual must earn its place by explaining cause.
2. **Never fabricate a number.** No win rates, no backtests, no borrowed ES/NQ statistics.
   Say "not measured" and move on.
3. **M2K only, 15/5/2 only.** Any other instrument or timeframe is an error, not a
   generalization.
4. **Single file, no dependencies.** Portability and load speed over architecture.
5. **Calm over persuasive.** This is a Read surface, not a Persuade surface. It is not
   selling anything.

## Accessibility & Inclusion

- Read-aloud narration is required on every page of every app in this family — the
  narrator is a standing accessibility commitment, not a feature.
- `prefers-reduced-motion` is already honored for scroll behavior; the animated canvas
  tapes have not been audited against it.
- Standard: WCAG AA for body text is the goal, with the documented exception that the
  amber accent is a locked brand color.
