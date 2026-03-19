# Task 06 — Feature Engineering (Week 6)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the sixth assignment: performing **feature engineering** on the project dataset(s) to prepare them for machine learning tasks in later weeks. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **feature matrix** (or equivalent ML-ready representation) derived from the project dataset(s), produced by a runnable pipeline that includes feature extraction, encoding, normalisation, and at least one **dimensionality reduction** technique (PCA or SVD). This feature-engineered dataset will serve as input for the clustering (Task 07), recommendation (Task 08), and other ML tasks.

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 06), and code (scripts or notebooks) in a clear location.
- **Feature engineering pipeline:** a runnable artifact that transforms raw (or cleaned) data into ML-ready features; must include feature extraction, encoding, normalisation, and dimensionality reduction.
- **Dimensionality reduction results:** at least one application of PCA or SVD (or an equivalent technique for non-tabular data), with documented explained variance or equivalent quality metric.
- **One task report** in the documentation folder: which features were created and why, how dimensionality reduction was applied, and how the resulting feature set relates to the project's ML goals; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 6 emphasises:

- **Feature extraction** — deriving informative attributes from raw data.
- **Dimensionality reduction** — reducing the number of features while retaining meaningful variance.
- **PCA / SVD** — specific techniques from the course syllabus.
- **Lab:** feature engineering using Python / Spark.

Teams are expected to use Python (e.g. scikit-learn, NumPy) and/or Spark MLlib for feature engineering. PySpark's `MLlib` feature transformers (e.g. `VectorAssembler`, `StandardScaler`, `PCA`) are recommended for large datasets; scikit-learn pipelines are acceptable for smaller samples or for non-distributed processing.

---

## 3. Feature engineering requirements

### 3.1 Feature extraction and encoding (all data types)

The pipeline must produce at least the following transformations, adapted to the project's data types:

| Data type | Required transformations |
|-----------|--------------------------|
| **Tabular** | Numeric feature normalisation or standardisation (e.g. `StandardScaler`, `MinMaxScaler`); encoding of categorical features (e.g. one-hot encoding, label encoding, or ordinal encoding); handling of any remaining missing values (e.g. imputation). |
| **Text** | Tokenisation, stopword removal, and a numeric representation (e.g. TF-IDF, Bag of Words, or word/sentence embeddings such as Word2Vec or a pre-trained model); the chosen representation must be justified in the task report. |
| **Images** | Resizing to a consistent resolution; pixel normalisation or standardisation; and either a flattened or convolution-derived feature representation (e.g. raw pixels, HOG features, or embeddings from a pre-trained model); the choice must be justified. |

Teams with multiple datasets of different types must apply the appropriate transformations to **each** dataset.

### 3.2 Dimensionality reduction (all teams)

- **All teams** must apply at least one **dimensionality reduction** technique:
  - **PCA (Principal Component Analysis):** for tabular or dense numeric features. The pipeline must document the number of components chosen, the **explained variance** (cumulative) for those components, and a brief interpretation of whether the reduction is adequate for the project.
  - **SVD (Singular Value Decomposition):** acceptable as an alternative (e.g. TruncatedSVD for sparse matrices such as TF-IDF). Same documentation requirements as PCA (number of components, explained variance or equivalent quality metric).
  - **For non-tabular data** (text, images): if PCA/SVD is applied to embedding vectors or feature matrices, the same documentation requirements apply. If a different dimensionality reduction technique is used (e.g. UMAP, t-SNE for visualisation purposes), the team must also apply PCA or SVD to the same data for comparison, and document both.
- The output of dimensionality reduction must be saved as a feature matrix or dataset that can be used in later ML tasks (Task 07 onwards).

### 3.3 Feature relevance and selection (optional but recommended)

Teams are encouraged (but not required) to perform a brief feature importance or relevance analysis (e.g. variance-based filter, correlation with a target variable if available, or mutual information) and to document which features were retained and why. This will strengthen the quality of later ML tasks.

### 3.4 Teams of 3: cloud-based feature engineering

- **Teams of 3** must run the feature engineering pipeline on the **cloud** (same cloud as in Task 03). Examples:
  - **AWS:** run PySpark MLlib transformers on EMR, or scikit-learn on SageMaker; read/write to S3.
  - **GCP:** run PySpark on Dataproc or scikit-learn on Vertex AI; read/write to GCS.
  - **Azure:** run PySpark on HDInsight or Synapse; read/write to ADLS.
- Feature engineering must be performed for **all** team members' datasets (each member's dataset from Task 01).
- The task report must state which cloud service was used, how data flowed from storage into the pipeline and back.

### 3.5 Teams of 4: cloud, IaC, and documentation of each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based; all datasets; cloud documented).
- **IaC remains mandatory.** Any new cloud resources provisioned for feature engineering compute (e.g. a new Spark cluster configuration, a notebook instance, or a feature store bucket) must be defined or extended in the IaC configuration from Task 03/04. The task report must describe what was added or changed.
- Each team member must contribute to the feature engineering pipeline; the task report must briefly describe each person's contribution (e.g. which dataset, which transformations, which section of the pipeline).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 06, **one** task report (e.g. `documentation/task06_feature_engineering.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Feature engineering pipeline

- At least one **runnable** artifact (script or notebook) that:
  - Reads cleaned data (from Task 04/05 output or a documented path).
  - Applies feature extraction and encoding as required for the data type(s) (Section 3.1).
  - Applies dimensionality reduction (PCA or SVD) and documents results (Section 3.2).
  - Writes the resulting feature matrix (or ML-ready dataset) to storage or a documented path.
- Instructions to run the pipeline in **correct technical English**.

### 4.3 Feature matrix output

- The resulting feature-engineered dataset (feature matrix or ML-ready representation) must be saved and documented:
  - Format (e.g. Parquet, NumPy array, CSV), location (storage path), and schema or shape.
  - A sample or summary (e.g. first 5 rows, shape, column names) added to `data_examples/` or described in the task report.

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task06_feature_engineering.md`) that includes:
  - **Feature extraction:** which features were created for each data type and why they are relevant to the project's ML goals.
  - **Encoding and normalisation:** which methods were applied and why.
  - **Dimensionality reduction:** which technique (PCA, SVD, or other), number of components chosen, **explained variance** (or equivalent quality metric), and interpretation of whether the reduction is adequate.
  - **Output:** format, location, schema or shape of the feature matrix.
  - **How to run** the pipeline (environment, command or notebook instructions).
  - For teams of 3: cloud service used, data flow from storage to compute and back.
  - For teams of 4: same as teams of 3, plus IaC changes and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 06 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 06** (e.g. "Feature engineering – PCA / SVD pipeline"). The task must be clearly identifiable as the feature engineering deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 06. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. feature extraction applied, PCA/SVD run and documented, feature matrix saved, report updated).

---

## 6. Grading (Task 06)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Feature extraction and encoding: all required transformations for relevant data types | 2 | 1.5 | 1.5 |
| Dimensionality reduction (PCA or SVD): applied, components chosen, explained variance documented | 3 | 2 | 2 |
| Feature matrix output saved and documented (format, location, schema/shape; sample in data_examples/ or report) | 2 | 2 | 2 |
| Team of 3: cloud compute used for feature engineering; all datasets processed; documented in report | — | 2 | — |
| Team of 4: cloud + IaC changes + each member's contribution described | — | — | 2 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 2 | 1.5 | 1.5 |
| Clear instructions on how to run the pipeline | 1 | 0 | 0.5 |
| At least 1 GitHub Project task for Task 06 | — | 1 | 1 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of scikit-learn, Spark MLlib, or the cloud environment.
- Mandatory choice of specific PCA/SVD library or number of components.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 06)

| Requirement | Applies to |
|-------------|------------|
| Feature extraction and encoding applied (appropriate to data type: tabular / text / images) | All teams |
| Dimensionality reduction (PCA or SVD): applied; number of components chosen; explained variance (or equivalent) documented | All teams |
| Feature matrix saved (format, location, shape documented); sample in data_examples/ or report | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (features, encoding, PCA/SVD results, output, how to run; correct technical English) | All teams |
| Team of 3: cloud compute for feature engineering; all datasets; documented in report | Teams of 3 |
| Team of 4: cloud + IaC changes for new resources; each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 06 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
