# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file browser Tetris (`tetris.html`) — no build tools, no dependencies, no package manager. Open the file directly in a browser to run.

## Running the Game

```bash
xdg-open tetris.html        # Linux
open tetris.html            # macOS
# Or: drag tetris.html into a browser window
```

## Architecture

Everything lives in `tetris.html` in three sections: `<style>`, markup, and `<script>`. The script is organized into these classes:

| Class | Responsibility |
|-------|---------------|
| `Bag` | 7-bag randomizer — shuffles all 7 piece types before repeating |
| `Piece` | Piece state (type, rotation, position) and `cells()` helper |
| `Board` | 10×22 grid (20 visible + 2 hidden spawn rows), collision, lock, line clear |
| `Game` | Game state machine (`START/PLAYING/PAUSED/GAME_OVER`), scoring, level, DAS/ARR timers delegated to `Input` |
| `Renderer` | Canvas drawing for board, hold panel, next queue |
| `Input` | Keyboard events, DAS (133ms) / ARR (10ms) auto-repeat logic |

The game loop (`requestAnimationFrame`) calls `input.update(delta)` → `game.update(delta, softDropping)` → all three `renderer.draw*()` methods every frame.

## Key Constants (top of `<script>`)

- `SHAPES` — SRS cell offsets for all 4 rotations of each piece
- `KICKS_JLSTZ` / `KICKS_I` — SRS wall kick tables indexed by `kickIndex(fromRot, toRot)`
- `LOCK_DELAY = 500ms`, `LOCK_RESET_MAX = 15`, `DAS = 133ms`, `ARR = 10ms`
- `CELL` — computed from viewport height at load time; changing it resizes everything

## Tetris Guideline Notes

- Rotation uses SRS; `kickIndex()` maps `(fromRot, toRot)` → index into kick table
- T-Spin detection is corner-based (3 of 4 corners of the T bounding box occupied)
- Fall speed formula: `(0.8 - (level-1) × 0.007)^(level-1)` seconds/row (capped at ~60fps)
- Back-to-back applies to Tetris clears and T-Spins (1.5× multiplier)
