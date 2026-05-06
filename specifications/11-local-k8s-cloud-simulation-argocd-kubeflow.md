# Task 11 — Local “Cloud Simulation” on Kubernetes (Argo CD + Kubeflow)

This document defines an **optional** path for teams who want to **simulate cloud deployment locally** using Kubernetes for **Task 11 (Graph Mining)**.

It supplements the official Task 11 specification.

> **Hard requirements for this add-on**
> - Use **Argo CD** (GitOps) to deploy and monitor your graph-mining pipeline.
> - Use **Kubeflow** for at least one Task-11-relevant pipeline/experiment.
> - In the **Task 11 report (`documentation/task11_graph_mining.md`)** include **screenshots** proving both Argo CD and Kubeflow usage.

---

## 1) Scope: what you must run in Kubernetes

You must run Task 11 as a Kubernetes-deployed pipeline (job/notebook container) that:
- builds the graph (nodes/edges) from your project data,
- computes **PageRank**,
- computes at least **one additional metric**,
- produces at least **one graph visualisation** image saved in the repo.

---

## 2) GitOps structure (Argo CD required)

Expected repo layout example:

```
infra/
  argocd/applications/
  k8s/
    graph-mining/
      base/
      overlays/local/
```

Argo CD must manage the resources (manifests/Helm/Kustomize) used for Task 11.

---

## 3) Task 11-specific expectations

### 3.1 Graph job/container
Run Task 11 as:
- `Job` (recommended), or
- `Deployment` if you run a service (not required).

The Task 11 report must document:
- where the job reads data from (path + format),
- node/edge definitions and counts,
- PageRank convergence parameters,
- where outputs are written (paths + formats).

### 3.2 Output artifacts
At minimum, store in repo (e.g. `data_examples/graph/`):
- Top-K PageRank table (CSV or Markdown)
- Additional metric output (CSV/Markdown)
- Graph visualisation image (PNG)

---

## 4) Kubeflow requirement (Task 11)

Kubeflow must be used to run (or orchestrate) your graph-mining work.

Accepted examples:
- A Kubeflow Pipeline that runs:
  1) “graph construction” step
  2) “PageRank + metrics” step
  3) “visualisation export” step
- A pipeline that runs the full graph job and exports artifacts to a shared volume/object-store-like service and then copies samples to `data_examples/`.

Minimum evidence:
- Pipeline parameters (graph threshold, top-K, iterations/tolerance).
- One run with produced artifacts referenced in the Task 11 report.

---

## 5) Mandatory screenshots (must be included in Task 11 report)

Store screenshots in repo (e.g. `data_examples/screenshots/task11/`) and embed them into `documentation/task11_graph_mining.md`.

### 5.1 Argo CD screenshots (required)
- Argo CD app showing:
  - **Synced** status
  - **Healthy** status
  - the Task 11 Job resource (and any dependencies)

### 5.2 Kubeflow screenshots (required)
- Kubeflow Pipelines UI showing:
  - pipeline graph or run list
  - at least one run producing Task 11 artifacts

---

## 6) What to add to the Task 11 report

Add a section like:

### “Local cloud simulation (Kubernetes + Argo CD + Kubeflow)”

Include:
- cluster type (kind/k3d/minikube) + how to start
- Argo CD app name + repo path
- Kubeflow pipeline name + what it runs for Task 11
- where screenshots are stored in repo

