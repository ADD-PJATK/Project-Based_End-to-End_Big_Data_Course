# Task 13 — Final Project Demo (Week 13)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the thirteenth and final assignment: presenting the **complete end-to-end Big Data project** in a live demonstration. It is a **business specification**, not a step-by-step tutorial. Presentation style and demo logistics are the team's responsibility.

The outcome is a **final project demonstration** — a live (or pre-recorded) presentation that walks through the complete data pipeline, machine learning results, visualization dashboard, and business insights derived over the course of the semester. Additionally, all code, documentation, and infrastructure must be in a **complete, clean, and reproducible** state in the repository by the time of the demo.

**Expected result of this task (summary):**
- **Repository in final state:** all code runnable, all documentation complete and consistent, `README.md` updated to reflect the full project.
- **Live demo (or pre-recorded video):** covers all four required sections (pipeline architecture, ML results, visualization dashboard, business insights) within the allocated time.
- **Presentation slides:** structured deck covering all four sections; submitted to the repository or as a link before the demo.
- **Final documentation review:** the `documentation/` folder must be internally consistent, written in correct technical English across all task reports (Tasks 01–12).

---

## 2. Context from the course

The course README for Week 13 specifies that students present:

1. **Data pipeline architecture**
2. **Machine learning results**
3. **Visualization dashboard**
4. **Business insights**

And deliver:

- **Code repository** — complete, well-organised, and reproducible.
- **Documentation** — all task reports in the `documentation/` folder, the repository `README.md`, and any supporting materials.
- **Presentation** — slides presented during the demo session.

---

## 3. Demo requirements

### 3.1 Demo structure (all teams)

The demonstration must address all four sections below, in any order the team finds logical. The demo session duration is set by the course schedule; each team must plan their content to fit within the allocated time.

| Section | Minimum content |
|---------|----------------|
| **1. Data pipeline architecture** | Overview of the full pipeline (data acquisition → storage → processing → ML → streaming → graph → visualization). Must show actual artefacts (e.g. the Spark SQL notebook, the Kafka producer script, the IaC code) rather than describing them only in words. |
| **2. Machine learning results** | Summary of results from Tasks 07 (clustering) and 08 (recommendations), and optionally Task 10 (streaming ML). Must include at least one evaluation metric value and its interpretation. Must show cluster visualisations or top-K recommendation tables from the repository. |
| **3. Visualization dashboard** | Live demonstration of the dashboard built in Task 12, or a walkthrough of the screenshots if a live demo is not feasible. Must show at least 5 charts and explain what each one communicates. |
| **4. Business insights** | At least **three concrete business insights** derived from the full project. Each insight must be: (a) tied to a specific result (e.g. a specific cluster, a recommendation metric, a graph metric, a streaming pattern), (b) stated in business language accessible to a non-technical stakeholder, and (c) actionable (i.e. suggests a decision or next step). |

### 3.2 Presentation slides (all teams)

- Teams must prepare a **presentation slide deck** structured around the four sections above.
- Slides must be submitted to the repository (as a PDF or link) **before the demo session**.
- Slides must be written in **correct technical English** (or in English with a glossary of Polish terms if the course is delivered partly in Polish — the technical parts must be in English).
- Recommended structure: title slide, team overview, pipeline diagram, one slide per pipeline stage (Tasks 01–12 briefly), ML results, dashboard screenshots, business insights, and conclusion.

### 3.3 Repository final state (all teams)

By the demo session, the repository must be in a **complete and clean** final state:

- **All code** must be runnable (or clearly documented as requiring environment setup) from the repository.
- **All task reports** (Tasks 01–12) must be present in `documentation/` and internally consistent (same terminology, correct technical English, consistent structure).
- **`README.md`** in the repository root must be updated to reflect the full project: dataset(s), project theme, pipeline overview, and instructions for running each major component (or a reference to the relevant task report).
- **`data_examples/`** must contain up-to-date samples representing the current state of the data (post-cleaning, post-feature engineering, and/or post-ML).
- **No placeholders, broken links, or TODO comments** in documentation files.
- Dependencies must be documented (e.g. `requirements.txt`, `environment.yml`, or equivalent).

### 3.4 Teams of 3: cloud infrastructure summary

- In addition to the general demo requirements, **teams of 3** must include in their presentation a **cloud infrastructure summary** slide or section:
  - Which cloud provider was used (AWS, GCP, or Azure).
  - A list of cloud services used across all tasks (e.g. EMR, S3, MSK, SageMaker, etc.).
  - A brief assessment: what worked well on the cloud, and what challenges were encountered.
- This summary may be delivered during the demo or as part of the slides.

### 3.5 Teams of 4: cloud infrastructure + IaC summary + individual contributions

- **Teams of 4** must fulfil all requirements for teams of 3 (cloud infrastructure summary).
- In addition, teams of 4 must include:
  - **IaC summary:** which IaC tool was used, what resources were managed across the semester (a list by task), and a brief statement on reproducibility (i.e. can the full cloud infrastructure be reproduced from the IaC code alone?).
  - **Individual contributions summary:** a slide or section clearly attributing each team member's primary contributions across the semester (tasks, code components, cloud configuration). Each member must speak during the demo.

---

## 4. Deliverables (all teams)

### 4.1 Repository in final state

- All code runnable; all task reports complete and consistent; `README.md` updated; `data_examples/` current; no broken links or TODOs in documentation; dependencies documented.

### 4.2 Presentation slides

- Slide deck (PDF or link) committed to the repository or shared via a documented link before the demo session. Must cover all four required sections (Section 3.1).

### 4.3 Live demo (or pre-recorded video)

- A live demonstration during the scheduled demo session, covering all four sections (Section 3.1). If a live demo is not possible (e.g. due to environment issues), a **pre-recorded video** covering the same content is acceptable, provided it is submitted before the session and the team is available for questions during the session.

### 4.4 Final documentation review

- All files in `documentation/` reviewed for consistency: same terminology, structure, and correct technical English throughout. The team is responsible for this review; inconsistencies discovered by the grader will be penalised.

---

## 5. GitHub Project final state (by team size)

### 5.1 Teams of 2

- No specific GitHub Project requirements for Task 13.

### 5.2 Teams of 3

- All GitHub Project tasks from Tasks 01–12 must be **closed or marked as done** in the GitHub Project by the demo session.

### 5.3 Teams of 4

- Same as teams of 3: all tasks closed or marked as done.
- The GitHub Project must provide a clear **summary of the full semester** (e.g. as a Project description or a pinned note): how many tasks were completed, which Epics were closed, and any open items with explanation.

---

## 6. Grading (Task 13 — Final Demo)

The Final Demo is graded separately from the project tasks and contributes **15% of the course grade** (as stated in the Evaluation Model). There is no separate 10-point score for Task 13; the grading below describes how the 15% Final Presentation weight is assessed.

| Criterion | All teams | Teams of 3 (additional) | Teams of 4 (additional) |
|-----------|-----------|--------------------------|--------------------------|
| Demo covers all 4 sections: pipeline architecture, ML results, dashboard, business insights | Core | Core | Core |
| At least 3 concrete, actionable business insights stated and tied to specific results | Core | Core | Core |
| Repository in final state: all code runnable, all reports complete and consistent, README updated | Core | Core | Core |
| Slides submitted before session; structured around the 4 sections; correct technical English | Core | Core | Core |
| Dashboard demonstrated live (or via screenshots/video) with ≥ 5 charts explained | Core | Core | Core |
| Cloud infrastructure summary slide (services used, lessons learned) | — | Required | Required |
| IaC summary (tool, resources managed, reproducibility statement) | — | — | Required |
| Individual contributions slide; each member speaks during demo | — | — | Required |
| GitHub Project: all tasks closed; summary of full semester (teams of 4) | — | Required | Required |

The grader will assess the quality of the demo holistically: clarity of explanation, depth of technical understanding shown, quality of business insights, and coherence of the presentation as a whole. Partial fulfilment of any criterion may result in partial credit.

---

## 7. Out of scope for this specification

- Mandatory presentation software (PowerPoint, Google Slides, reveal.js, or any other tool is acceptable).
- Exact demo session duration (defined by the course schedule).
- Exact submission deadline for slides (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 13)

| Requirement | Applies to |
|-------------|------------|
| Demo covers all 4 sections: pipeline architecture, ML results, dashboard, business insights | All teams |
| At least 3 concrete, actionable business insights stated with ties to specific results | All teams |
| Repository in final state: code runnable, all task reports (01–12) complete and consistent, README updated, data_examples/ current, no TODOs or broken links | All teams |
| Dependencies documented (requirements.txt, environment.yml, or equivalent) | All teams |
| Slide deck (PDF or link) submitted to repository before demo session; covers 4 required sections; correct technical English | All teams |
| Live demo (or pre-recorded video) of dashboard; ≥ 5 charts explained | All teams |
| Cloud infrastructure summary: cloud provider, list of services used per task, lessons learned | Teams of 3 and 4 |
| IaC summary: tool, resources managed across semester, reproducibility statement | Teams of 4 |
| Individual contributions slide; each member speaks during demo | Teams of 4 |
| All GitHub Project tasks closed; semester summary in GitHub Project (teams of 4) | Teams of 3 and 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
