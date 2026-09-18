# Circle App Kit Provider Boundary

Status: canonical integration contract

## Source-derived installation facts

Circle App Kit is available as an all-in-one SDK:

```bash
npm install @circle-fin/app-kit
```

For Arc / EVM integration, the preferred initial adapter is Viem:

```bash
npm install @circle-fin/adapter-viem-v2 viem
```

Other supported adapters include:
- `@circle-fin/adapter-ethers-v6`
- `@circle-fin/adapter-solana-kit`
- `@circle-fin/adapter-circle-wallets`

Circle Wallets is server-side only.

An API key from Circle Console is:
- required for Onramp;
- optional for Swap and Earn;
- without a key, Swap and Earn run against rate limits.

## FISCALITH boundary

FISCALITH does **not** import or depend on Circle App Kit packages.

FISCALITH defines provider-neutral financial semantics such as:

- SEND
- BRIDGE
- SWAP
- UNIFIED_BALANCE
- ONRAMP
- EARN

Provider bindings live outside the language core.

```text
ATRALITH / ATG
    ↓
FISCALITH semantic intent
    ↓
AEGIS + Execution Envelope
    ↓
AQUADUCT or PAYRAIL provider adapter
    ↓
Circle App Kit
```

## Adapter ownership

### AQUADUCT

AQUADUCT owns the testnet / certification harness for Circle App Kit behavior.

Recommended initial dependency set:

```bash
npm install @circle-fin/app-kit @circle-fin/adapter-viem-v2 viem
```

Add the Solana adapter only when a test requires a Solana leg.

### PAYRAIL

PAYRAIL owns the production Circle App Kit provider adapter after certification and policy approval.

### FISCALITH

FISCALITH owns the semantic contract only.

## Secret handling

Circle API keys and wallet-provider credentials:
- MUST remain server-side;
- MUST NOT be committed;
- MUST NOT be placed in GitHub Pages source;
- MUST NOT be embedded in ATRALITH / ATG messages;
- MUST NOT be embedded in FISCALITH payloads;
- SHOULD be referenced through capability-scoped secret handles.

## Standing rule

> **SDKs implement providers. FISCALITH defines financial meaning. ATRALITH carries the message. AEGIS authorizes. AQUADUCT proves. PAYRAIL executes production value.**
