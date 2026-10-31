# Experimental RTS Camera (first prototype)

This optional camera mode is a first step toward mouse-driven tactical soccer
controls. It reuses the existing match renderer and does **not** replace the
underlying 22-player simulation, controller system, or football physics.

## Controls (during a live match)

- **F8**: toggle the overhead camera on/off.
- **I / J / K / L**: pan up / left / down / right while the overhead view is on.
- **= / numpad +**: zoom in.
- **- / numpad -**: zoom out.

The original match broadcast camera remains the default. IJKL intentionally
avoid the game's existing arrow-key player movement controls. The view is
perspective from straight above, **not yet true orthographic**.

## Windows test

1. Build using `build.bat` from the repository root.
2. Start the game using `run.bat` and open a match.
3. After the brief match-intro camera animation, press F8.
4. Pan with IJKL, zoom with +/- and press F8 to return to the standard camera.

## Next development phases

- Edge-of-screen mouse panning and mouse-wheel zoom.
- Left-click single-player selection and drag-box multi-selection.
- Right-click move orders while preserving each player's animation and ball interaction.
- Tactics and queueing orders for multiple players.

This prototype has not been verified in a local Windows build; if MSVC reports
an error, retain the last console messages to make the fix precise.
