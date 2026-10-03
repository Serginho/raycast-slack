# Provenance

This repository is a vendored copy of the official Raycast Slack extension.

- **Upstream repo:** https://github.com/raycast/extensions
- **Path:** `extensions/slack`
- **Commit:** `3d41d3b66fe707d9be8e7d31cae3d7097a50157a`
- **License:** MIT (see `package.json`)
- **Imported on:** 2026-10-03

## Why vendored

Code is kept here so updates from upstream are pulled in deliberately (not
automatically), reviewed, and committed on our own schedule.

## Security review (at import commit)

Reviewed before import: `package.json` scripts/dependencies, `package-lock.json`
resolved registries, and all TypeScript sources for `eval`/`Function`,
`child_process`, filesystem writes, and outbound network targets.

- No install/build hooks (`preinstall`/`postinstall`) in `package.json`.
- All dependencies resolve to `registry.npmjs.org`; no non-standard registries.
- Dependencies are standard, widely-used packages (`@raycast/api`,
  `@slack/web-api`, `date-fns`, `lodash`, `node-emoji`, `https-proxy-agent`).
- No `eval`, dynamic `Function`, or shell/process execution in source.
- Network calls target only `slack.com` / `*.slack.com` and Raycast's own
  OAuth service; the Slack bearer token is attached only to Slack hosts, even
  across redirects (see `src/shared/client/downloadFile.ts`).
- No obfuscated or base64-encoded code found.

No indicators of malware were found. To pull a future upstream update, re-fetch
`extensions/slack` at the new commit from the upstream repo above, diff it
against this working tree, re-run this same checklist, and commit the result.
