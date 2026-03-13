# pUSD Protocol

**pUSD** is a privacy-preserving collateralized lending protocol built on the Midnight Network.

The protocol enables users to deposit collateral and mint a synthetic stablecoin while keeping individual borrowing positions private through zero-knowledge proofs.

Unlike traditional DeFi lending systems where all user positions are visible on-chain, pUSD separates **systemic solvency verification** from **individual financial privacy**.

## Overview

The protocol follows a simple model:

```
Deposit collateral → Mint pUSD → Maintain collateral ratio → Repay → Withdraw collateral
```

All positions are **overcollateralized** and enforced through **mathematical constraints embedded in zero-knowledge circuits**.

## Core Properties

### Privacy

Individual borrower positions are never revealed on-chain.

Private data:

- Collateral deposited by a user
- Debt owed by a user
- Position health

Public data:

- Total collateral in the system
- Total debt in the system
- Total supply of pUSD

This ensures that the protocol remains **auditable and solvent** while protecting user privacy.

### Verifiable Solvency

The protocol exposes global aggregates:

```
totalCollateral
totalDebt
totalSupply
```

Any observer can verify system health by computing:

```
system collateral ratio = totalCollateral / totalDebt
```

### Zero-Knowledge Enforcement

All lending rules are enforced through zero-knowledge proofs.

A user's device generates a proof verifying that the position satisfies protocol constraints without revealing the private values.

---

## Protocol Model

The core invariant enforced by the protocol:

```
collateral × 100 ≥ debt × 150
```

This ensures a **minimum collateral ratio of 150%**.

## Key Components

The system consists of several layers:

```
User Interface
↓
Client Wallet & Private State
↓
Protocol Smart Contract
↓
Proof Generation Layer
↓
Midnight Network
```

## Documentation

Detailed documentation can be found in the following files:

| Document | Description |
|--------|-------------|
| PROTOCOL.md | Technical protocol specification |
| ECONOMICS.md | Economic model and collateral rules |
| PRIVACY_MODEL.md | Privacy architecture |
| LIQUIDATION.md | Liquidation mechanics |
| ARCHITECTURE.md | System architecture |
| SECURITY.md | Security considerations |
| ROADMAP.md | Future protocol improvements |


## Whitepaper

The formal protocol design is described in the whitepaper:

```
WHITEPAPER.pdf
```

## Status

This protocol is currently **experimental research software**.

The repository documents the protocol design and research conducted by **Sevryn Labs**.

## License

MIT License
