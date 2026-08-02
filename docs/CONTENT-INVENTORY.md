# Content Inventory

Complete inventory of tracked content as of 2026-08-02. Update this file when content is added, removed, or migrated.

## Summary

| Category | Count | Notes |
|---|---|---|
| Research documents | 1 | Container boundary whitepaper |
| Technique writeups | 2 | re-1, re-2 (reverse engineering) |
| Writeup index | 1 | `writeups/README.md` |
| CVE analyses | 3 | CVE-2024-0132, CVE-2025-23359, CVE-2025-23266 (chain, in whitepaper) |
| Diagrams / figures | 6 | Whitepaper figures fig-01 … fig-06 |
| Screenshots (writeup) | 13 | re-1 (6), re-2 (7) |
| Certificate assets | 50 | AD-RTS, CAPT (+ 46 lab screenshots, grid), COSJ |
| Site screenshot | 1 | `assets/screenshots/personal-site-homepage.png` |
| Code samples | 1 | `poc.so` constructor (embedded in whitepaper) |
| Tracked content files | 76 | 6 text, 70 images (excludes repository docs) |

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
| re-1 | `techniques/linux/re/re-1/README.md` | ELF 32-bit x86, PIE, not stripped | static + GDB, byte-wise comparison loop | 6 |
| re-2 | `techniques/linux/re/re-2/README.md` | ELF 64-bit stripped | strings/ltrace/GDB, hex decode → XOR/OR comparison | 7 |

Both are StackSmash challenge writeups with full methodology (not just solutions).

## Writeups Index

- `writeups/README.md` — landing page; categories `web-security/`, `binary-exploitation/`, `penetration-testing/`, `reverse-engineering/` referenced. Only `reverse-engineering/` exists on disk, as an empty scaffold (`re-1/images/`).

## Diagrams and Figures

All figures are PNG. Whitepaper figures carry descriptive captions in the source document and follow a `fig-NN-<topic>.png` naming scheme. Writeup screenshots use descriptive names (`binary-identification.png`, `XOR-based-comparison.png`).

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

## Scaffold Directories (empty, untracked)

| Path | Intended content |
|---|---|
| `labs/tairn/` | Lab work notes from Tairn |
| `writeups/reverse-engineering/re-1/images/` | Future RE writeup figures |

## Not Present (referenced but not yet created)

README's future-work section references these planned locations; no content yet:

- `research/kernel/`, `research/active-directory/`, `research/infrastructure/`
- `techniques/ad/`, `techniques/linux/kernel/`
- AD technique writeups (Kerberoasting, AS-REP Roasting, DCSync, Golden Ticket — documented in azrael-vault, not in this repository since the 2026-03-19 restructure)
