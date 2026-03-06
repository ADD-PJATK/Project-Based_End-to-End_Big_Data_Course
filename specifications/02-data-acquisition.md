# Task 02 — Data Acquisition and Initial Quality Evaluation (Week 2)

**Business specification**  
Analysis of Large Data Sets (ADD) — Project-Based End-to-End Big Data Course

---

## 1. Purpose and scope

This document defines the **acceptance criteria and deliverables** for the second assignment: acquiring the initial dataset(s) and performing a **preliminary data quality evaluation**. It is a **business specification**, not a step-by-step tutorial. Implementation details are the team’s responsibility.

The outcome is the **initial dataset** available in the project repository (or with clear acquisition instructions), a **data_examples** folder with sample records, a **data validation script** that checks quality, and a **task report** in the project’s documentation. This establishes a baseline for later tasks (storage, processing, ML, visualization).

**Expected result of this task (summary):**
- **Appropriate structure in the repository:** e.g. `data_examples/`, `documentation/`, and scripts (e.g. in a dedicated folder or root) so that data, samples, reports, and code are clearly organised.
- **Validation script(s)** that implement the quality checks defined in Section 3 and produce a reproducible report.
- **One task report** for this assignment, written in **consistent language** and **correct technical English**, placed in the documentation area and readable as **technical documentation** (clear, structured, accessible to a reader who did not perform the task).

---

## 2. Data acquisition

- The team **must** have the dataset(s) chosen in Task 01 **acquired** and available for use (e.g. stored in the repo, or downloadable via a documented script/URL).
- **Teams of 2:** one shared dataset.
- **Teams of 3 or 4:** each team member **must** perform acquisition and quality checks **on their own dataset** (one dataset per person, as in Task 01).

### 2.1 Data examples (from this stage onwards)

- The team **must** create and maintain a **data_examples** folder (or equivalent) in the repository containing **a few sample records** that show how the data actually appears in the main dataset(s).
- Purpose: to give a quick, reproducible view of the data format and content without requiring access to the full dataset.
- **Teams of 2:** one set of samples for the shared dataset (e.g. a few rows for tabular data, a few documents or image thumbnails for text/image data).
- **Teams of 3 or 4:** samples for **each** dataset (each member’s dataset); samples may be in subfolders or clearly labelled (e.g. by dataset or owner) so that each main dataset is represented.

---

## 3. Preliminary data quality evaluation

All teams **must** perform a **preliminary evaluation of data quality**. Even if the source is trusted, a **validation script** is required so that quality checks are reproducible and documented.

### 3.1 Tabular data

The validation script **must** check at least:

| Check | Description |
|-------|-------------|
| **Missing values** | Identify nulls, empty cells, or placeholders (e.g. "N/A", "—") and report counts per column (or equivalent). |
| **Duplicates** | Detect duplicate rows (or key columns) and report how many duplicates exist. |
| **Consistency / encoding** | Detect inconsistencies in how the same type of information is recorded (e.g. mixed date formats, mixed units, inconsistent categorical labels, encoding issues). Report which fields were checked and what issues were found. |

The script must produce a **report** (e.g. printed summary, log file, or small report file) that states what was checked and the results. The report must be reproducible by running the script.

### 3.2 Non-tabular data (text)

For **text** datasets (e.g. documents, reviews, social posts), the validation script **must** check at least:

| Check | Description |
|-------|-------------|
| **Empty or too-short documents** | Count documents that are empty or below a reasonable minimum length; report counts. |
| **Encoding and format** | Verify character encoding (e.g. UTF-8) and report any files that fail to decode or use unexpected encodings. |
| **Duplicates** | Detect duplicate or near-duplicate documents (e.g. by hash or simple similarity) and report count. |
| **Basic statistics** | Report basic stats relevant to quality (e.g. document count, length distribution, vocabulary size or sample) so that the dataset scale and usability can be verified. |

The script must produce a **report** (e.g. printed summary or file) with the results. All descriptions and reports must be in **correct technical English**.

### 3.3 Non-tabular data (images)

For **image** datasets, the validation script **must** check at least:

| Check | Description |
|-------|-------------|
| **File integrity** | Verify that image files open correctly (no corrupted files); report count of valid vs invalid files. |
| **Format and dimensions** | Report format distribution (e.g. JPEG, PNG) and, where relevant, dimension/resolution consistency or distribution. |
| **Duplicates** | Detect duplicate images (e.g. by file hash or perceptual hash) and report count. |
| **Basic statistics** | Report total image count, size distribution, and any labels/metadata consistency if applicable. |

The script must produce a **report** with the results. All descriptions and reports must be in **correct technical English**.

### 3.4 Who performs the checks

- **Teams of 2:** the team performs the validation on the single shared dataset (one script and report).
- **Teams of 3 or 4:** **each** team member **must** run the appropriate checks **on their own dataset** and deliver their own validation script and report (or one repo with one script per dataset and one report per dataset, clearly attributed).

---

## 4. Deliverables (all teams)

### 4.1 Repository structure

- **data_examples/** (or equivalent): folder with **a few sample records** representative of the main dataset(s), as in Section 2.1. Must be present from this task onwards.
- **documentation/** (or equivalent, e.g. `docs/`): folder where **task reports** are stored. Each report must be a **single `.md` file per task** (e.g. `documentation/task02_data_acquisition.md` for this task). There is **one report per group per task**—not one per person. Students must achieve this through **appropriate commits** (e.g. one report file per task, updated by the whole team).
- **Teams of 3 or 4:** all members **must** contribute to the **same report file** for this task (e.g. by committing to one `documentation/task02_*.md`). The team **must** maintain **one consistent quality standard**: same tone, structure, and **correct technical English** across the whole document. The report is a single, coherent technical document for the group.

### 4.2 Initial dataset

- Dataset(s) available in or from the repository (e.g. data files, or a script that downloads them from a documented source).
- **Teams of 3 or 4:** each member’s dataset must be clearly identified (e.g. by folder, README, or script name).

### 4.3 Validation script(s)

- **At least one** executable script (e.g. Python) that implements the checks in Section 3 for the relevant data type (tabular, text, or images).
- The script must be runnable and produce a clear report (console output, log file, or generated report file).
- **Teams of 3 or 4:** one script per dataset (or one parameterised script run per dataset) so that each member’s dataset is validated.

### 4.4 Task report (quality evaluation) in documentation

- The quality evaluation must be written up as a **task report** in **Markdown (`.md`)** and placed in the **documentation** folder (see Section 4.1), e.g. `documentation/task02_data_acquisition.md`.
- **One report per group for this task** (one file). Teams of 3 or 4 contribute together to this single file and maintain one quality standard (consistent language and structure).
- The report must include:
  - What was checked (missing values, duplicates, consistency, and type-specific checks as in Section 3).
  - Main findings (e.g. number of missing values, duplicates, any consistency issues).
  - Any assumptions or limitations of the validation.
- The report must be written in **consistent language** and **correct technical English**, and must be **readable as technical documentation** (clear structure, accessible to someone who did not perform the task).

---

## 5. GitHub Project tasks (by team size)

### 5.1 Teams of 2

- No requirement to create GitHub Project **tasks** for this assignment (the repo and README from Task 01 are sufficient).

### 5.2 Teams of 3

- In the **GitHub Project** (created in Task 01), the team **must** create **at least one task** (Issue or Project task) that corresponds to **Task 02**. The task must be clearly identifiable as the “Data acquisition and quality evaluation” deliverable (e.g. by title or label).

### 5.3 Teams of 4

- In the **GitHub Project**, the team **must** create **one task per team member** (i.e. **4 tasks**) for Task 02. Each task must:
  - Be assigned to (or clearly associated with) one team member.
  - Include **clear acceptance criteria**: what “task completed” means (e.g. “Dataset X acquired; validation script runs and reports missing values, duplicates, consistency; quality summary added to repo”). Criteria must be written in **correct technical English** and aligned with this specification.

---

## 6. Grading (Task 02)

**Maximum score: 10 points per team** for the complete delivery of this task. The breakdown by team size is below; the sum of points for each column is 10.

| Criterion | 2-person | 3-person | 4-person |
|-----------|----------|----------|----------|
| Repository structure (data_examples/, documentation/) and one task report in documentation (consistent, correct technical English) | 3 | 1.5 | 1.5 |
| Initial dataset(s) acquired and available (each member’s dataset for 3–4) | 2 | 2 | 2 |
| Validation script implements required checks (tabular / text / images as applicable) | 3 | 3 | 3 |
| Script produces a clear, reproducible report | 2 | 2 | 2 |
| At least 1 GitHub Project task for Task 02 | — | 1.5 | 1.5 |
| 4 tasks with clear acceptance criteria (1 per person) | — | — | 0.5 |
| **Total** | **10** | **10** | **10** |

Partial fulfilment of a criterion may result in partial points at the grader’s discretion. All written deliverables (summaries, task descriptions, reports) must be in **correct technical English** (grammar, spelling, and domain-appropriate terminology).

---

## 7. Out of scope for this specification

- Step-by-step tutorials or tool-specific instructions.
- Mandatory choice of programming language or libraries (beyond producing a runnable script and report).
- Exact submission dates (defined elsewhere by the course rules).

---

## 8. Summary checklist (Task 02)

| Requirement | Applies to |
|-------------|------------|
| Repository structure: data_examples/ (sample records), documentation/ (reports as .md, one per task per group) | All teams |
| Teams of 3–4: one report file per task; all members commit to it; one consistent quality standard (language, correct technical English) | Teams of 3 and 4 |
| Initial dataset(s) available; each member’s dataset for 3–4 | All teams |
| Validation script: missing values, duplicates, consistency (tabular) or text/image checks as in §3 | All teams |
| Script produces reproducible report | All teams |
| Task report in documentation/ (findings, assumptions; consistent language, correct technical English, readable as technical documentation) | All teams |
| At least 1 GitHub Project task for Task 02 | Teams of 3 |
| 4 GitHub Project tasks, 1 per person, with clear acceptance criteria | Teams of 4 |

All deliverables and descriptions must be written in **correct technical English** (grammar, spelling, and domain-appropriate terminology).
