# Additional Assignments — Phase 2 (Unified Repository + AI Work Plan)

**Course:** Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course  
**Format:** Two graded deliverables in **one GitHub repository**  
**Language:** English (all student-written deliverables)

---

## 1. Overview

Phase 2 extends the two earlier additional assignments:

| Earlier assignment | Original spec folder | Original repo name (example) |
|--------------------|----------------------|------------------------------|
| **AA1** — Local Data Anonymizer | `additional-assignment-data-anonymization/` | `sXXXXX_anonymize` |
| **AA2** — Real-time Stock Data (Kafka / SSE) | `additional-assignment-kafka-stocks/` | `sXXXXX_kafka` |

Everything for Phase 2 lives in **one repository** on `main`:

- **AA1** and **AA2** solutions (already graded in Phase 1) must be present and still meet their original specs.
- **AA3** — bring everything together in that single repo (**3 points**: 2 integration + 1 working anonymizer).
- **AA4** — AI-assisted work plan document (**4 points**).

| Task | Title | Max points |
|------|--------|------------|
| **AA3** | Unified repo on `main` + working anonymizer | **3** (2 + 1) |
| **AA4** | AI-assisted work plan document | **4** |
| | **Total (Phase 2)** | **7** |

**Important:** Many students already kept AA1 and AA2 in **`sXXXXX_kafka`**. They receive integration points once layout is confirmed; **+1 point** requires a **working** anonymizer on `main` (verified by the instructor). Students who used **two separate repos** (`sXXXXX_anonymize` + `sXXXXX_kafka`) must **fix** this: merge the anonymizer into **`sXXXXX_kafka`** on `main` (same repository name as in the [AA2 spec](../additional-assignment-kafka-stocks/README.md)).

Detailed acceptance criteria: [ACCEPTANCE.md](./ACCEPTANCE.md).

Task briefs:

- [AA3 — Unified repository (3 pts)](./AA3-unified-repository.md)
- [AA4 — AI work plan (4 pts)](./AA4-ai-work-plan.md)

---

## 2. Single repository (mandatory)

Use **one** repository in the ADD GitHub organisation — the **same name as AA2**:

- **Name:** `sXXXXX_kafka` (replace `XXXXX` with your student ID, e.g. `s12345_kafka`)
- **Visibility:** public or accessible to the instructor
- **Default branch:** `main` must contain AA1, AA2, and the AA4 document

If AA1 was only in `sXXXXX_anonymize`, **move or merge** it into `sXXXXX_kafka` on `main`. You do **not** create a new repo name. The old `sXXXXX_anonymize` repo may stay for history; the **graded submission** for Phase 2 is **`sXXXXX_kafka` only**.

---

## 3. Required repository layout on `main`

```text
sXXXXX_kafka/
├── README.md                    # How to run AA1 + AA2 + link to ai-work-plan
├── .gitignore
├── anonymizer/                  # AA1 — full prior solution
│   ├── README.md
│   ├── examples/
│   ├── screenshots/
│   └── ... source code ...
├── kafka-stocks/                # AA2 — both apps in separate subfolders
│   ├── realtime-dashboard/      # App #1
│   ├── history-downloader/      # App #2 (folder name may vary)
│   └── screenshots/
├── documentation/
│   └── ai-work-plan.md          # AA4 — required filename
└── consolidation/               # recommended if you merged from two repos
    └── CONSOLIDATION.md
```

**Rules:**

- **AA1** under `anonymizer/` (or equivalent path documented in root README).
- **AA2** both apps in **separate subfolders** (under `kafka-stocks/` as above, or at repo root as in your original AA2 submission — paths must be clear in root `README.md`).
- **AA4** at `documentation/ai-work-plan.md`.
- Root `README.md` links to anonymizer, both Kafka apps, and the work plan.

---

## 4. Relationship to Phase 1 specifications

Phase 2 **does not replace** AA1 or AA2 requirements. Both must still satisfy:

- [AA1 — Data Anonymizer](../additional-assignment-data-anonymization/ACCEPTANCE.md)
- [AA2 — Kafka / SSE stocks](../additional-assignment-kafka-stocks/ACCEPTANCE.md)

AA3 checks that both are on `main` in the unified repo; **+1 point** is awarded separately for a **working anonymizer**. Phase 1 points (4+4) are unchanged; Phase 2 adds **7** points.

---

## 5. AI tools policy (Phase 2)

| Task | AI use |
|------|--------|
| **AA3** | Allowed for merging repos, fixing paths, updating READMEs |
| **AA4** | **Expected** to help draft the plan; document must disclose usage and list precautions |

AA1 runtime rule unchanged: **no AI/API calls during anonymization**.

See [AA4 — AI work plan](./AA4-ai-work-plan.md).

---

## 6. Grading summary

| Task | What is graded | Points |
|------|----------------|--------|
| **AA3a** | One repo `sXXXXX_kafka`; AA1 + AA2 on `main`; AA2 apps work; consolidation doc if merge needed | **2** |
| **AA3b** | Working anonymizer in repo (CLI + examples per AA1) | **1** |
| **AA4** | `documentation/ai-work-plan.md` per spec | **4** |
| | **Total** | **7** |

See [ACCEPTANCE.md](./ACCEPTANCE.md) for checklists.

---

## 7. Academic integrity

- Reuse your own AA1 and AA2 code when consolidating.
- Attribute substantial AI-generated text in `ai-work-plan.md` (AA4).
- No API keys or secrets on `main`.

---

## 8. Suggested timeline (non-binding)

| Step | Activity |
|------|----------|
| 1 | Ensure `sXXXXX_kafka` on `main` has anonymizer + kafka apps (merge from `sXXXXX_anonymize` if needed) |
| 2 | Root README + quick-start commands; verify both apps and CLI run |
| 3 | Write `documentation/ai-work-plan.md` with AI, then edit and disclose |
| 4 | Submit repository URL |

---

*Phase 2 additional assignments — ADD Project-Based End-to-End Big Data Course.*
