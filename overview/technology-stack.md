---
description: >-
  Overview of the main technologies, frameworks, and infrastructure choices used
  in the system.
---

# Technology Stack

Skyline is a polyglot, multi-chain system: chain-specific logic is written natively per chain, and a Go off-chain core binds the parts into one bridge.

### Off-chain core (Go)

The bridge validator node is a single Go binary built as a Cobra CLI, bundling every off-chain role: chain-specific oracles, batcher, relayer, bridging-address manager and coordinator, and an HTTP API. State is held in **bbolt**, an embedded single-file key-value store - each stateful component owns its own bucket layout, so a validator node has no external database dependency and no shared-state coupling between operators. Metrics flow through `hashicorp/go-metrics` to **Prometheus** with optional **DataDog** tracing; logging is structured via `hclog`.

### EVM Contracts

Solidity contracts target version **0.8.24** on **Hardhat** with TypeScript tooling and solhint, built on OpenZeppelin's upgradeable libraries behind **UUPS proxies**. Bridge smart contracts hold the settlement-side logic while gateway smart contracts covers the gateway side and verifies aggregate signatures via `bls-bn254`.

### Cardano validators

Cardano validators are written in **Helios** and compiled to Plutus/UPLC through a Node build script with parameter injection, tested with vitest — an NFT-gated minting validator that ties minting rights to continued NFT ownership.

### Solana program

The Solana side is a single upgradeable Anchor program written in **Rust 1.89** against **Anchor 0.32.1**, `anchor-spl`, and **Metaplex `mpl-token-metadata` 5.1.1**. Builds are reproducible through an Ubuntu 24.04 Docker image.

### Web layer

The frontend is **React 18 + TypeScript,** Redux Toolkit, Sentry, integrating Cardano wallets via CIP-30, Phantom on Solana and MetaMask on EVM. The backend API is **NestJS** with **PostgreSQL -** the only relational database in the system - plus JWT auth, cache-manager, cron scheduling, Winston logging and Swagger docs. A companion Go service, `cardano-api`, handles Cardano transaction assembly.

Across all repositories configuration in JSON-driven. Testing is consistently run using CI runs on Github Actions and all repositories are gated with code quality checks for linting and formatting.

