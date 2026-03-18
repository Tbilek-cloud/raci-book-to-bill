# Book to Bill RACI – GitHub Pages + Confluence Embed Guide

## How it works

```
Confluence Page
  └── iframe
        └── GitHub Pages  (hosts index.html — full interactive app)
                └── Google Apps Script  (audit log API)
                        └── Google Sheets  (persistent log database)
```

The Confluence page just holds a frame — the full app (filters, edit popup,
save login, audit log) runs inside it from GitHub Pages.

---

## Step 1 — Publish to GitHub Pages

1. Go to [github.com](https://github.com) → **New repository**
2. Name it: `raci-book-to-bill` — set to **Public**
3. Upload `index.html` (the RACI app artifact) to the repo root
4. Go to **Settings → Pages → Source** → select `main` / `root` → **Save**
5. Your app is live at:
   ```
   https://YOUR-USERNAME.github.io/raci-book-to-bill
   ```
   *(takes ~60 seconds to activate)*

---

## Step 2 — Connect the Audit Log (Google Sheets)

1. Create a new Google Sheet named `RACI Audit Log`
2. Add headers in Row 1:
   `Timestamp | User | User Label | Process Step | Column | Old Value | Old Active | New Value | New Active`
3. Go to **Extensions → Apps Script** → paste the Apps Script artifact → **Deploy as Web App**
   - Execute as: **Me**
   - Access: **Anyone**
4. Copy the **Web App URL**
5. In your GitHub repo, edit `index.html` — find:
   ```
   var APPS_SCRIPT_URL = 'YOUR_APPS_SCRIPT_URL_HERE';
   ```
   Replace with your URL → **Commit changes**

---

## Step 3 — Embed in Confluence

### Option A — Confluence iframe macro (recommended)

1. Open your Confluence page in **Edit** mode
2. Click **`+`** (Insert) → search for **iframe** macro
3. Set:
   - **URL**: `https://YOUR-USERNAME.github.io/raci-book-to-bill`
   - **Width**: `100%`
   - **Height**: `800px`
   - **Scrolling**: `yes`
4. **Publish** the page

> If the iframe macro is not available, ask your Confluence admin to
> enable it — it ships with Confluence but may need to be activated.

---

### Option B — HTML macro (if admin has enabled it)

1. Edit your Confluence page
2. Insert → **Other macros** → **HTML**
3. Paste this code:

```html
<iframe
  src="https://YOUR-USERNAME.github.io/raci-book-to-bill"
  width="100%"
  height="800"
  frameborder="0"
  style="border:none;border-radius:8px;"
  allowfullscreen>
</iframe>
```

4. Save and publish

---

### Option C — Wiki Markup (if macros are restricted)

Go to **Edit → `...` → Wiki Markup** and paste:

```
{html}
<iframe src="https://YOUR-USERNAME.github.io/raci-book-to-bill"
  width="100%" height="800" frameborder="0"></iframe>
{html}
```

---

## Step 4 — Admin Audit Log Access

| Method | How |
|---|---|
| **In the app** | Click "Audit Log" tab — sign in as `admin` / `admin123` |
| **Google Sheets** | Open the `RACI Audit Log` sheet directly — every save appends a row |
| **CSV export** | Click "↓ Export CSV" in the Audit Log tab |

---

## Updating the RACI content

To update process steps or RACI assignments:

1. Edit `index.html` in GitHub (click the file → pencil icon ✏️)
2. Find the `SECTIONS` array in the script
3. Make your changes → **Commit changes**
4. GitHub Pages refreshes automatically within ~60 seconds
5. The Confluence page shows the update immediately — no republishing needed

---

## Changing user accounts / passwords

In `index.html`, find the `USERS` object:

```javascript
var USERS = {
  'cbm.uki':    { pass: 'pass123', label: 'CBM – UKI' },
  'fbp.canada': { pass: 'pass123', label: 'FBP – Canada' },
  'admin':      { pass: 'admin123', label: 'Admin' },
  // add more users here
};
```

Change passwords, add users, or rename labels → commit → done.

---

## Files summary

| File | Where | Purpose |
|---|---|---|
| `index.html` | GitHub repo root | Full RACI app |
| Apps Script | Google Sheet → Extensions | Audit log API |
| `RACI Audit Log` | Google Sheets | Persistent log database |
| Confluence page | Your Confluence space | Embeds the app via iframe |

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Confluence says "iframe not allowed" | Ask admin to enable iframe / HTML macro |
| App not loading in iframe | Check GitHub Pages is active (Settings → Pages) |
| Audit log not saving | Verify Apps Script URL is set in `index.html` and Web App is deployed as "Anyone" |
| Changes not showing after edit | Wait 60s for GitHub Pages to rebuild, then hard-refresh (Ctrl+Shift+R) |
