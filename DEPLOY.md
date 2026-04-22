# Sous Pantry Landing Page — GitHub Pages Deployment

## Quick Setup

Your landing page is ready to deploy to GitHub Pages with your custom domain `souspantry.com`.

---

## 1. Push to GitHub

```bash
cd /Users/jf/Documents/SousPantry/landing_prelaunch

git init
git add .
git commit -m "Initial landing page commit"
git branch -M main
git remote add origin https://github.com/jamesianfoo-sp/sous_pantry_launch.git
git push -u origin main
```

---

## 2. Enable GitHub Pages

1. Go to your repo: https://github.com/jamesianfoo-sp/sous_pantry_launch
2. Click **Settings** (top right)
3. Scroll down to **Pages** (left sidebar)
4. Under "Build and deployment":
   - **Source**: select **Deploy from a branch**
   - **Branch**: select `main` and keep folder as `/ (root)`
5. Click **Save**

GitHub will deploy your site to `jamesianfoo-sp.github.io` within seconds.

---

## 3. Connect Your Custom Domain

### Step A: Tell GitHub about your domain

1. In **Settings** → **Pages**
2. Under "Custom domain", enter `souspantry.com`
3. Click **Save**
4. GitHub will create a `CNAME` file automatically

### Step B: Update your domain registrar's DNS

Where you purchased `souspantry.com` (GoDaddy, Namecheap, etc.):

1. Log in and go to **DNS Settings**
2. Find your **A Records** or **CNAME Records**
3. Add these **A records** pointing to GitHub:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
   (All four IPs — GitHub uses them for redundancy)

4. **Optional: Add a CNAME for www subdomain**
   ```
   www  →  jamesianfoo-sp.github.io
   ```

5. Click **Save** and wait 5–30 minutes for DNS to propagate

### Step C: Enable HTTPS

Once DNS is working:
1. Refresh **Settings** → **Pages**
2. Check the box: **"Enforce HTTPS"**
3. Done! GitHub's free SSL certificate is automatic.

---

## 4. Formspree is Already Connected

Your form endpoint `https://formspree.io/f/mqewyboa` is already embedded. Submissions go directly to your Formspree dashboard — no setup needed.

---

## Testing Before Deploy

Test locally:
```bash
cd /Users/jf/Documents/SousPantry/landing_prelaunch
npx serve -p 4321
# Visit http://localhost:4321
```

Submit test data → check `formspree.io` dashboard for the email + first_name fields.

---

## File Structure

```
landing_prelaunch/
├── index.html          # Single-page HTML (all CSS + JS inline)
├── DEPLOY.md          # This file
└── .claude/
    └── launch.json    # Local dev config
```

The entire site is **one HTML file** — no build step required. GitHub serves it directly.

---

## After Deploy

- Your site is **live** at `souspantry.com` (custom domain) and `jamesianfoo-sp.github.io` (GitHub subdomain)
- Monitor submissions in your Formspree dashboard
- Update copy/links → edit `index.html` → push to GitHub → auto-deploys instantly
- Add Google Analytics, etc., by inserting a `<script>` tag in the `<head>`

---

## GitHub Pages Auto-Deploy

Every time you push to `main`, GitHub automatically rebuilds and redeploys. No manual steps needed.

```bash
# Edit, commit, push → live within seconds
git add .
git commit -m "Update landing page"
git push
```

---

## Next Steps

Once live on `souspantry.com`:
- Share the link with your waitlist channels (Product Hunt, Twitter, email list, etc.)
- Watch Formspree for submissions
- Update the homepage with new features as the app evolves
