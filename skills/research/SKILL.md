---
name: research
description: Turn documents (research papers, notes, transcripts, one big doc or many) into a set of Comma videos. Each video is matched to a reel from Comma's library whose shape fits it, saved as an idea with the research behind it, and drafted onto that reel's shape, so most of the script is done. Use for "/comma:research", "turn these papers into videos", "make reels from this document", "plan videos from my research", or when files are attached and they want Comma videos from them.
argument-hint: "[files or folder, or what to focus on]"
---

# Research into Comma videos

The documents are the material; Comma's library supplies the shapes; this Claude does the reading and the writing.
$ARGUMENTS, if given, is files, a folder, or what to focus on.

1. Call `comma_guide` first. Follow its format and rules exactly. If it answers `pro_required`, say Comma Pro (or its
   free trial) is needed and stop.
2. Read everything they gave you, in full: attached files, pasted text, or (in Claude Code) the files or folder named.
   Note each document's name, so every fact can be traced back to one.
3. Find the videos. One video = one point a viewer gets in under a minute (a finding, a number that surprises, a
   mistake people make, a how-to, a before and after). Prefer the specific over the general. Usually 1-3 per document.
4. Match each video to a shape: `search_breakdowns` with a few words about that video, pick the reel whose structure
   carries that kind of point best, and say why in a few words.
5. Show the plan as a numbered list, one line each: working title · the point · source document · the shape (reel
   title, creator) and why. Ask which to make: all, some, or changes. Don't write before they answer.
6. For each video they keep, in order:
   1. `save_idea` with a new UUID `capture_key`: `idea` = the point in plain words; `context_summary` = the facts the
      video needs, each with its document name; `open_questions` = what the research doesn't answer.
      Keep the returned `idea_id`.
   2. `get_breakdown` on its shape. Map the research onto it beat by beat: keep the shape's structure, beat jobs, order
      and moves; replace its subject and lines entirely with the research, in the user's voice. Never copy the shape's
      lines. Never invent a fact, number or quote: a gap becomes a short blank like `[your result here]`.
   3. `save_script` with a new UUID `save_key`, the title, format, content type, beats, `idea_id` and
      `based_on_reel_id` (the shape's id), and `version_name` "From research".
   If `limit_reached` comes back, stop, say how many were saved, and that the rest can be done tomorrow.
7. Finish with a short table: title · shape · saved. Every one is in Comma: the idea in Ideas, the draft in Drafts.
   They open it in the app to finish it in their own words.
