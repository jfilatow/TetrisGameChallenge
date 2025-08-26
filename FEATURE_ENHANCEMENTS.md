## Feature Enhancements (TetrisJS)

This document proposes enhancements that preserve the project’s simplicity (single-file gameplay, no build step) while enriching the experience. Each enhancement is optional and can be implemented incrementally.

### 1) Visual and Audio Enhancements
- High‑fidelity assets: add an `assets/` folder for optional images and audio (e.g., backgrounds, block textures, icons, SFX, music).
- Dynamic/Themeable backgrounds: static images or subtle animations that do not impact gameplay logic. Allow easy theme switching.
- Subtle block styling: simple gradients or outlines to improve readability without complicating rendering.
- Sound effects: move/rotate/lock/line‑clear SFX; lightweight background music with mute toggle.

### 2) Core Gameplay Improvements
- Hard drop: instant drop to lowest valid position, awarding minimal landing feedback (no scoring yet).
- Delayed Auto Shift (DAS) feel: basic key repeat for left/right while held, tuned for simplicity.
- Wall‑kick tweaks: simple kick attempts for rotation near walls to reduce frustrating invalid rotations.
- Soft drop tuning: optionally accelerate more than 1 row per frame when key held (configurable).

### 3) Progression and Feedback (Lightweight)
- Basic scoring: points for line clears and soft/hard drops; keep logic minimal and isolated.
- Levels: increase fall speed after a number of lines; retain the fixed‑tick fallback for simplicity.
- Minimal HUD overlay: unobtrusive text for score, level, lines, next piece.
- Pause/Resume: a single key to pause the loop and show a small overlay.

### 4) New Modes (Simple Variants)
- Time Attack: clear N lines under a countdown timer; show remaining time and lines.
- Survival: periodic speed‑ups at fixed intervals; ends on game over.
- Practice: infinite bag and no game over; useful for testing rotation/movement.

### 5) Input and Accessibility
- Customizable key bindings: map left/right/rotate/drop/pause via a small config section.
- Colorblind‑friendly palettes: alternate `colors` mapping toggle.
- Adjustable speed: expose gravity step (frames per drop) as a simple setting.
- Reduced motion: disable animated backgrounds and flashy effects via a flag.

### 6) UI/UX Polishing
- Start/Restart prompts: lightweight overlay to start a new game and to restart after game over.
- Next/Hold: show next piece preview; optional simple Hold slot with a one‑swap rule.
- Simple settings modal: minimal, in‑canvas or adjacent DOM controls to toggle features.
- Responsive layout: keep canvas centered; optional scale‑to‑fit while preserving aspect ratio.

### 7) Data and Community (Optional, Minimal)
- Local persistence: store best score, settings, and last used theme in `localStorage`.
- Lightweight leaderboard: if added later, a simple POST to a small backend or serverless endpoint; keep the client logic optional.

### 8) Developer Experience
- Config block: a small JSON‑like object at the top of the script controlling toggles (audio on/off, theme, gravity, DAS repeat, etc.).
- Modularization (optional): keep single‑file build, but group code into clear sections or small inline modules to aid readability.
- Debug overlay: toggle to show FPS, drop interval, and piece state for testing.

### Asset Organization (If Used)
```
assets/
  backgrounds/
    classic.png
    neon.png
  audio/
    move.wav
    rotate.wav
    lock.wav
    line_clear.wav
    theme.mp3
  blocks/
    block_cyan.png
    block_yellow.png
    ...
```

### Implementation Notes
- Keep all enhancements off by default; enable via config flags to maintain minimal core.
- Prefer simple fallbacks (e.g., solid colors when textures disabled, silence when audio disabled).
- Avoid introducing build tooling; use modern browser APIs only.
- Ensure any added DOM remains lightweight and does not interfere with canvas input/rendering.
