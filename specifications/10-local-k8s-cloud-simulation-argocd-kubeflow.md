# Task 10 — Local “Cloud Simulation” on Kubernetes (Argo CD + Kubeflow)

This document defines an **optional** path for teams who want to **simulate cloud deployment locally** using a Kubernetes cluster for **Task 10 (Streaming Analytics)**.

It supplements the official Task 10 specification.

> **Hard requirements for this add-on**
> - Use **Argo CD** (GitOps) to deploy and monitor your Task 10 streaming job.
> - Use **Kubeflow** for at least one Task-10-relevant pipeline/experiment.
> - In the **Task 10 report (`documentation/task10_streaming_analytics.md`)** include **screenshots** proving both Argo CD and Kubeflow usage.

---

## 1) Scope: what you must run in Kubernetes

At minimum, your Kubernetes-deployed system must include:
- The **Kafka layer** from Task 09 (or an equivalent message bus), running and reachable from the streaming job.
- A **streaming analytics job** (Spark Structured Streaming or Flink) running as a Kubernetes workload.
- A **persistent output sink** (file/object store/database) OR a clearly documented in-cluster storage volume + exported sample outputs.

---

## 2) GitOps structure (Argo CD required)

Expected repo layout example:

```
infra/
  argocd/applications/
  k8s/
    streaming-analytics/
      base/
      overlays/local/
```

Minimum expectation:
- An Argo CD Application that deploys **Kafka + streaming job + sink** (can be one app or multiple apps).
- Manifests/Helm/Kustomize that are reproducible from scratch.

---

## 3) Task 10-specific expectations

### 3.1 Streaming job deployment
Run the job as:
- `Deployment` (long-running), or
- `Job` / `CronJob` (runs long enough to show multiple micro-batches/windows).

The report must document:
- Kafka topic(s) consumed
- window type and duration
- checkpoint location
- output sink path/format

### 3.2 Checkpointing in Kubernetes
Checkpointing must be configured and persisted to:
- a mounted volume (PVC) **or**
- an object-store-like service running in cluster (acceptable for local simulation).

---

## 4) Kubeflow requirement (Task 10)

Kubeflow must be used for a pipeline/experiment that is relevant to streaming analytics.

Accepted examples:
- A pipeline that deploys the streaming job (apply manifests), waits for readiness, then triggers a short producer replay and validates windowed outputs.
- A pipeline that runs a **stream replay** step and a **streaming job** step, then collects aggregated outputs to `data_examples/`.
- A pipeline that runs a batch “model export” step (Task 07/08) and then a streaming inference step (Task 10).

Minimum evidence:
- Pipeline parameters (window duration, K, topic name, runtime).
- One run with saved outputs and a short interpretation in the Task 10 report.

---

## 5) Mandatory screenshots (must be included in Task 10 report)

Store screenshots in repo (e.g. `data_examples/screenshots/task10/`) and embed them into `documentation/task10_streaming_analytics.md`.

### 5.1 Argo CD screenshots (required)
- Argo CD Application page with:
  - **Synced** status
  - **Healthy** status
  - visible resources for the streaming job (and Kafka if included)

### 5.2 Kubeflow screenshots (required)
- Kubeflow Pipelines UI showing:
  - pipeline graph or run list
  - at least one run tied to Task 10

---

## 6) What to add to the Task 10 report

Add a section like:

### “Local cloud simulation (Kubernetes + Argo CD + Kubeflow)”

Include:
- cluster type (kind/k3d/minikube) + how to start
- Argo CD app name(s) + repo path(s)
- Kubeflow pipeline name + what it validates for Task 10
- where screenshots live in repo

