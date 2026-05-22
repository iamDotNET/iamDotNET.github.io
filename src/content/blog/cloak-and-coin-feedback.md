---
title: "Gathering player feedback"
description: "Looking into trending data and adjusting gameplay based on player feedback."
pubDate: 2026-05-22
tags: ["Unreal Engine 5", "C++", "Game Analytics"]
draft: false
---

<h3>Overview</h3>
Cloak And Coin has been publicly available on Steam for over 5 months and during that time I've spent a lot of time gathering player feedback through both Steam and Discord to better understand what players enjoy, what frustrates them, and where players were getting stuck entirely.

---

As a solo developer it's very easy to become tunnel visioned on your own ideas. You spend months building mechanics and systems, eventually reaching a point where you know every corner of your own game. What seems obvious to you as the developer can feel completely unintuitive to a brand new player.

One of the most valuable things I've learned throughout Early Access is that player feedback is not just useful for bug fixing, it's one of the most important tools available for shaping gameplay and long-term progression.

## Gathering crucial player feedback

In my experience so far, your own ideas and instincts are amazing tools for shaping your game, but without proper player feedback it's incredibly easy to spend weeks or even months going down the wrong path.

Since launching into Early Access I've actively encouraged players to leave feedback wherever possible. I even added direct UMG widgets in-game prompting players to join the Discord community and leave feedback after completing contracts.

Some of the best feedback I received wasn't from veteran players, but from completely new players who had never really played stealth or heisting games before. Watching how those players approached mechanics was incredibly eye opening.

To help support this, I integrated GameAnalytics into the game in order to track:
- What kits (equipment) players were using
- Which levels players were successfully completing
- What difficulties players were actually selecting
- Where players were failing contracts most often

Analytics gave me the raw numbers, while Discord and Steam discussions gave me the reasoning behind those numbers putting both together painted a much clearer picture.

---

## Into the analytics

One of the biggest surprises early on was seeing how many new players struggled even on the lower difficulties.

Players who joined the Discord community generally adapted much faster because they engaged with other players, learned mechanics more quickly, and asked questions when something confused them.

Players outside of the community however often struggled in silence. Analytics showed that many players were failing contracts very early into Career Mode or avoiding certain mechanics entirely.

Without analytics I probably would have assumed those players simply stopped playing.

Instead, the data showed me exactly where players were struggling.

Thanks to a handful of very active community members I also gained really valuable insight into the differences between how new players and experienced stealth players approached the game.

That feedback ended up heavily shaping how difficulty balancing evolved over the following updates.

---

## New players

New players, especially players completely new to stealth or heisting games, struggled a lot with Cloak And Coin's Curse system.

Curses are gameplay modifiers that introduce additional threats or restrictions during contracts. The issue wasn't necessarily that the curses were unfair, but that newer players were encountering mechanics they had not properly learned or been introduced to beforehand.

As developers it's very easy to accidentally design around your own experience level.

After hundreds of hours testing the game myself I already understood:
- Guard pathing
- Stealth timing
- Risk vs reward
- Which kits countered specific threats

New players obviously did not.

Working directly with newer players helped me rebalance lower difficulties like Easy and Medium to better ease players into the game's systems.

Some of the changes included:
- Reducing the frequency of more punishing curses
- Restricting certain curse types from appearing in lower difficulties
- Improving loot quality on lower difficulties
- Allowing newer players more opportunities to recover from mistakes
- Adjusting early progression pacing

These changes ended up having a noticeable positive impact on retention and progression. Players were sticking around longer, completing more contracts, and eventually progressing further into Career Mode rather than bouncing off during the early hours.

---

## Veteran heisters

Interestingly, the opposite problem existed for experienced stealth players.

Players coming from games like:
- PayDay 2/3
- Dishonored
- Thief

were having a much easier time on earlier difficulties.

A lot of veteran players were breezing through Easy and Medium without much resistance, with some early feedback even suggesting that the game felt too forgiving.

Balancing for both new and experienced players became one of the biggest design challenges during Early Access.

To help support both styles of play I focused heavily on separating difficulty identity.

Easy and Medium became more tailored towards newer players by:
- Increasing opportunities for higher-tier loot
- Reducing overly punishing curse combinations
- Introduced enemy AI scaling, like reducing line of sight and response times for Guards
- Allowing players more room for experimentation

Meanwhile Hard and Elite became focused on introducing restrictions and modifiers that forced players to adapt their strategies.

This included adding new curses and tweaking curse logic such as:
- **Reinforced Doors** — preventing players from brute forcing entries with Dynamite or Lock Melters
- **Reduced Stun Time** — making crowd-control kits significantly less effective
- Expanded curse pools on higher difficulties
- Increased chances of multiple curses appearing simultaneously

The goal wasn't simply to make enemies stronger or increase numbers, but to force players to approach contracts differently depending on the active modifiers.

That distinction ended up making the higher difficulties feel much more deliberate rather than simply frustrating.

---

## Final thoughts

One of the biggest lessons I've learned throughout development is that player feedback is most valuable when combined with actual gameplay data.

Players are very good at explaining how something feels.

Analytics are very good at explaining what players are actually doing.

The best balancing decisions usually happen somewhere in the middle of those two things.

I still regularly monitor Discord discussions, Steam feedback, completion rates, and gameplay analytics whenever designing new mechanics or updating existing systems.

A lot of systems inside Cloak And Coin today probably would not exist in their current form without that constant feedback loop between players, analytics, and iteration.