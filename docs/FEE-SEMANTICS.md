# FISCALITH Fee Semantics

Fees are first-class financial semantics.

A financial intent may carry fee classes including application fee, protocol fee, forwarding fee, network gas fee, provider fee, vault fee, withdrawal fee, FX spread, slippage, custody fee, onramp fee and offramp fee.

## Pre-execution rule

```text
intent -> estimate -> FeeQuote[] -> AEGIS thresholds -> 54T integrity binding -> execute
```

The principal must be able to see and authorize the full debit, not only the nominal transfer amount.

## Application monetization

An application fee may be expressed only when the selected provider supports it and the fee:
- is disclosed before authorization;
- has an approved recipient;
- stays inside mandate and policy limits;
- participates in balance sufficiency checks;
- is included in reconciliation and receipts;
- never overrides route selection in conflict with the principal's constraints.

Provider revenue-share formulas are adapter facts, not universal FISCALITH rules.

## Proofs

ProofOfFeeQuote, ProofOfFeeAuthorization, ProofOfFeeCollection, ProofOfNetAmount and ProofOfRevenueShare.
