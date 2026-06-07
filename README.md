# Intent-Driven-Development

An extension of the [Intent-Driven Development template](https://github.com/intent-driven-dev/intent-driven-template/tree/main) for teams that want changes to start from clear intent, move through explicit behaviour and design artifacts, and finish with implementation tasks that preserve the reasoning behind the work.

## What This Extension Adds

- **Quality UI by default** — The `impeccable` skill is mandatory for any change with a UI surface. Every page, component, form, and layout goes through UX review covering visual hierarchy, accessibility, typography, spacing, color, motion, and edge cases before being considered complete.
- **Test-Driven Development enforced** — No production code without a failing test that passes after. The `test-driven-development` skill gates all feature and bugfix work, ensuring changes are verifiable from the start.

## What This Template Uses

- [OpenSpec](https://github.com/Fission-AI/OpenSpec) for setup, proposal, specification, design, ADR, and task artifacts.
- [OpenCode](https://opencode.ai/) as the development environment.
- [Superpowers](https://github.com/obra/superpowers) for guided practices including brainstorming, planning, debugging, TDD, verification, worktrees, and subagent-driven parallel work.
- Custom schemas from [intent-driven-dev/openspec-schemas](https://github.com/intent-driven-dev/openspec-schemas).
- A bundled local copy of the `intent-driven` custom schema for the full `proposal -> specs -> design -> adr -> tasks` lifecycle.
- OpenSpec git discipline so proposals land on `main` before apply, and implementation lands on `main` before archive.

## Workflow

The intent-driven workflow moves through these artifacts in order:

```text
proposal -> specs -> design -> adr -> tasks
```

- `proposal` captures why the change matters.
- `specs` describe observable behaviour with Gherkin-style scenarios (`GIVEN/WHEN/THEN`).
- `design` explains the implementation approach and trade-offs.
- `adr` records durable architectural decisions.
- `tasks` turn the accepted intent, behaviour, design, and decisions into work.

## Skill Gates

Each artifact type has a mandatory skill enforced by `openspec/config.yaml`:

| Artifact | Required Skill |
|----------|---------------|
| `proposal` | `grill-me` — rigorous design interrogation |
| `spec` | `gherkin-authoring` — structured behaviour scenarios |
| `design` | `c4-diagrams` — architecture boundaries and relationships |
| `adr` | `architectural-decision-records` — durable decision records |

Additionally, `AGENTS.md` enforces:
- `test-driven-development` for all implementation work.
- `impeccable` for all UI work.
- `openspec-git-discipline` for proposal/apply/verify/archive workflows.

## Getting Started

### Start A New Project

Clone this repository, open it with OpenCode, and start working from the bundled OpenSpec configuration, commands, skills, and schema.

### Add To An Existing Project

Open your existing project with OpenCode and ask it to install the template:

```text
Read and understand INSTALL_TEMPLATE.md and follow the instructions there.
```

## Schema

This repository includes a bundled local copy of the `intent-driven` schema at `openspec/schemas/intent-driven/`. The upstream schema lives in [intent-driven-dev/openspec-schemas](https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven).

To validate it:

```bash
openspec schema validate intent-driven
```
