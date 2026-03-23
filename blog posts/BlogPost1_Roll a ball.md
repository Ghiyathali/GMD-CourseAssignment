# Roll-a-Ball – Project Blog

## 1. Project Overview (Roll-a-Ball)
Roll-a-Ball is a simple 3D Unity game where the player controls a ball and must collect a set of collectible objects while avoiding an enemy. The objective of the game is to collect all collectibles before being caught by the enemy. If the enemy touches the player, the game is lost.

The purpose of this project was to learn the basics of game development in Unity, including scene setup, physics, scripting in C#, prefabs, collision detection, and simple AI behavior.

---

## 2. Project Setup & Game Design Document

### Project Setup
The project was created using Unity Hub. A new project was started using the **Universal 3D (URP)** template. The project was named **Rollaball**, and a new scene was created using the **Basic URP** scene template.

A Plane GameObject was added to the scene to act as the ground. The plane was renamed to **Ground**, its transform was reset to position (0, 0, 0), and it was framed properly in the Scene view. This provided a base surface for gameplay.

All scripting in the project was done using **C#**.

---

### Game Design

- **Genre:** Casual / Arcade  
- **Platform:** PC (Windows) / Web (WebGL)  
- **Perspective:** Third-person  
- **Player Goal:** Collect all collectibles before the enemy catches the player  

### Core Mechanics
- Physics-based player movement
- Collectible objects using collision detection
- Enemy AI that chases the player
- Win and lose conditions

### Controls
- **WASD / Arrow Keys:** Move the ball

### Win & Lose Conditions
- **Win:** Collect all 13 collectible cubes
- **Lose:** Enemy collides with the player ball

---

## 3. Development – Milestone 1: Player Movement & Physics
The first development milestone focused on creating the player and implementing movement. The player is represented by a ball GameObject with a Rigidbody component, allowing it to respond to physics and gravity.

Movement was implemented using C# scripting, applying forces to the Rigidbody so the ball rolls naturally across the ground. This milestone helped establish the core interaction of the game.

### What I Learned
- How Rigidbody physics works in Unity
- How gravity and forces affect GameObjects
- How to control a player using keyboard input

---

## 4. Development – Milestone 2: Collectibles, Prefabs & Obstacles
In the second milestone, collectible objects were added. A total of **13 yellow cube collectibles** were created. These cubes use collision detection so that when the player ball touches them, they are collected.

Prefabs were introduced at this stage. The collectible cube was turned into a prefab, allowing changes to one cube to automatically apply to all collectible cubes. This made managing multiple objects much easier.

Obstacles were also added to the level. Five cube obstacles were created, their shapes slightly modified, and scattered across the map to increase difficulty and challenge the player’s movement.

### What I Learned
- How to create and use prefabs
- How collision detection works
- How to design a simple level layout using obstacles

---

## 5. Development – Milestone 3: Enemy AI & Game Logic
The final development milestone focused on adding an enemy and implementing game logic. An AI-controlled enemy was created that constantly chases the player’s position.

The enemy uses simple logic to move toward the player. If the enemy collides with the player ball, the game ends and the player loses. This added tension and made the game more engaging.

The win condition was also implemented so that when all 13 collectibles are collected, the player wins the game.

### Challenges
One challenge was balancing the enemy speed so that the game felt challenging but still fair. This required testing and adjusting values through trial and error.

---

## 6. Final Result & Conclusion
The final version of Roll-a-Ball includes player movement, physics-based gameplay, collectibles, obstacles, an enemy AI, and clear win and lose conditions. The game successfully demonstrates the core concepts of Unity game development.

Through this project, I learned how to:
- Set up a Unity project and scene
- Use physics and gravity in gameplay
- Write C# scripts for player control and collisions
- Create and manage prefabs
- Implement simple AI behavior
- Structure a game using milestones

### Future Improvements
If more time were available, additional features such as sound effects, multiple levels, improved enemy behavior, and a restart menu could be added.

### Play the Game
https://ghiyathali.github.io/Roll-a-ball-/ 
