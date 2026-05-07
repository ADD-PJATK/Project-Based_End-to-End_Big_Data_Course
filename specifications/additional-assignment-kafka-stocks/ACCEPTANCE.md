# Acceptance criteria

## App #1 — Realtime Dashboard

- [ ] User can select one or more tickers (from the 50-company list)
- [ ] App connects to `GET /api/stream` (SSE) and shows **live updates**
- [ ] UI displays: ticker symbol, current price, timestamp
- [ ] App handles connection drops gracefully (reconnects or shows an error)

## App #2 — History Downloader / Viewer

- [ ] User can select tickers
- [ ] User can specify a time range (e.g. last N minutes, up to ~10 min)
- [ ] App fetches data via `GET /api/latest` or `/api/stream`
- [ ] Results are displayed in the UI (table or chart)
- [ ] Results can be saved as CSV or JSON

## Common (both apps)

- [ ] API key is passed via header `X-API-Key` or query param `api_key`
- [ ] API key is **not hardcoded** in source code (uses env variable or config file)
- [ ] Each app has a `README` with: how to run + how to configure the key
- [ ] Code runs locally without errors
