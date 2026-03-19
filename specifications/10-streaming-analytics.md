# Task 10 — Streaming Analytics (Week 10)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the tenth assignment: applying **real-time analytics** to live data streams using **Spark Structured Streaming** or **Apache Flink**. This task extends the Kafka pipeline from Task 09 by adding a **streaming ML model** (stream classification or stream clustering) and **windowed aggregations** applied to the incoming event stream. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **runnable streaming analytics job** that reads from the Kafka topic(s) set up in Task 09, applies real-time transformations and at least one ML inference or streaming aggregation, and writes results to storage or a monitoring output. Students process **live (or simulated live) data streams**.

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 10), and code (scripts or notebooks) in a clear location.
- **Streaming analytics job:** a runnable Spark Structured Streaming or Flink job that reads from Kafka, applies windowed aggregations, and applies or simulates at least one ML step (classification or clustering) on the stream.
- **Windowed outputs:** documented results from at least one window-based aggregation (e.g. counts, averages, or anomaly flags per time window).
- **One task report** in the documentation folder: streaming job architecture, ML step applied, windowing strategy, how results are stored, and how the job relates to the project's business goals; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 10 emphasises:

- **Stream clustering** — applying clustering to continuously arriving data.
- **Stream classification** — applying a pre-trained classifier to streaming records in real time.
- **Lab:** Spark Streaming / Flink — students process live data streams.

Teams are expected to use **Spark Structured Streaming** (via PySpark) reading from Kafka as the primary approach. **Apache Flink** (Python or Java/Scala API) is an acceptable alternative if documented and justified. The choice must be stated in the task report.

---

## 3. Streaming analytics requirements

### 3.1 Streaming job inputs and outputs

- The streaming job must **read from the Kafka topic(s)** set up in Task 09 (or from a replay of the same data via a running producer).
- The job must write results to at least one **persistent destination** (e.g. HDFS, cloud object storage, Cassandra, a file sink, or console output with documentation). Writes to console alone are acceptable only if combined with a file or storage sink.
- The job must run continuously (or for a defined duration sufficient to demonstrate processing of multiple micro-batches or windows) and produce observable output.

### 3.2 Windowed aggregations (all teams)

All teams must implement at least **one windowed aggregation** on the stream. Acceptable window types:

| Window type | Description |
|-------------|-------------|
| **Tumbling window** | Fixed, non-overlapping windows of a given duration (e.g. count events per 1-minute window). |
| **Sliding window** | Overlapping windows that slide by a step smaller than the window size (e.g. rolling average over last 5 minutes, updated every 1 minute). |
| **Session window** | Windows that open on activity and close after a configurable gap of inactivity. |

The chosen window type, duration, and slide (if applicable) must be documented and justified in the task report (e.g. "a 60-second tumbling window was chosen to detect traffic spikes in near-real-time at a business-relevant granularity").

At least one of the following windowed metrics must be computed and stored:
- Count of events per window.
- Average, sum, or min/max of a numeric field per window.
- Count of distinct values or anomaly flag per window.

### 3.3 ML on the stream (all teams)

All teams must apply at least one **ML step** to the incoming stream records. Two approaches are acceptable:

**Option A — Apply a pre-trained model to the stream (recommended):**
- Use the model trained in Task 07 (clustering) or Task 08 (recommendations) and apply it to each arriving event (e.g. assign a cluster label, or compute a similarity score).
- The model must be loaded from a saved artefact (e.g. a Spark MLlib model saved to HDFS/S3, or a scikit-learn model saved as a pickle and loaded in a UDF).
- The assigned label or score must be appended to each event record and written to the output sink.

**Option B — Online / incremental learning on the stream:**
- Use an online clustering or classification algorithm that updates its model state with each micro-batch (e.g. Spark Streaming K-Means, or a custom incremental model).
- Document how the model is initialised, updated, and how its state is persisted between micro-batches.

Both options are acceptable; the choice must be stated and justified in the task report. Option A is recommended for teams using Spark MLlib models from Task 07/08.

### 3.4 Fault tolerance and checkpointing

- The streaming job must be configured with **checkpointing** (e.g. `spark.sparkContext.setCheckpointDir(...)` or Spark Structured Streaming's `checkpointLocation` option, or Flink's state backend). The checkpoint directory must be documented in the task report.
- Teams do not need to demonstrate full fault recovery (e.g. killing the job mid-run), but must document the checkpointing configuration and explain why it is important for production streaming jobs.

### 3.5 Teams of 3: cloud-based streaming analytics

- **Teams of 3** must run the streaming analytics job on **cloud infrastructure** (same cloud as in Task 03):
  - **AWS:** EMR Spark Structured Streaming reading from MSK, or Kinesis Data Analytics (Flink).
  - **GCP:** Dataproc Spark Structured Streaming reading from Pub/Sub, or Dataflow (Apache Beam / Flink-compatible).
  - **Azure:** HDInsight or Synapse Spark Structured Streaming reading from Event Hubs.
- The streaming job must read from the cloud Kafka / messaging service set up in Task 09. The task report must describe the cloud compute service, how the job was deployed, and how results were stored.

### 3.6 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based streaming analytics).
- **IaC remains mandatory.** New cloud resources provisioned for the streaming analytics layer (e.g. streaming compute cluster, Flink environment, or output storage bucket) must be defined or extended in the IaC configuration. The task report must describe what was added or changed.
- Each team member must contribute to the streaming job; the task report must briefly describe each person's contribution (e.g. windowed aggregation, ML inference on stream, IaC configuration, output sink).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 10, **one** task report (e.g. `documentation/task10_streaming_analytics.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Streaming analytics job

- At least one **runnable** Spark Structured Streaming or Flink job (script or notebook) that:
  - Reads from the Kafka topic(s) from Task 09.
  - Applies at least one windowed aggregation (Section 3.2).
  - Applies at least one ML step on the stream (Section 3.3).
  - Writes results to a documented output sink.
  - Is configured with checkpointing.
- Instructions to run the job (start Kafka producer, start streaming job, verify output) in **correct technical English**.

### 4.3 Windowed output samples

- A sample or summary of at least one windowed aggregation result (e.g. a few rows of the aggregated output, or a time series of counts per window) added to `data_examples/` or described in the task report.

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task10_streaming_analytics.md`) that includes:
  - **Streaming architecture:** how Kafka (Task 09), the streaming job, and the output sink are connected (diagram or textual description).
  - **Windowing strategy:** which window type, duration, slide (if applicable), metric computed, and business justification.
  - **ML step:** which option (A or B), which model was used (reference to Task 07/08 artefact, or description of online model), and how the ML output was incorporated into the stream.
  - **Checkpointing:** configuration, checkpoint directory, and brief explanation of its importance.
  - **Output:** where results are written (path, format) and a sample or summary.
  - **How to run** the full streaming pipeline (start Kafka, start producer, start streaming job, verify output).
  - For teams of 3: which cloud streaming compute service was used and how results are stored in the cloud.
  - For teams of 4: same as teams of 3, plus IaC changes and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 10 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 10** (e.g. "Streaming analytics – Spark Structured Streaming with ML inference"). The task must be clearly identifiable as the streaming analytics deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 10. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. streaming job runs end-to-end, windowed aggregation produces output, ML step applied, checkpointing configured, report updated).

---

## 6. Grading (Task 10)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Streaming job reads from Kafka; runnable end-to-end; writes to documented output sink | 3 | 2 | 2 |
| Windowed aggregation implemented (type, duration documented; business justification given) | 2 | 1.5 | 1.5 |
| ML step applied on the stream (pre-trained model or online model; choice justified) | 3 | 2.5 | 2.5 |
| Checkpointing configured and documented | 1 | 1 | 1 |
| Team of 3: cloud streaming compute; documented in report | — | 1.5 | — |
| Team of 4: cloud + IaC changes + each member's contribution described | — | — | 1.5 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 0.5 | 0.5 |
| At least 1 GitHub Project task for Task 10 | — | 1 | 0.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Spark Structured Streaming, Flink, or the cloud streaming environment.
- Mandatory window duration values (teams choose durations appropriate to their data).
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 10)

| Requirement | Applies to |
|-------------|------------|
| Streaming job reads from Kafka topic(s) from Task 09; runnable | All teams |
| At least one windowed aggregation (type, duration, metric, and business justification documented) | All teams |
| At least one ML step applied on the stream (pre-trained model or online model; choice justified) | All teams |
| Results written to documented output sink (not console only) | All teams |
| Checkpointing configured and documented (directory, brief explanation of its importance) | All teams |
| Windowed output sample or summary in data_examples/ or report | All teams |
| Instructions to run the full streaming pipeline (start Kafka, producer, job, verify) | All teams |
| Task report in documentation/ (architecture, windowing, ML step, checkpointing, output, how to run; correct technical English) | All teams |
| Team of 3: cloud streaming compute; documented in report | Teams of 3 |
| Team of 4: cloud + IaC changes + each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 10 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
