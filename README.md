# Web Tetris

A fully-featured Tetris game running in the browser — single HTML file, zero dependencies.

**[Play instantly](https://chichichickenpie.github.io/web-tetris/tetris.html)** — just open `tetris.html` in any modern browser.

---

## Features

- **Tetris Guideline compliant**
  - 7-bag randomizer (prevents long droughts)
  - SRS (Super Rotation System) with full wall kick tables
  - Ghost piece, Hold piece, Next 5 preview
  - Lock delay with up to 15 resets
  - Back-to-back bonus (Tetris / T-Spin chains)
- **DAS / ARR** — standard delayed auto-shift and auto-repeat for smooth movement
- **Guideline scoring** — Single/Double/Triple/Tetris × level, T-Spin bonuses
- **Level system** — speed increases every 10 lines (Guideline formula)
- **Dark theme** with official Tetromino colors

## Controls

| Key | Action |
|-----|--------|
| `←` / `→` | Move left / right |
| `↓` | Soft drop |
| `Space` | Hard drop |
| `X` / `↑` | Rotate clockwise |
| `Z` / `Ctrl` | Rotate counter-clockwise |
| `C` / `Shift` | Hold |
| `P` / `Esc` | Pause / Resume |
| `Enter` | Start / Restart |

## Scoring

| Action | Points |
|--------|--------|
| Single | 100 × level |
| Double | 300 × level |
| Triple | 500 × level |
| Tetris | 800 × level |
| Tetris (B2B) | 1200 × level |
| T-Spin Single | 800 × level |
| T-Spin Double | 1200 × level |
| Soft drop | 1 pt / row |
| Hard drop | 2 pt / row |

## Tech Stack

- Vanilla JavaScript (ES2022+)
- HTML5 Canvas API
- CSS3
- No frameworks, no build tools — single `.html` file

## Usage

```bash
git clone https://github.com/chichichickenpie/web-tetris.git
cd web-tetris
open tetris.html   # macOS
xdg-open tetris.html  # Linux
```

Or just download `tetris.html` and open it directly.

## License

MIT
