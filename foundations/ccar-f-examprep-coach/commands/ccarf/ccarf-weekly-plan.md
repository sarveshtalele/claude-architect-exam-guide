---
description: Generate this week's day-by-day CCAR-F study schedule
argument-hint: "[optional: path-to-CCAR-F-Exam-Guide.pdf, if not already loaded this session]"
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill via `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (project `.claude/skills/` first, then user home `.claude/skills/`) and read it in full.

**PDF gate (mandatory):** follow the "PDF gate" section of that file exactly.
- If the PDF was already read earlier in this conversation, reuse that extraction.
- Else if `$ARGUMENTS` contains a `.pdf` path, read it now (chunk via `pages`, ≤20 pages/call, for files >10 pages) and extract per the SKILL.md gate procedure.
- Else, stop and ask the user for the PDF path — do not proceed.

Once the gate passes, run the `/ccarf-weekly-plan` procedure exactly as defined in SKILL.md under "`/ccarf-weekly-plan` — This week, day by day". If no prior profile/prep-plan exists in this conversation, ask only for daily hours and current phase (per the fallback rule in SKILL.md) rather than blocking on the full setup flow.
