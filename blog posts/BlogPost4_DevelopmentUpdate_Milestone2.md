# MDA #4 — Development Update: Milestone 2

## Milestone 2 — AI, Collectibles, UI & Audio

This post covers the second development milestone for Lab Escape: building all the systems that sit on top of the core gameplay loop. By the end of this milestone the game went from a basic running prototype to something that actually feels like a complete game — with an enemy chasing you, things to collect, a proper UI, and sound.

---

## Robot Chaser AI

The most technically interesting part of Milestone 2 was building the robot chaser AI. The robot uses a **Finite State Machine** with three states: Chasing, CatchingUp, and "stoping" the player.

In the Chasing state the robot gradually closes the distance to the player over time, creating a slow but constant pressure. If the player gets too far ahead the robot switches to CatchingUp, moving significantly faster until it closes the gap. If the robot gets very close to the player it enters the Lunging state, sprinting at full speed to try to catch them.

The robot also follows the player's lane — if the player switches left or right the robot smoothly lerps to the same X position. It also detects obstacles ahead using a raycast and jumps over them automatically, which required implementing manual gravity since the robot has no Rigidbody.

One design decision was making the robot always visible in frame rather than spawning far away. It starts 20 units behind the player and slowly closes in, so there's always a sense of danger even early in the run.

---

## Collectibles

Two collectible types were added: blood bags and speed boosts. Blood bags are the game's currency — each one collected adds 10 points to the score. Speed boosts give the player a temporary burst of speed for 3 seconds, which can help create distance from the robot but makes obstacles harder to dodge.

The CollectibleSpawner uses a Physics.OverlapSphere check before spawning to make sure collectibles don't appear inside obstacles. Collectibles spawn in a random lane with a 70/30 split between blood bags and speed boosts.

---

## Score System

The ScoreManager tracks two things: distance travelled and blood bags collected. The final score is calculated as distance plus blood bags multiplied by 10. High scores are saved between sessions using PlayerPrefs so players can try to beat their personal best.

---

## UI System

Four UI screens were built using Unity's Canvas system with TextMeshPro:

The **main menu** shows the game title and a Play button. The **HUD** displays score, distance and blood bag count in real time while playing. The **game over screen** shows the final score and personal best. The **pause menu** has Resume and Quit buttons and is triggered with the Escape key or the arcade machine's Start button.

One challenge was wiring the buttons — Unity 6 had an issue where public methods weren't showing in the button dropdown due to a compile error from the Input System. The workaround was to wire buttons through code in the UIManager's Start method using a helper function that searches for buttons by name within each panel.

---

## Audio

An AudioManager was built with two AudioSources — one for looping background music and one for sound effects using PlayOneShot. The background music uses a sci-fi track called "Glitch" from a free asset pack which fits the tense lab escape atmosphere well. Sound effects were added for jumping, collecting blood bags, speed boosts, death and button clicks.

---

## Character Model

The placeholder capsule was replaced with a proper character model from the Supercyan Character Pack Free Sample — a cartoon human character called Sam. Rather than keeping the capsule as the physics object with Sam as a child, Sam was made the main player object directly with the CapsuleCollider and Rigidbody attached to him. The PlayerAnimator script reads the player's current speed and sets the MoveSpeed parameter on Sam's Animator Controller, driving a run animation that responds to the game's increasing speed.

Robot Kyle, a free official Unity robot model, was added as the chaser visual.

---

## Challenges

The biggest challenge this milestone was getting the player model working correctly. Several issues came up including the character's built-in movement script conflicting with the New Input System, the camera not following correctly after switching to the new model, and the ground check not detecting tiles after repositioning the character. Each was solved through careful debugging of collider positions and physics settings.

The UI button wiring issue was also time-consuming but led to a cleaner solution of wiring everything through code rather than the Inspector.

---

## Current State

At the end of Milestone 2 the game has a full gameplay loop — run, dodge obstacles, collect items, get chased by a robot, and eventually die. All UI screens work correctly. Audio plays throughout. The game starts on a main menu and ends on a game over screen with score tracking. The foundation is solid for the final milestone which focuses on visual polish and builds.
