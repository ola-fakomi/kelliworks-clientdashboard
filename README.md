# KelliWorks Client Dashboard

Single-file HTML dashboard for KelliWorks internal client management.

## Project Structure

```
Client-database/
├── Documents/
│   ├── index.html                              ← Main dashboard (deploy this)
│   ├── KelliWorks_Dashboard_Developer_Handoff.md
│   └── KelliWorks_GoogleSheets_Links_Template.xlsx
├── vercel.json                                 ← Vercel deployment config
├── .gitignore
└── README.md
```

## Deploy to Vercel

### Option 1 — Vercel CLI (recommended)
```bash
npm i -g vercel
vercel
```
Follow the prompts. Vercel will serve `Documents/index.html` as the root.

### Option 2 — Vercel Dashboard
1. Go to vercel.com → New Project → Import Git Repository
2. Or drag the entire `Client-database` folder onto the Vercel dashboard

## Embed in Wix (kelliworks.com/clientadmin)

Once deployed, copy the Vercel URL and paste this into a Wix HTML iFrame embed:

```html
<iframe
  src="https://YOUR-VERCEL-URL.vercel.app"
  width="100%"
  height="960px"
  frameborder="0"
  style="border:none;"
  allow="clipboard-write"
></iframe>
```

## Access Control

- Set the Wix page (`/clientadmin`) to **Members Only**
- Add `reports@kelliworks.com` as a Wix Member
- For magic link login, install a passwordless login app from the Wix App Market

## Updating the Dashboard

All updates go through Claude. Workflow:
- **New clients / status changes** → Kelli exports updated CSV from Asana → sends to Claude
- **Missing Google Sheet links** → Kelli sends `client name + URL` to Claude
- **Contact info edits** → Edit directly in the dashboard (saves to browser localStorage)

Claude returns a new `index.html` — replace the file in `Documents/` and redeploy.

## 12 Clients Missing Google Sheet Links

- Bullet Construction Annual WorkFlow
- Childress & Jackson Annual WorkFlow
- Crest Annual WorkFlow
- Dean Kravitz - Kravitz Family
- Dean Kravitz - Theatre Home LLC
- FFHS - Sam Siebu
- GEMCO-Weekly WorkFlow
- GIANFERDI ENT.INC - James Iglesias
- Holy Temple Christian Academy
- Jammed Up Bakery - Sarah Perara
- Michael Alamillo
- Unleashed Management Co. - Cheyenne Arnold

## Live Data Status

| Source | Status |
|---|---|
| Asana | Live (pulls on page load via API) |
| Everhour | Static CSV snapshot |
| Slack | Links only |
| Google Sheets | 44 of 56 linked |
