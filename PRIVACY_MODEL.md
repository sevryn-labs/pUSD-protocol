# Privacy Model

The pUSD protocol separates public solvency verification from private borrower state.

## Public Data

The following values are visible on-chain.

- totalCollateral
- totalDebt
- totalSupply
- protocol parameters

These values allow the system to remain transparent and auditable.

## Private Data

The following values remain private.

- user collateral amount
- user debt amount
- position health

These values are never written to the public ledger.

## Zero-Knowledge Proofs

Private values are provided to the protocol through zero-knowledge witnesses.

The proof verifies that protocol rules are satisfied without revealing the private data.

Example constraint:

```
collateral × 100 ≥ debt × 150
```

The proof confirms the inequality without revealing the values of collateral or debt.

## Local State

Private position data is stored locally in the user's wallet environment.

The network never stores or broadcasts this information.

## Privacy Benefits

The protocol prevents several forms of on-chain surveillance.

- liquidation hunting
- portfolio deanonymization
- targeted financial attacks
