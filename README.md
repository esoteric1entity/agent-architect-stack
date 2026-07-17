# The Agent Architect Stack

> **Modular Infrastructure for AI Agents**
>
> A memory vault that grows into a knowledge graph, your agent's *second brain*, and a security runtime — with more to come. Install what you need, when you need it.
>
> **Own the memory. Own the guardrails. Own the *edge*.**
>
> Choose your harness. Built for Claude Code & OpenClaw variants today!
>
> *A **PDuk Brainworks** project. Apache-2.0 - (c) 2026 esoteric1entity.*

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status: Memory live](https://img.shields.io/badge/Memory-v4.0.0%20live-brightgreen.svg)](#project-status)
[![Status: Security released](https://img.shields.io/badge/Security-v0.2.1%20released-brightgreen.svg)](https://pypi.org/project/ai-agent-shield/)
[![Branches: 2 active](https://img.shields.io/badge/Branches-2%20active-lightgrey.svg)](#branches)

**🌐 Live site:** [esoteric1entity.github.io/agent-architect-stack](https://esoteric1entity.github.io/agent-architect-stack/)
**Explore:** [Mission](https://esoteric1entity.github.io/agent-architect-stack/mission.html) · [Ecosystem](https://esoteric1entity.github.io/agent-architect-stack/ecosystem.html) (curated, vetted tools directory) · [Contributors](https://esoteric1entity.github.io/agent-architect-stack/contributors.html)

---

## What it is

The **Agent Architect Stack** is an open-source umbrella of **independently installable modules** for AI agents. Each module — called a *branch* — is a peer sibling that does one thing well. You install the branches you want; the others stay out of your way.

| Branch | What it does | Status | Repo |
|---|---|---|---|
| **Memory** (Ultimate Memory Stack) | *Enhanced* persistent memory + knowledge graphs + Obsidian vault + prompt compression | ✅ **Released** — v4.0.0 | [esoteric1entity/ultimate-memory-stack](https://github.com/esoteric1entity/ultimate-memory-stack) |
| **Security** (agent-shield) | 8-layer defensive overlay: skill vetting, input sanitization, runtime hooks, network egress, audit logging | ✅ **Released** — v0.2.1 alpha (Layers 1, 2, 3, 4, 6 & 7 shipped); Layers 0 & 5 roadmapped | [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield) — public · [PyPI](https://pypi.org/project/ai-agent-shield/) |

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

Two branches, two install paths. Pick the branch you want; each is independent.

### Memory branch — four ways in

**Door 1 — Script (Linux / macOS / WSL · Windows)**

```bash
git clone https://github.com/esoteric1entity/ultimate-memory-stack.git

cd /path/to/your/workspace            # where the memory stack should live
/path/to/ultimate-memory-stack/setup-memory-stack.sh    # or: --target <dir>
/path/to/ultimate-memory-stack/verify.sh

# Flags: --minimal · --addon <name> · --no-templater · --compliance=<preset> · --yes
# Windows: setup-memory-stack.ps1 (same options, PowerShell-style: -Minimal, -Addon, -Compliance …; needs Python 3.8+)
```

**Door 2 — Tell your agent (any harness)**

```bash
git clone https://github.com/esoteric1entity/ultimate-memory-stack.git

# Then tell your agent — Claude Code, OpenClaw, or any capable harness:
#   "Install this — read INSTALL_AGENT.md and follow it."
```

**Door 3 — Claude Code marketplace**

> Run these inside Claude Code, not your shell — Claude Code must be installed & authenticated.

```bash
# 1. In Claude Code — add the marketplace + install the plugin
/plugin marketplace add esoteric1entity/ultimate-memory-stack
/plugin install ultimate-memory-stack@ultimate-memory-stack

# 2. Exit Claude Code (/exit or Ctrl-D)
# 3. In your shell: cd to the project where the memory should live
# 4. Relaunch Claude Code from inside that directory, then run:
/install-ultimate-memory-stack
```

> Note: existing `memory/` store in that project? Back it up first — or use the script/agent door, which preserves it automatically.

**Door 4 — no tooling at all**

Drag the `common-specs/` and `general-edition/` folders into your workspace, then paste [The Prompt](https://github.com/esoteric1entity/ultimate-memory-stack/blob/main/common-specs/BOOTSTRAP_PROMPT.md#the-activation-prompt) into your agent — it runs the setup wizard. Full manual steps: the [Install Guide](https://github.com/esoteric1entity/ultimate-memory-stack/blob/main/INSTALL.md).

Whatever the door, the installer refuses to mix your memory into the package tree and records exactly what it did in a manifest.

**~5 minutes to a working memory layer.** The installer auto-detects whether you're running Claude Code, OpenClaw, or another harness; installs the Skills into the right location; and verifies the install end-to-end.

### Security branch (agent-shield)

```bash
# Install from PyPI
pip install ai-agent-shield

# Verify
python -c "import agent_shield; print(agent_shield.__version__)"
```

Then wire the guards into your harness — see [INSTALL_AGENT.md](https://github.com/esoteric1entity/agent-shield/blob/main/INSTALL_AGENT.md) for consent-gated steps and verification.

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
- **Status:** v4.0.0 — released · 2026-07-16


### Security (agent-shield) — ✅ Released

An **8-layer defensive overlay** for AI agents. Sits between your agent and the outside world (skills, network, file system, tool calls) and inspects, sanitizes, audits, and blocks as needed.

The 8 layers:

| # | Layer | What it does | Status |
|---|---|---|---|
| 0 | Cron rotation | Automated schedule for hygiene tasks (audit rotation, key rotation) | 🟡 Roadmapped |
| 1 | Skill vetting | 3-tier automated + 5-layer manual escalation for any new Skill/tool | ✅ Shipped |
| 2 | Input sanitization | 4-layer sanitization (structural, content, encoding, context) | ✅ Shipped |
| 3 | Structured prompts | Anti-prompt-injection via structured output enforcement | ✅ Shipped |
| 4 | Runtime hooks | Bash + write guards (Python ports of the original bash hooks) | ✅ Shipped |
| 5 | Network egress | Ollama proxy + URL allowlist + rate limiting | 🟡 Roadmapped |
| 6 | Audit logging | Append-only JSONL with SHA-256 chain integrity | ✅ Shipped |
| 7 | Configuration | Layer-7 audit config + cross-addon contract | ✅ Shipped |

- **Repo:** [esoteric1entity/agent-shield](https://github.com/esoteric1entity/agent-shield) — public
- **PyPI:** [ai-agent-shield](https://pypi.org/project/ai-agent-shield/) — `pip install ai-agent-shield`
- **License:** Apache-2.0
- **Status:** v0.2.1 alpha — Layers 1, 2, 3, 4, 6 & 7 shipped; Layers 0 & 5 roadmapped


---

## Project status

**Memory branch v4.0.0 is live.** **Security branch v0.2.1 alpha is released** and available on [PyPI](https://pypi.org/project/ai-agent-shield/).

| Item | Status |
|---|---|
| Memory branch — Ultimate Memory Stack | ✅ Released · v4.0.0 · 2026-07-16 · [GitHub](https://github.com/esoteric1entity/ultimate-memory-stack) |
| Security branch — agent-shield | ✅ Released · v0.2.1 alpha · 2026-07-05 · [PyPI](https://pypi.org/project/ai-agent-shield/) · [GitHub](https://github.com/esoteric1entity/agent-shield) |
| Security branch — Layers 0 & 5 | 🟡 Roadmapped |
| Future branches | 🟡 In ideation & design |
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
- **agent-shield** — [`agent-shield`](https://github.com/esoteric1entity/agent-shield) v0.2.1 on [PyPI](https://pypi.org/project/ai-agent-shield/)
- **Ecosystem directory** — curated, vetted tools & resources across the AI-agent space; see the [Ecosystem page](https://esoteric1entity.github.io/agent-architect-stack/ecosystem.html)

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
