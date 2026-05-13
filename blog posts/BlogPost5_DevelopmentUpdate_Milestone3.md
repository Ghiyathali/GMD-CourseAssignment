# MDA #5 — Development Update: Milestone 3

## Milestone 3 — Polish, Art & Builds

This post covers the third and final development milestone for Lab Escape: replacing placeholder art with proper assets, adding animations, and producing working builds for all three target platforms — PC, WebGL, and the VIA Arcade Machine at school.

---

## Art Pass

The biggest visual improvement this milestone was importing the Sci-Fi Styled Modular Pack, a free asset containing 202 meshes and 153 prefabs including corridor sections, floors, walls, machines, doors and decorative elements. This replaced the plain grey placeholder cubes that had been standing in for the lab environment.

The pack was originally built for the Built-in render pipeline and needed to be converted to URP. This was done using the Render Pipeline Converter tool under the Window menu, which automatically upgraded all materials to use the Universal Render Pipeline/Lit shader.

The corridor pieces from the pack were used to give the infinite runner a proper enclosed lab feel — with walls, ceiling and floor all visible as the player runs through. The obstacle prefabs were updated to use sci-fi table and machine models from the Machines folder, and the laser barrier was replaced with a more visually appropriate barrier piece.

---

## Animations

Sam's running animation was already working through the FreeAnimations Animator Controller from the Supercyan Character Pack. The PlayerAnimator script drives the MoveSpeed parameter which blends between idle and run animations based on the player's current speed. Since the FreeAnimations controller doesn't include jump or slide animations, the physical jump and slide mechanics still work correctly — the player just doesn't have a dedicated animation for those states.

Robot Kyle from the Unity free asset pack was added as the chaser visual. His animator was set up to play an idle/walk cycle while chasing the player.

---

## Audio

Background music and sound effects were fully integrated this milestone. The Sci-Fi Music Pack provided six loopable tracks, with "Glitch" selected as the background music for its tense, mechanical feel that suits the lab escape theme. The Casual Game SFX Pack provided 48 sound effects, with specific clips chosen for collectible pickup, speed boost, jumping, death and button clicks.

The AudioManager uses two separate AudioSources — one for looping music and one for one-shot sound effects — which prevents SFX from cutting off the music.

---

## Windows Build

A Windows build was produced targeting Intel 64-bit architecture at 1920x1080 fullscreen resolution. The build was tested locally to confirm the main menu, gameplay, game over screen and pause menu all function correctly.

For the VIA Arcade Machine the build folder was copied to a USB drive and transferred to the arcade desktop's Games folder. A shortcut to the .exe was placed in the Game Shortcuts folder on the desktop. The game is accessed through the GMD section of Emulation Station, which maps the arcade's physical inputs to standard Xbox controller buttons — matching the gamepad bindings set up in the PlayerInputActions asset.

---

## WebGL Build

A WebGL build was produced and deployed to GitHub Pages for browser-based access. The build was configured with the correct compression settings for web deployment and tested in a browser to confirm it runs correctly without a local Unity installation.

---

## Challenges

The main challenge this milestone was getting the sci-fi environment assets working correctly in URP. The purple/magenta material issue required using the Render Pipeline Converter rather than manually reassigning shaders, and some prefabs needed their collider layers updated to ensure the player's ground detection still worked after replacing the placeholder tiles.

Sizing the corridor pieces to match the existing tile spawner dimensions also required some adjustment — the modular corridor pieces are 4x4 units natively and needed to be scaled to fit the 12-wide by 20-long tile footprint used by the spawning system.

---

## Final State

At the end of Milestone 3 Lab Escape is a complete, playable infinite runner with a full art pass, audio, animations, working UI, and builds for all three target platforms. The game runs on PC, in the browser via GitHub Pages, and on the VIA Arcade Machine at school with full gamepad support.
