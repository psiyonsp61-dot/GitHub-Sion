# Product Requirements Document: Dark Theme

## Summary

Add an optional dark theme to the existing browser-based Memory Game. Players
can switch between the current light appearance and a dark appearance without
interrupting a game. The selected appearance should persist between visits
where browser storage is available.

## Background

The game is implemented as a single HTML file, `memory-game.html`, with its
styles and JavaScript inline. Its current light theme uses CSS custom
properties for some colors, while several surfaces and interaction states use
hard-coded colors. The game also stores best scores in `localStorage`.

The theme feature must be kept separate from gameplay and score data so that
introducing it does not change existing game behavior or erase saved scores.

## Goals

- Offer a clear, accessible way to switch between light and dark themes.
- Apply the selected theme consistently to the page, controls, cards, score
  area, and game-completion dialog.
- Remember the player's choice across page reloads when browser storage is
  available.
- Preserve existing gameplay, responsive layout, accessibility, and best
  scores.

## Non-goals

- Redesigning the game or changing its gameplay, scoring, or animations.
- Adding additional themes beyond light and dark.
- Adding a settings page, framework, dependency, or build step.
- Automatically changing themes based on time of day or operating-system
  preference. The player controls the theme in this release.

## Target users

Players who prefer a darker interface, including those playing in dim
environments or who find a dark appearance more comfortable.

## User experience

- Add a theme toggle near the existing game controls, in a visible and
  consistent location on desktop and mobile.
- Make the control a semantic, keyboard-operable button. Its accessible name
  must communicate the action or current theme (for example, “Switch to dark
  theme” / “Switch to light theme”).
- On first visit, show the existing light theme to preserve the current
  default experience.
- Switching themes updates the page immediately and does not reset the board,
  timer, move count, rating, selected grid size, or open win dialog.
- When a saved theme preference exists, restore it on page load.
- If browser storage is unavailable, theme switching must still work for the
  current page session; gameplay must continue normally.

## Functional requirements

1. **Theme options:** Support exactly `light` and `dark` themes.
2. **Consistent styling:** Use theme-specific design tokens (such as CSS
   custom properties) for page background, primary and secondary surfaces,
   text, borders/shadows, buttons, card faces, and dialog surfaces. Avoid
   leaving fixed light-theme colors on visible elements in dark mode.
3. **Card readability:** Keep the face and back of cards visually distinct
   from each other and from the page. Preserve the existing card-flip
   animation and emoji visibility.
4. **Interactive states:** Provide distinguishable hover, focus, active, and
   selected states in both themes. Keyboard focus must remain clearly visible.
5. **Preference persistence:** Store the theme preference using a dedicated
   key that does not overlap with the existing `memoryGameScores` data. A
   missing or invalid saved value must fall back to light theme.
6. **Gameplay independence:** Changing the theme must not reinitialize or
   mutate game state, saved scores, or the selected grid size.
7. **Responsive behavior:** The toggle and themed surfaces must remain usable
   at the existing mobile and desktop breakpoints.
8. **Accessibility:** Maintain semantic controls and existing keyboard
   operation and ARIA behavior. Text and important controls must remain
   legible against their backgrounds in both themes.

## Design guidance

- Preserve the current light-theme appearance as closely as possible.
- Use a restrained dark palette with comfortable contrast rather than pure
  black for every surface.
- Keep the primary accent recognizable in both themes and ensure it is not
  the only visual indicator of button state.
- Theme all existing visible regions: page, statistics panel, grid-size
  buttons, card backs and faces, best-score list, and completion modal.

## Acceptance criteria

- [ ] A player can switch from light to dark and back using the theme button.
- [ ] The theme button can be reached and activated using the keyboard, and
      its focus indicator is visible in both themes.
- [ ] The chosen theme applies consistently to all game surfaces, including
      cards, best scores, and the completion dialog.
- [ ] Reloading the page restores the last selected theme when browser storage
      is available.
- [ ] With no saved preference, the game opens in the existing light theme.
- [ ] A missing or invalid stored theme value falls back to light without
      preventing the game from starting.
- [ ] Switching themes during an active game leaves the board, timer, moves,
      rating, and grid size unchanged.
- [ ] Existing 4x4 and 6x6 games remain playable by mouse and keyboard, and
      matching, win behavior, and play-again behavior are unchanged.
- [ ] Existing best scores still appear after the theme feature is added, and
      changing the theme does not modify or clear them.
- [ ] The layout and theme control remain usable on narrow and wide screens.

## Manual verification plan

1. Open `memory-game.html` in a browser with no saved theme preference. Confirm
   the original light appearance is shown.
2. Switch to dark mode and inspect the page, both grid sizes, card faces,
   statistics, best-score area, and completion dialog for legibility and
   consistent styling.
3. Start a game, make several moves, change the theme, and confirm the same
   cards remain revealed, the timer continues, and the move count, rating, and
   grid size are unchanged.
4. Complete a game and verify that scores are still saved and displayed.
   Switch themes and confirm the scores remain intact.
5. Reload the page and confirm the selected theme is restored.
6. Use Tab and Enter/Space to operate the theme control and game controls.
   Confirm focus remains visible in each theme.
7. Repeat at a narrow viewport and verify the controls and board remain
   usable.

## Implementation constraints

- Keep the implementation within the existing standalone `memory-game.html`
  unless implementation reveals a concrete reason to change that structure.
- Do not add external libraries, network requests, or a build requirement.
- Do not alter the format, key, or behavior of the existing best-score
  storage.

## Success measures

- All acceptance criteria pass in manual browser testing.
- No existing gameplay or score behavior regresses.
- Theme selection persists on supported browsers without being required for
  the game to function.
