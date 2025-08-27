## Game Requirements (Tetris)

### Overview
A minimalist Tetris implementation contained in a single HTML file (`tetris.html`) using Canvas 2D and plain JavaScript. No build steps or external dependencies are required.

### Scope
- In scope: core Tetris gameplay loop, 7‑bag piece generation, movement, rotation, soft drop, line clears, game over overlay, canvas rendering.
- Out of scope (not currently implemented): scoring, levels/speed scaling, next/hold previews, pause, hard drop, sound, UI outside the canvas.

## Functional Requirements

### FR-1: Game Container and Rendering
- The game MUST render to an HTML `<canvas>` with size 320×640 pixels.
- The background MUST be black; the canvas MUST have a 1px white border.
- Rendering MUST use the Canvas 2D context.
- Blocks MUST be drawn at 31×31 px (1 px smaller than the grid cell) to produce a visible grid effect.

### FR-2: Coordinate System and Grid
- The logical grid size MUST be 32 px per cell (grid = 32).
- The visible playfield MUST be 10 columns by 20 rows.
- The internal playfield MUST include 2 offscreen rows above the visible area (indices -2 and -1).

### FR-3: Tetromino Definitions
- The game MUST include the standard 7 tetrominoes: I, J, L, O, S, T, Z.
- Each tetromino MUST be defined by a binary rotation matrix in `tetrominos`.
- Each tetromino MUST map to a fixed color in `colors`:
  - I: cyan
  - O: yellow
  - T: purple
  - S: green
  - Z: red
  - J: blue
  - L: orange

### FR-4: Piece Generation
- Pieces MUST be generated using a 7‑bag sequence:
  - When the queue is empty, create a random permutation of all 7 pieces and enqueue them.
  - `getNextTetromino()` MUST pop from this sequence to spawn the next piece.

### FR-5: Spawn Rules
- Spawn column MUST center the tetromino horizontally: `col = 10/2 − ceil(width/2)`.
- Spawn row MUST be:
  - I piece: row = -1
  - All other pieces: row = -2

### FR-6: Gravity and Game Loop
- The game loop MUST use `requestAnimationFrame`.
- Pieces MUST fall by 1 row every 35 frames (fixed speed).
- If moving down results in an invalid position, the piece MUST revert and be placed.

### FR-7: Input Controls
- Left Arrow (37): move piece left by 1 column if valid.
- Right Arrow (39): move piece right by 1 column if valid.
- Up Arrow (38): rotate 90° clockwise if valid.
- Down Arrow (40): soft drop by 1 row; if invalid after move, place the piece immediately.

### FR-8: Rotation
- Rotation MUST be a 90° clockwise transform of the NxN matrix.
- A rotation MUST apply only if the resulting matrix at current row/col is a valid move (no wall kicks beyond this simple validity check).

### FR-9: Collision and Validity
- A move/rotation is valid only if:
  - All occupied cells are within horizontal bounds [0..9].
  - All occupied cells are within vertical bounds (< playfield height).
  - No occupied cell overlaps an occupied playfield cell.

### FR-10: Placement and Line Clears
- On placement, occupied cells of the active piece MUST be written into the playfield.
- If any part of the placed piece lies above row 0, the game MUST end (Game Over).
- After placement, the game MUST check rows from bottom to top; any full row MUST be cleared by dropping all rows above it down by one.

### FR-11: Game Over State
- On Game Over, the loop MUST be cancelled and an overlay MUST display text "GAME OVER!" centered on the canvas.

## Non-Functional Requirements

### NFR-1: Simplicity and Packaging
- The entire game (HTML, CSS, JS) MUST reside in a single file `tetris.html`.
- The project MUST run by opening `tetris.html` directly in a modern browser.
- No external libraries, assets, or build steps are allowed.

### NFR-2: Compatibility
- The game SHOULD run on modern desktop browsers supporting Canvas 2D and standard JS features.

### NFR-3: Performance
- Rendering SHOULD clear and redraw only via `clearRect` and simple `fillRect` operations every frame.
- The fixed gravity step (every 35 frames) SHOULD keep CPU/GPU usage minimal.

### NFR-4: Maintainability
- Functions SHOULD remain small and focused (e.g., `rotate`, `isValidMove`, `placeTetromino`, `loop`).
- Piece definitions and color mappings SHOULD remain centralized in `tetrominos` and `colors`.
- Always update the 'README.md' with the latest features and gamplay options when implemented. 

## Acceptance Criteria
- Opening `tetris.html` displays a black background and bordered canvas.
- A tetromino appears and drops automatically at fixed intervals.
- Arrow keys move/rotate/drop the piece per controls; illegal moves are ignored.
- When a piece lands, it becomes part of the playfield and a new piece spawns.
- Full rows are cleared and higher rows shift down correctly.
- The game ends with a visible "GAME OVER!" overlay when a piece locks with any block above row 0.
