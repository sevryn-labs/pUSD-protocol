# pUSD Protocol Specification

Version: v0.1  
Status: Draft  
Author: Sevryn Labs

# 1. Overview

The pUSD protocol is a privacy-preserving collateralized lending system built on the Midnight Network.

The protocol allows users to deposit collateral and mint a synthetic stablecoin (pUSD) while keeping individual positions private using zero-knowledge proofs.

The system enforces strict overcollateralization to ensure solvency while exposing only aggregate system data.

# 2. Definitions

| Term | Description |
|-----|-------------|
| Collateral | Asset deposited to secure borrowed funds |
| Debt | Amount of pUSD minted by a borrower |
| Collateral Ratio | Collateral value relative to outstanding debt |
| Liquidation | Forced closure of an undercollateralized position |
| Borrower | User who deposits collateral and mints pUSD |
| Liquidator | Actor who closes unsafe positions |

# 3. Protocol Parameters

| Parameter | Value | Description |
|----------|------|-------------|
| Minimum Collateral Ratio | 150% | Minimum collateral required for borrowing |
| Collateral Asset | tNight | Native asset used as collateral |
| Synthetic Asset | pUSD | Stablecoin minted by the protocol |
| Interest Rate | 0% | No stability fee in the initial version |

# 4. System State

The protocol maintains both **public state** and **private state**.

## 4.1 Public State

Public state is stored on-chain.

| Variable | Description |
|---------|-------------|
| totalCollateral | Total collateral deposited in the system |
| totalDebt | Total outstanding protocol debt |
| totalSupply | Total supply of pUSD tokens |
| liquidationRatio | Minimum collateral ratio |

## 4.2 Private State

Private state is maintained locally by users.

| Variable | Description |
|---------|-------------|
| collateralAmount | Collateral deposited by a user |
| debtAmount | Debt minted by a user |

Private state is provided to the protocol through **zero-knowledge witnesses**.

# 5. Protocol Invariants

The protocol enforces several mathematical invariants.

## 5.1 Collateral Constraint

For every borrower position:

```
collateral × 100 ≥ debt × 150
```

This ensures a minimum collateral ratio of **150%**.

## 5.2 Supply-Debt Parity

The total supply of pUSD must equal total outstanding debt.

```
totalSupply = totalDebt
```

## 5.3 Non-Negativity

All state variables must remain non-negative.

```
collateral ≥ 0
debt ≥ 0
```

# 6. Protocol Operations

The protocol supports several core operations.

## 6.1 Deposit Collateral

Allows a user to deposit collateral into the protocol.

Effects:

```
userCollateral += amount
totalCollateral += amount
```

## 6.2 Mint pUSD

Allows a user to mint pUSD against their collateral.

Condition:

```
(collateral × 100) ≥ (debt + mintAmount) × 150
```

Effects:

```
userDebt += mintAmount
totalDebt += mintAmount
totalSupply += mintAmount
```

## 6.3 Repay Debt

Allows a borrower to repay pUSD.

Effects:

```
userDebt -= amount
totalDebt -= amount
totalSupply -= amount
```

## 6.4 Withdraw Collateral

Allows a user to withdraw previously deposited collateral.

Condition:

```
(collateral - withdrawAmount) × 100 ≥ debt × 150
```

Effects:

```
userCollateral -= withdrawAmount
totalCollateral -= withdrawAmount
```

## 6.5 Transfer pUSD

pUSD behaves as a fungible token and can be transferred between users.

Token transfers do not affect lending positions.

## 6.6 Liquidation

A position becomes liquidatable when:

```
collateral × 100 < debt × 150
```

Effects:

```
totalCollateral -= victimCollateral
totalDebt -= victimDebt
totalSupply -= victimDebt
```

# 7. Privacy Model

The protocol uses zero-knowledge proofs to protect user position data.

Private values include:

- individual collateral
- individual debt

Proofs verify protocol rules without revealing private data.

Public observers can verify solvency through aggregate values.

# 8. Security Assumptions

The protocol assumes:

- honest proof verification by the network
- correct implementation of smart contract logic
- availability of liquidation actors

Failure of these assumptions may impact protocol safety.

# 9. Limitations

The current protocol design has several limitations.

- single collateral asset
- no price oracle
- no stability fee
- no governance mechanism

These features may be introduced in future versions.

# 10. Future Extensions

Potential improvements include:

- multi-collateral support
- decentralized price oracles
- dynamic stability fees
- partial liquidations
- governance mechanisms

# 11. Status

This specification describes an **experimental research protocol** developed by Sevryn Labs.

The implementation may evolve as further research and testing is conducted.
