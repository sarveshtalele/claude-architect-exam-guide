# CCAR-F Exam Prep Coach — portable install package

Everything needed to run a CCAR-F (Claude Certified Architect – Foundations) exam-prep
coach in Claude Code lives in this one folder. Download it, then follow the two-step copy
below — that's the whole install.

**Requires your own official CCAR-F Exam Guide PDF.** This skill will not invent exam
facts, domain weights, or practice questions — every command refuses to run until a real
PDF has been read in that session. There is no bundled or memorized fallback content.

## What's in this folder

```
ccar-f-examprep-coach/
  SKILL.md                      the full spec: PDF gate, domain model, all 9 commands
  USAGE_GUIDE.md                complete end-to-end guide: every command, how to customize
  README.md                     this file
  commands/ccarf/                9 command files, nested here just for a tidy single download
    ccarf-load-pdf.md
    ccarf-profile.md
    ccarf-diagnostic.md
    ccarf-prep-plan.md
    ccarf-weekly-plan.md
    ccarf-drill.md
    ccarf-mock.md
    ccarf-resources.md
    ccarf-score-check.md
```

Claude Code uses two separate mechanisms here, and they read from two separate
directories on your machine — that's a Claude Code requirement, not a choice made by this
package:
- **Skill** (`SKILL.md` + `USAGE_GUIDE.md`) — the brain. Holds the PDF gate, the domain
  model, the master reasoning rules, and the exact template for every command. Must live
  under a `skills/` directory. Also auto-triggers from plain language ("let's start CCAR-F
  prep") even without typing a command.
- **Commands** (`commands/ccarf/*.md`) — the doorbells. Each is a short file that locates
  and reads `SKILL.md` at runtime, then runs one section of it. These make `/ccarf-profile`,
  `/ccarf-mock`, etc. work as real slash commands from a cold conversation. Must live under
  a `commands/` directory — nested one level down inside this folder just so the whole
  package is one download, not because Claude Code reads it from there directly.

## Install — two copies, one for each directory Claude Code actually reads

**Personal (available in every project on your machine) — pick a destination:**

Windows (PowerShell):
```powershell
# 1. the skill itself
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills\ccar-f-examprep-coach"
Copy-Item ".\ccar-f-examprep-coach\SKILL.md",".\ccar-f-examprep-coach\USAGE_GUIDE.md",".\ccar-f-examprep-coach\README.md" "$env:USERPROFILE\.claude\skills\ccar-f-examprep-coach\"

# 2. the commands (note: different destination, and commands/ccarf drops one level)
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\commands\ccarf"
Copy-Item ".\ccar-f-examprep-coach\commands\ccarf\*" "$env:USERPROFILE\.claude\commands\ccarf\"
```

macOS/Linux (bash):
```bash
# 1. the skill itself
mkdir -p ~/.claude/skills/ccar-f-examprep-coach
cp ccar-f-examprep-coach/SKILL.md ccar-f-examprep-coach/USAGE_GUIDE.md ccar-f-examprep-coach/README.md ~/.claude/skills/ccar-f-examprep-coach/

# 2. the commands (note: different destination, and commands/ccarf drops one level)
mkdir -p ~/.claude/commands/ccarf
cp ccar-f-examprep-coach/commands/ccarf/* ~/.claude/commands/ccarf/
```

**Project-only instead** (available just inside one repo, shareable via version control):
run the same two copies but target `<project-root>/.claude/skills/ccar-f-examprep-coach/`
and `<project-root>/.claude/commands/ccarf/` instead of the `~/.claude/...` paths.

**If you only do step 1 and skip step 2:** the skill still works — it'll auto-trigger from
plain language like "let's start CCAR-F prep" — but the `/ccarf-*` slash commands won't be
registered, and typing them will show "Unknown command."

**After copying:** start a new Claude Code session (custom commands are only picked up at
session start, not mid-session) and run `/ccarf-load-pdf <path-to-your-exam-guide.pdf>` to
confirm it's working.

No build step, no dependencies. It's plain Markdown; any text editor can modify it.

## Quick start (after install)

1. Get your official CCAR-F Exam Guide PDF onto disk.
2. `/ccarf-load-pdf /absolute/path/to/CCAR-F-Exam-Guide.pdf`
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
