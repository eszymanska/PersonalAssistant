---
name: mindsweep
description: Guided brain dump through the GTD trigger list. Runs only when the user types /mindsweep.
argument-hint: "[personal|work|all]"
disable-model-invocation: true
---

Run a GTD mind sweep to get everything out of the user's head and into `inbox.md`. Scope: $ARGUMENTS. If empty, use `scope` under `## Mind sweep` in `settings.md`; if that is missing, use `all`.

How to run it:
1. Explain in one line: you will go through trigger categories one at a time; the user lists whatever comes to mind, says "next" to move on, or "stop" to finish early.
2. Present one category at a time with its prompts (below). Keep each prompt short.
3. Append every item the user mentions to `inbox.md` as `- <text> (captured YYYY-MM-DD)`, keeping their wording. Do not clarify or organize; that is for `/process`.
4. After each category, confirm briefly how many items were captured, then show the next category.
5. At the end, report the total captured and offer to run `/process`.

Trigger list — personal:
- **Commitments to others:** promises made, things owed, people to call or write back, thank-yous.
- **Home:** repairs, improvements, cleaning, furniture, appliances, garden, car, bills.
- **Finances:** banking, taxes, bills, insurance, investments, subscriptions to cancel.
- **Health:** doctor, dentist, check-ups, exercise, prescriptions.
- **Family and friends:** birthdays, gifts, visits, events, things to discuss.
- **Errands and purchases:** things to buy, return, pick up, repair.
- **Admin:** documents, IDs, registrations, warranties, paperwork.
- **Learning and hobbies:** courses, books, skills, creative projects.
- **Travel and fun:** trips, vacations, events, reservations.
- **Digital:** email backlog, files, backups, passwords, devices.
- **Waiting on:** things others owe you, orders, replies.
- **Someday:** things you would like to do one day.

Trigger list — work:
- **Projects started, not finished.** Projects to start.
- **Commitments to boss, colleagues, customers, partners.**
- **Communications:** emails, calls, messages to send or reply to.
- **Meetings:** to schedule, prepare for, follow up on.
- **Writing:** reports, docs, proposals, reviews.
- **Planning:** goals, plans, budgets, roadmaps.
- **People:** hiring, feedback, 1:1 topics, team issues.
- **Systems and tools:** things to set up, fix, or learn.
- **Professional development:** training, conferences, reading.
- **Waiting on:** approvals, replies, deliverables.
