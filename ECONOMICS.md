# Economic Model

The pUSD protocol implements overcollateralized lending.

## Collateral Asset

Collateral is provided using the Midnight network token:

```
tNight
```

## Synthetic Asset

Borrowers mint a synthetic stablecoin:

```
pUSD
```

## Collateral Ratio

The protocol enforces a minimum collateral ratio.

```
Minimum Ratio = 150%
```

This means:

```
collateral ≥ 1.5 × debt
```

## Minting Limit

The maximum debt a user may mint is determined by their collateral.

```
maxDebt = (collateral × 100) / 150
```

Example:

```
Collateral: 1500
Maximum debt: 1000
```

## System Solvency

The protocol exposes two aggregate values.

```
totalCollateral
totalDebt
```

System solvency can be evaluated by computing:

```
totalCollateral / totalDebt
```

## Token Supply

The pUSD supply expands and contracts with debt.

```
mint → supply increases
repay → supply decreases
```

Invariant:

```
totalSupply = totalDebt
```

## Liquidation

Positions below the collateral threshold are liquidated.

Liquidators repay the debt and claim the collateral.

This ensures the protocol remains solvent during market downturns.
