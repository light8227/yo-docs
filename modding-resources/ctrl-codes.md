---
title: Control Codes, Glyphs & Ruby Text
layout: default
has_children: false
parent: Modding Resources
---
# Control Codes, Glyphs & Ruby Text
## Glyphs
In the 3DS Yo-kai Watch games, for any source of rendered text, a feature is supported whereby you can enclose the name of a resource from any currently loaded ANM in square brackets and it'll be rendered, substituting the code. We call this code a glyph. Here are some examples:
* `[g_coin]` - Confirmed to work in Yo-kai Watch 2
  * Named after ゲームコイン (Gēmukoin) aka game coin - the Japanese term for Playcoins. Used for the Crank-a-kai.
* `[key]` - Confirmed to work in Yo-kai Watch 2
  * This key glyph is used to signify "Key Quests" in the game - and is used in nearly half the phase text cfg.bins!.
* `[home]` - Confirmed to work in Yo-kai Watch 2
  * This is only used in one text file in the game - the text that appears after you have successfully saved the game.
* `[next_arrow]` - Confirmed to work in Yo-kai Watch 2
* `[misn_arrow]` - Confirmed to work in Yo-kai Watch 2
* `[misn_arrow2]` - Confirmed to work in Yo-kai Watch 2
* `[watch]` - Confirmed to work in Yo-kai Watch 2
* `[mission]` - Confirmed to work in Yo-kai Watch 2
* `[mission2]` - Confirmed to work in Yo-kai Watch 2
* `[btn_l_w]` - Confirmed to work in Yo-kai Watch 2
* `[btn_r_w]` - Confirmed to work in Yo-kai Watch 2
* `[btn_a_w]` - Confirmed to work in Yo-kai Watch 2
* `[btn_x]` - Confirmed to work in Yo-kai Watch 2

## Control Codes 

In Yo-kai Watch, you may notice some strings include patterns such as `<SOMETHING>TEXT</SOMETHING>` and `<SOMETHING>`. These are control codes and can be categorised as such:
* Colour Tags. These affect the colour of the enclosed text.
* Keywords. These are used to substitute values e.g. `<GENDER>`.
* Actor control codes. These such as `<V>`, which plays audio, have an indirect function and are usually not rendered.

### Colour Tags
> [!WARNING]
> Color Tags are **not** self closing; they *must* be terminated via `</C>`, even if not nested, to avoid visual glitches. No other known control code type has this property.

There are 3 kinds of colour tags:

* Named Pallete. Specifically, this includes `<CG>`, `<CR>` and `<CN>`.
* Direct colour. One can use `<C#XXXXXX>` and `<C"XXXXXX>` to specify an RGB888 colour.
* Numerical Pallete. YW2 supports C0 through C20. YWB supports up to C30. Unrecognised colours default to `#000000`.

For example, `<CR>Red</C>, <CG>Green</C>, and <CN>Blue</C> are cool. So is <C8>Orange</C>`.

## Ruby Text
In Japanese builds (this functionality is not present in many localised builds as they do not utilise it), Ruby Text can be included via the syntax `[a/b]`. For example, `[父/とう]`.
