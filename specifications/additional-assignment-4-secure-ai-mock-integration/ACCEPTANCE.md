# AA4 — Secure AI Prompt + Mock Integration App — Acceptance Checklist

Used to grade **in-class Additional Assignment 4 (AA4)**.

**Repository:** `sXXXXX_kafka`  
**Graded branch:** `main`  
**Backup branch:** required (pre-AA4 work preserved on remote)

---

## A. Safety and offline operation (must-pass)

- [ ] No secrets on `main` (`.env`, API keys, tokens, passwords).
- [ ] No real personal data — only synthetic / fictional fixtures.
- [ ] Solution runs **offline** (no instructor API, no external Kafka).
- [ ] Network use limited to **localhost**.

Failure in this section → grade may be **0** regardless of other work.

---

## B. Repository hygiene

- [ ] Student uses existing repo **`sXXXXX_kafka`** (no new repo for AA4).
- [ ] Pre-AA4 state pushed to a **backup branch** on the remote.
- [ ] `main` restructured for AA4 (mock + integration + docs + scripts).
- [ ] AA1 anonymizer code present under `anonymizer/` (or documented equivalent).
- [ ] **Phase A commit** pushed before Phase B prompt; commit URL submitted in MS Teams.
- [ ] **MS Teams submission:** two links — (1) Phase A commit, (2) repository URL.

---

## B2. MS Teams submission (mandatory)

- [ ] **Link 1:** permanent GitHub commit URL for Phase A baseline (intentional bugs, before agent fixes).
- [ ] **Link 2:** repository URL pointing to final `main` after the session.
- [ ] Repo contains **`documentation/ai-chat/`** with full AI conversation history (any export format).
- [ ] `documentation/ai-chat/README.md` (or equivalent) names tool and file(s).
- [ ] Chat export contains no secrets (redacted if necessary).
- [ ] Chat covers Phase B agent run (and Phase A AI use if applicable).

Missing Link 1 or Link 2 → treat as **incomplete submission**.

---

## C. Required documents

### `documentation/plan-from-grading.md`

- [ ] Based on the student’s **own Phase 2 feedback** (not copied from a shared Git results folder).
- [ ] Sanitized summary of strengths/weaknesses.
- [ ] Concrete mock/test plan derived from that feedback.
- [ ] ≥ 5 anticipated failure modes with detection method.

### `documentation/prompt.md`

- [ ] Exact one-shot prompt text for Phase B.
- [ ] Run commands (install, start, test, demo).
- [ ] Acceptance checklist for the agent.
- [ ] Safety constraints (no secrets, offline, deterministic anonymizer).
- [ ] Sufficient detail for an agent to debug without trivial “run app” instructions.
- [ ] No sensitive data.

### `documentation/ai-fix-log.md`

- [ ] Initial failure evidence (logs / test output).
- [ ] Summary of fixes (high-level).
- [ ] Final success evidence (passing tests / demo output).
- [ ] Short reflection (5–10 sentences).

---

## D. Mock system

### Mock server

- [ ] `GET /api/tickers` — synthetic list.
- [ ] `GET /api/latest?ticker=...` — latest tick(s).
- [ ] `GET /api/stream?ticker=...` — SSE stream.
- [ ] Fixtures or local generator committed.

### Consumer

- [ ] Connects to mock stream.
- [ ] Live updates visible (UI or CLI).
- [ ] Buffers last N ticks (N documented).
- [ ] Exports JSON or CSV.

### Integration + AA1

- [ ] Pipeline: stream/export → anonymizer → `out/` (or documented path).
- [ ] Fictional sensitive fields in fixtures.
- [ ] Mapping format: many `find` → one `replace`.
- [ ] Anonymizer: local, deterministic, **no AI/HTTP at runtime**.

---

## E. Intentional bugs and tests

- [ ] ≥ **3 deliberate issues** on `main` before Phase B agent run.
- [ ] Reproducible detection (tests or scripted check).
- [ ] End-to-end success demonstrable after session (`demo.sh` or equivalent).

---

## F. README

- [ ] Top-level `README.md` with 1–5 command quick-start.
- [ ] Prerequisites documented (runtime versions, OS notes).
- [ ] Troubleshooting: ≥ 3 common issues.

---

## G. Bonus eligibility (+5 points)

Checked by instructor **~30 minutes after** the student starts the one-shot prompt:

- [ ] Agent run **finished** (or clearly still running with visible progress).
- [ ] Mock integration **works end-to-end** after **one** prompt only.
- [ ] Prompt is **substantive** — not “run the app” / “fix tests” with no context.
- [ ] Repo at end of Phase A was genuinely broken (not pre-fixed to game bonus).

If any bonus criterion fails → base score only (max **10**).

---

## H. Base score mapping (10 points)

| Score | Typical state |
|------:|---------------|
| **10** | All sections A–F satisfied; working offline stack; strong prompt + plan + log |
| **7–9** | Mock works; one document or test area weak |
| **4–6** | Partial mock; major gaps in prompt/plan or integration |
| **1–3** | Backup branch only; minimal mock; no working path |
| **0** | Safety failure, wrong repo, or empty `main` |

*Instructor may use multiple prompts when assigning base score; bonus requires exactly one.*
