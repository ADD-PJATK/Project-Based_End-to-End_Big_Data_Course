# Task 07 — Machine Learning on Big Data: Clustering (Week 7)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the seventh assignment: implementing **scalable clustering** on the project dataset(s) using the feature matrix produced in Task 06. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **runnable clustering pipeline** that trains and evaluates at least one clustering model (K-Means and/or hierarchical clustering) using a distributed or scalable ML framework (e.g. Spark MLlib, scikit-learn). The results must be documented with cluster assignments, evaluation metrics, and a business-relevant interpretation of what the discovered clusters represent.

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 07), and code (scripts or notebooks) in a clear location.
- **Clustering pipeline:** a runnable artifact that reads the feature matrix from Task 06, trains at least one clustering model, evaluates it, and produces documented cluster assignments.
- **Evaluation:** at least one quantitative metric (e.g. Silhouette Score, Davies–Bouldin Index, or Within-Cluster Sum of Squares) and a brief business interpretation of the discovered clusters.
- **One task report** in the documentation folder: which algorithm(s) were used, why, how the number of clusters was chosen, what the evaluation results show, and what the clusters mean for the project; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 7 emphasises:

- **Scalable machine learning** — applying ML to data that may not fit in memory on a single machine.
- **Clustering methods** — unsupervised discovery of groups in data.
- **Lab:** implement K-Means and hierarchical clustering using Spark MLlib and scikit-learn.

Teams are expected to use **Spark MLlib** (e.g. `pyspark.ml.clustering.KMeans`) for large datasets, or scikit-learn for smaller samples where distributed processing is not required. The choice must be justified based on dataset size and documented in the task report.

---

## 3. Clustering pipeline requirements

### 3.1 Algorithm requirements

All teams must implement **at least one** of the following clustering methods:

| Algorithm | Framework options | Notes |
|-----------|-------------------|-------|
| **K-Means** | Spark MLlib `KMeans`, scikit-learn `KMeans` | Required minimum. Must include a method for choosing k (see §3.2). |
| **Bisecting K-Means** | Spark MLlib `BisectingKMeans` | Acceptable alternative or addition to standard K-Means. |
| **Hierarchical clustering** | scikit-learn `AgglomerativeClustering` (on a sample) | Acceptable for smaller datasets or as supplementary analysis. Must state if run on a sample and why. |
| **Gaussian Mixture Models (GMM)** | Spark MLlib `GaussianMixture`, scikit-learn `GaussianMixture` | Acceptable addition or alternative. |

At minimum, **K-Means** (or Bisecting K-Means) must be implemented. Additional methods are encouraged and will be positively noted in grading.

### 3.2 Choosing the number of clusters

The team must apply at least one **systematic method** for selecting k:

- **Elbow method:** plot Within-Cluster Sum of Squares (WCSS or inertia) for a range of k values and identify the "elbow."
- **Silhouette analysis:** compute the mean Silhouette Score for a range of k values and select the k with the highest score.
- **Gap statistic or other principled method:** acceptable if documented.

The chosen k must be stated and justified in the task report based on the above analysis. A visualisation (plot) of the elbow curve or silhouette scores must be included in the deliverables (e.g. in `data_examples/` or embedded in the notebook/report).

### 3.3 Evaluation

The pipeline must compute and document at least one evaluation metric for the final model:

| Metric | Description |
|--------|-------------|
| **Silhouette Score** | Mean silhouette coefficient: ranges from −1 to +1; higher is better. Preferred metric. |
| **Davies–Bouldin Index** | Average ratio of intra-cluster to inter-cluster distances; lower is better. |
| **Within-Cluster Sum of Squares (WCSS)** | Also called inertia; lower is better. Used in the elbow method. |

All metrics used must be documented in the task report with an interpretation (e.g. "a Silhouette Score of 0.42 suggests moderate cluster separation, which is acceptable given the high-dimensional feature space").

### 3.4 Business interpretation

- The task report must include a **brief business interpretation** of the discovered clusters: what does each cluster represent in the context of the project (e.g. "Cluster 0 appears to contain users with low engagement; Cluster 1 contains high-volume purchasers"). If the clusters do not have a clear interpretation, the report must state this and explain why.
- If cluster labels can be assigned (e.g. named by dominant feature values), they should be.

### 3.5 Teams of 3: cloud-based ML

- **Teams of 3** must run the clustering pipeline using **managed cloud ML compute** on the cloud chosen in Task 03. Examples:
  - **AWS:** PySpark MLlib on EMR, or scikit-learn on SageMaker.
  - **GCP:** PySpark on Dataproc, or scikit-learn on Vertex AI notebooks.
  - **Azure:** PySpark on HDInsight or Synapse Spark, or scikit-learn on Azure ML.
- Clustering must be performed for **all** team members' datasets (each member's dataset from Task 01); results for each dataset must be documented.
- The task report must state which cloud service was used and how data flowed from the feature store / storage to the ML pipeline.

### 3.6 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based; all datasets; cloud documented).
- **IaC remains mandatory.** Any new cloud resources provisioned for ML compute (e.g. a new cluster configuration, ML workspace, or experiment tracking service) must be defined or extended in the IaC configuration. The task report must describe what was added or changed.
- Each team member must contribute to the clustering pipeline; the task report must briefly describe each person's contribution (e.g. which dataset, which algorithm, which section of the analysis).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 07, **one** task report (e.g. `documentation/task07_clustering.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Clustering pipeline

- At least one **runnable** artifact (script or notebook) that:
  - Reads the feature matrix from Task 06 (or a documented equivalent).
  - Applies a method for choosing k (elbow or silhouette analysis) and trains the final model.
  - Evaluates the model with at least one metric and outputs cluster assignments.
- Instructions to run the pipeline (environment, command, or notebook steps) in **correct technical English**.

### 4.3 Cluster assignments output

- The cluster assignment for each record (or sample) must be saved and documented:
  - Format (e.g. Parquet, CSV), location (storage path), and schema or shape.
  - A sample or summary (e.g. cluster distribution: number of records per cluster) added to `data_examples/` or described in the task report.

### 4.4 Visualisations

- At least one visualisation must be included (e.g. elbow curve, silhouette scores per k, or 2D scatter plot of clusters after PCA reduction). Visualisations must be saved as image files in the repository or referenced clearly in the report.

### 4.5 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task07_clustering.md`) that includes:
  - **Algorithm(s) used** and justification for the choice (e.g. why K-Means vs hierarchical vs GMM, considering dataset size and project goals).
  - **Choice of k:** method used (elbow / silhouette), plot or summary of results, and the chosen k with justification.
  - **Evaluation:** metric(s) computed, values obtained, and interpretation.
  - **Business interpretation:** what the clusters represent in the project context.
  - **Output:** where cluster assignments are saved (path, format, schema).
  - **How to run** the pipeline (environment, command or notebook instructions).
  - For teams of 3: cloud service used and data flow from feature storage to ML compute.
  - For teams of 4: same as teams of 3, plus IaC changes and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 07 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 07** (e.g. "Clustering – K-Means pipeline with Spark MLlib"). The task must be clearly identifiable as the clustering deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 07. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. pipeline runs, k chosen and justified, Silhouette Score computed, cluster assignments saved, report updated).

---

## 6. Grading (Task 07)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Clustering algorithm implemented (K-Means minimum); pipeline runnable | 3 | 2 | 2 |
| Systematic k selection (elbow or silhouette analysis) with visualisation | 2 | 2 | 2 |
| Evaluation metric(s) computed and interpreted (Silhouette Score, DBI, or WCSS) | 2 | 1.5 | 1.5 |
| Business interpretation of clusters included in report | 1 | 1 | 1 |
| Team of 3: cloud ML compute; all datasets; documented in report | — | 1.5 | — |
| Team of 4: cloud + IaC changes + each member's contribution described | — | — | 1.5 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 0.5 | 0.5 |
| Clear instructions on how to run the pipeline | 1 | 0.5 | 0.5 |
| At least 1 GitHub Project task for Task 07 | — | 1 | 0.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Spark MLlib, scikit-learn, or the cloud environment.
- Mandatory use of a specific clustering library version.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 07)

| Requirement | Applies to |
|-------------|------------|
| Clustering pipeline runnable; reads feature matrix from Task 06 | All teams |
| At least K-Means (or Bisecting K-Means) implemented | All teams |
| Systematic method for choosing k (elbow or silhouette); visualisation included | All teams |
| Evaluation metric computed and interpreted (Silhouette Score, DBI, or WCSS) | All teams |
| Cluster assignments saved (format, location, schema/distribution documented) | All teams |
| Business interpretation of discovered clusters included in task report | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (algorithm, k choice, evaluation, interpretation, output, how to run; correct technical English) | All teams |
| Team of 3: cloud ML compute; all datasets; documented in report | Teams of 3 |
| Team of 4: cloud + IaC changes + each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 07 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
