---
description: Load/refresh the official CCAR-F Exam Guide PDF for this session (required before any other ccarf command produces real content)
argument-hint: <absolute-path-to-CCAR-F-Exam-Guide.pdf>
allowed-tools: Read, Glob
---

Locate the CCAR-F exam-prep skill by using `Glob` for `**/skills/ccar-f-examprep-coach/SKILL.md` (check the current project's `.claude/skills/` first, then the user's home `.claude/skills/`). Read that file in full — it defines the PDF gate procedure, the domain model, the master reasoning rules, and the distractor classes this whole skill relies on.

Then run the `/ccarf-load-pdf` procedure exactly as defined in that file's "`/ccarf-load-pdf` — Load / refresh the Exam Guide" section, using `$ARGUMENTS` as the PDF path.

If `$ARGUMENTS` is empty, ask the user for the absolute path to their CCAR-F Exam Guide PDF (or ask them to attach it) and stop — do not proceed without a real path.

If the path is given, read it with the `Read` tool. PDFs longer than ~10 pages must be read in chunks using the `pages` parameter (max 20 pages per call) — issue as many `Read` calls as needed to cover the whole document. Extract and report per the SKILL.md template: domain count and whether weights sum to ~100%, scenario count, total task statements extracted, and the core exam facts (item count, time limit, passing score, fee). Flag anything that looks incomplete or inconsistent rather than silently smoothing it over.
