---
description: Run the 30-question CCAR-F diagnostic baseline, weighted by the real PDF domain weights
argument-hint: "[optional: path-to-CCAR-F-Exam-Guide.pdf, if not already loaded this session]"
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill via `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (project `.claude/skills/` first, then user home `.claude/skills/`) and read it in full.

**PDF gate (mandatory):** follow the "PDF gate" section of that file exactly.
- If the PDF was already read earlier in this conversation, reuse that extraction.
- Else if `$ARGUMENTS` contains a `.pdf` path, read it now (chunk via `pages`, ≤20 pages/call, for files >10 pages) and extract per the SKILL.md gate procedure.
- Else, stop and ask the user for the PDF path — do not proceed.

Once the gate passes, run the `/ccarf-diagnostic` procedure exactly as defined in SKILL.md under "`/ccarf-diagnostic` — 30-question baseline": 30 items split proportionally across the PDF's real domains, delivered 5 at a time, each item grounded in an actual task statement extracted from the PDF, graded live with distractor-class naming, closing with the full diagnostic report template.
