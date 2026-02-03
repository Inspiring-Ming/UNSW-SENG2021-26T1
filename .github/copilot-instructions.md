<!-- Purpose: concise guidance for AI coding agents working on this repo -->
# Copilot / AI agent instructions — UNSW-SENG2021-26T1

This repository is a small static website used to host weekly topics. The guidance below is focused, actionable, and specific to patterns in this codebase.

- Project type: static HTML/CSS site (no build step). Files of interest: `index.html`, `styles.css`, and the `weeks/` directory which contains `weekN.html` pages.
- Hosting: site is served via GitHub Pages (see footer text in `index.html` / week pages).

Quick facts to reference in edits
- Navigation pattern: `index.html` contains a grid of links like `<a href="weeks/week2.html" class="week-card">` — when adding a week, update `index.html` to include a new card.
- Week pages live in `weeks/` and use relative links to `../styles.css` and `../index.html`. Week pages include previous/next links like `<a href="week1.html">← Previous: Week 1</a>`; keep these relative and consistent.
- Comments: each week page embeds Giscus via a script tag (example in `weeks/week2.html`) with attributes such as `data-repo` and `data-repo-id`. Do not change `data-repo-id` or `data-category-id` unless you understand Giscus configuration and are intentionally migrating comment data.

How to run locally
- No build required. Serve the folder with a simple static server. Example (macOS):
  - `python3 -m http.server 8000` then open `http://localhost:8000`
  - or use `npx http-server` / `live-server` if preferred.

Editing conventions and examples
- Add a new week page: create `weeks/week11.html` following the structure of existing pages (`weeks/week2.html` is a good template). Important: link `../styles.css`, add a back-link to `../index.html`, and add `week-nav` previous/next anchors.
- Update `index.html` when adding/removing weeks so the grid reflects the site navigation. Keep card markup consistent (use `week-card`, `week-grid` classes). Example card:
  `<a href="weeks/week2.html" class="week-card">
     <h3>Week 2</h3>
     <p>APIs & Web Architecture</p>
   </a>`
- Styling: global styles are in `styles.css`. Reuse existing class names (`content-card`, `week-card`, `back-link`, `comments-section`, etc.) to preserve consistent look.

Repository patterns and gotchas
- Relative linking is used extensively; avoid converting to absolute paths unless necessary. Week pages reference `../styles.css` so path changes will break styling if not updated consistently.
- There is no JS build pipeline; adding npm/tooling is allowed but explain why and add minimal config (`package.json`) and brief steps in the PR description.
- Comments are powered by Giscus (third-party). Changing repo/comment configuration risks losing/disconnecting comments — surface any such change to maintainers in the PR.

PR guidance for contributors
- Small content changes: edit the week page in `weeks/` and update `index.html` if navigation needs to change. Keep commits atomic and title PRs like `docs(weekX): update prompt and links`.
- Structural/tooling changes: include a short README section and sample commands; prefer simple changes and document migration steps.

If unclear, check these files as ground truth: `index.html`, `styles.css`, `weeks/week1.html`, `weeks/week2.html`.

If you want me to extend this file (examples, tests, or a local dev helper script), say which area to expand.
