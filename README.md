# SHI — Sovereign Human Identifiers

> **You don't register your identity with us. We teach you how to own it.**

**Status: exploratory architecture and proposed open protocol v0.1 — not a deployed identity network, audited wallet, accepted standard, or proof-of-personhood system.**

SHI is a proposed self-sovereign identity toolkit and open interoperability protocol. The SHI website is **glue**: an independent guide and open-source setup assistant that helps people create, host, protect, export and recover their own identities. SHI must not become a central identity custodian or require a SHI-operated service to remain functional.

## Principles

1. **User-owned keys and hosting.** Each person chooses their own hosting provider (for example Northflank or Cloudflare), deploys an independently usable identity service and controls recovery.
2. **Portable identity.** Export encrypted records, move between providers and preserve the same DID where the chosen DID method supports updates and key rotation. A provider migration must not require a new identity.
3. **Open verification.** Publish formats, test vectors and verifiers so any compatible application can verify proofs without asking SHI for permission.
4. **Multichain.** A single SHI can link wallets on Stellar, XRPL, EVM and other networks using signed challenges. Axelar may relay messages where supported, but must not be a required identity dependency.
5. **Human and AI payments.** Standardise transaction-bound, independently verifiable human-authorised and agent-delegated payment attestations. Ordinary crypto transactions remain possible without SHI.
6. **Privacy by default.** Never publish biometric templates, seed phrases, permanent tracking identifiers or private witnesses on public chains. Avoid stable public identity references in every payment.
7. **Honest personhood claims.** Device biometrics prove local user verification, not uniqueness. Proof of unique personhood requires an independently assessed enrolment/duplicate-detection scheme, consent, appeal and privacy review.

## Three security layers

| Layer | Purpose | Key rule |
| --- | --- | --- |
| 1 — Savings Vault | Separate manual hot/cold wallets | No AI access or automatic refill |
| 2 — SHI Identity & Spending | DID, device biometric/passkey access, encrypted identity keys, user-controlled spending wallet, ZKP authorisations | Do not expose unrestricted wallet seeds or identity keys to the cloud application |
| 3 — AI Handler / PAI | Disposable independent wallet and automated signer | Manually funded from layer 1 or 2, limited permissions, replaceable and revocable |

A revoked SHI agent delegation **does not invalidate a stolen layer-3 seed**. Keep the layer-3 balance small and enforce restrictions at the signer and/or smart-contract layer when possible.

## Proposed enrolment and migration journey

1. Visit an open-source SHI setup site; choose a hosting provider and create **your own** provider account.
2. Deploy the user-owned service using a documented template; configure service credentials and secrets.
3. Generate identity keys **locally** on the user's device, protected by hardware-backed mechanisms/passkeys where possible. Create an encrypted portable backup and independent recovery method.
4. Create a DID using a method with documented resolution, rotation and endpoint-update support. Publish only necessary public verification data.
5. Optionally link a blockchain wallet by signing a fresh, domain-separated, expiring challenge. Never upload a seed phrase to the setup website.
6. Optionally enrol with a separate personhood credential issuer and generate privacy-preserving proofs for supported claims.
7. Optionally authorise a PAI AI Handler with explicit key, scope, budget, expiry, replay protection and revocation.
8. Export the encrypted identity package, restore to a second host and verify the **same DID** and linked authorisations still resolve. Remove the old host's access.

**Cloud secrets warning:** environment secrets are visible to authorised running workloads; they are not a zero-knowledge vault. Store service credentials there, not unrestricted layer-2 seed phrases. Use client-side encryption and carefully designed signing custody.

## Proposed SHI-PAY v0.1

Two authorisation classes:
- **HUMAN:** evidence that a payment was authorised by a wallet/credential controlled by an SHI holder.
- **AGENT:** evidence that a distinct AI Handler key was delegated narrowly scoped authority by an SHI holder.

A verifier must validate the proof/signature, trusted verification keys, delegated scope, revocation state, expiry, network/chain ID, wallet, recipient, amount, nonce and transaction binding. Proofs must not be replayable. A valid SHI key does **not** by itself establish a unique biological human.

XRPL/Stellar memos can carry compact proof **references or hashes**, not automatically validated identity proofs. The verifier must retrieve and verify referenced data; transaction memos alone do not enforce spending restrictions. On-chain verification/enforcement requires appropriate smart contracts or protocol-specific mechanisms. ZKPs are optional: wallet ownership is often proven more simply by digital signatures.

## Reference architecture

- **Identity:** W3C-compatible DID documents and verification methods; credential standards where appropriate.
- **Private runtime:** local key generation and ZKP witness handling; no central SHI custody.
- **Self-hosted coordinator:** user-owned Northflank/Cloudflare/other deployment; encrypted backup, DID endpoint and optional proof verification.
- **Payment adapters:** Stellar/Soroban, XRPL and EVM adapters, independently testable.
- **Interoperability:** Axelar messaging where actual supported routes exist; direct verification fallback.
- **Uniqueness:** separate open research track. No claim of worldwide duplicate-free enrolment until a credible independent mechanism is implemented and tested.

## Initial milestones

1. Publish protocol draft, threat model, privacy model and independently implementable test vectors.
2. Create a locally generated DID and encrypted recovery kit.
3. Deploy to one cloud, migrate to another, and demonstrate stable DID resolution.
4. Link a Stellar Testnet and an EVM Testnet wallet with signed challenges.
5. Prove a human-authorised testnet payment and a delegated AI Handler testnet payment.
6. Revoke the agent and demonstrate rejection by an SHI verifier; separately test contract-enforced spending restrictions.
7. Add XRPL memo proof references and third-party verification.
8. Investigate personhood and duplicate enrolment without centralising biometric ownership.
9. Seek independent security review and external implementers before claiming standardisation.

## Repository structure

- [Protocol draft](docs/SHI-PROTOCOL-v0.1.md)
- [Security and recovery](docs/SECURITY-AND-RECOVERY.md)
- [Roadmap](docs/ROADMAP.md)

**SHI is independent of MONK, The Easy Trade and SOVRA.** No token issuance is required.
