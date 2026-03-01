# Security Policy

## Reporting a Vulnerability in a Community Plugin

**Do NOT open a public issue.** Email hello@dcyfr.ai with:

- Plugin ID (e.g., `author/plugin-name`)
- Description of the vulnerability
- Steps to reproduce
- CVSS score (if known)

We will respond within **48 hours** and coordinate disclosure with the plugin author.

## Scope

- Community plugins in this repository
- The automated CI pipeline and scanning infrastructure

## Out of Scope

- Vulnerabilities in the DCYFR AI framework itself (report to `dcyfr-ai`)
- Theoretical risks without a working proof-of-concept

## Emergency Removal

For critical vulnerabilities (CVSS ≥ 9.0), DCYFR reserved the right to remove a plugin
and notify affected users without waiting for the patch.
