# Deploy TENDHA Fortnite — Permanent Free Hosting

Three free options that **never expire** (unlike Netlify Drop's 1-hour timer). All three give you HTTPS, a public URL, and let you update by re-uploading. Pick whichever feels easiest.

---

## Option 1 — GitHub Pages (recommended, simplest forever-host)

**What you get:** A free permanent URL like `https://yourname.github.io/tendha/`. No credit card, no expiry, unlimited bandwidth for normal traffic.

### Step-by-step (no command line needed)

1. **Make a GitHub account** at https://github.com/signup. Pick a username — that becomes part of your URL.

2. **Create a new repository:**
   - Click the **+** icon top-right → **New repository**
   - Repository name: `tendha` (or whatever you want — that name appears in your URL)
   - Set it to **Public** (required for free Pages)
   - Check **Add a README file** (so the repo isn't empty)
   - Click **Create repository**

3. **Upload your site files:**
   - On the repo page, click **Add file** → **Upload files**
   - Open File Explorer to your `outputs\tendha-fortnite-site\` folder
   - Select **all files inside** (index.html, catalog.html, admin.html, accounts.json, README.md, DEPLOY.md, and the `assets` folder) and drag them onto the GitHub upload area
   - Wait for upload, then click **Commit changes** at the bottom

4. **Turn on GitHub Pages:**
   - Click **Settings** (top of repo)
   - In the left sidebar click **Pages**
   - Under "Build and deployment" → **Source**, select **Deploy from a branch**
   - Set **Branch** to `main` and folder to `/ (root)`, click **Save**
   - Wait 1–2 minutes. The page will refresh and show your live URL: `https://yourname.github.io/tendha/`

5. **Visit and share that URL** — it's permanent. No password.

### Updating later

When you change inventory in admin and click **Publish to website**, you get a fresh `accounts.json`. To update the live site:

- Go to your repo on GitHub → click `accounts.json` → click the pencil icon ✏️ → upload new file (or paste new content) → **Commit changes**
- Or click **Add file** → **Upload files** → drag the new `accounts.json` to overwrite the existing one
- Live site updates within ~30 seconds

For bigger changes (HTML/CSS edits), drag updated files the same way.

### Custom domain (optional, ~$10/year)

1. Buy a domain at https://www.cloudflare.com/products/registrar/ (cheapest) or Namecheap/Porkbun.
2. In your repo → **Settings** → **Pages** → **Custom domain** → enter `tendha.com` (or whatever).
3. At your domain registrar, point an A record to GitHub's IPs (instructions show on the GitHub page).
4. Wait ~10 minutes. HTTPS is automatic.

---

## Option 2 — Cloudflare Pages (also free, faster CDN)

Like GitHub Pages but uses Cloudflare's global CDN (faster everywhere). Also free forever.

1. Sign up at https://pages.cloudflare.com (free)
2. Click **Create a project** → **Direct Upload**
3. Project name: `tendha-fortnite`
4. Drag your `tendha-fortnite-site-deploy.zip` onto the upload zone
5. Wait ~20 seconds → your URL is `https://tendha-fortnite.pages.dev`

Bonus: Cloudflare Pages has free **password protection** (Cloudflare Access) on the same plan. Useful if you ever want to put `/admin.html` behind a login.

Updating later: same process — drag a new zip whenever you have changes.

---

## Option 3 — Netlify (free, 100GB/month bandwidth)

Same as what you tried before, but you must **claim the site** within the 1-hour window so it doesn't expire.

1. Visit https://app.netlify.com/drop, drag your zip
2. Within 1 hour, click **"Claim your site"** at the top of the page
3. Sign up free (email or GitHub)
4. **Site settings → Change site name** → pick `tendha-fortnite` → permanent URL `https://tendha-fortnite.netlify.app`

---

## Comparison

| Option | Cost | Speed | Updating | Best for |
|---|---|---|---|---|
| GitHub Pages | Free forever | Fast | Drag files in repo | Most users — simple, reliable |
| Cloudflare Pages | Free forever | Fastest | Drag zip on dashboard | Speed + free password gate |
| Netlify | Free forever (after claiming) | Fast | Drag file in deploys tab | Easiest first deploy if you remember to claim |

---

## After you're live: keep the admin private

- Once deployed, **don't share the `/admin.html` URL publicly**. Anyone who has it can read your inventory data.
- Optional: rename `admin.html` to something hard to guess like `admin-7Hj4xQ.html` (also update the link in `index.html` and `catalog.html` footers).
- Or use Cloudflare Access (Option 2) for a real password gate.

## Files in this site

- `index.html` — landing page (hero, charts, about, contact)
- `catalog.html` — public catalog (666 accounts, filters, search, detail modal)
- `admin.html` — private dashboard (login, manage inventory, publish to site)
- `accounts.json` — the inventory data customers see (publicly readable)
- `assets/styles.css` — shared dark dashboard styling
- `README.md` — overview
- `DEPLOY.md` — this file
