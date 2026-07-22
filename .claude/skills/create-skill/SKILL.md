---
name: create-skill
description: Build a new personal skill for this workspace. Use when the user says "create a skill", "make a skill", "новый скилл" / "создай скилл", or describes a repeatable task they want to trigger by a phrase. Interviews for the essentials, then writes a well-formed .claude/skills/<name>/SKILL.md. Skills are personal and local to this folder.
---

## What this skill does

Turns "I keep doing X" into a reusable skill the user can trigger by a phrase. A skill is just a
folder `.claude/skills/<name>/` with a `SKILL.md` inside: some frontmatter (a `name` and a
`description` that lists the trigger phrases) and a short list of steps the agent follows.

Run everything in the user's working language (see `system/profile.md`).

## Steps

1. **Name it.** Short, kebab-case (e.g. `plan-my-day`, `log-call`). Confirm the folder will be
   `.claude/skills/<name>/`.
2. **Trigger phrases.** Ask what the user would type to fire it — collect a few, in their
   language(s). These go into the `description` so the skill actually gets picked up.
3. **What it does + steps.** Get the task in plain words, then turn it into a short numbered list
   of concrete steps. Keep it minimal — the simplest thing that works. Anything that changes data
   (files, a connected Google account) should preview first and wait for a yes.
4. **Write the file.** Create `.claude/skills/<name>/SKILL.md` with this shape:
   ```
   ---
   name: <name>
   description: <one line: what it does + the trigger phrases, incl. the user's language>
   ---

   ## What this skill does
   <one or two sentences>

   ## Steps
   1. ...
   2. ...
   ```
   If the skill just runs an existing project/prompt (like `catch-me-up` running
   `Projects/my-digest/`), the steps can be as short as "read and follow `Projects/<name>/<file>.md`."
5. **Show it back** and confirm. Tell the user it will trigger next session (or right away) when
   they type one of the phrases. Offer to test it now.

## Done when

`.claude/skills/<name>/SKILL.md` exists, has valid frontmatter with real trigger phrases, and the
user has seen it. Skills are personal — they live in this folder and belong to the user.
