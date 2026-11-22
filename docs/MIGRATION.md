# Publishing model

GitHub holds the raw research. Azrael Security presents selected work for readers who need a blog-format explanation or an executive report.

This replaces the former plan to migrate all content to azraelsec.dev and archive this repository. The filename is retained so existing documentation links continue to work; no research, figures, or technique notes have moved.

## Source and editorial layers

| Layer | Home | Responsibility |
|---|---|---|
| Canonical research | This repository | Full papers, methodology, lab conditions, evidence, figures, detection guidance, and revision history |
| Publication catalog | [publications.json](../publications.json) | Dated public entries that profile and site consumers can read |
| Editorial presentation | [Azrael Security](https://azraelsecurity.vercel.app) | Selected blog posts and executive reports from the top 3–10 research pieces, linking back to the raw source |
| Profile discovery | [GitHub profile](https://github.com/CR1MS0N-Operator) | Links to published work; the profile's refresh is maintained separately |

## Current scope

- Raw research remains here, with existing paths and evidence preserved.
- The catalog lists existing published work only; notes and planned tracks are not posts.
- No executive-report URLs are recorded until the corresponding public pages exist.
- This repository does not implement site curation, editorial generation, or a scheduled profile refresh.
- The top 3–10 is an editorial selection goal as the corpus grows, not a claim that that many completed publications exist today.

## Publishing flow

1. Publish the complete, reviewed source and evidence here under the existing research or technique layout.
2. Add its title, original publication date, and canonical GitHub URL to the [catalog](../publications.json), following the [catalog contract](PUBLICATIONS.md).
3. Select work for a site blog post or executive report. Keep measured findings, limitations, and defensive guidance consistent with the source.
4. Once a public editorial page exists, add its optional `summary_url` to the catalog. Both layers link to their counterpart.
5. Revise the raw source in GitHub; review related editorial pages when conclusions change. Formatting changes do not reset publication dates.

## Publication boundaries

The [security policy](../SECURITY.md) applies to both layers. Credentials, internal addressing, operational configuration, PII, and non-lab data never become public. No automatic migration, content deletion, or repository archival is part of this model.
