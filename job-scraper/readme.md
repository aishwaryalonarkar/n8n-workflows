## Overview
Scrapes job from the SerpApi and remoteok into Google Sheets.

## Setup
1) Import the JSON into n8n.
2) In each node:
   - Replace `YOUR_SERPAPI_KEY` (if present) with your SerpAPI key.
   - Replace `YOUR_GOOGLE_SHEET_ID` and `YOUR_SHEET_TAB_NAME_OR_GID`.
3) Reconnect Google Sheets credentials in n8n (Credentials > Google Sheets OAuth2).
4) Execute once manually to test; then enable the Cron trigger.

## Notes
- “Log to Google Sheets” is set to **Append** (does not overwrite).
- No credentials or private links are included in this repo.

