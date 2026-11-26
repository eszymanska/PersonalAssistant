---
name: project
description: Create a project, or list projects and flag stalled ones. Use when the user runs /project, asks to create or start a project, or asks to see their projects or which ones are stalled (for example "show my projects", "make a project for the kitchen").
argument-hint: "[project name]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Arguments: $ARGUMENTS

**If a project name was given, create a project:**
1. Check `projects/` for an existing project with a similar name. If one exists, show it and ask whether to use it instead.
2. Ask, in a single message, only for what is missing:
   - The outcome: what does "done" look like? Propose a phrasing as a finished state.
   - The area from `horizons.md` it belongs to (suggest one; if no areas are defined yet, suggest one and offer to add it).
   - The very next physical action and its context.
   - A due date, if any (optional).
3. Create `projects/<kebab-case-slug>.md` using the project format in `CLAUDE.md`, with today's date as `Created` and a first log entry `- YYYY-MM-DD Project created`.
4. Add the next action to `next-actions.md` under its context, tagged `+slug`.
5. Confirm in one or two lines.

**If no name was given, list projects:**
1. Read every file in `projects/` (not the archive).
2. For each project show: name, status, area, due date if any, and its open next action(s) found by `+slug` in `next-actions.md`, `waiting-for.md`, and `calendar.md`.
3. Flag **stalled** projects: active projects with no open item tagged with their slug. Offer to define a next action for each.
4. Flag projects with a due date in the next 14 days or overdue.
5. Keep the list compact, one or two lines per project.
