# CCAR-F Exam Prep Coach — Complete Guide

This is the full end-to-end guide for using the CCAR-F (Claude Certified Architect –
Foundations) exam-prep skill. It covers what the skill does, what it requires, how to run
every command, and how to adapt it. If you just want to get started, jump to §4.

## 1. What this skill does

It turns Claude Code into a personal study coach for the CCAR-F certification exam:
learner profiling, a weighted diagnostic test, a phased study roadmap, weekly schedules,
domain drills, full mock exams, resource pointers, and progress tracking. Every domain,
weight, scenario, and task statement it uses comes from your own official CCAR-F Exam
Guide PDF — nothing is invented or assumed.

## 2. Requirement: the official CCAR-F Exam Guide PDF

This skill will not produce exam facts, domain weights, scenarios, or practice questions
without first reading your actual CCAR-F Exam Guide PDF in the current session. There is no
built-in fallback content. This is deliberate: a study coach that quietly guesses at exam
facts is worse than one that refuses to guess.

Have the PDF saved somewhere on disk and know its path before you start — you'll give that
path to the first command you run.

## 3. Installing it

See [`README.md`](./README.md) for exact install paths, including how to add this skill to
a brand-new project folder that doesn't have it yet. Short version: this `skills/` folder
and a companion `commands/ccarf/` folder both need to exist under either your personal
`~/.claude/` directory (available in every project) or a specific project's `.claude/`
directory (available only there).

## 4. First run

The very first command you run in a session will ask you for the PDF path if you don't
supply it as an argument. You only need to do this once per conversation — every later
command in the same conversation reuses the same extracted PDF content automatically.

```
/ccarf-load-pdf /absolute/path/to/CCAR-F-Exam-Guide.pdf
```

You'll get back a short confirmation: how many domains and scenarios were found, whether
the domain weights sum to 100%, how many task statements were extracted, and the core exam
facts (item count, time limit, passing score, fee). Check this output before continuing —
if a domain came back with zero task statements or the weights don't add up, the PDF may be
malformed or partially unreadable, and it's worth pointing that out before building a study
plan on top of it.

You can skip this step and jump straight to any other command with the PDF path as an
argument instead — e.g. `/ccarf-diagnostic /path/to/guide.pdf` — and it will load the PDF
inline before running.

## 5. Command reference

| Command | Args | What it does |
|---|---|---|
| `/ccarf-load-pdf` | `<path>` (required) | Reads and extracts the Exam Guide PDF for the rest of the session |
| `/ccarf-profile` | `[path]` | 4 quick questions — role, hours/day, weeks to exam — mapped to your PDF's real domains |
| `/ccarf-diagnostic` | `[path]` | 30-item baseline test, weighted by your PDF's real domain weights → scaled score + 🔴🟡🟢 per domain |
| `/ccarf-prep-plan` | `[path]` | Full phased study roadmap (Foundation → Deep Mastery → Simulation) sized to your timeline |
| `/ccarf-weekly-plan` | `[path]` | This week only, day-by-day, hour-by-hour |
| `/ccarf-drill` | `[domain] [path]` | 5-8 rapid-fire questions on one domain, graded live with the trap named |
| `/ccarf-mock` | `[short\|standard\|full] [path]` | Timed exam simulation drawing scenarios from your PDF's real scenario bank |
| `/ccarf-resources` | `[path]` | Study material pointers, mapped to your PDF's real domains and task statements |
| `/ccarf-score-check` | `[path]` | 15-item progress quiz, compared against your last score, with an automatic plan adjustment |

The `[path]` argument is only needed the first time in a conversation, or if you want to
swap in a different PDF mid-session.

**Recommended order for a first pass:**
```
/ccarf-load-pdf <path>   → confirm extraction looks right
/ccarf-profile            → role, hours/day, weeks to exam
/ccarf-diagnostic         → find out where you actually stand
/ccarf-prep-plan          → full roadmap sized to your gaps and timeline
/ccarf-weekly-plan        → this week's schedule
```
From there, cycle through `/ccarf-drill [domain]` and `/ccarf-mock` as you study, and run
`/ccarf-score-check` periodically to see if you're on track.

You don't have to run them in this order — every command works standalone. If you jump
straight to `/ccarf-mock` or `/ccarf-drill` with no profile or diagnostic on record, it
just asks the one or two questions it actually needs (e.g. which domain to drill) instead
of forcing you through the full setup first.

### `/ccarf-load-pdf`
Reads the PDF, chunking automatically for anything over ~10 pages, and reports what it
found. Run this again with a new path if you want to swap PDFs (e.g. a newer version of the
guide) mid-session.

### `/ccarf-profile`
Asks your job title, main responsibilities, study hours per day, and target exam date or
weeks remaining. Uses your answers to flag which of the PDF's real domains you're likely
already strong in versus which need the most work.

### `/ccarf-diagnostic`
A 30-item test split across your PDF's domains in proportion to their real weights (e.g. a
domain worth 27% of the exam gets roughly 27% of the 30 items). Delivered five items at a
time, each item written around an actual task statement from your PDF — never copied from
the PDF's own sample questions. You get immediate ✅/❌ feedback with a one-line rationale
and the name of the reasoning trap if you picked a distractor. Closes with a full score
report: raw score, projected scaled score against your PDF's real passing score, and a
red/yellow/green breakdown per domain.

**Multiple-response ("select TWO/THREE") grading:** all-or-nothing. You need every correct
option and no extra ones to get credit — the same standard the real exam almost certainly
applies.

### `/ccarf-prep-plan`
Builds a full study roadmap using your profile and diagnostic results if you've run them
this session, or a couple of quick self-rated questions if you haven't. Splits your
available hours (daily hours × 7 × weeks) across three phases — Foundation, Deep Mastery,
Exam Simulation — biased toward your weak domains and the PDF's highest-weight domains. If
your available time is very short (a week or less, or under about 5 total hours), it skips
the full roadmap and gives you a triage plan instead, and says plainly that a confident pass
is unlikely on that timeline.

### `/ccarf-weekly-plan`
Just the current week, broken into a day-by-day schedule sized to your daily study hours,
with a mid-week checkpoint quiz and a weekend timed practice set.

### `/ccarf-drill [domain]`
Pick a domain by number or name (or leave it blank and it'll default to your weakest domain
from the last diagnostic or score-check). Generates 5-8 original items covering every task
statement the PDF lists for that domain, one at a time, graded immediately.

### `/ccarf-mock [short|standard|full]`
A timed exam simulation. `short` is 15 items (~20 min), `standard` is 30 items (~40 min),
`full` matches your PDF's real item count and time limit. Scenarios are drawn from your
PDF's real scenario bank in the same proportion the real exam uses. No feedback is given
until you submit — asking for an answer mid-test gets "Not available until you submit."
You can answer one item at a time as you go, or submit everything at once at the end (e.g.
`1-B, 2-AC, 3-D…`) — either works.

The results report breaks your score down by domain and by scenario, tallies which of the
reasoning traps you fell for most, and points you at what to study next. The "scaled score"
in the report is a linear approximation anchored on your PDF's real passing score — useful
for tracking trend, not a guarantee of your actual exam-day score.

### `/ccarf-resources`
Maps your PDF's real domains and task statements to study resources — official Claude Code
docs, Agent SDK/API docs, and Anthropic's public courses. If a task statement doesn't map
cleanly to any of the listed resources, it says so rather than forcing a weak match.

### `/ccarf-score-check`
A 15-item quiz focused on your current weak domains, compared against your last recorded
score this session, with the coming week's plan adjusted based on the result. If you
haven't run a diagnostic yet this session, it's reported as a baseline instead of a
before/after comparison.

## 6. Session memory

Everything the skill knows in a given conversation — the PDF extraction, your profile,
your diagnostic scores, your current phase — lives only in that conversation. Starting a
new chat means starting cold: run `/ccarf-load-pdf` again and give a one-line recap of
where you left off.

To carry progress across sessions without re-loading the PDF every time, use a **Claude
Project**: attach the PDF once in the project's files, paste the Project System Prompt
(bottom of `SKILL.md`) into the project instructions, and every conversation in that project
keeps the same context.

## 7. Customizing this skill

Everything lives in plain Markdown files with YAML frontmatter — no build step.

- **Change what triggers the skill from natural language** (e.g. saying "let's study for
  CCAR-F" without typing a command): edit the `description:` field in `SKILL.md`'s
  frontmatter.
- **Add a new command:** create `commands/ccarf/ccarf-<name>.md` following the pattern of
  the existing nine — frontmatter with `description` / `argument-hint` / `allowed-tools:
  Read, Glob`, then a body that locates `SKILL.md` via `Glob` + `Read`, runs the PDF gate,
  then runs one section of it. Add a matching `##` section to `SKILL.md` and a row to its
  command table.
- **Loosen or change the PDF requirement:** it's defined in `SKILL.md` under "PDF gate —
  mandatory, applies to every command." This is the core guarantee the skill is built
  around — think carefully before weakening it.
- **Point this whole thing at a different exam:** keep the skeleton — mandatory source
  document → a reasoning model (optional but useful: master rules + named distractor
  classes) → one command per study-workflow step, each independently gated on the source
  document → a Project System Prompt for persistent use. Swap every CCAR-F-specific label.

## 8. Known limitations

- **Scenario selection isn't a true random draw.** For `/ccarf-mock`, Claude picks a
  plausible mix of scenarios itself rather than calling a random-number generator. Fine for
  practice; don't treat any single mock's scenario mix as statistically representative.
- **The scaled-score conversion is an approximation**, linearly anchored on your PDF's
  stated passing score. The real exam's actual scoring curve isn't public. Use it to track
  whether you're trending up, not as a literal prediction of your real score.
- **Coverage isn't guaranteed in any single run.** Because items are generated fresh every
  time (to avoid ever reproducing your PDF's actual questions), one `/ccarf-diagnostic` or
  `/ccarf-mock` can't promise to touch every task statement in a large guide. Repeated
  `/ccarf-drill` sessions per domain close this gap over time.
- **Very large or unusually formatted PDFs may need a bit of back-and-forth** — if the
  extraction misses a domain or task statement, just point it out and ask for a re-read of
  that section.
- **Installing to both a personal (`~/.claude/`) and a project-local (`.claude/`) location
  at once** causes commands to show up twice in places that list them. Harmless, but pick
  one location if it bothers you.
