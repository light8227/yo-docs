---
title: Porting YW2 Maps to YW3
layout: default
grand_parent: Modding Guides
parent: Map Modding
has_children: false
nav_order: 2
---

# Porting YO-KAI WATCH 2 Maps to YO-KAI WATCH 3
For YO-KAI WATCH 2 to YO-KAI WATCH 3, aside from BT maps, (Which won't be covered here) there are 2 main changes you need to make:
* Convert the mapenv - a W.I.P tool to assist with this can be found [here](https://github.com/n123git/yw-mapenvconv/).
* Convert the colbox `prm` to `XCL` for hitboxes.
  * As of this guide the only XCL reader does not have write capabilities - so this is currently not possible, a tool however is being developed for this.
