---
name: edit
description: Get a ready-to-use editing prompt to edit the user's video in the editing style of a reel from Comma's library (captions, cuts, zooms, transitions, overlays, sound, color, the steps in order and the moves beat by beat), fitted to their own script and editing tool. Use for "/comma:edit", "edit my video like this reel", "give me the editing style of …", "how do I edit this", "make an edit prompt for CapCut / Premiere / an AI editor".
argument-hint: "[a reel, a style, or one of their Comma scripts]"
---

# Edit it like a reel that worked

$ARGUMENTS, if given, names a reel, a style ("fast cuts with zooms"), or one of their Comma scripts.

1. Find the reel. If they named one, `search_breakdowns` for it. Otherwise ask what their video is and search with a few
   words about it or the style they want; show three whose `edit_style` is filled in, one line each (title, creator,
   the edit in a few words), and let them pick.
2. `get_edit_prompt` with its id. If it has no cookbook yet, say so and offer another reel.
3. If it's for one of their Comma scripts, `list_my_scripts` / `get_script` and map the reel's beat-by-beat edit moves
   onto their beats by job (their hook gets the hook's moves, and so on), with their timings.
4. Ask which tool they edit in (CapCut, Premiere, Final Cut, DaVinci, Descript, an AI video editor, or an editor they
   hire), unless they said. Rewrite the prompt for it: menu names and settings for an app, plain instructions for a
   person, one pasteable prompt for an AI tool. Keep every concrete value from the cookbook (sizes, positions, timings).
5. Give it as one block they can copy. Copy the editing style only, never the original creator's content.

If a call answers `pro_required`, say Comma Pro (or its free trial) is needed and stop.
