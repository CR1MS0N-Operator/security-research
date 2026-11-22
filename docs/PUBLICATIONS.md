# Publication catalog

[publications.json](../publications.json) is the public, hand-maintained catalog of published research and completed technique writeups. Profile and site consumers can use it without interpreting git commits as research posts.

## Contract

The root object has a `publications` array, newest first. Each entry has:

| Field | Required | Meaning |
|---|---|---|
| `title` | Yes | The published document's title as nonempty plain text |
| `published_at` | Yes | Original public publication date, `YYYY-MM-DD`; not the last edit or today's date |
| `url` | Yes | Canonical HTTPS GitHub document URL in this repository on `main` |
| `summary_url` | No | HTTPS URL of an existing public Azrael Security blog post or executive report |

There is one entry per published document, with unique canonical URLs. Consumers should validate entries and sort by `published_at` rather than relying on array order. A catalog fetch or validation failure must not fabricate posts; consumers should preserve their last valid output. Editorial selection and refresh scheduling belong to consumers, not this file.

Do not add drafts, unfinished notes, placeholder URLs, planned papers, repository maintenance commits, or release events. Add `summary_url` only after the editorial page is publicly available; omit the field otherwise.

## Date provenance

| Publication | Date | Repository evidence |
|---|---|---|
| Below the Abstraction (Whitepaper 1) | 2026-04-12 | [Changelog publication entry](../CHANGELOG.md#2026-04-12), corroborated by the [completed paper's frontmatter](../research/container-boundaries/README.md) |
| StackSmash re-2 | 2026-02-08 | [Changelog writeup entry](../CHANGELOG.md#2026-02-08); [source](../techniques/linux/re/re-2/README.md) includes analysis and outcome evidence |

The [re-1 notes](../techniques/linux/re/re-1/README.md) explicitly leave analysis and validation unfinished. They remain discoverable in the README but are intentionally excluded from this completed-publication catalog. Their challenge-work date is not used as a publication date.

## Contributor checklist

1. Confirm the source is public, complete, reviewed, and covered by the [security policy](../SECURITY.md).
2. Record the original date from publication evidence, not a metadata edit or unrelated commit. Add that evidence to the table above.
3. Add the entry to `publications.json` and the README's published-work section. Update the [inventory](CONTENT-INVENTORY.md).
4. Check JSON parsing, required nonempty fields, valid calendar dates, uniqueness, descending dates, and public URL destinations before opening the PR.

No new dependency, generator, network job, or executable code is required to maintain the catalog.
