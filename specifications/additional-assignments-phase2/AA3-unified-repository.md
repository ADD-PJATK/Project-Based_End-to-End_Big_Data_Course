# Additional Assignment 3 (AA3) — Everything in One Repository on `main`

**Points:** **3 / 7** (Phase 2 total): **2** integration + **1** working anonymizer  
**Parent:** [Phase 2 overview](./README.md)

---

## 1. Purpose

All additional assignments (AA1, AA2, and the new AA4 document) must live in **one repository** on `main`: `sXXXXX_kafka`.

**AA3 scoring:**

| Part | Points | What is checked |
|------|--------|-----------------|
| **AA3a** — Integration | **2** | `sXXXXX_kafka` on `main` with AA1 tree + both AA2 apps; root README; consolidation note if needed; both stock apps still work |
| **AA3b** — Working anonymizer | **1** | Anonymizer **runs** from the repo per documented command (AA1 criteria) |

| Your situation | What to do |
|----------------|------------|
| **Already `sXXXXX_kafka`** with AA1 + AA2 | Fix layout if needed; short note in `consolidation/CONSOLIDATION.md` (“already integrated”). |
| **Two repos** (`sXXXXX_anonymize` + `sXXXXX_kafka`) | **Merge** anonymizer into `sXXXXX_kafka` on `main`; document in `CONSOLIDATION.md`. |
| **Only one of AA1 / AA2 done** | Finish the missing part on `main` first. |

Phase 1 grades for AA1 and AA2 are **not** re-awarded; AA3b only adds **1 point** for a verified working anonymizer in `sXXXXX_kafka`.

---

## 2. Deliverables (AA3a — integration, 2 points)

On **`main`** of `sXXXXX_kafka`:

1. Repo in ADD org, named `sXXXXX_kafka`.
2. **`anonymizer/`** (or documented path) — AA1 code, `examples/`, README, screenshots on `main`.
3. **Both AA2 apps** in separate subfolders (repo root or `kafka-stocks/`), each with README and screenshots.
4. **Root `README.md`** with student ID, repo map, quick start for anonymizer + both apps, no secrets in Git.
5. **`consolidation/CONSOLIDATION.md`** (recommended): merge notes or “already integrated”; no API keys committed.

---

## 3. Working anonymizer (AA3b — 1 point)

The **+1 point** is awarded only if the instructor can run the anonymizer from `sXXXXX_kafka` using your README.

### Required for 1 point

- [ ] CLI runs with the command documented in `anonymizer/README.md` (paths valid after merge).
- [ ] `examples/mapping.json` and at least one sample input produce correct anonymized output.
- [ ] README still states: **no HTTP/LLM at runtime** for anonymization.
- [ ] Screenshots for anonymizer still present (or updated after move).

### Not sufficient for the extra point

- Anonymizer files present on `main` but CLI fails or examples broken.
- Only a stub or placeholder without AA1 functionality.

Full AA1 reference: [AA1 ACCEPTANCE](../additional-assignment-data-anonymization/ACCEPTANCE.md).

---

## 4. AA2 functional checks (part of AA3a — 2 points)

- [ ] Realtime app runs per its README.
- [ ] History app runs per its README.
- [ ] API key only via environment (not in repo).
- [ ] Screenshots present for both apps.

Reference: [AA2 ACCEPTANCE](../additional-assignment-kafka-stocks/ACCEPTANCE.md).

---

## 5. Integration quality

- Update broken paths in READMEs after moving files.
- Union `.gitignore` for all subprojects.
- Meaningful commits when merging (explain in `CONSOLIDATION.md` if needed).

---

## 6. Grading (AA3 — 3 points total)

### AA3a — Integration (2 points)

| Points | Criterion |
|--------|-----------|
| **2** | `sXXXXX_kafka` on `main`; AA1 tree + both AA2 apps present, documented, runnable; root README OK; consolidation note if merge required; no secrets |
| **1** | Integrated but one Kafka app broken, weak README, or missing `CONSOLIDATION.md` when merge was required |
| **0** | Wrong repo name, still two submission repos, or missing AA1/AA2 on `main` |

### AA3b — Working anonymizer (1 point)

| Points | Criterion |
|--------|-----------|
| **1** | Anonymizer runs; examples work; runtime rule documented; screenshots OK |
| **0** | Missing, broken, or not runnable from repo |

**AA3 total** = AA3a + AA3b (max **3**).

---

*AA3 — Unified repository (3 points).*
