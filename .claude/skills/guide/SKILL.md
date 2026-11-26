---
name: guide
description: Explain how this GTD system works, answer questions about it, or set up a new instance. Use when the user runs /guide, or asks how the system works or what it can do (for example "how does this work?", "what can you do?", "what's the difference between a project and a next action?", "help me set this up").
argument-hint: "[setup | topic or question]"
---

If this was triggered by a plain-language request instead of the slash command, take the arguments from the user's latest message.

Explain the system or set it up. Arguments: $ARGUMENTS

Explain from the live files, not from memory: read `CLAUDE.md`, the relevant `.claude/skills/<name>/SKILL.md` files, and `settings.md`, so the explanation matches how the system works now. Use plain words, short paragraphs, and examples from the user's own files when they have any. Never change files except in setup mode.

## No arguments: the tour

Five short steps. Show one at a time; after each, the user says "next" to go on or "stop" to end.
1. **GTD in a minute.** The five stages, capture → clarify → organize → reflect → engage, each with the command that does it (`/capture` and `/mindsweep`; `/process`; `/project`, `/waiting`, `/contexts`; `/weekly-review` and `/summary`; `/today`, `/next`, `/done`).
2. **Where things live.** The main files from the file map in `CLAUDE.md`, one line each. Mention that everything is plain Markdown the user can edit by hand.
3. **A typical day.** `/today` to plan, capture as things come up, `/process` to empty the inbox, `/next` to choose, `/done` to check off. Mention that plain words work too ("what should I do now?").
4. **A typical week.** `/weekly-review` to get clear, current, and creative; `/summary` to see progress.
5. **Your setup.** The current values in `settings.md` and the registered contexts, and how to change them (edit `settings.md`, or `/contexts`).

At the end, if `settings.md` does not say `setup: done`, offer `/guide setup`; otherwise offer a first `/mindsweep` if the inbox and next actions are empty, or `/today` if not.

## `setup`: first-run onboarding

One question at a time. The user can say "skip" for any step, which keeps the current value. Save each answer as soon as it is given, editing minimally and keeping HTML comments.
1. **Git sync.** Explain `manual`, `direct-main`, and `pull-request` in one line each, recommend `direct-main` if the user works from several devices, and set `mode` in `settings.md`.
2. **Mind sweep scope.** Ask whether this instance is for personal life, work, or both, and set `scope` under `## Mind sweep`.
3. **Planning the day.** Explain the `/today` options and set `calendar-blocks` and `gmail` under `## Today`. Mention that Calendar and Gmail are only used when connected.
4. **Contexts.** Show the registered contexts. Ask which to keep, rename, or add, and apply the changes with the `/contexts` flows.
5. **Areas of focus.** Ask for the user's main areas of life or work (a short list is enough) and add them under `## Horizon 2 — Areas of focus and responsibility` in `horizons.md`, one `- <area>` line each. Leave the other horizons for a later horizons review.
6. **Finish.** Set `setup: done` under `## Setup` in `settings.md`, summarize the choices in a few lines, and offer to run `/mindsweep` now.

Follow the git sync mode for the changes, as in `CLAUDE.md`.

## A topic or question

Answer briefly: what it is, how the system handles it, and the command to use. For a command name (for example `process` or `contexts`), summarize what that command does and when to use it, from its `SKILL.md`. For a GTD concept, explain it in two or three sentences, then show how it maps to the files. If the user's files have a fitting example, use it. Offer the matching command at the end.
