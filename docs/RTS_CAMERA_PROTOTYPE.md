# Tactical RTS controls (mouse, Space quick focus)

This mode builds on the original League-Soccer soccer simulation. It keeps the
existing human-control path, football animations, ball physics and opposition AI.

## Gameplay

Enter a match and press **F8** to switch to the top-down tactical camera.

| Input | Effect |
|---|---|
| **Space** (press) | Select and control the nearest player **on your team** to the ball, whether attacking or defending; snap the camera to that player |
| **Space** (hold) | Keep the camera centered on that newly selected player, like League of Legends; release to resume free panning |
| **Left click** | Select a team player and attach the actual keyboard controller |
| **Left drag** | Draw a green selection rectangle; select one player inside it when released (not multi-select yet) |
| **Right click grass** | Run the selected player to the clicked point using the original player movement system |
| **Arrow keys** | Directly move the selected player, overriding the current right-click move order |
| **E** | Sprint (hold) |
| **C** | Slower/controlled dribbling |
| **S** | Short pass in attack; press in defense |
| **W** | Through/long pass in attack; goalkeeper rush in defense |
| **A** | Lofted pass in attack; sliding tackle in defense |
| **D** | Shot in attack; team pressure in defense |
| **Z** | Special modifier |
| **F8** | Exit RTS mode and restore the broadcast camera |
| **I/J/K/L** | Move the RTS camera (keyboard fallback) |
| **Mouse at screen edges** | Fast camera pan |
| **Middle drag** | Fast camera pan |
| **Mouse wheel**, **+/-** | Zoom the RTS camera |

The exact pass target is still selected by the existing game logic using player
movement/input direction, context and football AI. **Mouse-pointer-directed
passing is not yet implemented.**

## Window handling and resolution

- **RTS mode confines the mouse to the game window when it has focus.** It
  prevents edge-panning from clicking the desktop or other applications.
- **F8** releases confinement. **Alt+Tab** temporarily releases confinement so
  you can work in another app. Quitting the match also releases it.
- Resolution is not fixed. The project defaults to a **1280x720 window** if
  the config is missing. In `football.config`, `context_x` and `context_y`
  specify dimensions, while `context_fullscreen` enables fullscreen. When
  changing these settings, quit the game first, then restart it.

## Clear tactical pitch

The original `media/textures/pitch/overlay.png` contains dark weathered
patches in the baked pitch texture. Because these are distracting in a distant
top-down view, the generator now leaves this decorative overlay off by default.
To restore the original look, set `rts_clear_pitch_overlay=0` in
`football.config` before launching the match. Pitch lines and gameplay
physics are still generated as before.

## Windows test

After merging the pull request:

```cmd
cd /d "C:\Users\c\Documents\League-Soccer"
git pull origin master
build.bat
run.bat
```

In a match: F8, select a player with left-click, tap Space (the circle should
jump to the nearest friendly player to the ball), hold Space to follow, release
Space and move the camera freely, then test Alt+Tab and F8 confinement release.

The Windows C++ build and in-game behavior require local testing. If MSVC
reports an error, capture the **first compiler error**.
