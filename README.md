# Decision Guard: skill for coding agents

Decision Guard is an Atlassian Forge app that checks Jira work against decisions your team already recorded in Confluence. Every quote is verified word for word in code, replaced decisions are retracted, and nothing is written to Jira without a human's approval.

This repo holds the open-source skill that lets third-party coding agents (Claude Code, Codex, Cursor and others) use Decision Guard's MCP tools before they write code. The app itself is installed from its Forge install link.

## MCP endpoint

```
https://mcp.atlassian.com/forge/3ed0592a-d90c-462c-94ab-698ebe81d75d
```

Tools: `get-issue-context`, `find-decisions`, `verify-quote`, `get-audit-log`. All are read-only.

Before you connect:

1. Install Decision Guard on your Atlassian site (Jira and Confluence).
2. A site admin turns on external MCP exposure for the app: Atlassian Administration > Apps > Sites > your site > Connected apps > Decision Guard > View app details > turn on "Expose tools to MCP-compatible apps".
3. Your client signs in with OAuth and only sees what your Atlassian account can see.

## Add the skill

**Claude Code**

```bash
claude mcp add --transport http decision-guard https://mcp.atlassian.com/forge/3ed0592a-d90c-462c-94ab-698ebe81d75d
mkdir -p ~/.claude/skills && cp -R skills/decision-guard ~/.claude/skills/
```

Then run `/mcp` in Claude Code, pick `decision-guard`, and approve the sign-in.

**Other agents**

Add the MCP endpoint as a remote (HTTP) MCP server in your client, then copy `skills/decision-guard/SKILL.md` to where your agent reads skills or instructions.

## Privacy

See [PRIVACY.md](PRIVACY.md).

## License

MIT, see [LICENSE](LICENSE).
