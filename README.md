# The Agent Architect Stack

> **Modular Infrastructure for AI Agents**
>
> A memory vault, your agent's *second brain*, and a security runtime, with more to come. Install what you need, when you need it.
>
> **Own the memory. Own the guardrails. Own the *edge*.**
>
>
> Tested with Claude Code and OpenClaw. More harnesses planned.
>
> *A **PDuk Brainworks** project. (c) 2026 esoteric1entity.*

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status: Memory released](https://img.shields.io/badge/Memory-v4.0.1%20released-brightgreen.svg)](#project-status)
[![Status: Security released](https://img.shields.io/badge/Security-v0.2.1%20released-brightgreen.svg)](https://pypi.org/project/ai-agent-shield/)


**Live site:** [esoteric1entity.github.io/agent-architect-stack](https://esoteric1entity.github.io/agent-architect-stack/)

**Explore:** [Get Started](https://esoteric1entity.github.io/agent-architect-stack/get-started.html) · [How It Works](https://esoteric1entity.github.io/agent-architect-stack/how-it-works.html) · [Memory](https://esoteric1entity.github.io/agent-architect-stack/memory.html) · [Security](https://esoteric1entity.github.io/agent-architect-stack/security.html) · [Mission](https://esoteric1entity.github.io/agent-architect-stack/mission.html) · [Ecosystem](https://esoteric1entity.github.io/agent-architect-stack/ecosystem.html) (curated tools directory) · [Contributors](https://esoteric1entity.github.io/agent-architect-stack/contributors.html)

---

## What It Is

The **Agent Architect Stack** is an open-source umbrella of **independently installable modules** for AI agents. Each module is a standalone tool that does one thing well. You install the tools you want; the others stay out of your way.

| Tool | What It Does | Repo |
|---|---|---|
| **Memory** (Ultimate Memory Stack) | *Enhanced* persistent memory + Obsidian vault | [esoteric1entity/ultimate-memory-stack](https://github.com/esoteric1entity/ultimate-memory-stack) |
| **Security** (agent-shield) | Defensive overlay: skill vetting, input sanitization, runtime hooks, network egress (designed but not built), audit logging | [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield) · [PyPI](https://pypi.org/project/ai-agent-shield/) |

---

## Why This Exists

AI agents are powerful but stateless. They forget between sessions. They run with full tool access and no defensive layer. They drift in projects without structure. Memory and Security address the first two; more tools are planned.

We're not building a monolith. We're building a **growing tree of focused modules**.

---

## Who It's For

- **Agent developers** who want their agents to remember and defend across sessions
- **Open-source maintainers** who want clean, composable infrastructure instead of a one-size-fits-all framework
- **Research labs and small teams** who need agent infrastructure they can audit, modify, and ship

If you've ever thought "I wish this agent framework had a real memory layer," this stack is for you.

---

## Quick Start

### Security Tool (agent-shield)


Checks shell commands, and where file writes and edits go, before they run, once wired as a hook. In Claude Code, the PowerShell tool, file reads, web fetches, notebook edits and other tools are not checked. On Windows (not WSL), Claude Code often runs commands with that tool, and always does without Git Bash. It is a filter, not a sandbox. It does not stop prompt injection. [All known limits](https://esoteric1entity.github.io/agent-architect-stack/security.html#limits)

```bash
pip install ai-agent-shield==0.2.1
```


On macOS and Linux, install agent-shield in a virtual environment outside your project folder, and start Claude Code each time from a terminal where that environment is active. On any system, skip `pipx` and `uv tool` for now, and tell your assistant the same: the hooks can't find an install made that way.

Then point your assistant at [INSTALL_AGENT.md](https://github.com/esoteric1entity/agent-shield/blob/v0.2.1/INSTALL_AGENT.md) in the repo on GitHub, since the PyPI install does not include that file. It wires the guards into Claude Code. After that, commands that match its list of dangerous patterns are blocked, those that match its list of risky ones are put to you, and everything else is left to your assistant's own permission settings.

The guide's step 2 installs from GitHub main. You already have 0.2.1 from PyPI, so tell your assistant to skip that step.

**Install check**

```bash
echo '{"tool_input":{"file_path":"~/.claude/settings.json"}}' | python -m agent_shield.write_guard
```

What it prints: a deny. Your settings file is not touched. This tests the file-edit guard only. [See all known limits](https://esoteric1entity.github.io/agent-architect-stack/security.html#limits).

```
{"hookSpecificOutput": {"hookEventName": "PreToolUse", "permissionDecision": "deny", "permissionDecisionReason": "Cannot modify Claude settings.json (contains hook/permission configs)"}}
```

Then run `agent-shield-plugin status`. If the hooks were wired with `agent-shield-plugin enable`, it should say enabled. For project scope, run `agent-shield-plugin --project <dir> status`. Status does not show that the hooks fire.

Run both checks in the terminal you start Claude Code from (bash, zsh, Git Bash or PowerShell; in cmd.exe the first one prints nothing). If the first one fails there, the hooks will likely fail too, and Claude Code may then let actions through unchecked.

For OpenClaw the guide uses the library for now; agent-shield's [README](https://github.com/esoteric1entity/agent-shield/blob/v0.2.1/README.md) shows how to wire its `before_tool_call` adapter yourself, which needs a recent gateway.

---

## Tools



### Memory (Ultimate Memory Stack) · Released

The flagship. Gives AI agents **persistent memory across sessions**: knowledge that survives context resets and stays organized in a human-readable vault.

| Component | What It Provides | Tier |
|---|---|---|
| Core stack + install engine | The memory vault scaffold, protocol auto-registration, schemas, templates, wizard, and `verify.sh` | A (core) |
| `/config-obsidian-vault` | Obsidian-based personal-knowledge-management interface | B (primary) |
| `/install-graphiti` | Knowledge graph over your entities + relationships + temporal facts | C (opt-in) |
| `/install-graphify` | Code symbol graph (functions, classes, imports) | C (opt-in) |

Optional add-ons set up third-party tools, and some have known problems in the current release.


- **Repo:** [esoteric1entity/ultimate-memory-stack](https://github.com/esoteric1entity/ultimate-memory-stack)
- **License:** Apache-2.0

### Security (agent-shield) · Released


agent-shield checks what your AI agent is about to run, and where it is about to write. It blocks actions that match its list of dangerous patterns, lets you decide on those that match its list of risky ones, and lets everything else through. Wired as a hook, it keeps a record of what it decided.

The 8 layers:

| # | Layer | What It Does | Status |
|---|---|---|---|
| 0 | Cron rotation | Automated schedule for hygiene tasks (audit rotation, key rotation) | Designed but not built |
| 1 | Skill vetting | 3-tier automated + 5-layer manual escalation that you run on a new skill or tool | Shipped |
| 2 | Input sanitization | 4-layer sanitization (structural, content, encoding, context) | Shipped |
| 3 | Structured output | Structured output enforcement | Shipped |
| 4 | Runtime hooks | Bash + write guards | Shipped |
| 5 | Network egress | Ollama proxy + URL allowlist + rate limiting | Designed but not built |
| 6 | Audit logging | A log that can be checked for edited lines | Shipped |
| 7 | Configuration | Layer-7 audit config + cross-layer contract | Shipped |

- **Repo:** [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield)
- **PyPI:** [ai-agent-shield](https://pypi.org/project/ai-agent-shield/)
- **License:** Apache-2.0

*More tools planned.*

---

## Harnesses and Systems

**Security (agent-shield)**

- Harnesses: Claude Code (PreToolUse hooks) and OpenClaw (a before_tool_call plugin; needs a recent gateway). More are planned, starting with Hermes Agent and OpenCode.
- Operating systems: Windows, Linux (including WSL) and macOS, with Python 3.11 or later; its test suite runs on all three in CI. On Windows, commands Claude Code runs through its PowerShell tool are not checked.



## Project Status

| Item | Status |
|---|---|
| Memory Tool (Ultimate Memory Stack) | Released · v4.0.1 · 2026-08-19 · [GitHub](https://github.com/esoteric1entity/ultimate-memory-stack) |
| Security Tool (agent-shield) | Released · v0.2.1 alpha · 2026-07-05 · [PyPI](https://pypi.org/project/ai-agent-shield/) · [GitHub](https://github.com/esoteric1entity/agent-shield) |
| Future Tools | In Ideation & Design |

---

## Authoring Process

The architecture itself is **original to esoteric1entity**: a sustained personal design effort begun in early 2026, drawing on prior studies, practices, and influences (2025), and first deployed as the maker's own agent stack. The Memory and Security tools are **descendants of that original design, not its source.**

This stack was built using **multiple AI agents across multiple machines, working alongside the human designer**, with cross-agent peer review at each step (the Tribunal Pattern).

Recent releases went through an adversarial review before shipping.

---

## Key Concepts

- The umbrella topology (independent tools, one storefront)
- The modular consumer architecture (install any tool alone)
- The personal-content boundary (what does NOT go in public repos)
- The Tribunal Pattern (cross-agent peer review)

---

## License

[Apache License 2.0](LICENSE). Use, modify, distribute, fork. Go forth.

---

## Citing This Work

Everything here is open source under Apache-2.0, no strings attached. If the stack helps
you build something, a citation or mention of **PDuk Brainworks** /
esoteric1entity is always appreciated:
a link back, a line in your credits, or GitHub's
"Cite this repository" button (powered by [`CITATION.cff`](./CITATION.cff)).

---

## Authors

- **esoteric1entity**, architect + design lead

## Acknowledgements

- Special thanks to [@angiexu25](https://github.com/angiexu25) for the early inspiration toward agentic AI.

---

*"Persistent memory shouldn't be an afterthought. It should be a primitive. And it shouldn't be the only primitive."*
