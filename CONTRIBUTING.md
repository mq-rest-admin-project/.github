# Contributing to mq-rest-admin

Thank you for your interest in contributing. This document covers
everything you need to get started.

## How the project works

mq-rest-admin provides typed wrappers for the IBM MQ administrative
REST API across five programming languages. Each language port lives in
its own repository with its own release lifecycle, sharing a common API
design and consistent method signatures.

| Repository | Language | Description |
|---|---|---|
| [mq-rest-admin-python](https://github.com/mq-rest-admin-project/mq-rest-admin-python) | Python | pymqrest — Python wrapper |
| [mq-rest-admin-java](https://github.com/mq-rest-admin-project/mq-rest-admin-java) | Java | Java wrapper |
| [mq-rest-admin-go](https://github.com/mq-rest-admin-project/mq-rest-admin-go) | Go | Go wrapper |
| [mq-rest-admin-ruby](https://github.com/mq-rest-admin-project/mq-rest-admin-ruby) | Ruby | Ruby wrapper |
| [mq-rest-admin-rust](https://github.com/mq-rest-admin-project/mq-rest-admin-rust) | Rust | Rust wrapper |
| [mq-rest-admin-common](https://github.com/mq-rest-admin-project/mq-rest-admin-common) | — | Shared documentation fragments |
| [mq-rest-admin-dev-environment](https://github.com/mq-rest-admin-project/mq-rest-admin-dev-environment) | — | Dockerized MQ test environment |

File issues on the specific language repo. If you're unsure which repo
is relevant, pick the closest match and the maintainer will route it.

## Development setup

### Prerequisites

- **Docker** — required for running validation and integration tests.
  All linting, type checking, and testing runs inside dev containers.
- **[uv](https://docs.astral.sh/uv/)** — Python package manager, used
  to install VERGIL's host-side CLI tools.
- **Language-specific toolchains** — each language port has its own
  development prerequisites (e.g., Go toolchain for mq-rest-admin-go,
  JDK for mq-rest-admin-java). See the individual repo's README for
  details.

### Install the tooling

```bash
uv tool install --python 3.14 \
  'vergil-tooling @ git+https://github.com/vergil-project/vergil-tooling@v2.0'
```

This installs the `vrg-*` CLI tools (`vrg-commit`, `vrg-submit-pr`,
`vrg-validate`, `vrg-docker-run`, and others) on your host.

### Claude Code hook guard

Each repo includes a `.claude/hooks/guard.sh` PreToolUse hook that
blocks raw `git` and `gh` commands in AI agent sessions — all
operations must go through the `vrg-git` / `vrg-gh` wrappers.

## Workflow

All repositories use `develop` as the integration branch.

1. **Branch from `develop`.**
   Use the naming convention `feature/<issue>-<slug>` or
   `chore/<issue>-<slug>`, where `<issue>` is the GitHub issue number.

2. **Commit with `vrg-commit`.**
   This enforces conventional commit format, branch policy, and
   co-author attribution. Raw `git commit` is blocked by the
   pre-commit hook.

3. **Validate locally.**
   ```bash
   vrg-docker-run -- uv run vrg-validate
   ```
   This runs the full validation pipeline inside a dev container.
   Language-specific checks (lint, typecheck, test) run automatically
   based on each repo's `primary-language` setting in `vergil.toml`.
   The same checks run in CI.

4. **Submit a PR with `vrg-submit-pr`.**
   This creates a standards-compliant pull request linked to the
   issue.

5. **Wait for review.**
   All PRs require human approval and passing CI before merge.

## Integration testing

The [mq-rest-admin-dev-environment](https://github.com/mq-rest-admin-project/mq-rest-admin-dev-environment)
repo provides a Dockerized IBM MQ instance for integration testing.
Language ports with `integration-tests = true` in their `vergil.toml`
run tests against a real MQ instance in CI. See the dev-environment
repo's README for setup instructions when running integration tests
locally.

## For contributors using AI tools

mq-rest-admin welcomes AI-assisted contributions under a clear
accountability model.

### Identity

Each contributor who uses AI tools creates a dedicated
`<username>-agent` GitHub account for AI-assisted development. This
is a real GitHub account — not a bot, not a shared service account.
One agent identity per human, regardless of which AI tool or model
you use.

- **Agent identity** (`<username>-agent`): used for all AI-assisted
  commits and PRs
- **Human identity** (`<username>`): used for reviews, approvals,
  and merges

### Accountability

You are accountable for everything your agent produces. "The AI did
it" is not a defense. When you submit a PR from your agent account,
you are asserting that you reviewed the work, understand it, and take
responsibility for it.

### In practice

- All AI-assisted work is committed under the agent identity with
  a `Co-Authored-By` trailer
- All reviews and approvals are performed under your human identity
- At 2+ human contributors, cross-human review is required — you
  cannot approve your own agent's PRs
- The specific AI tool and model used are recorded in commit metadata
  for auditing, but the security boundary is human vs. not-human

## For contributors not using AI

Standard open-source contribution model:

1. Fork the repository
2. Create a feature branch
3. Make your changes and validate locally
4. Open a pull request

The same quality bar applies to all contributions regardless of how
they were produced. PRs require human approval from an org member and
passing CI.

## What to expect from review

- **Human approval required.** Every PR is reviewed and approved by a
  human before merge.
- **CI must pass.** The full validation pipeline runs on every PR.
  If CI fails, the PR cannot merge.
- **At 2+ contributors**, cross-human review is enforced: the
  reviewer must be a different human than the one who directed the
  work.
- **Feedback is constructive.** We review code, not people.

## Template override convention

This organization uses a shared `.github` repository for default issue
and PR templates. GitHub's inheritance for template directories is
all-or-nothing: if a repo has any file in its own
`.github/ISSUE_TEMPLATE/` directory, it gets none of the org defaults
for that directory. To customize templates for a specific repo, provide
the complete set in that repo's directory. Standalone files
(CONTRIBUTING.md, SECURITY.md, etc.) inherit independently on a
per-file basis.

## License

All mq-rest-admin repositories are licensed under
[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html). By
contributing, you agree that your contributions will be licensed under
the same terms.

This is an independent community project, not an IBM product.
