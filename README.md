# RexLink Wallet

![Status](https://img.shields.io/badge/status-MVP%20docs-blue)
![Platform](https://img.shields.io/badge/platform-Expo%20%2F%20React%20Native-000020?logo=expo)
![Web3](https://img.shields.io/badge/web3-wallet%20linking-7C3AED)
![Security](https://img.shields.io/badge/security-non--custodial-orange)

**RexLink Wallet** is the mobile wallet companion for the CoinRex ecosystem. It is designed for wallet pairing, remote authentication, human-readable approval requests, reward claim approvals, and wallet-linked actions across the CoinRex platform.

This repository is reserved for the RexLink mobile app and its documentation. The main CoinRex platform backend remains in:

```text
https://github.com/CoinRex-net/coinrex-platform
```

## Purpose

RexLink gives CoinRex users a dedicated mobile surface for actions that should be reviewed from a wallet context before approval.

| Area | Role |
| --- | --- |
| Wallet pairing | Connect a mobile wallet session to CoinRex through pairing codes or QR flows |
| Remote approvals | Review approval requests before sensitive wallet-linked actions continue |
| Reward claims | Approve CoinRex reward claim requests from a trusted mobile session |
| Session control | View active sessions and revoke access when needed |
| Web3 readiness | Support wallet-aware review eligibility and future on-chain actions |

## Planned Stack

| Layer | Technology |
| --- | --- |
| Mobile app | Expo, React Native |
| Web3 utilities | ethers |
| Local security | Expo SecureStore, local authentication |
| QR flows | Expo Camera, QR payload handling |
| Realtime | CoinRex WebSocket approval channels |
| Backend integration | CoinRex RexLink APIs under `api/rex-signer/` |

## Repository Scope

This repository should contain:

- RexLink mobile application source.
- Expo configuration such as `app.json` and `eas.json`.
- Mobile assets, screens, storage helpers, wallet helpers, and theme files.
- RexLink-specific setup, security, release, and API integration documentation.

This repository should not contain:

- CoinRex platform PHP source code.
- Production `.env` files, private keys, seed phrases, API tokens, or keystores.
- Generated folders such as `node_modules/`, `.expo/`, or build artifacts.
- Database dumps, runtime uploads, logs, or backend-only scripts.

## Local Development

After the mobile app source is added:

```bash
npm install
npx expo start
```

On Windows PowerShell, if npm script execution is blocked, use:

```bash
npx.cmd expo start
```

For Android emulator testing against a local CoinRex platform install, the API base URL can use:

```text
http://10.0.2.2/coinrex
```

For browser or local network testing:

```text
http://localhost/coinrex
```

## CoinRex Integration

RexLink connects to CoinRex through the platform's wallet-linking and approval endpoints.

| Capability | CoinRex API group |
| --- | --- |
| Pairing sessions | `api/rex-signer/create_pairing.php`, `complete_pairing.php`, `pairing_qr.php` |
| Session management | `api/rex-signer/sessions.php`, `revoke_session.php` |
| Approval requests | `api/rex-signer/create_approval_request.php`, `approval_requests.php`, `approval_decision.php` |
| Realtime auth | `api/rex-signer/realtime_auth.php` |
| Claim approvals | `api/rex-signer/create_claim_approval.php`, `complete_claim_tx.php` |
| Review eligibility | `api/review-eligibility/wallet_nonce.php`, `verify_wallet.php`, `check.php` |

## Documentation

| Document | Description |
| --- | --- |
| [Repository Setup](docs/REXLINK_REPOSITORY_SETUP.md) | Publishing, branch rules, secrets, and first release checklist |

## Security Principles

- RexLink should never ask users to paste production seed phrases into untrusted surfaces.
- Secrets, private keys, keystores, and production API credentials must stay out of Git.
- Approval screens should show human-readable action details before the user accepts.
- Sessions should be revocable from both wallet and platform contexts.
- Sensitive local state should use secure mobile storage and device authentication where appropriate.

## Current Status

This repository currently contains documentation for the RexLink mobile wallet repository. Mobile app source can be added in a separate code commit after review.
