# ♛ Regal Chess

A premium, **fully offline** chess game that runs in any modern browser and installs like a native app.
No servers, no CDN, no external fonts, no images — every piece is inline SVG and every sound is synthesized with the Web Audio API.

![Screenshot placeholder](screenshot.png)
<!-- Replace screenshot.png with a real screenshot of the game. -->

**▶ Play online:** https://YOUR-USERNAME.github.io/YOUR-REPO/  <!-- placeholder: replace after deploying -->

---

## Features

**Game modes**
- **Play vs Computer** — 5 difficulty levels (Beginner → Expert), choose White / Black / Random, optional clocks
- **Play with Friend** — local 2-player on one device, custom names, choose or randomize colours, three board modes: *Fixed*, *Auto-flip*, *Tabletop* (the opponent's pieces and clock face them across the table)
- **Continue** an unfinished game (auto-saved after every move, in either mode)
- **Puzzles** — 30 built-in mate-in-1 and mate-in-2 puzzles with hints and saved progress
- **Learn** — interactive tutorials: piece moves, castling, en passant, promotion, check vs checkmate
- **Stats & Badges** — win/loss/draw per difficulty, friend-mode stats, 14 achievements
- **Import / Export** — PGN and FEN (copy/paste, file download, file upload)

**Rules (complete)**
- Legal moves for every piece, pins, check, checkmate, stalemate
- Castling (unmoved pieces, empty squares, not out of / through / into check)
- En passant (including the discovered-check edge case), promotion with a popup (or auto-queen), promotion with capture
- Threefold repetition, 50-move rule, insufficient material, draw offers, resignation
- Timeouts (a draw if the opponent cannot possibly mate)
- The engine is verified with perft against the standard reference positions

**Computer opponent**
- Minimax with alpha-beta pruning, iterative deepening, transposition table, move ordering (TT move, MVV-LVA, killers, history), late-move reductions, quiescence search
- Evaluation: material, piece-square tables, king safety (pawn shield, open files), passed / doubled / isolated pawns, rook files, bishop pair
- Runs in a **Web Worker** created from an inline Blob, so the UI never freezes
- Difficulty = search depth + controlled randomness; Beginner makes occasional mistakes so newcomers can win
- Hint button, evaluation bar, undo (reverts your move *and* the reply), premoves

**Extras**
- Live opening names (≈55 built-in lines)
- Post-game **review**: step through the game; every move marked Best / Good / Inaccuracy / Mistake / Blunder, with an evaluation graph
- Move history in algebraic notation; tap any move to review that position, then jump back to the live game
- Captured-pieces tray with material advantage
- Clocks: Unlimited, 3+2, 5+0, 10+0, 15+10 with low-time warning

**Design & comfort**
- Dark theme (default) and light theme, glass panels, soft glows
- 3 board themes (Classic Wood, Emerald Green, Midnight Blue) + a custom colour picker; 3 piece styles (Glossy, Flat, Neon)
- Smooth piece sliding, capture pop, pulsing check glow, confetti on victory
- Click-to-move **and** drag-and-drop (mouse + touch), legal-move dots / capture rings, last-move highlight
- Colour-blind-safe highlights (blue / amber / orange / violet; classifications also use symbols, not just colour)
- English **and বাংলা (Bangla)** for all menus and labels
- Haptics (vibration) and Screen Wake Lock during a game, where the browser supports them
- Fully responsive, thumb-friendly, no page scrolling during a game

**Keyboard shortcuts**
`U` undo · `F` flip board · `H` hint · `←` `→` step through moves · `Home` / `End` first / live position · `Esc` close dialogs / cancel selection

---

## Install as an app

| Platform | Steps |
|---|---|
| **Android (Chrome / Edge)** | Open the game → menu (⋮) → **Install app** (or use the **Install app** tile on the home screen) |
| **iPhone / iPad (Safari)** | Open the game → **Share** → **Add to Home Screen** |
| **Desktop (Chrome / Edge)** | Click the install icon in the address bar, or use the **Install app** tile |

After the first load the service worker caches everything, so the game works with **no internet connection**.

> **Icon note:** `icon.svg` is used as both the regular and the *maskable* icon. Some platforms (notably iOS home-screen icons) prefer PNG; if you want one, export `icon.svg` to a 180×180 / 192×192 / 512×512 PNG and add it to `manifest.json`.

---

## Deploy on GitHub Pages

1. Create a new GitHub repository (e.g. `regal-chess`).
2. Upload **all five files** to the repository root: `index.html`, `manifest.json`, `sw.js`, `icon.svg`, `README.md`.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then **Save**.
5. After a minute your game is live at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.
6. Update the *Play online* link and the *GitHub* link / name in the footer (search for `[YOUR NAME]` and `YOUR-USERNAME` in `index.html`).

All paths are relative, so it works from a sub-folder URL such as `/regal-chess/`.
**Updating the game?** Change the `CACHE` name in `sw.js` (e.g. `regal-chess-v2`) so installed copies refresh.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire game — HTML, CSS and JavaScript inline in one file |
| `manifest.json` | PWA manifest (name, colours, icons, standalone display) |
| `sw.js` | Service worker — caches everything for offline play |
| `icon.svg` | App icon (also referenced as maskable) |
| `README.md` | This file |

## License

MIT License — free to use, modify and share. Add a `LICENSE` file with the standard MIT text and your name:

```
MIT License

Copyright (c) 2026 [YOUR NAME]

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
SOFTWARE.
```
