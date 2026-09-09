# Privacy Officer Command

A free, self-contained, in-browser training simulator for HIPAA / healthcare privacy
compliance — now with a dedicated comparative thread against the **Philippine Data
Privacy Act of 2012 (Republic Act No. 10173)**. Twenty-six modules across four levels,
a Level 0 diagnostic, a living "Regulatory Watch" tracker covering both the U.S. and
Philippine regulatory landscape, and hands-on interactive casework — PHI/SPI
classification, incident response, breach risk assessment, a mock OCR investigation,
executive briefing drafting, and a full HIPAA-vs-RA10173 module built for anyone
working cross-border healthcare compliance (a very real role given the Philippines'
large health-BPO sector serving U.S. clients).

**This is one HTML file.** No backend, no build step, no npm install, no database.
Open it in a browser and it works. That also makes it trivial to host for free.

> **Educational tool, not legal advice.** Every case, document, and organization in
> this app is fictional. Regulatory content was verified as of the date noted inside
> the app (see the "Regulatory Watch" section) against the U.S. Official Federal
> Register/HHS/OCR and the Philippine Official Gazette/National Privacy Commission —
> healthcare privacy law changes in both countries, so always confirm anything
> time-sensitive at [hhs.gov/hipaa](https://www.hhs.gov/hipaa/index.html) or
> [privacy.gov.ph](https://privacy.gov.ph) before relying on it operationally.

---

## Quick start (no deployment needed)

Just download `index.html` and double-click it, or open it in any modern browser
(`File → Open`). Everything works offline except the Google Fonts used for
typography, which gracefully fall back to system fonts if there's no connection.

## Deploying to GitHub Pages (free hosting, ~2 minutes)

1. **Create a repository.** On GitHub, click **New repository**. Any name works —
   for example `privacy-officer-command`. Make it **public** (GitHub Pages is free
   for public repos; private repos need GitHub Pro/Team/Enterprise for Pages).
2. **Add the files in this folder** (`index.html`, `.nojekyll`, `README.md`,
   `LICENSE`) to the repository — either drag-and-drop them in the GitHub web UI
   ("Add file → Upload files"), or via git:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Privacy Officer Command training app"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
   git push -u origin main
   ```
3. **Turn on Pages.** In the repository, go to **Settings → Pages**. Under
   "Build and deployment," set **Source** to **Deploy from a branch**, then set
   **Branch** to `main` and the folder to `/ (root)`. Click **Save**.
4. **Wait about a minute**, then visit:
   - `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/` (most repos), or
   - `https://YOUR-USERNAME.github.io/` (only if your repo is literally named
     `YOUR-USERNAME.github.io`)

That's it — no build action, no `gh-pages` branch, no dependencies. The
`.nojekyll` file just tells GitHub not to run its Jekyll static-site processor,
which isn't needed here and can occasionally interfere with plain HTML files.

### Other free static hosts

Because this is a single static file, it also deploys as-is to Netlify, Vercel,
Cloudflare Pages, or any static file host — drag the file into their dashboard,
or point the host at this repo. No framework, no build command needed.

## How progress saving works

The app auto-saves your progress (answers, written work, module status) using a
three-tier fallback it detects automatically:

1. **Claude's built-in storage**, if viewed as an artifact inside Claude.ai.
2. **Your browser's `localStorage`**, once deployed anywhere else (GitHub Pages,
   opened locally, etc.). This is per-browser and per-device — it won't follow
   you to a different computer or browser, and clearing your browser's site data
   will erase it.
3. If neither is available (e.g. some private/incognito modes), the app still
   works, it just won't remember anything between visits — use the **Download my
   portfolio** button on the Progress page before closing the tab.

## Project structure

```
index.html    — the entire application (HTML + CSS + JavaScript, no dependencies)
.nojekyll     — disables GitHub Pages' Jekyll processing (not needed for this app)
README.md     — this file
LICENSE       — MIT license (feel free to replace with whatever fits your use — see note below)
```

Everything — training content, interactive exercises, scoring logic, and
rendering — lives inside `index.html`, organized into two clearly separated
sections (marked with comment headers in the file):

- **Data layer** — modules, cases, question banks, regulatory-status entries,
  citations. Edit this to add new content without touching any UI code.
- **Application layer** — state management, storage, rendering, and the
  interactive engines (classification, scenario decisions, workflows,
  four-factor analysis, etc.).

## Updating regulatory content

Healthcare privacy law changes — on both sides of this app. Search the file for
`APP_BUILD_DATE` and the `REGULATORY_WATCH` array — that's the "living" part of the
app designed to be updated as rules move between proposed, effective, and vacated
status, covering both HIPAA developments and Philippine NPC circulars/advisories.
The `AUTHORITIES` object holds the citation library (Official Gazette, HHS/OCR,
National Privacy Commission, etc.) used by the "Authority" buttons throughout the
app. Module 26 (`m26` in `SCENARIO_BANKS`) is the dedicated HIPAA-vs-RA10173 module
if you want to extend that comparison further.

## License

An MIT `LICENSE` file is included as a common, permissive default for this kind
of project — replace the placeholder name/year or swap in a different license
if you'd prefer. This is your call to make, not a legal recommendation.

## Disclaimer

This application is an educational simulation. Nothing it produces — risk
registers, breach determinations, investigation reports, policy drafts — is
real compliance work product. The Readiness Index and competency scores are
educational indicators only; they are not a professional qualification or
certification.
