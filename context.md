# Repository Context

## What this project is

This repository contains a browser-based **Memory Game**, also known as
**Concentration**. It is a single-page game built with HTML, CSS, and
JavaScript. The player flips cards to find matching pairs of symbols and tries
to complete the board in as few moves as possible.

## How to play

- Open `memory-game.html` in a modern web browser.
- Choose a 4x4 board with 8 pairs or a 6x6 board with 18 pairs.
- Flip cards using a mouse or keyboard. Matching pairs stay revealed; other
  cards turn face down again.
- Complete every pair to finish the game.
- Compare your moves, elapsed time, and star rating, then play again or choose
  the other board size.

## Features

- Responsive layouts for desktop and smaller screens.
- Animated card flips and emoji symbols.
- Move counter, game timer, and a move-based star rating.
- Keyboard-operated cards and ARIA labels/live regions for accessibility.
- Best scores saved in the browser's local storage.

Scores are stored on the device and browser where the game is played; they are
not synced to an account or other devices. Clearing the browser's site data may
remove them.

## How it is built and run

The game, styles, and game logic are contained in `memory-game.html`. It uses
plain HTML, CSS Grid, and vanilla JavaScript, with no third-party libraries,
build step, or server-side component.

Open `memory-game.html` directly in a browser, or run a local server from the
repository directory:

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000/memory-game.html>.

## Repository name

The repository is named `memory-game-GHCP`, but the README and application do
not define an expansion for “GHCP.” This document does not assume what the
suffix stands for.
