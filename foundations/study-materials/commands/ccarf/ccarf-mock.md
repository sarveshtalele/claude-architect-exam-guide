---
description: Run a timed, exam-style CCAR-F mock test across the PDF's real scenario bank
argument-hint: "[short|standard|full] [optional: path-to-CCAR-F-Exam-Guide.pdf]"
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill via `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (project `.claude/skills/` first, then user home `.claude/skills/`) and read it in full.

**PDF gate (mandatory):** follow the "PDF gate" section of that file exactly.
- If the PDF was already read earlier in this conversation, reuse that extraction.
- Else check `$ARGUMENTS` for a `.pdf` path — if present, read it now (chunk via `pages`, ≤20 pages/call, for files >10 pages) and extract per the SKILL.md gate procedure.
- Else, stop and ask the user for the PDF path — do not proceed.

Once the gate passes, parse `$ARGUMENTS` for a mode (`short`, `standard`, or `full`; ignore the `.pdf` path token if present). If no mode is given, default to `short` and say so explicitly.

Run the `/ccarf-mock` procedure exactly as defined in SKILL.md under "`/ccarf-mock [short|standard|full]` — Exam simulation": draw scenarios from the PDF's real scenario bank, distribute items by the PDF's real domain weights, give no feedback until the learner submits, then produce the full mock results report with per-domain, per-scenario, and distractor-class breakdowns.
