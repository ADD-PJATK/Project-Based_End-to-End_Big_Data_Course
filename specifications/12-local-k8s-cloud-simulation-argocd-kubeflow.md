# Task 12 — Local “Cloud Simulation” on Kubernetes (Argo CD + Kubeflow)

This document defines an **optional** path for teams who want to **simulate cloud hosting locally** on Kubernetes for **Task 12 (Visualization & BI)**.

It supplements the official Task 12 specification.

> **Hard requirements for this add-on**
> - Use **Argo CD** (GitOps) so the grader can monitor the dashboard deployment.
> - Use **Kubeflow** for at least one pipeline/experiment that produces or refreshes dashboard-ready data.
> - In the **Task 12 report (`documentation/task12_visualization_bi.md`)** include **screenshots** proving both Argo CD and Kubeflow usage (in addition to dashboard screenshots required by Task 12).

---

## 1) Scope: what you must deploy

You must deploy at least one of the following dashboard options into Kubernetes:
- **Apache Superset** (recommended), or
- **Metabase**, or
- **Streamlit / Dash** app.

The deployment must be managed via **Argo CD**.

---

## 2) GitOps structure (Argo CD required)

Expected repo layout example:

```
infra/
  argocd/applications/
  k8s/
    bi/
      base/
      overlays/local/
```

Minimum expectation:
- Argo CD Application YAML for the BI stack.
- Kubernetes manifests/Helm/Kustomize for:
  - dashboard service (Superset/Metabase/Streamlit/Dash)
  - any required dependencies (e.g. a database)

---

## 3) Task 12-specific expectations (local “cloud simulation”)

### 3.1 Dashboard accessibility
The dashboard must be accessible to the grader from the local setup:
- document the URL/port-forward steps, and
- provide screenshots (already required by Task 12).

### 3.2 Reproducibility
Document:
- how Argo CD syncs the dashboard from Git,
- how to start the local cluster,
- how to access the UI.

---

## 4) Kubeflow requirement (Task 12)

Kubeflow must be used to produce or refresh **dashboard-ready artifacts**.

Accepted examples:
- A Kubeflow Pipeline that exports:
  - Task 05 analytics results (aggregations) for BI,
  - Task 07 cluster distributions,
  - Task 08 recommendation metrics,
  - Task 10 windowed streaming outputs,
  - Task 11 PageRank top-K tables,
  into a single “BI dataset” directory or database table.

Minimum evidence:
- Pipeline parameters (date range, top-K, refresh mode).
- One successful run producing artifacts that the dashboard reads.

---

## 5) Mandatory screenshots (must be included in Task 12 report)

Store screenshots in repo (e.g. `data_examples/screenshots/task12/`) and embed them into `documentation/task12_visualization_bi.md`.

### 5.1 Argo CD screenshots (required)
- Argo CD app showing:
  - **Synced** status
  - **Healthy** status
  - deployed dashboard resources

### 5.2 Kubeflow screenshots (required)
- Kubeflow Pipelines UI showing:
  - pipeline graph or run list
  - at least one run that generates dashboard-ready artifacts

### 5.3 Dashboard screenshots (still required by Task 12 spec)
- At least **5 dashboard screenshots** (one per chart/panel), captioned in the report.

---

## 6) What to add to the Task 12 report

Add a section like:

### “Local cloud simulation (Kubernetes + Argo CD + Kubeflow)”

Include:
- cluster type (kind/k3d/minikube) + how to start
- Argo CD app name + repo path
- Kubeflow pipeline name + what it produces for the dashboard
- where screenshots are stored in repo

