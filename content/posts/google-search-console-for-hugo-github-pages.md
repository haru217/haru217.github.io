---
title: "Google Search Console for Hugo + GitHub Pages: Fix the 404 and Get Verified"
date: 2026-03-14T20:10:00+09:00
draft: false
---

If Google Search Console says:
- **“We couldn’t find your site”**
- **“Ownership verification failed”**

…and you’re using **Hugo + GitHub Pages**, the issue is almost always the same:

1) your Pages site is not actually live (still 404), or
2) you verified the wrong URL (baseURL mismatch), or
3) your HTML tag never got deployed.

This guide walks you through a reliable, boring checklist that works.

## Step 1: Confirm your site is live (not 404)
Open your public URL in an incognito window.

Typical GitHub Pages URLs:
- User/Org site: `https://<username>.github.io/`
- Project site: `https://<username>.github.io/<repo>/`

If you see GitHub’s message like **“There isn't a GitHub Pages site here.”** you must fix Pages first.

### Fix: Enable GitHub Pages correctly
In your repo:
- Settings → Pages
- Build and deployment:
  - **Source: GitHub Actions** (recommended for Hugo), or
  - **Deploy from a branch** (only if you generate static files yourself)

For Hugo, **GitHub Actions** is usually easiest.

## Step 2: Make sure Hugo baseURL matches the real URL
In Hugo config (`hugo.yaml` / `config.toml` / `config.yaml`), set:

- For user site:
  - `baseURL: "https://<username>.github.io/"`
- For project site:
  - `baseURL: "https://<username>.github.io/<repo>/"`

If baseURL is wrong, your sitemap, canonical URLs, and internal links will be wrong too.

## Step 3: Deploy once, then verify
Verification methods that work well:

### Option A (recommended): HTML tag verification
Search Console gives you something like:

```html
<meta name="google-site-verification" content="..." />
```

Add it to your site head (theme-dependent). Common approaches:
- If your theme supports custom head injection, use that
- Otherwise, add it to a `layouts/partials/head.html` override

Then:
1. commit
2. push
3. wait for Pages build to finish
4. re-open the site to confirm the tag exists in the rendered HTML
5. click **Verify** in Search Console

### Option B: DNS TXT record (most stable)
If you have a custom domain, DNS verification is stable and doesn’t break when you change themes.

## Step 4: Submit your sitemap (don’t skip this)
Once verified, submit:
- `https://<site>/sitemap.xml`

Hugo generates a sitemap by default for most setups.

## Step 5: Expect the first results to be slow
Normal timeline:
- Verification: immediate
- Sitemap accepted: same day
- First indexing: a few days

What you can control:
- publish more posts
- internal links between posts
- strong titles + meta descriptions

## Quick failure checklist
If verification fails again, check:
- the site URL returns **200** (not 404)
- your GitHub Actions deploy is green
- the meta tag is present in the final HTML (View Source)
- you verified the correct property (`https://` vs `http://`, trailing slash)
