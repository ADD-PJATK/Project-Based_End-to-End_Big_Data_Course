# Task 05 — Large Scale Data Processing (Week 5)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the fifth assignment: extending the processing pipeline from Task 04 with **large-scale batch processing**, **Spark SQL queries**, and **data aggregations**. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **first full analytics pipeline**: a runnable artifact (script or notebook) that applies Spark SQL and aggregations to the project dataset(s) and produces a documented analytics result. This result becomes the basis for later tasks (feature engineering, ML, streaming, visualization).

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 05), and code (scripts or notebooks) in a clear location.
- **Spark SQL pipeline:** at least one runnable artifact that reads data, applies Spark SQL queries and aggregations, and writes a documented result to storage.
- **Analytics outputs:** aggregated tables, statistics, or derived datasets that provide project-relevant insights and are documented in the task report.
- **One task report** in the documentation folder: what queries were run, why they are meaningful for the project, how to reproduce the results; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 5 emphasises:

- **Batch vs streaming processing** — understanding when to use each paradigm.
- **Spark SQL** — structured querying over large datasets.
- **Lab:** data aggregation, processing large datasets.
- **Deliverable:** first analytics pipeline.

Teams are expected to use **Spark SQL** (via PySpark's `SparkSession.sql(...)` interface, DataFrames with SQL-like operations, or equivalent structured API). Alternatives to PySpark (e.g. Scala Spark, Dask for large datasets) are acceptable if documented and justified.

---

## 3. Pipeline requirements

### 3.1 What the pipeline must do

- **Read** input data from the storage solution used in Task 03 (or from a documented path). If a subset or sample is used, the report must state this and explain why.
- **Register data as SQL views or tables** and run at least **three meaningful Spark SQL queries** relevant to the project. Examples:
  - Aggregations (`GROUP BY`, `COUNT`, `SUM`, `AVG`) to produce summary statistics.
  - Filtering and sorting to identify top records (e.g. most frequent categories, highest-value transactions).
  - Joins between datasets or derived tables (for teams with multiple datasets, this is especially encouraged).
  - Window functions (e.g. `RANK`, `ROW_NUMBER`, `LAG/LEAD`) for ranking or trend analysis.
- **Store** the query results as a new dataset or structured output (e.g. Parquet or CSV written to the storage from Task 03, or to a documented local path). The output format and location must be documented.
- **Produce** at least one derived or aggregated dataset that will be reusable in later tasks (e.g. as input to feature engineering or ML).

### 3.2 Technical form

- The pipeline must be **runnable** (e.g. a PySpark script or Jupyter notebook). The repository must document **how to run it** (required environment, command, or notebook instructions).
- Dependencies must be listed (e.g. in `requirements.txt`, `environment.yml`, or in the task report).
- The pipeline must demonstrate use of **Spark SQL** explicitly (not only DataFrame API; at least one `spark.sql(...)` call or equivalent structured SQL interface must be present).

### 3.3 Teams of 3: cloud-based batch processing

- **Teams of 3** must run the Spark SQL pipeline using **managed cloud compute** on the cloud chosen in Task 03 (AWS, GCP, or Azure). Examples:
  - **AWS:** run PySpark on EMR or a notebook on SageMaker reading from S3.
  - **GCP:** run PySpark on Dataproc reading from GCS, or use BigQuery SQL for aggregations.
  - **Azure:** run PySpark on HDInsight or Synapse Spark reading from ADLS.
- The task report must state which cloud service was used for compute, how data was read from cloud storage, and where results were written.
- All team members' datasets must be processed through the Spark SQL pipeline, not just one.

### 3.4 Teams of 4: cloud, ETL tool, and IaC

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based batch processing on all datasets).
- The cloud ETL tool introduced in Task 04 **must continue to be used** (or a new cloud ETL component must be added) to orchestrate or trigger the Spark SQL pipeline. The task report must state how the ETL tool integrates with the SQL layer.
- **IaC remains mandatory.** Any new cloud resources provisioned for this task (e.g. new compute cluster, job definition, or additional storage) must be defined using the IaC technology from Task 03/04 (e.g. Terraform, CloudFormation, Bicep). The task report must describe what was added or changed in the IaC configuration.
- Each team member must contribute; the report must briefly describe each person's contribution to the Spark SQL pipeline or analytics results.

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 05, **one** task report (e.g. `documentation/task05_large_scale_processing.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Spark SQL pipeline

- At least one **runnable** artifact (script or notebook) that:
  - Reads data from documented input (storage or path).
  - Applies at least **three Spark SQL queries** as described in Section 3.1.
  - Writes documented results to storage or a documented path.
- Instructions to run the pipeline (environment, command, or notebook steps) in **correct technical English**.

### 4.3 Analytics outputs

- At least one derived or aggregated dataset (Parquet, CSV, or equivalent) written to storage or a documented path, usable in later tasks.
- A sample or summary of the output (e.g. a few rows or a statistical summary) must be added to `data_examples/` or described in the task report.

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task05_large_scale_processing.md`) that includes:
  - **What queries were run** and **why** they are relevant to the project (one paragraph per query or group of queries).
  - **Input and output:** data source, output location, output format, and schema or sample.
  - **Batch vs streaming:** a brief explanation of why batch processing was chosen for this task and what kinds of questions it answers in the project context.
  - **How to run** the pipeline (environment, command or notebook instructions).
  - For teams of 3: which cloud compute service was used and how data flows from storage to compute and back.
  - For teams of 4: same as teams of 3, plus which ETL tool was used for orchestration/triggering and what IaC changes were made.
  - For teams of 4: brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 05 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 05** (e.g. "Spark SQL analytics pipeline – large scale processing"). The task must be clearly identifiable as the large-scale processing deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 05. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. Spark SQL pipeline runs, results stored, cloud and IaC usage documented, report updated).

---

## 6. Grading (Task 05)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Spark SQL pipeline: at least 3 meaningful queries; reads from documented input; writes to documented output | 4 | 3 | 2.5 |
| Analytics outputs documented (sample or summary in data_examples/ or report; output reusable in later tasks) | 2 | 2 | 2 |
| Team of 3: cloud compute used for Spark SQL; all datasets processed; documented in report | — | 2 | — |
| Team of 4: cloud compute + ETL tool integration + IaC changes; each member's contribution described | — | — | 2 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 2 | 1.5 | 1.5 |
| Clear instructions on how to run the pipeline | 2 | 0.5 | 0.5 |
| At least 1 GitHub Project task for Task 05 | — | 1 | 1 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Spark, PySpark, or the cloud runtime environment.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 05)

| Requirement | Applies to |
|-------------|------------|
| Spark SQL pipeline: at least 3 queries, runnable, documented input and output | All teams |
| Analytics outputs written to storage or documented path; sample in data_examples/ or report | All teams |
| Batch vs streaming rationale included in task report | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (queries, batch rationale, input/output, how to run; correct technical English) | All teams |
| Team of 3: cloud compute (EMR / Dataproc / HDInsight or equivalent); all datasets; documented in report | Teams of 3 |
| Team of 4: cloud + ETL tool integration + IaC changes for new resources; each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 05 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
