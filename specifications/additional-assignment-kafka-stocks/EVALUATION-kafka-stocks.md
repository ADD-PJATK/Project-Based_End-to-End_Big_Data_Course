# Kafka / SSE additional assignment — batch evaluation

**Scope:** GitHub repos matching `ADD-PJATK/s*_kafka` (excluding `kafka-local-demo`), reviewed against `README.md` and `ACCEPTANCE.md` in this folder.  
**Snapshot date:** 2026-05-10 (default branch `main`).  
**Note:** Student names from the class roster are **not** mapped to `sXXXXX` IDs here; match IDs to your gradebook locally.

**Scoring legend**

- **6** — one submission stands out as the strongest overall (still aligned with the brief).  
- **5** — several submissions above average; short note on what earned the extra credit.  
- **4** — all four rubric items from the assignment (repo, READMEs, screenshots, git hygiene) satisfied without major gaps.  
- **Below 4** — short **English** comment on what is missing vs. the rubric.

---

## 6 / 4 — outstanding (one student)

| Repo | Score | Why the extra credit (English) |
|------|-------|--------------------------------|
| [s25504_kafka](https://github.com/ADD-PJATK/s25504_kafka) | **6** / 4 | Very strong end-to-end delivery: both apps clearly separated, per-app READMEs, multiple real screenshots, long series of focused commits, plus extra engineering context (e.g. CI and k8s) that goes beyond the minimum. |

---

## 5 / 4 — above average (several students)

| Repo | Score | Why the extra credit (English) |
|------|-------|--------------------------------|
| [s22460_kafka](https://github.com/ADD-PJATK/s22460_kafka) | **5** / 4 | Automated tests and tooling (e.g. jsdom coverage, Playwright-related screenshot workflow); documentation and screenshots are aligned with the running apps. |
| [s34859_kafka](https://github.com/ADD-PJATK/s34859_kafka) | **5** / 4 | Careful iteration on SSE/chart behaviour, good per-app READMEs, solid screenshot set, and attention to secrets in shared docs. |
| [s25182_kafka](https://github.com/ADD-PJATK/s25182_kafka) | **5** / 4 | Polished single-codebase UI with clearly separated dashboard vs. history features, strong README narrative, and screenshots that show charts and export behaviour. |
| [s32447_kafka](https://github.com/ADD-PJATK/s32447_kafka) | **5** / 4 | Clean split into two apps, per-app READMEs, helper scripts for local dev, and screenshots for both applications. |
| [s24337_kafka](https://github.com/ADD-PJATK/s24337_kafka) | **5** / 4 | Reproducible Python setup (`pyproject` / lockfile), rich screenshot set covering both apps, and thorough documentation. |

---

## 4 / 4 — rubric met

| Repo | Score |
|------|-------|
| [s22734_kafka](https://github.com/ADD-PJATK/s22734_kafka) | 4 / 4 |
| [s23032_kafka](https://github.com/ADD-PJATK/s23032_kafka) | 4 / 4 |
| [s24775_kafka](https://github.com/ADD-PJATK/s24775_kafka) | 4 / 4 |
| [s34090_kafka](https://github.com/ADD-PJATK/s34090_kafka) | 4 / 4 |
| [s34841_kafka](https://github.com/ADD-PJATK/s34841_kafka) | 4 / 4 |

---

## Below 4 — what is missing (comments in English)

| Repo | Score | Missing vs. rubric (English) |
|------|-------|------------------------------|
| [s23372_kafka](https://github.com/ADD-PJATK/s23372_kafka) | 3 / 4 | Repository only contains history-app screenshots; add at least one screenshot for the **realtime / SSE** app with live data (and ensure both apps are visibly covered). |
| [s34851_kafka](https://github.com/ADD-PJATK/s34851_kafka) | 3 / 4 | No image files in the repo after screenshots were removed; restore **screenshots** (or embed them in README) for **both** apps with charts/tables. |
| [s22083_kafka](https://github.com/ADD-PJATK/s22083_kafka) | 3 / 4 | `screenshots/` is effectively empty; add real screenshots for **both** apps (live data, chart or table). |
| [s34700_kafka](https://github.com/ADD-PJATK/s34700_kafka) | 3 / 4 | No screenshot files present; **history_app** README is too thin vs. the checklist (prereqs, install, API key, run, endpoints). |
| [s34852_kafka](https://github.com/ADD-PJATK/s34852_kafka) | 2 / 4 | Single combined project instead of **two** clearly separated app folders; **no** screenshots; commit history mostly bulk uploads — use more incremental commits. |
| [s23840_kafka](https://github.com/ADD-PJATK/s23840_kafka) | 2 / 4 | Only **App #1** present; **App #2** (history downloader/viewer) missing; root **`.gitignore`** missing; only one screenshot; need more commits. |
| [s34850_kafka](https://github.com/ADD-PJATK/s34850_kafka) | 2 / 4 | Marked unfinished in commit message; root README lacks required sections; **screenshots** folder empty; only **two** commits. |
| [s24168_kafka](https://github.com/ADD-PJATK/s24168_kafka) | 1 / 4 | No application code, no screenshots, README not sufficient — only an initial commit. |

---

## Roster headcount

- **Repos found:** 19 (`s*_kafka` under ADD-PJATK).  
- Your on-screen roster: **20** students — one ID may be missing, under a different repo name, or not pushed yet; reconcile manually.

---

## Method (for repeatability)

- Listed default-branch tree via GitHub API: app folders, `README.md` depth, `.gitignore`, image files (`*.png` / `*.jpg`), commit count and messages.  
- Functional behaviour (SSE, polling, export) was **not** executed in a browser; scores for **4+** assume README + structure + artefacts match the assignment unless obvious gaps (e.g. no images, one app only).
