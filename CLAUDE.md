# The Right Edge — Second Edition · Project Memory

## What This App Is
Single-file animated teaching app for **M2K micro Russell futures only** — pattern
trading on the 2-minute entry chart. Covers the auction mechanics behind triangle
breakouts, the Liar Bar (mid-bar false breaks), the 20 EMA bounce, the four-condition
close test, EMA period arithmetic, flag tightness grading, and a 12-question
interleaved exam. "Second Edition — the mechanism cut": it explains *why* each pattern
works (resting orders, inventory, vacuum), not just what it looks like.

## Session handoff (do this every session)
- Start: read `SESSION_NOTES.md` (the dated journal) and `CONTINUATION.md` if present, before touching anything. The newest entry says what was decided, what was verified and what is next.
- Wrap-up: add a dated entry to `SESSION_NOTES.md` with what was asked, what changed, what was verified (and how) and what is next. Commit and push it together with the work.
- Every settled decision goes in the ledger below as ONE line: what we decided, why, and what was ruled out and why. Every correction Arnie gives gets logged with his reason. Reasons matter more than facts: facts can be re-derived from the code, reasons cannot.
- Unsure what was agreed? Re-read this file and the journal before asking Arnie again.

## Decisions and why (one line each, newest last)
- M2K only, never MES or MNQ: Arnie clarified mid-session that he trades M2K exclusively on 15 / 5 / 2-minute charts with entries on the 2. Ruled out: keeping the original "M2K · MES" wording, because a second instrument muddies the teaching and does not match how he trades (2026-07-23).
- Added a 15-minute button to the EMA time machine: Arnie's top chart is the 15-minute, and the toggle only had 2 and 5 (2026-07-23).
- Deploy v2 only; v1 stays on disk, not deployed: two live apps teaching the same material would split attention. v1 is kept for its "Trade or Skip" chart trainer, worth porting back as Section 12 (2026-07-23).
- Single-file architecture preserved; the narrator is this app's own inline version, not trend-check-pro's external `narrator.js`: an external file would break self-containment. Ruled out: adding any external file; port the saved-speed and sentence-highlight conveniences inline if wanted (2026-07-23).
- Vercel via GitHub integration, not Netlify, for now: Netlify free build minutes were exhausted until August 1, 2026. `netlify.toml` kept in the repo so Netlify is connect-only later (2026-07-23).
- Vercel deployed through the browser import, not the CLI: the CLI turned out to be neither installed nor authenticated, so the browser path was faster. The two locks that had blocked the CLI were removed on Arnie's explicit order; the global "never Vercel CLI" rule was retired and marked do-not-reinstate (2026-07-23).
- Honesty posture kept: the four-condition close test is labeled "reasoned, not backtested" and the 0.25 × ATR(14) figure "a judgment call", because no published research measures close-distance-above-EMA on intraday futures. Ruled out: quoting any win rate here, because the sibling app's ES/NQ figures do not apply to Russell (2026-07-23).
- Trading design system (Oxanium + Space Mono, amber/emerald/coral on dark navy), used for trading apps only and never elsewhere (reason for the palette itself not recorded) (2026-07-23).
- Created/Revised date stamp added under Arnie's standing order of 2026-07-23 (reason not recorded) (2026-07-23).
- Impeccable + Hallmark design skills added project-scoped on 2026-07-31, then removed the next day along with reduced-motion, stat-sourcing and accessibility fixes (reason for removal not recorded) (2026-08-01).
- Private access gate, Google Sign-In for Arnie's account only: locks the trading app to his address using the same Firebase pattern proven on opening-edge-playbook and m2k-mastery; any other account is signed straight back out. Covered by the shared browser key's wildcard Netlify referrer, so no per-app Google console work (2026-08-01).
- Sign-in gate pinned with `position:fixed; inset:0` and max z-index: a normal-flow gate can be clipped by a page whose CSS sets `html,body{overflow:hidden}`, which caused black screens on two sim-practice-video apps. Preventive here (2026-08-01).
- Session memory lives in this file and `SESSION_NOTES.md`, never only in chat: cloud sessions start on a fresh computer, chat history gets compacted, and only files in the repo survive (2026-10-21, after Dylan Davis's "decisions.md" video). Ruled out: a separate decisions.md, because this file is the one Claude Code re-reads after compaction.

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

## Compact Instructions
When this conversation is compacted, the summary must keep, in this order:
1. Every decision made this session, with its reason and what was ruled out.
2. Every correction Arnie gave, in his words where possible, and his reason.
3. What has been verified and how (test run, build, live check with URL and time) versus what is only claimed or planned.
4. What is next and what is still open, including anything waiting on Arnie's yes.
5. The exact files changed, the branch, and whether the work is committed and pushed.
Drop tool output, file contents and search results; they can be re-read from disk.
