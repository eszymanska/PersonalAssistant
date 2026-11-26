---
name: summary
description: Show an encouraging summary of what the user got done in a period. Use when the user runs /summary, or asks how they have been doing (for example "how was my week?", "what did I get done this month?", "show my progress").
argument-hint: "[day | week | month | year | YYYY-MM | YYYY-MM-DD..YYYY-MM-DD]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Summarize what the user got done, to show progress and keep them motivated. Period: $ARGUMENTS

**Period.** `day` is today, `week` the last seven days including today (default), `month` the last 30 days, `year` the last 365 days. `YYYY-MM` is that calendar month; `YYYY-MM-DD..YYYY-MM-DD` is that range, inclusive. The previous period is the same length, right before it.

**Data.** Read only these, and only for the dates needed:
- `completed.md`: lines under each `## YYYY-MM-DD` heading. A line starting with `Project completed:` is a completed project; one starting with `Received:` is a received waiting-for item; every other line is a completed action.
- `daily/YYYY-MM-DD.md`: `## Focus` items; `- [x]` is done, `- [ ]` is not.
- `projects/*.md` and `projects/archive/*.md`: the `Area:` line, to group work by area through the `+slug` tag.
- `reviews/`: which weeks had a weekly review.
- `horizons.md`: which areas and goals matter most.
- `inbox.md` and the project files, only for the closing next step.

**Metrics.** Compute for the period and for the previous period:
- Actions completed, projects completed, items received.
- Focus hit rate: done focus items over planned focus items, across the `daily/` files in the period. Skip it if there are none.
- Active days: days with at least one completed action. Current streak: consecutive days up to today (or the period's end) with at least one completed action.
- Weekly reviews done in the period (for `week`: done or not).

**Reply format.** Keep it compact, in chat:
1. **Headline:** one encouraging line built from the strongest true fact (for example "12 actions done and a project shipped — your best week this month").
2. **Wins:** completed projects, then up to three notable actions, preferring those tied to areas or goals marked important in `horizons.md`.
3. **Numbers:** one line per metric, with the previous period's value and ↑, ↓, or = (for example `Actions: 12 (prev 9) ↑`).
4. **Where the effort went:** completed actions by area, then by context, as short text bars, largest first (for example `Health ████ 4`). Actions without a project count under `No project`.
5. **One next step:** a single gentle suggestion, such as one stalled project or a full inbox. Skip it if nothing stands out.

**Tone.**
- Compare only with the user's own past, never with an ideal or with other people.
- Never shame a miss. Unchecked focus items were choices, not failures; do not list them.
- If there is little data (for example the system is new), say so kindly and celebrate what is there.
- Every number must come from the files. Never invent or round up progress.

Read-only: this skill changes no files. Never put this summary in an artifact or send it to an outside service (rule 12 in `CLAUDE.md`).
