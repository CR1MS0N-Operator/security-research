# Migration to azraelsec.dev

Status and mapping for the eventual archival of this repository.

## Status

**Phase: Preparation.** No content has been moved to azraelsec.dev. This session (2026-08-02) produced documentation only: architecture, contribution, security, changelog, agent rules, content inventory, and this migration record.

| Phase | Description | Status |
|---|---|---|
| Preparation | Documentation, inventory, migration mapping | **In progress** |
| Content migration | Whitepaper, techniques, writeups published to azraelsec.dev | Pending |
| Verification | Links, redaction, availability checks on the site | Pending |
| Archive | Repository archived after verification | Pending |

## Destination

[azraelsec.dev](https://azraelsec.dev) — Azrael Security public site. The site carries the same security policy as this repository (`SECURITY.md`): lab-originated content only, redaction applied, no operational data.

## Content Mapping

| Repository content | Destination | Notes |
|---|---|---|
| `research/container-boundaries/README.md` (Whitepaper 1) | azraelsec.dev research section | Flagship artifact; figures migrate with it |
| Whitepaper figures (fig-01 … fig-06) | Same page as whitepaper | Captions preserved |
| `techniques/linux/re/re-1`, `re-2` | azraelsec.dev writeups / RE section | Redacted flag material stays redacted |
| Writeup screenshots | With respective writeups | Reviewed against redaction policy |
| `writeups/README.md` | Writeup index page | Categories reflected on site |
| `assets/certificates/` | azraelsec.dev profile / certifications page | Or excluded — decision pending |
| `assets/screenshots/personal-site-homepage.png` | Superseded by the live site | Likely not migrated |
| `README.md`, `ARCHITECTURE.md`, `CONTRIBUTING.md`, `SECURITY.md`, `CHANGELOG.md`, `AGENTS.md`, `docs/` | Not migrated (repo-internal) | Remain in repository until archive; migration record kept |

## Never Migrates

Per `SECURITY.md`: credentials, tokens, keys, internal IPs/topology, C2 configuration, PII, non-lab data. Nothing on the never-public list moves to azraelsec.dev.

## After Migration

- Repository is archived (read-only) once site content is verified.
- This file remains as the permanent record of what moved where.
- Future research continues to be published on azraelsec.dev; the archive preserves provenance and history.
