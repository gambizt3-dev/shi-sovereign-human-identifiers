# SHI Security, Custody and Recovery

## Non-negotiable custody boundaries
- Generate and hold master DID keys and Layer 2 wallet signing material under the user's control; prefer device secure hardware and encrypted export.
- Never require users to enter seed phrases into the SHI setup website or publish them in GitHub, logs, memos or cloud environment variables.
- Cloud secret injection allows running code to read those secrets. Use for service credentials and limited disposable agent keys only when the threat model permits.
- Separate identity recovery material from crypto wallet seed phrases; recovering SHI must not silently grant access to savings wallets.
- Do not store raw biometric scans or templates on-chain. Device passkey verification is not proof of global uniqueness.
- Require signed, scoped, expiring agent delegation; log authorisation decisions without sensitive witnesses.
- A compromised agent seed remains dangerous after delegation revocation. Restrict funds, rotate wallet, and enforce on-chain rules where possible.

## Portable recovery kit — conceptual format
- Encrypted identity backup with authenticated encryption and documented key derivation
- DID method, resolution metadata and public key references
- Encrypted service configuration and user-owned provider migration guide
- Linked-wallet public identifiers and proofs, with revocation information
- Recovery instructions and independently stored recovery secret

Never include plaintext seeds or biometric templates in an export. Test restoring to a different provider **before** deleting the original deployment. Some DID methods cannot preserve the same DID after key or method changes; choose deliberately.

## Open security questions
- Compromise of user device, host, provider, DNS, verifier, proof store and backup
- Key rotation and lost-device recovery without central operator
- Proof privacy, correlation across chains and revocation freshness
- Biometric uniqueness error rates, appeals, consent and jurisdiction-specific restrictions
- Audited cryptographic libraries, circuit correctness, on-chain gas/fees and wallet policy enforcement

**Do not use real money or production secrets in the initial prototype.**
