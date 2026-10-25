# SHI Development Roadmap

## Stage 0 — Open specification
Publish v0.1 draft, architecture, threat model, test vectors, reference licence and governance proposal.

## Stage 1 — Self-hosting
Build a mobile-first setup guide and deployment templates for a user-owned Northflank service and Cloudflare equivalent. Generate keys on-device, encrypt backups and test export/import with a stable DID.

## Stage 2 — Multichain wallet linking
Implement wallet challenge signing on Stellar Testnet and an EVM testnet; add XRPL Testnet. Avoid any requirement to bridge funds or create a SHI coin.

## Stage 3 — SHI-PAY
Create independently verifiable transaction-bound HUMAN and AGENT evidence. Implement memo references where useful and smart-contract verification where available. Include expiry, revocation and anti-replay test cases.

## Stage 4 — Agent security
Pair/revoke disposable PAI keys, manually fund separate Layer 3 wallets, enforce limits and test compromised-agent recovery.

## Stage 5 — Interoperability and personhood research
Evaluate supported Axelar message routes and direct fallback verification. Research open, privacy-respecting duplicate-detection and independent issuers; do not claim uniqueness without evidence.

## Stage 6 — Adoption
Publish SDKs, example integrations, security audits, independent conformance tests and community governance. Pursue relevant standards venues only after technical maturity.
