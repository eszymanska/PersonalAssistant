---
name: process
description: Clarify and organize inbox items with the GTD decision tree. Use when the user runs /process, or asks to process, clarify, or empty the inbox (for example "let's go through my inbox").
argument-hint: "[batch]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Process `inbox.md` to zero, following the GTD clarify and organize steps. First move due ticklers from `calendar.md` into the inbox (rule 13 in `CLAUDE.md`). Read `contexts.md`, `horizons.md` (areas), and the list of files in `projects/` first so suggestions use real contexts, areas, and projects.

Mode: $ARGUMENTS
- Default (empty): go one item at a time, top to bottom.
- `batch`: propose a decision for every item in one compact list, let the user correct any, then apply all at once.

For each item, propose a decision using this decision tree, then wait for the user to confirm or adjust:

1. **What is it? Is it actionable?**
   - **No, and not needed:** trash. Requires an explicit yes.
   - **No, but useful later:** file in `reference/<topic>.md`. Append to an existing topic file if one fits; otherwise propose a new topic name.
   - **No, but maybe one day:** add to `someday-maybe.md` under a fitting heading. Things to maybe buy go under `## Wish list`; gift ideas for others go in `reference/gift-ideas.md`.
   - **No, but relevant on a specific date:** add to `calendar.md` as info or as a `tickler:` entry.
2. **Yes, it is actionable. What is the desired outcome?** If it needs more than one action, it is a project. Propose a project name phrased as an outcome and an area, then create `projects/<slug>.md` using the project format in `CLAUDE.md`. If it belongs to an existing project, link it with `+slug`.
3. **What is the very next physical action?** Propose a concrete, verb-first action. If the user's wording is vague, rewrite it and show the rewrite.
   - **Simple purchase that needs no research or decision** (groceries, household restock, consumables): add to `lists/shopping.md` under the matching shop heading, and make sure the single `Buy items on the shopping list` action exists (its context follows the shopping-list rule in `CLAUDE.md`).
   - **Takes less than two minutes:** suggest doing it now. If the user does it, log it in `completed.md` under today's date.
   - **Someone else should do it:** add to `waiting-for.md` with `from:` and today's `since` date. If the user needs to send the request first, also add that as a next action.
   - **Must happen on a specific day or time:** add to `calendar.md` under `## Upcoming`, sorted by date.
   - **Otherwise:** add to `next-actions.md` under the matching `## @context` heading, with project tag, time estimate, and energy if known.
4. **Context check.** Use only contexts from `contexts.md`. If none fits, propose a new one (name and description). On approval, add it to `contexts.md` and add its `## @name` section to `next-actions.md`.

Rules:
- Present each proposal compactly, for example: `"dentist" -> next action: "Call Dr. Rossi's office to book cleaning" @phone ~5m. OK?`
- The user can answer "ok", correct any part, say "skip" (leave in the inbox), or "stop".
- Remove an item from `inbox.md` only after it has been placed (or trash was confirmed).
- Never put more than one item's decisions in a single question in default mode.
- At the end, summarize in a few lines: items processed, where they went, new projects, new contexts, items skipped.
