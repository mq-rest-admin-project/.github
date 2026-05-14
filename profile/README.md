# mq-rest-admin

**Typed wrappers for the IBM MQ administrative REST API across five
programming languages.**

mq-rest-admin provides idiomatic client libraries for the IBM MQ 9.4
`runCommandJSON` REST endpoint. Each language port shares a common API
design: consistent method signatures, automatic attribute name
translation between language conventions and native MQSC parameter
names, and typed responses.

This is an independent community project, not an IBM product.

---

## Language ports

| Repository | Language | Package |
|---|---|---|
| [mq-rest-admin-python](https://github.com/mq-rest-admin-project/mq-rest-admin-python) | Python | pymqrest |
| [mq-rest-admin-java](https://github.com/mq-rest-admin-project/mq-rest-admin-java) | Java | mq-rest-admin |
| [mq-rest-admin-go](https://github.com/mq-rest-admin-project/mq-rest-admin-go) | Go | mqrest |
| [mq-rest-admin-ruby](https://github.com/mq-rest-admin-project/mq-rest-admin-ruby) | Ruby | mq_rest_admin |
| [mq-rest-admin-rust](https://github.com/mq-rest-admin-project/mq-rest-admin-rust) | Rust | mq-rest-admin |

## Supporting repos

| Repository | Purpose |
|---|---|
| [mq-rest-admin-common](https://github.com/mq-rest-admin-project/mq-rest-admin-common) | Shared documentation fragments |
| [mq-rest-admin-dev-environment](https://github.com/mq-rest-admin-project/mq-rest-admin-dev-environment) | Dockerized IBM MQ instance for integration testing |

## Shared design

All language ports follow the same API structure:

- Every MQSC command exposed by `runCommandJSON` has a corresponding
  typed method
- Attribute names are automatically translated between language
  conventions (e.g., `snake_case` in Python, `camelCase` in Java) and
  native MQSC parameter names
- Typed request and response objects — no raw dictionaries or untyped
  maps
- Consistent error handling across all ports

---

## Contributing

Contributions are welcome. See the
[contributing guidelines](https://github.com/mq-rest-admin-project/.github/blob/develop/CONTRIBUTING.md)
for development setup, workflow, and the AI contributor identity model.

---

## Author

Built by [Phillip Moore](https://github.com/wphillipmoore) — 35 years
of infrastructure engineering, including extensive work with IBM MQ.
More at
[The Infrastructure Mindset](https://the-infrastructure-mindset.ghost.io).
