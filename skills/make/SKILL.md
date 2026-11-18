---
name: make
description: Turn one topic the user has researched or discussed in this chat into one short-video script that teaches or explains it, in Comma's exact format, optionally on the shape of a reel that worked, and save it to their Comma Drafts. For many documents or many videos, use the research skill instead. Use when they say "/comma:make", "make this a reel", "turn this into a script for Comma", or similar.
argument-hint: "[topic or angle, optional]"
---

# Make a reel script with Comma

The user did the research; this turns it into a reel that teaches or explains it. $ARGUMENTS, if given, is the topic or angle.

1. Call `comma_guide` first, every time. Follow its format and rules exactly: they are Comma's, and the user's words come first. If it answers `pro_required`, tell the user Comma Pro (or its free trial) is needed and stop.
2. Gather the material: what the user researched, decided and said in this conversation. Use only that. Never invent facts, numbers or events about them; leave a short blank like `[how many]` instead.
3. Ask one question only if the video's point is unclear.
4. Offer a shape: call `search_breakdowns` with a few words about their video, show three in one line each (title, creator, why it worked), and let them pick or say "no shape". Call `get_breakdown` on their pick. Borrow its structure and moves, never its subject or lines.
5. Write the script beat by beat (label, what they say, on-screen words, shot) and show it to them as a readable script, not JSON.
6. Save only when they say so: `save_script` with a new UUID `save_key` (reuse it if you retry), the title, format, content type, beats, `based_on_reel_id` if a shape was used, and `idea_id` if it came from one of their Comma ideas. To revise a script they already have in Comma, pass its `script_id`: Comma adds a new version beside theirs and never overwrites their words.
7. Tell them it's in Comma's Drafts (they'll see it next time they open the app).
