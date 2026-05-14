# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in any mq-rest-admin
component, please report it through
[GitHub's private vulnerability reporting](https://github.com/mq-rest-admin-project/.github/security/advisories/new).
This ensures your report is handled confidentially.

If private vulnerability reporting is unavailable, email
**w.phillip.moore@gmail.com** with the subject line
"mq-rest-admin Security Report". Do not open a public issue for
security vulnerabilities.

## Scope

The following components are in scope for security reports:

- **mq-rest-admin-python** — Python wrapper library (pymqrest)
- **mq-rest-admin-java** — Java wrapper library
- **mq-rest-admin-go** — Go wrapper library
- **mq-rest-admin-ruby** — Ruby wrapper library
- **mq-rest-admin-rust** — Rust wrapper library
- **mq-rest-admin-common** — Shared documentation fragments
- **mq-rest-admin-dev-environment** — Dockerized MQ test environment
  and its composite GitHub Action

## Out of Scope

- Vulnerabilities in IBM MQ itself or the IBM MQ REST API — report
  these to IBM
- Vulnerabilities in upstream language dependencies — report these to
  the upstream maintainer
- Vulnerabilities in GitHub, Docker, or other third-party platforms
- Social engineering attacks against project contributors

This is an independent community project, not an IBM product.

## Response Commitment

- **Acknowledgment**: within 7 days of receiving a report
- **Assessment**: initial severity assessment within 14 days
- **Resolution**: target fix or mitigation plan within 30 days of
  acknowledgment, depending on severity and complexity

These timelines reflect the project's current scale as a small
community project. Response times may vary, but every report will be
acknowledged and investigated.

## Disclosure Policy

We follow coordinated disclosure. Once a fix is available, we will:

1. Release the fix across affected components
2. Publish a security advisory on GitHub
3. Credit the reporter (unless they request anonymity)

We ask that reporters allow reasonable time for a fix before public
disclosure.
