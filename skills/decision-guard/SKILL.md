---
name: decision-guard
description: Before implementing or changing code for a Jira issue, check it against the team's recorded decisions using the Decision Guard tools on the Atlassian MCP server. Use whenever the user asks you to work on a Jira issue key (for example PAY-150).
---

# Decision Guard

Your team records decisions (ADRs) in Confluence. The Decision Guard tools let you check a Jira issue against them before you write code.

## Setup

Add the Decision Guard MCP server to your client. The URL is `https://mcp.atlassian.com/forge/3ed0592a-d90c-462c-94ab-698ebe81d75d`. The Decision Guard app must be installed on your Atlassian site, and your site admin must first turn on external MCP exposure for it.

## When to run

Run it before you start any task that names a Jira issue key, and before large changes to storage, dependencies, security, or data handling.

## Steps

1. Call `find-decisions` with the issue key.
2. For each match that touches what you are about to do, copy the exact sentence that matters and call `verify-quote` with `decisionId`, `quote` and `issueKey`.
3. If `verified` is true and `inForce` is true, and the planned change goes against the sentence: **stop**. Show the user the decision id, the quote, and the link, and ask whether to continue.
4. If `supersededBy` is set, check the newer decision instead.
5. If `verified` is false, do not repeat the quote as fact.

## Rules

- Never paraphrase a decision as if it were a quote. Only quote what `verify-quote` confirmed.
- These tools are read-only. To flag a conflict on the Jira issue, ask the user to use the Decision Guard agent in Rovo. A human approves every write.
