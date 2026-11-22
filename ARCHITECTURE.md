# Architecture

This document describes how `security-research` is structured: what each directory holds, how writeups are formatted, and the content categories used across the repository.

## Repository Role

`security-research` is the public research hub for Azrael Security. It publishes original offensive security research, adversary emulation technique development, and infrastructure-focused vulnerability analysis. All work is conducted on self-operated, authorized lab infrastructure (see `SECURITY.md`).

This repository remains the canonical public home for raw research and evidence. The Azrael Security site is the editorial layer for selected blog posts and executive reports, not a replacement or archive destination. The publishing model is documented in [docs/MIGRATION.md](docs/MIGRATION.md).

## Directory Layout

```
security-research/
├── README.md                      # Research landing page and publication navigation
├── publications.json             # Dated public publication catalog
├── ARCHITECTURE.md                # This document
├── CONTRIBUTING.md                # How to add research; review process
├── SECURITY.md                    # Engagement boundary, redaction policy
├── CHANGELOG.md                   # Release history derived from git
├── AGENTS.md                      # Commands and conventions for AI agents
├── docs/
│   ├── CONTENT-INVENTORY.md       # Full content inventory
│   ├── MIGRATION.md               # GitHub source / site editorial publishing model
│   └── PUBLICATIONS.md            # Catalog contract and publication-date evidence
├── research/
│   └── container-boundaries/      # Flagship track: whitepaper + figures
│       ├── README.md              # Whitepaper 1 (published 2026-04-12)
│       └── assets/                # Figures fig-01 … fig-06
├── techniques/
│   └── linux/
│       └── re/                    # Reverse engineering challenge writeups
│           ├── re-1/              # ELF 32-bit reconnaissance notes (unfinished)
│           └── re-2/              # ELF 64-bit stripped, XOR comparison (StackSmash)
├── writeups/
│   └── README.md                  # Index of available writeups and notes
└── assets/
    ├── banner-dark.svg            # Theme-aware research blueprint artwork
    ├── banner-light.svg
    ├── banner-dark-compact.svg    # Simplified phone artwork without fine print
    ├── banner-light-compact.svg
    ├── certificates/              # Certification artifacts (AD-RTS, CAPT, COSJ)
    └── screenshots/               # Environment and site screenshots
```

### Empty scaffold directories

Earlier documentation described these untracked placeholder directories; they are not part of a fresh clone and have no published content:

- `labs/tairn/` — lab work notes from the Tairn platform
- `writeups/reverse-engineering/` — future RE writeup home (see `writeups/README.md`)

Empty directories are not tracked by git. The landing page links existing content only.

## Research Structure

Research is organized by track. Each track owns a top-level directory:

| Track | Directory | Status |
|---|---|---|
| Container boundaries | `research/container-boundaries/` | Active — flagship, Whitepaper 1 published |
| Linux kernel & systems | (planned) | No published content |
| Active Directory | (planned) | No published content |
| Red team infrastructure | (planned) | No published content |
| Reverse engineering | `techniques/linux/re/` | re-2 complete; re-1 investigation notes |

Planned tracks (`research/kernel/`, `research/active-directory/`, `research/infrastructure/`, `techniques/ad/`) do not yet contain content and are not listed as publications.

## Content Categories

Five categories of content exist in the repository:

### 1. Research findings
Deep analytical artifacts (e.g. the container boundary whitepaper). Distinguished from technique writeups by their scope: they analyze a vulnerability class, a CVE chain, or a research question end to end — root cause, reproduction, impact, detection. Home: `research/<track>/`.

### 2. Techniques
Reusable, mechanical documentation of a specific method: binary analysis approach, attack technique, or tool workflow. Each technique is a standalone directory with a `README.md` and any figures under `images/`. Home: `techniques/<platform>/<category>/<technique>/`.

### 3. Writeups
Challenge or lab writeups presented in report format (objective, recon, analysis, outcome). Home: `writeups/<category>/` (currently scaffolded).

### 4. Diagrams and figures
All figures live in an `assets/` or `images/` directory adjacent to the document that references them. Figures use descriptive filenames (`fig-03-ldpreload-hook-env.png`) and every image reference in markdown carries a caption describing what the figure demonstrates.

### 5. Code samples
Small, self-contained code snippets embedded in writeups (e.g. the `poc.so` constructor in Whitepaper 1). PoC code is published only with detection guidance and environmental context, per `SECURITY.md`.

## Writeup Format

### Frontmatter

Every research document (`research/**/README.md`) opens with YAML frontmatter:

```yaml
---
created: YYYY/MM/DD
updated: YYYY/MM/DD
tags:
  - <topic>
  - <category>
status: completed | in-progress | planned
---
```

### Research document structure

Research findings follow the whitepaper section template:

1. **Abstract** — problem, scope, key result
2. **Background** — stack/components under test
3. **Prior Work** — related public research, the research gap
4. **Methodology** — environment, exact versions, reproduction steps
5. **Results** — measured outcomes, including negative results
6. **Findings** — numbered, each traceable to evidence
7. **Defensive Guidance** — patch, configuration, monitoring
8. **Conclusion** — what the results mean for operators

### Technique writeup structure

Technique writeups use: metadata (platform, category, tools), objective, recon, analysis, outcome/validation, key takeaways, techniques & patterns, defensive notes. The completed re-2 writeup is the reference implementation; re-1 remains unfinished reconnaissance notes.

## Document Conventions

- **Content-only.** Markdown, local image assets, and the JSON publication catalog; no documentation build step. CI checks conventional commit messages.
- **Relative links** between repository documents; anchors kept lowercase.
- **Evidence-first:** claims are tied to tool output, source references, or measured results. Negative results are documented with the same rigor as positive ones.
- **Redaction:** anything covered by `SECURITY.md` redaction policy is redacted before commit (flags, host identifiers, usernames where applicable).
- **Micro-commits:** one logical change per commit, conventional commit style (`docs:`, `research:`, `chore:`). See `CONTRIBUTING.md`.
