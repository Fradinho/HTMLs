# CLAUDE.md

This file documents the repository structure, conventions, and workflows for AI assistants working in this codebase.

## Repository Overview

**Repository:** `fradinho/htmls`
**Purpose:** A collection of HTML files and related web assets.
**Primary branch:** `main`

This repository is currently in its initial state. As content is added, this file should be updated to reflect the actual structure and conventions.

## Repository Structure

```
/
├── CLAUDE.md          # This file
└── (HTML files and assets to be added)
```

As the project grows, expect directories such as:

```
/
├── CLAUDE.md
├── index.html         # Root entry point (if applicable)
├── pages/             # Individual HTML pages
├── assets/
│   ├── css/           # Stylesheets
│   ├── js/            # JavaScript files
│   └── img/           # Images and media
└── components/        # Reusable HTML fragments (if applicable)
```

## Development Workflow

### Branching

- Default branch: `main`
- Feature branches: `feature/<short-description>`
- Fix branches: `fix/<short-description>`
- Documentation branches: `docs/<short-description>`

### Commit Messages

Use concise, imperative-mood commit messages:

```
Add login page HTML structure
Fix broken navigation links in index.html
Update contact form layout for mobile
```

### Making Changes

1. Create or switch to a feature branch off `main`
2. Edit HTML/CSS/JS files
3. Validate HTML before committing (see Validation section)
4. Commit with a descriptive message
5. Push and open a pull request targeting `main`

## HTML Conventions

### Document Structure

Every HTML file should follow this baseline structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
</head>
<body>
  <!-- content -->
</body>
</html>
```

### Formatting

- **Indentation:** 2 spaces (no tabs)
- **Attribute quoting:** Always use double quotes (`"`)
- **Self-closing tags:** Omit the trailing slash on void elements (`<br>` not `<br/>`)
- **Lowercase:** All element names and attribute names in lowercase
- **Boolean attributes:** Write without value (`<input disabled>` not `<input disabled="disabled">`)

### Accessibility

- Every `<img>` must have an `alt` attribute
- Use semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<footer>`, `<article>`, `<section>`) instead of generic `<div>` wrappers where meaning is implied
- Form inputs must have associated `<label>` elements
- Heading hierarchy must be sequential (`h1` → `h2` → `h3`; do not skip levels)
- Interactive elements must be keyboard-reachable

### CSS

- Prefer external stylesheets linked via `<link>` over inline `style` attributes
- Inline styles are acceptable only for dynamic, JavaScript-driven values
- Avoid `!important`; resolve specificity conflicts structurally

### JavaScript

- Prefer `<script src="...">` at the end of `<body>` (before `</body>`) to avoid render-blocking
- Use `defer` or `async` attributes on `<script>` tags in `<head>` when scripts must be there
- No inline event handlers (`onclick="..."`) — attach listeners in JS files instead

## Validation

Before committing HTML files, validate them:

```bash
# Using the W3C Nu HTML Checker (requires Java or Docker)
# Online: https://validator.w3.org/

# Using html-validate (Node.js):
npx html-validate <file>.html

# Using tidy:
tidy -errors -quiet <file>.html
```

Fix all errors; warnings should be reviewed and addressed where practical.

## Key Conventions for AI Assistants

- **Do not** introduce inline styles unless the change is truly dynamic
- **Do not** use deprecated HTML elements (`<center>`, `<font>`, `<marquee>`, etc.)
- **Do not** omit `<!DOCTYPE html>` or the `lang` attribute on `<html>`
- **Always** add `alt` text to images; use `alt=""` only for decorative images
- **Always** keep the heading hierarchy intact
- **Prefer** semantic elements over class-named `<div>` wrappers
- **Prefer** relative paths for internal links and asset references
- When adding new pages, update any navigation that links between pages
- When modifying structure significantly, re-validate with a HTML validator

## Claude Code Configuration

Project settings live in `.claude/settings.json` and are committed to the repository so they apply to every session.

### Active plugins

| Plugin | Source | Purpose |
|--------|--------|---------|
| `frontend-design` | `builtin` | UI/UX design assistance for frontend work |

The `frontend-design@builtin` plugin is enabled for all sessions in this repository. When working on HTML, CSS, or JS files, use its design capabilities for layout, component structure, and visual guidance.

## Notes

- This repository was initialized on 2026-05-16.
- Update this CLAUDE.md whenever significant structural or convention changes are made.
