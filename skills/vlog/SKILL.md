---
name: vlog
description: At the end of any session, turn everything above in this conversation (research done, something learned, a feature built, a bug fixed, a decision worked through) into a first-person vlog-style reel in Comma's exact format, and save it to their Comma Drafts. Works for a research chat as well as a Claude Code build ("that was a lot, now make it a video"). Use for "/comma:vlog", "make a vlog of what we built", "turn this session into a video", "make a reel about what we just did".
argument-hint: "[angle or audience, optional]"
---

# This session, as a vlog

The user lived this session; the reel tells it as their story, in their voice. $ARGUMENTS, if given, is the angle or
audience.

1. Everything above in this conversation is the material, whatever it was: research, learning, building, deciding.
   Call `comma_guide` first. Follow its format and rules exactly. If it answers `pro_required`, say Comma Pro (or its
   free trial) is needed and stop.
2. Gather what really happened, from the whole conversation: what they set out to do or find out, what they found, what
   surprised them. If code changed in Claude Code, also look at `git log` / `git diff --stat` for this session for real
   names, numbers and the before and after. Find:
   - the goal at the start, in one line;
   - the turn: what broke, surprised them or changed the plan (the most specific moment wins);
   - the result, with the real numbers and names;
   - the one thing a viewer can take away.
   Never invent events, results or numbers. A missing detail becomes a short blank like `[how long it took]`.
   Leave out anything private: keys, client names, internal URLs.
3. Pitch three angles in one line each (the mistake, the result, the lesson, or the build itself) and let them pick.
   If they already gave one, skip this.
4. Offer a shape: `search_breakdowns` (try "day in the life", "build", "I made") and show three in one line each; let
   them pick or say "no shape", then `get_breakdown`. Borrow its structure and moves, never its subject or lines.
5. Write it beat by beat (label, what they say, on-screen words, shot): first person, spoken, short sentences, the hook
   in the first line. Shots should be filmable by them: a screen recording of the feature, the code, them at the desk,
   the before and after. Show it as a readable script, not JSON.
6. Save only when they say so: `save_script` with a new UUID `save_key` (reuse it on retries), the title, format,
   content type, beats and `based_on_reel_id` if a shape was used. To redo a script already in Comma, pass its
   `script_id`: Comma adds a version and never overwrites their words.
7. Tell them it's in Comma's Drafts.
