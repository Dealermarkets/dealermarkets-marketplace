# DealerMarkets plugin marketplace (private)

One marketplace that lists both DealerMarkets plugins, each kept in its own repo:

| Plugin | Repo | For |
| --- | --- | --- |
| `dealermarkets` | [`Dealermarkets/dealermarkets-plugin`](https://github.com/Dealermarkets/dealermarkets-plugin) | Dealers: search and compare products |
| `dealermarkets-admin` | [`Dealermarkets/dealermarkets-admin-plugin`](https://github.com/Dealermarkets/dealermarkets-admin-plugin) | App Admins (Jim, Mike) only |

Status: **test** (2026-11-24). Both entries point at the plugins' `marketplace-test` branches, whose connectors use the staging Worker (`dealermarkets-mcp-staging.dealermarkets.workers.dev`). The aim is to find out whether adding this repo once is enough for new plugin versions to reach the user.

## Files

| Path | Read by | Format |
| --- | --- | --- |
| `.agents/plugins/marketplace.json` | ChatGPT (desktop app, Codex) | OpenAI's: each entry needs `policy` and `category`; `"source": "url"` for a plugin at its repo's root |
| `.claude-plugin/marketplace.json` | Claude (claude.ai Add marketplace, Claude Code) | Claude's: `owner` required; `"source": "github"` |

ChatGPT also reads `.claude-plugin/marketplace.json` as a "legacy-compatible" fallback; the `.agents` file is there so it gets its own format.

## Adding it

- **ChatGPT desktop:** Plugins › Add › Add a marketplace, then enter `https://github.com/Dealermarkets/dealermarkets-marketplace`.
- **Claude:** Customize › Plugins › Add › Add marketplace, enter `Dealermarkets/dealermarkets-marketplace`, connect GitHub and give the Claude GitHub App access to this repo and both plugin repos.
- **Claude Code:** `claude plugin marketplace add Dealermarkets/dealermarkets-marketplace`.

All three repos are private, so whoever adds the marketplace needs read access to all of them.

## Releasing a plugin version

Bump `version` in the plugin's manifests (`plugin.json` and `.claude-plugin/plugin.json`) and push to the branch the entry points at. Moving an entry to another branch or repo is a change to this repo.
