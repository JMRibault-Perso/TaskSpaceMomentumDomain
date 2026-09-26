# How to Publish taskspacemomentum.ai

## Overview
This site is set up for GitHub Pages, with the custom domain `taskspacemomentum.ai` registered at **Porkbun**.

---

## Step 1: Enable GitHub Pages

1. Go to the repository **Settings > Pages**
2. Under **Source**, select branch `main`, folder `/ (root)`
3. Click **Save**
4. Your site will initially be available at: `https://jmribault-perso.github.io/TaskSpaceMomentumDomain/`

## Step 2: Add the Custom Domain in GitHub

1. Still in **Settings > Pages**, under **Custom domain**, enter `taskspacemomentum.ai`
2. Click **Save** — this commits the `CNAME` file (already included in this repo) to the branch
3. Leave **Enforce HTTPS** unchecked for now — it will become available once DNS propagates (Step 3)

## Step 3: Configure DNS at Porkbun

Log in to [Porkbun](https://porkbun.com) → **Domain Management** → `taskspacemomentum.ai` → **DNS Records**.

### Apex domain (`taskspacemomentum.ai`)
Add four **A** records (all with Host left blank / `@`):

| Type | Host | Answer            |
|------|------|--------------------|
| A    |      | 185.199.108.153    |
| A    |      | 185.199.109.153    |
| A    |      | 185.199.110.153    |
| A    |      | 185.199.111.153    |

Optional (IPv6) — add these **AAAA** records too:

| Type | Host | Answer                  |
|------|------|--------------------------|
| AAAA |      | 2606:50c0:8000::153      |
| AAAA |      | 2606:50c0:8001::153      |
| AAAA |      | 2606:50c0:8002::153      |
| AAAA |      | 2606:50c0:8003::153      |

> Alternative: Porkbun supports an **ALIAS** record type for the apex domain, which can be used instead of the four A records:
> `Type: ALIAS, Host: (blank), Answer: jmribault-perso.github.io`

### `www` subdomain
Add a **CNAME** record:

| Type  | Host | Answer                       |
|-------|------|------------------------------|
| CNAME | www  | jmribault-perso.github.io    |

### Remove conflicting records
Delete any existing default **A**, **ALIAS**, or **URL Forward** records Porkbun created for the apex/`www` when the domain was registered — they will conflict with the records above.

## Step 4: Wait for DNS Propagation

- Can take a few minutes up to 24-48 hours
- Check status with https://dnschecker.org (search `taskspacemomentum.ai`, type A)
- Once propagated, go back to **Settings > Pages** in GitHub — it will show a green checkmark next to the custom domain, and the **Enforce HTTPS** checkbox will become available. Enable it.

---

## Testing Locally Before Publishing

### Windows (PowerShell):
```powershell
cd path\to\this\folder
python -m http.server 8000
```
Then open http://localhost:8000

---

## Customization Checklist

Before publishing, search `index.html` for `[PLACEHOLDER]` and replace:

- [ ] Meta description and title
- [ ] Hero description
- [ ] Hero credential badges (standards/certifications)
- [ ] Pedigree bar (companies/programs)
- [ ] About section text and stats
- [ ] Services descriptions (6 cards)
- [ ] Standards & Frameworks cards (4 cards)
- [ ] Focus Areas lists (4 categories)
- [ ] Featured Initiative + achievement highlights
- [ ] Contact info: email, phone, address, LinkedIn
- [ ] Footer email/LinkedIn links

---

## Troubleshooting

### Website not showing?
1. Clear browser cache (Ctrl + F5)
2. Wait for DNS propagation
3. Confirm the `CNAME` file in the repo root still contains exactly `taskspacemomentum.ai`

### DNS issues?
- Use https://dnschecker.org to verify propagation
- Make sure Porkbun doesn't have leftover default A records or URL forwarding rules pointing elsewhere

---

## Next Steps

After publishing:
1. Submit the site to Google Search Console
2. Set up analytics
3. Confirm SSL/HTTPS is enforced
4. Test on mobile devices
