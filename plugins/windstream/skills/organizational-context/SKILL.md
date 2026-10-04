---
name: organizational-context
description: Consult Wind Stream when a question turns on team knowledge that is not in the codebase. Use when the user asks what the team decided, why something was chosen, what was discussed before, who worked on something, or what the team's convention or position is.
---

# Organizational context from Wind Stream

Wind Stream holds your organization's conversations, decisions and shared context.
When the answer to a question lives in what the team has said, not in the code, ask
Wind Stream with the `conversation` tool of the connected Wind Stream MCP server.

## When to consult Wind Stream

Consult it for:

- **Decisions**: "What did we decide about auth?", "What is our approach to caching?"
- **Prior discussion**: "What came out of the architecture review?"
- **Rationale and history**: "Why did we choose this framework?", "Who worked on billing?"
- **Conventions**: "What is our convention for error handling?"

Do not consult it for:

- Questions the codebase answers. Read the code.
- General programming knowledge.
- Questions about external libraries or APIs. Use their documentation.

## How to ask

Call `conversation` with:

- `message`: the user's question. Rephrase only when it leans on something said earlier
  in this conversation that Wind Stream cannot see, such as a pronoun.
- `reference`: the session reference from an earlier Wind Stream response, to continue
  that session. Omit it to start a new one.
- `context`: the relevant file content, when the question is about specific code. For
  "does this match what we agreed?", read the file and pass it.

If Wind Stream reports that several sessions match, show the options to the user, let
them choose, and send the message again with the chosen `reference` and
`metadata: { "resolved_from": "disambiguation" }`.

## Presenting the answer

- Give the response as it came back. Add commentary only if the user asks.
- Keep the session reference for follow-up questions, and include the session link so
  the user can continue in Wind Stream.
- If Wind Stream lacks the context, say so. Do not invent an answer.

## Offering it unprompted

While working on code, offer to check Wind Stream when a team decision could change
the approach: the user is building something the team may have already discussed, is
puzzled by why the code is the way it is, or faces several valid approaches where a
convention might settle it. Ask first; for example: "This touches the auth system.
Want me to check Wind Stream for team decisions about it?"
