# AGENTROPOLIS FISCALITH

**FISCALITH is the chain-neutral financial language for autonomous agents and institutional agentic commerce.**

FISCALITH defines financial meaning. It does not replace ATRALITH / ATG, grant authority, choose settlement rails, custody assets, or sign transactions.

## Canonical separation

- **ATRALITH / ATG** — AGENTROPOLIS agent language and communication envelope.
- **FISCALITH** — financial and economic semantics carried by ATG when agents discuss or request value movement.
- **AGENTENTITY** — persistent agent identity, state, provenance and controller relationships.
- **AEGIS** — policy, risk and authority evaluation.
- **Execution Envelope** — bounded authorized execution context.
- **AQUADUCT** — testnet provisioning, adapter certification, simulation, verification and receipt plane.
- **PAYRAIL** — approved production economic routing and settlement execution.
- **Forge** — provisioning, certification, promotion, restriction and revocation boundary.

## Core corridor

```text
AGENTENTITY
    ↓
ATRALITH / ATG
    ↓
FISCALITH financial payload
    ↓
Execution Envelope
    ↓
AEGIS
    ↓
AQUADUCT when sandbox / certification is required
    ↓
PAYRAIL when production execution is approved
    ↓
provider / rail
    ↓
Proofs + receipts
    ↓
ATG response
```

## Core semantic families

- PAY / SEND
- QUOTE / BID / OFFER
- BRIDGE
- SWAP
- UNIFIED_BALANCE
- ONRAMP / OFFRAMP
- EARN
- INVOICE
- ESCROW
- JOB
- PAYROLL
- ROYALTY / SPLIT
- BUDGET / TREASURY
- FX
- CREDIT
- COLLATERAL
- SUBSCRIPTION
- REFUND
- RECONCILE
- SETTLE

## Provider neutrality

FISCALITH never hard-codes Circle, Arc, Base, Solana, XRPL, Stellar, Hedera, Robinhood Chain, bank rails, or another provider as the language itself.

Provider-specific execution belongs behind PAYRAIL or an approved sandbox/certification adapter.

## Standing rule

> **ATRALITH tells agents how to speak. FISCALITH defines what financial meaning means. AEGIS decides whether the action is allowed. AQUADUCT proves it safely when required. PAYRAIL routes approved production value. Receipts prove what happened.**
