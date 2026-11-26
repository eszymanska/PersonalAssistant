---
name: waiting
description: Add a waiting-for item, or review what you are waiting on. Use when the user runs /waiting, says they are waiting on someone or something (for example "Sam owes me the contract", "I'm waiting for the plumber's quote"), or asks what they are waiting for.
argument-hint: "[what — from whom]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Arguments: $ARGUMENTS

**If arguments were given, add an item:**
1. Work out what is being waited for and from whom. If the person or organization is missing, ask for it.
2. If it clearly relates to an existing project in `projects/`, suggest the `+slug` tag.
3. Optionally ask for a follow-up date only if the user mentioned timing; otherwise default to no follow-up date.
4. Append to `waiting-for.md`: `- [ ] <what> — from: <who> [+slug] (since YYYY-MM-DD) [follow-up: YYYY-MM-DD]`.
5. Confirm in one line.

**If no arguments were given, review the list:**
1. Show open items grouped by person, with how many days each has been waiting.
2. Highlight items whose follow-up date has passed, and items waiting more than 7 days with no follow-up date.
3. For each highlighted item, offer: send a follow-up (add a next action like "Email <who> to check on <what>" in the right context), set a new follow-up date, mark it received (use the `/done` flow), or drop it (requires confirmation).
