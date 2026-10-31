# RTS mouse camera and player selection prototype

This is an **opt-in** mouse-driven camera/selection layer above the existing match.
The 22-player simulation, AI, football physics, keyboard controls, and normal
broadcast camera remain intact.

## Controls during a live match

1. Press **F8** once to enable the tactical overhead camera. F8 again returns
   to the original broadcast camera.
2. Move the mouse pointer to any **screen edge** to pan across the pitch.
3. Turn the **mouse wheel** to zoom in or out.
4. Hold the **middle mouse button** and drag to move the camera directly.
5. **Left-click a player on the home team** to select that player.
   A **yellow ring at the player's feet** follows the selected player.
   Click empty grass to clear the selection.
6. **I/J/K/L** panning and **+/-** zoom still work as keyboard fallbacks.

## Important current limitations

- Single-player selection only; box selection and right-click movement orders
  have **not** been implemented yet.
- Only the **home team (team 0)** can be selected in this prototype.
- Selection changes the marker, not who is controlled by the match AI.
- The camera is a straight-down **perspective** view, not orthographic yet.
- The selection ring uses the project's pre-existing yellow large debug-circle
  geometry (no new binary assets).
- The screen-edge region is 25 px; wheel zoom has height bounds to prevent
  clipping. Selection uses rendered player positions with a 34 px hit radius.

## Windows testing

From a terminal opened at the repository root:

```cmd
build.bat
run.bat
```

During a match: press F8, move the pointer to a screen edge, scroll the wheel,
middle-drag, then left-click a home player. Check that the ring follows the
player and disappears when empty grass is clicked. Press F8 again to restore
the normal broadcast view.

**Windows C++ build and in-game rendering have not been tested by the assistant.**
If you get a compiler error, share the first error and surrounding lines.

## Next work

- Drag rectangle and multi-player selection.
- Right-click movement commands integrated with the existing controller/AI path.
- Better selection UI and camera angle/orientation options.
