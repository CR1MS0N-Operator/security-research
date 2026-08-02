# Security

Policies governing what research data enters this repository, how it is redacted, and what never becomes public.

## Engagement Data Boundary

All research documented here is conducted on self-operated, authorized lab infrastructure:

- **Cerberus** — Arch Linux edge node; rootless Podman (container boundary research)
- **Tairn** — NixOS 24.11; Docker, Mythic C2, Windows AD lab (AD/adversary emulation)
- **NightForge** — Arch Linux operator workstation; kernel research, RE

These platforms are part of the private Veil WireGuard mesh. Only the platform identities above are public; their network addressing, credentials, and internal configuration are not.

**Boundary rules:**

- No production infrastructure is tested, ever.
- No unauthorized target scanning is performed.
- Content in this repository reflects only lab-originated data.
- Live engagement or operational data does not enter this repository.

## Redaction Policy

Before any content is committed, the following must be redacted:

| Item | Treatment |
|---|---|
| Flags / challenge answers | Replaced with `████` blocks (see re-2 writeup) |
| Usernames (host accounts) | Replaced with uid numbers where relevant |
| Host identifiers beyond platform names | Removed or generalized |
| Internal IPs / subnets | Never published |
| Credentials, tokens, API keys | Never published |
| Session environment | Filtered to relevant variables only |
| Screenshots | Reviewed for sensitive content (hostnames, paths, open sessions) before commit |

Redaction is applied to figures and terminal output, not just prose. When a screenshot cannot be redacted cleanly, it is omitted and replaced with a textual description.

## What Never Goes Public

- Credentials, tokens, keys, or secrets of any kind
- Internal IP addresses, subnets, or network topology beyond the platform identities in the README
- C2 configuration details, agent payloads, or operational infrastructure state
- Personally identifiable information (operator or third-party)
- Any data originating outside the authorized lab boundary
- Details of live or past engagements

These items are also excluded from migration to azraelsec.dev. The azraelsec.dev site carries the same policy as this repository.

## Vulnerability Disclosure

Findings are disclosed responsibly: they are published only after vendor patches are available or coordinated disclosure completes (see Whitepaper 1 — all three CVEs were patched before publication). This repository does not publish zero-day details for unpatched vulnerabilities.

## Reporting

To report a security issue with this repository's content or configuration, open a GitHub issue. Do not include sensitive operational details in the report.
