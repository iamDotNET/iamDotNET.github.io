---
title: "Building and designing Cloak And Coin"
description: "Designing Multiplayer Gameplay Systems in Unreal Engine 5."
pubDate: 2026-03-12
tags: ["Unreal Engine 5", "Steamworks API", "C++"]
draft: false
---

<h3>Overview</h3>

Cloak And Coin is a multiplayer medieval stealth heist game built in Unreal Engine 5. The project was developed primarily using Unreal Engine's Blueprint visual scripting system, allowing rapid iteration on gameplay mechanics while still applying software engineering principles around modularity, replication, and maintainability.

The goal was not simply to create individual gameplay features, but to build interconnected systems that could support emergent player behaviour.

The core gameplay loop revolves around:

1. Planning an approach
2. Infiltrating guarded locations
3. Managing detection risk
4. Using equipment/player loadouts creatively
5. Escaping with the stolen objective

---

## Building Systems Rather Than Features

Although Cloak And Coin was primarily developed using Blueprints, I treated the project with the same principles I would apply when writing traditional code:

- Reusable components instead of duplicated logic
- Clear ownership of responsibilities
- Data-driven configuration
- Separation between gameplay systems

Blueprints allowed me to rapidly prototype mechanics, test ideas, and iterate based on player feedback.

For a gameplay-focused project, iteration speed was critical. Being able to adjust AI behaviour, player interactions, and game flow quickly helped me refine the experience throughout development.

---

## Lessons Learned

The biggest challenge when developing Cloak And Coin was not implementing individual mechanics — it was making sure all systems worked together.

A stealth game is a combination of:

- AI behaviour
- Player interaction
- Multiplayer networking
- Game flow
- Difficulty tuning

Changing one system often affected another.

Through development, I learned the importance of building flexible systems that could evolve as the design changed.

---

###  Final Thoughts

Cloak And Coin was an opportunity to take a game idea from concept to a fully playable multiplayer experience.

The project strengthened my skills in:

Unreal Engine gameplay development
Multiplayer architecture
AI behaviour design
Rapid gameplay iteration
Building maintainable gameplay systems

The biggest lesson was that successful gameplay programming is not only about writing code, it is about designing systems that create memorable player experiences.