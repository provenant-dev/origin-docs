---
coverY: 0
layout:
  cover:
    visible: false
    size: full
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: true
---

# Platform Documentation

Origin Cloud&trade; helps organizations construct and manage their digital identity &mdash; and use that identity to improve efficiency and build reputation. Origin is rooted in world-class cryptography and cybersecurity, translating that rigor into simple business processes that anyone can understand. It is built atop [open source technologies](https://github.com/WebOfTrust), operated commercially by [Provenant](https://provenant.net)&trade; and its partners, and supports low-friction interactions with ecosystem participants who do not use Origin directly.

Which features of Origin are most relevant to you depends on your perspective:

- If you belong to an org that needs to consume Origin features, see [Clients](perspectives/clients.md).
- If you belong to an org that uses Origin to deliver value-added identity features to others, see [Service Providers](perspectives/sps/README.md).
- If you are a developer who wants to create services on Origin, see [Developers](perspectives/developers.md).

---

## For contributors to this documentation repo

This section is for people editing or maintaining the content in this repository. End users of the platform do not need to read it.

### What this repo is

`origin-docs` is the source for the public-facing Origin platform documentation, rendered via [GitBook](https://www.gitbook.com/). GitBook reads the Markdown files in this repo and publishes them as a browsable website. There is no build step, no test suite, and no runtime application to launch &mdash; the deliverable is the Markdown content itself.

### Prerequisites

| Tool | Purpose | Notes |
|------|---------|-------|
| Git | Version control | Any recent version |
| A text editor or IDE | Editing Markdown | VS Code with a Markdown preview plugin works well |
| GitBook account (optional) | Previewing rendered output | Only needed for layout/image testing; plain Markdown preview is usually enough |

No language runtime, Docker, database, or virtual environment is required.

### Getting started (from a fresh clone)

```bash
git clone git@github.com:provenant-dev/origin-docs.git
cd origin-docs
```

Open any `.md` file in your editor. GitBook-specific front matter (YAML blocks at the top of files) and `&#x20;` / `\` line-continuation sequences are GitBook formatting artifacts &mdash; leave them in place.

To preview rendering locally, you can use any Markdown viewer. For a faithful GitBook preview you need a GitBook account linked to this repository; contact [origin-ecosystem@provenant.net](mailto:origin-ecosystem@provenant.net) for access.

### Verifying your changes

There is no automated test suite. Quality checks are manual:

1. Confirm all internal Markdown links resolve to real files (`grep -rP '\]\((?!https?://)' .` is a quick scan for any non-HTTP Markdown link).
2. Confirm the `SUMMARY.md` table of contents includes any new pages you added.
3. Open a pull request; a human reviewer checks content accuracy before merging.

GitBook re-renders the site automatically on every merge to `main`.

### Repo structure

```
origin-docs/
├── README.md               # This file; also the GitBook home page
├── SUMMARY.md              # GitBook table of contents (must be kept in sync)
├── glossary.md             # Platform-wide term definitions
├── perspectives/
│   ├── clients.md          # Guide for client orgs
│   ├── developers.md       # Guide for developers building on Origin
│   └── sps/
│       ├── README.md       # Guide for service providers
│       └── dir.md          # Service provider directory listing
├── concepts/
│   ├── pii.md              # How Origin handles personally identifiable information
│   └── creds/
│       ├── README.md       # Overview of credentials and verifiable data
│       ├── formats.md      # X.509 vs VC vs ACDC credential formats
│       ├── issuing.md      # How to issue credentials
│       ├── verifying.md    # How to verify credentials
│       └── vleis/
│               ├── README.md   # vLEI overview and index
│               ├── why.md      # Problems solved by vLEIs
│               ├── types.md    # LE, OOR, ECR, and QVI vLEI types
│               ├── journey.md  # Step-by-step path to vLEI issuance
│               └── uses.md     # Ways to use vLEIs
├── tasks/
│   └── sign-with-vlei.md   # How-to: signing content with a vLEI
└── .gitbook/
    └── assets/             # Images referenced by GitBook pages
```

### Key rules for contributors

- **Keep `SUMMARY.md` in sync.** GitBook uses it as the navigation tree. A page not listed there will not appear in the published site.
- **Do not hand-edit GitBook front matter.** The YAML blocks at the top of some files control GitBook layout options; editing them incorrectly breaks the rendered output.
- **Images live in `.gitbook/assets/`.** Reference them with a relative path from the file that uses them (e.g., `../../.gitbook/assets/vd-by-attrib.png`).
- **No generated files.** All content in this repo is hand-authored. Do not commit auto-generated output.
- **GitBook artifacts are intentional.** The `&#x20;` entities and trailing `\` sequences are GitBook's way of encoding non-breaking spaces and line breaks in Markdown; do not "fix" them.

### Going deeper

| Document | What it covers |
|----------|---------------|
| [SUMMARY.md](SUMMARY.md) | Complete GitBook navigation tree |
| [Glossary](glossary.md) | Definitions of all platform-specific terms |
| [Origin for Developers](perspectives/developers.md) | Building services on Origin |
| [Origin for Service Providers](perspectives/sps/README.md) | Becoming a service provider or facilitator |
| [Origin for Clients](perspectives/clients.md) | Using Origin as a client organization |
| [vLEI Concepts](concepts/creds/vleis/README.md) | What vLEIs are and how they work |
| [Credential Formats](concepts/creds/formats.md) | X.509 vs W3C VC vs ACDC |
| [Sign with a vLEI](tasks/sign-with-vlei.md) | Simple mode vs chained mode signing |
| [PII on Origin](concepts/pii.md) | How personally identifiable information is handled |
| [Service Provider Directory](perspectives/sps/dir.md) | Current list of service providers |
| [KERI ecosystem docs](https://kerisse.org) | Underlying cryptographic foundation (external) |
| [GLEIF vLEI Governance Framework](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework) | GLEIF rules governing vLEI issuance (external) |
| [Origin platform KB](https://github.com/provenant-dev/origin-platform) | Architecture, security model, and developer KB for the broader Origin platform |

> Additional technical documentation for contributors will be added to a `docs/` folder in this repository as the project matures.

### Related Origin platform repos

Origin is implemented across a family of `origin-*` repositories. This repo (`origin-docs`) contains only the public-facing user documentation. The platform KB, service implementations, and tooling live in sibling repos under the [provenant-dev](https://github.com/provenant-dev) GitHub organization.
