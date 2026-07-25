# SigEp Chapter School Logos — Searchable Download Site

## What's here

- `index.html` — the whole site (search, select, download). No build step, no server-side code.
- `data/master.json` — one record per SigEp chapter: chapter designation, official school name, alias, address, federal school code, and which logo files exist for it.
- `logos/white/` — White Background logo PNGs.
- `logos/transparent/` — Transparent logo PNGs (add these once the source folder is downloaded — see note below).

## Status right now

- 387 chapters total in the roster.
- 208 have a White Background logo matched and ready.
- 363 have address + Federal School Code data matched from your Salesforce export.
- The Transparent folder was showing as iCloud placeholders (not yet downloaded to disk) when this was built, so `logos/transparent/` is currently empty. Once you force-download that folder in Finder, send the files over and this can be filled in — no code changes needed, just files added to that folder and a re-run of the matching script.
- 24 chapters (mostly discontinued/merged schools like Parsons College, Northrop University, defunct branch campuses) had no match in the address export — flagged with blank address fields in the data file. Worth a manual pass if that matters to you.

## Publishing it (GitHub Pages — free, no server needed)

1. Create a new repository on github.com (public repos get free Pages hosting; private repos need a paid plan for Pages).
2. Upload the contents of this `webapp` folder to the repo (drag-and-drop on github.com works fine for this size, or use `git push` if you're comfortable with git).
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment," set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
5. Save. GitHub gives you a URL like `https://yourusername.github.io/repo-name/` within a minute or two — that's the live site anyone can use.

Any time you add more logos or update the data, just upload the changed files to the repo and the live site updates automatically (usually within a minute).

## Alternatives to GitHub Pages

The site is just static files, so it also works dropped into Netlify, Vercel, an S3 bucket with static hosting, or any regular web server — no GitHub required if you'd rather use something else.

## How end users use it

- Type in the search box to filter by school name, chapter designation, alias, city/state, or federal school code.
- Check the boxes on the schools they want.
- Click **Download selected**, choose White Background or Transparent, choose a file naming convention (chapter designation, official school name, alias, chapter+school, or federal ID), and download.
- One file downloads directly; multiple files download as a single zip.

## Updating the data later

The two source CSVs and the `merge.py` / `build_data.py` scripts used to build `data/master.json` aren't included here since they're a one-time build step, but the same approach (join chapter/name CSV with address/federal ID CSV by school name) can be re-run any time the underlying spreadsheets change. Ask Claude to redo it if you get an updated CSV.
