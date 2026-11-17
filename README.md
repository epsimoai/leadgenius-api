# LeadGenius Pro Agent API Skill

A specialized skill for AI agents to interact with the [LeadGenius](https://last.leadgenius.app) Pro B2B platform through its REST API. This skill enables agents to manage clients and leads, trigger enrichment, and automate outreach workflows.

This repository holds the `leadgenius-api` agent skill in [`skills/leadgenius-api/`](skills/leadgenius-api/SKILL.md). It is maintained by Epsimo AI. It was previously published as the `leadgenius-skill` repository; the skill name `leadgenius-api` is unchanged.

## 🚀 Install the agent skill

```bash
npx skills add epsimoai/leadgenius-api
```

The `skills` CLI needs Node.js 22.20 or later. The skill's helper scripts need Python 3 and the `requests` package:

```bash
pip install requests
```

Supported agent tools:

| Agent tool | Command | Project path | Global path (with `-g`) |
| --- | --- | --- | --- |
| Claude Code | `npx skills add epsimoai/leadgenius-api -a claude-code` | `.claude/skills/leadgenius-api/` | `~/.claude/skills/leadgenius-api/` |
| OpenAI Codex CLI | `npx skills add epsimoai/leadgenius-api -a codex` | `.agents/skills/leadgenius-api/` | `~/.agents/skills/leadgenius-api/` |
| Cursor | `npx skills add epsimoai/leadgenius-api -a cursor` | `.agents/skills/leadgenius-api/` | `~/.cursor/skills/leadgenius-api/` |
| Kiro (IDE and CLI) | `npx skills add epsimoai/leadgenius-api -a kiro-cli` | `.kiro/skills/leadgenius-api/` | `~/.kiro/skills/leadgenius-api/` |
| Other tools | `npx skills add epsimoai/leadgenius-api`, then pick the tool | per tool | per tool |

In the Kiro IDE you can also import the skill from GitHub with the URL `https://github.com/epsimoai/leadgenius-api/tree/main/skills/leadgenius-api`. See the [skills CLI agent list](https://github.com/vercel-labs/skills/blob/main/docs/agents.md) for other tools.

### 🔑 Credentials

Create a LeadGenius account at https://last.leadgenius.app. The scripts sign in with your account email and password (`python3 scripts/auth.py --email you@example.com`, run from the skill directory) and save a token in `~/.leadgenius_auth.json`. You can use a LeadGenius API key instead:

| Variable | Status | Where to get it |
| --- | --- | --- |
| `LGP_API_KEY` | Optional (the scripts fall back to the saved sign-in token) | In the [LeadGenius app](https://last.leadgenius.app), open Settings → API, then create or copy your API key (`lgp_` prefix) |
| `LGP_USER_ID` | Required when `LGP_API_KEY` is set | `scripts/auth.py` prints your user ID after sign-in and saves it as `user_id` in `~/.leadgenius_auth.json` |

Keep keys and passwords out of chats, prompts and commits.

### Sample prompt

> List my LeadGenius clients, then create a test lead for the first client using its `client_id` slug and confirm it appears in the lead list.

[LeadGenius homepage](https://last.leadgenius.app)

## 🛠 Features

- **Lead Lifecycle**: List, create, update and delete leads, one at a time or in batches.
- **AI Enrichment**: Trigger settings-driven enrichment, Copyright AI and SDR AI processing on leads.
- **Client Management**: Create and manage client workspaces that scope leads.
- **Imports**: CSV import and a HubSpot → LeadGenius import guide.
- **Integrations**: Configure webhooks, search history and territory analytics.

## 📂 Repository Structure

- `skills/leadgenius-api/SKILL.md`: Core instructions for AI agents.
- `skills/leadgenius-api/references/`: Detailed documentation.
  - `api_reference.md`: Human-readable endpoint documentation.
  - `openapi.json`: Machine-readable specification.
  - `HUBSPOT_TO_LEADGENIUS.md`: HubSpot → LeadGenius import guide.
  - `LEADGENIUS_IMPORT_GUIDELINES.md`: Import pitfalls and lessons learned.
- `skills/leadgenius-api/scripts/`: Helper utilities (`auth.py`, `api_call.py`, `lgp.py`, `import_csv.py`, `test_api.py`).

## ⚖ License

MIT License. See [LICENSE](LICENSE) for details.
