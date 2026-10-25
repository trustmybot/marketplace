# TMB plugin marketplace — STABLE

Catalog for the **stable channel** of the [TMB plugin](https://github.com/trustmybot/plugin). It tracks `trustmybot/plugin@main`, where each `vX.Y.Z` release lands after its rc passes the CI release-gate. This is the channel to install unless you want pre-release builds.

| Channel | Catalog | Plugin source | Version |
|---|---|---|---|
| dev | [`trustmybot-dev`](https://github.com/trustmybot/marketplace-dev) | `trustmybot/plugin@dev-build` | `X.Y.Z-dev.<n>.gh<PR>` |
| rc | [`trustmybot-rc`](https://github.com/trustmybot/marketplace-rc) | a `vX.Y.Z-rc.N` tag | `X.Y.Z-rc.N` |
| **stable** (this one) | `trustmybot` | `trustmybot/plugin@main` | `X.Y.Z` |

Every channel installs the plugin as `tmb`, so one `tmb` is enabled per project at a time.

## Install

Pick a scope. TMB keeps its trajectory DB and hooks per project, so install it **into the project**, never at user scope:

| Scope | Written to | Use when |
|---|---|---|
| `project` | `.claude/settings.json` (committed) | The whole team runs TMB on this repo. The default for stable. |
| `local` | `.claude/settings.local.json` (git-ignored) | Only you run it, or teammates are on other channels. |

Run from the project root.

```bash
claude plugin marketplace add trustmybot/marketplace --scope project
claude plugin install tmb@trustmybot --scope project
```

Replace both `--scope project` with `--scope local` for a personal install.

Then fully quit and relaunch Claude Code, and run `/tmb:onboard` in the project.

## Upgrade to the newest release

Claude Code caches a clone of `main`. A new release reaches your install only after a refresh, run from the project root:

```bash
claude plugin marketplace update trustmybot
claude plugin update tmb@trustmybot --scope project
```

Then fully quit and relaunch Claude Code. Release notes are in the plugin's [CHANGELOG](https://github.com/trustmybot/plugin/blob/main/CHANGELOG.md) and on its [releases page](https://github.com/trustmybot/plugin/releases).

## Trying a pre-release

Disable this install first, at the scope it was installed in, then follow the [rc](https://github.com/trustmybot/marketplace-rc) or [dev](https://github.com/trustmybot/marketplace-dev) catalog's README. `disable` keeps the install so `enable` brings it back.

```bash
claude plugin disable tmb@trustmybot --scope project
```

## Source

Plugin code lives at [trustmybot/plugin](https://github.com/trustmybot/plugin). This repo holds only the catalog, `.claude-plugin/marketplace.json`.
