# MDA #3 — Development Update: Milestone 1

## Milestone 1 — Core Gameplay Loop

This post covers the first development milestone for Lab Escape: getting the core gameplay loop up and running. The goal was to have a player that moves, reacts to input, and runs through a procedurally generated corridor — basically making it feel like a runner game before adding any of the extra systems on top.

---

## What Got Built

### Project Setup
The project was set up in Unity 6 using the Universal 3D template. Folder structure was established early to keep scripts, prefabs, audio, and assets organised. Two key packages were installed from the Package Manager: the New Input System for handling keyboard and gamepad input, and Cinemachine for the third-person camera.

### GameManager
The GameManager was the first script written. It uses a singleton pattern so any script in the project can access it globally without needing a scene reference. It manages four game states — Menu, Playing, Paused, and GameOver — and uses UnityEvents to notify other systems when the state changes. This made it easy to hook up the UI later without tight coupling between systems.

### PlayerController
This was the most complex part of Milestone 1. The player needed to do four things: run forward automatically, switch between three lanes smoothly, jump, and slide. 

Running forward is handled through a Rigidbody in FixedUpdate, which keeps it in sync with Unity's physics system. Lane switching uses a target X position that the player lerps toward each frame, giving a smooth sliding feel rather than snapping. Jumping applies an upward velocity to the Rigidbody and uses a ground check sphere to prevent double jumps. Sliding shrinks the CapsuleCollider for the duration of the slide so the player can fit under obstacles, then restores it using a coroutine.

One issue that came up early was the player running in the wrong direction — everything was spawning behind the camera. This was fixed by negating the Z velocity so the player runs in the negative Z direction, and updating all spawner scripts to match.

### Input System
The New Input System was used instead of the legacy Input Manager. A PlayerInputActions asset was created with four actions — MoveLeft, MoveRight, Jump, and Slide. Each action has multiple bindings: keyboard keys (WASD and arrow keys) and gamepad bindings that map to the VIA Arcade Machine's Xbox-style controller layout. The arcade machine runs through Emulation Station which maps its physical inputs to standard gamepad buttons, so Button South maps to jump, Button North to slide, and Left Stick horizontal to lane switching.

### Cinemachine Camera
A third-person camera was set up using Cinemachine 3.x, which works differently from older versions. In Unity 6, position and rotation control are added as Procedural Components rather than being built into the camera directly. The Third Person Follow component handles the camera offset and damping, while the Rotation Composer keeps the camera locked onto the player.

### Tile Spawner
The infinite corridor is built using an object pooling system. Ten tiles are pre-spawned at the start, and as the player moves forward, tiles behind the player are deactivated and repositioned ahead. This avoids the performance cost of constantly instantiating and destroying GameObjects. The tile length and count are exposed in the Inspector so they can be tuned easily.

### Obstacle Spawner
Lab tables and laser barriers spawn ahead of the player at randomised lane positions. The spawner ensures at least one lane is always clear so the game is never unwinnable. Spawn interval decreases over time, making the game progressively harder as the player survives longer.

---

## Challenges

The biggest challenge was getting the player direction and spawner directions consistent. Because Unity's Z axis runs both forward and backward, it took a few iterations to make sure the player, tiles, obstacles, and collectibles were all aligned in the same direction.

Getting the Cinemachine camera set up in Unity 6 also took longer than expected since the component layout changed significantly from older versions and most online tutorials cover the older API.

---

## Current State

At the end of Milestone 1 the game has a player that runs forward with increasing speed, switches lanes, jumps and slides, collides with obstacles, and has an infinite procedurally generated corridor. The input system works on both keyboard and gamepad. The GameManager correctly tracks game state and the foundation is solid for building the AI and UI systems in Milestone 2.
