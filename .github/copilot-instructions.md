# Copilot instructions — Wedding site

Purpose: short, actionable rules so an AI coding agent can be immediately productive in this repository.

1) Big picture
- This is a small static website composed of standalone HTML pages: [index.html](index.html), [geminy.html](geminy.html), [jopa.html](jopa.html).
- Each page is self-contained: markup, CSS (in <style>), inline SVGs and small inline scripts.
- **Design reference**: All layout and styling changes must follow the visual design mockup stored in `.github/design-reference.png`. This mockup shows the final approved layout, colors, typography, spacing, and interactive elements. Any changes to design or layout should align with this reference.
- npm is initialized with `live-server` for local development. Use `npm run start` to preview changes at `http://localhost:8000`.

2) Key patterns to follow (examples)
- Styling: CSS variables in `:root` are used for theming. See `:root` in [geminy.html](geminy.html) and [index.html](index.html).
- Decorative assets: SVGs are inlined inside the HTML (not in separate files). Preserve inline SVG structure and ids when editing.
- Animations: small scripts use `IntersectionObserver` to add `.visible` to `.fade` elements (example in `geminy.html`). If you change animations, update both CSS and the observer logic.
- Layout: pages use a central `.container` and large sections like `.hero`, `.program`, `.intro`. Keep these class names unless the user asks for a refactor.

3) Developer workflows (how to preview / test changes)
- With npm initialized, start the local dev server:

```bash
cd c:\Projects\Wedding
npm install
npm run start
# Server runs on http://localhost:8000 with auto-reload on file changes
```

- (Legacy) Alternatively, run a lightweight HTTP server directly:

```bash
cd c:\Projects\Wedding
python -m http.server 8000
# then open http://localhost:8000/index.html
```

4) Editing rules (what an AI agent must preserve)
- Do not introduce a build system or new toolchain without explicit user approval (npm is already set up).
- Prefer small, focused edits: modify an HTML file in-place or add small JS/CSS files. If adding files, place them under a new `assets/` folder (e.g. `assets/js/`, `assets/css/`, `assets/img/`) and use relative links.
- Preserve Google Fonts links and existing external resource URLs unless the user requests a change.
- Keep text content localization/encoding: pages use `lang="ru"` and `charset=UTF-8`. Do not remove these attributes.
- **Always consult the design reference** (`.github/design-reference.png`) when making any layout, color, typography, or spacing changes. The mockup is the source of truth for the final visual appearance.

5) Common tasks and examples
- Update colors: edit `:root` variables in the file you change (example: `--bg`, `--text`, `--green` in [geminy.html](geminy.html)).
- Change hero text: update the `<h1>` inside `.hero` and keep the surrounding `.container` markup.
- Add a new section: follow the existing pattern — a `<section>` with `.container` and class like `.intro` or `.program`, and copy the surrounding decorative SVG pattern.
- Add interactive JS: Put new logic in a small file at `assets/js/` and include it with a relative `<script src="assets/js/name.js"></script>` before `</body>`.

6) What not to do
- Don't split single-file pages into frameworks (React/Vue) or assume a build process.
- Don't remove or minify inline SVGs; they are intentionally editable and styled by page CSS.

7) When unsure, ask the user
- If a requested change affects multiple pages, propose the change and ask whether to apply it across all pages.
- If adding an asset folder or changing linking patterns, confirm the preferred structure (assets/ vs. static/).

If any part of this feels incomplete or you want additional examples (e.g., where to place images or how to version styles), tell me what to expand and I'll iterate.
