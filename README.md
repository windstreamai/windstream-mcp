# Wind Stream plugin

Wind Stream is your organization's shared memory: the conversations, decisions and
context your team builds up. This plugin connects your coding agent to it, so you can
ask what the team decided, and why, without leaving your work.

It supports **Claude Code** and **Codex** (tested with Claude Code 2.1.289 and Codex
CLI 0.160.0).

## What you get

- **The Wind Stream MCP server**, connected and ready: converse with Wind Stream,
  search and read sessions, start new ones.
- **`ask`**: ask Wind Stream directly. In Claude Code:
  `/windstream:ask What did we decide about the API redesign?` In Codex, say it in
  your own words: "Ask Wind Stream what we decided about the API redesign."
- **`organizational-context`**: your agent offers to check Wind Stream when a question
  turns on a team decision.

## What is sent to Wind Stream

Your questions, and any file content your agent passes along with them, are saved to a
Wind Stream session. Sessions are visible to your team in Wind Stream. Treat a question
to Wind Stream as you would a message in a shared team channel.

## Before you install

- A Wind Stream account in an organization with MCP access enabled. If you see
  "MCP access is not enabled for this organization", ask your Wind Stream admin.
- A Wind Stream token. See [Get a token](#get-a-token).

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
```

Then make your token available to Codex as `WINDSTREAM_TOKEN`; the guide shows how to
do that without leaving it in your shell history.

## Get a token

1. Sign in to Wind Stream at https://app.windstream.ai.
2. Open **Settings**, then **API Tokens**.
3. Choose **Generate Token** and copy the token right away. It is not shown again.

The token is personal and belongs to one organization. Do not share it or commit it.
Tokens expire after 30 days: when your agent reports that Wind Stream needs
authentication, generate a new token and set it again as described in the guide for
your client.

## Using the wind CLI?

`wind setup` already connects Wind Stream to Claude Code and Codex, so you do not need
this plugin for the connection. Installing both is safe: each client keeps a single
Wind Stream server, and the plugin adds its skills. The guide for your client has the
details.

## Support

success@windstream.ai

## License

See [LICENSE.md](LICENSE.md). Use is governed by the
[Wind Stream terms](https://windstream.ai/terms-of-service) and, in addition, by your
organization's own license agreement with Wind Stream.

- Privacy: https://windstream.ai/privacy-policy
- Data processing: https://windstream.ai/data-processing-addendum
