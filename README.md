# DealerMarkets plugin marketplace

The DealerMarkets plugins for ChatGPT and Claude. Each plugin lives in its own repo; this repo only lists them.

| Plugin | Repo | For |
| --- | --- | --- |
| `dealermarkets-admin` | [`Dealermarkets/dealermarkets-admin-plugin`](https://github.com/Dealermarkets/dealermarkets-admin-plugin) (`main`) | DealerMarkets App Admins only |

The dealer plugin will be added here when it's released.

## Adding it

- **ChatGPT desktop:** Plugins › Add › Add a marketplace, enter `https://github.com/Dealermarkets/dealermarkets-marketplace` and leave Git ref and Sparse paths empty. No GitHub account is needed. ChatGPT picks up new plugin versions when the app restarts.
- **Claude:** Customize › Plugins › Add › Add marketplace, enter `Dealermarkets/dealermarkets-marketplace`.
- **Claude Code:** `claude plugin marketplace add Dealermarkets/dealermarkets-marketplace`.

## Files

| Path | Read by | Format |
| --- | --- | --- |
| `.agents/plugins/marketplace.json` | ChatGPT (desktop app, Codex) | OpenAI's: each entry needs `policy` and `category`; `"source": "url"` for a plugin at its repo's root |
| `.claude-plugin/marketplace.json` | Claude (claude.ai Add marketplace, Claude Code) | Claude's: `owner` required; `"source": "github"` |

ChatGPT also reads `.claude-plugin/marketplace.json` as a "legacy-compatible" fallback; the `.agents` file is there so it gets its own format. Keep both files listing the same plugins.

## Releasing a plugin version

Bump `version` in the plugin's manifests (`plugin.json` and `.claude-plugin/plugin.json`) and push to the plugin repo's `main`. This repo only changes when a plugin is added, removed or moved. All repos here must stay public: ChatGPT downloads them with git and can't sign in to GitHub.
