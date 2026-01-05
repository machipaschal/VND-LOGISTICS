# VND-LOGISTICS

Small, single-page static site for VND UNIQUE — a simple logistics and transport landing page.

Overview
- This repository is a minimal static website (no build tools). The UI is rendered client-side using Tailwind CSS (CDN) and a small amount of custom CSS/JS.

Tech stack
- HTML, CSS, JavaScript
- Tailwind CSS loaded via CDN (configured inline in `index.html`)
- Fonts & images loaded from external CDNs (Google Fonts, Unsplash)

Project structure (important files)
- `index.html` — single-page app markup and inline Tailwind configuration. This is the canonical source of DOM structure and IDs.
- `script.js` — all interactive behavior (mobile nav toggles, smooth scrolling, form handling, modal). Key functions/IDs: `toggleMobileNav()`, `handleFormSubmission`, `hamburger`, `mobile-nav-overlay`, `close-mobile-nav`, `quote-form`, `calculator-form`, `submission-modal`.
- `style.css` — project-specific overrides and modal styling (classes `.modal`, `.modal-content`, `.hero-background`). Use this for styles not easily expressed with Tailwind utilities.
- `.github/copilot-instructions.md` — project-specific guidance for AI coding agents.

Run / preview locally
- No build step. Open `index.html` in a browser directly, or run a simple static server for nicer local testing.

PowerShell example:
```powershell
cd "c:\Users\MACHI\Documents\VND\VND-LOGISTICS";
python -m http.server 8000
# open http://localhost:8000 in a browser
```

Or use VS Code Live Server for hot reload.

Editing notes & conventions
- Tailwind is provided via CDN and configured inline in `index.html` with `tailwind.config`. There is no compilation step—editing classes in `index.html` updates the UI immediately.
- Keep the DOM element IDs mentioned above unchanged unless you update `script.js` accordingly — JS attaches listeners by ID and by `a[href^="#"]` for smooth scrolling.
- `script.js` currently prevents default form submission and shows a local modal. To integrate server-side form handling, replace the `handleFormSubmission` implementation with a `fetch()` call to your API and handle success/error states in the modal.

Example: turning `handleFormSubmission` into a `fetch()` call
- See `script.js` near `function handleFormSubmission(event) { ... }` — add a `fetch()` POST and show server feedback in the existing modal.

Adding pages or assets
- If you add pages, create new `.html` files and link them from `index.html`. The project intentionally avoids a SPA framework and build complexity.
- Consider adding an `assets/` folder for local images if you want offline development or to avoid hotlinking.

Deployment
- This static site can be deployed to GitHub Pages, Netlify, or any static hosting service. For GitHub Pages, enable Pages on the `main` branch and set the site root to `/`.

Contributing / PRs
- Keep changes focused and small. Preserve IDs and JS behavior unless updating `script.js` to match markup changes.

Questions / next steps
- Want a sample `fetch()` integration in `script.js` to demonstrate server submission? I can add that.
- Want a short `LICENSE` file or GitHub Pages deployment configuration added?

Contact
- Maintainer: repository owner `machipaschal` (see repo).

