# Rewire: project notes

The single place to catch up on Rewire: what it is, where everything lives, every decision made so far, and what's next.
**If you're Claude in a new conversation, read this whole file first, then read `source/rewire.html`.**

_Last updated: November 12, 2026 · current version 7.1_

---

## 1. What Rewire is

A daily neuroplasticity ("use it or lose it") brain-training web app built by **Kellan Ismail**, a premedical neuroscience student at Michigan State University (applying to medical school in **May 2028**). It supports his application's adaptation theme.

- Eight cartoon mini-games, each built on a published research task, with adaptive difficulty and a daily three-game circuit aimed at the player's weakest skill.
- Puzzle Lab: medical crosswords (5×5 Mini, 11×11 Daily, 13×13 Challenge), Term Lab (medical word building), Case of the Week (clinical neurology cases).
- Progress tracking, medical-training ranks, badges, weekly challenges, Mastery levels, daily cited brain facts, References, About page, settings and accessibility, background music, installable offline app.

## 2. Where everything lives

| What | Where |
|---|---|
| Live app on Claude | https://claude.ai/artifact/SW48eRg3gryAx2becwgMFc (always the newest version; Claude can read the full code back from this link) |
| Public site | https://kellanismail.github.io/rewire/ |
| GitHub repository | https://github.com/kellanismail/rewire |
| Master source code | `source/rewire.html` (one file: HTML + CSS + JavaScript) |
| Site files (generated) | repository root: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` |
| Build script | `source/build-site.js` |
| Crossword tools | `source/crossword-tools/` |

## 3. How to update the app

1. Edit `source/rewire.html` (this is also what gets published to the Claude link).
2. Run `node source/build-site.js` from the repository root. It writes `index.html`, `manifest.webmanifest` and `sw.js` at the root (adds the doctype, mobile viewport, icons, manifest link and service-worker registration that Claude's viewer normally supplies).
3. Commit with a clear message, e.g. `Version 8: ...`.
4. Bump `const APP_VERSION` in `rewire.html` for each release (shown on the About page; also names the offline cache).

Kellan has been uploading files by hand on github.com (Add file → Upload files). Only `index.html` (and `sw.js` when the version changes) usually need re-uploading; icons and manifest rarely change.

## 4. Kellan's working preferences (important)

- **Never build a new version until Kellan explicitly says so** ("go", "let's do it", "next iteration"). He sends notes first; Claude keeps a running list and confirms it, without generating.
- He likes: explanations in plain language, a short summary of what changed, honest testing notes, and flagged items to review.
- Design style he chose: **playful cartoon** (thick outlines, hard offset shadows, bright colors, mascot "Neuri", a purple neuron).
- Sound and music start **muted/off**; preferences are remembered.

## 5. Decisions already made (don't relitigate)

**Content and integrity**
- Science claims stay honest: practice improves the trained tasks; far transfer is limited (2014 consensus statement). The app never promises to raise IQ and says it's not diagnostic.
- Citations use **AMA style**, listed on the References tab with a "✓ Checked against source" or "Not yet checked" status. Only 2 are checked (Northwestern Medicine article; Gómez-Pinilla 2008). The rest were written from memory and need verification against originals.
- Daily facts are paraphrased (not copied) from: Northwestern Medicine HealthBeat, "11 Fun Facts About Your Brain," compiled by Kapil Sachdeva, MD, updated June 2024. Pop-up shows source + link. Note: a few of those facts are popular simplifications (60% fat, brain "fully formed" at 25, spinal cord stops growing at 4); quoted accurately and credited, but peer-reviewed replacements would be stronger.
- Copyright: summarize sources in your own words; never reuse figures/tables as images.

**About page**
- Uses the lightly polished version of Kellan's "Why I built Rewire" text, signed "Kellan Ismail."
- **No** "how Rewire was made" / AI-assistance section (Kellan's explicit decision).
- **No** phone, home town, GPA, test scores, awards, or photo. **No** contact email yet.
- Placeholders ready (hidden until filled): `ABOUT_VIDEO` (YouTube link, Unlisted is fine, or a video file path) and `CONTACT_EMAIL` (Kellan will create a dedicated address). Both are constants near the About code in `rewire.html`.
- About-me content comes from his résumé: MSU neuroscience; research assistant, Bhattacharya Lab (MSU IQ), single-cell/spatial transcriptomics with Python + ML; former medical assistant (internal medicine & pediatrics practice); McLaren Greater Lansing volunteer; Motown Mercy director of partnerships; Learn to Be tutor; National Kidney Foundation volunteer; martial arts, golf, weightlifting, SCUBA, travel.

**Accounts and research (ON HOLD)**
- Accounts will use **anonymous code IDs** (e.g. `MAPLE-OTTER-42-TEAL`), no personal information. Save-your-code card/QR, device-first storage with cloud sync, admin view by code only, Firebase or Supabase.
- A **built-in Survey tab** (always available, any user can fill it out; no pop-ups or timing).
- **Neither gets built until Kellan has a faculty mentor and IRB approval.** Do not build early.

**Games**
- Switchyard was replaced by Creature Keeper (too easy).
- The quick crossword is **5×5**, not 7×7: a 7×7 grid needs mostly 7-letter answers, which the hand-written word list can't fill.
- Shape Shifter Sort uses Okabe-Ito colors (color-blind safe); Potion Shop has a color-blind mode in Settings.

## 6. Next-version list (waiting for Kellan's go)

1. **Louder music**: raise the overall level ~2-3×, default volume ~70%, add a limiter (DynamicsCompressor) so it never clips. Music engine is `const Music` in `rewire.html` (`level()` sets loudness; currently `.16 * vol`).

## 7. Waiting on Kellan

- Video for the About page; dedicated contact email.
- Verification of the "Not yet checked" references (Kellan said he'd also add his own references to `MY_REFERENCES`).
- Brain Food section sources (so far only Gómez-Pinilla 2008, Nat Rev Neurosci).
- A faculty mentor + IRB (unlocks accounts and the survey).
- Fix on his résumé: ACT shows "34/46" (should be 34/36); "LinkedInURL" is placeholder text.

## 8. Ideas discussed for later (not scheduled)

Brain Atlas (tap brain regions, unlock as you play), Myth or Fact quiz, fixed-difficulty check-in assessments every 4 weeks (fair way to measure improvement, since adaptive levels shift), first-time tutorial + placement test, "What's new" changelog page, backup/restore, more crossword themes, peer-reviewed daily facts.

## 9. Version history

| Version | Highlights |
|---|---|
| 1 | Prototype: 4 games, daily rotation, adaptive difficulty, fading brain map |
| 2 | Cartoon redesign, sound, 6 themed games, points/combos/stars |
| 3 | Progress screen: charts, practice calendar, records, CSV export |
| 4 | Shape Shifter Sort, Neuron Trail, Puzzle Lab (crossword, Term Lab) |
| 5 | Did you know? pop-up, Facts tab, Creature Keeper, 11×11 crossword bank, game "juice" |
| 6 | Ranks, badges, weekly challenges, Mastery levels 11-15, References tab, 5×5 and 13×13 crosswords, Advanced Term Lab, cited NM facts |
| 7 | Background music, About page, Case of the Week, Settings & accessibility, installable offline app |
| 7.1 | Puzzles tab; bigger tab bar (bottom bar on phones) |

## 10. How the code is organized (`rewire.html`)

One file. Roughly in order:
- `<style>`: design tokens at the top (`:root`, with dark-mode overrides in two blocks), then components. Colors always come from tokens; both light and dark themes are designed.
- HTML: header (mascot, stats, Sound/Music/Settings buttons), `.mainnav` tab bar, then one `<section>` per view: `home`, `puzzles`, `progress`, `facts`, `refs`, `about`, `settings`, `play` (games and puzzles run here).
- Script (one IIFE): `Sound` (effects), `GAMES` (each game: params, rules, `run(ctx)`, science card), n-back engines, shapes, state/storage (`localStorage` key `rewire.v2`), ranks/badges/weekly challenges, home rendering, game runner + `makeJuice()` (points, combos, sparkles), `finish()`, Puzzle Lab (crossword banks `XW_BANKS` + `XW_CLUES`, Term Lab, Case of the Week `CASES`), progress charts, references (`REFERENCES`, `MY_REFERENCES`), daily facts (`FACTS`), `Music`, settings, About, routing (hash-based: `#puzzles`, `#progress`, `#facts`, `#refs`, `#about`, `#settings`).
- Adding a daily fact: add `{ text, ref }` to `FACTS` (ref = an id in `REFERENCES`).
- Adding a reference: add to `MY_REFERENCES` (same shape as `REFERENCES`; `group: 'Your references'`).

## 11. Crossword tools (`source/crossword-tools/`)

Hand-written word lists (no outside dictionary): `medical.js` (medical words with clues), `general.js` (everyday 3-6 letter words), `general7.js` (7-letter words, Mini/7×7 experiments only), `clues.js` + `clues2.js` (clues for everyday words).

- `gen.js`: builds symmetric American-style grids and fills them. Settings via environment variables, e.g. 11×11: `MINB=28 MAXB=36 OUT=bank.jsonl node gen.js 30 <seed>`; 13×13: `N=13 LONGMIN=8 LONGLO=2 LONGHI=5 SEVENMAX=6 MAXRUN=11 MAXROW=7 MINB=36 MAXB=48 ...`; 5×5: `N=5 LONGMIN=99 LONGLO=0 LONGHI=0 SEVENMAX=0 MAXROW=2 MINB=0 MAXB=4 ...`. `BAN=WORD1,WORD2` excludes theme answers already used.
- `select2.js <bank.jsonl> <count> <out.json>`: picks the best puzzles and lists answers that still need clues.
- `export2.js`: combines `chosen5.json` (Mini), `chosen.json` (Daily), `chosen13.json` (Challenge) with clues into `banks.js`, failing if any answer lacks a clue. Paste its contents over `XW_BANKS`/`XW_CLUES` in `rewire.html`.

## 12. How testing has been done

Each release was tested headlessly with Playwright (Chromium): every view loads without console errors; games start, take input and finish; crosswords validated structurally and solved via Reveal; light/dark themes; phone (390 px and 340 px), tablet and desktop widths with no sideways scrolling; GitHub build served locally, including offline mode via the service worker. Audio can't be heard in testing; Kellan checks music by ear.
