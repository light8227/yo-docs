---
title: Adding NPCs (YW2)
layout: default
parent: Creating Your Own Postgame Stories
grand_parent: Modding Guides
---

# Adding NPCs (YW2)
> **Written by @n123original on Discord. This guide assumes you already know how to navigate romfs and use CfgBin Editor. If not, please read [the starting guide](../gettingstarted.html).**

## Registering the NpcBin

* First, navigate to `data/res/map/common`, and copy `npc_common.npcbin`.
* Next, rename your copied file to `<NPC>.npcbin`.
  * `<NPC>` is a placeholder for your NPC's internal name, for example, one might rename their file to `superCoolNPC.npcbin`.
* Next, navigate to `data/res/map/<MAP>/`
  * `<MAP>` here is a placeholder, for example, Uptown Springdale would be `t101g00`.
* Next, open the `npc.pck`, and place your newly created `.npcbin` inside this `.pck`.
* Finally, save the `npc.pck`.

## Registering NPCSet
* Next, outside of the `.pck`, open `<MAP>_npc_set*.cfg.bin`.
  * `<MAP>` here is a placeholder, for example, Uptown Springdale would be `t101g00`.
  * The `*` is a versioning placeholder. Meaning instead of just `t101g00_npc_set.cfg.bin`, files such as `t101g00_npc_set_0.01b.cfg.bin` may also exist. Pick the file with the highest version.
* Next, duplicate an `NPC_BASE_*` entry, the new entry should appear at the end of the tree.
* Next, set the `NPCID` to the CRC-32 hash of your NPC's internal name.
* Next, set the `BaseID` to your NPC's `BaseID`. This determines the model used.
* Next, pick an `NPCType`. The `NPCType` determines the icon used on the minimap, here is a list:

Yo-kai Watch 2 `NPCType`s:

0. N/A (Used for cars)
1. N/A
2. Human (Blue Circle with Eyes)
3. Yo-kai (Purple Whisp with Eyes)
4. Shop (Green Circle with Eyes)
5. Animal (Small Blue Circle with Eyes)
6. Enemy (Red & Yellow Wisp with Eyes)
7. Wayfarer Manor (Light Blue Wisp with Eyes)
8. Locked Area (Lock Icon)
9. Yo-kai2 (Darker Blurry Purple Whisp with Eyes)
10. Eyepo Tail Right (Circle with Eyepo icon pointing south-east)
11. Eyepo Tail Left (Circle with Eyepo icon pointing west, slightly to the south)
12. Comic Book (Open blue book with blank pages)
13. Medallium
14. Human2 (Appears identical?)
15. Blue Range (Old Lady Event)
16. Bony War (Red Wisp with Eyes)
17. Fleshy Ally (Blue Wisp with Eyes)
18. Bony War Rock (Red Rock)
19. Fleshy War Rock (Blue Rock)
20. Bony Range (Bony War Red Circle)
21. N/A (E-rank door doesn't exist, hence there is no texture)
22. D-Rank Watch Lock (Blue Watch Lock)
23. C-Rank Watch Lock (Green Watch Lock)
24. B-Rank Watch Lock (Red Watch Lock)
25. A-Rank Watch Lock (Gold Watch Lock)
26. S-Rank Watch Lock (Purple Watch Lock)

27+ are unregistered in Yo-kai Watch 2.


* Next, set all the other parameters to `0`.
* Next, increment (increase by 1) the `ChildCount` of the `NPC_BASE` tree that contains the entries.
* Next, click on the `NPC_APPEAR` tree. Take note of the `ChildCount`.
* Next, duplicate an `NPC_PRESET_*` entry, the new entry should appear at the end of the tree.
* Next, set the `NPCID` to your NPC's ID.
* Next, set the `NPCAppearStartPos` to the `ChildCount` you have noted down earlier.
* Next, set the `NPCAppearLength` to 1.
* Next, increment (increase by 1) the `ChildCount` of the `NPC_PRESET` tree that contains the entries.
* Next, duplicate an `NPC_APPEAR_*` entry, the new entry should appear at the end of the tree.
* Next, set the first parameter to your NPC's internal name.
* Next, set the `Cond` (4th) and the 6th param to 0.
* If you want to set a condition for the NPC to appear, change the `Cond` to the CExpression you wish to use.
* Next, set the other parameters to `-1`.
* Finally, increment (increase by 1) the `ChildCount` of the `NPC_APPEAR` tree that contains the entries.

This is sufficient to have an NPC. But chances are, you want your NPC to do something.

> [!WARNING]
> For now, this guide will not cover making the NPC actually talk, but will cover making it execute a trigger, and therefore running XQ.

## Registering NPCTalk
* Next, open `<MAP>_npc_talk*.cfg.bin`.
  * `<MAP>` here is a placeholder, for example, Uptown Springdale would be `t101g00`.
  * The `*` is a versioning placeholder. Meaning instead of just `t101g00_npc_talk.cfg.bin`, files such as `t101g00_npc_talk_0.03d.cfg.bin` may also exist. Pick the file with the highest version.
* Next, click on the `TALK_CONFIG` tree. Take note of the `ChildCount`.
* Next, duplicate a `TALK_INFO_*` entry, the new entry should appear at the end of the tree.
* Next, set the `TalkConfigStartPos` to the `ChildCount` you have noted down earlier.
* Next, set the `TalkConfigLength` to 1.
* Next, set the `NPCID` to your NPC's ID.
* Next, increment (increase by 1) the `ChildCount` of the `TALK_INFO` tree that contains the entries.
* Next, duplicate a `TALK_CONFIG_*` entry, the new entry should appear at the end of the tree.
* Next, set the first param to 1.
* Next, set every other param to 0.
* Next, set `ConditionalCond` to 0.
* Next, decide on whether you want your NPC to execute a trigger (and thus run XQ).
* If so, create an NPCTrigger (type 11) with your `NPCID` as the `TriggerID`.
* Next, compile the CExpression `RunTrigger(0x<TriggerID)` e.g., for `TriggerID` 0x12345678, this would be `RunTrigger(0x12345678)`.
* Next, set that as your `TrigCond`.
* Next, increment (increase by 1) the `ChildCount` of the `TALK_CONFIG` tree that contains the entries.
