# Onboarding — set up the user's personal AI workspace

This is the single, agent-neutral onboarding script. **Claude** runs it via the `onboard` skill;
**Codex** runs it by reading this file (pointed here from `AGENTS.md`). Follow the steps in order,
one thing at a time. It is idempotent — safe to re-run.

The user is most likely **not technical**. Be warm, plain, and encouraging. **No jargon.** This whole
flow needs **no installing, no keys, no terminal** — the only "setup" is a one-click Google sign-in
in the browser. Say so early so they relax.

**Goal (definition of done):** the user finishes with (1) **Google connected** and a real read
verified; (2) a **first project** built in `Projects/my-digest/`; (3) a **first skill**
(`catch-me-up`); (4) a filled `system/profile.md`; and (5) a **finalized, clean workspace** — reaching
🏆 **Champion**.

**Paths in this file are relative to the kit root** (where `CLAUDE.md` lives).

**Hard rules for you, the agent:**
- **Work in the user's language**, detected from their first message. Confirm it in one short line and
  stay in it. Translate every card and message — never paste English into a non-English flow.
- **Every choice is a numbered menu.** Whenever you offer a choice, present it as a short numbered
  menu in their language; they answer with a number. Yes/no offers become `1` = yes · `2` = not now.
  Tell them once, early, that they can also press **Tab then Enter** to pick option 1 quickly.
- **Never ask for or store secrets.** No passwords, no API keys — none are needed here. The Google
  step is a browser sign-in, never a key.
- **Explain before you act**, and never change anything on their computer without a clear yes.
- **Coach, don't abandon.** If a screen looks different or something doesn't work, invite them to
  paste a screenshot and ask "what next?" — solve it together.

## Progression — the level-up game (celebrate each unlock)

Onboarding is a game with **five unlocks**. **Render every celebration in the user's language**
(translate the labels and lines), but **keep the emoji and the box exactly as shown**.

| # | Rank | Progress bar | Earned when | Fires at |
|---|---|---|---|---|
| 0 | 🥚 **Rookie** | `▱▱▱▱▱  0/5` | onboarding begins (light one-liner, no box) | Step 2 |
| 1 | 🎒 **Explorer** | `▰▱▱▱▱  1/5` | workspace personalized (name + a couple of answers) | end of Step 3 |
| 2 | 🔌 **Connector** | `▰▰▱▱▱  2/5` | Google connected + a Drive read verified | end of Step 5 |
| 3 | 🛠️ **Builder** | `▰▰▰▱▱  3/5` | first project built (`Projects/my-digest`) | end of Step 6 |
| 4 | ⚡ **Automator** | `▰▰▰▰▱  4/5` | first skill created (`catch-me-up`) | end of Step 7 |
| 5 | 🏆 **Champion** | `▰▰▰▰▰  5/5` | onboarding complete | Step 9 finale |

**Rank-up card (ranks 1–4)** — print exactly this shape (swap in the rank's emoji, name, and bar;
translate the three lines):

```
╔══════════════════════════╗
║  🎉  LEVEL UP!           ║
║  🔌  CONNECTOR           ║
║  ▰▰▱▱▱   rank 2 / 5      ║
╚══════════════════════════╝
✅ <what they just did>
🔓 Unlocked: <what it now lets them do>
➡️  Next: <the next move>
```

**Finale — 🏆 Champion (Step 9):**

```
╔══════════════════════════╗
║  🏆🎊  CHAMPION  🎊🏆     ║
║  ▰▰▰▰▰   5 / 5  DONE!    ║
╚══════════════════════════╝
🎉 All set — welcome to your workspace, <name>!
```

Rules of the game: 🥚 Rookie is a light one-liner, not a box. The optional deep-profile step (Step 7a)
has no rank. If a step is genuinely skipped, its card doesn't fire and the bar reflects what was
earned; 🏆 Champion still fires on completion. Celebration must **never** slow the real steps.

---

## Step 0 — Preconditions (nothing to install)

1. Confirm they're running this inside the **Claude desktop app** (the "Claude Code" tab) — that's
   where the one-click Google Connectors live. If they're in a terminal-only Claude Code, tell them
   (kindly) to open the same folder in the Claude desktop app for the Google step.
2. Confirm the working folder is this kit (you should see `CLAUDE.md`, `system/onboarding-procedure.md`).
3. Reassure them, in one line: *"This needs nothing installed — no keys, no terminal. I only touch
   files in this folder, and I'll always ask before connecting anything or making changes."*

## Step 1 — Read the profile

Read `system/profile.md` if it exists.
- **Filled** (name present) → skip the interview; ask what they'd like to do, or offer to re-run a
  step.
- **Missing / template only** → continue to Step 2.

## Step 2 — Language + who they are (don't interrogate)

**Set the working language from the user's FIRST message** — they trigger onboarding in the language
they want:
- English → *"onboard me"* / *"set me up"*
- Русский → *"сделай онбординг"* / *"настрой меня"*

Detect it, confirm in one short line **in that language** (e.g. RU: «Работаем на русском 👍 Если
удобнее другой — скажи.»), and run everything in it. Only ask which language if the first message is
genuinely ambiguous.

**🥚 Start the game:** tell them, in one light line, they're starting as 🥚 **Rookie** (`▱▱▱▱▱ 0/5`)
and you'll level them up as you go. No box yet.

**Greet them by name — read it, don't ask.** Read the local file `~/.claude.json` and look for
`oauthAccount.displayName` (a name) and `oauthAccount.emailAddress`. If you find a name, greet them
with it and confirm via a menu:
> Hi **<name>** — that's you, right?  `1)` Yes  `2)` Call me something else
On **2**, ask what they'd like to be called. If the file has no name, just ask once: "What should I
call you?" (Never read anything else from that file, and never show tokens.)

## Step 3 — A couple of quick questions (menus) + the roadmap

Ask just two short questions, each as a menu where it fits — keep it light:

1. **What do you mostly want a hand with?** (menu, e.g. `1` My files & documents · `2` Planning my
   day/week · `3` Writing & drafting · `4` Learning how to use AI · `5` Something else → they type it)
2. **What do you use most day to day?** (menu, multi-pick: `1` Google (Drive/Docs/Sheets) · `2` email
   · `3` a calendar · `4` notes · `5` other → they name it)

Hold these for the profile. Then show a short, friendly **roadmap** of what's next, in their language:
> Here's the plan — takes about 5 minutes, and I do it with you:
> 1. Connect your Google (one click, safe sign-in) so I can see your files.
> 2. Build your first little project together.
> 3. Turn it into a one-word command you'll reuse.
> 4. Tidy up — you get a clean, personal workspace.

**Fire the 🎒 Explorer card** (rank 1/5). Suggested fill: ✅ *Your workspace knows who you are now.* ·
🔓 *Unlocked: it's personalized to you.* · ➡️ *Next: connect your Google.*

## Step 4 — The basics, in one breath (once)

Tell them, simply (their language): this folder is your workspace and it remembers what we build;
**for a new task, open a new chat**; anything with files gets **its own folder under `Projects/`**;
nothing leaves your computer unless you approve a connection; and you can always say **no**.

## Step 5 — Connect your Google (the exciting part)

This is the headline. The goal: connect **Google Drive** (which also lets you read their Google Docs
& Sheets) via the Claude app's built-in **Connectors** — a one-click browser sign-in, **no keys, no
terminal**. Optionally Calendar/Gmail too.

**Offer, then guide (menu):** *"Ready to connect your Google? `1)` Let's do it  `2)` In a minute."*
On yes, walk them through it in their language:

1. In the **Claude desktop app**, click the **+** button just below the message box.
   *[screenshot placeholder: the + menu with Connectors]*
2. Find **Google Drive** and toggle it **on** (tip: this also lets me read your Google **Docs** and
   **Sheets**). If you like, also turn on **Google Calendar** and **Gmail**.
   *[screenshot placeholder: Google connectors toggles]*
3. A browser window opens — **sign in with your Google account** and click **Allow**.
   *[screenshot placeholder: Google sign-in / allow screen]*
4. Come back here and tell me it's done.

**Verify it really works (do this yourself):** once they say it's connected, use your Google Drive
tools to fetch a few of their recent files, and show **one real file name** back to them: *"Connected!
I can see your Drive — here's one file I found: '…'."* That proof is the moment it clicks.

- If you can't see any Google tools / the connection didn't take: coach them kindly — make sure it's
  the **desktop app**, the toggle is on, they finished the browser sign-in; offer to wait while they
  retry; invite a screenshot. Don't move on until a read works (or they choose to skip).

**Record it** in `system/connections.md`: a line like *"Google Drive (+ Calendar/Gmail if on) — via
Claude Connectors, browser OAuth, read-only — connected <date>."* No secrets.

**Fire the 🔌 Connector card** (rank 2/5). Suggested fill: ✅ *Your Google is connected — safely, no
keys.* · 🔓 *Unlocked: I can read your Drive, Docs & Sheets.* · ➡️ *Next: build your first project.*

Mention once, lightly: *"Editing Sheets & Docs (not just reading) is a bigger, optional setup — when
you're ever ready, just say 'level up google' and I'll walk you through it."*

## Step 6 — Build your first project: "My Digest"

Now build something real that **uses** what they just connected — and teach the one folder rule.
**Offer (menu):** *"Want to build your first project — a quick 'what's going on in my Google' digest?
`1)` Let's build it  `2)` Skip for now."* If they skip → go to Step 7 (the 🛠️ Builder card just
doesn't fire).

On yes:
1. **Make the folder and files.** Create `Projects/my-digest/` and copy the two templates into it:
   `system/templates/my-digest/README.md` and `system/templates/my-digest/routine.md`. Personalize —
   swap `{{name}}` for their name; keep it in their language.
2. **Narrate the lesson, once:** *"Notice it lives in `Projects/my-digest/` — its own folder. Every
   project you build goes under `Projects/`, never loose in the main folder."*
3. **Run it once** so they see it work: follow `Projects/my-digest/routine.md` — read a handful of
   their recent Google Drive files (and today's Calendar events if Calendar is on), and write a short,
   friendly summary to `Projects/my-digest/digest-<YYYY-MM-DD>.md`. Show it to them.
4. Record `Projects/my-digest` as their **first project** (for the profile).

**Fire the 🛠️ Builder card** (rank 3/5). Suggested fill: ✅ *You built your first project — and it
used your real Google data.* · 🔓 *Unlocked: projects are how your work adds up here.* · ➡️ *Next:
make it a one-word command.*

## Step 7 — Your first skill: one word to run it again

Teach how skills work by **using the `create-skill` skill** to wrap what they just built.
**Offer (menu):** *"Want to turn this into a one-word command? Next time just say 'catch me up' and I
run it. `1)` Yes, make it  `2)` Skip for now."* If they skip → go to Step 7a.

On yes:
1. **Invoke `create-skill`** to build `.claude/skills/catch-me-up/`. Inputs are known: name
   `catch-me-up`; trigger phrases in the user's language(s) (e.g. "catch me up" / "что нового" /
   "дай сводку"); what it does — read and follow `Projects/my-digest/routine.md`.
2. **Narrate the lesson, once:** *"Skills are your personal one-word commands — they live in
   `.claude/skills/`. You've got `create-skill` to make more any time."*
3. Offer to test it right away ("try saying 'catch me up'"). Record `catch-me-up` as their **first
   skill**.

**Fire the ⚡ Automator card** (rank 4/5). Suggested fill: ✅ *You turned your project into a one-word
command.* · 🔓 *Unlocked: you can automate anything you repeat.* · ➡️ *Next: I'll finish setting up
your workspace.*

## Step 7a — Optional: tell me a bit more about you (~2 min)

**Offer, don't insist** (their language): *"Optional — give me ~2 minutes on what you do day to day
and I'll be much more useful. Want to? `1)` Sure  `2)` Maybe later."*
- **Yes** → run the **`deepen-profile`** skill (writes a `## Daily work` section into
  `system/profile.md`). Then Step 8.
- **No** → fine; tell them they can say "deepen my profile" any time. Then Step 8.

## Step 8 — Save the profile

Write everything captured into `system/profile.md` (see `system/profile.example.md` for the shape):
name, working language, what they want help with, tools they use, date onboarded, **first project**
(`Projects/my-digest`), **first skill** (`catch-me-up`), the `## Daily work` section if Step 7a was
done, and their final **Rank: 🏆 Champion**.

Say one short line: *"Almost done — let me tidy your workspace, then we celebrate."* Then Step 9.

## Step 9 — Finalize the workspace (you do this yourself, carefully)

**First, tell the user what you're about to do** (their language): *"I'll clean the setup text out of
your workspace files so you're left with a tidy, personal cockpit. I keep a backup, just in case."*

Then finalize **by editing the files yourself** — this needs no script:

1. **Guard — never finalize the master copy.** If a file named **`.canonical`** exists in the kit
   root, **stop finalizing, say nothing about it, and just go to Step 10.** (That file only exists on
   the kit author's copy; a real user's copy doesn't have it.)
2. **Guard — profile filled.** Only proceed if `system/profile.md` has a real name (Step 8 done).
3. **Back up** the originals: copy `CLAUDE.md` and `AGENTS.md` into `system/.preonboard/` (create the
   folder; don't overwrite backups that already exist).
4. In `CLAUDE.md` **and** `AGENTS.md`: **remove the `<!-- ONBOARDING-ONLY -->` … `<!-- /ONBOARDING-ONLY -->`
   block(s)** entirely, then **prepend a personalized header** right after the first `# ` title line,
   built from `system/workspace-header.tmpl.md` (fill `{{name}}`, `{{language}}`, `{{date}}`,
   `{{focus}}`). Keep everything else intact.
5. Don't announce file paths or diffs — just a friendly *"Your workspace is ready."*

**Then fire the 🏆 Champion finale card** (their language), then Step 10.

## Step 10 — Your workspace from here on (the briefing)

Close with a short, warm briefing — **no menu, just tell them**, in their language (a few tight lines):

1. **It's yours and it's clean.** The setup text is gone; this folder is your personal workspace now.
2. **It compounds.** Keep working from this folder — every project and skill you make lives here, so I
   learn more about how *you* work and get faster over time.
3. **One task = one new chat.** Start each new thing in a fresh chat; files it makes go in their own
   folder under `Projects/`.
4. **Back it up to Google Drive.** I recommend putting this folder inside your Google Drive (install
   *Google Drive for Desktop*) so if anything happens to your computer, your workspace is safe. Offer:
   *"Want me to point you to how?"*
5. **Go further when ready:** *"Say 'catch me up' any time. Once a week, say 'level up'. And when you
   want to **edit** Google Sheets & Docs, say 'level up google'."*

End on one encouraging line in their language.
