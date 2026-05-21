# Phase 2 Additional Assignments — Acceptance Criteria & Grading Checklist

**Repository:** `sXXXXX_kafka` in ADD GitHub organisation  
**Branch:** `main`  
**Total:** **7 points** (AA3: 3 + AA4: 4)

---

## A. Repository gate

| # | Criterion | Pass |
|---|-----------|------|
| A1 | Repo name matches `sXXXXX_kafka` | ☐ |
| A2 | Repo in ADD org (or approved equivalent) | ☐ |
| A3 | `main` contains AA1, AA2, and `documentation/ai-work-plan.md` | ☐ |
| A4 | No API keys / secrets in tracked files on `main` | ☐ |

---

## B. AA3a — Integration (2 points)

| # | Criterion | Pass |
|---|-----------|------|
| B1 | Anonymizer tree on `main` (`anonymizer/` or documented path) | ☐ |
| B2 | Both AA2 apps on `main`, separate subfolders | ☐ |
| B3 | Root README: map + quick start for anonymizer + both apps | ☐ |
| B4 | Both AA2 apps run per README; screenshots; env API key only | ☐ |
| B5 | `consolidation/CONSOLIDATION.md` if merge needed (or “already one repo”) | ☐ |

**AA3a score:** ☐ 0 | ☐ 1 | ☐ 2

---

## C. AA3b — Working anonymizer (1 point)

| # | Criterion | Pass |
|---|-----------|------|
| C1 | CLI runs from documented command in repo | ☐ |
| C2 | `examples/mapping.json` + sample input produce output | ☐ |
| C3 | README: no HTTP/LLM at runtime for masking | ☐ |
| C4 | Anonymizer screenshots present / valid | ☐ |

**AA3b score:** ☐ 0 | ☐ 1

*All of C1–C4 must pass for the 1 point.*

---

## D. AA4 — AI work plan (4 points)

| # | Criterion | Pass |
|---|-----------|------|
| D1 | `documentation/ai-work-plan.md` on `main` | ☐ |
| D2 | Sections 3.1–3.10 per [AA4 spec](./AA4-ai-work-plan.md) | ☐ |
| D3 | Scope table filled in | ☐ |
| D4 | ≥6-step workflow; ≥8 prompting rules | ☐ |
| D5 | ≥10 precautions (AA4 §3.6 themes) | ☐ |
| D6 | ≥4 task-specific AI plans for ADD project | ☐ |
| D7 | AI disclosure ≥150 words | ☐ |
| D8 | Pre-commit checklist ≥8 items; revision log ≥2 rows | ☐ |
| D9 | ~1,200+ words; clear English; no secrets | ☐ |

**AA4 score:** _____ / 4

---

## E. Total score

| Task | Max | Awarded |
|------|-----|---------|
| AA3a — integration | 2 | |
| AA3b — working anonymizer | 1 | |
| AA4 — AI work plan | 4 | |
| **Total** | **7** | |

**Comments:**

---

## F. Instructor notes

- **AA3a (2 pts):** Unified `sXXXXX_kafka`; both Kafka apps work; not a full AA1 re-grade.
- **AA3b (1 pt):** Extra point only if anonymizer is **verified working** on `main`.
- **AA4 (4 pts):** Plan document quality and disclosure.
- Phase 1 additional assignments remain **4+4** separately.

---

*Phase 2 acceptance checklist — ADD.*
