---
description: 15-question CCAR-F progress quiz with automatic plan adjustment
argument-hint: "[optional: path-to-CCAR-F-Exam-Guide.pdf, if not already loaded this session]"
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill via `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (project `.claude/skills/` first, then user home `.claude/skills/`) and read it in full.

**PDF gate (mandatory):** follow the "PDF gate" section of that file exactly.
- If the PDF was already read earlier in this conversation, reuse that extraction.
- Else if `$ARGUMENTS` contains a `.pdf` path, read it now (chunk via `pages`, ≤20 pages/call, for files >10 pages) and extract per the SKILL.md gate procedure.
- Else, stop and ask the user for the PDF path — do not proceed.

Once the gate passes, run the `/ccarf-score-check` procedure exactly as defined in SKILL.md under "`/ccarf-score-check` — Progress quiz & plan adjustment": 15 items focused on the learner's weak domains, compared against their last recorded score this session, closing with the progress report and a plan adjustment. If no prior score exists this session, report this as a baseline rather than fabricating a delta.
