# SHI Protocol v0.1 — Working Draft

**Status: proposal only; no normative ecosystem deployment exists yet.**

## Roles
- **Holder:** human who controls SHI identity keys and recovery.
- **Verifier:** independent service that checks cryptographic evidence.
- **Issuer:** optional independent provider that attests a specific claim (e.g. personhood); self-issuance alone cannot establish uniqueness.
- **PAI / AI Handler:** separate agent identifier and signing key with delegated authority.
- **Payment adapter:** network-specific implementation for XRPL, Stellar, EVM, etc.

## Identifier model
Use an existing interoperable DID method selected for key rotation, independent resolution and updateable service endpoints. Do not assume an arbitrary `did:shi:` method is registered or resolvable. A wallet address is a separately linkable account, not automatically a DID.

## Wallet-link protocol (design requirements)
A wallet owner signs a domain-separated, one-use challenge binding DID, wallet address, chain/network ID, intended relying party, nonce, issued-at and expiry. Verify the signature using the target network's actual signing semantics. Publish the minimal verifiable association needed, with consent and revocation support. Do not derive a ZKP from a seed phrase or publish a seed hash.

## Proposed payment-attestation envelope
Illustrative logical schema (NOT final wire format):

```json
{
  "version": "shi-pay/0.1-draft",
  "type": "HUMAN_OR_AGENT",
  "chain_id": "network-specific-id",
  "transaction_binding": "canonical-transaction-digest",
  "proof_reference": "content-addressed-or-resolvable-proof",
  "delegation_reference": "optional-for-agent",
  "expires_at": "ISO-8601-timestamp",
  "nonce": "unique-random-value"
}
```

No real proof is valid solely because an envelope says HUMAN or AGENT. A verifier must independently check proof validity, credential trust, signing key, transaction binding, replay protection, revocation, and any applicable delegation constraints. Privacy-preserving proof systems must explicitly define public inputs, hidden witness, circuit and verifier keys.

## Human versus AI agent
- **HUMAN** means a valid credential/key authorisation, not proof that a unique person physically clicked a button at payment time.
- **AGENT** means a separate signing key acted under an unexpired, non-revoked delegation. Verify limits and network-specific enforceability.
- **UNVERIFIED** is a verifier's conclusion, not a self-declared trustworthy memo.

## Chain adapters
- **XRPL:** Memo may reference evidence. Ledger validates ordinary signatures and transaction rules, not SHI claims by default.
- **Stellar:** Memo may reference evidence; Soroban contracts can implement explicit verification and constrained authorisation where supported.
- **EVM:** Smart contracts/account abstraction may implement proof verification and spending policies.
- **Axelar:** Optional supported cross-chain messaging; do not assume native XRPL, Stellar and every EVM chain share a universally supported route.

## Standardisation approach
Public versioned draft, permissively licensed reference code, test vectors, interoperability tests, security review, independent implementers, then standards engagement. This document is not an ISO, W3C or IETF standard.
