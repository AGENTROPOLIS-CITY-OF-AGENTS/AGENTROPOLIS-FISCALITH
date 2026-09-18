# FISCALITH Bridge State Machine

A bridge is a multi-step financial operation.

```text
PLANNED -> ESTIMATED -> AUTHORIZED -> SOURCE_APPROVED -> BURNED
-> ATTESTATION_PENDING -> ATTESTED -> MINT_PENDING -> SETTLED
```

Partial completion is preserved. If the burn succeeded, a later failure does not make the original bridge safe to restart from zero.

> Retry the state, not the money.

## Exact-recipient mode

Provider-signed source-fee quotes are opaque, time-bound execution artifacts. Bind the quote hash to the exact BridgeIntent, recipient, amount, source, destination, fee mode, mandate and authorization. Do not decode, modify, reconstruct or silently substitute a caller-supplied quote.

## Recovery evidence

ProofOfPartialExecution, ProofOfRecovery, ProofOfRoute, ProofOfQuote, ProofOfFeeQuote, ProofOfBalanceChange and ProofOfSettlement.
