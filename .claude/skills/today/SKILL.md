---
name: today
description: Plan the day — hard landscape, due items, and a short daily focus list. Use when the user runs /today, or asks to plan their day (for example "plan my day", "what does today look like?", "good morning, let's plan").
argument-hint: "[@context ...] [energy low|med|high]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Plan today with the user. Arguments: $ARGUMENTS

GTD keeps two things apart, and so does this plan:
- **Hard landscape:** what must happen today, at a set time or on this day.
- **Daily focus:** 3 to 5 next actions the user would like to do today. They are a choice, not a commitment; anything left undone simply stays in `next-actions.md`.

Read the `## Today` section of `settings.md` first. Defaults when missing: `calendar-blocks: ask`, `gmail: on`, `gmail-limit: 5`.

If today's file `daily/YYYY-MM-DD.md` already exists, show it and offer to update it instead of starting over.

Steps:
0. **Yesterday.** If `completed.md` or `daily/` has anything for yesterday, open with one encouraging line, for example `Yesterday: 5 done, 3/4 focus.` Mention only what went well; skip the line if nothing was done.
1. **Hard landscape.** Read today's entries in `calendar.md` (this moves due ticklers to the inbox, rule 13 in `CLAUDE.md`). If a calendar connector is available, also read today's events from the user's primary calendar. Show one timeline, sorted by time, followed by the free blocks of 30 minutes or more between now and the end of the working day (for example `09:00–11:30 free (2h30)`). Without a calendar connector, use `calendar.md` alone and say so in one line.
2. **Due items.** In one line each, only if there are any:
   - Waiting-for items whose follow-up date is today or past, each with a one-line suggested nudge.
   - The number of inbox items. If there are more than five, suggest a quick `/process` before choosing the focus.
   - Active projects with no open next action (stalled).
3. **Email check.** Only if `gmail` is `on` and a Gmail connector is available: look at unread or starred messages from the last 24 hours and list at most `gmail-limit` that look like they need an action from the user, one line each (sender and subject). Offer to capture any of them to `inbox.md`. Capture only; do not clarify them here.
4. **Situation.** If the arguments did not say, ask one question: "Where will you be today, and how's your energy?"
5. **Daily focus.** Propose 3 to 5 open actions from `next-actions.md` that match the contexts, energy, and free blocks. Rank them as `/next` does: project due dates first, then areas and goals in `horizons.md`, then the oldest `added` date. Give a one-line reason for each and the free block it fits in. Keep the total estimated time well under the free time.
6. **Confirm.** Let the user swap, drop, or add actions. Then:
   - **Calendar blocks.** If `calendar-blocks` is `ask`, ask once whether to add focus blocks to the calendar, and add only the blocks the user approves. If `on`, add them and list what was added. If `off`, or there is no calendar connector, skip this. A block is an event titled with the action text, placed in its free block. This sends action text to an outside service, so never add a block without the setting or an explicit yes.
   - **Save** the plan to `daily/YYYY-MM-DD.md` in the daily plan format in `CLAUDE.md`.
7. Reply with the final plan in a compact form: timeline, then focus list.

Never write to Gmail. Read from connectors only what these steps need.
