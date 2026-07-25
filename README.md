# University Logo Finder

A generic, searchable site for finding official university/college logos, addresses, and federal school codes. No branding to any one organization — anyone can use it to find and download a school's logo.

## What's here

- `index.html` — the whole site (search, filter, select, download). No build step, no server-side code.
- `data/master.json` — one record per school: official name, alias, address, federal school code, football conference, and which logo files exist for it.
- `logos/white/` — White Background logo PNGs (208 schools).
- `logos/transparent/` — Transparent Background logo PNGs (205 schools).

## Status right now

- 208 schools have a White Background logo, 205 have a Transparent Background logo.
- 363 of 388 schools have address + Federal School Code data matched.
- Football conference data was researched separately per school (current as of the 2025 season, with confirmed 2026 conference moves noted inline) and covers every school in the list — most fields say the actual conference; schools without a football program say so.
- A handful of schools (mostly discontinued or merged institutions — Parsons College, Northrop University, and similar) have blank address fields since they no longer appear in current institutional records.

## Publishing it (GitHub Pages — free, no server needed)

Since there are 200+ image files, uploading through the GitHub website directly will hit its 100-file-per-drag limit, so use GitHub Desktop instead:

1. Create a free GitHub account at github.com if you don't have one, and install GitHub Desktop from desktop.github.com.
2. On github.com, create a new repository (Public, so Pages hosting is free).
3. In GitHub Desktop: File → Clone Repository → your new repo → pick a folder to save it locally.
4. Copy everything from inside this `webapp` folder into that cloned repo folder (so `index.html` sits at the top level of the repo).
5. In GitHub Desktop, write a commit summary, click "Commit to main," then "Push origin."
6. On github.com, go to the repo's Settings → Pages, set Source to "Deploy from a branch," branch `main`, folder `/(root)`, and Save.
7. After a minute or two, refresh that page — it'll show your live URL, e.g. `https://yourusername.github.io/repo-name/`.

Any static host works the same way (Netlify, Vercel, S3, your own server) if you'd rather not use GitHub.

## How people use the site

- Search by school name, alias, city/state, football conference, or federal school code.
- Filter by logo version (White/Transparent Background) or by football conference.
- Check boxes on the schools they want, click "Select all filtered" to grab everything currently shown.
- Click "Download selected," choose White or Transparent Background, choose a file naming convention (official school name, short alias, federal school code, or original filename), and download. One file downloads directly; multiple download as a single zip.
- Each card has a "Report an error / request an edit" link that opens a pre-filled email. There's also a "Request a school be added" button in the header for schools missing from the list. Both currently go to **zacgillman@gmail.com** — change the `REPORT_EMAIL` constant near the top of the `<script>` block in `index.html` if that should go somewhere else later.

## Updating the data later

The build scripts that produced `data/master.json` (joining the roster CSV, the address/federal-ID CSV, the logo filenames, and the conference research) aren't included here since they were a one-time step — just ask Claude to redo the merge if the underlying spreadsheets or logo folders change.
