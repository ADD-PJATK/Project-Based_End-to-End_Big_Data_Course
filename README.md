# Modern Course Mode

# Project-Based End-to-End Big Data Course

**Course:** Analysis of Large Data Sets (ADD)
**Teaching Model:** Project-Based Learning (End-to-End Data System)
**Language:** English
**ECTS:** 5

### Core Idea

Students work in **teams (2 - 4 people)** to build a **complete Big Data pipeline**:

**Data → Storage → Processing → Machine Learning → Visualization → Presentation**

Instead of isolated exercises, the **entire semester revolves around one project**.

Example project topics:

* Social media analysis
* Streaming IoT analytics
* E-commerce recommendation system
* Fraud detection system
* Graph analysis of social networks
* Movie recommendation engine

---

# Recommended Technology Stack (Free / Open Source)

## Data Processing

* **Apache Spark** – distributed analytics engine for big data processing and ML. ([Medium][2])
* **Hadoop / HDFS** – distributed storage (kept from syllabus).

## Streaming

* **Apache Kafka** – event streaming platform.
* **Apache Flink** – real-time processing framework supporting large data streams. ([CareerFoundry][3])

## Programming

* **Python**
* **PySpark**

Python dominates modern data analytics due to powerful libraries such as Pandas and NumPy. ([Integrate.io][4])

## Machine Learning

* **Spark MLlib**
* **Scikit-learn**

## Data Mining / Workflow

Replace **RapidMiner** (used in syllabus) with:

* **KNIME (open source)**
* **Python ML ecosystem**

KNIME is a free open-source data analytics platform widely used for machine learning workflows. ([Graphite Note][5])

## Storage

* **HDFS**
* **Apache Cassandra (NoSQL)**
* **Parquet data format**

Cassandra integrates well with big-data ecosystems like Spark and Hadoop. ([Medium][6])

## Visualization

* **Apache Superset**
* **Metabase**
* **Python (Matplotlib / Plotly)**

---

# Semester Structure

Total: **13 weeks**

Each week combines:

* short lecture
* workshop
* project work

---

# Week-by-Week Plan (Modern Mode)

## Week 1 – Introduction to Big Data Projects

Lecture:

* Big Data ecosystem
* Real industry architectures
* Introduction to course project

Lab:

* Team formation
* Selection of dataset
* Introduction to **Python + Jupyter Notebook**

Deliverable:
Project proposal.

**Detailed documentation:** [Task 01 — Project Proposal (business specification)](specifications/01-project-proposal.md)

---

# Week 2 – Data Acquisition

Lecture:

* Data sources
* APIs
* Web scraping
* Streaming vs batch data

Lab:

* Collecting data from:

  * APIs
  * open datasets
  * web sources

Tools:

* Python
* Requests
* Pandas

Deliverable:
Initial dataset.

**Detailed documentation:** [Task 02 — Data Acquisition and Initial Quality Evaluation (business specification)](specifications/02-data-acquisition.md)

---

# Week 3 – Data Storage

Lecture:

* Distributed storage
* Hadoop HDFS architecture
* Data lakes

Lab:

* Setup:

  * Hadoop / HDFS
  * Docker environment

Deliverable:
Data stored in distributed storage.

**Detailed documentation:** [Task 03 — Data Storage (business specification)](specifications/03-data-storage.md)

---

# Week 4 – Big Data Processing

Lecture:

* MapReduce concept
* Spark architecture

Lab:

* PySpark basics
* Data transformations
* Data cleaning pipeline

**Detailed documentation:** [Task 04 — Big Data Processing (business specification)](specifications/04-big-data-processing.md)

---

# Week 5 – Large Scale Data Processing

Lecture:

* Batch vs streaming processing
* Spark SQL

Lab:

* Data aggregation
* Processing large datasets

Deliverable:
First analytics pipeline.

**Detailed documentation:** [Task 05 — Large Scale Data Processing (business specification)](specifications/05-large-scale-processing.md)

---

# Week 6 – Feature Engineering

Lecture:

* Feature extraction
* Dimensionality reduction
* PCA / SVD (from syllabus)

Lab:

* Feature engineering using Python / Spark

**Detailed documentation:** [Task 06 — Feature Engineering (business specification)](specifications/06-feature-engineering.md)

---

# Week 7 – Machine Learning on Big Data

Lecture:

* Scalable machine learning
* Clustering methods

Lab:

* Implement clustering:

  * K-Means
  * hierarchical clustering

Tools:

* Spark MLlib
* Scikit-learn

**Detailed documentation:** [Task 07 — Machine Learning on Big Data: Clustering (business specification)](specifications/07-clustering.md)

---

# Week 8 – Recommendation Systems

Lecture:

* Collaborative filtering
* Matrix factorization

Lab:

* Build recommendation engine

Example:
Movie recommender.

**Detailed documentation:** [Task 08 — Recommendation Systems (business specification)](specifications/08-recommendation-systems.md)

---

# Week 9 – Stream Processing

Lecture:

* Streaming data
* Kafka architecture

Lab:

* Kafka data ingestion
* Real-time pipeline

**Detailed documentation:** [Task 09 — Stream Processing (business specification)](specifications/09-stream-processing.md)

---

# Week 10 – Streaming Analytics

Lecture:

* Stream clustering
* Stream classification

Lab:

* Spark Streaming / Flink

Students process **live data streams**.

**Detailed documentation:** [Task 10 — Streaming Analytics (business specification)](specifications/10-streaming-analytics.md)

---

# Week 11 – Graph Mining

Lecture:

* Graph analytics
* PageRank
* Network analysis

Lab:

* Graph analysis using:

  * Spark GraphX
  * NetworkX

**Detailed documentation:** [Task 11 — Graph Mining (business specification)](specifications/11-graph-mining.md)

---

# Week 12 – Visualization & BI

Lecture:

* Data storytelling
* Dashboards

Lab:

* Build dashboard using:

  * Superset
  * Metabase
  * Python dashboards

**Detailed documentation:** [Task 12 — Visualization & BI (business specification)](specifications/12-visualization-bi.md)

---

# Week 13 – Final Project Demo

Students present:

1. Data pipeline architecture
2. Machine learning results
3. Visualization dashboard
4. Business insights

Deliverables:

* code repository
* documentation
* presentation

**Detailed documentation:** [Task 13 — Final Project Demo (business specification)](specifications/13-final-project-demo.md)

---

# Learning Outcomes (Extended)

Students will be able to:

1. Design **Big Data architectures**
2. Build **distributed data pipelines**
3. Apply **scalable machine learning**
4. Process **streaming and graph data**
5. Deploy **analytics dashboards**

---

# Example Final Project Architecture

```
Data Sources
      ↓
Data Collection (Python / API / Scraping)
      ↓
Kafka Streaming
      ↓
Spark Processing
      ↓
Storage (HDFS / Cassandra)
      ↓
Machine Learning (Spark ML / Python)
      ↓
Visualization (Superset / Metabase)
```

---

✅ This approach keeps **all core syllabus concepts**:

* MapReduce
* clustering
* decision trees
* stream mining
* graph mining
* recommendation systems

but teaches them **in a realistic modern data pipeline** used in industry.
