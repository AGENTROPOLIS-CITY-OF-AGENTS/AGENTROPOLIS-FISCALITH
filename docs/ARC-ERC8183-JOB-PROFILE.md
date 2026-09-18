# Arc ERC-8183 Job Profile

Status: Arc testnet reference profile

## Purpose

Map ERC-8183 agentic-commerce jobs into provider-neutral FISCALITH job semantics without making Arc or ERC-8183 the definition of agent work.

FISCALITH remains the financial language. ERC-8183 is an execution/escrow adapter.

## Arc testnet reference

Current Arc documentation identifies the ERC-8183 AgenticCommerce reference implementation on Arc Testnet as:

`0x0747EEf0706327138c69792bF28Cd525089e4583`

This address is testnet-scoped and MUST NOT be treated as a mainnet constant.

The Arc testnet USDC ERC-20 interface used by the quickstart is:

`0x3600000000000000000000000000000000000000`

Network constants must be re-verified against current official Arc documentation before use.

## Role mapping

| ERC-8183 | FISCALITH / AGENTROPOLIS |
| --- | --- |
| client | principal / purchaser / requesting AGENTENTITY |
| provider | service-performing AGENTENTITY or governed provider |
| evaluator | configured verifier / evaluator |
| job | FISCALITH.JOB |
| budget | FISCALITH.BUDGET |
| escrow funding | FISCALITH.ESCROW.FUND |
| deliverable hash | ProofOfWork input |
| completion | outcome decision + settlement trigger |
| rejected / expired | refusal / failure / expiry evidence |

## Lifecycle

```text
ATG.REQUEST
  -> FISCALITH.JOB.CREATE
  -> AEGIS + Execution Envelope
  -> ERC-8183 createJob
  -> provider sets budget
  -> client approves + funds escrow
  -> provider submits deliverable hash
  -> evaluator evaluates
  -> complete / reject / expire
  -> settlement evidence
  -> ATG.RECEIPT
```

Reference lifecycle states:

```text
OPEN -> FUNDED -> SUBMITTED -> COMPLETED
                           \-> REJECTED
OPEN/FUNDED/SUBMITTED      \-> EXPIRED
```

## FISCALITH job object

A provider-neutral job intent SHOULD preserve:

- job_intent_id
- client AGENTENTITY reference
- provider AGENTENTITY reference
- evaluator reference
- mandate_ref
- execution_envelope_ref
- description commitment
- deliverable commitment rules
- budget asset and amount
- expiration
- escrow policy
- dispute / rejection policy
- required proofs
- settlement requirements
- provider adapter

## Proof mapping

ERC-8183 lifecycle evidence can contribute to:

- ProofOfAuthority
- ProofOfWork
- ProofOfOutcome
- ProofOfExecution
- ProofOfSettlement
- ProofOfSLA
- ProofOfFiscalDiscipline

A `Completed` contract state proves that the configured evaluator completed the onchain lifecycle. It does not independently prove universal correctness or fitness.

## Evaluator policy

The Arc quickstart permits the client to also act as evaluator.

AGENTROPOLIS MAY allow that for low-risk test flows. Higher-risk or institutional profiles SHOULD be able to require an independent evaluator, dual approval, or external verifier according to AEGIS policy.

## Security invariants

- An ERC-8183 job cannot enlarge an agent's mandate.
- Escrow funding requires approved financial authority.
- Deliverable hashes are evidence commitments, not the deliverable itself.
- Completion cannot silently promote AGENTENTITY authority.
- Settlement does not itself transfer AGENTENTITY ownership.
- Wallet keys and Circle entity secrets never enter ATG or FISCALITH payloads.
- All consequential state transitions require receipts.
