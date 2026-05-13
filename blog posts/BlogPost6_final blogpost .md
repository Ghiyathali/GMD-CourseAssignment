# MDA #6 — Final Blog Post: Lab Escape

## The Finished Game

Lab Escape is an infinite runner built in Unity 6 over the course of one month as part of a game development module. The player controls a human test subject escaping from a research laboratory, running through an endless procedurally generated corridor while dodging obstacles, collecting blood bags, and staying ahead of a relentless security robot.

---

## What the Game Looks Like

The game opens on a main menu with a Play button. Once the game starts the player is immediately running forward through a sci-fi lab corridor. The camera sits behind and slightly above the player in a third-person perspective, giving a clear view of obstacles ahead and the robot chasing from behind.

The corridor is made up of modular sci-fi environment pieces that tile seamlessly as the player runs forward — walls, ceiling and floor giving the sense of an enclosed lab facility. Obstacles appear in random lane configurations, always leaving at least one lane clear so the game is never unfair. Red blood bag collectibles and yellow speed boost collectibles appear throughout, rewarding players who take risks.

The robot chaser is always visible in the background, gradually closing the gap. As the player's speed increases over time the game becomes progressively harder, and a well-timed speed boost can create valuable breathing room.

---

## How All Requirements Were Met

**Scripting** — The project uses MonoBehaviours throughout, with coroutines for the slide mechanic and speed boost timer, and UnityEvents in the GameManager to notify other systems of state changes without tight coupling.

**Input & Vectors** — The New Input System handles all input with separate bindings for keyboard, gamepad and the VIA Arcade Machine. Lane switching uses Vector3 lerping for smooth movement, and all forward motion is handled through Rigidbody velocity.

**Physics** — The player has a Rigidbody and CapsuleCollider. Obstacles use trigger detection for collectibles and collision detection for obstacles. A ground check sphere detects whether the player is grounded for jump logic.

**Graphics & Audio** — Free Asset Store models were used for the player character (Supercyan Character Pack), the robot chaser (Robot Kyle), and the lab environment (Sci-Fi Styled Modular Pack). An AudioManager handles looping background music and one-shot sound effects for all game events.

**Animation** — The player character uses an Animator Controller with a MoveSpeed float parameter that drives blend between idle and run animations. A PlayerAnimator script feeds the current player speed into the animator each frame.

**Game Architecture** — A GameManager singleton manages all game states (Menu, Playing, Paused, GameOver) and broadcasts state changes via UnityEvents. Object pooling is used for tile spawning to avoid runtime instantiation overhead. A ScoreManager singleton tracks distance and collectibles with persistent high scores via PlayerPrefs.

**Game AI** — The robot chaser uses a three-state Finite State Machine: Chasing (slowly closing the gap), CatchingUp (aggressively closing when the player gets too far), and Lunging (sprinting at full speed when very close). The robot also follows the player's lane position and uses raycasts to detect and jump over obstacles.

**User Interface** — A full UI system was built with four screens: main menu, HUD (live score, distance, blood bag count), game over screen (final score, personal best), and pause menu. All screens respond correctly to game state changes.

---

## Platform Support

The game runs on three platforms:

**PC (Windows)** — A standalone .exe build at 1920x1080 fullscreen. Controlled with keyboard (WASD/arrow keys, Space, S).

**WebGL** — Hosted on GitHub Pages for browser-based play with no installation required.

**VIA Arcade Machine** — The Windows build is deployed through Emulation Station which maps the arcade's physical controls to Xbox controller inputs, matching the gamepad bindings in the PlayerInputActions asset. Left stick switches lanes, Button North jumps, Button South slides, and Start pauses.

---

## Reflections

This project was a significant step up from Roll-a-Ball in terms of complexity. Managing multiple interconnected systems — spawning, AI, input, UI, audio — required careful architecture decisions early on, particularly around the GameManager event system which made it possible to add new systems without modifying existing ones.

The biggest technical challenges were getting the player model working correctly with the physics system, and resolving Unity 6 compatibility issues with Cinemachine 3.x and the New Input System. Both required adapting approaches that work differently in Unity 6 compared to older versions covered in most online tutorials.

The most satisfying part was seeing the robot AI come together — watching it chase, catch up when the player slows down, and lunge at the right moment made the game feel genuinely tense in a way that placeholder geometry never could.

---

## What I Would Do Differently

With more time I would add jump and slide animations to the player character, add more obstacle variety, implement a proper high score leaderboard, and polish the UI with custom fonts and visual effects. I would also look at adding environmental variety to the corridor — different room types, lighting changes, and hazards — to keep longer runs visually interesting.

Overall Lab Escape meets all the brief requirements and is a complete, playable game across all three target platforms.
