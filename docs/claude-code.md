# Wind Stream for Claude Code

## Install

```bash
claude plugin marketplace add windstreamai/windstream-mcp
claude plugin install windstream@windstream
```

The install reports one option not yet set: your Wind Stream token.

## Set your token

Get a token from Wind Stream (**Settings**, then **API Tokens**; see the
[README](../README.md#get-a-token)).

Start Claude Code and run:

```
/plugin configure windstream@windstream
```

Paste the token when asked. Claude Code stores it as a secret, separate from your
settings files; on macOS that is the Keychain. Restart Claude Code to apply it.

To set it from a script instead, pass it on standard input as a JSON object. For
example, with the token already in an environment variable your script holds:

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

Uninstalling removes the stored token.

## Using the wind CLI as well?

`wind setup` registers its own Wind Stream MCP server, named `windstream`. The two work
together: with that server in place, Claude Code uses it and does not load the plugin's
copy, so the tools appear once. `claude mcp list` then shows `windstream` and no
`plugin:windstream:windstream` line, and the connection uses the token `wind` manages.
The plugin's token option goes unused.

With `wind`, the plugin adds the two skills. You do not need it for the connection.

## Troubleshooting

**`! Needs authentication` in `claude mcp list`.** The token is missing, mistyped or
expired. Tokens expire after 30 days. Generate a new one in Wind Stream and set it
again.

**No Wind Stream server in `claude mcp list`.** The token option is not set. The
server loads only once it has a token. Run `/plugin configure windstream@windstream`.

**"MCP access is not enabled for this organization".** Your organization needs MCP
access. Ask your Wind Stream admin.

**A long answer never arrives.** Wind Stream finishes the turn on the server even when
the call times out. Ask your agent to fetch the session, or open the session link in
Wind Stream.
