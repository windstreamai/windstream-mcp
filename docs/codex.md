# Wind Stream for Codex

This guide is for the Codex CLI.

## Install

```bash
codex plugin marketplace add windstreamai/windstream-mcp
codex plugin add windstream@windstream
```

## Set your token

Get a token from Wind Stream (**Settings**, then **API Tokens**; see the
[README](../README.md#get-a-token)).

Codex reads the token from the `WINDSTREAM_TOKEN` environment variable, which must be
set in the shell you start Codex from. To set it for the current shell without the
token landing in your shell history:

```bash
read -rs WINDSTREAM_TOKEN && export WINDSTREAM_TOKEN
```

Paste the token and press Enter; nothing is echoed. Then start Codex from that shell.

To keep it across sessions, put an `export WINDSTREAM_TOKEN=…` line in a file your
shell loads at startup, using an editor. Keep that file out of version control.

## Check that it works

```bash
codex mcp list
```

You should see:

```
Name        Url                                Bearer Token Env Var  Status   Auth
windstream  https://app.windstream.ai/api/mcp  WINDSTREAM_TOKEN      enabled  Bearer token
```

Then start a new Codex session and ask:

```
Ask Wind Stream what the team has been working on.
```

## Update

```bash
codex plugin marketplace upgrade windstream
codex plugin add windstream@windstream
```

Start a new Codex session to use the updated plugin.

## Uninstall

```bash
codex plugin remove windstream@windstream
codex plugin marketplace remove windstream
```

Then remove `WINDSTREAM_TOKEN` from wherever you set it.

## Using the wind CLI as well?

`wind setup` registers the same server under the same name, with the same token
variable, so Codex shows one `windstream` server either way. `wind up` supplies the
token to the Codex session it launches. If you start `codex` yourself, set
`WINDSTREAM_TOKEN` as described above.

## Troubleshooting

**Wind Stream tools fail with an authorization error.** `WINDSTREAM_TOKEN` is not set
in the shell Codex started from, or the token has expired. Tokens expire after 30
days. Generate a new one in Wind Stream, set the variable, and start Codex again.

**"MCP access is not enabled for this organization".** Your organization needs MCP
access. Ask your Wind Stream admin.

**A long answer never arrives.** Wind Stream finishes the turn on the server even when
the call times out. Ask Codex to fetch the session, or open the session link in Wind
Stream.
