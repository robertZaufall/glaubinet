# glaubinet

Read [shared infrastructure rules](../infrastructure/AGENTS.md) and the
[project infrastructure and architecture note](../infrastructure/glaubinet.md)
before infrastructure work. Those sibling links are for local checkout navigation.

## Ownership and files

This public repository owns the glaubi.net Project Hub directory. Edit `index.html`
for cards, categories, copy and styling; `favicon.svg` for its icon; `robots.txt`
for crawler policy. Linked applications and Cloudflare routing have separate
owners. A directory edit does not deploy or remove an application's route.

The page has inline CSS and JavaScript and no package manager, build system or
application backend. `.github/workflows/static.yml` deploys the repository root
to GitHub Pages on `master` pushes and manual dispatch. Treat added non-hidden
files, including this guide, as publicly served content. Keep credentials, private
operational records and infrastructure evidence outside this checkout.

## Editing and validation

- Preserve existing card markup, category placement and unrelated destinations.
  Update displayed counters when destinations/categories change; count aliases
  according to the current page's convention.
- Check changed URLs and duplicate destinations, and run `git diff --check`.
  For layout changes, inspect desktop and phone rendering. A local preview can
  use `python3 -m http.server 8000 --bind 127.0.0.1` from this directory.
- Keep fonts and the hub favicon under `site-assets/` with relative URLs; the
  domain-root favicon and `/assets/*` belong to the dashboard. Run
  `python3 check_assets.py` before publication. `robots.txt` is a crawler preference, not access control.
- Route changes require fresh DNS, route and deployed Worker inspection. Preserve
  other application mounts and the shared catch-all; its source is not here.

## Publication and recovery

Commit/push only when requested. Inspect the worktree, stage intended paths only,
commit on the requested/current branch, integrate remote changes with pull/rebase
and push without force. Wait for the Pages workflow for the pushed SHA; verify
local/tracking/remote revision agreement and compare changed content at both
`https://robertzaufall.github.io/glaubinet/` and `https://glaubi.net/`.

Recover content with a reviewed revert/new commit and Pages deployment when
authorized. If origin and public responses differ, inspect routing/cache behavior
before changing services. Keep infrastructure observations and verification dates
current in the sibling project note; retain application procedures here.
