---
title: Base IDs
layout: default
has_children: true
parent: Modding Resources
---

# Base IDs
## Format
BaseIDs are the CRC-32 hash of the model's file name. Note that in YW1, only the first three numbers are included, while later titles use the whole file name. The layout of a model's file name (excluding certain test models) is shown below:

The layout can be represented in form `xYYYYYY`. `x` is a character representing the type of model. `YYYYYY` is a 6 digit number with no specific purpose other than being unique within its type.

### First Character

#### YW1

|Letter|Character Type|
|------|--------------|
|c     |Humans|
|d     |Vehicles|
|i     |Interactable Objects|
|m     |Animated Non-interactable Objects|
|r     | Critters |
|x     | Yo-kai Tribe Medals |
|y     | Yo-kai |
|z     | Test Models |

#### YW2-YWB2

|Letter|Character Type|
|------|--------------|
|c     |Humans|
|d     |Vehicles|
|g     | Mounts (YW3+) |
|i     |Interactable Objects|
|m     |Animated Non-interactable Objects|
|r     | Critters |
|t     | DX Medals |
|x     | Bosses |
|y     | Yo-kai |
|z     | Test Models |

#### YW4

|Letter|Character Type|
|------|--------------|
|c     |Humans and Animals|
|i     |Items|
|w     |Special Yo-kai|
|x     |Boss and Misc. Yo-kai|
|y     |Yo-kai|
