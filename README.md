# Article Tracker — Auto-Refresh Setup

Automatically refreshes the Content Team editorial calendar tracker from Asana every day at 6am PST.

## Files

- `generate.py` — fetches Asana data and builds `article_tracker.html`
- `.github/workflows/refresh.yml` — GitHub Actions workflow that runs on a schedule
- `article_tracker.html` — the generated tracker (auto-updated by the workflow)

## Setup (one time)

### 1. Create a GitHub repo

- Go to github.com → New repository
- Name it something like `article-tracker`
- Set it to **Private** (recommended)
- Upload these files to the repo

### 2. Add your Asana token as a secret

- Go to your repo → **Settings** → **Secrets and variables** → **Actions**
- Click **New repository secret**
- Name: `ASANA_TOKEN`
- Value: your Asana Personal Access Token (from Asana → Profile → Apps → Developer Apps)
- Click **Add secret**

### 3. Enable GitHub Pages (for a shareable link)

- Go to your repo → **Settings** → **Pages**
- Under "Source" select **Deploy from a branch**
- Branch: `main`, folder: `/ (root)`
- Click **Save**
- Your tracker will be live at: `https://YOUR-USERNAME.github.io/article-tracker/article_tracker.html`

### 4. That's it

The tracker will now auto-refresh every day at 6am PST. You can also trigger it manually anytime from the **Actions** tab → **Refresh Article Tracker** → **Run workflow**.

## Sharing

Once GitHub Pages is enabled, share the URL with your team. It always shows the latest data — no downloads, no manual steps.

## Extending to new months

To add new months (e.g. June 2026), add the new Asana section GIDs to the `SECTION_IDS` list in `generate.py` and update the `MONTHS` list in the HTML template section.
