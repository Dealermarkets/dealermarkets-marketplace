# DealerMarkets plugin marketplace

One marketplace that lists both DealerMarkets plugins, each kept in its own repo:

| Plugin | Repo | For |
| --- | --- | --- |
| `dealermarkets` | [`Dealermarkets/dealermarkets-plugin`](https://github.com/Dealermarkets/dealermarkets-plugin) | Dealers: search and compare products |
| `dealermarkets-admin` | [`Dealermarkets/dealermarkets-admin-plugin`](https://github.com/Dealermarkets/dealermarkets-admin-plugin) | DealerMarkets App Admins only |

Status: **test**. Both entries point at the plugins' `marketplace-test` branches, whose connectors use the staging server.

## Files

| Path | Read by | Format |
| --- | --- | --- |
| `.agents/plugins/marketplace.json` | ChatGPT (desktop app, Codex) | OpenAI's: each entry needs `policy` and `category`; `"source": "url"` for a plugin at its repo's root |
| `.claude-plugin/marketplace.json` | Claude (claude.ai Add marketplace, Claude Code) | Claude's: `owner` required; `"source": "github"` |

ChatGPT also reads `.claude-plugin/marketplace.json` as a "legacy-compatible" fallback; the `.agents` file is there so it gets its own format.

## Adding it

- **ChatGPT desktop:** Plugins › Add › Add a marketplace, then enter `https://github.com/Dealermarkets/dealermarkets-marketplace`.
- **Claude:** Customize › Plugins › Add › Add marketplace, enter `Dealermarkets/dealermarkets-marketplace`, connect GitHub if asked.
- **Claude Code:** `claude plugin marketplace add Dealermarkets/dealermarkets-marketplace`.

The dealer plugin repo is still private, so only people with access to it can install that plugin.

## Releasing a plugin version

Bump `version` in the plugin's manifests (`plugin.json` and `.claude-plugin/plugin.json`) and push to the branch the entry points at. Moving an entry to another branch or repo is a change to this repo.
