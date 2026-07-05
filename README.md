# Value Masters 2026 — Credentials Site

A tiny static site that hosts verifiable credential pages for Value Masters 2026
winners, in the same spirit as CFA Institute's "Add to Profile" badges.

## Folder structure

```
/
├── index.html                      -> landing page, lists all credentials
├── assets/
│   ├── style.css                   -> shared styling
│   └── logo.png                    -> Value Masters 2026 emblem
└── credentials/
    └── dilshan-tharindu.html       -> one page per credential
```

**This structure is the fix for the earlier folder issue**: everything lives
inside one repo, `assets/` holds shared files referenced with relative paths
(`../assets/...` from inside `credentials/`, `assets/...` from `index.html`),
and each new credential is just one more file in `credentials/`.

## How to publish with GitHub Pages

1. Create a new repo on GitHub, e.g. `valuemasters2026-credentials`
   (public repo, since GitHub Pages on the free tier needs public repos).
2. Upload this whole folder's contents to the repo root (keep the structure above).
3. In the repo: **Settings → Pages → Source** → select the `main` branch,
   root folder (`/`) → **Save**.
4. GitHub gives you a URL like:
   `https://dils1321.github.io/valuemasters2026-credentials/`
5. Your credential page will then live at:
   `https://dils1321.github.io/valuemasters2026-credentials/credentials/dilshan-tharindu.html`

## Before you publish — update the real URL

Once you know the exact GitHub Pages URL, nothing else needs to change:
each credential page reads its own URL automatically (`window.location.href`)
for the "Add to LinkedIn profile" and "Share on LinkedIn" buttons, so there's
no hardcoded domain to fix.

## Adding a new winner's credential

1. Duplicate `credentials/dilshan-tharindu.html`.
2. Rename it, e.g. `credentials/jane-doe.html`.
3. Edit: name, credential title, issue date, credential ID in the "detail-grid"
   section and the `<h1>`/meta tags at the top.
4. Add a matching entry to `index.html`'s `index-list` so it's discoverable.

## LinkedIn "Add to Profile" button

The button on each credential page builds a real LinkedIn deep link
(`linkedin.com/profile/add?...`) using that page's own URL, name, issuing
organization, and issue date — the same mechanism CFA Institute, Coursera,
and Credly use. LinkedIn pulls in whatever `certUrl` you pass in, so make
sure the page is live on the internet before anyone clicks the button
(LinkedIn will show/link to that URL from the person's profile).
