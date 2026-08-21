# Project State Governor

[简体中文](README.zh-CN.md)

[![Install with skills.sh](https://skills.sh/b/ghost011118/project-state-governor)](https://skills.sh/ghost011118/project-state-governor)

**Stop losing project truth between agent sessions.**

Project State Governor is an agent skill for maintaining a small, evidence-backed source of truth across conversations, branches, implementation cycles, reviews, and research. It helps an agent distinguish current state from historical notes, verify completion claims, preserve important negative evidence, and keep project documentation from turning into a pile of stale status files.

## Why it exists

Long-running agentic projects often fail in a quiet way: code, tests, plans, review notes, and chat summaries begin to disagree. A new agent then spends time reconstructing the project—or acts on an obsolete assumption.

Project State Governor gives the agent a durable operating model:

- Git preserves low-level history.
- `AGENTS.md` defines how agents should operate.
- A compact canonical state system records what is true now.
- Conversations are working context, not authoritative memory.
- Evidence outranks confidence.

## What it does

- Reconstructs current project state from requirements, contracts, Git, code, tests, and documentation.
- Classifies missions, workstreams, milestones, tasks, research hypotheses, decisions, constraints, blockers, and lessons.
- Separates session completion from task, milestone, workstream, and mission completion.
- Preserves verified `COMPLETED` and `CANCELLED` workstream transitions until their details can be safely compressed into decision-relevant history.
- Reconciles contradictory documents without treating old AI output as truth.
- Preserves expensive negative evidence so failed directions are not repeated.
- Consolidates stale or duplicate state while keeping Git as the historical archive.
- Coordinates cleanly with engineering and research governance skills.
- Refuses to invent product intent, accept release risk, or persist secrets.

## When to use it

Use Project State Governor when you need to:

- resume a substantial project in a fresh conversation;
- answer “what is actually done, active, blocked, or next?”;
- clean up fragmented plans, TODOs, handoffs, or review summaries;
- reconcile branch-specific progress with canonical project state;
- verify a completion claim before recording it as done;
- preserve a rejected research direction or an important recurring lesson;
- decide whether a conversation produced durable state worth saving.

Do not use it as a replacement for product ownership, implementation, research execution, or release approval.

## Installation

### Codex

macOS/Linux:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Ghost011118/project-state-governor.git \
  ~/.codex/skills/project-state-governor
```

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
git clone https://github.com/Ghost011118/project-state-governor.git `
  "$env:USERPROFILE\.codex\skills\project-state-governor"
```

Start a new Codex task after installation so the skill list is refreshed.

### Claude Code and other Agent Skills-compatible hosts

The portable core is `SKILL.md` plus `references/`. Copy or clone the repository into the skill directory documented by your host. For Claude Code personal skills, the commonly used location is:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Ghost011118/project-state-governor.git \
  ~/.claude/skills/project-state-governor
```

Host discovery paths and supported metadata vary. `agents/openai.yaml` is Codex-specific UI metadata and can be ignored by hosts that do not use it.

## Quick start

Invoke it explicitly when reconstructing or repairing project state:

```text
Use $project-state-governor to inspect this repository, identify the
authoritative current state, and propose the minimum canonical update.
```

Or ask naturally:

```text
Reconcile our project state after the last three branches. Verify what is
actually complete, preserve important failed approaches, and identify the next
evidence-backed task.
```

The skill first recalls and verifies evidence, then applies only a semantic state diff:

```text
RECALL -> PROPOSE -> VERIFY -> APPLY -> CONSOLIDATE
```

## Canonical state layouts

For small and medium projects:

```text
AGENTS.md
PROJECT_STATE.md
```

For larger projects:

```text
AGENTS.md
.project/
  MANIFEST.md
  STATE.md
  DECISIONS.md
  CONSTRAINTS.md
  NEGATIVE_EVIDENCE.md
  areas/
```

The files form one canonical state system. The goal is not maximum documentation; it is the minimum sufficient, high-confidence project knowledge a fresh agent needs.

## Core safety boundaries

Owner and product decisions remain inside applicable law, actual authorization
boundaries, non-waivable security or safety constraints, and objective facts.
The skill verifies that a claimed hard constraint is real and applicable rather
than elevating convention, preference, or speculation into one.

Project State Governor does not autonomously:

- redefine the project mission or success criteria;
- choose among legitimate but undefined business outcomes;
- accept unresolved release, security, legal, operational, or research risk;
- treat code, tests, reviews, or prior AI output as automatically authoritative;
- delete uniquely valuable history when its significance is uncertain;
- persist credentials, tokens, personal data, or other secrets.

## Repository contents

```text
SKILL.md                         Main skill instructions
agents/openai.yaml              Codex UI metadata
assets/icon.svg                 Skill icon
references/project-state-schema.md
references/persistence-lifecycle.md
references/reconstruction-workflow.md
references/manifest-routing.md
```

## Compatibility and validation

- The package follows the `SKILL.md`-based Codex skill structure.
- The core instructions have no runtime dependency or external service requirement.
- The skill is primarily written in English so it remains portable across agent hosts; the full user documentation is provided in English and Chinese.
- Host-specific discovery and UI metadata may differ. Please open an issue with reproducible evidence for compatibility gaps.

## Contributing

Evidence-backed improvements are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Security reports should follow [SECURITY.md](SECURITY.md).

## Directory listing kit

Maintainers and directory curators can reuse the concise descriptions, tags, and compatibility notes in [docs/DIRECTORY-LISTING.md](docs/DIRECTORY-LISTING.md).

## License

Licensed under the [Apache License 2.0](LICENSE).
