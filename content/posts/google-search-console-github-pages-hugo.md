---
title: "Google Search Console for GitHub Pages (Hugo): Setup + Verification"
date: 2026-03-14
draft: false
description: "Step-by-step: add your GitHub Pages site to Google Search Console and verify ownership using a meta tag (Hugo) or HTML file."
tags: ["seo", "google-search-console", "github-pages", "hugo"]
---

If you’re publishing a Hugo blog on **GitHub Pages**, Google Search Console (GSC) is the fastest way to:

- confirm Google can see your site
- submit your sitemap
- monitor impressions/clicks
- catch indexing errors early

This guide shows two verification methods that work well for Hugo:

1) **HTML tag (recommended)**
2) **HTML file upload**

## 1) Add your property (URL Prefix)

In GSC, add a new property:

- Property type: **URL prefix**
- URL: `https://YOURNAME.github.io/`

Why URL Prefix?
- GitHub Pages sites aren’t true “domains” you control via DNS.
- URL Prefix verification works without DNS.

## 2) Verify ownership (recommended: HTML tag)

GSC will show a meta tag like:

```html
<meta name="google-site-verification" content="YOUR_TOKEN" />
```

### Hugo: add the meta tag safely

Create this file in your Hugo project:

- `layouts/partials/extend_head.html`

Add the meta tag inside.

Example:

```html
<meta name="google-site-verification" content="YOUR_TOKEN" />
```

Then:

```bash
hugo
```

Commit + push to GitHub Pages.

After your site is updated, go back to GSC and click **Verify**.

## 3) Alternative verification: HTML file

GSC may also offer an HTML file like:

- `googleXXXXXXXXXXXX.html`

You must publish that file at:

- `https://YOURNAME.github.io/googleXXXXXXXXXXXX.html`

### Hugo: where to place it

Put the verification file in:

- `static/googleXXXXXXXXXXXX.html`

Hugo copies everything in `static/` to the site root.

The file content is usually:

```text
google-site-verification: googleXXXXXXXXXXXX.html
```

(Use the exact file contents GSC expects.)

## 4) Submit your sitemap

Once verified, submit:

- `https://YOURNAME.github.io/sitemap.xml`

In GSC:

- Sitemaps → Add a new sitemap → `sitemap.xml`

## 5) Common gotchas (GitHub Pages)

- Make sure your Hugo `baseURL` matches your live URL (including the trailing slash).
- Don’t keep the meta tag in a draft-only branch.
- GitHub Pages deploy can take a few minutes—verify after it’s live.

That’s it—once GSC is connected, your SEO work becomes measurable.
