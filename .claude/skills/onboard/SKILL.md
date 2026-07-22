---
name: onboard
description: Use when someone is setting up this starter kit for the first time — English "onboard me" / "set me up" / "get me started", Russian "сделай онбординг" / "настрой меня", or when there is no filled system/profile.md yet. The user's FIRST message sets the working language — detect it and run onboarding in it. It's warm and non-technical, needs no install/keys/terminal, greets the user by name (read from the Claude account), offers every choice as a numbered menu, helps them connect Google in one click, builds their first project + skill, and levels them up through five ranks to 🏆 Champion. Idempotent — re-run any time.
---

## What this skill does

Thin wrapper. The actual onboarding steps live in **`system/onboarding-procedure.md`** — one
agent-neutral script so Claude and Codex onboard users identically. Your job:
**read `system/onboarding-procedure.md` and follow it exactly, in order.**

## Steps

1. Read `system/onboarding-procedure.md`.
2. Execute it top to bottom, **in the user's language** (detected from their first message —
   "onboard me" / "сделай онбординг"): preconditions (Claude desktop app, this folder; nothing to
   install) → read `system/profile.md` → greet by name (read `~/.claude.json` → confirm via menu,
   never ask if it's there) → a couple of quick menu questions + show the roadmap → teach the basics
   → **connect Google (Tier 1: one-click Connectors, verify with a real Drive read)** → build the
   first project `Projects/my-digest/` (uses the Google connection) → wrap it as the `catch-me-up`
   skill (via `create-skill`) → optional `deepen-profile` → write `system/profile.md` → **finalize
   the workspace yourself** (guarded: skip if `.canonical` exists; back up to `system/.preonboard/`;
   strip the `<!-- ONBOARDING-ONLY -->` blocks; prepend the personalized header) → fire the 🏆
   Champion finale → give the closing briefing.
3. **Every choice is a numbered menu.** One thing at a time. Idempotent: if `system/profile.md` is
   already filled, skip the interview and offer to re-run a step.

## The game (celebrate each unlock, boxed cards, in the user's language)

🥚 Rookie → 🎒 Explorer → 🔌 Connector → 🛠️ Builder → ⚡ Automator → 🏆 Champion. The first project
and first skill are offered (skippable); a skipped card just doesn't fire, and 🏆 Champion still
fires on completion.

## Hard rules (do not bend)

- **No keys, no terminal, no install** for the core flow. Never ask the user to paste a password or
  key — none are needed. The Google step is a browser sign-in.
- **Explain before you act; never change anything without a clear yes.** You only read/edit files in
  this folder and read a service the user connected.
- **Work in the user's language**, translating every card and message.
- **Coach, don't abandon.** If a screen looks different or something errors, invite a screenshot and
  "what next?" — solve it together.

## Done when

Google is connected (a real Drive read worked), `Projects/my-digest/` + the `catch-me-up` skill
exist, `system/profile.md` is filled, the workspace is finalized (ONBOARDING-ONLY blocks gone,
personalized header present), the 🏆 Champion card fired, and the closing briefing was given. See
`system/onboarding-procedure.md` for the full definition of done.
