# Circle App Kit Provider Contract

Circle App Kit is a provider implementation behind FISCALITH and PAYRAIL.

Supported provider capabilities currently include Send, Bridge, Swap, Unified Balance, Onramp and Earn.

## Provider boundary

- FISCALITH defines meaning.
- AEGIS authorizes.
- 54T preserves signer, secret, capability and intent-integrity boundaries.
- AQUADUCT proves new or changed adapters on testnet/sandbox.
- PAYRAIL selects an approved production provider and route.
- Circle App Kit executes provider-specific mechanics.

## Dynamic support discovery

Do not hard-code Circle's evolving chain/capability matrix as language canon. Use provider discovery such as `getSupportedChains()` where available and maintain certified snapshots only for compatibility testing.

## Signer policy

Production agents never receive raw private keys.

Preferred production paths are external signers, controlled wallets, user-approved challenge flows, HSM/MPC/custody systems, or scoped smart-account/session capabilities.

Raw-key adapters are test/local-only behind AQUADUCT and disabled by default.

## Gas policy

Gas sponsorship/abstraction is preferred wherever supported. Unsupported sponsorship is an explicit route constraint, not a silent requirement that an agent hold native gas.
