# AGENTS.md - dcyfr-community-plugins

## Project Overview

Community plugin marketplace for the DCYFR AI framework. This repo is registry- and policy-driven: plugin metadata, contribution docs, trust scoring, and CI automation matter more than application code.

## Architecture

- Marketplace metadata: `marketplace.json`
- Plugin submissions live under `plugins/`
- Contribution and security rules live in `CONTRIBUTING.md`, `SECURITY.md`, and `VERIFIED_PUBLISHERS.md`
- Automation lives in `.github/workflows/`

## Working Rules

- Treat community plugins as untrusted input; preserve the repo's security posture.
- Prefer schema, policy, and workflow updates over ad hoc manual exceptions.
- If a change affects submission requirements, update the corresponding docs and CI expectations together.
