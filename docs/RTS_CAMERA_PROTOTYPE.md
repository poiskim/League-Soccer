# RTS mouse camera and actual player control

The optional F8 tactical mode leaves the original soccer simulation and default
broadcast camera intact. This revision connects player selection to the engine's
**real HumanGamer controller**, so movement and ball animations still run through
the existing football game code.

## Mouse and keyboard

- **F8** — enter/leave the RTS tactical camera.
- **Mouse at screen edge** — pan (roughly 5x faster than the first prototype).
- **Middle mouse drag** — fast camera pan.
- **Mouse wheel** — zoom.
- **Left click on one of your team's players** — select and **control** the player.
  A yellow ring follows the player.
- **Left-click and drag** — visible green marquee box. On release, the
  closest eligible player to the rectangle's center becomes selected/controlled.
  This is **single-player box selection** for now, not multi-selection.
- **Right-click a pitch location** — selected player moves toward that location,
  using the existing HumanController movement/ball interactions.
- **Arrow keys** — manually move the selected player and cancel any queued
  right-click run order.
- **I/J/K/L** — camera pan fallback; **+/-** — zoom fallback.
- Click empty grass — retain the active player, so control never silently
  switches to an invisible player.

The old broadcast radar HUD/minimap is automatically hidden while RTS mode
is active and restored with the normal camera. The game still runs its original
opponent and teammate AI.

## Limits / known differences from the final RTS design

- One player selected at a time (multi-select to follow).
- Only the team assigned to the keyboard is selectable. If neither side is
  human-controlled, entering RTS mode assigns the keyboard to the home team.
- The camera uses overhead perspective, not orthographic projection.
- Right-click orders are basic straight-line movement without pathfinding or
  tactical formation logic; they stop when the selected player reaches the
  target or receives a manual arrow-key direction.
- Dragging **with the left button** draws the selection rectangle; dragging
  **with the middle button** moves the camera.
- Overlay and control changes have not been locally verified with Windows/MSVC.

## Windows test

Merge the PR, then from the repository directory:

```cmd
git pull origin master
build.bat
run.bat
```

In a match press F8, left-click a player and verify they respond to arrow keys.
Then right-click open grass to see the player run there. Left-drag a rectangle
over another player; release and check the yellow ring moves to the new player
and manual control switches with it. Move the mouse to the screen edge and
spin the wheel to test the faster camera. Press F8 again and check the broadcast
radar returns.

Share the **first compiler error** if the build fails.
