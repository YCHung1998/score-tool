## Why

The scoring tool currently runs only as a local file (`index.html`) that must be downloaded and opened manually. Publishing it to GitHub Pages gives anyone a permanent public URL they can bookmark and open on any device — no download or setup required.

## What Changes

- Initialize a git repository in the project root
- Add a `.gitignore` to exclude OS and editor noise
- Create a GitHub repository and push the code
- Enable GitHub Pages (deploying from the `main` branch root)
- The app will be publicly accessible at a `github.io` URL

## Capabilities

### New Capabilities
- `static-hosting`: The app is publicly hosted at a stable URL via GitHub Pages, accessible from any browser without local setup

### Modified Capabilities
<!-- No existing spec-level requirements are changing -->

## Impact

- New file: `.gitignore`
- No changes to `index.html` or application logic
- No new dependencies, no build step required (single-file app deploys as-is)
- Requires: a GitHub account and a new public/private GitHub repository
