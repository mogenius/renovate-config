# mogenius Renovate Config

Shared [Renovate](https://docs.renovatebot.com/) base configuration for mogenius repositories.

## Usage

Add the following to your repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>mogenius/renovate-config//presets/gitops.json#main"
  ],
  "reviewers": [
    "@your-reviewer"
  ]
}
```

### Automerge patch updates

Repositories that are not using the gitops preset can opt into automerging patch updates:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>mogenius/renovate-config//presets/automerge-patch.json#main"
  ]
}
```

## What's included

- **Recommended base config** with vulnerability alerts and dependency dashboard
- **Separate PRs** for major, minor, and patch updates
- **Semantic commits** with `build` type and sign-off
- **Labels** on PRs: `renovate`, `manager:<name>`, `updateType:<type>`
- **Lock file maintenance** enabled
- **npm majors** of third-party packages need approval via the Dependency Dashboard (patch/minor create PRs directly)
- **TypeScript** held below 7 until the tooling supports TS 7's new compiler API
- **GitHub Actions** pinned to digest (no auto-digest bumps)
- **ArgoCD** manifest support for `.yaml` files
- **Go version** range strategy set to `bump`
- **Custom regex managers** for:
  - Inline `# renovate: datasource=...` annotations in any file
  - `_VERSION` ARG/ENV variables in Dockerfiles
  - Docker image references in YAML manifests (with digest support)
  - `version_manifest.txt` files
- Timezone: `Europe/Berlin`
