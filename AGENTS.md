# security-research — Agent Rules

## Purpose
Container boundary vulnerability research and root cause analysis (RCA). Q2 sustaining track: weekly container research, three staged RCAs (CVE-2024-0132, CVE-2025-23359, CVE-2025-23266). Repository is the public research hub; archive prep after migration to azraelsec.dev is documentation-only.

## Agent Personas
- **T1 strategic** (Open WebUI) — research planning, methodology
- **T5 code** (OpenCode) — exploit PoC development, analysis tooling
- **T6 research** (Perplexity) — CVE/PoC lookup

## Tooling
- Local lab: Podman rootless on Cerberus/NightForge
- Analysis: docker-explorer, gVisor, nsenter
- Language focus: C, Go (kernel/container primitives)

## Context Management
- Whitepaper 1 shipped (2026-04-12)
- Whitepaper 2 deferred to Q3
- All findings documented in azrael-vault

## Critical Constraints
- No production infrastructure testing — lab environment only
- No unauthorized target scanning
- All PoCs must include detection guidance
- Kernel exploits require full RCA (root cause, not just PoC)
- No pushes without explicit user approval — commit locally only
- No content moves/deletes outside tracked migration work

## Research Methodology
1. CVE selection via Perplexity query (latest public PoCs, exploitation primitives)
2. Lab environment replication (minimal container setup)
3. Root cause analysis (code audit, patch diff)
4. Detection guidance (nuclei template, Suricata rule)
5. Documentation (azrael-vault, potential whitepaper)

## Repository Commands

```bash
# Status / history
git status --short          # current state before any work
git log --oneline -20       # recent history

# Working loop (micro-commits, conventional style)
git add <file>              # stage one logical change
git commit -m "docs: add SECURITY.md — engagement boundary and redaction policy"

# Diff review (hunk)
git difftool                # review staged/unstaged changes in hunk
hunk session review --repo . --json   # programmatic review snapshot
```

## Documentation Conventions (AI agents)

- **One logical change per commit.** Conventional prefixes: `docs:`, `research:`, `technique:`, `chore:`.
- **Frontmatter** on research docs: `created`, `updated`, `tags`, `status` (see `ARCHITECTURE.md`).
- **Evidence-first:** every claim tied to tool output, source reference, or measured result; negative results documented like positive ones.
- **Version pinning:** OS, kernel, runtime (Podman/Docker/runc/crun), toolkit versions in every finding.
- **Redaction before commit** per `SECURITY.md`: flags → `████`, usernames → uid, no IPs/credentials/PII. Review screenshots.
- **Format:** follow the whitepaper template (`research/`) or re-1/re-2 template (`techniques/`). Relative links only.
- **Inventory + migration:** update `docs/CONTENT-INVENTORY.md` when content is added; check `docs/MIGRATION.md` before archive-related work.
- **Verification:** smoke-test the change, run `git difftool` (hunk) review, then commit. Never claim completion without evidence.

## Archive / Migration Notes

- Target: azraelsec.dev (see `docs/MIGRATION.md`).
- Archive-prep sessions are documentation-only: no content moves, no deletions.
- Guardrails from `SECURITY.md` apply to migrated content as well.

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:46cd31e7 -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/core-concepts/sync-concepts.md for details and anti-patterns.

## Agent Context Profiles

The managed Beads block is task-tracking guidance, not permission to override repository, user, or orchestrator instructions.

- **Conservative (default)**: Use `bd` for task tracking. Do not run git commits, git pushes, or Dolt remote sync unless explicitly asked. At handoff, report changed files, validation, and suggested next commands.
- **Minimal**: Keep tool instruction files as pointers to `bd prime`; use the same conservative git policy unless active instructions say otherwise.
- **Team-maintainer**: Only when the repository explicitly opts in, agents may close beads, run quality gates, commit, and push as part of session close. A current "do not commit" or "do not push" instruction still wins.

## Session Completion

This protocol applies when ending a Beads implementation workflow. It is subordinate to explicit user, repository, and orchestrator instructions.

1. **File issues for remaining work** - Create beads for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **Handle git/sync by active profile**:
   ```bash
   # Conservative/minimal/default: report status and proposed commands; wait for approval.
   git status

   # Team-maintainer opt-in only, unless current instructions forbid it:
   git pull --rebase
   bd dolt push
   git push
   git status
   ```
5. **Hand off** - Summarize changes, validation, issue status, and any blocked sync/commit/push step

**Critical rules:**
- Explicit user or orchestrator instructions override this Beads block.
- Do not commit or push without clear authority from the active profile or the current user request.
- If a required sync or push is blocked, stop and report the exact command and error.
<!-- END BEADS INTEGRATION -->

<!-- BEGIN BEADS CODEX SETUP: generated by bd setup codex -->
## Beads Issue Tracker

Use Beads (`bd`) for durable task tracking in repositories that include it. Use the `beads` skill at `.agents/skills/beads/SKILL.md` (project install) or `~/.agents/skills/beads/SKILL.md` (global install) for Beads workflow guidance, then use the `bd` CLI for issue operations.

### Quick Reference

```bash
bd ready                # Find available work
bd show <id>            # View issue details
bd update <id> --claim  # Claim work
bd close <id>           # Complete work
bd prime                # Refresh Beads context
```

### Rules

- Use `bd` for all task tracking; do not create markdown TODO lists.
- Run `bd prime` when Beads context is missing or stale. Codex 0.129.0+ can load Beads context automatically through native hooks; use `/hooks` to inspect or toggle them.
- Keep persistent project memory in Beads via `bd remember`; do not create ad hoc memory files.

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/core-concepts/sync-concepts.md for details and anti-patterns.
<!-- END BEADS CODEX SETUP -->
