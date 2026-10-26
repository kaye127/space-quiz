# Copilot instructions

## Project structure and commands

The app is a single-file, standalone web page in `index.html`. Its HTML, CSS, quiz data, and JavaScript behavior are all inline; it runs directly in a browser without a server or dependencies. There are no build, test, or lint commands configured in the repository.

## Architecture

- The HTML defines the quiz and results views, progress and score indicators, answer group, feedback, and live announcement region.
- The inline stylesheet owns the visual system and responsive behavior. CSS custom properties define light/dark palettes, with `prefers-color-scheme` and `prefers-reduced-motion` handling.
- The inline script is an IIFE. The `questions` array is the source of quiz content; `renderQuestion`, `selectAnswer`, and `showResults` update the DOM and manage the quiz lifecycle.
- Quiz state (`currentQuestion`, `score`, and `answered`) is held in the script. The results view is shown after the last answer and can reset the state for a replay.

## Codebase conventions

- Keep the app self-contained in `index.html`; do not add a framework, runtime dependency, or server requirement.
- Add quiz content as objects in `questions`, using the existing `question`, `answers`, `correct`, and `fact` fields. `correct` is the zero-based index into `answers`.
- Build answer controls with native buttons and update dynamic content through DOM APIs. Preserve keyboard focus transitions, accessible names/live announcements, and progress-bar ARIA values when changing quiz flow.
- Keep styles consistent with the existing CSS custom properties and responsive/dark-mode patterns. Honor reduced-motion preferences for animations.
