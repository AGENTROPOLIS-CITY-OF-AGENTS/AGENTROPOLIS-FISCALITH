# FISCALITH Swap State Machine

A swap is price-sensitive and must carry downside constraints.

Same-chain:
```text
PLANNED -> ESTIMATED -> AUTHORIZED -> ALLOWANCE_READY -> SUBMITTED -> SETTLED
```

Cross-chain:
```text
PLANNED -> ESTIMATED -> AUTHORIZED -> SOURCE_SUBMITTED -> SOURCE_CONFIRMED
-> DESTINATION_PENDING -> DESTINATION_CONFIRMED -> SETTLED
```

PENDING is neither failure nor settlement.

## Price protection

Support explicit slippage bounds, stop limits/minimum output, maximum provider fee and maximum total fee. Provider defaults must not silently become institutional policy.

## Proofs

ProofOfQuote, ProofOfPriceProtection, ProofOfSlippage, ProofOfSourceExecution, ProofOfDestinationDelivery, ProofOfSettlement and ProofOfNetAmount.
