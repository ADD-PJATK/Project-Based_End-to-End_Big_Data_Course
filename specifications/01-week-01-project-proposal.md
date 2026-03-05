# Task 01 — Project Proposal (Week 1)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the first assignment: team formation, dataset choice, and project proposal. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team’s responsibility.

The outcome is a **project proposal** that sets the dataset, topic, and problem domain for the entire semester pipeline (data acquisition → storage → processing → ML → visualization).

---

## 2. Dataset requirement

### 2.1 Teams of 2

- The team **must** select **one** dataset used for the whole project.
- **Minimum size by data type:**
  - **Tabular data:** at least **10,000 samples** (rows/records).
  - **Other types** (e.g. text corpora, images): at least **2,000 samples**; the README must state the size and justify suitability for the full Big Data pipeline.
- The dataset must be suitable for the end-to-end pipeline. The choice must be justified in the repository README (see below).

### 2.2 Teams of 3 or 4

- **Each team member** must have **their own dataset** (one dataset per person).
- **Preferably**, the datasets should be **of different types**, for example:
  - **Tabular** (e.g. CSV, relational)
  - **Text** (e.g. documents, reviews, social posts)
  - **Images** (e.g. image classification, vision tasks)
- **Minimum size by data type:**
  - **Tabular data:** at least **10,000 samples** (rows/records) per tabular dataset.
  - **Text or image data:** at least **2,000 samples** per dataset; the README must state the size and justify suitability for each dataset.
- All datasets must be suitable for the shared project theme and the end-to-end pipeline. The README must list each dataset, its type, size, and how it fits the project.

---

## 3. Repository and naming

- The team **must** create **one** repository in the **ADD-PJATK** organization:  
  **https://github.com/ADD-PJATK**
- **Repository name** must follow this pattern, using **student index numbers** (s + 5 digits):
  - **2-person teams:** `sXXXXX_sXXXXX` (e.g. `s12345_s67890`)
  - **3-person teams:** `sXXXXX_sXXXXX_sXXXXX`
  - **4-person teams:** `sXXXXX_sXXXXX_sXXXXX_sXXXXX`
- The repository will be used for the whole course; the root of the repo is the **project root** (no extra nesting by assignment).

---

## 4. Deliverables (all teams)

### 4.1 README in the repository root

A single **README** (e.g. `README.md`) in the **root** of the repository must contain:

1. **Data source(s)**
   - **Teams of 2:** Clear identification of the dataset (name, origin, URL or citation). Statement that the dataset meets the minimum size (**≥ 10,000 samples** for tabular, **≥ 2,000 samples** for other types) and how this was verified (e.g. row count, link to documentation).
   - **Teams of 3 or 4:** For **each** team member’s dataset: name, origin, URL or citation; **data type** (tabular / text / images or other); **size** (e.g. sample/record count); and how it meets the minimum (tabular **≥ 10,000**, other types **≥ 2,000**). Preferably, datasets should be of **different types** (e.g. one tabular, one text, one images).

2. **Project / topic area**
   - Short description of the **problem domain** the team intends to work in (e.g. social media analysis, IoT analytics, recommendations, fraud detection, graph analysis).
   - What **goals or questions** the project will address over the semester (high level), so that later tasks (data acquisition, storage, processing, ML, visualization) are clearly aligned with this proposal. For teams of 3 or 4, how each dataset contributes to this common theme must be briefly stated.

No specific README structure is imposed beyond the above; formatting is left to the team. The README must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 5. Additional deliverables by team size

### 5.1 Teams of 2

- No additional deliverables beyond Section 4.

### 5.2 Teams of 3

- **GitHub Project (classic or Projects (beta))**  
  Create a **Project** in the same repository (or linked to it) under the **Projects** tab.
- **Epics**  
  Create **at least 12 Epics**, one per assignment:
  - Epic 1 ↔ Task 01 (this assignment)
  - Epic 2 ↔ Task 02  
  - …  
  - Epic 12 ↔ Task 12  
  - *Task 13 does not require a separate Epic.*
- Epics may be minimal for now (e.g. title and optional short description); they will be refined in later weeks.

### 5.3 Teams of 4

- Same as for **teams of 3** (GitHub Project + at least 12 Epics, one per tasks 1–12).
- **In addition**, each Epic must include a **full description of expectations**: what must be implemented or delivered in that task, so that the Epic serves as a clear acceptance specification for the corresponding assignment. This description must be written in **correct technical English** and aligned with the official task specifications (e.g. from this and future specification documents).

---

## 6. Grading (Task 01)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Repository in ADD-PJATK, correct naming (`sXXXXX_sXXXXX` …) | 2 | 2 | 2 |
| Dataset(s) meet minimum size (tabular ≥ 10,000; other ≥ 2,000) and type diversity where required | 3 | 3 | 3 |
| README: data source(s), type, size, verification | 2 | 2 | 2 |
| README: project/topic area, goals (and per-dataset role for 3–4) | 3 | 2 | 1.5 |
| GitHub Project + 12 Epics (one per tasks 1–12) | — | 1 | 1.5 |
| Epics include full description of expectations per task | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader’s discretion. All written deliverables (README, Epic descriptions, etc.) must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step tutorials or tool-specific instructions.
- Mandatory technology choices for Week 1 (beyond using the ADD-PJATK repo and README).
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 01)

| Requirement | Applies to |
|-------------|------------|
| One dataset; tabular ≥ 10,000 samples, other types ≥ 2,000 samples | Teams of 2 |
| One dataset per member; preferably different types (tabular, text, images); tabular ≥ 10,000, other types ≥ 2,000 per dataset | Teams of 3 and 4 |
| Repo in ADD-PJATK, name `sXXXXX_sXXXXX` […] | All teams |
| README: data source(s) + type + size / verification | All teams |
| README: project/topic area and high-level goals (and per-dataset role for 3–4) | All teams |
| GitHub Project + 12 Epics (1 per tasks 1–12) | Teams of 3 and 4 |
| Epics with full expectation descriptions | Teams of 4 only |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
