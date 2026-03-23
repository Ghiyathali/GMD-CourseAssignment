# MDA #2 — Game Design Document & Milestones

## Game Overview

**Lab Escape** is an infinite runner game built in Unity 6, inspired by Subway Surfers but with an original theme and setting. The player controls a human test subject escaping from a research laboratory, being chased by a security robot. The game runs endlessly, increasing in difficulty over time, until the player either collides with an obstacle or gets caught by the robot.

The game is designed to run on PC, WebGL (hosted on GitHub Pages), and the VIA Arcade Machine at school, with full gamepad support mapped to the arcade's Xbox-style controller layout.

---

## Core Mechanics (MDA Framework)

**Mechanics:**
- 3-lane switching using left/right input
- Jumping over obstacles
- Sliding under obstacles
- Collecting blood bags (currency/score) and speed boosts (temporary acceleration)
- Procedurally spawned tiles, obstacles, and collectibles
- A robot chaser AI with a finite state machine (Chasing, Catching Up, Lunging)

**Dynamics:**
- As the player's speed increases over time, reaction time shrinks and the game becomes harder
- The robot gradually closes the gap, creating constant pressure even when the player avoids obstacles
- Speed boosts create a risk/reward moment — they help outrun the robot but make obstacles harder to dodge
- Blood bags reward players who take risks by running through contested lanes

**Aesthetics:**
- Tension and urgency from the robot chaser always being visible behind the player
- Satisfaction from clean lane switches and well-timed jumps
- A dark, clinical lab aesthetic — cold lighting, sterile corridors, industrial obstacles

---

## Theme & Setting

The player is a nameless test subject in a near-future research lab. Something has gone wrong — the facility is on lockdown and a security robot has been dispatched to stop the escape. The corridors are endless (procedurally generated), filled with lab equipment, laser barriers, and scattered blood bags left behind by previous failed escape attempts.

---

## Obstacles & Collectibles

| Object | Type | Effect |
|---|---|---|
| Lab table | Obstacle | Blocks a full lane, must jump or switch |
| Laser barrier | Obstacle | Tall barrier, must switch lane or slide |
| Blood bag | Collectible | +10 points each |
| Speed boost | Collectible | Temporary speed increase for 3 seconds |

---

## Milestones

### Milestone 1 — Core Gameplay Loop (Week 1–2)
Get the player moving, switching lanes, jumping and sliding. Build the infinite tile spawner and basic obstacle spawning. Establish the GameManager state machine and input system for both keyboard and arcade gamepad.

**Deliverables:** Working PlayerController, TileSpawner, ObstacleSpawner, GameManager, InputActions asset with keyboard and gamepad bindings.

### Milestone 2 — AI, Collectibles & Game Feel (Week 2–3)
Implement the robot chaser AI with FSM states. Add collectibles with gameplay effects. Build the ScoreManager. Wire up the full UI system including HUD, main menu, game over screen and pause menu.

**Deliverables:** RobotChaser with Chasing/CatchingUp/Lunging states, CollectibleSpawner, ScoreManager with persistent high score, UIManager with all screens functional.

### Milestone 3 — Polish, Art & Builds (Week 3–4)
Replace placeholder geometry with free Asset Store models. Add animations to the player and robot. Implement audio (background music, sound effects, alarm). Build and deploy WebGL to GitHub Pages. Package Windows build for the arcade machine.

**Deliverables:** Final art pass, animation system, AudioManager, working WebGL build on GitHub Pages, arcade-compatible Windows build.

---

## Technical Requirements Coverage

| Requirement | Implementation |
|---|---|
| Scripting | MonoBehaviours, coroutines (slide, speed boost), UnityEvents |
| Input & Vectors | New Input System, Vector3 lane movement, transform manipulation |
| Physics | Rigidbody on player, CapsuleCollider, trigger zones for collectibles |
| Graphics & Audio | Asset Store models, laser shader, AudioManager |
| Animation | Animator on player (run/jump/slide/die) and robot |
| Game Architecture | GameManager singleton, object pooling, ScriptableObjects |
| Game AI | RobotChaser FSM with three states |
| User Interface | HUD, main menu, game over screen, pause menu |
