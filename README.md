# .github

Org-level repo for **Mytho-Compendium**. Two purposes:

1. **profile/README.md**: renders as the organization's GitHub homepage.
2. **docs/**: public, manually-synced mirror of the Claude Code / omp shared context docs that live locally one directory above the three product repos (mytho-compendium-app, mytho-compendium-server, mytho-compendium-content). Those local files are not tracked by any repo (loaded via omp's parent-directory **CLAUDE.md** walk-up). This repo exists so the same context is visible to anyone browsing the org on GitHub.

**docs/CLAUDE.md** is deliberately nested inside **docs/**, never at this repo's root. A root-level **CLAUDE.md** would be auto-loaded as live project memory by any omp/Claude Code session working inside this repo, which is not the intent, this copy exists for GitHub display only.

## Syncing

**docs/** is a **read-only mirror**, kept in sync manually:

1. Edit the real files in the local parent folder: **CLAUDE.md** at the root, plus everything under **docs/**.
2. Copy the updated content into this repo's **docs/CLAUDE.md** and matching **docs/** paths and commit. Rewrite **docs/CLAUDE.md**'s internal references as sibling-relative, not prefixed with **docs/**, since the file lives one level deeper here than in the local source.

**CLAUDE.local.md** is intentionally never mirrored, it holds personal local paths and individual working preferences, not project context.
