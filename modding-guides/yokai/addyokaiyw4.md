---
title: Adding Yo-kai to YW4
layout: default
grand_parent: Modding Guides
parent: Yo-kai and Battles
---


# Adding Yo-kai to YO-KAI WATCH 4
**Original guide by 8227light on Discord**

Before I begin this guide, note that **at this time, you must have a model already in the game's format.** There is no model importer, so you can only have existing Yo-kai or a texture edit of an existing Yo-kai.

Furthermore, the **actual usability is very limited at this time.** It is currently unknown how to fully add Yo-kai properly, so right now, your Yo-kai is completely useless because it effectively doesn't exist. We don't know how to make the model appear, nor how to make the icons work properly.

# Required Files

The files you need may vary depending on what you are trying to do, ie whether you're adding an existing Yo-kai or doing a recolor. For this guide, I'll act as if you're doing a recolor of Present Noko.

**chara_base_0.00.00.cfg.bin:** Assigns some core info, such as Tribe and Rank.

**chara_param_0.13.62.cfg.bin:** Assigns some core info, such as stats and moves.

**addmenber_text.cfg.bin:** This is for dialogue the Yo-kai says when befriending you, for both the Crank-a-Kai and Konkatsu.

**chara_text.cfg.bin:** This is for assigning a name to your Yo-kai.

# g4pkm

In the header of the g4pkm, before the strings for the files inside of the g4pkm are listed, there are CRC hashes of said filenames. It is currently unknown if these are absolutely necessary to change.

# objbin
The objbin contains various parameters for the model itself to use.

By clicking on the OBJ tree, you can find the string of the model name. It is currently unknown what the purpose of this string is.

Inside the SETUP tree, in SETUP_PARAM_0, you can find the filepath for what skeleton to use, which will lead to a model file, a g4pkm.

# g4pk

In the header of the g4pk, before the strings for the files inside of the g4pk are listed, there are CRC hashes of said filenames. It is currently unknown if these are absolutely necessary to change.

# mevbin
This cfgbin type is older, and thus has no trees. Thankfully, the mevbins are also pretty simple to look at.

The COUNT entry at the start details how many MOT_X entries and EVENT_X entries there are.

The ID in the MOT_X entries are CRC hashes of names stored in that mevbin's g4mt counterpart, which is stored in the g4pk. (For example, a _p010.mevin's MOT_X ID names would be from the g4mt file inside of the _p010.g4pk file.) Seemingly, only the last names in the g4mt are used for this, ie if a mevbin has two MOT_X entries, then the last two names in the g4mt are the CRC hashes for them.

# chara_text: NOUN_INFO
Open the file in CfgBinEditor after downloading the latest MyTags.

Duplicate the entry of the Yo-kai you're recoloring, in this case, Present Noko, and change the string for their name.

You'll want to make a new NounID here, which you can generate at https://emn178.github.io/online-tools/crc/. This NounID is just a CRC hash of 'name_[ModelName]'. So, for this guide, I'll be hashing 'name_y02210010'.

# chara_base: CHARA_BASE_INFO_LIST
Open the file in CfgBinEditor after downloading the latest MyTags.

Skip the CHARA_BASE_BATTLE_LIST struct and move on down to the CHARA_BASE_INFO_LIST struct.

Duplicate the entry of the Yo-kai you want to base your new one off of, and make a new BaseID. BaseIDs are just a CRC hash of the model name, and for this guide, I'll make my Noko recolor's model name y02210010.

The Filename should be pretty self-explanatory. It's the name used in the actual files. For this guide, y02210010.

The NameID here will be the same as the NounID that you made previously for chara_text.

You'll want to make a new CharaModelID. CharaModelIDs are just a CRC hash of 'mdl_[ModelName]'. So, for this guide, I'll be hashing 'mdl_y02210010'.

In the CharaMotionID section, set it to your new BaseID. They're the same.

In the MenuResourceID section, set it to your new BaseID. They're the same.

Next comes setting up a CHARA_BASE_INFO_REF_BATTLE entry. This lets the file know what to reference in the other struct in this file, CHARA_BASE_BATTLE_LIST, which contains data for Role, Rank, and Tribe. CharaBaseBattleStartPos refers to the entry number in the aforementioned struct that it will start looking in, and CharaBaseBattleLength is how many entries from that point it will look at, which will always be 1 for this. Duplicate a REF_BATTLE entry and configure it so it references the correct entry.

# chara_base: CHARA_BASE_BATTLE_LIST
For our last steps in this file, duplicate the BATTLE_LIST entry of the Yo-kai you're basing your new one off of. Note the entry number in the list after doing so, as that will be the number you should be putting in for the CharaBaseBattleStartPos in the other struct.

Role, FavoriteFood, DislikedFood, Tribe, and Rank are pretty self-explanatory, as long as you know what number correlates to what. You can find a key below.

**Food**:
  - 0: No Food
  - 1: Rice Balls
  - 2: Bread
  - 3: Candy
  - 4: Milk
  - 5: Juice
  - 6: Burgers
  - 7: Ramen
  - 8: Sushi
  - 9: Veggies
  - 10: Fruit
  - 11: Meat
  - 12: Seafood
  - 13: Curry
  - 14: Sweets
  - 15: Soba
  - 16: Udon
  - 17: Snacks
  - 18: Chocobars
  - 19: Ice Cream
  - 20: Doughnuts
  - 21: Tempura
  - 22: Sukiyaki

**Role:**
  - 0: No Role
  - 1: Attacker
  - 2: Shooter
  - 3: Tank
  - 4: Healer
  - 5: Watcher

**Tribe:**
  - 0: No Tribe
  - 1: Goriki
  - 2: Onnen
  - 3: Mononoke
  - 4: Tsukumono
  - 5: Uwanosora
  - 6: Omamori
  - 7: Mikakunin
  - 8: Mikado
  - 9: Izana
  - 10: Oni
  - 11: Wicked
  - 12: Shinma

**Rank:**
  - 0: No Rank
  - 1: Rank E
  - 2: Rank D
  - 3: Rank C
  - 4: Rank B
  - 5: Rank A
  - 6: Rank S

Once you're done, make sure to update the ChildCounts of each struct by clicking the dropdown.

# chara_param: CHARA_PARAM_INFO_LIST
Duplicate the entry of the Yo-kai you're basing your new one off of, and make a new ParamID. ParamIDs are a CRC hash of 'para_[ModelName]'. So, for this guide, I'll be hashing 'para_y02210010'.

Use the BaseID you made earlier for the BaseID section.

You'll see various stats prefixed with BaseA/B/C. BaseA/B correlate to base stats around Lv1 and Lv99, while BaseC correlates to base stats around Lv120.

ElementResist and ElementWeak refer to which Elements the Yo-kai are strong or weak to. You can find a key for them below.

Speed refers to the tier of speed that Yo-kai will have. You can find a key for it below.

CharaType should be set to 'yokai' already. If it isn't, change it.

TransformsInto should only be necessary if you are making a Shadowside Yo-kai or assigning what a transformation should revert back into. If this is the case, put the ParamID of what they transform or revert into. Otherwise, leave it as 0 for them to undergo Great Change.

**Elements:**
  - 1: Fire
  - 2: Water
  - 3: Lightning
  - 4: Earth
  - 5: Ice
  - 6: Wind
  - 7: Light
  - 8: Dark

**Speed:** 0 - Normal, 2 - Slow, 3 - Fast
  - 0: Normal
  - 1: Very Slow
  - 2: Slow
  - 3: Fast
  - 4: Very Fast

# chara_param: YOKAI_PARAM_INFO_LIST
Duplicate the entry of the Yo-kai you're recoloring.

Put in your newly made ParamID.

The different MoveIDs, SkillID, and SoultimateID use the ParamIDs for said moves. Don't change these unless you want a different moveset, of course, but if you do, look and see what the other IDs for moves are.

The XMoveUnlock variables refer to the level at which the Yo-kai will unlock that XMove. If you want it to be innately learned, for example, set it to 0.

Once you're done, make sure to update the ChildCounts of each struct by clicking the dropdown.

# addmenber_text: TEXT_INFO
Duplicate the entry of the Yo-kai you're recoloring.

In the TextID section, put your new ParamID. They're the same.

TextIndex refers to whether it's for the Crank-a-Kai or Konkatsu. 0 is for the Crank-a-Kai, and 1 for Konkatsu.

TextString is obvious. Write what you want them to say.

As of 7/4/24, this is the most we can do for now.
Should any further developments be done, or everything is fully figured out, I will edit the above guide and remove this part.
