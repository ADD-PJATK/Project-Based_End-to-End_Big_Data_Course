# Task 03 — Data Storage (Week 3)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the third assignment: storing the project dataset(s) in a **distributed or scalable storage solution**. It is a **business specification**, not a step-by-step tutorial. Implementation details (e.g. setup, configuration) are the team’s responsibility.

The outcome is **data stored in distributed storage** (or an equivalent scalable storage solution) that the team will use in later tasks. The chosen storage **must be used at least once in the project**—at least for this task. **GitHub is not a place for storing dataset files**; only code, documentation, small samples (e.g. in `data_examples/`), and references or scripts to obtain data belong in the repository.

**Expected result of this task (summary):**
- **Appropriate repository structure:** `data_examples/`, `documentation/` (with one task report for Task 03), and code/scripts as agreed in earlier tasks.
- **Data stored** in a qualifying storage solution (see Sections 2–4), with clear documentation of where and how it is stored and how to access it.
- **One task report** in the documentation folder: storage choice, how data was stored, and how it fits the project; written in **consistent language** and **correct technical English**.

---

## 2. Storage technologies (course stack)

The course README recommends the following for storage and lab setup; teams may use these or the cloud options in Section 3.

| Technology | Role |
|------------|------|
| **Hadoop / HDFS** | Distributed storage; fits batch processing and data lakes. |
| **Docker** | Environment for running HDFS, Spark, or other services locally or in the cloud. |
| **Data lakes** | Pattern for storing raw and processed data at scale (often on HDFS or object storage). |
| **Apache Cassandra** | NoSQL wide-column store; integrates with Spark and big-data ecosystems. |
| **Parquet** | Columnar storage format; efficient for analytics and Spark. |

Teams of 2 may use **any** of the above (e.g. HDFS in Docker, or a cloud offering that provides HDFS/object storage). Teams of 3 and 4 have additional cloud requirements (Section 4).

---

## 3. Cloud options (informational)

Beyond the course stack, the **three most popular public clouds** offer managed Big Data storage and processing. The following is **descriptive only** (no setup instructions); teams choose and implement on their own.

### 3.1 Amazon Web Services (AWS)

- **S3 (Simple Storage Service):** object storage used as the backbone of data lakes; stores arbitrary blobs (e.g. CSV, Parquet, logs) with high durability and scalability.
- **EMR (Elastic MapReduce):** managed Hadoop and Spark clusters; can read/write S3 and HDFS.
- **Athena:** serverless SQL over data in S3 (e.g. Parquet, CSV).
- **Redshift:** data warehouse for analytics; often fed from S3 or EMR.

**Example Big Data story:** Ingest logs or events into **S3** buckets (raw zone); run **EMR** (Spark) for cleaning and aggregation; write results as Parquet back to S3 (processed zone); query with **Athena** or load into **Redshift** for dashboards.

### 3.2 Google Cloud Platform (GCP)

- **Cloud Storage (GCS):** object storage; similar role to S3 for data lakes and bulk data.
- **Dataproc:** managed Hadoop and Spark clusters; reads/writes GCS and HDFS.
- **BigQuery:** serverless data warehouse; can query data in GCS or load it for analytics.

**Example Big Data story:** Store raw events or files in **GCS**; run **Dataproc** (Spark) for ETL and feature engineering; export to **BigQuery** for SQL analytics and reporting, or keep Parquet in GCS for downstream ML.

### 3.3 Microsoft Azure

- **Azure Data Lake Storage (ADLS Gen2):** scalable storage for analytics; compatible with Hadoop (ABFS) and Spark.
- **HDInsight:** managed Hadoop, Spark, Kafka clusters; integrates with ADLS.
- **Azure Synapse Analytics:** data warehouse and lakehouse; can query ADLS and run Spark.
- **Azure Blob Storage:** object storage; often used together with ADLS for raw data.

**Example Big Data story:** Land raw data in **ADLS** (or Blob); process with **HDInsight** (Spark) or Synapse Spark; store refined datasets in ADLS (Parquet); run SQL or ML in **Synapse** for reporting and models.

---

## 4. Mandatory use of storage and cloud (by team size)

### 4.1 All teams

- The project **must** use a **proper storage solution** (distributed or scalable) for the dataset(s). This storage **must be used at least once in the project**—**at least for this task (Task 03)**. In later tasks, teams may store materials in other, more convenient locations **only if they document a clear justification** (e.g. in the task report or README).
- **GitHub is not a place for storing dataset files.** Code, documentation, `data_examples/`, and scripts (e.g. to download or list data) belong in the repo; the actual bulk data must live in the chosen storage (HDFS, object storage, Cassandra, etc.).

### 4.2 Teams of 2

- No mandatory cloud. The team **must** store data in a qualifying storage (e.g. HDFS, Docker-based storage, or any cloud object/store of their choice).

### 4.3 Teams of 3

- The team **must** use **one** of the **three** major public clouds: **AWS**, **GCP**, or **Azure** for storage (and/or processing that uses that cloud’s storage). The specific services (e.g. S3, GCS, ADLS) and setup are the team’s responsibility; the task report must state which cloud and how it was used.

### 4.4 Teams of 4

- The team **must** use **one** of **AWS**, **GCP**, or **Azure** for storage (as for teams of 3). **In addition**, for creating the storage (e.g. buckets, containers, accounts), the team **must** use **some Infrastructure as Code (IaC)** technology—e.g. Terraform, Pulumi, AWS CloudFormation, Google Deployment Manager, or Azure Bicep/ARM/Terraform. The IaC code (or a reference to it and how to run it) must be in the repository or documented in the task report; the report must describe which IaC tool was used and what resources it provisions.

---

## 5. Deliverables (all teams)

### 5.1 Repository structure

- **data_examples/** and **documentation/** must be maintained as in previous tasks. For Task 03, **one** task report (e.g. `documentation/task03_data_storage.md`) **per group**; teams of 3 and 4 contribute to the same report file and maintain one consistent quality standard (**correct technical English**).

### 5.2 Data stored in the chosen storage

- Dataset(s) (or a defined subset used for the project) **must** be stored in the chosen storage solution (HDFS, cloud object storage, Cassandra, etc.). The repository must document:
  - **Where** the data is stored (e.g. bucket name, path, cluster or endpoint).
  - **How** to access it (e.g. script, credentials note, or link to docs) without storing the data itself in GitHub.
  - **What** is stored (e.g. format: Parquet, CSV; schema or sample as in `data_examples/`).

### 5.3 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task03_data_storage.md`) that includes:
  - Choice of storage (and, for teams of 3 and 4, cloud provider and services used).
  - How the data was stored (paths, formats, access method).
  - How this fits the project and the course stack (or cloud story).
  - For teams of 3: which of AWS / GCP / Azure was used and how.
  - For teams of 4: which of AWS / GCP / Azure was used, how storage was created, and **which IaC (Infrastructure as Code) technology** was used (e.g. Terraform, CloudFormation, Bicep) and what it provisions.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 6. GitHub Project tasks (by team size)

### 6.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 03 (optional).

### 6.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 03** (e.g. “Data storage – dataset in [storage name]”). The task must be clearly identifiable as the storage deliverable.

### 6.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 03. Each task must have **clear acceptance criteria** (what “task completed” means), written in **correct technical English** and aligned with this specification (e.g. storage chosen, data stored, documentation updated).

---

## 7. Grading (Task 03)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Data stored in qualifying storage; documented (where, how to access); GitHub not used for bulk data | 7 | 4 | 4 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 3 | 2 | 1.5 |
| Team of 3: used AWS or GCP or Azure; documented in report | — | 2 | — |
| Team of 4: used AWS or GCP or Azure and IaC for storage; documented in report | — | — | 2 |
| At least 1 GitHub Project task for Task 03 | — | 2 | 1.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 1 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader’s discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 8. Out of scope for this specification

- Step-by-step setup or configuration of HDFS, Docker, or cloud services.
- Exact submission dates (defined elsewhere by the course rules).

---

## 9. Summary checklist (Task 03)

| Requirement | Applies to |
|-------------|------------|
| Data stored in distributed/scalable storage (not on GitHub); used at least for this task | All teams |
| Documentation: where and how data is stored, how to access it | All teams |
| Task report in documentation/ (storage choice, how used, correct technical English) | All teams |
| Team of 3: used AWS or GCP or Azure; documented in report | Teams of 3 |
| Team of 4: used AWS or GCP or Azure and an IaC technology for creating storage; documented in report | Teams of 4 |
| At least 1 GitHub Project task for Task 03 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
