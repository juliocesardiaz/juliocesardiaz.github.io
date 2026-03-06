# CLAUDE.md — AI Assistant Guide for juliocesardiaz.github.io

This file provides context for AI assistants (Claude Code and others) working in this repository.

## Project Overview

Personal portfolio website for Julio C. Diaz, hosted on GitHub Pages at the custom domain **juliocdiaz.com**. The site is a static portfolio showcasing three web development projects, each with its own embedded single-page application (SPA).

## Repository Structure

```
juliocesardiaz.github.io/
├── CLAUDE.md                  # This file
├── CNAME                      # Custom domain: juliocdiaz.com
├── index.html                 # Landing page (currently "Under Construction")
├── css/
│   ├── style.css              # Custom site-wide styles
│   ├── font-awesome-4.5.0/    # Icon library (vendored)
│   └── skeleton-2.0.4/        # Responsive CSS framework (vendored)
├── images/                    # Project thumbnail images
│   ├── experts.png
│   ├── face2face.png
│   └── webdubz.png
├── pages/
│   ├── work.html              # Portfolio index listing all projects
│   ├── comingsoon.html        # Placeholder page
│   ├── experts.html           # Experts project showcase page
│   ├── face2face.html         # Face2Face project showcase page
│   ├── webdubz.html           # WebDubz project showcase page
│   ├── experts/               # Experts SPA (AngularJS)
│   │   ├── index.html
│   │   ├── app.js             # AngularJS app + route config
│   │   ├── controllers/       # QuestionsController, AnswersController
│   │   ├── services/          # QuestionsFactory, UtilitiesFactory
│   │   ├── partials/          # HTML templates
│   │   ├── css/               # App-specific styles
│   │   └── lib/               # Vendored AngularJS libraries
│   └── webdubz2/              # WebDubz SPA (AngularJS)
│       ├── index.html
│       ├── app.js             # AngularJS app + UI-Router config
│       ├── controllers/       # TraxController, UploadController
│       ├── services/          # TraxFactory
│       ├── partials/          # HTML templates
│       ├── css/               # App-specific styles
│       ├── lib/               # Vendored libraries (WavesurferJS, etc.)
│       └── node_modules/      # Checked-in npm deps (do not delete)
└── pdf/
    └── Diaz_Julio-Resume.pdf  # Resume file
```

## Technology Stack

### Main Site
- **HTML5 / CSS3** — No build tools; raw HTML files
- **Skeleton 2.0.4** — Lightweight responsive grid framework (vendored under `css/`)
- **Font Awesome 4.5.0** — Icon library (vendored under `css/`)

### SPAs (inside `pages/`)
- **AngularJS** — Both `experts/` and `webdubz2/` use AngularJS 1.x
- **Angular UI-Router** — Client-side routing in webdubz2
- **ng-File-Upload** — File upload directive used in webdubz2
- **WavesurferJS** — Audio waveform visualization in webdubz2
- **Bootstrap** — CSS framework used in the Experts app

## Project Descriptions

### Experts (`pages/experts/`)
A Q&A/course-roster web application built with AngularJS. Collaborators: Julio Diaz & Ashlin Aronin (Sep 2015). MIT licensed.

### WebDubz (`pages/webdubz2/`)
A music sharing and remixing platform. Frontend is AngularJS; the backend (PHP/Laravel/MySQL/FFmpeg) is external and not in this repo. MIT licensed.

### Face2Face (`pages/face2face.html`)
A collaboration tool built with PHP, Silex, Twig, and MySQL. External project (was hosted on OpenShift); only the showcase page lives here.

## Development Workflow

### Local Development
There is **no build step**. Serve files directly with a static server:

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

Then open `http://localhost:8000` in a browser.

### Deployment
Pushing to the `master` branch automatically deploys via **GitHub Pages**. The custom domain is set via the `CNAME` file (`juliocdiaz.com`).

### Branching Convention
- `master` — production branch, auto-deployed to GitHub Pages
- `claude/<description>-<session-id>` — branches created by Claude Code for AI-driven changes

## Key Conventions

### File Editing
- All HTML, CSS, and JS files are edited directly — no compilation or transpilation.
- Vendor libraries are **checked in** (not installed via npm/CDN at runtime). Do not delete `node_modules/` inside `pages/webdubz2/` — it is intentionally committed.
- Indentation: **3 spaces** (per `.vscode/settings.json` in webdubz2; apply consistently across the repo).

### AngularJS Patterns
Both SPAs follow the same AngularJS 1.x structure:
- `app.js` — module definition and route/state configuration
- `controllers/` — one file per controller (`*Controller.js`)
- `services/` — one file per factory (`*Factory.js`)
- `partials/` — HTML templates referenced by routes

### CSS
- Global styles live in `css/style.css`.
- App-specific styles live in each SPA's own `css/` directory.
- Skeleton's 12-column grid is used for layout on the main site.

### Assets
- Project thumbnail images go in `images/` at the repo root.
- The resume PDF lives in `pdf/`.

## What to Avoid

- **Do not add a build system** (webpack, Vite, etc.) unless explicitly requested — the project intentionally has no build step.
- **Do not delete `node_modules/`** inside `pages/webdubz2/` — it is tracked by git.
- **Do not push directly to `master`** without confirmation — that triggers a live deployment.
- **Do not add Angular 2+** or React; this project uses AngularJS 1.x by design.
- **Do not create new documentation files** (READMEs, etc.) beyond what's explicitly requested.

## Git Notes

- Remote: `origin` → GitHub (`juliocesardiaz/juliocesardiaz.github.io`)
- Primary production branch: `master`
- AI feature branches follow the pattern `claude/<feature>-<session-id>`
- Push command: `git push -u origin <branch-name>`
