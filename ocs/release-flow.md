Adds `docs/release-flow.md` documenting the release path from `npm run release` (`scripts/release.mjs`) through `.github/workflows/release.yml` to published npm packages, GitHub Release creation, and container image builds.

### Summary
- Traces local lockstep versioning, `package-lock.json` refresh, commit/tag creation, and tag-triggered CI checks.
- Documents three concrete failure points across the local script, npm publish loop, and container image job, including expected log messages and resulting state.

### Verification & Limits
- Inspected `package.json`, `scripts/release.mjs`, `.github/workflows/release.yml`, and `RELEASE.md`.
- Did not execute `npm run release` or publish against live npm / GHCR; failure symptoms and recovery behavior are derived from the script and workflow definitions.
- Used AI assistance to organize the documentation; reviewed and verified every pipeline step against the repository files.
