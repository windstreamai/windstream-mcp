# Wind Stream

Ask Wind Stream what your team decided. This plugin connects Claude Code or Codex to
your organization's Wind Stream: its sessions, decisions and shared context.

## Contents

- The Wind Stream MCP server (`https://app.windstream.ai/api/mcp`).
- `ask` — ask Wind Stream, search and read sessions, start or continue a conversation.
- `organizational-context` — lets your agent consult Wind Stream when a question turns
  on a team decision.

## What is sent to Wind Stream

Your questions, and any file content your agent passes along with them, are saved to a
Wind Stream session that your team can see.

## Requirements

A Wind Stream account in an organization with MCP access enabled, and a Wind Stream
token. Claude Code asks for the token as a plugin option and stores it as a secret,
separate from your settings files. Codex reads it from the `WINDSTREAM_TOKEN`
environment variable.

## Install, update, uninstall

See the guides in the repository this plugin is distributed from:
https://github.com/windstreamai/windstream-mcp

## Support and terms

success@windstream.ai. Use is governed by the Wind Stream Terms of Service
(https://windstream.ai/terms-of-service); see [LICENSE.md](LICENSE.md).
