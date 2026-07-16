# CCAR-F Exam Prep Coach — portable install package

This folder plus its companion `commands/ccarf/` folder are everything needed to run a
CCAR-F (Claude Certified Architect – Foundations) exam-prep coach in Claude Code, on any
machine, for any user.

**Requires the learner's own official CCAR-F Exam Guide PDF.** This skill will not invent
exam facts, domain weights, or practice questions — every command refuses to run until a
real PDF has been read in that session. There is no bundled or memorized fallback content.

## What's in this package

```
ccar-f-examprep-coach/          ← this folder (a Claude Code "skill")
  SKILL.md                      the full spec: PDF gate, domain model, all 9 commands
  USAGE_GUIDE.md                complete end-to-end guide: every command, how to customize
  README.md                     this file

commands/ccarf/                 ← ships alongside, NOT inside the skill folder
  ccarf-load-pdf.md             registers /ccarf-load-pdf
  ccarf-profile.md              registers /ccarf-profile
  ccarf-diagnostic.md           registers /ccarf-diagnostic
  ccarf-prep-plan.md            registers /ccarf-prep-plan
  ccarf-weekly-plan.md          registers /ccarf-weekly-plan
  ccarf-drill.md                registers /ccarf-drill
  ccarf-mock.md                 registers /ccarf-mock
  ccarf-resources.md            registers /ccarf-resources
  ccarf-score-check.md          registers /ccarf-score-check
```

Two different Claude Code mechanisms, working together:
- **Skill** (`ccar-f-examprep-coach/SKILL.md`) — the brain. Holds the PDF gate, the domain
  model, the master reasoning rules, the distractor classes, and the exact template for
  every command. Also auto-triggers from plain language ("let's start CCAR-F prep") even
  without typing a command.
- **Commands** (`commands/ccarf/*.md`) — the doorbells. Each is a short file that locates
  and reads `SKILL.md` at runtime, then runs one section of it. These are what make
  `/ccarf-profile`, `/ccarf-mock`, etc. work as real slash commands from a cold conversation
  — no need to trigger the skill by name first.

## Install (pick one)

**Personal — available in every project on this machine:**
```
~/.claude/skills/ccar-f-examprep-coach/   ← copy this whole folder here
~/.claude/commands/ccarf/                 ← copy this whole folder here
```

**Project-only — available just inside one repo, and shareable via version control:**
```
<project-root>/.claude/skills/ccar-f-examprep-coach/
<project-root>/.claude/commands/ccarf/
```

Don't install to both locations for the same project — Claude Code will register the
commands twice (harmless, just shows duplicate entries in places that list available
commands/skills).

No build step, no dependencies. It's plain Markdown; any text editor can modify it.

## Add this to a new project you haven't set up yet

If you're in a project folder where Claude doesn't yet recognize `/ccarf-*` commands (or
any Claude Code skill/command at all), here's the exact fix.

**Check first — does the folder structure already exist?**

Windows (PowerShell):
```powershell
Test-Path "$env:USERPROFILE\.claude\skills\ccar-f-examprep-coach"
Test-Path "$env:USERPROFILE\.claude\commands\ccarf"
```
macOS/Linux:
```bash
ls ~/.claude/skills/ccar-f-examprep-coach ~/.claude/commands/ccarf
```
If both exist and contain files, the skill is already installed personally (available in
every project) — the issue is likely just that Claude Code needs the folders to have
existed before the session started, or the commands are project-scoped elsewhere. Restart
your Claude Code session and try again.

**If they don't exist, copy this package in. Personal install (recommended — works in every
project from then on):**

Windows (PowerShell):
```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills\ccar-f-examprep-coach"
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\commands\ccarf"
Copy-Item "<source-path>\ccar-f-examprep-coach\*" "$env:USERPROFILE\.claude\skills\ccar-f-examprep-coach\" -Recurse -Force
Copy-Item "<source-path>\commands\ccarf\*" "$env:USERPROFILE\.claude\commands\ccarf\" -Force
```
macOS/Linux (bash):
```bash
mkdir -p ~/.claude/skills/ccar-f-examprep-coach ~/.claude/commands/ccarf
cp -r <source-path>/ccar-f-examprep-coach/* ~/.claude/skills/ccar-f-examprep-coach/
cp <source-path>/commands/ccarf/* ~/.claude/commands/ccarf/
```
Replace `<source-path>` with wherever you have this package sitting (e.g. a cloned repo, a
downloaded zip, or another project that already has it installed).

**Project-only install instead** (so it only works inside one specific repo, and can be
committed to version control so teammates get it automatically on `git pull`): run the same
copy commands but target `<project-root>/.claude/skills/ccar-f-examprep-coach/` and
`<project-root>/.claude/commands/ccarf/` instead of the `~/.claude/...` paths.

**Verify it worked:** start a new Claude Code session in the target folder/project and type
`/ccarf-load-pdf` — you should see it prompt for a PDF path rather than say "Unknown
command." If it still doesn't register, double check the two folders above both exist and
contain the `.md` files (nine command files, plus `SKILL.md`/`USAGE_GUIDE.md`/`README.md` in
the skill folder) — a skill with no commands folder, or a commands folder with no skill,
will not work correctly on its own.

## Quick start

1. Get your official CCAR-F Exam Guide PDF onto disk somewhere you can give Claude an
   absolute path to it.
2. In Claude Code: `/ccarf-load-pdf /absolute/path/to/CCAR-F-Exam-Guide.pdf`
3. `/ccarf-profile` → answer the 4 questions.
4. `/ccarf-diagnostic` → 30-question baseline, weighted by the PDF's real domains.
5. `/ccarf-prep-plan` → full roadmap. `/ccarf-weekly-plan` → this week only.
6. `/ccarf-drill [domain]`, `/ccarf-mock [short|standard|full]`, `/ccarf-score-check` as you
   go. `/ccarf-resources` any time for study material pointers.

Every command re-runs the PDF check automatically — if you skip step 2, the next command
you run will ask for the PDF path itself before doing anything else.

## Full details

See [`USAGE_GUIDE.md`](./USAGE_GUIDE.md) for the complete end-to-end guide: every command
explained in detail, session-memory behavior, known limitations, and how to customize this
for a different exam entirely.
