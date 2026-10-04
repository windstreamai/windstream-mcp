# Wind Stream for Codex

## Install

```bash
codex plugin marketplace add windstreamai/windstream-mcp
codex plugin add windstream@windstream
```

## Set your token

Get a token from Wind Stream (**Settings**, then **MCP Token**; see the
[README](../README.md#get-a-token)).

Codex reads the token from the `WINDSTREAM_TOKEN` environment variable. Set it in the
environment Codex starts from:

```bash
export WINDSTREAM_TOKEN="<your-token>"
```

To keep it across sessions, set it where you keep other secrets for your shell. Do not
commit it.

## Check that it works

```bash
codex mcp list
```

You should see a `windstream` server at `https://app.windstream.ai/api/mcp` with
`WINDSTREAM_TOKEN` as its bearer token variable. Then ask Codex:

```
Ask Wind Stream what the team has been working on.
```

## Update

```bash
codex plugin marketplace upgrade windstream
codex plugin add windstream@windstream
```

## Uninstall

```bash
codex plugin remove windstream@windstream
codex plugin marketplace remove windstream
```

## Using the wind CLI as well?

`wind setup` registers the same server under the same name, with the same token
variable. Codex shows one `windstream` server either way, and `wind` supplies the token
when it launches Codex.

## Troubleshooting

**Wind Stream tools fail with an authorization error.** `WINDSTREAM_TOKEN` is not set
in the environment Codex started from, or the token has expired. Generate a new one in
Wind Stream, set the variable, and start Codex again.

**"MCP access is not enabled for this organization".** Your organization needs MCP
access. Ask your Wind Stream admin.

**A long answer never arrives.** Wind Stream finishes the turn on the server even when
the call times out. Ask Codex to fetch the session, or open the session link in Wind
Stream.
