# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Pure static HTML/CSS/JS — no build step, no dependencies, no package manager. Each game is a single self-contained `.html` file.

Deployed via GitHub Pages at: **https://csfo-bsp.github.io/browser-games**

## Developing

Open any `.html` file directly in a browser to test. No server required (games use no external fetches).

To preview with a local server:
```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Deploying

Push to `main` — GitHub Pages rebuilds automatically (usually within ~1 minute).

```bash
git -c commit.gpgsign=false add <files>
git -c commit.gpgsign=false commit -m "..."
git push
```

> GPG signing must be disabled per the `-c commit.gpgsign=false` flag — the repo's global git config requires a signing key that isn't set up.

## Architecture

| File | Purpose |
|---|---|
| `index.html` | Landing page linking to all games |
| `football.html` | Penalty shootout game |
| `tictactoe.html` | Two-player tic tac toe |

**football.html** — DOM + CSS transitions only (no canvas). Goal is divided into 6 zones (3 cols × 2 rows). Goalie AI saves ~44% of shots by randomly picking the correct zone; otherwise dives to a random wrong zone. Ball shrinks during flight to simulate perspective.

**tictactoe.html** — Two-player local game with win detection and persistent scoreboard across rounds.
