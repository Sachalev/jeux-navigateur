# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This workspace contains standalone, single-file browser games written in French. Each game is a self-contained HTML file with embedded CSS and JavaScript — no build tools, no dependencies, no package manager.

## GitHub

Repository: https://github.com/Sachalev/jeux-navigateur
Remote: `origin` → `https://github.com/Sachalev/jeux-navigateur.git`

## Running the games

Open any `.html` file directly in a browser (no server required):
- `puissance4.html` — Connect Four (Puissance 4) with 2-player and vs-AI modes
- `echecs.html` — Chess game (Jeu d'Échecs)

## Git workflow

After every meaningful unit of work, commit the changes and push to GitHub:

```bash
git add <changed files>
git commit -m "descriptive message explaining what was done and why"
git push
```

Commit frequently — after each feature, fix, or significant edit — so the commit history serves as a complete log of progress. Write specific commit messages (e.g. `"fix: AI blocks opponent's winning move at depth 1"`) rather than vague ones (`"update"`). This ensures no work is ever lost and the state of the project is always recoverable from Git history.

## Architecture

Each game is entirely self-contained in one file:
- **CSS** in `<style>` — dark blue/purple gradient theme (`#1a1a2e` background), consistent across files
- **HTML** — game board rendered via JavaScript into a `<div id="board">` grid
- **JavaScript** in `<script>` — all game logic, state, and rendering inline

### Connect Four (`puissance4.html`)
- Board state: 2D array `board[ROWS][COLS]` (6×7), cells are `null | 'red' | 'yellow'`
- AI: Minimax with alpha-beta pruning, depth 6, column evaluation order `[3,2,4,1,5,0,6]` (center-first)
- Win detection: `checkWin(row, col, player)` checks 4 directions from the last placed piece

### Chess (`echecs.html`)
- Same visual style as Puissance 4
- Board uses Unicode chess piece characters rendered in CSS grid cells
