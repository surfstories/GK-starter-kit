---
name: level-up
description: Weekly upgrade ritual for this workspace — use when the user says "level up", "what should I automate", "upgrade my system", "find me leverage", or when you've noticed them doing the same manual task 3+ times. Interviews for friction, scopes ONE automation, ships ONE artifact (prompt, script, or skill) that fits their personal working style. Also handles "level up google" → open system/guides/connect-google-full.md. Personal to the user. Re-run weekly.
---

## What this skill does

Thin wrapper. The method lives in **`system/level-up-method.md`** — one agent-neutral
script so Claude and Codex run it identically. Your job: **read
`system/level-up-method.md` and follow it exactly, in order.**

One run = one shipped artifact (or one clean Eliminate/Delegate exit — also a win).

**Special case — "level up google":** if the user says "level up google" (or asks to *edit* Google
Sheets/Docs), don't run the friction interview — instead open `system/guides/connect-google-full.md`
and walk them through that advanced setup, in their language.

## Steps

1. Read `system/level-up-method.md`.
2. Phase 1 — friction interview, one question at a time → 1–3 candidates, user picks one.
3. Phase 2 — four gates: Eliminate/Automate/Delegate → process map (all five elements) →
   lowest autonomy level that works → the number it moves. Spec → `system/decisions.md`.
4. Phase 3 — build the simplest form that solves it; place it per kit rules
   (skills → `.claude/skills/`, everything else → `Projects/<name>/`).
5. Three-line close with the manual-first reminder.

## Hard rules (do not bend)

- **Eliminate first.** If dropping the task breaks nothing, exit cheerfully and log the win.
- **Lowest autonomy that works.** Push back on L3+ for a first build.
- **No number → no build.** If it doesn't move a metric, stop.
- **Manual-first.** Every new artifact starts supervised; autonomy is earned by clean runs.
- **Read before write; no secrets.** Anything that changes data previews first and waits for a yes;
  never write passwords or keys into the folder.
