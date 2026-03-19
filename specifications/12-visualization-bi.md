# Task 12 — Visualization & BI (Week 12)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the twelfth assignment: building an **interactive analytics dashboard** that communicates the key insights from the project's data pipeline, machine learning results, and graph analytics. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **documented, runnable dashboard** (or a set of documented visualisations) that presents project results in a form accessible to a non-technical stakeholder, with a coherent **data story** explaining what was found and why it matters. This dashboard will be demonstrated in the Final Project Demo (Task 13).

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 12), and code or configuration files for the dashboard in a clear location.
- **Dashboard or visualisation set:** at least 5 distinct charts or panels covering different aspects of the project results; interactive where possible.
- **Data story:** a documented narrative that connects the visualisations to the project's business goals and explains what decisions or insights the dashboard supports.
- **One task report** in the documentation folder: dashboard design rationale, tool choice, chart descriptions with business interpretation, and how to run or access the dashboard; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 12 emphasises:

- **Data storytelling** — organising visualisations and results into a coherent narrative for decision-makers.
- **Dashboards** — interactive, accessible views of data for business users.
- **Lab:** build a dashboard using **Apache Superset**, **Metabase**, or **Python dashboards** (e.g. Plotly Dash, Streamlit).

Teams are expected to use one or more of the following tools:

| Tool | Notes |
|------|-------|
| **Apache Superset** | Open-source BI platform; supports SQL-based datasets, interactive charts, and shareable dashboards. |
| **Metabase** | Open-source BI tool; simpler setup; good for business-friendly dashboards from SQL databases. |
| **Plotly Dash** | Python-native interactive dashboard framework; code-first; suited to ML-heavy projects. |
| **Streamlit** | Python-native app framework; suited to data science workflows and rapid prototyping. |
| **Matplotlib / Seaborn / Plotly (static or interactive)** | Acceptable for the chart set if a full BI tool is not used; the team must justify why a full BI tool was not suitable. |

The tool choice must be documented and justified in the task report.

---

## 3. Dashboard requirements

### 3.1 Minimum chart requirements (all teams)

The dashboard (or visualisation set) must include **at least 5 distinct charts or panels**, covering at least **three different aspects** of the project results. Required aspects:

| Aspect | Example charts |
|--------|---------------|
| **Data overview** | Distribution of a key variable (histogram or box plot), sample size summary, data type breakdown. |
| **Processing and analytics results** | Aggregation output from Task 05 (e.g. time series, bar chart of top categories, heatmap of a Spark SQL result). |
| **ML results** | Cluster distribution from Task 07 (e.g. bar chart of cluster sizes, scatter plot of clusters in 2D PCA space); recommendation or classification accuracy from Task 08. |
| **Streaming or graph insights** | Window-based metric from Task 10 (e.g. event rate per window); top-PageRank nodes from Task 11; community size distribution. |
| **Business-oriented summary** | A high-level KPI or insight panel (e.g. "top 10 most recommended items", "clusters by dominant feature", "highest-traffic time windows") aimed at a non-technical audience. |

At least **one chart must be interactive** (e.g. a filterable chart, a drill-down panel, or a dropdown selector), unless the team uses only static Python charts (in which case the team must justify why interactive charts were not feasible and provide at least one chart with parameterised code that allows rerunning for different slices of the data).

### 3.2 Data story (all teams)

- The dashboard must be accompanied by a **written data story** (in the task report, or as a text section within the dashboard itself) that:
  - Introduces the project context and the business question or problem being addressed.
  - Walks through the key insights from each section of the dashboard.
  - States **at least two concrete business insights or recommendations** derived from the data (e.g. "Based on the clustering results, Cluster 2 represents high-value customers who could be targeted with premium recommendations").
  - Is written in **correct technical English** accessible to a non-technical reader.

### 3.3 Dashboard accessibility and reproducibility

- The dashboard must be **accessible** for the grader without requiring credentials to a team member's personal cloud account, unless the team provides clear documented instructions for obtaining access (e.g. a read-only public link, a screenshot set with an explanation, or a self-hosted instance that can be started via `docker-compose up`).
- The dashboard or visualisation code must be **reproducible**: the grader must be able to run or rebuild it from the repository using documented instructions.

### 3.4 Teams of 3: cloud-hosted dashboard

- **Teams of 3** must deploy or host the dashboard (or at least the data it reads from) on the **cloud** chosen in Task 03:
  - **Apache Superset / Metabase on cloud VM or container:** deployed to a cloud VM (e.g. AWS EC2, GCP Compute Engine, Azure VM) or container service (e.g. ECS, Cloud Run, Container Apps).
  - **Plotly Dash / Streamlit on cloud:** deployed to a managed app service or VM.
  - **Native cloud BI:** e.g. Amazon QuickSight, Google Looker Studio, or Azure Power BI Embedded (reading from cloud data sources).
- The dashboard must read its data from the **cloud storage** used in previous tasks (e.g. S3, GCS, ADLS). The task report must describe the deployment setup and how to access the dashboard.

### 3.5 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-hosted dashboard; reads from cloud storage).
- **IaC remains mandatory.** The infrastructure used to host the dashboard (e.g. VM, container service, or managed app) must be provisioned using the IaC technology from previous tasks. The task report must describe which IaC tool was used and which resources were provisioned.
- Each team member must contribute to the dashboard or data story; the task report must briefly describe each person's contribution (e.g. data pipeline connecting to dashboard, specific chart, data story narrative, IaC configuration).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 12, **one** task report (e.g. `documentation/task12_visualization_bi.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Dashboard or visualisation set

- At least one of the following must be present in the repository:
  - **Dashboard configuration files** (e.g. Superset JSON export, Metabase export, or Dash/Streamlit Python script).
  - **Static visualisation scripts** (e.g. Python notebooks or scripts that generate the required charts).
- Instructions to run or access the dashboard (start command, URL, or screenshot set with annotations) in **correct technical English**.

### 4.3 Screenshots

- At least **5 screenshots** of the dashboard (one per chart or panel) must be saved in the repository (e.g. in `data_examples/` or a dedicated `screenshots/` folder). Screenshots must be annotated or captioned in the task report.

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task12_visualization_bi.md`) that includes:
  - **Tool choice:** which BI / visualisation tool was used and why it was chosen.
  - **Chart descriptions:** for each of the ≥ 5 charts, a description of what it shows, what data it reads from, and what insight it communicates.
  - **Data story:** project context, walkthrough of key insights, and at least two concrete business insights or recommendations.
  - **Interactivity:** which charts are interactive and how.
  - **How to run / access** the dashboard (start command, URL, or screenshot-based instructions).
  - For teams of 3: cloud deployment details (service used, URL or access instructions) and how the dashboard reads from cloud storage.
  - For teams of 4: same as teams of 3, plus IaC resources provisioned for dashboard hosting and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation and accessible to a non-technical stakeholder.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 12 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 12** (e.g. "Visualization & BI – interactive dashboard with Superset / Dash"). The task must be clearly identifiable as the visualisation deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 12. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. at least 5 charts built, data story written, dashboard accessible, screenshots saved, report updated).

---

## 6. Grading (Task 12)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| At least 5 charts / panels covering ≥ 3 project result aspects (overview, analytics, ML, streaming/graph, business summary) | 3 | 2.5 | 2.5 |
| At least 1 interactive chart (or parameterised code equivalent with justification) | 1 | 1 | 1 |
| Data story: project context, insights walk-through, ≥ 2 concrete business insights/recommendations | 2 | 1.5 | 1.5 |
| Screenshots (≥ 5) saved and captioned in report; dashboard reproducible from repository | 2 | 1 | 1 |
| Team of 3: dashboard deployed on cloud (or reads from cloud storage); access documented | — | 2 | — |
| Team of 4: cloud deployment + IaC for hosting infrastructure + each member's contribution described | — | — | 2 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 1 | 1.5 |
| Clear instructions to run or access the dashboard | 1 | 0.5 | 0.5 |
| At least 1 GitHub Project task for Task 12 | — | 0.5 | 0.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of Apache Superset, Metabase, or Plotly Dash.
- Mandatory choice of colour scheme or visual design standards.
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 12)

| Requirement | Applies to |
|-------------|------------|
| At least 5 distinct charts/panels covering ≥ 3 result aspects (overview, analytics, ML, streaming/graph, business summary) | All teams |
| At least 1 interactive chart (or parameterised code with justification) | All teams |
| Data story: project context, key insights, ≥ 2 business insights or recommendations | All teams |
| Screenshots (≥ 5) saved and captioned in task report | All teams |
| Dashboard or chart code reproducible from repository | All teams |
| Instructions to run or access the dashboard (start command, URL, or screenshot-based) | All teams |
| Task report in documentation/ (tool choice, chart descriptions, data story, interactivity, how to run; correct technical English) | All teams |
| Team of 3: cloud-hosted or cloud-connected dashboard; access documented | Teams of 3 |
| Team of 4: cloud deployment + IaC for hosting; each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 12 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
