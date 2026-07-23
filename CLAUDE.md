# The Right Edge — Second Edition · Project Memory

## What This App Is
Single-file animated teaching app for **M2K micro Russell futures only** — pattern
trading on the 2-minute entry chart. Covers the auction mechanics behind triangle
breakouts, the Liar Bar (mid-bar false breaks), the 20 EMA bounce, the four-condition
close test, EMA period arithmetic, flag tightness grading, and a 12-question
interleaved exam. "Second Edition — the mechanism cut": it explains *why* each pattern
works (resting orders, inventory, vacuum), not just what it looks like.

## Live URLs
- **Production:** https://the-right-edge.vercel.app
- **GitHub:** https://github.com/arnoldshapiro-del/the-right-edge
- **Local:** `C:\Users\arnol\Desktop\Project Files Do Not Delete\the-right-edge\`

## Deployment
- **Vercel** via GitHub integration (imported 2026-07-23). Every push to `main`
  auto-deploys. No CLI involved.
- `netlify.toml` is present and ready — Netlify can be connected from **August 1, 2026**
  when the free build minutes reset. Not connected yet, deliberately.
- Static site: no build step, no framework, no npm, no package.json. Preset "Other",
  root `./`, build command empty.

## Tech
- One self-contained `index.html` (~84 KB). Inline CSS + JS. No external resources
  except Google Fonts.
- Trading design system: Oxanium + Space Mono, amber/emerald/coral on dark navy.
  (Trading apps only — never this palette elsewhere.)
- 11 sections, ids `s1`–`s11`.
- 4 animated canvas "tapes": ascending triangle, descending triangle, Liar Bar, EMA bounce.
- Narrator: inline read-aloud, `#nplay` button, voice picker, rate 0.96, `SPEECH`
  map keyed `s1`–`s11` (one entry per section). Cancels on `beforeunload`.
- Exam: 12 questions, `QS` array, score persists via `Store` (`re2.exam`, last 6 runs).
- EMA time-machine toggle: `data-tf` buttons for 2 / 5 / **15**-minute. `setTM()` is
  generic — adding another timeframe is a one-line HTML change, no JS edit.

## Instrument + Timeframe Scope (LOCKED 2026-07-23)
**M2K ONLY.** Not MES, not MNQ. Arnie's charts are **15-minute, 5-minute, 2-minute**,
with entries taken on the 2. The app was originally written "M2K · MES" and was
rescoped this session — all MES/MNQ references removed and verified at zero on the
live site. Do not reintroduce them.

## Honesty Posture (deliberate — keep it)
The app openly labels what is *not* backtested:
- The four-condition close test is "reasoned, not backtested."
- The 0.25 × ATR(14) figure is flagged "my judgment call, not a tested figure."
- No published research measures close-distance-above-EMA on intraday futures.

This matters because the sibling app (opening-edge-playbook) carries ES/NQ win rates
that do **not** apply to M2K. Never quote a percentage here as if it were measured on
Russell. See memory `m2k-only-and-timeframes.md`.

## Verified Working (2026-07-23, on the live URL)
- Zero MES/MNQ/ES/NQ references; M2K appears 6 times
- Header reads `M2K only · 15 / 5 / 2-minute · entries on the 2`
- All three timeframe buttons; 15-min math correct (9 EMA 2.25 hrs, 20 EMA 5 hrs,
  200 EMA 50 hrs)
- Exam runs, scoring increments correctly
- Narrator speaks (`speechSynthesis.speaking` true on click), all 11 sections covered
- No console errors

## Known Issues / Future Ideas
- **Narrator is this app's own inline version, not a copy of trend-check-pro's
  `narrator.js`** (16.6 KB external file). Deliberate — this app is single-file by
  design. Missing two conveniences from the canonical one: saved reading-speed
  preference across sessions, and sentence-by-sentence highlighting while reading.
  Port them inline if wanted; do not add an external file.
- No PWA files yet (manifest, icons, service worker).
- v1 of this app had a **"Trade or Skip" trainer** — 7 chart scenarios called live.
  v2 dropped it. The exam tests concepts verbally; that trainer tested chart
  recognition. Worth porting back as Section 12. The v1 file is on disk, not deployed.
- No gallery card in arnies-app-showcase yet.
