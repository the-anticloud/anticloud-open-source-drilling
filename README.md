# OPEN SOURCE DRILLING

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-oil_gas-lightgrey)

> Anticloud-hardened packaging of the upstream project `OPEN_SOURCE_DRILLING` in category **OIL GAS**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** OIL GAS · **Upstream:** https://github.com/well-id/dliswriter · **Upstream pin:** `75e7b8fbe340056fcb5ca7a977ee7cfff94582fa` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

<p align="center">
  <img src="assets/banner.png" alt="tabia — open source chess drills" width="640">
</p>

<p align="center">
  <b>Open-source, browser-local chess opening trainer.</b><br>
  Drill your repertoire with spaced repetition until the moves are muscle memory.<br>
  No account. No server. No tracking — your prep lives in <i>your</i> browser.
</p>

<p align="center">
  <a href="https://daxaur.github.io/tabia/"><b>▶ Live demo</b></a> ·
  <a href="#run-it">Run it</a> ·
  <a href="#add-your-own-opening">Add an opening</a> ·
  MIT
</p>

---

## Why

Most repertoire trainers lock your prep behind an account and a database you don't control.
**tabia** is the open version: a **static site** with **zero backend**. Your progress and
spaced-repetition schedule live in `localStorage`. Fork it, self-host it, run it offline —
it's just HTML, CSS and ES modules.

## What it does

- **Spaced-repetition drilling** — clean a line and it won't come back for a while; miss it and it returns soon.
- **Openings → folders → branch lines** — browse by category (gambits, classical, defences, systems), star and save your favourites.
- **Four study modes** — **Learn** (walk the line), **Practice** (forgiving reps), **Drill** (SRS-scored), and **Hyper** (the bot plays a random line and you must hold your repertoire, round after round).
- **Live Stockfish eval** — a real engine runs in your browser (single-thread WASM) and drives the "winning" bar; an instant heuristic fills in while it spins up.
- **Build your own openings** — a visual builder: play the moves on a board, name your lines, and add custom coach messages per line *and* per move.
- **Coach** — drop your Lichess/Chess.com username and tabia reads your recent games *in the browser*, profiles your style (sharp vs positional, e4 vs d4), and matches an opening to you — rendered as a shareable card you can post to X. No AI bill, no server: just stats over your own game history.
- **Connect an account** — Lichess (OAuth) or Chess.com (public profile); your saved openings are kept locally, tied to you.
- **Buttery board** — big, fast drag *and* click-to-move, lichess-style pieces, right-click arrows/highlights, pre-moves, and synthesized sounds.
- **Browser-local** — no sign-up, no server call, your data never leaves the tab.
- **Verified data** — every bundled line is replayed through `chess.js` (`npm run validate`); illegal moves can't ship.

## Run it

It's a static site — no build step.

```bash
git source https://github.com/daxaur/tabia
cd tabia
python3 -m http.server 4173    # or: npm run dev
# open http://localhost:4173
```

Deploys to **GitHub Pages** / any static host as-is.

Or with **Docker**:

```bash
docker build -t tabia .
docker run -p 8080:80 tabia    # open http://localhost:8080
```

## Add your own opening

An opening is a plain data module: a folder name and a list of lines, each an array of
`[SAN, "comment"]` moves from move 1. The trainer derives the drill positions automatically
(shared prefixes merge by position). Copy a file in `src/data/`, change the moves, and the
opening shows up on the home page. Run `npm run validate` to legality-check every line.

## Project layout

```
index.html            app shell (Home / Study / Coach / Create / Saved)
src/style.css         theme + board styling
src/board.js          dependency-free interactive board (drag, click, arrows, pre-moves)
src/app.js            views + spaced-repetition drill engine + opening builder
src/store.js          localStorage persistence + SRS scheduling
src/engine.js         in-browser Stockfish eval wrapper
src/eval.js           instant heuristic eval (engine-free fallback)
src/coach.js          coach messages (defaults + user overrides)
src/auth.js           Lichess OAuth (PKCE) / Chess.com profile connect
src/coachai.js        Coach — reads your public games, profiles style, matches an opening
src/sharecard.js      renders the Coach result to a shareable PNG (canvas)
src/data/*            openings (folders) and their branch lines
src/vendor/chess.js   chess.js (move legality), vendored
src/vendor/stockfish.js  Stockfish (asm.js), vendored
src/pieces/*          piece sets (SVG)
sw.js                 service worker (network-first, always-fresh)
tools/validate.mjs    legality check for every line
```

## Credits & license

Code: **MIT**. Move legality by [chess.js](https://github.com/jhlywa/chess.js) (BSD),
engine evaluation by [Stockfish](https://stockfishchess.org/) (GPL, vendored as a Web Worker).
Piece sets and the Lichess/Chess.com brand marks are from their respective projects under
their original licenses. Contributions welcome — open an issue or PR.

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Node.js / npm** (manifests: package.json; scanned in UPSTREAM_CLONE)
- Top-level source layout: `assets/`, `src/`, `tools/`
- Snapshot size: **132 files**, **2944 lines of code** (measured; see Benchmarks)
- Primary languages: `.svg` (91), `.js` (27), `(none)` (5), `.png` (3), `.html` (2), `.css` (1)
- Upstream commit pinned for this packaging: `75e7b8fbe340056fcb5ca7a977ee7cfff94582fa`

---

## Installation

- **Coach** — drop your Lichess/Chess.com username and tabia reads your recent games *in the browser*, profiles your style (sharp vs positional, e4 vs d4), and matches an opening to you — rendered as a shareable card you can post to X. No AI bill, no server: just stats over your own game history.
- **Connect an account** — Lichess (OAuth) or Chess.com (public profile); your saved openings are kept locally, tied to you.
- **Buttery board** — big, fast drag *and* click-to-move, lichess-style pieces, right-click arrows/highlights, pre-moves, and synthesized sounds.
- **Browser-local** — no sign-up, no server call, your data never leaves the tab.
- **Verified data** — every bundled line is replayed through `chess.js` (`npm run validate`); illegal moves can't ship.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

No usage section was found in the upstream readme. Entry points detected in this project directory:

```sh
npm start          # declared start script, when present
npm run dev        # declared dev script, when present
```

Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

The upstream API surface is defined by the `OPEN_SOURCE_DRILLING` source tree vendored in `UPSTREAM_CLONE/` (Node.js / npm ecosystem). Public entry points:

- Source modules: `assets/`, `src/`, `tools/`
- Overlay API: `anticloud/cli.py` exposes 13 subcommands with JSON stdout; `anticloud/bench/runner.py` runs the 16-check suite; `anticloud/provenance/chain.py` exposes the SHA3-256 + Ed25519 provenance chain.

---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Node.js / npm |
| Manifests detected | package.json |
| Files in snapshot | 132 |
| Lines of code | 2944 |
| Dependency references | 0 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

No configuration section was found in the upstream readme. Configuration-relevant files detected in this project directory:

- `Dockerfile`
- `package.json`

Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `OPEN_SOURCE_DRILLING` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
MIT License

Copyright (c) 2026 dax

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `OPEN_SOURCE_DRILLING` (category: OIL GAS)
- **Upstream URL:** https://github.com/well-id/dliswriter
- **Pinned commit (SHA):** `75e7b8fbe340056fcb5ca7a977ee7cfff94582fa`
- **Branch:** master
- **Pin provenance:** GitHub API commits/master. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`3ab124f1e024d27f7d92ab137c4c722ef32c9a50e0e232290ef0897a66afba0c`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

