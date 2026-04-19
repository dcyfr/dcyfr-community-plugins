# DCYFR Community Plugin Marketplace

[![Security Scan](https://github.com/dcyfr/dcyfr-community-plugins/actions/workflows/community-plugin-scan.yml/badge.svg)](https://github.com/dcyfr/dcyfr-community-plugins/actions/workflows/community-plugin-scan.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/dcyfr/dcyfr-community-plugins)
[![Sponsor](https://img.shields.io/badge/sponsor-30363D?style=flat-square&logo=GitHub-Sponsors&logoColor=#EA4AAA)](https://github.com/sponsors/dcyfr)

> **⚠️ UNAUDITED BY DCYFR SECURITY TEAM**
> Community plugins are automatically scanned but have **not** been manually reviewed
> by the DCYFR security team. Use at your own risk. For audited plugins, see
> [dcyfr/dcyfr-plugins](https://github.com/dcyfr/dcyfr-plugins).

Community-contributed plugins for the DCYFR AI framework. All submissions are
automatically scanned for security issues, but pass/fail is determined by CI — not
human review.

## How It Works

1. Community members submit a plugin via Pull Request.
2. CI runs automated security scans (manifest validation, SBOM check, vulnerability scan,
   trust score calculation).
3. If **all scans pass** and trust score ≥ 70, the PR is **auto-merged**. No human required.
4. Plugins with trust score 90+ and 100+ downloads are escalated for DCYFR security audit
   and may be promoted to [dcyfr-plugins](https://github.com/dcyfr/dcyfr-plugins).

## Plugins

| Plugin | Trust Score | Category | Verified |
| ------ | ----------- | -------- | -------- |
| (no plugins yet — [submit yours!](#submitting-a-plugin)) | — | — | — |

## Submitting a Plugin

See [CONTRIBUTING.md](CONTRIBUTING.md) for full instructions.

**Quick start:**

```bash
# Clone and create your plugin directory
git clone https://github.com/dcyfr/dcyfr-community-plugins
cd dcyfr-community-plugins
mkdir plugins/your-plugin-name
```

Then add: `.claude-plugin/manifest.json`, `trust-score.json`, `sbom.json`, and your code.

### Plugin Structure

Every submission must follow this layout:

```
plugins/your-plugin-name/
  .claude-plugin/
    manifest.json       # plugin metadata (name, version, capabilities, permissions)
  trust-score.json      # self-declared metrics used as baseline for scoring
  sbom.json             # Software Bill of Materials (CycloneDX format)
  index.ts              # plugin entry point (exports default plugin)
  package.json          # npm metadata, dependencies
  README.md             # what your plugin does and how to use it
  LICENSE               # must be SPDX-compatible (MIT recommended)
```

### `manifest.json` Minimum Fields

```json
{
  "name": "your-plugin-name",
  "version": "1.0.0",
  "description": "What this plugin does",
  "author": "your-github-handle",
  "license": "MIT",
  "capabilities": ["code_quality"],
  "permissions": ["read_files"],
  "dcyfr": {
    "minVersion": "1.0.0",
    "maxVersion": "*"
  }
}
```

**Valid capabilities:** `code_quality`, `security`, `testing`, `compliance`, `performance`, `accessibility`, `api_quality`, `ui_quality`, `sbom`, `dependency_analysis`

**Valid permissions:** `read_files`, `read_env`, `network` (network requires trust score ≥ 85)

### Trust Score Breakdown

CIs compute trust scores automatically — your `trust-score.json` is used as a baseline:

| Factor | Weight | Description |
|--------|--------|-------------|
| Security scan | 30% | No secrets, vulnerabilities, or malware detected |
| License | 20% | Valid SPDX identifier, OSI-approved |
| SBOM completeness | 15% | All deps declared, no phantom deps |
| Manifest validity | 15% | All required fields present, valid capabilities |
| Code quality | 10% | No obvious anti-patterns, no `eval`, no `exec` |
| Author reputation | 10% | GitHub account age, prior contributions |

**Minimum to auto-merge: 70.** Scores below 70 require manual DCYFR review.

## Verified Publisher Program

Plugin authors who meet the [verified publisher criteria](VERIFIED_PUBLISHERS.md) receive
a ✅ badge and priority in search results.

## Plugin Quality Tiers

| Tier | Trust Score | Review Type | Badge |
| ---- | ----------- | ----------- | ----- |
| Community | ≥ 70 | Automated only | — |
| Verified | ≥ 85 + criteria met | Automated + criteria check | ✅ |
| Audited | ≥ 90 + DCYFR audit | Full manual security review | 🔒 |

## Security

Found a vulnerability in a community plugin? See [SECURITY.md](SECURITY.md).

## License

MIT — see [LICENSE](LICENSE).
