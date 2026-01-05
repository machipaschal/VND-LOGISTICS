<!-- Auto-generated: tailored Copilot instructions for contributors and coding agents -->
# Project-specific Copilot Instructions

Purpose: help an AI coding agent be immediately productive in this repository.

1) Big picture
- This is a small, single-page static site (SPA-like) composed of `index.html`, `script.js`, and `style.css`.
- UI is rendered client-side using Tailwind CSS via CDN (configured inline in the `<head>`). No build tools are present.
- All interactive logic lives in `script.js` (DOM toggles, smooth scroll, form handling). There is no backend integration present — forms are handled purely on the client and show a modal.

2) Key files and patterns (explicit examples)
- `index.html` — entry point and canonical source of markup and ids. Important IDs: `hamburger`, `mobile-nav-overlay`, `close-mobile-nav`, `quote-form`, `calculator-form`, `submission-modal`.
- `script.js` — register event listeners and DOM manipulation. Example: `toggleMobileNav()` directly sets `mobileNavOverlay.style.transform` and updates `hamburger.innerHTML`.
- `style.css` — contains small overrides and modal styles (class `.modal`, `.modal-content`). Tailwind covers most layout; `style.css` is used for background images and behavior not easily expressed via Tailwind utilities.

3) Project-specific conventions you must follow
- Keep Tailwind usage in `index.html` (currently loaded via CDN). If you need to change the Tailwind config, edit the inline `tailwind.config` script in the `<head>` (there is no build step to recompile Tailwind).
- Prefer editing classes in `index.html` and adding small overrides in `style.css` instead of trying to add a complex build toolchain.
- DOM-driven behavior uses element IDs; preserve these IDs when refactoring components unless you update `script.js` accordingly.

4) Integration & extension notes
- Forms (`quote-form`, `calculator-form`) only call `handleFormSubmission` which prevents default submission and shows the modal. To integrate a backend endpoint, replace or augment `handleFormSubmission` with a `fetch()` POST to your API and show errors/success based on the response. Example change point: `script.js` near `function handleFormSubmission(event) { ... }`.
- Images and fonts are externally hosted (Unsplash, Google Fonts). Consider adding a local `assets/` folder if you need offline builds.

5) Local development / preview (no build tools)
- Open `index.html` in a browser directly, or run a simple static server. Example (PowerShell):
```
cd "c:\Users\MACHI\Documents\VND\VND-LOGISTICS";
python -m http.server 8000
# then open http://localhost:8000 in a browser
```
- VS Code Live Server extension also works for quick reloads.

6) When making changes, what to watch for
- Because Tailwind is included via CDN and configured inline, changes to classes are reflected immediately in the browser — no rebuild step.
- Keep `script.js` event attachments intact when editing markup (IDs and anchor hrefs like `#calculator`). The smooth-scroll behavior listens to `a[href^="#"]` so renaming anchors will affect scroll.

7) Common tasks and where to implement them
- Add server-side form handling: implement an API and update `handleFormSubmission` in `script.js` to `fetch()` and handle JSON responses.
- Add new pages: create new HTML files and link from `index.html` rather than converting to a SPA framework — the repo is intentionally minimal.

8) Merge guidance for agents
- If a `.github/copilot-instructions.md` already exists, preserve any project rationale and brief examples, but ensure the 1–2 line run instructions and the `script.js` edit points are present.

If any of these details are out of date or you want conventions expanded (linting, CI, build), tell me which area to augment and I will iterate.
