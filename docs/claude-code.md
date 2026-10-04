# Wind Stream for Claude Code

## Install

```bash
claude plugin marketplace add windstreamai/windstream-mcp
claude plugin install windstream@windstream
```

The install reports one option not yet set: your Wind Stream token.

## Set your token

Get a token from Wind Stream (**Settings**, then **MCP Token**; see the
[README](../README.md#get-a-token)).

Start Claude Code and run:

```
/plugin configure windstream@windstream
```

Paste the token when asked. Claude Code keeps it in your system's secure storage, not
in a settings file. Restart Claude Code to apply it.

To set it from a script instead, pipe it in so the token never appears in your shell
history:

```bash
printf '{"token":"%s"}' "$WINDSTREAM_TOKEN" | claude plugin configure windstream@windstream --values-stdin
```

## Check that it works

```bash
claude mcp list
```

You should see:

```
plugin:windstream:windstream: https://app.windstream.ai/api/mcp (HTTP) - ✔ Connected
```

Then, in Claude Code:

```
/windstream:ask What has the team been working on?
```

## Update

```bash
claude plugin marketplace update windstream
claude plugin update windstream@windstream
```

Restart Claude Code to apply the update. Your token is kept.

## Uninstall

```bash
claude plugin uninstall windstream@windstream
claude plugin marketplace remove windstream
```

## Using the wind CLI as well?

`wind setup` registers its own Wind Stream MCP server, named `windstream`. With the
plugin installed too, Claude Code has two Wind Stream servers and lists every Wind
Stream tool twice. Nothing breaks, but the duplicate tools take up room in every
conversation.

If you use `wind`, you already have the connection and do not need this plugin.

## Troubleshooting

**`! Needs authentication` in `claude mcp list`.** The token is missing, mistyped or
expired. Generate a new one in Wind Stream and set it again.

**No Wind Stream server in `claude mcp list`.** The token option is not set. The
server loads only once it has a token. Run `/plugin configure windstream@windstream`.

**"MCP access is not enabled for this organization".** Your organization needs MCP
access. Ask your Wind Stream admin.

**A long answer never arrives.** Wind Stream finishes the turn on the server even when
the call times out. Ask your agent to fetch the session, or open the session link in
Wind Stream.
