# Task 04 — Big Data Processing (Week 4)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the fourth assignment: implementing a **first data processing pipeline** using a distributed or scalable processing engine (e.g. **Spark / PySpark**), with **data transformations** and a **data cleaning pipeline**. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team’s responsibility.

The outcome is a **runnable pipeline** (script or notebook) that reads project data (from the storage from Task 03, or from a documented path or sample), applies **transformations** and **cleaning steps**, and produces a documented output (e.g. cleaned dataset, or clear description of the transformation and cleaning logic). This sets the basis for later tasks (large-scale processing, aggregation, ML).

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 04), and code (e.g. scripts or notebooks) in a clear location.
- **Basic EDA:** every team must deliver a basic Exploratory Data Analysis (EDA) that meets the three conditions in Section 3.4 (including correlation matrices where applicable).
- **Processing pipeline:** at least one runnable artifact (e.g. PySpark script or Jupyter notebook) that demonstrates MapReduce/Spark-style processing, data transformations, and a defined data cleaning pipeline. Teams of 3 must implement a **full pipeline** (ingestion → storage → quality validation → processing). Teams of 4 must use a **cloud ETL tool** and **IaC** remains mandatory (see Section 3.4).
- **One task report** in the documentation folder: what the pipeline does, which transformations and cleaning steps were applied, EDA outcomes, and how to run it; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 4 emphasises:

- **MapReduce concept** and **Spark architecture**
- **Lab:** PySpark basics, data transformations, data cleaning pipeline

Teams are expected to use a **Spark-based** (or equivalent distributed) approach. PySpark is the recommended programming interface; alternatives (e.g. Scala Spark, or another distributed engine with similar concepts) are acceptable if documented and justified in the task report.

---

## 3. Processing pipeline requirements

### 3.1 What the pipeline must do

- **Read** input data from a documented source (e.g. the storage from Task 03, a local path, or a sample dataset). If the full dataset is not read (e.g. for cost or size reasons), the report must state what subset or sample was used and why.
- **Apply data transformations** (e.g. filtering, mapping, aggregations, joins, type conversions) that are relevant to the project and that demonstrate use of the chosen engine (e.g. Spark DataFrames / RDDs).
- **Implement a data cleaning pipeline** (e.g. handling missing values, duplicates, outliers, or format normalisation) with clear, documented steps. The cleaning logic must be reproducible (e.g. fixed rules or parameters described in code or report).
- **Produce** a defined output: e.g. a cleaned dataset written to storage or to a local path, or a clear description of the output schema and where it is written. The output (or a sample) should be documentable (e.g. in `data_examples/` or in the report).

### 3.2 Technical form

- The pipeline must be **runnable** (e.g. a Python script using PySpark, or a Jupyter notebook with PySpark). The repository must document **how to run it** (e.g. required environment, command, or notebook instructions).
- Dependencies (e.g. PySpark, Python version) should be listed (e.g. in `requirements.txt`, `environment.yml`, or in the task report).

### 3.3 Teams of 3: full pipeline

- **Teams of 3** must implement a **full end-to-end pipeline** in this task, in the following order:
  1. **Data ingestion from source** — fetch or pull data from the original source (e.g. API, file URL, web).
  2. **Place data in their storage** — load the ingested data into the storage solution used in Task 03 (e.g. S3, GCS, ADLS, HDFS).
  3. **Quality validation** — run the data quality checks (as in Task 02: missing values, duplicates, consistency) on the data in that storage (or on a read from it).
  4. **Processing** — only then run the transformation and data cleaning pipeline (Section 3.1) on the validated data.
- **All** of the team’s datasets (each member’s dataset) **must** go through this full pipeline—not just one. The task report must describe each of the four stages and how they are chained, and state who is responsible for which dataset or part of the pipeline.

### 3.4 Teams of 4: cloud ETL tool and IaC

- **Teams of 4** must use **at least one ETL (Extract–Transform–Load) tool offered on the cloud** (the same cloud as in Task 03: AWS, GCP, or Azure). Examples:
  - **AWS:** e.g. AWS Glue, Lambda + Step Functions, or EMR with orchestration.
  - **GCP:** e.g. Dataflow, Dataprep, Cloud Data Fusion, or Dataproc with Cloud Composer.
  - **Azure:** e.g. Azure Data Factory, Synapse pipelines, or Databricks workflows.
- The ETL tool must be used for at least part of the pipeline (e.g. orchestration, ingestion into storage, or a transform step). The task report must state which cloud ETL tool was used, which steps it covers, and how it integrates with the rest of the pipeline (e.g. Spark/notebooks). Each member **must** contribute to the pipeline; the report must briefly describe each person’s contribution.
- **IaC (Infrastructure as Code) remains mandatory** for teams of 4. The team must continue to use an IaC technology (as in Task 03: e.g. Terraform, CloudFormation, Bicep) to provision infrastructure used in this task—e.g. ETL resources, compute, or storage for the pipeline—or to extend the IaC from Task 03. The task report must describe how IaC is used (which tool, what resources are provisioned or updated).

### 3.5 Basic EDA (all teams)

- **All teams** must produce a **basic Exploratory Data Analysis (EDA)** at this stage and include it in the deliverables. The EDA must satisfy **all three** of the following conditions:

| # | Condition | Description |
|---|-----------|-------------|
| 1 | **Correlation analysis** | For **tabular** data: at least one **correlation matrix** (or correlation heatmap) for numeric columns; document how it was computed (e.g. Pearson) and where the result is stored or displayed (e.g. in a notebook, in the report, or in `data_examples/`). For **non-tabular** data (e.g. text, images): an equivalent analysis must be proposed and implemented (e.g. co-occurrence matrix, feature correlation for embeddings, or similarity matrix on a sample); the report must describe the choice and the outcome. |
| 2 | **Summary statistics and distributions** | Provide **summary statistics** (e.g. count, mean, median, min, max, standard deviation for numeric fields; value counts for categorical) and/or **distribution visualisations** (e.g. histograms, box plots, bar charts) so that the scale and shape of the data are documented. For non-tabular data, provide equivalent summaries (e.g. document length distribution, image size distribution, label distribution). |
| 3 | **Missing values and duplicates overview** | Report **counts (or proportions)** of missing values per relevant field and of duplicate records (or documents/images), and optionally a simple visualisation. This supports quality and cleaning decisions and must be reproducible (e.g. from a script or notebook). |

- The EDA may be implemented in the same notebook or script as the pipeline, or in a separate artifact; it must be **runnable or reproducible** and the results (or references to them) must be described in the task report in **correct technical English**.

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 04, **one** task report (e.g. `documentation/task04_big_data_processing.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Basic EDA

- A **basic EDA** that satisfies all three conditions in Section 3.5: (1) correlation matrix or equivalent, (2) summary statistics and/or distributions, (3) missing values and duplicates overview. The EDA must be reproducible (script or notebook) and its outcomes documented in the task report.

### 4.3 Runnable pipeline

- At least one **runnable** pipeline (script or notebook) that:
  - Reads from a documented input (for teams of 3: the full pipeline includes ingestion → storage → quality validation → processing).
  - Applies transformations and a data cleaning pipeline as in Section 3.
  - Produces a documented output.
- **Teams of 4:** at least one **cloud ETL tool** (AWS / GCP / Azure) must be used for part of the pipeline, and **IaC** must still be used (e.g. to provision ETL or pipeline infrastructure); the report must state which ETL tool and how, and how IaC is used.
- Instructions to run the pipeline (e.g. in README, in the task report, or in a dedicated `docs/` file) in **correct technical English**.

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task04_big_data_processing.md`) that includes:
  - **What** the pipeline does (high-level); for teams of 3: description of the four stages (ingestion → storage → quality validation → processing).
  - **EDA:** summary of the three EDA conditions (correlation analysis, summary statistics/distributions, missing values and duplicates overview) and where the results are stored or displayed.
  - **Input:** source of data (e.g. storage from Task 03, path, or sample) and any subset/sampling used.
  - **Transformations:** which operations were applied and why they are relevant to the project.
  - **Cleaning pipeline:** which cleaning steps were implemented (e.g. missing values, duplicates, normalisation) and in what order.
  - **Output:** where the result is written (path, storage, format) and, if applicable, a short schema or sample.
  - **How to run:** environment and command (or reference to README/code).
  - For teams of 3: how the full pipeline (ingestion → storage → validation → processing) is chained.
  - For teams of 4: which cloud ETL tool was used, which steps it covers, **how IaC is used** (which tool, what resources), and brief description of each member’s contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 04 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 04** (e.g. “Big Data processing – PySpark pipeline”). The task must be clearly identifiable as the processing deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 04. Each task must have **clear acceptance criteria** (what “task completed” means), written in **correct technical English** and aligned with this specification (e.g. pipeline runnable, transformations and cleaning documented, report updated).

---

## 6. Grading (Task 04)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Basic EDA: all 3 conditions (correlation matrix or equivalent, summary stats/distributions, missing/duplicates overview) | 3 | 2 | 2 |
| Runnable pipeline: transformations and cleaning, documented output; Team of 3: full pipeline (ingestion → storage → validation → processing) | 3 | 3 | 2.5 |
| Team of 4: cloud ETL tool (AWS/GCP/Azure) and IaC still used; documented in report | — | — | 1 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 2 | 1.5 | 1 |
| Clear instructions on how to run the pipeline | 2 | 2 | 2 |
| At least 1 GitHub Project task for Task 04 | — | 1.5 | 1 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader’s discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Spark, PySpark, or the runtime environment.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 04)

| Requirement | Applies to |
|-------------|------------|
| Basic EDA: (1) correlation matrix or equivalent, (2) summary stats/distributions, (3) missing values and duplicates overview | All teams |
| Runnable pipeline (e.g. PySpark) with transformations and a data cleaning pipeline | All teams |
| Team of 3: full pipeline (ingestion → storage → validation → processing); **all** datasets must go through it | Teams of 3 |
| Team of 4: cloud ETL tool (AWS/GCP/Azure) and IaC still used; documented in report | Teams of 4 |
| Documented input and output; cleaning steps described | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (pipeline, EDA, transformations, cleaning, how to run; correct technical English) | All teams |
| Team of 4: each member’s contribution described in report | Teams of 4 |
| At least 1 GitHub Project task for Task 04 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
