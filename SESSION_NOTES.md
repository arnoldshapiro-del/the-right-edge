# The Right Edge — Session Notes

## 2026-07-23 — Initial publish, M2K rescope, Vercel deploy

### What we did
- Located `the-right-edge-2.html` (Arnie saved it to the Desktop, not Downloads — an
  earlier full-profile search found nothing because it had not been saved yet).
  Verified 84,085 bytes and both sentinel strings ("THE LIAR BAR", "RESTING ORDERS").
- Created the project folder, moved the file in as `index.html`.
- Added `vercel.json`, `netlify.toml`, `.gitignore`, `README.md`.
- `git init -b main`, committed, created the public GitHub repo, pushed.
- **Rescoped the app to M2K only** after Arnie clarified mid-session that he trades
  M2K exclusively (not MES/MNQ) on 15 / 5 / 2-minute charts:
  - Header line rewritten
  - Two "means the same thing on M2K and MES" teaching lines reworded to preserve the
    scale-invariance point without a second instrument
  - One exam question reworded ("across instruments" → "across market speeds and seasons")
  - **Added a 15-minute button** to the EMA time machine
- Deployed to Vercel through the GitHub integration (browser import, driven in Chrome).
- Created both `.url` shortcuts.

### What's working
Everything, verified on the live URL — not assumed. Zero MES/MNQ references, all three
timeframe toggles with correct arithmetic, exam scoring, narrator actually speaking,
no console errors.

### What's next
- Optional: port the v1 "Trade or Skip" chart trainer back as Section 12.
- Optional: PWA files (none yet).
- Optional: gallery card in arnies-app-showcase.
- August 1: connect Netlify (config already in repo, connect-only).

### Important decisions
- **v2 only, v1 not deployed.** Two live apps teaching the same material would split
  attention. v1 stays on disk for the Trade-or-Skip trainer.
- **Single-file architecture preserved.** Did not swap in trend-check-pro's external
  `narrator.js` — it would break self-containment. The inline narrator covers all 11
  sections and works.
- **Vercel, not Netlify, for now.** Netlify build minutes exhausted until Aug 1.

### Problems encountered
- **The Vercel CLI was blocked by two locks, not one.** Layer 2 (`branch-guard.js`
  vercel net) was removed on Arnie's explicit order. Layer 1 (four `vercel:*` deny
  rules in `~\.claude\settings.json`) could NOT be removed by Claude — Claude Code's
  safety classifier blocks edits to the permissions file. Arnie deleted those four
  lines himself via Notepad find-and-replace; verified afterwards that the file still
  parses as valid JSON and all 8 other protections survived.
- The CLI turned out to be **neither installed nor authenticated** anyway, so the
  browser import was the faster path regardless.
- Global `CLAUDE.md` rule #1 was rewritten: "never Vercel CLI" retired and marked
  do-not-reinstate.

## 2026-10-21 — Session memory: handoff rules, decision ledger, compaction instructions

### What was asked
Arnie asked that the reasons behind decisions survive new sessions and compaction,
after Dylan Davis's video "ChatGPT & Claude Quietly Forget Mid-Task. One File Fixes It".

### What changed
- Added three sections to `CLAUDE.md`, modeled on who-dey-101-2026: "Session handoff
  (do this every session)" and "Decisions and why (one line each, newest last)" right
  after the identifying section, and "Compact Instructions" at the very end.
- The decision ledger was built only from this repo's own CLAUDE.md, SESSION_NOTES.md
  and commit messages; where a reason was never written down it says
  "(reason not recorded)".
- A separate `decisions.md` was ruled out because `CLAUDE.md` is the file Claude Code
  re-reads after compaction.
- Notes-only change. `index.html` and every config file are untouched; the app is
  unchanged.

### What was verified
- `git diff --stat HEAD~1` after the push shows only `.md` files.
- Live URL https://the-right-edge.vercel.app returns HTTP 200 (result recorded in the
  final session reply).

### What's next
- Unchanged from 2026-07-23: optional Trade-or-Skip trainer as Section 12, PWA files,
  gallery card in arnies-app-showcase, Netlify connect.
- From now on, every settled decision gets one line in the CLAUDE.md ledger and every
  session gets a dated entry here.
