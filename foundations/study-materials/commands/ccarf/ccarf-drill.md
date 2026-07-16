---
description: Rapid-fire practice questions on one CCAR-F domain, graded live with trap explanations
argument-hint: "[domain number or name] [optional: path-to-CCAR-F-Exam-Guide.pdf]"
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill via `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (project `.claude/skills/` first, then user home `.claude/skills/`) and read it in full.

**PDF gate (mandatory):** follow the "PDF gate" section of that file exactly.
- If the PDF was already read earlier in this conversation, reuse that extraction.
- Else check `$ARGUMENTS` for a `.pdf` path — if present, read it now (chunk via `pages`, ≤20 pages/call, for files >10 pages) and extract per the SKILL.md gate procedure.
- Else, stop and ask the user for the PDF path — do not proceed.

Once the gate passes, parse `$ARGUMENTS` for a domain number or name (ignore the `.pdf` path token if present). If no domain is given, ask which domain, or default to the learner's currently-weakest 🔴 domain from the last diagnostic/score-check on record this session.

Run the `/ccarf-drill` procedure exactly as defined in SKILL.md under "`/ccarf-drill [domain]` — Single-domain rapid fire": 5-8 original items covering every task statement the PDF lists for that domain, one at a time, graded immediately with the master rule and distractor class named, ending on the learner's weakest task statement in that domain.
