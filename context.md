# Repository Context

## What this project is

This repository contains standalone browser mini-games built with HTML, CSS,
and JavaScript. The games run directly in a modern browser without external
dependencies, a build step, or a server-side component.

## Games

### Memory Game

`memory-game.html` is a responsive Memory (Concentration) game. Choose a 4x4
board with 8 pairs or a 6x6 board with 18 pairs, then find every matching pair.
It includes animated emoji cards, a timer, move counter, star rating, keyboard
controls, and best scores saved in browser local storage. A light/dark theme
choice is also saved locally.

### Tic-Tac-Toe

`tic-tac-toe.html` is a responsive single-player Tic-Tac-Toe game. The player
goes first as X and plays against the computer as O. The computer takes
available winning moves, blocks immediate threats, and otherwise chooses a
center, corner, or open square. The current page session tracks player wins,
computer wins, and draws.

Both games use semantic browser controls and are designed to work with a
keyboard as well as a mouse.

## How to run

Open either `memory-game.html` or `tic-tac-toe.html` directly in a modern web
browser. Alternatively, start a local server from the repository directory:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/memory-game.html` or
`http://localhost:8000/tic-tac-toe.html`.

## Repository name

The repository is named `memory-game-GHCP`, but the README and applications do
not define an expansion for “GHCP.” This document does not assume what the
suffix stands for.
