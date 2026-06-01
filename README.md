# Ready State — website

Marketing + lead-gen site for **Ready State**: robot-readiness for homes & hospitality.

Static site — `index.html` plus a client-side **Robot-Readiness Assessment** (`assessment.html`) that scores a visitor's property instantly. No build step, no backend, no dependencies beyond Google Fonts. Hosts free on GitHub Pages.

---

## Run it locally

Just open `index.html` in a browser. Or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages (free)

This folder is **already a git repo with one commit** (`Ready State site - initial launch`). It was initialized in your OneDrive folder, which left a couple of stray `.lock` files — clear them first, then push.

1. Create an empty repo named **`ready-state-web`** on GitHub (under `ndybiehl`) — no README/license.
2. From this folder on your Mac:

```bash
# clear the OneDrive-left lock files (safe — your files are intact)
rm -f .git/index.lock .git/HEAD.lock .git/objects/maintenance.lock

git add -A
git commit -m "Add interactive readiness assessment + polish hero"
git branch -M main
git remote add origin https://github.com/ndybiehl/ready-state-web.git
git push -u origin main
```

3. On GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch"**, Branch: **`main`** / folder **`/ (root)`**, Save.
4. Live in ~1 min at: **https://ndybiehl.github.io/ready-state-web/**

> If `git status` ever complains about a lock, just re-run the `rm -f .git/*.lock` line.

## Custom domain (when you have one)

1. Buy the domain (e.g. `readystate.co` — `.com` may be taken; confirm before printing it anywhere).
2. Create a file named **`CNAME`** in the repo root containing just the domain, e.g. `readystate.co`.
3. GitHub **Settings → Pages → Custom domain** → enter the domain → enable **Enforce HTTPS**.
4. At your DNS host, point the domain at GitHub Pages (A records to GitHub's IPs, or a `CNAME` for `www` → `ndybiehl.github.io`). GitHub shows the exact records.

---

## Before you go live — TODO checklist

These are flagged with `TODO` in the code:

- [ ] **Confirm the name + domain.** "Ready State" — check `readystate.co` / `.com` availability before committing the brand.
- [ ] **Real email.** Replace `hello@readystate.co` in **both** `index.html` and `assessment.html` (search `CONTACT_EMAIL`, plus the contact link in `index.html`).
- [ ] **Real phone.** Replace `(000) 000-0000` and the `tel:+10000000000` link.
- [ ] **About section.** Tighten the bio if you want specifics (years, credentials). Currently kept generic and **does not mention Key MSP** (keeps this a clean stand-alone brand).
- [ ] **Pricing.** "Homes from $750" is a placeholder anchor to qualify leads — set your real number.
- [ ] **Social image** (optional): add an `og:image` for nice link previews.

## Optional: capture leads to an inbox (no mail-app popup)

The contact form currently opens the visitor's email app via `mailto:` (zero setup, works on static hosting). To collect submissions straight to your inbox instead:

1. Make a free form at [formspree.io](https://formspree.io) → get an endpoint like `https://formspree.io/f/abcdwxyz`.
2. In `index.html`, replace the `<form id="contactForm">` submit script with a normal form post:
   ```html
   <form id="contactForm" action="https://formspree.io/f/abcdwxyz" method="POST">
   ```
   and delete the `mailto` script block at the bottom.

---

*Stand-alone venture — keep separate from Key MSP (own brand, vendors, and clients).*
