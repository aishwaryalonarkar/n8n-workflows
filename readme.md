
## Overview

This repository houses multiple **n8n** workflows that solve common automation needs:
- **Scraping & aggregation** (e.g., jobs, listings, news)
- **ETL pipelines** (fetch → transform → load to DB/Sheets)
- **Notifications** (Slack/Email/Discord alerts)
- **Integrations** (APIs, webhooks, spreadsheets, cloud services)

Each workflow is provided as a **sanitized JSON export** ready to import into your n8n instance.

---

## Repository Structure

```
n8n-workflow/
├─ workflows/
│ ├─ job-scraper/
│ │ ├─ workflow-SerpApi.json
│ │ ├─ workflow-remoteok.json
│ │ └─ README.md
│ ├─ etl-example/
│ │ ├─ etl-example.n8n.sanitized.json
│ │ └─ README.md
│ └─ ...
├─ .env.example
├─ docker-compose.yml
└─ README.md ← you are here
```



## Quick Start

### Option A — n8n Cloud
1. Sign in to **n8n Cloud**.
2. Go to **Workflows → Import from File** and select any `*.sanitized.json` from `workflows/`.
3. Open nodes that require configuration (e.g., HTTP Request, Google Sheets) and add your credentials.
4. Run the workflow once to verify, then enable the trigger(s).

### Option B — Local n8n
1. Copy `.env.example` to `.env`, fill values.
2. Use Docker (see next section) or install n8n globally via npm.
3. Import the workflow JSON files from **Workflows → Import from File**.

---

## Self‑Host with Docker

> The following is a minimal, production‑friendly starting point. Adjust ports, volumes, and reverse proxy to your needs.

**docker-compose.yml**

```yaml
version: "3.8"
services:
  n8n:
    image: n8nio/n8n:latest
    env_file:
      - ./.env
    ports:
      - "5678:5678"
    volumes:
      - n8n_data:/home/node/.n8n
    restart: unless-stopped
volumes:
  n8n_data:
