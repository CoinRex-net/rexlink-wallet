# RexLink Repository Setup Guide

This guide defines how the `CoinRex-net/rexlink-wallet` repository should be maintained as the dedicated RexLink mobile wallet repository.

The main CoinRex platform repository is:

```text
https://github.com/CoinRex-net/coinrex-platform
```

The RexLink wallet repository is:

```text
https://github.com/CoinRex-net/rexlink-wallet
```

## Repository Identity

| Field | Value |
| --- | --- |
| GitHub organization | `CoinRex-net` |
| Repository name | `rexlink-wallet` |
| App name | RexLink Wallet |
| Primary purpose | Mobile wallet pairing and approval companion for CoinRex |
| Primary stack | Expo, React Native, ethers |
| Recommended visibility | Private during MVP, public only after security review |

## Repository Purpose

RexLink is the CoinRex wallet-linking and approval companion app. This repository should contain:

- Expo / React Native mobile application code.
- RexLink wallet UI, session pairing, approval request screens, and wallet activity views.
- Mobile configuration files such as `app.json`, `eas.json`, and `metro.config.js`.
- Mobile-specific assets.
- Mobile storage, theme, component, and wallet helpers.
- App-level documentation and mobile setup instructions.

This repository should not contain:

- CoinRex platform PHP source code.
- `.env` files or production secrets.
- Private keys, seed phrases, keystores, or API tokens.
- Generated dependency folders such as `node_modules/`.
- Expo cache folders such as `.expo/`.
- Backend database dumps, uploads, logs, or platform runtime files.

## Recommended Initial App Import

When the mobile app source is ready to publish, import only the RexLink mobile files:

```text
assets/
src/
App.js
app.json
eas.json
index.js
LICENSE
metro.config.js
package.json
package-lock.json
README.md
```

Keep these local/generated folders out of Git:

```text
.expo/
.npm-cache/
node_modules/
```

## Recommended `.gitignore`

```gitignore
node_modules/
.expo/
.npm-cache/
dist/
build/
*.jks
*.keystore
.env
.env.*
npm-debug.log*
yarn-debug.log*
yarn-error.log*
```

## Branch Rules

For the MVP stage:

- Use `main` as the protected release branch.
- Require pull requests before merging.
- Require at least one approving review.
- Require status checks once CI is added.
- Block force pushes.
- Block deletion of the `main` branch.

## Suggested GitHub Topics

```text
coinrex
rexlink
wallet
expo
react-native
web3
ethers
mobile-app
```

## Suggested Secrets

Do not commit secrets. Add future build and deployment values through GitHub Actions secrets or Expo/EAS secrets.

Possible future secret names:

```text
EXPO_TOKEN
EAS_PROJECT_ID
ANDROID_KEYSTORE_BASE64
ANDROID_KEYSTORE_PASSWORD
ANDROID_KEY_ALIAS
ANDROID_KEY_PASSWORD
COINREX_API_BASE_URL
```

## First Code Release Checklist

- Confirm no backend platform code is included.
- Confirm no `.env`, private key, seed phrase, API token, keystore, or production URL is committed.
- Confirm `.gitignore` excludes `.expo/`, `.npm-cache/`, `node_modules/`, and build artifacts.
- Run `npm install` or `npm ci` successfully.
- Run `npx expo start` and open the app in Expo Go or an emulator.
- Test local CoinRex API base URL configuration.
- Review wallet creation, restore, pairing, session, claim approval, and settings screens.
- Update repository description and topics.
- Add branch protection after the first code push.
- Keep the main platform README pointing to this repository once RexLink source is live.

## Platform Link Back

The CoinRex platform README should point users here for the mobile wallet app:

```text
RexLink wallet app lives in https://github.com/CoinRex-net/rexlink-wallet.
```

That keeps the platform repository focused on backend, APIs, Web3 contracts, and realtime services while RexLink evolves as a mobile app with its own releases.
