## Context

The project is a single `index.html` file with no build tooling, no package manager, and no external dependencies. It uses `localStorage` for persistence. The project directory is not yet a git repository.

GitHub Pages serves static files directly from a GitHub repository branch — the root `index.html` is automatically served as the homepage, making this a zero-configuration deployment.

## Goals / Non-Goals

**Goals:**
- Get the app live at a public `github.io` URL with minimal setup
- Keep zero build steps — deploy the file as-is
- Enable future updates by pushing commits to `main`

**Non-Goals:**
- Custom domain setup
- CI/CD pipeline or automated deploy on push (GitHub Pages already handles this)
- Server-side features or backend
- Any changes to the app code itself

## Decisions

**1. Deploy source: root of `main` branch (not `gh-pages` branch, not `/docs` folder)**  
The project has a single file at the root. Using the `main` branch root is the simplest option — no separate branch to maintain and no subdirectory to configure. GitHub Pages supports this directly.

**2. No build step, no GitHub Actions workflow**  
A static single-file app requires no compilation. GitHub Pages serves `index.html` from the branch root with zero additional configuration. Adding a workflow would be unnecessary complexity.

**3. Repository visibility: user's choice**  
GitHub Pages works for both public and private repositories (private requires GitHub Pro/Team). The tasks will note this but leave the choice to the user.

## Risks / Trade-offs

- [localStorage is per-origin — data saved on one device won't appear on another] → Expected behavior; the app is a local scoring tool, not a sync service. Document this in the help tab if needed.
- [GitHub Pages URL includes the repo name as a path prefix (e.g. `/score-tool/`)] → The app uses no absolute paths or root-relative URLs, so this is not an issue.
- [Pushing to a public repo exposes the source code] → The code is a single static file with no secrets; this is acceptable.

## Migration Plan

1. `git init` in the project root
2. Add `.gitignore`
3. Initial commit with `index.html` and planning artifacts
4. Create GitHub repo via `gh repo create`
5. Push `main` branch
6. Enable GitHub Pages in repo Settings → Pages → Source: `main` branch, `/ (root)`
7. Confirm the site is live at the provided URL
