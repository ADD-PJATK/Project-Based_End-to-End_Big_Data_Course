# Task 09 — Stream Processing (Week 9)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the ninth assignment: setting up a **streaming data pipeline** using **Apache Kafka** (or an equivalent event streaming platform) and building a **real-time data ingestion pipeline** connected to the project's storage or processing layer. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **runnable Kafka-based pipeline** (producer + consumer, or an equivalent streaming ingest flow) that simulates or replays project data as a stream of events, and connects that stream to downstream processing or storage. This forms the foundation for streaming analytics in Task 10.

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 09), and code (scripts or notebooks) in a clear location.
- **Kafka producer:** a runnable script that publishes project data as events to a Kafka topic (or equivalent message bus).
- **Kafka consumer:** a runnable script (or Spark Structured Streaming / Flink source) that reads from the topic and writes events to storage or a processing layer.
- **One task report** in the documentation folder: streaming architecture, topic design, how the pipeline was run, and how streaming fits the project; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 9 emphasises:

- **Streaming data** — event-driven data architectures and real-time pipelines.
- **Kafka architecture** — topics, producers, consumers, brokers, offsets.
- **Lab:** Kafka data ingestion, real-time pipeline.

Teams are expected to use **Apache Kafka** (self-hosted via Docker, or a managed cloud service) as the primary event streaming platform. Alternatives (e.g. Apache Pulsar, RabbitMQ for limited use cases) are acceptable only if explicitly justified and documented; the core concepts (topics, producers, consumers) must still be demonstrated.

---

## 3. Streaming pipeline requirements

### 3.1 Kafka setup

- The team must set up a working **Kafka cluster** (minimum: 1 broker, appropriate for the project scale). Acceptable setups include:
  - **Local / Docker:** Kafka + Zookeeper (or KRaft) via Docker Compose.
  - **Cloud managed:** AWS MSK, GCP Pub/Sub (messaging equivalent), Azure Event Hubs (Kafka-compatible protocol).
- The setup must be **documented** in the task report and/or in a configuration file (e.g. `docker-compose.yml`, IaC script): how to start the broker(s), and how the team validated that Kafka is running.

### 3.2 Topic design

- The team must create **at least one Kafka topic** for the project data. The topic design must be documented:
  - **Topic name(s):** meaningful names reflecting the data domain (e.g. `transactions`, `sensor_readings`, `user_events`).
  - **Partitions:** number of partitions and the rationale (e.g. one partition per dataset source, or parallelism requirement).
  - **Retention:** configured retention period or size (or the default, if kept as default with justification).
  - **Message format:** how messages are serialised (e.g. JSON, Avro, CSV line). The schema or example message must be documented.

### 3.3 Kafka producer

- The team must implement at least one **Kafka producer** that:
  - Reads project data (from the storage in Task 03/04/05, or from a local file / API) and publishes it as a stream of events to the Kafka topic.
  - Produces events at a **configurable rate** or in batches (e.g. simulating a real-time feed by replaying historical data with a configurable sleep interval, or actually reading from a live API or data generator).
  - Logs or prints confirmation that messages are being produced (e.g. message count, topic name, timestamp).
- The producer must be **runnable** and documented (how to start, configure the source, and stop).

### 3.4 Kafka consumer

- The team must implement at least one **Kafka consumer** that:
  - Subscribes to the topic(s) and reads incoming events.
  - Performs at least one action on the consumed events (e.g. writes to storage, prints to console with a count, or passes events to a Spark Structured Streaming / Flink source for downstream processing).
  - Demonstrates **offset management** (e.g. auto-commit, or manual commit with documentation of the strategy used).
- The consumer must be **runnable** and documented (how to start and verify it is consuming correctly).
- If the consumer is a **Spark Structured Streaming** job reading from Kafka (recommended for integration with Task 10), this is acceptable and preferred.

### 3.5 End-to-end validation

- The team must demonstrate that the pipeline works **end to end**: messages produced to the topic are consumed and reach their destination (storage, console, or downstream processor). Evidence of this must be included in the task report (e.g. screenshots, log output excerpts, or a description of how the pipeline was validated).

### 3.6 Teams of 3: managed cloud Kafka

- **Teams of 3** must use a **managed cloud streaming service** on the cloud chosen in Task 03:
  - **AWS:** Amazon MSK (Managed Streaming for Apache Kafka).
  - **GCP:** Google Cloud Pub/Sub (Kafka-compatible or native API) or Confluent Cloud on GCP.
  - **Azure:** Azure Event Hubs with the Kafka protocol interface.
- The task report must state which service was used, how the topic was created, and how producer and consumer connect to the cloud service.
- All team members' datasets should be represented in the streaming pipeline (e.g. one topic per dataset, or one combined topic with a dataset identifier field in the message schema).

### 3.7 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (managed cloud Kafka).
- **IaC is mandatory** for provisioning the streaming infrastructure. The team must use the IaC technology from previous tasks (e.g. Terraform, CloudFormation, Bicep) to provision the managed Kafka / Event Hub / Pub/Sub resource, topics (where supported by the IaC provider), and any associated networking or access control. The task report must describe which IaC tool was used and which resources were provisioned.
- Each team member must contribute to the streaming pipeline; the task report must briefly describe each person's contribution (e.g. producer for dataset X, consumer and storage sink, IaC configuration, topic design).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 09, **one** task report (e.g. `documentation/task09_stream_processing.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Kafka producer script

- At least one **runnable** producer script (e.g. Python using `kafka-python`, `confluent-kafka`, or PySpark streaming write):
  - Reads project data and publishes events to the configured topic.
  - Configurable (e.g. message rate, number of messages, source path) via parameters or environment variables.
  - Instructions to run (e.g. required libraries, environment variables for broker address, command).

### 4.3 Kafka consumer script (or Spark Structured Streaming source)

- At least one **runnable** consumer (Python consumer, or Spark Structured Streaming job reading from Kafka):
  - Subscribes to the topic and reads events.
  - Performs at least one action (storage write, print/log, or passes to processing layer).
  - Instructions to run.

### 4.4 Kafka setup configuration

- Configuration file(s) (e.g. `docker-compose.yml` for local setup, or IaC code for cloud setup) that allow the grader to reproduce the Kafka cluster setup. Must be in the repository.

### 4.5 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task09_stream_processing.md`) that includes:
  - **Streaming architecture diagram or description:** how the producer, topic(s), consumer, and downstream storage/processing are connected.
  - **Kafka setup:** broker configuration, how to start the cluster, and how its operation was validated.
  - **Topic design:** name(s), partitions, retention, message format (with an example message).
  - **Producer:** what data it publishes, at what rate, and how to run it.
  - **Consumer:** what it does with consumed events, offset management strategy, and how to run it.
  - **End-to-end validation:** evidence that the pipeline works (log excerpt, screenshot reference, or description).
  - **How streaming fits the project:** a brief paragraph on why streaming is relevant for the project's domain (e.g. what business questions require real-time processing).
  - For teams of 3: which cloud managed Kafka service was used, how it was configured, and how producer/consumer connect.
  - For teams of 4: same as teams of 3, plus which IaC tool was used and what resources it provisions; brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 09 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 09** (e.g. "Stream processing – Kafka ingestion pipeline"). The task must be clearly identifiable as the stream processing deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 09. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. Kafka running, topic created, producer/consumer runnable and tested end-to-end, report updated).

---

## 6. Grading (Task 09)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Kafka setup (local Docker or cloud) running and documented (broker config, how to start) | 2 | 1 | 1 |
| Topic design documented (name, partitions, message format with example) | 1 | 1 | 1 |
| Runnable Kafka producer: publishes project data to topic, configurable, documented | 3 | 2 | 2 |
| Runnable Kafka consumer: reads from topic, performs action, offset strategy documented | 2 | 2 | 2 |
| End-to-end validation evidence included in report | 1 | 1 | 1 |
| Team of 3: managed cloud Kafka (MSK / Pub/Sub / Event Hubs); documented in report | — | 1.5 | — |
| Team of 4: managed cloud Kafka + IaC for streaming infrastructure + each member's contribution | — | — | 1.5 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 1 | 1 |
| At least 1 GitHub Project task for Task 09 | — | 0.5 | 0.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Kafka, Zookeeper, or Docker.
- Mandatory choice of Kafka client library version.
- Schema registry or Avro schema management (encouraged but not required).
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 09)

| Requirement | Applies to |
|-------------|------------|
| Kafka cluster running (local Docker or cloud); setup documented (broker config, how to start) | All teams |
| At least one topic created; name, partitions, message format documented with example message | All teams |
| Runnable producer: reads project data, publishes to topic, configurable rate/source | All teams |
| Runnable consumer: reads from topic, performs action; offset management strategy documented | All teams |
| End-to-end validation evidence (log excerpt or description) in task report | All teams |
| Paragraph on why streaming is relevant for the project domain | All teams |
| Kafka setup configuration file in repository (docker-compose.yml or IaC) | All teams |
| Task report in documentation/ (architecture, setup, topic design, producer, consumer, validation, how to run; correct technical English) | All teams |
| Team of 3: managed cloud Kafka (MSK / Pub/Sub / Event Hubs); documented in report | Teams of 3 |
| Team of 4: cloud + IaC for streaming infrastructure; each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 09 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
