# Task 09 — Local “Cloud Simulation” on Kubernetes (Argo CD + Kubeflow)

This document defines an **optional** path for teams who want to **simulate cloud deployment locally** using a Kubernetes cluster, while still keeping the project **observable and reproducible**.

This add-on applies to **Task 09 (Stream Processing)** and supplements the official Task 09 specification.

> **Hard requirements for this add-on**
> - You must use **Argo CD** (GitOps) so the grader can monitor deployments.
> - You must use **Kubeflow** (at least one pipeline/experiment relevant to Task 09).
> - In the **Task 09 report (`documentation/task09_stream_processing.md`)** you must include **screenshots** proving both Argo CD and Kubeflow usage.

---

## 1) What “local cloud simulation” means (for grading)

You are not required to use a real public cloud if you choose this add-on.  
Instead, you deploy your Task 09 pipeline into a local Kubernetes cluster and provide **cloud-like** properties:

- **GitOps deployment** (Argo CD reads from Git and applies Kubernetes manifests / Helm / Kustomize).
- **Clear service boundaries** (Kafka + producer + consumer as Kubernetes workloads).
- **Observability evidence** (Argo CD application health/sync, Kubeflow run UI evidence).
- **Reproducibility** (a grader can follow your steps to recreate the deployment).

---

## 2) Minimal technical setup (allowed choices)

### 2.1 Local Kubernetes
Use one of:
- `kind`, `k3d`, `minikube`, or Docker Desktop Kubernetes.

### 2.2 Argo CD (required)
Deploy Argo CD to the cluster and manage your project through **Argo CD Applications**.

### 2.3 Kubeflow (required)
Install Kubeflow (any working local distribution is acceptable) and use it for **one Task-09-related pipeline** (see section 5).

---

## 3) Required repository structure (GitOps-friendly)

Add a dedicated folder, for example:

```
infra/
  k8s/
    base/
    overlays/
      local/
  argocd/
    applications/
```

Minimum expectation:
- One Argo CD Application YAML that points to your repo path.
- Kubernetes manifests / Helm chart / Kustomize that deploy:
  - Kafka (and dependencies like Zookeeper if used)
  - Task 09 producer
  - Task 09 consumer

---

## 4) Task 09-specific expectations in Kubernetes

### 4.1 Kafka in Kubernetes
You must run Kafka in the cluster (single-broker is acceptable for local simulation).

Evidence expected in the Task 09 report:
- What you deployed (Kafka image/chart, broker count, how it is exposed inside cluster).
- How you validated Kafka is running (topic list, broker logs, or readiness state).

### 4.2 Producer and consumer as Kubernetes workloads
Your producer and consumer must run as Kubernetes resources (e.g. `Deployment`, `Job`, or `CronJob`).

Evidence expected:
- How you configured broker address/topic via ConfigMap/Env.
- Logs or output excerpt showing producing and consuming works end-to-end.

---

## 5) Kubeflow requirement (Task 09)

Kubeflow must be used for at least one pipeline/experiment relevant to Task 09.

Accepted examples:
- A Kubeflow Pipeline that runs a “replay producer” step (publishing events) and a “consumer validation” step (checks records were written to sink).
- A Pipeline that validates Kafka connectivity and topic existence, then starts a short-lived producer job and collects consumption metrics.

Minimum evidence:
- A Kubeflow run with parameters (topic name, message rate, duration).
- Pipeline outputs or logs saved and referenced.

---

## 6) Mandatory screenshots (must be included in Task 09 report)

In `documentation/task09_stream_processing.md`, include screenshots (stored in repo, e.g. `data_examples/screenshots/task09/`):

### 6.1 Argo CD screenshots (required)
- Argo CD **Applications list** showing your Task 09 app.
- The Task 09 app details page showing:
  - **SYNC status** (Synced/OutOfSync)
  - **HEALTH status** (Healthy/Degraded)
  - Deployed resources (Kafka + producer + consumer)

### 6.2 Kubeflow screenshots (required)
- Kubeflow Pipelines UI showing:
  - the pipeline definition (name + graph) **or** run list
  - at least one **successful run** (or clearly explained failure with fix steps)

---

## 7) What to write in the Task 09 report (extra section)

Add a short section, for example:

### “Local cloud simulation (Kubernetes + Argo CD + Kubeflow)”

Include:
- Cluster type (kind/k3d/minikube) and how to start it.
- Argo CD app name + repo path it watches.
- Kubeflow pipeline name + what it does for Task 09.
- Where screenshots are stored in the repo.

