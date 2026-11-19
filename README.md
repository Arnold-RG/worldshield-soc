# WorldShield SOC

**Security operations · Global threat intelligence** · [Repository](https://github.com/Arnold-RG/worldshield-soc)

## Overview

Security operations dashboard and research workspace focused on cyber events, alert review, and analyst-facing investigation workflows. The repository currently exposes a public UI, development dependencies, scripts and tests; integrations and autonomous incident handling must be verified before being described as live.

> **Engineering status:** Repository structure reviewed in November 2026. Specific capabilities and platform/device security are not certified by this README. Confirm a behavior with source and tests before making public claims.

## Technology and architecture

**Observed stack:** Browser UI assets, Python development tests, security tooling.

| Location | Purpose |
| --- | --- |
| `public/` | Public UI and static resources |
| `scripts/` | Operational and developer scripts |
| `tests/` | Test cases |
| `pytest.ini` | Python test configuration |
| `requirements-dev.txt` | Development test dependencies |
| `.env.example` | Environment-variable example; never put live credentials in version control |

## Quick start

Install Git and the appropriate runtime/SDK first; inspect the configuration and existing scripts before running anything against production. From the repository root:

```sh
python -m venv .venv
# Activate .venv for your operating system
python -m pip install -r requirements-dev.txt
python -m pytest
```

**Development guidance:** Python tests can be run with the command above; the UI hosting/deployment mechanism should be read from the current scripts and workflows. No live threat-feed certification is implied.

## Product scope and usability

- SOC-oriented UI and analyst workflows are the project direction; verify each data connector before representing any information as real-time.
- All alerts must distinguish mock demonstrations from real telemetry.
- Threat events need immutable identifiers, sources, timestamps and review status.

The release experience should support clear labels, accessible focus/keyboard navigation (where applicable), useful errors, and truthful customer-facing information. Preview changes before publishing.

## Security and privacy

- Treat incoming events as untrusted; encode/sanitize output and rate-limit ingestion endpoints when introduced.
- Use scoped service accounts; no stored secrets, unapproved active response or automatic blocking.
- Provide audit logs, retention limits, backup/restore and an incident response runbook before production.

Use least privilege, documented trust boundaries and secret scanning. Never include real access tokens in examples. Report vulnerabilities privately through the repository's `SECURITY.md` when available.

## Quality assurance and DevOps

| Release gate | Expected evidence |
| --- | --- |
| Build | Clean, reproducible build using locked dependency versions where available |
| Tests | Unit/integration or relevant command-line tests; passing CI run links |
| Security | Dependency/secret scans and review of authentication and data handling |
| UX | Mobile/desktop and accessibility checks for interactive web interfaces |
| Delivery | Reviewed changes, environment separation, verified deployments and rollback plan |
| Operations | Logs/metrics/alerts for running services; availability/link checks for static websites |

**Important:** This table defines the target quality process, not a claim that every check has passed. Kubernetes is optional and should be introduced only when real backend complexity and scale justify it.

## Improvement roadmap

1. Inventory actual UI controls and tested end-to-end workflows.
2. Separate mock data from authenticated telemetry; define event schema and RBAC.
3. Add CI lint/tests, SAST/dependency checks, API integration tests and deployment runbooks.
4. Add observability, SLOs and incident drill before any live SOC use.

## Working on the project

Keep changes small and reviewable. Update this README when commands or features change, attach test evidence to pull requests, maintain honest limitations and review licenses before adding assets. The repository owner approves release publication.
