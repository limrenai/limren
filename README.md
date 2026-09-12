# Limren

Limren is an execution-control layer for AI agents that perform mutating operations against external systems.

This repository contains the Limren execution core.

## Status

Early development.

The first implementation is intentionally narrow: one provider, one mutating action, and one handwritten action contract.

## Execution model

```text
Agent
  ↓
Intent
  ↓
Dependency binding
  ↓
Decision
  ↓
Commit
  ↓
Provider
  ↓
Verification
```

## Core invariants

1. Protected mutations are executed from validated Limren intents, not directly from raw agent tool calls.

2. No strict commit without a target-enforced precondition.

If the target system cannot enforce the required condition atomically, Limren must report a weaker guarantee or refuse the strict commit.

## Repository structure

```text
limren/
├── limren/          # execution core
├── contracts/       # action contracts
├── docs/            # architecture and design specifications
├── tests/           # tests and failure scenarios
├── pyproject.toml   # Python project configuration
├── LICENSE
└── README.md
```

Start with [`docs/execution-core.md`](docs/execution-core.md) to understand the execution model.

## License

Apache License 2.0.
