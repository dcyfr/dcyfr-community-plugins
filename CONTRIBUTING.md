# Contributing to DCYFR Community Plugins

> **⚠️ UNAUDITED DISCLAIMER**
> Community plugins pass automated scans but are **not** manually reviewed by the
> DCYFR security team. Authors are responsible for their plugin's security.

## Submission Requirements

### 1. Directory Structure

Create a directory under `plugins/<your-plugin-name>/` with:

```
plugins/your-plugin-name/
├── .claude-plugin/
│   └── manifest.json      # Plugin manifest (REQUIRED)
├── trust-score.json       # Self-assessed trust score (REQUIRED)
├── sbom.json              # CycloneDX 1.4 SBOM (REQUIRED)
├── README.md              # Plugin documentation (REQUIRED)
└── LICENSE                # License file (REQUIRED)
```

### 2. manifest.json Schema

```json
{
  "plugin_id": "your-github-handle/your-plugin-name",
  "name": "your-plugin-name",
  "version": "1.0.0",
  "description": "What your plugin does",
  "license": "MIT",
  "capabilities": ["code_quality"],
  "permissions": {
    "filesystem": { "read": ["**/*.ts"], "write": [], "delete": [] },
    "network":    { "allowed": false, "allowedDomains": [], "maxRequests": 0 },
    "execution":  { "allowShellCommands": false, "allowedCommands": [], "maxProcesses": 0 },
    "mcp":        { "allowedServers": [], "deniedServers": [] },
    "data":       { "allowEnvironmentVars": false, "allowSecretAccess": false }
  },
  "entrypoint": "index.js",
  "minFrameworkVersion": "2.0.0"
}
```

### 3. trust-score.json Schema

```json
{
  "plugin_id": "your-handle/your-plugin",
  "overall": 75,
  "dimensions": {
    "security": 80,
    "community": 70,
    "maintenance": 75,
    "transparency": 75
  },
  "recommendation": "install",
  "rationale": "Describe why this score is accurate"
}
```

Minimum `overall` score to pass auto-merge: **70**.

### 4. sbom.json (CycloneDX 1.4)

Generate with `cyclonedx-node-npm` or use the example template in
[dcyfr/dcyfr-plugins](https://github.com/dcyfr/dcyfr-plugins).

## Verified Publisher Criteria

See [VERIFIED_PUBLISHERS.md](VERIFIED_PUBLISHERS.md) to apply for a ✅ badge.

## Auto-Merge Policy

PRs are **automatically merged** when:

1. All CI checks pass (manifest valid, SBOM present, license approved, trust score ≥ 70)
2. PR touches only files under `plugins/<your-plugin-name>/`
3. `plugin_id` in manifest matches the PR author's GitHub handle
4. No critical or high-severity CVEs in dependencies

PRs are **held for human review** when:

- Trust score is between 50–69 (borderline)
- Network access is requested (`network.allowed: true`)
- Secret access is requested
- Any scan fails

## Escalation to Official Marketplace

Plugins with **trust score ≥ 90** and **100+ downloads** are automatically nominated
for DCYFR security audit. If the audit passes, the plugin may be promoted to
[dcyfr/dcyfr-plugins](https://github.com/dcyfr/dcyfr-plugins).

## Code of Conduct

By submitting a plugin, you agree to the [DCYFR Code of Conduct](https://dcyfr.ai/conduct).
Malicious plugins will be removed and the author banned.
