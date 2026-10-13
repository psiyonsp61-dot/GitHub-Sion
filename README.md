# Browser Mini-Games

This repository contains small, responsive browser games built with standalone
HTML, CSS, and JavaScript files. Open a game file directly in a modern browser
to play; no dependencies or build step are required.

## Memory Game

`memory-game.html` is a responsive and accessible Memory (Concentration) card
game.

## Features

- 4x4 and 6x6 grid options
- Smooth card flip animations
- Timer and moves counter
- Star rating system
- Local storage for best scores
- Keyboard controls for accessibility
- Responsive design for all devices
- No external dependencies

## How to Play

- Open `memory-game.html` in a web browser.
- Click or use the keyboard (Tab + Enter/Space) to flip cards.
- Find matching pairs to win, using as few moves as possible.
- Choose a 4x4 or 6x6 grid.

## Technical Details

- Pure HTML, CSS, and JavaScript with no external dependencies.
- Responsive layout using CSS Grid.
- Keyboard controls and ARIA attributes.
- Best scores saved in browser local storage.

## Tic-Tac-Toe

`tic-tac-toe.html` is a single-player game against the computer.

- You play as X and take the first turn; the computer plays as O.
- Click or keyboard-operate an empty square to make a move.
- Start a new round at any time. The current page session tracks wins and
  draws.
- The computer looks for winning moves and blocks immediate threats.
- The board is responsive and includes keyboard focus indicators and
  screen-reader status updates.

## Development

1. Clone the repository
2. Open either `memory-game.html` or `tic-tac-toe.html` in a web browser
3. Or serve the repository using a local HTTP server:
   ```bash
   python3 -m http.server 8000
   ```
4. Visit `http://localhost:8000/memory-game.html` or
   `http://localhost:8000/tic-tac-toe.html`