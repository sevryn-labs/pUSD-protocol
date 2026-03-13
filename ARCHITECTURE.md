# System Architecture

The pUSD protocol is composed of several layers.

## Architecture Overview

```
User Interface
↓
Wallet & Local State
↓
Protocol Smart Contract
↓
Proof Generation Layer
↓
Midnight Network
```

## Client Layer

User wallets maintain private state and generate zero-knowledge proofs.

## Contract Layer

Smart contracts enforce protocol rules and maintain public state.

## Proof Layer

Zero-knowledge proofs verify protocol constraints without revealing private data.

## Network Layer

The Midnight network validates transactions and maintains the ledger.
