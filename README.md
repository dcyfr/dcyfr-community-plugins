# DCYFR Community Plugin Marketplace

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
