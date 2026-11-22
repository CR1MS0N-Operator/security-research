# Content Inventory

Inventory of tracked research and supporting content. Update this file when content is added, removed, or migrated. Raw research and evidence remain on GitHub under the [publishing model](MIGRATION.md).

## Summary

| Category | Count | Notes |
|---|---|---|
| Research documents | 1 | Container boundary whitepaper |
| Technique documents | 2 | re-2 completed; re-1 unfinished reconnaissance notes |
| Writeup index | 1 | `writeups/README.md` |
| CVE analyses | 3 | CVE-2024-0132, CVE-2025-23359, CVE-2025-23266 (chain, in whitepaper) |
| Diagrams / figures | 6 | Whitepaper figures fig-01 … fig-06 |
| Screenshots (writeup) | 13 | re-1 (6), re-2 (7) |
| Certificate assets | 50 | AD-RTS, CAPT (+ 46 lab screenshots, grid), COSJ |
| Site screenshot | 1 | `assets/screenshots/personal-site-homepage.png` |
| Presentation artwork | 4 | Local, accessible dark/light SVG research banners in desktop and compact layouts |
| Publication catalog | 1 | `publications.json`: two completed public entries; contract and date evidence in `docs/PUBLICATIONS.md` |
| Code samples | 1 | `poc.so` constructor (embedded in whitepaper) |

## Research

### Container Boundaries — Whitepaper 1
- **Path:** `research/container-boundaries/README.md`
- **Title:** *Below the Abstraction: Hook Isolation Failures in the NVIDIA Container Toolkit*
- **Status:** completed (published 2026-04-12)
- **CVE chain:** CVE-2024-0132 → CVE-2025-23359 → CVE-2025-23266
- **Findings:** 3 (structural boundary failure, execseal asymmetry, runtime-specific reachability)
- **Figures:** 6 (`assets/fig-01-cdi-spec-diff.png` … `fig-06-patched-env-replacement.png`)
- **Code sample:** `poc.so` shared-library constructor (`__attribute__((constructor))`), demonstrated under crun
- **Scope:** rootless/rootful Podman × runc/crun four-way comparison

## Techniques

### Reverse Engineering
| Writeup | Path | Binary | Method | Figures |
|---|---|---|---|---|
| re-1 (unfinished notes) | `techniques/linux/re/re-1/README.md` | ELF 32-bit x86, PIE, not stripped | early reconnaissance; analysis and validation remain WIP | 6 |
| re-2 | `techniques/linux/re/re-2/README.md` | ELF 64-bit stripped | strings/ltrace/GDB, hex decode → XOR/OR comparison | 7 |

Both are StackSmash challenge documents. Only re-2 has completed analysis and outcome/validation; re-1 is not a completed publication and is excluded from the catalog.

## Writeups Index

- `writeups/README.md` — index linking existing research, the completed technique writeup, and unfinished notes. Unpopulated categories are not presented as available content.

## Diagrams and Figures

Research figures are PNG. Whitepaper figures carry descriptive captions in the source document and follow a `fig-NN-<topic>.png` naming scheme. Writeup screenshots use descriptive names (`binary-identification.png`, `XOR-based-comparison.png`). The four SVG banners are presentation assets, not research evidence; compact variants omit fine print for phone readability.

## Code Samples

One executable sample: the `poc.so` constructor in Whitepaper 1 (Section 5). Published with environmental context (runtime, uid mapping), deployment constraint (absolute host path required), and detection guidance (Section 7).

## Assets

### Certificates
- `assets/certificates/AD-RTS-Certificate.png` — Active Directory Red Team Specialist
- `assets/certificates/CAPT-Certificate.png` — Certified Associate Penetration Tester
- `assets/certificates/CAPT/labs/` — 46 CAPT lab screenshots + `summaries/all-labs-grid.jpg`
- `assets/certificates/COSJ.png` — Certified Offensive Security Junior

### Screenshots
- `assets/screenshots/personal-site-homepage.png`

## Historical Scaffold Directories (untracked, absent from fresh clones)

| Path | Intended content |
|---|---|
| `labs/tairn/` | Lab work notes from Tairn |
| `writeups/reverse-engineering/re-1/images/` | Future RE writeup figures |

## Not Present (referenced but not yet created)

These previously planned locations have no published content and are not linked as available work:

- `research/kernel/`, `research/active-directory/`, `research/infrastructure/`
- `techniques/ad/`, `techniques/linux/kernel/`
- AD technique writeups (Kerberoasting, AS-REP Roasting, DCSync, Golden Ticket — documented in azrael-vault, not in this repository since the 2026-03-19 restructure)
