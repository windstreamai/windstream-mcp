# Wind Stream plugin

Wind Stream is your organization's shared memory: the conversations, decisions and
context your team builds up. This plugin connects your coding agent to it, so you can
ask what the team decided, and why, without leaving your work.

It supports **Claude Code** and **Codex**.

## What you get

- **The Wind Stream MCP server**, connected and ready: converse with Wind Stream,
  search and read sessions, start new ones.
- **`ask`**: ask Wind Stream directly. In Claude Code:
  `/windstream:ask What did we decide about the API redesign?`
- **`organizational-context`**: your agent offers to check Wind Stream when a question
  turns on a team decision.

## Before you install

- A Wind Stream account in an organization with MCP access enabled. If you see
  "MCP access is not enabled for this organization", ask your Wind Stream admin.
- A Wind Stream MCP token. See [Get a token](#get-a-token).

## Install

**Claude Code** — full guide: [docs/claude-code.md](docs/claude-code.md)

```bash
claude plugin marketplace add windstreamai/windstream-mcp
claude plugin install windstream@windstream
```

Then start Claude Code, run `/plugin configure windstream@windstream`, and paste your
token.

**Codex** — full guide: [docs/codex.md](docs/codex.md)

```bash
codex plugin marketplace add windstreamai/windstream-mcp
codex plugin add windstream@windstream
export WINDSTREAM_TOKEN="<your-token>"
```

## Get a token

1. Sign in to Wind Stream at https://app.windstream.ai.
2. Open **Settings** and find **MCP Token**.
3. Generate a token and copy it. It is shown once.

The token is yours and belongs to one organization. Do not share it or commit it.
Tokens expire: when your agent reports that Wind Stream needs authentication, generate
a new token and set it again as described in the guide for your client.

## Using the wind CLI?

`wind setup` already connects Wind Stream to Claude Code and Codex. You do not need
this plugin for the connection. See the guide for your client before installing both.

## Support

success@windstream.ai

## License

See [LICENSE.md](LICENSE.md). Use is governed by the
[Wind Stream Terms of Service](https://windstream.ai/terms-of-service). Privacy:
https://windstream.ai/privacy-policy.
