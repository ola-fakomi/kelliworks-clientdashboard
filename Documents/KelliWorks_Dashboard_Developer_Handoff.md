# KelliWorks Client Dashboard — Developer Handoff

**Prepared for:** KelliWorks Web Developer  
**File:** `KelliWorks_Client_Dashboard.html`  
**Date:** April 2026

---

## What This Is

A single-file HTML dashboard for KelliWorks (bookkeeping firm). It contains all client data, branding, and logic in one self-contained `.html` file — no server, no database, no dependencies to install.

---

## How to Deploy on Wix

### Step 1 — Host the file
The file must be publicly hosted before embedding in Wix. Best options:

**Option A — Netlify (easiest, free, 2 minutes)**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `KelliWorks_Client_Dashboard.html` onto the page
3. Copy the URL Netlify gives you (e.g. `https://bright-sunflower-abc123.netlify.app`)

**Option B — GitHub Pages (free, more control)**
1. Create a GitHub repo, upload the file renamed to `index.html`
2. Go to Settings → Pages → Select `main` branch → Save
3. URL will be: `https://yourusername.github.io/your-repo-name/`

**Option C — Your existing web host**
Upload to any folder on your hosting and use the direct URL.

> ⚠️ The host MUST use `https://` (not `http://`). Netlify and GitHub Pages both do this automatically.

---

### Step 2 — Embed in Wix

1. Open Wix Editor → Navigate to the page where dashboard should appear
2. Click **+** (Add Elements) → **Embed & Social** → **HTML iFrame**
3. Place it on the page, then click **"Enter Code"**
4. Paste this code (replace the URL):

```html
<iframe
  src="https://YOUR-HOSTED-URL-HERE"
  width="100%"
  height="960px"
  frameborder="0"
  style="border:none;"
  allow="clipboard-write"
></iframe>
```

5. Click **Apply** → resize the element to full width → **Publish**

**Recommended iFrame height:** `960px` minimum. If content is cut off, increase to `1100px`.

---

### Step 3 — Protect the page (required)

This dashboard contains client information. Restrict access:

- In Wix: Page Settings → Permissions → **Members Only** or **Password Protected**
- Create logins for each team member in Wix Members

---

## How to Deploy on WordPress (future move)

1. Create a new page in WordPress
2. Add a **Custom HTML** block (built into Gutenberg editor)
3. Paste the same `<iframe>` code from above
4. Set page visibility to **Private** or use a membership plugin (MemberPress, WP Members, etc.)
5. Publish

---

## Updating the Dashboard

The dashboard is maintained by Claude (AI assistant at Cowork/Claude desktop app). To update:

| What needs updating | Who does it | How |
|---|---|---|
| Client data (new clients, status changes) | Kelli → Claude | Export updated CSV from Asana, send to Claude |
| Google Sheet links (add missing ones) | Kelli → Claude | Send list of client name + URL |
| Contact info (phone, email, EIN) | Team | Edit directly inside dashboard (Contact Info tab → Save) |
| Branding/colors | Developer → Claude | Describe the change |
| New features | Kelli → Claude | Describe what you need |

After any update, Claude will provide a new `KelliWorks_Client_Dashboard.html` file. Replace the hosted file with the new one — no code changes needed.

---

## Key Technical Details

| Property | Value |
|---|---|
| File type | Single-file HTML (self-contained) |
| File size | ~170KB |
| Dependencies | None (no npm, no frameworks, no CDN required) |
| Data storage | Embedded in HTML as Base64 (client-side read-only) |
| Contact edits | Saved to browser `localStorage` per user |
| Live Asana sync | Runs in browser via Asana REST API (PAT embedded) |
| Live hours data | Everhour hours embedded from CSV export |
| Google Sheets links | 44 of 56 embedded; 12 pending |
| Browser support | All modern browsers (Chrome, Safari, Firefox, Edge) |

---

## What the Dashboard Shows

### Views (top navigation)
- **Board** — Summary stats: active clients, hours YTD, overdue tasks, revenue
- **Client Database** — Full 56-client table with search, filters, export
- **Outstanding** — Clients off-track or on hold, high overdue counts
- **Revenue** — Income by year (2023–2026 YTD)

### Per-Client Modal (click any client)
- **Overview** — Status, tier, service, progress, link to Asana project, 📊 Google Status Sheet button
- **Contact Info** — Phone, email, entity type, EIN, address, Google Sheet URL (editable, saves locally)
- **Asana Tasks** — Live task list pulled from Asana API
- **⏱ Hours** — Everhour hours (this month / YTD / last year) + Asana time breakdown
- **💬 Slack** — Slack channel link + activity snapshot
- **🤖 Ask AI** — AI chat specific to this client (searches Asana + Slack)
- **Revenue** — Year-by-year gross income, billing details

### AI Chat (bottom-right corner)
Global AI assistant that can answer questions about any of the 56 clients, revenue, overdue tasks, team status, etc. Type a client name and it returns a full project update.

---

## Admin-Only Fields

The following fields are intentionally hidden from the dashboard view:
- **Rate / Monthly Cost** — Removed from all views; admin use only
- To add an admin-only view in the future, implement password protection at the page/route level

---

## 12 Clients Missing Google Sheet Links

These clients don't yet have a status sheet in the system. Once Kelli provides the URLs, Claude can add them in under 5 minutes:

1. Bullet Construction Annual WorkFlow
2. Childress & Jackson Annual WorkFlow
3. Crest Annual WorkFlow
4. Dean Kravitz - Kravitz Family
5. Dean Kravitz - Theatre Home LLC
6. FFHS - Sam Siebu
7. GEMCO-Weekly WorkFlow
8. GIANFERDI ENT.INC - James Iglesias
9. Holy Temple Christian Academy
10. Jammed Up Bakery - Sarah Perara
11. Michael Alamillo
12. Unleashed Management Co. - Cheyenne Arnold

---

## Questions?

Contact Kelli at kelli@kelliworks.com or bring them back to Claude for any dashboard changes.
