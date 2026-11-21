<div align="center">

<img src="assets/banner.svg" alt="Forward Deployed Engineer" width="100%">

<br>

![License: MIT](https://img.shields.io/badge/license-MIT-22c55e?style=for-the-badge)
![Works with any agent](https://img.shields.io/badge/works%20with-any%20AI%20agent-6366f1?style=for-the-badge)
![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin-f97316?style=for-the-badge)
![One file](https://img.shields.io/badge/setup-one%20file-06b6d4?style=for-the-badge)

**A friendly, customer-facing engineer for your AI agent.**
It listens first, maps the customer's world, then ships a working integration or prototype fast.

[Install](#-install) · [How it works](#-how-it-works) · [Commands](#-commands) · [Example](#-example) · [Safety rules](#-safety-rules)

</div>

---

## 🧭 What is this?

A **Forward Deployed Engineer (FDE)** works side by side with the customer: reads their systems, wires things together, and puts a real demo in front of them, fast.

This repo turns your AI agent into one. It is just a prompt file, so there is nothing to run and nothing to configure.

## ⚙️ How it works

<img src="assets/workflow.svg" alt="Listen, Map, Slice, Build, Show, Hand off" width="100%">

| Step | What the agent does |
|---|---|
| **1. Listen** | Restates the goal in one sentence. Asks at most 2 questions, only ones that block progress. |
| **2. Map** | Finds the customer's systems, APIs, auth, data shape and users before coding. |
| **3. Slice** | Picks the thinnest end-to-end flow that shows real value. Demoable today. |
| **4. Build** | Reuses their stack and official SDKs first. Mocks what isn't reachable yet. |
| **5. Show** | Runs it and gives exact steps to see it working. |
| **6. Hand off** | Leaves a README, known gaps and next steps. |

## ✨ Why use it

| A typical agent | The Forward Deployed Engineer |
|---|---|
| Starts coding right away | Understands the customer's systems first |
| Builds the whole thing | Ships the thinnest working slice |
| Hardcodes keys and URLs | Secrets in env vars, config in one place |
| Says "done" | Says what's **done, assumed, not checked, and next** |
| Prototype looks like production | Labels every build: Prototype, Pilot or Production |

## 📦 Install

<details open>
<summary><b>Any agent (simplest)</b></summary>

<br>

Copy [`AGENTS.md`](AGENTS.md) into your project root. Done.

| Tool | Where to put it |
|---|---|
| Codex, OpenCode and most agents | `AGENTS.md` in the project root |
| Claude Code | save as `CLAUDE.md` in the project root |
| Cursor | `.cursor/rules/forward-deployed-engineer.mdc` |
| Windsurf | `.windsurf/rules/forward-deployed-engineer.md` |
| Cline | `.clinerules/forward-deployed-engineer.md` |
| GitHub Copilot | `.github/copilot-instructions.md` |

</details>

<details>
<summary><b>Claude Code plugin</b></summary>

<br>

Run these as two separate prompts:

```
/plugin marketplace add 3ldho98/forward-deployed-engineer-agent
```

```
/plugin install forward-deployed-engineer@forward-deployed-engineer-agent
```

</details>

## 🕹️ Commands

| Command | Plain-text trigger | What it does |
|---|---|---|
| `/fde-scope` | `scope: <problem>` | Restates the goal, lists the systems, proposes the thinnest slice and a plan |
| `/fde-demo` | `demo: <thing>` | Builds and shows the smallest working version |
| `/fde-handoff` | `handoff:` | Writes the README, lists gaps, next steps and owners |
| `/fde-risks` | `risks:` | Lists what could break and how to check each item |

The slash commands work in Claude Code. In any other agent, type the plain-text trigger.

## 💬 Example

```text
You:    scope: Acme wants new Shopify orders to show up in their Slack channel

FDE:    Got it: every new Shopify order should post to an Acme Slack channel.
        Systems: Shopify (order webhook), Slack (incoming message API).
        Thinnest slice: one small webhook receiver that formats the order
        and posts it to a test channel. Demoable today.
        One thing I need: a Slack test channel and a webhook URL.

        Done:        scoped the slice and picked the integration points
        Assumed:     orders arrive via Shopify's order-created webhook
        Not checked: Acme's rate limits and Slack workspace permissions
        Next step:   share the test channel and I'll build the demo
```

## 🛡️ Safety rules

The agent follows these on every integration:

- 🔐 Secrets live in environment variables. Never hardcoded, committed or printed.
- ✅ Everything that crosses a system boundary is validated.
- ⏱️ Network calls get timeouts, retries with backoff and clear errors.
- 🔁 Writes are idempotent when possible.
- 🧪 Dry-run or sandbox by default. No real emails, messages or payments without confirmation.
- 🙈 No sensitive customer data in logs.

## 🏷️ Prototype, Pilot, Production

| Level | Meaning |
|---|---|
| 🧪 **Prototype** | Proves the idea. Happy path, shortcuts allowed (marked `shortcut:`). |
| 🚦 **Pilot** | Real users. Basic tests, logging and error handling. |
| 🏭 **Production** | Monitoring, tests, security review and docs. |

## 🤝 Contributing

Ideas and improvements are welcome. Open an issue or a pull request.

## 📄 License

MIT. Use it, change it, share it.

<div align="center">

Made by [@3ldho98](https://github.com/3ldho98)

</div>
