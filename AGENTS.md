# security-research — Agent Rules

## Purpose
Container boundary vulnerability research and root cause analysis (RCA). Repository is the canonical public home for raw research and evidence; selected blog posts and executive reports belong on the Azrael Security site. See `docs/MIGRATION.md` for the publishing model.

## Language policy (operator rule, 2026-11-01, decision #289)

Only Rust, Go and C/C++ ship first-party software:

- **Big projects** — services, long-lived programs, substantial internal logic → **Rust**, as much as possible.
- **Tools and scripts** — first-party CLIs, gates, helpers → **Go**, standard library only.
- **C/C++** — only when a measurement shows a drastic difference; never a default, never a preference.

**Browser UI is the one scoped exception (decision #290).** TypeScript is permitted for code that runs
in a browser when an application genuinely needs a framework; services and APIs stay Rust/Go, and a
TypeScript/Node backend is a violation, not an application of the exception. Static/content sites are
content, not software.

**No tier applies — this repo is a research and documentation hub, not a software repo.** Any PoC that ships follows the tier by its shape; C and Go are already the stated research focus.

Authority: decision #289 and `~/Documents/ai-lab-vault/AGENTS.md` § "Language policy". Open point: existing shell glue is thin operator glue, not software, and stays until touched.

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
- **Inventory + publications:** update `docs/CONTENT-INVENTORY.md` when content is added; index completed public work in `publications.json` per `docs/PUBLICATIONS.md`.
- **Verification:** smoke-test the change, run `git difftool` (hunk) review, then commit. Never claim completion without evidence.

## Publishing Notes

- Raw research, figures, and evidence remain in this repository; do not archive it as a side effect of site publication.
- Site blog posts and executive reports are a curated editorial layer, not a replacement for raw sources.
- Guardrails from `SECURITY.md` apply to both layers. Add editorial URLs only after the public pages exist.

## Live state outranks the record (fleet rule, 2026-10-26)

A measurement taken now outranks any document, skill or config that contradicts it — including this
file. Never pin live facts (model ids, prices, ports, paths, versions) in docs or skills: name the role
and resolve it live. Before a dispatch, run `cr1ms0n-fleet-check` (it fails loudly on a dead pin).
Canonical rule and its origin: `~/Documents/ai-lab-vault/AGENTS.md` § "Live state outranks the record".
