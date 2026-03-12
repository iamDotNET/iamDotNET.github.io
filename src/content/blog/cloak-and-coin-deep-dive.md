---
title: "Building and Designing Cloak And Coin"
description: "A deep dive into the systems, architecture, and technical decisions behind Cloak And Coin."
pubDate: 2026-03-12
tags: ["Unreal Engine 5", "Steamworks API", "C++"]
draft: false
---

<h3>Overview</h3>

Cloak And Coin is a multiplayer stealth heisting game built in Unreal Engine 5 where up to four players infiltrate locations, steal valuables, and escape before the guards catch them.

Because I'm developing the game solo, every system had to follow a simple rule: **be technically robust but mechanically simple**. If something required a complex AI framework or an overly heavy networking system, it probably wasn't the right approach for the game.

This post walks through the core systems that power Cloak And Coin, including multiplayer networking, enemy AI, interaction systems, and progression.

---

## Multiplayer Architecture

Multiplayer was one of the first systems I tackled because the entire game is designed around cooperative heists.

Instead of building a dedicated server architecture, I chose to use Steam's **P2P networking via the Steamworks API**, integrated through the **Advanced Sessions plugin** in Unreal Engine.

This allowed me to:

- Support drop-in co-op for up to 4 players
- Avoid running and maintaining dedicated servers
- Use Steam matchmaking and lobbies
- Sync progression through Steam Cloud saves

In practice, the flow works like this:

1. A player hosts a lobby through Steam.
2. Friends join through the Steam overlay or invite system.
3. The host acts as the listen server.
4. The game uses **server travel** to move all players into the selected contract.

Because server travel can cause loading issues in multiplayer, I implemented a **custom loading screen system that persists across travel**. This ensures players don't see the default Unreal loading hitch when transitioning between contracts.

---

## Designing Simple but Effective Enemy AI

Enemy AI in *Cloak And Coin* intentionally avoids complicated behaviour trees or heavy perception systems.

Instead, enemies rely on a **very simple skeleton AI**:

- Pawn Sensing for player detection
- Line-of-sight checks
- State-based behaviour

Each enemy generally operates in a few core states:

- Patrol
- Suspicious
- Chase
- Capture

For example, guards patrol predefined routes until they detect a player. Once a player enters their sensing radius and line of sight is confirmed, they transition into a **chase state**.

If the guard catches the player, the player is **sent to prison**, where teammates must rescue them using prison keys.

Keeping this system simple makes it easy to introduce new enemy types without rewriting core logic.

### Civilians

- Detect players quickly
- Alert guards
- Despawn after reporting the player

### Shapeshifters

- Rogue-like enemies that stalk players
- Attempt to capture players silently
- Can be stunned using thrown items like the shovel

All enemies use the same core sensing and pursuit logic, which keeps the AI predictable and maintainable.

---

## Interaction System

Almost everything in *Cloak And Coin* can be interacted with, loot, keys, doors, safes, and NPCs.

To keep interactions responsive and multiplayer-friendly, I built a **line of sight driven interaction system**.

Each interactable object contains a range that players can interact with at:

1. Detects when the player enters range
2. Displays an interaction widget above the object
3. Allows the player to interact via a key press

The interaction prompt is handled through **UI widgets attached to actors in the world**.

One challenge I ran into was ensuring interactions updated correctly when players quickly moved in and out of collision ranges, especially in multiplayer sessions.

To solve this I added a **force refresh event** that re-checks active interactions whenever overlap events fire. This keeps the UI consistent even with network latency.

---

## Item System

Items in *Cloak And Coin* are intentionally simple but versatile.

Every item in the game shares one core mechanic: **it can be thrown.**

This single rule allows items to serve multiple purposes without introducing complicated systems.

### Shovel

- Used as a melee weapon
- Can be thrown to stun enemies

### Dynamite

- Blows open safes and locked doors
- Alerts nearby guards

### Vault Key

- Required to open the main vault in a level
- Spawns randomly to encourage exploration

Because items share a unified throwable system, adding new items to the game is straightforward.

---

## Procedural Elements

While levels are handcrafted, many elements are **randomised each run** to keep contracts fresh.

These include:

- Key spawn locations
- Loot placement
- Certain objective items

This approach strikes a balance between **designed spaces** and **replayability**, ensuring players can learn a map while still needing to adapt during each contract.

---

## Career Mode and Progression

Beyond individual heists, the game features a **Career Mode** where players build their reputation as thieves.

Contracts are presented through a **contract board**, which periodically re-rolls available jobs. Each contract includes:

- A location
- Objectives
- Difficulty modifiers
- Rewards

Players earn currency from successful heists which can unlock:

- New contracts
- Gameplay modifiers
- Additional progression systems

Save data is synced through **Steam Cloud**, ensuring player progress persists across devices.

---

## Final Thoughts

Building *Cloak And Coin* as a solo developer meant every system had to be designed with **simplicity, flexibility, and maintainability** in mind.

Rather than building large complex systems, I focused on creating **small systems that work well together**:

- Simple AI that supports multiple enemy types
- A unified throwable item system
- Lightweight Steam-based multiplayer
- Randomised elements layered on handcrafted levels

This approach has allowed the game to grow steadily without becoming technically overwhelming to maintain.

And of course… there are still plenty more heists to build.