# TENDHA Fortnite — Website

Your full website is in this folder. It contains:

```
tendha-fortnite-site/
├── index.html          ← Public landing page (hero, about, contact)
├── catalog.html        ← Public account catalog (loads from accounts.json)
├── admin.html          ← Private admin dashboard (login required)
├── accounts.json       ← The catalog data (admin publishes this)
├── assets/
│   └── styles.css      ← Shared styles for the public pages
└── README.md           ← This file
```

---

## 1. Customize before going live

Open `index.html` in any text editor and find/replace these placeholders with your real handles:

- `yourhandle` → your Telegram, Discord, Instagram username
- `discord.gg/yourinvite` → your real Discord invite link
- `tendha2020@gmail.com` → already set, change if needed

Also do the same in `catalog.html` (same placeholders appear in the Buy modal).

---

## 2. Deploy to Netlify (free, ~3 minutes)

1. Open your file manager and locate the `tendha-fortnite-site` folder.
2. Visit https://app.netlify.com/drop in your browser.
3. Drag the **entire folder** (not individual files) onto the drop zone.
4. Wait ~10 seconds. Netlify gives you a URL like `https://glittery-pavlova-7a3b9c.netlify.app`.
5. Click **"Claim your site"** at the top of the page, sign up with email or GitHub (free).
6. Go to **Site settings → Change site name** and pick something like `tendha-fortnite`. Your URL becomes `https://tendha-fortnite.netlify.app`.

That's your public website.

---

## 3. First-time admin setup

1. Visit `https://your-site.netlify.app/admin.html`.
2. The first time, it asks you to create an admin username and password — pick whatever you want.
3. Log in. You're now in the dashboard.
4. To add another admin, click **Manage admins** in the sidebar. You can add staff with their own username/password and a role (owner / staff).

---

## 4. Publishing changes (the main workflow)

When you add accounts, change statuses, or update images:

1. Open `https://your-site.netlify.app/admin.html`, log in.
2. Make your changes (auto-saved in your browser).
3. Click **Publish to website** (gold button) → downloads a fresh `accounts.json`.
4. Go back to your Netlify site dashboard → **Deploys** tab → drag the new `accounts.json` into the drop zone.
5. ~10 seconds later the live catalog updates.

That's it. You don't redeploy the whole site — just the JSON file.

---

## 5. Important security caveats

**The admin login is client-side only.** This means:

- Anyone who opens `admin.html` in a browser can see the JavaScript. The password check happens locally in their browser.
- Admin credentials are stored in browser `localStorage`, which is per-device.
- A determined attacker can bypass it by editing the page in their browser. It is enough to keep casual visitors out, but it is not real authentication.
- Your account inventory data (`accounts.json` + the data baked into `admin.html`) is publicly accessible to anyone who knows the URL.

**Recommended: don't link to `admin.html` publicly.** It's already only linked from the footer (small "Admin" link). For better security:

- **Option A:** Rename `admin.html` to something hard to guess, like `admin-7Hj42xQ.html`. Update the footer link in `index.html` and `catalog.html` to match.
- **Option B (better):** Put the whole site behind a Cloudflare Pages deploy with **Cloudflare Access** (free tier). That gives you a real password gate before anyone can even reach the pages.
- **Option C (best, future):** Move to a backend with a real auth system. Tools like Supabase + Vercel can do this; ask Claude to help if your business gets there.

For now, treat the admin password as a "keep honest people honest" gate. **Do not store anything in the admin panel that you would not be okay with becoming public if someone bypassed the login.**

---

## 6. Updating the website itself (CSS, layout, copy)

- Edit `index.html`, `catalog.html`, or `assets/styles.css` in any text editor (VS Code, Notepad, anything).
- Drag those edited files back to Netlify's Deploys tab.
- Or, if you want, drag the whole folder again to do a full redeploy.

---

## 7. Local testing

The catalog page uses `fetch()` to load `accounts.json`. Browsers block `fetch()` from `file://` URLs — opening `catalog.html` directly with a double-click won't work.

**To test locally:** use a tiny local server:

- **Python (if you have it):** Open a terminal in the site folder, run `python -m http.server 8000`, visit `http://localhost:8000`.
- **VS Code:** Install the "Live Server" extension, right-click `index.html` → "Open with Live Server".

Once deployed to Netlify, this issue goes away — the live URL works fine.

---

## 8. Custom domain (optional, ~$10/year)

1. Buy a domain at Cloudflare Registrar, Namecheap, or Porkbun (cheapest option around).
2. In Netlify: **Site settings → Domain management → Add custom domain**.
3. Follow Netlify's DNS instructions (usually just paste two records into your domain registrar).
4. SSL/HTTPS is automatic and free.

---

## Questions or stuck?

Open the `Vault-Ledger-Pro.html` file in this folder's parent directory if you want to keep using the original (untouched) dashboard alongside the new site. Both work independently.
