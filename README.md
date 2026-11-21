# Forward Deployed Engineer Agent

*A friendly customer-facing engineer for your AI agent. Understands the customer's world, then ships working integrations and prototypes fast.*

Drop one file into your project and your AI agent starts working like a Forward Deployed Engineer (FDE).

## What it does
- Listens first, asks only the questions that block progress
- Maps the customer's systems, auth, and data before coding
- Builds the thinnest working slice, demoable the same day
- Reuses the customer's stack and official SDKs before writing custom code
- Follows safe integration rules (secrets, timeouts, retries, dry-run, no sensitive logs)
- Labels work as Prototype / Pilot / Production so nobody is surprised
- Ends every reply with Done / Assumed / Not done / Next step

## Install
Copy [`AGENTS.md`](AGENTS.md) into your project root. Done.

| Tool | Where to put it |
|---|---|
| Codex, OpenCode, most agents | `AGENTS.md` in project root |
| Claude Code | save as `CLAUDE.md` in project root |
| Cursor | `.cursor/rules/forward-deployed-engineer.mdc` |
| Windsurf | `.windsurf/rules/forward-deployed-engineer.md` |
| Cline | `.clinerules/forward-deployed-engineer.md` |
| GitHub Copilot | `.github/copilot-instructions.md` |

## Claude Code plugin
Run these as two separate prompts:

```
/plugin marketplace add 3ldho98/forward-deployed-engineer-agent
```

```
/plugin install forward-deployed-engineer@forward-deployed-engineer-agent
```

Commands: `/fde-scope`, `/fde-demo`, `/fde-handoff`, `/fde-risks`

## Triggers (any agent)
Type these in chat:
- `scope: <problem>`
- `demo: <thing>`
- `handoff:`
- `risks:`

## Example
> `scope: Acme wants new Shopify orders to appear in their internal Slack channel`

The agent restates the goal, lists the systems (Shopify webhooks, Slack API), proposes a one-file webhook receiver as the first slice, and asks for the one thing it needs (a Slack test channel).

## License
MIT
