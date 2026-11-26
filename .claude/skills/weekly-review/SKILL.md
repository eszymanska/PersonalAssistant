---
name: weekly-review
description: Guided GTD weekly review — get clear, get current, get creative. Runs only when the user types /weekly-review.
disable-model-invocation: true
---

Guide the user through the GTD weekly review, one step at a time. After each step, wait for the user before moving on. The user can say "skip" to skip a step or "stop" to end early; still write the review notes at the end.

First, find the most recent file in `reviews/` and tell the user when the last review was (or that this is the first).

## Get clear
1. **Collect loose ends.** Ask the user to gather physical papers, notes, receipts, photos, voice memos, and messages that contain commitments, and to dump anything from them into the inbox (capture them as they list items).
2. **Empty the head.** Ask: "Anything new on your mind since last week?" Capture replies to `inbox.md`. Offer `/mindsweep` if the user feels cluttered.
3. **Process the inbox to zero.** Run the `/process` flow on `inbox.md` (offer batch mode if there are many items).

## Get current
4. **Review next actions.** Go through `next-actions.md` by context. Ask the user to mark anything done (log to `completed.md`), and point out actions older than 30 days: still relevant, rewrite, move to someday, or drop?
5. **Review the past calendar.** Look at `calendar.md` entries from the past two weeks and `completed.md` for this week. Ask if anything there triggers new actions. Then remove past calendar entries (and move any past `tickler:` items into the inbox and process them).
6. **Review the upcoming calendar.** Show entries for the next two to three weeks. Ask what preparation each needs and capture actions.
7. **Review waiting for.** Use the `/waiting` review flow: overdue follow-ups, long waits, received items.
8. **Review projects.** Use the `/project` list flow. For each active project, confirm it is still active and has a next action. Fix stalled ones. Offer to put projects on hold, move them to someday, or mark them complete.
9. **Review checklists and reference.** Ask if any checklist or reference file in `reference/` needs updating.

## Get creative
10. **Review someday/maybe.** Show `someday-maybe.md`. Ask whether anything should become an active project now, and whether anything can be deleted (confirm).
11. **Be creative.** Ask: "Any new ideas, projects, or bold moves you want to capture?" Capture to the inbox or someday/maybe.
12. **Horizons check.** If `horizons.md` shows "Last reviewed" more than 90 days ago (or never), suggest a short horizons review now or scheduling one as a calendar entry. If reviewed now, update the date.

## Wrap up
13. **Celebrate.** Run the `/summary week` flow and show it.

Write `reviews/YYYY-MM-DD.md` (today's date) with:
- Date and which steps were done or skipped.
- Completed this week (from `completed.md`, the last seven days).
- Summary: the headline and the numbers from step 13.
- Projects added, completed, put on hold, or dropped.
- Stalled projects found and how they were resolved.
- Waiting-for follow-ups made.
- Top three focus areas for next week, as stated by the user (ask for them).

Finish with a short summary and the counts: inbox items processed, active projects, open next actions, waiting-for items.
