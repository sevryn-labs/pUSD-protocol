# Protocol Specification

This document describes the core mechanics of the pUSD lending protocol.

## Overview

pUSD is a decentralized collateralized lending system that allows users to mint synthetic stablecoins by depositing collateral.

The protocol enforces strict overcollateralization to maintain system solvency.

## Actors

The protocol involves three types of participants.

### Borrowers

Borrowers deposit collateral and mint pUSD.

They must maintain a collateral ratio above the liquidation threshold.

### Token Holders

Users who hold or transfer pUSD tokens.

They rely on the solvency guarantees of the protocol.

### Liquidators

Participants who monitor the system and liquidate undercollateralized positions.

Liquidators repay debt in exchange for seized collateral.

## Protocol Flow

```
Deposit collateral
↓
Mint pUSD
↓
Maintain collateral ratio
↓
Repay debt
↓
Withdraw collateral
```

## Public State

The protocol exposes the following values publicly:

- totalCollateral
- totalDebt
- totalSupply
- liquidationRatio
- mintingRatio

These values allow anyone to verify system solvency.

## Private State

Individual borrower positions remain private.

Private state includes:

- user collateral amount
- user debt amount

This state is stored locally and supplied to the protocol through zero-knowledge proofs.

## Protocol Invariants

The system enforces several invariants.

### Overcollateralization

```
collateral × 100 ≥ debt × 150
```

### Debt-Supply Equality

```
totalDebt = totalSupply
```

Every unit of pUSD corresponds to debt within the system.

## Token Model

pUSD functions as a transferable fungible token.

Users may:

- transfer tokens
- approve allowances
- use delegated transfers

Token transfers do not affect lending positions.

## Liquidation

Positions that fall below the collateral ratio threshold become eligible for liquidation.

Liquidators repay the outstanding debt and seize the collateral.

## System Guarantees

The protocol guarantees:

- No undercollateralized minting
- No invalid liquidation
- Verifiable solvency
- Private borrower positions
