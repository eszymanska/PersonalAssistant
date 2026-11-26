---
name: next
description: Suggest what to do now based on context, time, and energy. Use when the user runs /next, or asks what to work on (for example "what should I do now?", "I have 20 minutes at home, what can I do?", "anything for low energy?").
argument-hint: "[@context ...] [time e.g. 30m] [energy low|med|high]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Suggest what the user should do now. Arguments: $ARGUMENTS

Parse the arguments:
- Words starting with `@` are contexts (one or more).
- A duration such as `15m`, `30m`, `1h` is the time available.
- `low`, `med`, or `high` is the user's current energy.
- Anything missing is unconstrained. Do not ask for it.

Steps:
1. Read `calendar.md`. Move due ticklers into the inbox (rule 13 in `CLAUDE.md`). Then show anything else dated today or overdue first. That is the hard landscape and comes before any next action.
2. Read `next-actions.md`. Keep open actions (`- [ ]`) that match the contexts given (`@anywhere` always matches). Drop actions whose `~time` exceeds the time available. When energy is given, prefer actions whose `!energy` is at or below it; actions without an energy tag remain eligible.
3. Rank the remaining actions:
   - Actions tied to projects with a due date soon (read the `Due:` line in `projects/<slug>.md`).
   - Actions tied to areas or goals the user marked as important in `horizons.md`.
   - Older actions (by `added` date) before newer ones, all else equal.
4. Show the top 3 to 5 suggestions, each with a one-line reason. Do not dump the whole list.
5. Also mention, in one line each and only if relevant: waiting-for items whose follow-up date has passed, and the count of unprocessed inbox items.

If nothing matches, say so and suggest the closest alternatives (for example, actions in another context).
