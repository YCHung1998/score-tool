## ADDED Requirements

### Requirement: App is publicly accessible via a stable URL
The app SHALL be hosted at a permanent public URL (GitHub Pages `github.io` domain) that anyone can open in a browser without downloading files.

#### Scenario: Accessing the live URL
- **WHEN** a user navigates to the GitHub Pages URL in any modern browser
- **THEN** the scoring tool loads and is fully functional

#### Scenario: App works without local file access
- **WHEN** the app is accessed via the public URL (not a local `file://` path)
- **THEN** all features (roster, scoring, rankings, export, import, help) work correctly

### Requirement: App deploys from the repository root with no build step
The deployment SHALL serve `index.html` directly from the root of the `main` branch without any compilation, bundling, or CI/CD pipeline.

#### Scenario: Automatic serving of index.html
- **WHEN** GitHub Pages is configured with source set to the `main` branch root
- **THEN** `index.html` is served as the homepage at the root URL

#### Scenario: No build artifacts required
- **WHEN** a commit is pushed to `main`
- **THEN** the updated app is live within minutes with no manual build step

### Requirement: Future updates are deployable via git push
The hosting setup SHALL allow the app to be updated by pushing commits to the `main` branch — no manual upload or re-configuration required.

#### Scenario: Deploying an update
- **WHEN** a change to `index.html` is committed and pushed to `main`
- **THEN** the live site reflects the updated content within a few minutes
