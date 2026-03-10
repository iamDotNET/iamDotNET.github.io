---
title: "My First Technical Deep Dive"
description: "How I implemented multiplayer player state replication in UE5."
date: "2026-03-10"
---

# Introduction

Here I explain how I handled player state replication in UE5.

## Networking System

- Used Steam P2P sessions for connecting players.
- Player states are replicated using UE5's `Replicate` flags.
- Optimized updates to minimize bandwidth.

## Challenges

- Syncing physics interactions across clients.
- Ensuring guards’ AI was consistent for all players.