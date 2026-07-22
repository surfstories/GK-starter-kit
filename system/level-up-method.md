# Level up — make your system compound over time

This is the single, agent-neutral method. **Claude** runs it via the `level-up` skill;
**Codex** runs it by reading this file (pointed here from `AGENTS.md`). Interview style:
one question at a time, short answers.

**One run = one shipped artifact.** Find one piece of friction, scope it, build the
smallest thing that removes it. Run it weekly and the system compounds: every week your
setup knows one more trick that fits how *you* work.

**These are yours.** Everything you build here lives on your machine and captures *your* working
style — your personal toolbox, no one else's rules.

---

## Phase 1 — Find the friction (interview)

Ask conversationally, one at a time. Stop early once 1–3 real candidates surfaced:

1. *"Walk me through your week. What did you do 3 or more times?"* (frequency)
2. *"What felt manual, boring, or copy-paste?"* (drudgery)
3. *"What could a smart intern handle if you wrote the steps down once?"* (delegation test)
4. *"If your workload doubled tomorrow, what would break first?"* (bottleneck)

**Output:** a numbered list of 1–3 candidates, one line each on why it's worth automating.
Ask the user to pick ONE. If nothing real surfaced, say so and stop — do not invent work.

## Phase 2 — Scope it

Walk the picked candidate through four gates, in order:

**Gate 1 — Eliminate / Automate / Delegate (in that order).**
- *Eliminate first:* "What happens if you just stop doing this?" If the answer is
  "nothing breaks" — congratulations, that's the win. Log it in `system/decisions.md` and
  exit cheerfully. Don't automate waste.
- *Automate* if the task survives elimination and has repeatable steps.
- *Delegate* if it's judgment-heavy or too variable — suggest a person, log it, exit.

**Gate 2 — Map the process.** Five elements, all required:
trigger (what starts it) · data sources (where info comes from) · transformations (how the
data changes) · decision points (where it branches) · destination (where the output goes).
If the user can't articulate all five: "If you can't explain it to a person, you can't
explain it to an automation. Sketch it first, then come back." Stop.

**Gate 3 — Pick the autonomy level.** Default = the LOWEST level that solves the problem:

| Level | Name | What happens |
|---|---|---|
| L0 | Manual | no automation, maybe a checklist |
| L1 | Suggested | tool suggests, you decide every step |
| L2 | Drafted | tool drafts, you review and send/apply |
| L3 | Supervised | tool runs, you spot-check |
| L4 | Autonomous | tool handles it end to end |

Push back on L3+ for a first build — autonomy is earned through real runs, not granted.

**Gate 4 — Name the number it moves.** Time saved per week, errors avoided, response
speed, revenue touched — one concrete number. If the user can't name one: "If it doesn't
move a number, why build it?" Stop.

**Output:** append the scoped spec to `system/decisions.md` (date, task, the five process
elements, autonomy level, the number). This is the durable record.

## Phase 3 — Build it

Ship the SIMPLEST form that solves it — the user must explicitly ask for more complexity:

1. **Saved prompt** — a reusable prompt the user pastes when needed. Zero moving parts.
2. **Deterministic script** — plain code, no AI step. Best for clear transformation rules.
3. **AI-assisted skill** — a SKILL.md with one AI step (drafting, classifying, summarizing).
4. **Agent** — multi-step reasoning + tools. Last resort.

**Where artifacts go (kit rules):** skills → `.claude/skills/<name>/SKILL.md` · everything else
(project files, any script) → its own folder `Projects/<project-name>/`. Never loose in the root.

**Manual-first rule:** every new artifact starts supervised. Run it by hand, check the
output, and only loosen supervision after several clean runs. Note the current level in
the artifact itself.

## Hard rails

- **Read before you write.** Anything that changes data (files, a connected Google account) starts
  supervised — draft/preview first, the user approves, only then apply. Never touch anything outside
  this folder or a service the user connected without asking.
- **No secrets in the folder.** Never write passwords or keys into any file here.
- **Sharing is optional.** Want to share a skill? Just send someone the `SKILL.md`. Most skills stay
  personal, and that's by design.

## Output contract (every run)

1. One entry in `system/decisions.md` (the scoped spec, or the eliminate/delegate win).
2. One artifact in the right folder (unless the run exited at Eliminate/Delegate — that
   exit is a valid result, not a failure).
3. A three-line close: what was scoped, what was built, and the manual-first reminder.
