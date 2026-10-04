---
name: ask
description: Ask Wind Stream, your organization's shared memory, about team decisions, prior discussions and session content. Use when the user says "ask Wind Stream" or "check Wind Stream", wants to search or read Wind Stream sessions, or wants to start or continue a Wind Stream conversation.
---

# Ask Wind Stream

Wind Stream holds your organization's conversations, decisions and shared context.
Use the tools of the Wind Stream MCP server to answer the user's request. The tools
are referred to below by their short names; use them from whichever Wind Stream MCP
server is connected.

## Choose the tool by intent

| The user wants to | Use |
|---|---|
| Ask a question or discuss a topic | `conversation` |
| Find something across sessions | `ws_search`, then `ws_fetch` for detail |
| Read a specific session or asset | `ws_fetch` with its reference |
| See recent sessions | `ws_list` with `scope: "recent"` |
| Start a new session | `ws_create`, or `conversation` with no reference |
| Branch from an existing session | `ws_branch` |

## Conversations

1. If an earlier Wind Stream response in this conversation gave a session reference,
   pass it as `reference` to continue that session. A session URL or title also works.
   Omit `reference` to start a new session.
2. Pass the user's words as `message`. Do not rephrase or filter them.
3. If the question is about local files or code, read them and pass the relevant
   content as `context`. Tell the user which files you are sending: what you pass is
   saved to a session their team can see.

If Wind Stream reports that several sessions match, show the options to the user and
let them choose. Then send the original message again with the chosen `reference` and
`metadata: { "resolved_from": "disambiguation" }`. If they want a new session instead,
send `metadata: { "resolved_from": "disambiguation", "create_new": true, "title": "<their topic>" }`
with no `reference`.

A conversation turn is saved on the server even if the call times out. If it times
out, do not send the message again: fetch the session with `ws_fetch` and read the
reply there.

## Search, then read

1. Call `ws_search` with the user's topic.
2. If several results fit, show their titles and let the user pick.
3. Call `ws_fetch` on the chosen reference. Use `mode: "summary"` to get oriented,
   `mode: "recent"` for the latest exchanges, or `mode: "window"` with `from_sequence`
   for a specific slice.

## Present the answer

Give Wind Stream's response as it came back. Do not add an introduction, a summary or
commentary unless the user asks for one. If Wind Stream says it lacks the context,
say so; do not fill the gap from your own knowledge.

Keep the session reference from each response so the next request continues the same
session, and include the session link so the user can open it in Wind Stream.
