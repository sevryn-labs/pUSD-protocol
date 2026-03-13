# Liquidation Mechanism

Liquidation protects the protocol from undercollateralized positions.

## Liquidation Condition

A position becomes liquidatable when:

```
collateral × 100 < debt × 150
```

## Liquidator Role

Liquidators monitor the system for distressed positions.

When a position falls below the threshold, they may repay the debt and claim the collateral.

## Liquidation Flow

```
1. Liquidator identifies undercollateralized position
2. Liquidator submits liquidation transaction
3. Debt is repaid
4. Collateral is seized
```

## System Protection

The protocol verifies liquidation conditions cryptographically.

Invalid liquidation attempts fail before execution.

Healthy positions cannot be liquidated.
