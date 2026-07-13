# 🟢 Claude Certified Architect – Foundations (CCAR-F)

> The hands-on, scenario-based entry credential in the Claude Certification Program. It
> validates that you can make sound **tradeoff decisions** when building production systems
> with **Claude Code, the Claude Agent SDK, the Claude API, and MCP**.

[⬅ Back to the main guide](../README.md) · [🏅 Official CCAR-F page](https://anthropic-partners.skilljar.com/claude-certified-architect-foundations-certification) · [📄 Exam Guide PDF](study-materials/)

---

## 📋 Exam at a Glance

| Attribute | Detail |
|---|---|
| **Credential** | Claude Certified Architect – Foundations |
| **Exam code** | `CCAR-F` |
| **Items** | 60 (multiple-choice **and** multiple-response) |
| **Structure** | 4 scenarios drawn at random from a bank of **6** |
| **Time** | 120 minutes |
| **Passing score** | **720** on a 100–1,000 scale |
| **Delivery** | Proctored (online or test center) |
| **Fee** | $125 USD |
| **Validity** | 12 months |

> ℹ️ Facts above are from the official Exam Guide (v1.0, effective July 2026). Always confirm
> against the current [PDF](study-materials/) — the guide is subject to change.

---

## 🗺️ The 5 Content Domains

| # | Domain | Weight | What it tests |
|---|---|:---:|---|
| 1 | **Agentic Architecture & Orchestration** | 27% | Agentic loops (`stop_reason`), coordinator/subagent patterns, the Task tool, hooks, task decomposition, session resume/fork |
| 2 | **Tool Design & MCP Integration** | 18% | Tool descriptions, structured errors (`isError`), tool distribution, `tool_choice`, `.mcp.json` scoping, built-in tools |
| 3 | **Claude Code Configuration & Workflows** | 20% | `CLAUDE.md` hierarchy & `@import`, slash commands, `.claude/rules/` globs, plan vs. direct execution, CI (`-p`, JSON output) |
| 4 | **Prompt Engineering & Structured Output** | 20% | Explicit criteria, few-shot, `tool_use` + JSON schemas, nullable fields, retry-with-feedback, Batches API, multi-pass review |
| 5 | **Context Management & Reliability** | 15% | Summarization risk, case-facts blocks, escalation triggers, error propagation, provenance, confidence calibration |

## 🎬 The 6 Scenarios (4 appear on exam day, at random)

1. **Customer Support Resolution Agent** — Agent SDK + MCP tools; 80%+ first-contact resolution.
2. **Code Generation with Claude Code** — slash commands, `CLAUDE.md`, plan vs. direct execution.
3. **Multi-Agent Research System** — coordinator + search/analyze/synthesize/report subagents.
4. **Developer Productivity with Claude** — Agent SDK, built-in tools, MCP servers.
5. **Claude Code for Continuous Integration** — CI/CD reviews, test generation, PR feedback.
6. **Structured Data Extraction** — `tool_use` + JSON schemas, validation, edge cases.

---

## 🧠 The Mental Model That Passes This Exam

CCAR-F questions reward **practical architectural judgment**, not memorization. Almost every
correct answer follows one of three rules, and almost every wrong answer is a recognizable trap.

**3 Master Rules**
- **R1 — Root cause, not symptom.** Fix what is actually broken.
- **R2 — Deterministic beats probabilistic.** When compliance matters, prefer hooks,
  prerequisite gates, `tool_choice`, and JSON schemas over prose instructions.
- **R3 — Proportionate wins.** The lowest-effort, highest-leverage fix is usually correct;
  ML classifiers and heavy infra "first steps" are traps.

**8 Distractor Classes:** System-Prompt Enforcement · Few-Shot Overload · Over-Engineering ·
Sentiment-Based Escalation · Tool Bloat · Batch API for Blocking Work · Self-Review ·
Text-Signal Loops.

> The [prep skill](claude-skills/examprep-guide-skill.md) and
> [prompt packs](prepare-with-prompts/prompt-based-learning.md) teach every concept through
> these rules and name the trap on every wrong answer.

---

## 📦 What's in This Folder

| Path | Contents |
|---|---|
| [`study-materials/`](study-materials/) | Official **CCAR-F Exam Guide** PDF (blueprint, task statements, sample questions) |
| [`claude-skills/`](claude-skills/examprep-guide-skill.md) | `ccar-f-examprep-coach` — a slash-command study coach (`/diagnostic`, `/mock`, …) aligned to the real blueprint |
| [`prepare-with-prompts/`](prepare-with-prompts/prompt-based-learning.md) | Three copy-paste Claude Project prompts: **Learning**, **Practice**, **Mock Test** |

---

## 🚀 How to Prepare (a 3-step path)

1. **Read the blueprint.** Open the [Exam Guide PDF](study-materials/) and self-assess against
   each domain's task statements.
2. **Study interactively.** Create a Claude Project, upload the PDF, and either:
   - paste a [prompt pack](prepare-with-prompts/prompt-based-learning.md) (fastest), or
   - install the [`ccar-f-examprep-coach` skill](claude-skills/examprep-guide-skill.md) for a
     repeatable `/profile → /diagnostic → /prep-plan → /mock` workflow.
3. **Build the three projects.** An agentic loop with escalation logic; a Claude Code team
   setup (`CLAUDE.md` hierarchy, `.claude/rules/`, a `context: fork` skill, an MCP server);
   and a structured-extraction pipeline (`tool_use` + JSON schema + validation-retry).

---

## 📚 Official Resources

| Resource | Use it for |
|---|---|
| [Claude Code docs](https://code.claude.com/docs/en/overview) | Domains 1–3 & 5 — sub-agents, MCP, `CLAUDE.md`, hooks, plan mode, CLI (`-p`) |
| [Claude API & Agent SDK docs](https://docs.claude.com) | Domains 1, 2, 4 — Messages API, tool use, JSON schemas, Batches API |
| [Anthropic courses](https://github.com/anthropics/courses) | `anthropic-api-fundamentals`, `tool-use`, `prompt-engineering-interactive-tutorial` |
| [All Anthropic courses (Skilljar)](https://anthropic.skilljar.com/) | Structured video learning across the ecosystem |

---

<p align="center"><sub>Part of the <a href="../README.md">Claude Certified Architect — Study Guide &amp; Resource Hub</a>.</sub></p>
