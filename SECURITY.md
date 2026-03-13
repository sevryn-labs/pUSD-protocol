# Security Considerations

The protocol includes several safeguards to maintain system integrity.

## Protocol Invariants

The following invariants must always hold.

```
collateral × 100 ≥ debt × 150
```
```
totalDebt = totalSupply
```

## Economic Attacks

The protocol protects against:

- undercollateralized minting
- invalid liquidation
- debt inflation

## Privacy Attacks

Borrower positions remain private.

Observers cannot determine individual collateral or debt values.

## Liquidation Safety

Liquidation only succeeds when the collateral ratio falls below the required threshold.

Invalid liquidation attempts fail automatically.
