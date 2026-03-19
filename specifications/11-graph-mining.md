# Task 11 — Graph Mining (Week 11)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the eleventh assignment: performing **graph analytics** on the project dataset(s) to discover structural patterns, central nodes, and communities. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team's responsibility.

The outcome is a **runnable graph analysis pipeline** that constructs a graph from project data, computes graph metrics (including PageRank), and identifies communities or structural patterns. Results must be interpreted in the context of the project domain and documented in a task report.

**Expected result of this task (summary):**
- **Repository structure:** `data_examples/`, `documentation/` (with one task report for Task 11), and code (scripts or notebooks) in a clear location.
- **Graph construction:** a graph (nodes and edges) built from the project data and documented with schema, size (node/edge counts), and construction logic.
- **Graph analytics pipeline:** a runnable artifact that computes at least PageRank and one additional metric (degree distribution, community detection, or betweenness/closeness centrality).
- **One task report** in the documentation folder: how the graph was built, which metrics were computed, what the results mean for the project domain, and how to reproduce the analysis; written in **consistent language** and **correct technical English**.

---

## 2. Context from the course

The course README for Week 11 emphasises:

- **Graph analytics** — analysing relationships and structural properties of networks.
- **PageRank** — a ranking algorithm that identifies important nodes in a directed graph.
- **Network analysis** — degree distributions, centrality, community detection.
- **Lab:** graph analysis using **Spark GraphX** and **NetworkX**.

Teams are expected to use **Spark GraphX** (via PySpark's `graphframes` library, which provides a DataFrame-based graph API on top of GraphX) for large graphs, or **NetworkX** (Python) for smaller graphs or supplementary analysis. The choice must be justified based on graph size and documented in the task report.

---

## 3. Graph analytics requirements

### 3.1 Graph construction

- The team must **construct a graph** from the project dataset(s):
  - Define **nodes** (vertices): what entities are nodes (e.g. users, products, documents, transactions, locations).
  - Define **edges**: what relationships are edges (e.g. user–user interaction, co-purchase, similarity above a threshold, network connection). Edges may be directed or undirected; the choice must be documented.
  - Assign **properties** to nodes and/or edges if the data supports it (e.g. edge weight, node attribute).
- The graph construction logic must be reproducible (implemented in code, not manual).
- The constructed graph must be documented: node count, edge count, and whether it is directed or undirected.

If the primary project dataset does not naturally produce a graph (e.g. pure tabular sensor data with no relational structure), the team must propose and justify an alternative graph construction (e.g. a similarity graph where nodes are records and edges connect records with similarity above a threshold, or a bipartite graph from the recommendation task). The approach must be documented in the task report.

### 3.2 PageRank (mandatory)

- All teams must compute **PageRank** on the constructed graph (directed, or adapted for undirected as appropriate).
- Results must include:
  - The **top-K nodes by PageRank score** (e.g. top 10 or 20), documented as a table.
  - A **business interpretation**: what does a high PageRank mean for these nodes in the project domain (e.g. "top-ranked nodes are the most influential users in the social network", "most cited documents", "most central products in the co-purchase graph")?
  - The **convergence parameters** used (e.g. damping factor, number of iterations or tolerance), documented in the task report.

### 3.3 Additional graph metrics (at least one)

All teams must compute at least **one additional graph metric** from the following options:

| Metric | Description | Recommended tool |
|--------|-------------|------------------|
| **Degree distribution** | Histogram of node in-degree and/or out-degree; identify hubs (high-degree nodes) | GraphFrames, NetworkX |
| **Connected components** | Count and size distribution of weakly or strongly connected components | GraphFrames, NetworkX |
| **Community detection** | Identify clusters or communities (e.g. Label Propagation Algorithm in GraphFrames, Louvain in NetworkX) | GraphFrames `LPA`, NetworkX |
| **Betweenness centrality** | Nodes that act as bridges between communities; high centrality = high influence on information flow | NetworkX (for smaller graphs) |
| **Triangle count** | Local clustering coefficient or global triangle count; indicates density of connections | GraphFrames, NetworkX |
| **Shortest path / diameter** | Average shortest path length or graph diameter (compute on a sample for large graphs) | NetworkX |

The chosen metric must be computed, results documented (summary statistics or top-K nodes), and interpreted in the project context.

### 3.4 Visualisation

- At least one **graph visualisation** must be included (e.g. a subgraph of the top-30 nodes by PageRank, or a community-coloured layout):
  - Use **NetworkX** with `matplotlib` or `pyvis` for visualisation (note: for large graphs, visualise a representative subgraph or sample).
  - The visualisation must be saved as an image file in the repository (e.g. in `data_examples/`) and referenced in the task report.
  - A brief caption must be included explaining what the visualisation shows.

### 3.5 Teams of 3: cloud-based graph analytics

- **Teams of 3** must run the graph analytics pipeline using **cloud compute** on the cloud chosen in Task 03:
  - **AWS:** GraphFrames on EMR, or NetworkX in a SageMaker notebook with data on S3.
  - **GCP:** GraphFrames on Dataproc, or NetworkX on a Vertex AI notebook with data on GCS.
  - **Azure:** GraphFrames on HDInsight or Synapse Spark, or NetworkX on Azure ML with data on ADLS.
- The graph must be constructed from data in cloud storage (as stored in previous tasks). The task report must state which cloud service was used and how data was read.
- If the team has multiple datasets (each member's dataset), each team member should perform graph analysis on their own dataset or contribute a distinct part of the analysis.

### 3.6 Teams of 4: cloud, IaC, and each member's contribution

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud-based graph analytics).
- **IaC remains mandatory.** Any new cloud resources provisioned for graph analytics compute must be defined or extended in the IaC configuration. The task report must describe what was added or changed.
- Each team member must contribute to the graph analytics pipeline; the task report must briefly describe each person's contribution (e.g. graph construction for dataset X, PageRank computation, community detection, visualisation).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** and **documentation/** must be maintained. For Task 11, **one** task report (e.g. `documentation/task11_graph_mining.md`) **per group**; teams of 3 and 4 contribute to the same report and maintain one consistent quality standard (**correct technical English**).

### 4.2 Graph analytics pipeline

- At least one **runnable** artifact (script or notebook) that:
  - Constructs the graph from project data (reads from storage or documented path).
  - Computes PageRank and at least one additional metric.
  - Produces a visualisation of the graph (subgraph if necessary).
  - Saves results to a documented location.
- Instructions to run (environment, command or notebook steps) in **correct technical English**.

### 4.3 Graph outputs

- **Top-K PageRank table** (at least top 10 nodes) saved as a CSV or Markdown table in `data_examples/` or in the task report.
- **Visualisation image** saved to the repository (e.g. `data_examples/graph_visualisation.png`).
- **Additional metric result** documented (summary statistics or top-K table, as appropriate).

### 4.4 Task report (documentation)

- A **task report** in **Markdown** in the documentation folder (e.g. `documentation/task11_graph_mining.md`) that includes:
  - **Graph construction:** node and edge definitions, whether directed or undirected, node/edge counts, construction logic, and justification (or alternative construction if applicable, Section 3.1).
  - **PageRank:** top-K nodes, convergence parameters, and business interpretation.
  - **Additional metric:** which metric was computed, key results (summary or top-K), and interpretation in the project domain.
  - **Visualisation:** description of what the visualisation shows and where the file is saved.
  - **Tools used:** GraphFrames vs NetworkX choice and justification.
  - **How to run** the pipeline (environment, command or notebook instructions).
  - For teams of 3: cloud compute service used and how data was read from cloud storage.
  - For teams of 4: same as teams of 3, plus IaC changes and brief description of each member's contribution.

The report must be in **consistent language** and **correct technical English**, readable as technical documentation.

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create a dedicated GitHub Project **task** for Task 11 (optional).

### 5.2 Teams of 3

- In the **GitHub Project**, the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 11** (e.g. "Graph mining – PageRank and community detection"). The task must be clearly identifiable as the graph mining deliverable.

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 11. Each task must have **clear acceptance criteria** (what "task completed" means), written in **correct technical English** and aligned with this specification (e.g. graph constructed, PageRank computed with top-K table, additional metric computed, visualisation saved, report updated).

---

## 6. Grading (Task 11)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Graph construction: nodes and edges defined, documented (counts, direction, logic) | 2 | 2 | 2 |
| PageRank computed: top-K table, convergence parameters, business interpretation | 3 | 2.5 | 2.5 |
| Additional metric (degree distribution, community detection, centrality, etc.) computed and interpreted | 2 | 1.5 | 1.5 |
| Graph visualisation saved and referenced in report | 1 | 0.5 | 0.5 |
| Team of 3: cloud compute used for graph analytics; documented in report | — | 2 | — |
| Team of 4: cloud + IaC changes + each member's contribution described | — | — | 2 |
| Repository structure (data_examples/, documentation/) and one task report (consistent, correct technical English) | 1 | 0.5 | 0.5 |
| Clear instructions on how to run the pipeline | 1 | 0.5 | 0.5 |
| At least 1 GitHub Project task for Task 11 | — | 0.5 | 0.5 |
| 4 GitHub Project tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader's discretion. All written deliverables must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step setup of GraphFrames, NetworkX, or the cloud environment.
- Mandatory choice of graph visualisation library (NetworkX + matplotlib, pyvis, Gephi, or similar are all acceptable).
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 11)

| Requirement | Applies to |
|-------------|------------|
| Graph constructed from project data (nodes, edges defined and documented; node/edge counts stated) | All teams |
| PageRank computed; top-K nodes table; convergence parameters documented; business interpretation in report | All teams |
| At least one additional graph metric (degree distribution / community detection / centrality / etc.) computed and interpreted | All teams |
| Graph visualisation (subgraph if needed) saved as image in repository and referenced in report | All teams |
| Instructions to run the pipeline (environment, command) | All teams |
| Task report in documentation/ (graph construction, PageRank, additional metric, visualisation, tools, how to run; correct technical English) | All teams |
| Alternative graph construction documented and justified if dataset does not naturally form a graph | Teams where applicable |
| Team of 3: cloud compute for graph analytics; documented in report | Teams of 3 |
| Team of 4: cloud + IaC changes + each member's contribution described | Teams of 4 |
| At least 1 GitHub Project task for Task 11 | Teams of 3 |
| 4 GitHub Project tasks with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
