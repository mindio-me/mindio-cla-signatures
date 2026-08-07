# mindio-cla-signatures

Auto-managed CLA signature storage for [mindio-web](https://github.com/mindio-me/mindio-web) and
[mindio-server](https://github.com/mindio-me/mindio-server), maintained by
[contributor-assistant/github-action](https://github.com/contributor-assistant/github-action).

Signing once in either repo covers both. Do not edit files in this repo by hand — the bot writes to
`signatures/version1/cla.json` automatically when a contributor signs.

## Maintainer notes: `CLA_PAT`

Both `mindio-web` and `mindio-server` hold an Actions secret named `CLA_PAT` — a GitHub fine-grained
personal access token, scoped to **Contents: Read and write** on this repo (`mindio-cla-signatures`)
only, nothing else. It's what lets their `cla.yml` workflows write `signatures/version1/cla.json` here.

- **Owner:** wufasong
- **Scope:** this repo only, Contents: Read and write
- **Set on:** both `mindio-web` and `mindio-server` as the `CLA_PAT` Actions secret
- **Expiry:** fine-grained PATs expire — check the token's expiry at
  https://github.com/settings/personal-access-tokens (look for `mindio-cla-signatures-write`)
- **On expiry:** the CLA workflow in both repos will start failing with a token/auth error instead of
  running normally. To fix: generate a new fine-grained PAT with the same scope (repo:
  `mindio-cla-signatures`, permission: Contents Read and write), then update the `CLA_PAT` secret on
  both `mindio-web` and `mindio-server` (Settings → Secrets and variables → Actions).
