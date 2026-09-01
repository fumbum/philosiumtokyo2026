# Philosium Tokyo 2026 — site

A single, self-contained page (`index.html` — no build step, no dependencies besides two Google Fonts) with the event title, subtitle, description, quick info, program, and a registration link to the Google Form (`https://forms.gle/Ca6pWJ7sjqAA4ue4A`).

## Option A — new repo, deployed on its own

1. Create a new GitHub repo (e.g. `philosium-tokyo`), public.
2. From this folder:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Add Philosium Tokyo 2026 site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/philosium-tokyo.git
   git push -u origin main
   ```
3. In the Cloudflare dashboard → **Workers & Pages → Create → Pages → Connect to Git**, pick the repo. Build settings: **no build command, output directory `/`** (it's a static file, nothing to build).
4. Cloudflare gives you a `*.pages.dev` URL immediately; add a custom domain (e.g. `tokyo.philosium.com`) under the Pages project's **Custom domains** tab once it's live — that's a CNAME Cloudflare sets up for you if the domain's DNS is already on Cloudflare.

## Option B — add as a page inside the existing philosium.com repo

If `philosium.com` is already a GitHub + Cloudflare Pages static site, drop `index.html` into a subfolder (e.g. `/tokyo/index.html`) of that repo instead of a new repo, then commit + push the same way. It'll be reachable at `philosium.com/tokyo` with no separate Cloudflare project needed — Pages redeploys automatically on every push to the connected branch.

## Editing later

Everything is in one file — text, layout, and styling are all inline in `index.html`. To change wording, dates, or the form link, edit the file directly and push again; Cloudflare Pages redeploys automatically within a minute or two of the push.
