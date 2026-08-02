# Contributing

How to add research, techniques, and writeups to this repository.

## Scope

This repository publishes original offensive security research and technique documentation from the Azrael Security research program. Contributions must:

- Come from authorized, self-operated lab infrastructure only (see `SECURITY.md`)
- Never describe testing against production or unauthorized systems
- Include detection guidance wherever a finding or PoC is presented
- Follow the format and review process below

This is a documentation repository. Content is not moved or deleted outside of explicit migration work; structural changes to content are out of scope for normal contributions.

## Adding Research

### 1. Choose the home

| Content | Location |
|---|---|
| Vulnerability / CVE research, whitepapers | `research/<track>/` |
| Technique documentation (binary analysis, AD attacks, kernel primitives) | `techniques/<platform>/<category>/<technique>/` |
| Challenge or lab writeups | `writeups/<category>/` |
| Figures, screenshots | `assets/` or `<writeup>/images/` |
| Lab work notes | `labs/<platform>/` |

### 2. Create the document

- Every research document starts with YAML frontmatter: `created`, `updated`, `tags`, `status` (see `ARCHITECTURE.md`).
- Research findings follow the whitepaper section template (abstract → background → prior work → methodology → results → findings → defensive guidance → conclusion).
- Technique writeups follow the re-1/re-2 template: metadata, objective, recon, analysis, outcome, takeaways, defensive notes.
- Figures: descriptive filenames, captioned image references, stored next to the document that uses them.

### 3. Version-pin the environment

Every finding documents the exact environment: OS and version, kernel version, runtime versions (Podman/Docker/runc/crun), toolkit versions, GPU/driver where relevant. Version pinning is what makes results reproducible.

### 4. Include detection guidance

All PoCs must ship with detection guidance: what to monitor, which rule/pattern catches the behavior, expected vs anomalous behavior. Kernel exploits additionally require full root cause analysis, not just a working trigger.

### 5. Redact before committing

Apply the `SECURITY.md` redaction policy before `git add`: flags, host identifiers, usernames where applicable, and anything on the never-public list. Review every screenshot and figure for sensitive content.

## Review Process

1. **Self-review checklist** (before commit):
   - Environment versions pinned
   - Negative results documented where applicable
   - Detection guidance present
   - Redaction policy applied
   - Links relative and valid
2. **Diff review:** review the staged/unstaged diff in hunk (`hunk diff` or `git difftool`) before committing. One logical change per commit.
3. **Micro-commits:** commit per logical change with conventional commit prefixes:
   - `docs:` — documentation
   - `research:` — research content (findings, whitepapers)
   - `technique:` — technique writeups
   - `chore:` — housekeeping
4. **No push without approval:** changes are committed locally; pushing requires explicit instruction.

## Guardrails

- Lab environment only. No production infrastructure testing.
- No unauthorized target scanning.
- No credentials, tokens, keys, internal IPs, or PII in any commit.
- Do not move or delete content outside of tracked migration work.
- Archive prep is documentation-only: no content moves.
