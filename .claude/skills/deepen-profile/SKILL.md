---
name: deepen-profile
description: Enrich the user's profile with how they actually work day to day. Use when the user says "deepen my profile", "update my profile", "расскажу о своей работе", "розкажу про свою роботу", or during onboarding as an offered step. A short interview about daily tasks, tools/programs, and friction — the answers make future help much sharper. Writes a "## Daily work" section into system/profile.md.
---

## What this skill does

The onboarding interview captures who the user is. This captures **what they actually do** — so
the agent (and smarter future agents) can help them be productive instead of asking the basics
every time. It adds/updates a `## Daily work` section in `system/profile.md`. It's just context
about the user, to make future help sharper.

Run in the user's working language. Keep it to a few minutes — one question at a time, and it's
fine to skip any.

## Steps

1. **Frame it briefly:** "A few questions about your day-to-day. The better I understand your
   work, the more I can take off your plate. Skip anything you want."
2. **Ask, one at a time** (short answers are fine):
   1. **A typical day/week** — walk me through what you actually work on. What are you responsible for?
   2. **Tools & programs** — what do you use daily, and for what? (Google Drive/Docs/Sheets, email,
      calendar, notes, messaging apps, etc.)
   3. **Recurring tasks** — what do you do over and over? (These are future automation candidates.)
   4. **Friction** — where does your time go that you wish it didn't? What's annoying or slow?
   5. **Hand-offs** — who do you work with / pass things to / get things from?
3. **Write it** into `system/profile.md` under a `## Daily work` section (create it if missing;
   update in place if it exists). Do **not** touch the identity fields at the top. Use short
   bullets under: Typical day, Tools & programs, Recurring tasks, Friction, Works with.
4. **Close the loop:** if any recurring task or friction looks automatable, mention it once and
   offer to `level-up` or `create a skill` for it — don't push.

## Done when

`system/profile.md` has a filled `## Daily work` section reflecting the user's answers, and the
identity fields above are untouched. Re-runnable any time as work changes.
