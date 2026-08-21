---
title: Porting YW1 Maps to YW2
layout: default
grand_parent: Modding Guides
parent: Map Modding
has_children: false
nav_order: 1
---

# Porting YO-KAI WATCH 1 Maps to YO-KAI WATCH 2
For YO-KAI WATCH 1 to YO-KAI WATCH 2, the only change you need to make is NPCs:
* You might need to place npcs in an `npc.pck` for them to register.
* If the YW1 NPC has `OnTalk` scripts, you must convert them into a trigger in the YW2 map’s `.xq` file:
  * You can do this by recompiling the NPC for Yo-kai Watch 2 via NPCMake
* The NPCs `AppearCond` might need adjusting to appropriately match Yo-kai Watch 2, e.g. it might reference a flag that doesn't exist.
This is an *extremely simple* process and definitely the easiest port.
