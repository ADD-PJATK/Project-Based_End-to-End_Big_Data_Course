# Task 08 — Recommendation Systems (Week 8)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the eighth assignment: building a **recommendation engine** based on **collaborative filtering** and/or **matrix factorization**. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **runnable recommendation pipeline** that trains and evaluates a recommendation model on the project dataset(s) and produces documented recommendations for sample users or items. Teams whose project domain does not naturally support user–item recommendations must propose and justify an adapted approach (see Section 3.4).

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 08), and code (scripts or notebooks) in a clear location.
- **Recommendation pipeline:** a runnable artifact that trains at least one recommendation model (e.g. ALS in Spark MLlib), evaluates it with appropriate metrics, and generates recommendations for a sample of users or items.
- **Evaluation results:** at least one offline evaluation metric (e.g. RMSE, MAE, Precision@K, or MAP@K) with documented interpretation.
- **One task report** in the documentation folder: model choice, data preparation for recommendations, evaluation results, and sample recommendations with interpretation; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 8 emphasises:

- **Collaborative filtering** — recommending items based on the behaviour of similar users (or similar items).
- **Matrix factorization** — decomposing the user–item interaction matrix into latent factors.
- **Lab:** build a recommendation engine (example: movie recommender).

Teams are expected to use **Spark MLlib's ALS (Alternating Least Squares)** as the primary recommendation algorithm, as it is designed for distributed, scalable matrix factorization. scikit-learn or Surprise (Python library) are acceptable for smaller datasets if documented and justified.

---

## 3. Recommendation pipeline requirements

### 3.1 Data preparation

- The team must construct (or identify from the existing dataset) a **user–item interaction matrix** or equivalent:
  - **Explicit feedback:** e.g. ratings, scores, review stars.
  - **Implicit feedback:** e.g. purchase counts, click counts, view counts, binary interaction flags.
- If the dataset does not naturally contain user–item interactions, the team must **justify and document** how the interaction matrix was constructed (e.g. co-occurrence of two entities, time-series similarity, or another proxy measure).
- The interaction matrix must be split into **training and test sets** (e.g. 80/20 random split, or a time-based split if the data has timestamps). The split strategy must be documented.

### 3.2 Algorithm requirements

All teams must implement **at least one** of the following:

| Algorithm | Framework | Notes |
|-----------|-----------|-------|
| **ALS (Alternating Least Squares)** | Spark MLlib `ALS` | Required minimum; supports both explicit and implicit feedback. |
| **SVD-based collaborative filtering** | Surprise `SVD`, scikit-learn (manual) | Acceptable for smaller datasets; must be justified. |
| **Item-based or user-based k-NN collaborative filtering** | Surprise, scikit-learn, or custom | Acceptable as supplementary method alongside ALS. |

At minimum, **ALS** (or an equivalent matrix-factorization model) must be implemented. Additional methods (e.g. content-based filtering as a comparison) are encouraged and will be positively noted in grading.

### 3.3 Evaluation

The pipeline must compute and document at least one evaluation metric:

| Metric | Applicable to | Description |
|--------|---------------|-------------|
| **RMSE (Root Mean Squared Error)** | Explicit feedback | Lower is better. Standard metric for rating prediction. |
| **MAE (Mean Absolute Error)** | Explicit feedback | Lower is better. Complementary to RMSE. |
| **Precision@K** | Implicit / ranking | Fraction of top-K recommendations that are relevant. |
| **MAP@K (Mean Average Precision @ K)** | Implicit / ranking | Average precision across users for top-K ranked items. |
| **NDCG@K** | Implicit / ranking | Normalised Discounted Cumulative Gain; accounts for rank position. |

For **explicit feedback:** RMSE or MAE must be computed. For **implicit feedback:** Precision@K or MAP@K must be computed. The metric values and their interpretation must be included in the task report.

### 3.4 Adapted approach for non-recommendation datasets

If the project dataset does not naturally support a user–item recommendation scenario (e.g. a purely tabular sensor dataset with no user identity), the team must:
- Propose an **adapted recommendation task** in the task report (e.g. "item-to-item similarity recommendations based on cluster proximity from Task 07", or "content-based recommendations using TF-IDF similarity for text datasets").
- Implement this adapted approach and evaluate it with appropriate metrics.
- The report must clearly state why the standard user–item approach was not applicable and how the chosen adaptation addresses the project domain.

### 3.5 Sample recommendations

- The pipeline must produce **sample recommendations** for at least 5 sample users (or items), stored and documented:
  - A table or list of top-K (e.g. K = 5 or 10) recommended items for each sample user.
  - A brief interpretation: are the recommendations plausible given what is known about those users/items?
- Sample recommendations must be added to `data_examples/` or included in the task report.

### 3.6 Teams of 3: cloud-based recommendation

- **Teams of 3** must run the recommendation pipeline using **managed cloud ML compute** on the cloud chosen in Task 03. Examples:
  - **AWS:** ALS on EMR or SageMaker.
  - **GCP:** ALS on Dataproc or BigQuery ML matrix factorization.
  - **Azure:** ALS on HDInsight/Synapse Spark or Azure ML.
- If the project has multiple datasets (each member's dataset), the recommendation model should be applied to the dataset(s) most suitable for the task; the report must justify which dataset was used.
- The task report must state which cloud service was used and how data flowed.

### 3.7 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based; documented).
- **IaC remains mandatory.** Any new cloud resources provisioned for recommendation training (e.g. a new compute cluster, model registry bucket, or experiment tracking instance) must be defined or extended in the IaC configuration. The task report must describe what was added or changed.
- Each team member must contribute to the recommendation pipeline; the task report must briefly describe each person's contribution (e.g. data preparation, model training, evaluation, sample generation).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 08, **one** task report (e.g. `documentation/task08_recommendation_systems.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Recommendation pipeline

- At least one **runnable** artifact (script or notebook) that:
  - Prepares the user–item interaction matrix (or equivalent) and splits it into train/test sets.
  - Trains at least one recommendation model (ALS or equivalent).
  - Evaluates the model with at least one metric (Section 3.3).
  - Generates top-K recommendations for a sample of users or items.
- Instructions to run the pipeline in **correct technical English**.

### 4.3 Sample recommendations output

- Top-K recommendations for at least 5 sample users/items, saved and documented (e.g. CSV or Markdown table in `data_examples/` or in the task report).

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task08_recommendation_systems.md`) that includes:
  - **Data preparation:** how the interaction matrix was constructed; split strategy and rationale.
  - **Algorithm(s) used** and justification (or adapted approach for non-recommendation datasets, as in Section 3.4).
  - **Evaluation:** metric(s) computed, values obtained, and interpretation.
  - **Sample recommendations:** table of top-K recommendations for sample users/items; plausibility assessment.
  - **Output:** where model artefacts or recommendations are saved (path, format).
  - **How to run** the pipeline (environment, command or notebook instructions).
  - For teams of 3: cloud service used and data flow from storage to ML compute.
  - For teams of 4: same as teams of 3, plus IaC changes and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 08 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 08** (e.g. "Recommendation engine – ALS collaborative filtering"). The task must be clearly identifiable as the recommendation systems deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 08. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. interaction matrix prepared, ALS trained and evaluated, sample recommendations generated, report updated).

---

## 6. Grading (Task 08)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Interaction matrix (or equivalent) prepared; train/test split documented | 2 | 1.5 | 1.5 |
| Recommendation model trained and runnable (ALS or justified alternative) | 3 | 2 | 2 |
| Evaluation metric(s) computed and interpreted (RMSE/MAE for explicit; Precision@K or MAP@K for implicit) | 2 | 2 | 2 |
| Sample top-K recommendations for ≥ 5 users/items with plausibility assessment | 1 | 1 | 1 |
| Team of 3: cloud ML compute; dataset selection justified; documented in report | — | 2 | — |
| Team of 4: cloud + IaC changes + each member's contribution described | — | — | 2 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 0.5 | 0.5 |
| Clear instructions on how to run the pipeline | 1 | 0 | 0.5 |
| At least 1 GitHub Project task for Task 08 | — | 1 | 1 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Spark MLlib ALS, Surprise, or the cloud environment.
- Mandatory choice of K (number of recommendations); teams choose K and justify it.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 08)

| Requirement | Applies to |
|-------------|------------|
| User–item interaction matrix (or adapted equivalent) constructed and documented | All teams |
| Train/test split applied; split strategy documented | All teams |
| At least one recommendation model trained (ALS or justified alternative) | All teams |
| Evaluation metric computed and interpreted (RMSE/MAE or Precision@K/MAP@K) | All teams |
| Sample top-K recommendations for ≥ 5 users/items; plausibility assessment in report | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (data prep, algorithm, evaluation, samples, output, how to run; correct technical English) | All teams |
| Adapted approach documented if standard user–item scenario not applicable | Teams where applicable |
| Team of 3: cloud ML compute; dataset selection justified; documented in report | Teams of 3 |
| Team of 4: cloud + IaC changes + each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 08 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
