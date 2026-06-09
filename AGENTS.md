# AGENTS.md

## OpenSpec Skill Requirements — LOAD FIRST

Before ANY OpenSpec action, load these in order:

| Phase | Required Skills |
|---|---|
| **new** | `openspec-git-discipline` |
| **continue** (any artifact) | `openspec-git-discipline` |
| **propose** | `openspec-git-discipline` + `grill-me` + (`impeccable` if UI surface) |
| **apply** | `openspec-git-discipline` + `test-driven-development` |
| **verify** | `openspec-git-discipline` |
| **archive** | `openspec-git-discipline` |

- `openspec-git-discipline`: commit after each artifact during new/continue; proposal on main before apply; merge to main before archive. **Never create commits, branches, or merges without explicit user approval.**
- `test-driven-development`: no production code without a failing test that passes after. **No exceptions — not even for POCs, scaffolding, or "it's simple."** Run `npx vitest run` before marking any task complete.
- `grill-me`: interview relentlessly BEFORE writing any proposal artifact. One question at a time, every decision branch explored.
- `impeccable`: complement grill-me with design-specific questions. Run `$impeccable init` once per project to set up PRODUCT.md and DESIGN.md.