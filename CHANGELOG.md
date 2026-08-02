# Changelog

All notable changes to this repository, derived from git history. No release tags exist; entries are dated and keyed to commit hashes.

## [Unreleased]

### Documentation (archive prep)
- Audit `README.md`: accurate repository structure, technique status, documentation index
- Add `ARCHITECTURE.md` — research structure, writeup format, content categories
- Add `CONTRIBUTING.md` — contribution and review process
- Add `SECURITY.md` — engagement boundary, redaction policy, non-public data
- Add `CHANGELOG.md` — this file
- Add `AGENTS.md` — agent commands and conventions
- Add `docs/CONTENT-INVENTORY.md` — full content inventory
- Add `docs/MIGRATION.md` — azraelsec.dev migration status

## 2026-05-20

### Documentation
- README expanded to 322 lines: research methodology (five phases), CVE-2025-23266 deep-dive, lab environment details, technique library, reproducibility principles (`42455d9`)

## 2026-04-12

### Research
- **Whitepaper 1 published:** *Below the Abstraction: Hook Isolation Failures in the NVIDIA Container Toolkit* — CVE-2024-0132 → CVE-2025-23359 → CVE-2025-23266 chain under rootless Podman, four-way runtime comparison (`94db7bb`)

### Housekeeping
- Remove `CLAUDE.md` (`11a6877`)

## 2026-03-24

### Documentation
- Add repo-level Claude Code context (`373ad22`)

## 2026-03-19

### Changed
- **Restructured as Azrael Security research hub:** RE thread, kernel research, container boundary research scaffold (`8145230`)
- Removed portfolio-era `SECURITY.md`, `HIRING.md`, and markdown CI tooling as part of the restructure

## 2026-02-08

### Added
- StackSmash re-1 and re-2 writeups with redacted flag material (`01a36df`, `a8792ad`, `7c3a43a`)
- Personal site link and screenshot (`1855cc5`)
- File upload writeup formatting fixes (`84f3b51`)

## 2026-02-07

### Changed
- Labs reorganized into writeups taxonomy with landing pages; `SECURITY.md` added (`63bf654`)
- Markdown formatting normalized via prettier + markdownlint (`0d2c0f2`, `67c45ca`, `8718bb2`, `9ecc76d`, `efe12e5`)
- Markdown CI enforcement added (`ffb67b0`) and subsequently removed (`c9d6614`)
- Dependency sync for reproducible CI installs (`0793086`, `e2fc213`)
- `node_modules` ignored (`b482463`)

## 2026-01-14

### Changed
- README enhanced with field report and portfolio narrative (`f0d65c7`)

## 2026-01-10

### Added (initial portfolio)
- Initial commit: professional security portfolio with Enterprise AD Attack Chain showcase (`065dd11`)
- ACLGuard tool documentation and professional sample artifact (`b4ddb9c`)
- Verification links and professional narrative integration (`54bd7c5`, `5005ece`, `640116d`)
- Binary exploitation showcase and comprehensive labs (`1c6da8e`)
- Hiring manager summary document `HIRING.md` (`c68283f`)
- AD attack chain methodology template and quick navigation (`19cae57`)
- AD-RTS / CAPT verification artifacts and image path fixes (`ceeaf8f`, `1bac20a`, `475001e`)

---

Entries grouped by date; multiple commits per date are summarized. Full detail in `git log`.
