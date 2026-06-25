# The Agent Architect Stack

> **Modular infrastructure for AI agents. *Enhanced* persistent memory, secure runtime, and more — install what you need, when you need it.**
>
> Built-in harness memory is session-bound and opaque; this stack gives you durable, inspectable infrastructure you actually own.
>
> *A **PDuk Brainworks** project. Apache-2.0 - (c) 2026 esoteric1entity.*

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status: Memory live](https://img.shields.io/badge/Memory-v3.6.2%20live-brightgreen.svg)](#project-status)
[![Status: Security released](https://img.shields.io/badge/Security-v0.2.0%20released-brightgreen.svg)](https://pypi.org/project/ai-agent-shield/)
[![Branches: 2 active](https://img.shields.io/badge/Branches-2%20active-lightgrey.svg)](#branches)

**🌐 Live site:** [esoteric1entity.github.io/agent-architect-stack](https://esoteric1entity.github.io/agent-architect-stack/)

---

## What it is

The **Agent Architect Stack** is an open-source umbrella of **independently installable modules** for AI agents. Each module — called a *branch* — is a peer sibling that does one thing well. You install the branches you want; the others stay out of your way.

| Branch | What it does | Status | Repo |
|---|---|---|---|
| **Memory** (Ultimate Memory Stack) | *Enhanced* persistent memory + knowledge graphs + Obsidian vault + prompt compression | ✅ **Released** — v3.6.2 | [esoteric1entity/ultimate-memory-stack](https://github.com/esoteric1entity/ultimate-memory-stack) |
| **Security** (agent-shield) | 8-layer defensive overlay: skill vetting, input sanitization, runtime hooks, network egress, audit logging | ✅ **Released** — v0.2.0 alpha (Layers 1, 2, 3, 4, 6 & 7 shipped); Layers 0 & 5 roadmapped | [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield) — public · [PyPI](https://pypi.org/project/ai-agent-shield/) |

**Pick-and-choose.** You can install just Memory, just Security, or both. They share conventions (config formats, audit log schema) but **no hard runtime dependency** — per the modular-consumer principle.

**Designed to work better together.** When you install both, Memory's audit logs feed Security's anomaly detection. When you install just one, that branch is the whole product.

---

## Why this exists

AI agents are powerful but stateless. They forget between sessions. They run with full tool access and no defensive layer. They drift in projects without structure. The Agent Architect Stack addresses each of those problems with a dedicated, focused module.

We're not building a monolith. We're building a **growing tree of focused modules** that cooperate when installed together and stay out of the way when installed alone.

---

## Who it's for

- **Agent developers** who want their agents to remember, defend, and stay organized across sessions
- **Open-source maintainers** who want clean, composable infrastructure instead of a one-size-fits-all framework
- **Research labs and small teams** who need agent infrastructure they can audit, modify, and ship

If you've ever thought "I wish this agent framework had a real memory layer" or "I wish there was a security layer between my agent and the network," this stack is for you.

---

## Quick start

### Memory branch (the breadwinner)

```bash
# Clone the Memory branch repo
git clone https://github.com/esoteric1entity/ultimate-memory-stack.git

# Install (Linux / macOS / WSL)
cd /path/to/your/workspace            # where the memory stack should live
/path/to/ultimate-memory-stack/setup-memory-stack.sh    # or: --target <dir>

# Verify
/path/to/ultimate-memory-stack/verify.sh

# Windows: setup-memory-stack.ps1 (same options, PowerShell-style: -Minimal, -Addon, -Compliance …; needs Python 3.8+)
```

### Security branch (agent-shield)

```bash
# Install from PyPI
pip install ai-agent-shield

# Verify
python -c "import agent_shield; print(agent_shield.__version__)"
```

Then wire the guards into your harness — see [INSTALL_AGENT.md](https://github.com/esoteric1entity/agent-shield/blob/main/INSTALL_AGENT.md) for consent-gated steps and verification.

**~5 minutes to a working memory layer.** The installer auto-detects whether you're running Claude Code, OpenClaw, or another harness; installs the Skills into the right location; and verifies the install end-to-end.

For modular install options:

```bash
/path/to/ultimate-memory-stack/setup-memory-stack.sh --minimal              # core only
/path/to/ultimate-memory-stack/setup-memory-stack.sh --addon memory-vault   # add a specific addon
/path/to/ultimate-memory-stack/setup-memory-stack.sh --no-templater         # skip Templater auto-enable
```

---

## Branches

### Memory (Ultimate Memory Stack) — ✅ Released

The flagship. Gives AI agents **persistent memory across sessions** — knowledge that survives context resets, gets searchable as a graph, and stays organized in a human-readable vault.

| Component | What it provides | Tier |
|---|---|---|
| Core stack + install engine | The memory vault scaffold, protocol auto-registration, schemas, templates, wizard, and `verify.sh` | A — core |
| `/config-obsidian-vault` | Obsidian-based personal-knowledge-management interface | B — primary |
| `/install-graphiti` | Knowledge graph over your entities + relationships + temporal facts | C — opt-in |
| `/install-graphify` | Code symbol graph (functions, classes, imports) across 31 languages | C — opt-in |
| `/install-llmlingua` | Prompt compression at a quality-preserving threshold | C — opt-in |

- **Repo:** [esoteric1entity/ultimate-memory-stack](https://github.com/esoteric1entity/ultimate-memory-stack)
- **License:** Apache-2.0
- **Status:** v3.6.2 — released · 2026-06-16


### Security (agent-shield) — ✅ Released

An **8-layer defensive overlay** for AI agents. Sits between your agent and the outside world (skills, network, file system, tool calls) and inspects, sanitizes, audits, and blocks as needed.

The 8 layers:

| # | Layer | What it does | Status |
|---|---|---|---|
| 0 | Cron rotation | Automated schedule for hygiene tasks (audit rotation, key rotation) | 🟡 Roadmapped |
| 1 | Skill vetting | 3-tier automated + 5-layer manual escalation for any new Skill/tool | ✅ Shipped in v0.2.0 |
| 2 | Input sanitization | 4-layer sanitization (structural, content, encoding, context) | ✅ Shipped in v0.2.0 |
| 3 | Structured prompts | Anti-prompt-injection via structured output enforcement | ✅ Shipped in v0.2.0 |
| 4 | Runtime hooks | Bash + write guards (Python ports of the original bash hooks) | ✅ Shipped in v0.2.0 |
| 5 | Network egress | Ollama proxy + URL allowlist + rate limiting | 🟡 Roadmapped |
| 6 | Audit logging | Append-only JSONL with SHA-256 chain integrity | ✅ Shipped in v0.2.0 |
| 7 | Configuration | Layer-7 audit config + cross-addon contract | ✅ Shipped in v0.2.0 |

- **Repo:** [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield) — public
- **PyPI:** [ai-agent-shield](https://pypi.org/project/ai-agent-shield/) — `pip install ai-agent-shield`
- **License:** Apache-2.0
- **Status:** v0.2.0 alpha — Layers 1, 2, 3, 4, 6 & 7 shipped; Layers 0 & 5 roadmapped


---

## Project status

**Memory branch v3.6.2 is live.** **Security branch v0.2.0 alpha is released** and available on [PyPI](https://pypi.org/project/ai-agent-shield/).

| Item | Status |
|---|---|
| Memory branch — Ultimate Memory Stack | ✅ Released · v3.6.2 · 2026-06-16 · [GitHub](https://github.com/esoteric1entity/ultimate-memory-stack) · *(Classified: next release in development)* |
| Security branch — agent-shield | ✅ Released · v0.2.0 alpha · 2026-06-24 · [PyPI](https://pypi.org/project/ai-agent-shield/) · [GitHub](https://github.com/esoteric1entity/agent-shield) |
| Security branch — Layers 0 & 5 | 🟡 Roadmapped |
| Umbrella landing page (this) | ✅ Complete |
| Umbrella name + brand | ✅ Locked: PDuk Brainworks / The Agent Architect Stack |

---

## Authoring process

The architecture itself is **original to esoteric1entity** — a sustained personal design effort begun in early 2026, drawing on prior studies, practices, and influences (2025), and first deployed as the maker's own agent stack. The Memory and Security branches are **descendants of that original design, not its source.**

This stack was built using **multiple AI agents across multiple machines, working alongside the human designer** — with cross-agent peer review at each step (the Tribunal Pattern). Every architectural decision is captured in a decision-log entry with full documentation discipline (purpose / rationale / sound reasoning / scope CAN / scope CANNOT).

The same discipline applies to code quality: releases are developed test-first, must pass the full unit, integration, and end-to-end suites, and go through an independent adversarial review pass before shipping — with every claim backed by an append-only, internally maintained test-evidence register.

---

## Key concepts

- The umbrella topology (independent branches, one storefront)
- The modular consumer architecture (install any branch alone)
- The personal-content boundary (what does NOT go in public repos)
- The Tribunal Pattern (cross-deployment peer review)
- **Memory branch** — [`ultimate-memory-stack`](https://github.com/esoteric1entity/ultimate-memory-stack)
- **agent-shield** — [`agent-shield`](https://github.com/esoteric1entity/agent-shield) v0.2.0 on [PyPI](https://pypi.org/project/ai-agent-shield/)

---

## License

[Apache License 2.0](LICENSE). Use, modify, distribute, fork — go forth.

---

## Citing this work

Everything here is free under Apache-2.0 — no strings attached. If the stack helps
you build something, the one thing we ask — **entirely optional, always
appreciated** — is a citation or mention of **esoteric1entity** /
**PDuk Brainworks**: a link back, a line in your credits, or GitHub's
"Cite this repository" button (powered by [`CITATION.cff`](./CITATION.cff)).

---

## Authors

- **esoteric1entity** — architect + design lead

## Acknowledgements

- Special thanks to [@angiexu25](https://github.com/angiexu25) for the early inspiration toward agentic AI.

---

*"Persistent memory shouldn't be an afterthought. It should be a primitive. And it shouldn't be the only primitive."*
