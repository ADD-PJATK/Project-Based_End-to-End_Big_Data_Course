# Additional Assignment 4 (AA4) — AI-Assisted Work Plan Document

**Points:** **4 / 7** (Phase 2 total)  
**Parent:** [Phase 2 overview](./README.md)  
**Deliverable path:** `documentation/ai-work-plan.md` on `main` in `sXXXXX_kafka`

---

## 1. Purpose

Students routinely use **AI coding assistants** (Cursor, GitHub Copilot, ChatGPT, Claude, etc.) on data engineering projects.  
AA4 requires a **written plan** that you (with AI help) produce **before or during** serious implementation work — not a post-hoc excuse, but a **operating manual** for how *you* will use AI safely and effectively on **this course’s ADD project**.

You **should use AI** to help draft and refine this document.  
The document itself must make that usage **transparent** and include **clear rules and precautions**.

---

## 2. Audience and tone

- **Audience:** yourself and your teammates (if any) during Weeks 1–13 of the ADD project.
- **Tone:** professional, concise, **correct technical English**.
- **Length:** **1,200–2,500 words** (excluding tables and templates). Shorter is fine if all mandatory sections are covered with substance.

---

## 3. Mandatory document structure

File: `documentation/ai-work-plan.md`

Use the section headings below (you may add subsections). **All sections are required.**

### 3.1 Title block

- Document title: `AI-Assisted Work Plan — ADD Project`
- Student ID, name, date (last updated)
- Course: Analysis of Large Data Sets (ADD)
- Repository: link to your **main project repo** (not only `sXXXXX_kafka`)

### 3.2 Scope of AI use in this project

State explicitly **where AI is allowed** and **where it is not** for your team, for example:

| Activity | Allowed? | Notes |
|----------|----------|-------|
| Boilerplate code, CLI scaffolding | Yes / No | … |
| Spark / PySpark transformations | Yes / No | … |
| Writing task reports (`documentation/taskNN_*.md`) | Yes / No | … |
| Debugging error messages | Yes / No | … |
| Designing architecture diagrams | Yes / No | … |
| **Runtime** anonymization (AA1 tool) | **No** (per AA1 spec) | … |
| **Grading / exam** individual work | Per course rules | … |

Customize the table for your project; do not leave it empty.

### 3.3 Tools and models

List tools you actually use or plan to use:

- IDE / agent (e.g. Cursor Agent, Copilot, Cody),
- Chat UI (e.g. ChatGPT, Claude),
- Any **local** models.

For each tool, note:

- what it is good for in your workflow,
- data handling (cloud vs local, training on prompts or not — best-effort student research is OK).

### 3.4 Standard workflow (step-by-step)

Describe a **repeatable workflow** you will follow when asking AI for help on a task.  
Minimum **6 steps**, in order. Example shape (adapt):

1. Write a **short human spec** (goal, inputs, outputs, constraints).
2. Paste **only necessary context** (file snippets, schema, not whole repo).
3. Request **plan first**, then code, then tests.
4. **Review** every generated line; run locally.
5. **Document** what changed in the task report.
6. **Commit** with a message that reflects your work, not “AI did everything”.

Your steps must be **specific** to data engineering (paths, tests, data samples).

### 3.5 Prompting rules (what to always include in prompts)

Provide **at least 8 bullet rules** you will follow, such as:

- Always name **file paths** and **language/stack** (PySpark 3.x, Python 3.11, etc.).
- Ask for **idempotent** scripts and explicit **run instructions**.
- Require **error handling** for missing files and empty data.
- Forbid invented libraries or APIs — verify imports exist.
- Ask for **diff-style** or minimal changes when editing existing files.
- State **course constraints** (e.g. “must read from Kafka topic X”, “checkpoint required”).
- Include **acceptance criteria** from the task spec in the prompt.
- End with: “If unsure, ask clarifying questions before coding.”

### 3.6 Precautions and prohibited uses (critical section)

**Minimum 10 distinct precautions**, written as clear **must / must not** rules.  
Include **all** of the following themes (you may merge into fewer bullets if each theme is explicit):

1. **Secrets:** never paste API keys, passwords, `.env` contents, or cloud credentials into AI tools.
2. **Personal data:** do not upload real personal data; use fictional or public datasets only.
3. **Verification:** never merge AI output without running it; “looks correct” is not enough.
4. **Hallucinations:** verify CLI flags, class names, and Spark APIs against official docs.
5. **Licence and attribution:** note when AI-generated blocks need comment or citation in reports.
6. **Team consistency:** one style per repo; AI must not rewrite unrelated files.
7. **Scope creep:** AI must not add features outside the task specification.
8. **Testing evidence:** keep logs, screenshots, or sample outputs proving the pipeline ran.
9. **Academic integrity:** AI assists learning; you remain responsible for understanding and defending the work.
10. **When to stop using AI:** e.g. novel production incident, subtle data leakage, exam conditions.

### 3.7 Task-specific AI plans (ADD project)

For **at least four** course tasks from your project timeline (e.g. Task 03 storage, Task 07 clustering, Task 09 Kafka, Task 10 streaming — pick tasks relevant to **your** repo), provide a short subsection each:

- **Task ID and name**
- **What you will ask AI to do** (2–4 bullets)
- **What you will do yourself without AI** (2–4 bullets)
- **Definition of done** (how you know the task is complete)

### 3.8 Disclosure: how this document was produced with AI

Required honesty section (minimum **150 words**):

- Which AI tool(s) helped draft which sections,
- What prompts you used at a high level (paraphrase, do not paste secrets),
- What you **edited manually** after AI draft,
- What you **rejected** from AI suggestions and why.

### 3.9 Review checklist before every commit

Provide a **markdown checklist** (≥8 items) you will use before pushing, e.g.:

- [ ] I ran the script/notebook end-to-end on a clean path.
- [ ] No secrets in diff.
- [ ] Task report updated in English.
- [ ] …

### 3.10 Revision log

Table with at least **2 rows**:

| Date | Version | Change |
|------|---------|--------|
| YYYY-MM-DD | 0.1 | Initial draft with … |
| YYYY-MM-DD | 1.0 | Added precautions after … |

---

## 4. Explicit prohibitions (document content)

The plan document must **not**:

- Contain real API keys, tokens, or passwords.
- Claim that AI output can be submitted **without human review**.
- Contradict AA1 rule (anonymizer must not call AI at runtime).
- Be a generic essay with no project-specific tasks or paths.

---

## 5. Grading (AA4 — 4 points)

| Points | Criterion |
|--------|-----------|
| **4** | All mandatory sections present with substance; ≥10 precautions; ≥4 task-specific plans; disclosure section honest; English clear; 1,200+ words |
| **3** | One section thin or checklist too generic |
| **2** | Missing task-specific plans or &lt;8 precautions |
| **1** | Template-like, little project linkage |
| **0** | Missing file, wrong path, or academic integrity violation (e.g. copied plan) |

---

## 6. Optional enhancements (not required)

- Mermaid diagram: human → AI → review → commit.
- Appendix: **bad prompt vs good prompt** examples (redacted).
- Link to team’s `.cursor/rules` or `AGENTS.md` if you maintain one.

---

## 7. Suggested use of AI to create this deliverable

You are **encouraged** to:

1. Paste this specification (sections 3.1–3.10) into your AI tool.
2. Ask it to draft `ai-work-plan.md` for your specific ADD project topic.
3. **Edit** every section until it reflects what you will actually do.
4. Add real task numbers and repository paths from your project.

The grade rewards a **usable, honest plan**, not the most polished generic text.

---

*AA4 — AI-assisted work plan document.*
