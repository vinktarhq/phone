# Dialify: a phone for your AI agent

[Dialify](https://dialify.io?ref=agent-plugin) lets your agent call a business for you. You say
what you need, it shows you the plan, and it dials only after you say yes. A voice agent makes the
call, opens by saying it is an AI assistant calling for you, and the outcome and transcript come
back into your chat.

This plugin gives Claude Code, Cursor and Codex two things:

- **The Dialify MCP server** (`https://mcp.dialify.io/mcp`). You sign in in the browser. No key
  to paste, and no account needed beforehand.
- **The `phone` skill.** It teaches the agent how to check a number, write the brief, get your yes,
  follow the call and report only what the business confirmed.

Then ask for things like "call the dentist and move my appointment to Tuesday morning" or "ring
the timber yard and ask whether order 4471 ships this week".

## What it will and will not do

- It calls **business lines only**, in their working hours. No private people, no mobiles.
- It **never dials without your yes**. You read the plan first, word for word.
- It **says it is an AI** in its first sentence, every call.
- It agrees to **nothing you did not allow**, and never handles payment details or codes.
- It reports a booking as confirmed **only when the business said it back** in their own words.

## What it costs

Three free calls of up to three minutes. After that, prepaid credits: one credit is one US cent,
and a call in US English is 35 credits a minute. You pay only for time spent talking to a person.
Voicemail, no answer and a busy line cost nothing.

## Install

**Claude Code**

```sh
claude plugin marketplace add vinktarhq/phone
claude plugin install dialify@dialify
```

Claude Code says Dialify needs authentication: run `/mcp`, pick `dialify` and authenticate.

**Claude Desktop and Claude on the web**

Open [claude.ai/customize/connectors](https://claude.ai/customize/connectors), choose Add custom
connector, and enter `https://mcp.dialify.io/mcp`. Choose Connect and sign in.

**Cursor**

Import this repository under Customize → Plugins → From GitHub Repository. Cursor asks you to
sign in the first time it connects.

**Codex**

```sh
codex plugin marketplace add vinktarhq/phone
codex plugin add dialify@dialify
codex mcp login dialify
```

**Any other MCP client**

Add `https://mcp.dialify.io/mcp` as a Streamable HTTP server; it finds the sign-in on its own. Then
ask your agent to call `get_guide`.

## Privacy

Transcripts are kept for 30 days so you can read them, then removed. Dialify does not keep
call audio; the voice provider that carries the call deletes its copy after one day.
[dialify.io/legal/privacy](https://dialify.io/legal/privacy)
