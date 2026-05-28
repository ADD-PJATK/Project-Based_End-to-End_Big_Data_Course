# Additional Assignment 4 — Secure AI Prompt + Mock Integration App (AA4)

> **Format:** in-class lab session (~90 minutes total)  
> **Tools allowed:** AI coding assistants are **encouraged** (Cursor Agent, Copilot, ChatGPT, Claude, etc.)  
> **Critical constraint:** your prompt and repo must **not** expose any real secrets or sensitive data.

---

## 0. In-class session — what will happen (read this first)

This assignment is **not** a take-home project. You will complete it **during one lab session**, in three phases.

### Phase A — Prepare the repository (~15–20 minutes)

You have **about 15–20 minutes** to prepare your repository on `main`:

- move your previous AA1/AA2/Phase 2 work to a **backup branch** (see Section 4),
- restructure `main` according to this specification,
- add the mock server, client, integration glue, tests, and **intentional bugs**,
- write `documentation/plan-from-grading.md` (based on **your own** Phase 2 feedback — see Section 5).

**Important:** at the end of Phase A your mock app should **not** be fully working yet. It must contain deliberate issues that an AI agent can discover and fix **using only your prompt** (no secrets, no hand-holding like “run my already-fixed app”).

You may use AI during Phase A to scaffold files, but the **graded prompt** is written and run in Phase B.

#### Mandatory Phase A commit (required for submission)

When Phase A time ends, you **must** commit and push your work to `main` **before** writing or running the Phase B prompt.

This commit is the **Phase A snapshot** — the deliberately broken baseline the AI agent is supposed to fix.

**Requirements for this commit:**

- pushed to `origin/main` (or your default remote),
- includes `documentation/plan-from-grading.md`, mock stack, tests, and intentional bugs,
- does **not** yet include the final Phase B prompt run results (no `prompt.md` fixes applied by the agent, or add `prompt.md` only after Phase A if you prefer — but the code state must still be broken),
- commit message should be clear, e.g. `AA4 Phase A: mock baseline with intentional bugs`.

**Save the commit URL** — you will submit it in MS Teams (see Section 12).

The instructor uses this commit to verify that your repo was genuinely broken before the one-shot agent run (bonus eligibility).

---

### Phase B — Write and run your prompt (~30 minutes)

When Phase A ends, you must:

1. Write **`documentation/prompt.md`** — a single, high-quality prompt as close to **ideal** as you can make it.
2. **Run that prompt once** in your AI coding agent (one submission / one agent run — not a chain of follow-ups for the bonus).
3. Let the agent work. Do **not** manually fix the code yourself during this phase if you want the **bonus** (see grading).

Your prompt must be **self-contained and actionable**. It must tell the AI:

- how to install dependencies and run the mock stack offline,
- where to look first (paths, tests, fixtures),
- what “done” means (acceptance checklist),
- how to diagnose failures (run tests, read logs, inspect SSE parsing, etc.),
- safety rules (no secrets, no external API, anonymizer is deterministic).

**Anti-cheat rule:** the instructor will review **both** the final app **and** the prompt. If you spend Phase A building a fully working app and your prompt is essentially *“run the application”*, you will **not** receive the one-prompt bonus — even if the app works. The prompt must contain real engineering guidance, not a trivial launcher.

---

### Phase C — Discussion (~remaining time)

After you start the agent run:

1. **Take a chair and sit in the centre of the room.**
2. We will hold a **group discussion** about **defending your main ADD project** in the upcoming semester (what to prepare, what questions to expect, how to demonstrate reproducibility, etc.).

This discussion is part of the session. Participation is expected.

---

### Instructor check — 30 minutes after you run the prompt

**30 minutes after you launch your prompt**, the instructor will walk around and check:

- whether the agent run has **finished**,
- whether your mock integration **works end-to-end** (mock server → client → export → anonymizer → passing tests),
- whether your **prompt quality** is genuine (not a placeholder).

| Outcome | Points |
|---------|--------|
| Assignment completed during the session (working mock + integration + evidence) | **up to 10 / 10** (see Section 10) |
| **Bonus:** working app after **one** high-quality prompt (instructor verified) | **+5 extra points** |

You may use **multiple prompts** during the session to reach the base **10 / 10**. Only the **single-prompt success** qualifies for the **+5 bonus**.

If your agent is still running when the instructor visits, wait — do not hide a broken state. Be ready to show logs and `documentation/ai-fix-log.md`.

---

## 1. What this assignment connects

This assignment reuses and connects your earlier work:

| Earlier work | Original spec |
|--------------|---------------|
| **AA1** — Local Data Anonymizer | `additional-assignment-data-anonymization/` |
| **AA2** — Kafka / SSE Stock Apps | `additional-assignment-kafka-stocks/` |
| **Phase 2** — Unified repo + AI work plan | `additional-assignments-phase2/` |

**New skill:** use AI **safely and effectively** to debug an integration **without exposing sensitive data** — only an anonymized plan + a local mock environment + a strong prompt.

---

## 2. High-level goal

On `main` in `sXXXXX_kafka` you deliver:

1. **`documentation/plan-from-grading.md`** — your Phase 2 feedback turned into a concrete mock/test plan (sanitized).
2. **`documentation/prompt.md`** — the exact one-shot prompt for Phase B.
3. **Mock integration stack** — local offline substitute for the instructor stock API + pipeline into your anonymizer.
4. **`documentation/ai-fix-log.md`** — evidence of failures, fixes, and final success (filled in after Phase B).
5. **Tests / demo script** — reproducible pass/fail signal.

Everything must run **offline** (localhost only). No calls to `add.piotrkojalowicz.dev` or external Kafka.

---

## 3. Safety rules (mandatory)

Your repo and prompt must **not** contain:

- real API keys, tokens, passwords, or `.env` secrets,
- real personal data,
- private URLs or credentials from the instructor service.

Use only:

- **synthetic / fictional fixtures**,
- a **local mock SSE + REST server**,
- your **AA1 anonymizer** with deterministic local replacements (no AI at runtime).

---

## 4. Repository — use `sXXXXX_kafka` (not a new repo)

**Do not create a new repository.**

Continue in your existing Phase 2 repo:

- **Name:** `sXXXXX_kafka` (same as AA2)
- **Graded branch:** `main`

### Step 1 — Preserve your previous work

Before changing `main`, push everything you built so far to a **backup branch**, for example:

```bash
git checkout main
git pull
git checkout -b backup/pre-aa4-YYYY-MM-DD
git push -u origin backup/pre-aa4-YYYY-MM-DD
```

Use any branch name that makes sense. The requirement is: **your old AA1 + AA2 + Phase 2 state must remain reachable on the remote**, not only on your laptop.

### Step 2 — Restructure `main` for AA4

Check out `main` again and reshape it for this assignment. Recommended layout:

```text
sXXXXX_kafka/                     ← same repo; main = AA4 submission
├── README.md                     ← quick-start for mock stack + link to docs
├── .gitignore
├── documentation/
│   ├── prompt.md                 ← Phase B: your one-shot agent prompt
│   ├── plan-from-grading.md      ← Phase A: plan from your Phase 2 feedback
│   ├── ai-fix-log.md             ← Phase B/C: evidence + reflection
│   └── ai-chat/                  ← full AI conversation export(s) + README
├── anonymizer/                   ← AA1 code (reuse from backup branch)
├── kafka-stocks/                 ← optional: keep AA2 apps here OR on backup only
├── mock/
│   ├── server/                   ← local GET /api/tickers, /latest, /stream (SSE)
│   ├── client-dashboard/         ← minimal UI or CLI consumer
│   └── fixtures/                 ← synthetic ticks + fictional sensitive fields
├── integration/
│   ├── pipeline/                 ← stream → export → anonymize → out/
│   └── tests/                    ← must fail before Phase B fixes; pass after
└── scripts/
    ├── run_mock.sh               ← (or .ps1 / Makefile targets)
    ├── run_tests.sh
    └── demo.sh                   ← one command proving end-to-end success
```

**Rules:**

- `main` must match this assignment’s structure closely enough that the instructor can run `scripts/demo.sh` (or your documented equivalent).
- AA1 anonymizer code must be present under `anonymizer/` (copy from your backup branch if needed).
- AA2 apps may stay on the backup branch only, **or** remain under `kafka-stocks/` if paths are documented — but **grading focuses on the mock integration**, not the live instructor API.

---

## 5. Plan from your Phase 2 feedback (mandatory)

File: `documentation/plan-from-grading.md`

You must base this document on **your own Phase 2 grading feedback** — what you scored, what was missing, what the instructor commented on (AA3 integration, anonymizer, AI work plan, README gaps, etc.).

**The instructor will not publish individual results in the course Git repository.** You are expected to remember or note your feedback from:

- the returned Phase 2 grade / report,
- in-class comments,
- or your own notes from the earlier submission.

In the document (sanitized — no secrets):

- summarize your Phase 2 outcome in **your own words**,
- list concrete weaknesses you will simulate in the mock (e.g. wrong paths, missing README steps, SSE parsing, mapping format, test flakiness),
- define what you will mock and what tests will prove success,
- list **at least 5 anticipated failure modes** and how to detect each one.

Do **not** paste instructor CSV files or private grading URLs. A short bullet summary is enough if it maps clearly to your mock design.

---

## 6. The prompt — `documentation/prompt.md` (mandatory)

This file must contain the **exact text** you paste into your AI agent at the start of Phase B.

The prompt must enable the agent to:

1. install dependencies and start the mock stack locally,
2. run tests / demo and observe failures,
3. locate and fix bugs with **minimal, focused changes**,
4. re-run tests and confirm end-to-end success,
5. update `documentation/ai-fix-log.md` with evidence.

### Minimum content in the prompt

| Topic | Required |
|-------|----------|
| Stack and versions | e.g. Python 3.11 + FastAPI, Node 20 + Express |
| Repository layout | key folders and entry points |
| Run commands | install, start server, start client, run tests, run demo |
| Acceptance checklist | explicit “done when …” criteria |
| Safety constraints | no secrets; offline only; anonymizer deterministic |
| Debugging playbook | run tests first, read logs, inspect SSE `data:` lines, check paths |
| Scope limit | fix only what is needed; do not rewrite unrelated files |

### Prompts that will **not** earn the bonus

Examples of **insufficient** prompts:

- “Run the app.”
- “Fix everything.”
- “Make tests pass.” (with no paths, commands, or criteria)
- “Use my API key …” (secrets — also a safety violation)

The instructor compares prompt quality against the state of the repo at the end of Phase A.

---

## 7. Mock integration — technical requirements

### 7.1 Mock server (local)

Implement on `localhost`:

| Endpoint | Behaviour |
|----------|-----------|
| `GET /api/tickers` | synthetic ticker list |
| `GET /api/latest?ticker=...` | latest tick(s) from fixtures or generator |
| `GET /api/stream?ticker=...` | SSE stream of synthetic ticks |

Any language/framework is fine.

### 7.2 Consumer

A minimal **web dashboard** or **CLI** that:

- connects to the mock stream,
- shows live updates (ticker, price, timestamp at minimum),
- buffers the last **N** ticks (document N),
- exports JSON or CSV.

### 7.3 Integration + anonymizer

Pipeline under `integration/` that:

- consumes streamed or exported data,
- writes a file suitable for anonymization (include fictional sensitive fields: `trader_email`, `operator_name`, `comment`, etc.),
- runs your **AA1 anonymizer** with a valid mapping (`find[]` → `replace`),
- writes output under `out/` (or documented path).

### 7.4 Intentional bugs (Phase A)

Include **at least 3 deliberate issues** on `main` before Phase B, for example:

- broken relative path (works only from one directory),
- incorrect SSE parsing,
- wrong field name in test assertion,
- broken script command in README,
- anonymizer mapping mismatch,
- race: tests start before server is ready,
- CSV quoting / delimiter bug.

Document the fixes **after** Phase B in `documentation/ai-fix-log.md` — not in the prompt as a cheat sheet.

---

## 8. Evidence — `documentation/ai-fix-log.md`

After Phase B (and any further work during the session), include:

- initial failure output (test logs / terminal),
- summary of what the agent changed,
- final passing evidence (`run_tests.sh` / `demo.sh` output),
- 5–10 sentences: what you learned about prompting and debugging.

You may paraphrase the AI conversation. No secrets.

---

## 9. Deliverables checklist

- [ ] Backup branch pushed with pre-AA4 work
- [ ] `main` restructured per Section 4
- [ ] `documentation/plan-from-grading.md`
- [ ] **Phase A commit** pushed before Phase B prompt (URL saved for MS Teams)
- [ ] `documentation/prompt.md` (Phase B one-shot text)
- [ ] `documentation/ai-fix-log.md`
- [ ] **`documentation/ai-chat/`** — full AI conversation history from this assignment (see Section 12)
- [ ] Mock server + consumer + integration + anonymizer
- [ ] ≥ 3 intentional bugs + tests that fail then pass
- [ ] `README.md` quick-start (1–5 commands)
- [ ] `.gitignore`; no secrets on `main`

Full checklist: [ACCEPTANCE.md](./ACCEPTANCE.md).

---

## 12. Submission via MS Teams (two links)

Submit **two links** in the MS Teams assignment for AA4:

| # | What to submit | Example |
|---|----------------|---------|
| **1** | **Phase A commit URL** — permanent link to the commit you pushed at the end of Phase A (baseline with intentional bugs, **before** the agent fixes) | `https://github.com/ADD-PJATK/s12345_kafka/commit/abc123...` |
| **2** | **Repository URL** — link to `sXXXXX_kafka` on `main` with the **final state** after the session | `https://github.com/ADD-PJATK/s12345_kafka` |

Both links are **mandatory**. Missing either link → submission incomplete (may receive **0** or reduced score).

### What must be in the repository (Link 2)

The repo on `main` must contain, in addition to the working (or attempted) mock stack:

- `documentation/prompt.md`
- `documentation/ai-fix-log.md`
- **`documentation/ai-chat/`** — the **complete AI chat history** for this assignment

You may use **any technical export format** you can produce from your tool, for example:

- Cursor / VS Code agent transcript (`.json`, `.jsonl`, `.md`),
- ChatGPT / Claude “export conversation” (`.json`, `.html`, `.md`),
- Copilot chat log,
- a single consolidated `documentation/ai-chat/session.md` if you copy-paste manually.

**Rules for the chat export:**

- must cover **Phase A scaffolding** (if AI was used) **and** the **Phase B agent run** (and any follow-up prompts if you used more than one),
- must **not** contain API keys, passwords, or other secrets (redact before committing if needed),
- add a one-line `documentation/ai-chat/README.md` stating which tool produced which file(s).

The instructor will compare Link 1 (Phase A commit) with Link 2 (final repo + chat) to grade prompt quality, bonus eligibility, and academic integrity.

---

## 10. Grading (10 points + up to 5 bonus)

### Base score — **10 points** (completable during the session)

Awarded if, by the end of the lab, your submission on `main` satisfies [ACCEPTANCE.md](./ACCEPTANCE.md):

| Points | Criterion |
|-------:|-----------|
| 2 | Repo layout on `main`; backup branch exists; README quick-start |
| 2 | `plan-from-grading.md` — realistic plan tied to your Phase 2 feedback |
| 2 | `prompt.md` — safe, detailed, actionable (even if bonus not achieved) |
| 2 | Mock server + consumer + integration + anonymizer work offline end-to-end |
| 2 | ≥ 3 bugs, tests fail→pass, `ai-fix-log.md` with evidence |

Partial credit is possible (e.g. 6/10 if mock works but prompt/plan are weak).

You may use **any number of prompts** to reach **10 / 10**.

### Bonus — **+5 points** (one prompt only)

Extra **5 points** if **all** of the following are true:

1. Your mock integration **works end-to-end** after **exactly one** agent run using `documentation/prompt.md` (no follow-up prompts for the bonus).
2. The instructor verifies prompt **quality** — it is not a trivial “run app” instruction.
3. Phase A repo state contained real bugs that the prompt genuinely helps the agent find.

**Maximum possible:** **15 / 15** (10 base + 5 bonus).

---

## 11. Academic integrity

- Reuse your **own** AA1/AA2 code from the backup branch.
- You are responsible for understanding what is on `main` and what the agent changed.
- No secrets on `main` or in `documentation/ai-chat/`. Anonymizer must not call AI or HTTP at runtime.
- The **Phase A commit** and **AI chat export** must match what actually happened — do not fabricate logs.
- Misrepresenting a pre-fixed app as “broken” to game the bonus will result in **loss of bonus and possible base-point deduction**.
- Submitting a repo without chat history, or a Phase A commit taken **after** the agent already fixed the code, is treated as an integrity issue.

---

*AA4 — Secure AI prompt + mock integration (in-class session).*
