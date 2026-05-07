# Acceptance criteria & Grading rubric

## Grading — 0 to 4 points

| # | Criterion | Points |
|---|-----------|--------|
| 1 | **Git repository** — created in the ADD GitHub organisation, named `sXXXXX_kafka` (your student ID) | 1 pt |
| 2 | **Full usage instructions** — README explains how to build, configure and run both apps; all required elements listed below are present | 1 pt |
| 3 | **Screenshots of working apps** — at least one screenshot per app showing live data, including charts/tables | 1 pt |
| 4 | **Proper use of Git** — meaningful commit messages, at least 3–5 commits showing development progress (not one big "final" commit) | 1 pt |

**Total: 4 points**

---

## 1. Git repository (1 pt)

- [ ] Repository created under the **ADD GitHub organisation**
- [ ] Repository name: `sXXXXX_kafka` (replace `XXXXX` with your student ID, e.g. `s12345_kafka`)
- [ ] Repository is **public** or accessible to the instructor
- [ ] API key is **not committed** — use an `.env` file and add it to `.gitignore`

---

## 2. Required README elements (1 pt)

Each app must have a `README.md` that includes all of the following:

- [ ] **Prerequisites** — what needs to be installed (Python, Node, etc.) and versions
- [ ] **Installation** — step-by-step: clone, install dependencies (`pip install -r requirements.txt` / `npm install` / etc.)
- [ ] **Configuration** — how to set the API key (e.g. `export ADD_API_KEY=...` or `.env` file)
- [ ] **How to run** — exact command to start the app (e.g. `python app.py` / `npm run dev`)
- [ ] **Which endpoints are used** and how

> A good README means someone who has never seen your code can run it in under 5 minutes.

---

## 3. Screenshots (1 pt)

Must be included in the repository (e.g. `screenshots/` folder or embedded in the README):

- [ ] **App #1** — screenshot showing live price updates for at least 2 tickers, with a chart or history table
- [ ] **App #2** — screenshot showing fetched data for a selected time range, with a chart or table and a downloaded file (CSV/JSON)
- [ ] Screenshots show **real data** (not empty state or mock data)

---

## 4. Git usage (1 pt)

- [ ] At least **3 commits** with meaningful messages (e.g. `"Add SSE client for live stream"`, `"Add ticker selection UI"`)
- [ ] **No "init" or "final" mega-commits** containing the entire codebase
- [ ] `.gitignore` present and correct (excludes `.env`, `__pycache__`, `node_modules`, etc.)
- [ ] Each app is in its own directory or clearly separated

---

## Functional requirements checklist

### App #1 — Realtime Dashboard

- [ ] User can select one or more tickers (from the 50-company list)
- [ ] App connects to `GET /api/stream` (SSE) and shows **live updates**
- [ ] UI displays: ticker symbol, current price, timestamp
- [ ] Chart or scrolling history of last N ticks
- [ ] App handles connection drops gracefully (reconnects or shows an error)

### App #2 — History Downloader / Viewer

- [ ] User can select tickers
- [ ] User can specify a time range (last N minutes, up to ~10 min)
- [ ] App fetches data via `GET /api/latest` (polling with ≥10 s interval) or `/api/stream`
- [ ] Results are displayed in the UI (table or chart)
- [ ] Results can be saved as CSV or JSON file

### Common (both apps)

- [ ] API key passed via `X-API-Key` header or `api_key` query param
- [ ] API key **not hardcoded** — stored in env variable or `.env` file
- [ ] App runs locally without errors on a clean install
