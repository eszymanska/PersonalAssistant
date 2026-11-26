---
name: capture
description: Capture a thought into the GTD inbox instantly. Use when the user runs /capture, or explicitly asks to capture, jot down, note, or add something to their inbox (for example "capture: call the bank", "add renew passport to my inbox", "remind me to email Sam"). Do not use for commitments the user only mentions in passing; offer to capture those instead. Do not use for adding items to the shopping list; those go straight to `lists/shopping.md` as described in CLAUDE.md.
argument-hint: "<thought>"
---

Capture the following into `inbox.md`:

$ARGUMENTS

Rules:
- If nothing was given above, take the item or items from the user's latest message. If there is still nothing to capture, ask "What do you want to capture?" and capture the reply.
- Append one line per distinct item at the end of `inbox.md`, in the format `- <text> (captured YYYY-MM-DD)` using today's date. If the input clearly contains several separate items (separate lines, or a list), capture each as its own line. Keep the user's wording; do not rewrite.
- Do not clarify, organize, categorize, or ask follow-up questions. Capture must be instant.
- Reply with one line: how many items were captured and how many are now in the inbox.
