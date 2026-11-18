---
name: idea
description: Save an idea from this conversation to the user's Comma ideas, with what they decided, Claude's unconfirmed suggestions and open questions kept apart. Use for "/comma:idea", "save this idea to Comma", "keep this for later in Comma".
---

# Save an idea to Comma

1. Ask which idea, if more than one is in play.
2. Call `save_idea` with a new UUID `capture_key` (reuse it on retries):
   - `idea`: the idea in the user's own words, short;
   - `context_summary`: what matters from the discussion;
   - `user_decisions`: only choices the user explicitly confirmed;
   - `assistant_suggestions`: your suggestions they haven't confirmed;
   - `open_questions`: what is still undecided;
   - `original_text`: their own words worth keeping, if any.
3. If it answers `upgrade_required`, tell them to update Comma and open it once, then try again.
4. Tell them it's in Comma. If they want a script from it now, use the make skill (or research, for many at once).
