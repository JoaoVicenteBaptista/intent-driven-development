# AGENTS.md

- For OpenSpec propose/apply/verify/archive workflows, use the local `openspec-git-discipline` skill to enforce proposal commits before apply and merge-before-archive discipline.
- For any implementation work (features, bug fixes, components, data access), the `test-driven-development` skill MUST be loaded first. No production code without a failing test that passes after.
- For any UI work (pages, components, forms, layouts), the `impeccable` skill MUST be loaded. Run `$impeccable init` once per project to set up PRODUCT.md and DESIGN.md. Skip when the change has no UI surface.
- The `grill-me` skill MUST include design questions (colors, typography, layout preferences) when the proposal involves a UI surface. Read PRODUCT.md and DESIGN.md first if they exist.