# 🔵 Claude Certified Architect – Professional (CCAR-P)

> The senior, strategic architect credential in the Claude Certification Program. It validates
> that you can **design, build, and deliver production-grade AI solutions** on Claude end to
> end — selecting models and patterns, integrating with enterprise systems, and building in
> **evaluation, security, compliance, and governance** from the start.

[⬅ Back to the main guide](../README.md) · [🏅 Official CCAR-P page](https://anthropic-partners.skilljar.com/claude-certified-architect-professional-certification) · [📄 Exam Guide PDF](study-materials/)

---

## 📋 Exam at a Glance

| Attribute | Detail |
|---|---|
| **Credential** | Claude Certified Architect – Professional |
| **Exam code** | `CCAR-P` |
| **Items** | 63 (multiple-choice **and** multiple-response) |
| **Time** | 120 minutes |
| **Passing score** | **720** on a 100–1,000 scale (criterion-referenced) |
| **Delivery** | Proctored via **Pearson VUE** (online or test center) |
| **Fee** | $175 USD |
| **Prerequisites** | None required; 3+ yrs systems architecture & 6+ mo Claude/LLM in production *recommended* |
| **Validity** | 12 months |

> ℹ️ Facts above are from the official Exam Guide (v1.0, effective July 2026). Always confirm
> against the current [PDF](study-materials/) — the guide is subject to change.

### Foundations vs. Professional — which should you take?

| | 🟢 **Foundations (CCAR-F)** | 🔵 **Professional (CCAR-P)** |
|---|---|---|
| Focus | Hands-on: Agent SDK, MCP, Claude Code internals | Strategic: end-to-end design, integration, governance |
| Structure | 4 of 6 scenarios | 7 weighted domains (no scenario bank) |
| Items / Fee | 60 · $125 | 63 · $175 |
| Adds | — | RAG, evaluation frameworks, compliance (GDPR/HIPAA/FedRAMP), stakeholder & lifecycle management |

There is no mandatory ordering, but Foundations is the natural on-ramp to Professional.

---

## 🗺️ The 7 Content Domains

| # | Domain | Weight | What it tests |
|---|---|:---:|---|
| 1 | **Solution Design & Architecture** | 17% | Business-problem translation, end-to-end design (input→processing→output→feedback), pattern selection (workflow / agentic / augmented-LLM), decomposition, business-value pillars |
| 2 | **Claude Models, Prompting & Context Engineering** | 13% | Model selection by trade-off, system prompts & guardrails, zero/few-shot & CoT, token/context optimization, prompt reuse (caching, modular prompts, Skills) |
| 3 | **Integration** | 19% | **RAG (chunking, indexing, retrieval)**, connection-protocol choice (MCP / API / CLI / agent-to-agent), authn/authz gaps, capability bloat, observability at scale, progressive vs. monolithic context |
| 4 | **Evaluation, Testing & Optimization** | 16% | Metrics (accuracy/latency/cost/safety/security), eval datasets & mixed-method testing, A/B testing, failure diagnosis, cost/latency optimization, observability |
| 5 | **Governance, Safety & Risk Management** | 14% | Guardrails, failure modes, human-in-the-loop validation, compliance (GDPR, HIPAA, FedRAMP), ethical AI (bias, fairness, transparency) |
| 6 | **Stakeholder Communication & Lifecycle Management** | 14% | Structured discovery, communicating trade-offs, SLA/expectation management, architecture documentation, lifecycle phases (discovery→design→handoff→monitoring→iteration) |
| 7 | **Developer Productivity & Operational Enablement** | 7% | Configuring Claude tooling for teams (e.g., Claude Code), improving developer workflows, operational debugging |

---

## 🧠 The Mental Model That Passes This Exam

CCAR-P rewards **architectural judgment under trade-offs** (cost, latency, accuracy, safety,
SLA). These study frameworks — derived from the official sample-question rationales and domain
objectives — capture how correct answers are justified.

**6 Master Principles**
- **P1 — Fix the failing component, not a proxy.** *(RAG returns confident-but-wrong answers
  after a doc refresh → investigate retrieval/indexing, not model weights or temperature.)*
- **P2 — Least privilege; minimize the attack surface.** *(Remove the unneeded tool rather
  than log or confirm its use.)*
- **P3 — Structural optimization beats blunt instruments.** *(Order the static prefix first
  and enable prompt caching, don't truncate context or blindly downsize the model.)*
- **P4 — Proportionate & business-value-aligned.**
- **P5 — Governance & evaluation by design**, not bolted on.
- **P6 — Evidence over intuition** — metrics, eval datasets, and logs over "looks good."

**8 Distractor Classes:** Guard-Instead-of-Remove · Blunt-Instrument Optimization ·
Wrong-Layer Diagnosis · Detective-for-Preventive · Over-Engineering · Capability Bloat ·
Vibes-Based Evaluation · Compliance-as-Afterthought.

> The [prep skill](claude-skills/examprep-guide-skill.md) and
> [prompt packs](prepare-with-prompts/prompt-based-learning.md) teach every concept through
> these principles and name the trap on every wrong answer.

---

## 📦 What's in This Folder

| Path | Contents |
|---|---|
| [`study-materials/`](study-materials/) | Official **CCAR-P Exam Guide** PDF (blueprint, objectives, sample questions) |
| [`claude-skills/`](claude-skills/examprep-guide-skill.md) | `ccar-p-examprep-coach` — a slash-command study coach across all 7 domains (`/diagnostic`, `/mock`, `/drill 1–7`) |
| [`prepare-with-prompts/`](prepare-with-prompts/prompt-based-learning.md) | Three copy-paste Claude Project prompts: **Learning**, **Practice**, **Mock Test** (with a trade-off focus) |

---

## 🚀 How to Prepare (a 3-step path)

1. **Read the blueprint.** Open the [Exam Guide PDF](study-materials/) and self-assess against
   each of the 7 domains' objectives.
2. **Study interactively.** Create a Claude Project, upload the PDF, and either:
   - paste a [prompt pack](prepare-with-prompts/prompt-based-learning.md) (fastest), or
   - install the [`ccar-p-examprep-coach` skill](claude-skills/examprep-guide-skill.md) for a
     repeatable `/profile → /diagnostic → /prep-plan → /mock` workflow.
3. **Build a capstone.** One end-to-end Claude solution that exercises Domains 1, 3, 4, 5, and
   6 at once: a **RAG pipeline** + an **evaluation harness** (metrics + dataset + A/B) +
   **observability** + a **governance layer** (guardrails, HITL, a PII/compliance note), plus a
   one-page architecture doc that communicates the key trade-offs to a non-technical stakeholder.

---

## 📚 Official Resources

| Resource | Use it for |
|---|---|
| [Claude API & Agent SDK docs](https://docs.claude.com) | Domains 1–5 — patterns, model selection, prompt caching, tool use, RAG, Batches API |
| [Claude Code docs](https://code.claude.com/docs/en/overview) | Domains 3 & 7 — MCP, Agent SDK, sub-agents, headless CLI, CI |
| [Anthropic Usage Policy & Trust Center](https://www.anthropic.com/legal/aup) | Domain 5 — governance, safety, and acceptable-use guardrails |
| [Anthropic courses](https://github.com/anthropics/courses) | `prompt-engineering-interactive-tutorial`, `tool-use`, `real-world-prompting` |
| [All Anthropic courses (Skilljar)](https://anthropic.skilljar.com/) | Structured video learning across the ecosystem |

> For Domain 5, also study whichever regulations apply to your industry (GDPR, HIPAA, FedRAMP):
> know **what each constrains** and **where PII and data-residency requirements enter the
> architecture**.

---

<p align="center"><sub>Part of the <a href="../README.md">Claude Certified Architect — Study Guide &amp; Resource Hub</a>.</sub></p>
