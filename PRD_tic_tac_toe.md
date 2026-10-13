# Product Requirements Document: Tic-Tac-Toe

## Summary

Provide a lightweight, single-player Tic-Tac-Toe game that runs directly in a
modern web browser from one standalone HTML file. The player uses X and moves
first; the computer uses O. The game tracks round results while the page stays
open.

## Background

This repository contains small browser games implemented without frameworks,
external libraries, or a build step. The Tic-Tac-Toe experience should follow
that approach and remain independent of the existing Memory Game.

## Goals

- Let one person play complete Tic-Tac-Toe rounds against the computer.
- Make game state, whose turn it is, and round results clear.
- Support mouse, keyboard, and assistive technology.
- Work on narrow and wide screens without installation or network access.

## Non-goals

- Local or online multiplayer.
- Difficulty selection or a perfect-play/minimax computer opponent.
- Persistent scores across reloads or browser sessions.
- Themes, sound, accounts, analytics, or external assets.
- Changes to Memory Game behavior.

## Target user

Someone who wants to play a familiar, quick Tic-Tac-Toe game in a browser,
including on a keyboard or small-screen device.

## Game rules

- The human player is X and takes the first turn of each round.
- The computer is O.
- Players alternate turns by marking an empty square.
- The first player to make a horizontal, vertical, or diagonal line of three
  marks wins.
- A round with all nine squares filled and no winning line is a draw.
- Once a round ends, no more squares can be played until a new round begins.

## User experience

- Present a clear 3-by-3 board, a short instruction, current-turn/result status,
  player/computer/draw counters, and a **New game** control.
- A human-selected empty square becomes X immediately. The computer makes its
  response after a brief pause so that the turn change is perceptible.
- Disable unavailable cells during the computer turn and once the round ends.
- Visually highlight the three winning squares.
- **New game** clears the current board and starts a fresh round without
  resetting the session score.
- The opening player remains X after every restart.

## Functional requirements

1. **Valid moves:** Only an empty square can be marked. A square cannot be
   selected again after it has a mark.
2. **Turn order:** The player always moves first as X. After a valid player
   move that does not end the round, the computer plays O.
3. **Computer move policy:** The computer first takes an available move that
   wins immediately. If none exists, it blocks an immediate player win. If
   neither applies, it chooses the center when open, otherwise a random open
   corner, otherwise a random remaining open square.
4. **Round completion:** Detect X wins, O wins, and draws. Announce the result,
   highlight winning cells when applicable, and prevent further moves.
5. **Session score:** Track player wins, computer wins, and draws in page
   memory. Update exactly one counter per completed round. Scores reset when
   the page is reloaded.
6. **Restart:** Starting a new round cancels any pending computer move,
   clears board marks and highlights, restores the initial status, and leaves
   the session counters unchanged.
7. **Accessible controls:** Use real buttons for board cells and restart.
   Cells must have accessible names describing their row, column, and current
   contents. Announce turn and result updates through a live status region.
8. **Responsive layout:** Keep the board square, legible, and usable on narrow
   viewports as well as desktop.
9. **Standalone delivery:** Keep markup, styles, and game logic in
   `tic-tac-toe.html`; require no external packages, resources, server, or
   build step.

## Design and interaction guidance

- Use a friendly, uncluttered visual style that distinguishes X and O using
  both color and their letter marks.
- Provide visible keyboard-focus indicators and clear hover/disabled states.
- Respect the user's reduced-motion preference.
- Keep board geometry stable as moves are made; do not rely on color alone to
  communicate a win.

## Acceptance criteria

- [ ] Opening `tic-tac-toe.html` directly in a browser shows a playable empty
      board with X identified as the player's mark and first turn.
- [ ] Clicking an empty cell or activating it by keyboard marks it X once.
- [ ] The computer makes one O move after a valid player move, and unavailable
      cells cannot be changed.
- [ ] When an immediate O win is available, the computer takes it.
- [ ] When X has an immediate winning threat and O cannot win immediately, the
      computer blocks that threat.
- [ ] Otherwise, the computer follows the documented center/corner/open-square
      move policy.
- [ ] Each possible winning line orientation is recognized; winning cells are
      highlighted and the correct score counter increases exactly once.
- [ ] A full board with no winning line is announced as a draw and increments
      the draw counter exactly once.
- [ ] No move is accepted after a round ends.
- [ ] Starting a new round, including during the computer's delay, clears the
      board and cancels the pending turn while preserving session scores.
- [ ] Cell accessible names expose row, column, and mark/empty state; status
      and result changes are announced to assistive technology.
- [ ] The game remains usable at narrow and desktop viewport widths and honors
      reduced-motion settings.
- [ ] The existing Memory Game continues to work independently.

## Manual verification plan

1. Open `tic-tac-toe.html` directly in a browser and check the initial status,
   all nine empty cells, and zeroed score counters.
2. Use a mouse and then keyboard to place X. Confirm the status changes while
   the computer thinks, then returns to the player's turn after O appears.
3. Create an X immediate-win threat and verify the computer blocks it. Create
   an available O winning move in a test game state and verify it is taken.
4. Play to a player win, a computer win, and a draw. Verify the right status,
   highlight, and single counter increment for each result.
5. Try to activate occupied and completed-round cells; confirm the board
   rejects those moves.
6. Start a new round during the computer delay and after a completed round.
   Confirm no delayed O appears after restart and that scores remain.
7. Navigate and play using keyboard controls; inspect accessible cell names
   and live status announcements.
8. Repeat at a narrow viewport and with reduced motion enabled.
9. Open `memory-game.html` and confirm it remains unaffected.

## Success measures

- Every acceptance criterion passes in browser verification.
- Complete rounds resolve once with correct board state and score.
- The game is usable with keyboard and assistive technology.
- It remains a standalone browser file with no external runtime dependencies.
