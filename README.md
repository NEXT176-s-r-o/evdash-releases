# evDash official Android releases

This repository is the official public distribution channel for evDash Android
APK releases.

It deliberately contains **no application source code, signing key, keystore,
customer data, diagnostic data, or internal build configuration**.

## Verify before installing

Each published GitHub Release includes:

- the signed APK;
- a `.sha256` file for that exact APK;
- concise release notes;
- a matching entry in [releases.json](releases.json).

Before installing, compare the APK SHA-256 checksum with the value shown in the
release. Only install builds published by the
[`NEXT176-s-r-o`](https://github.com/NEXT176-s-r-o) organization.

## Update channels

- [Latest release](../../releases/latest) — recommended for normal installs.
- [All releases](../../releases) — previous official builds.
- [releases.json](releases.json) — machine-readable manifest for download
  pages and update clients.

This repository is one official distribution source alongside evdash.eu. It is
not an app store, and Android may ask the owner to allow installation from their
browser or file manager.

## China availability

GitHub availability varies by network in mainland China. A regional mirror may
mirror only an APK whose filename and SHA-256 are present in this repository's
manifest; it must not rebuild or re-sign evDash.

## Reporting an issue

For app support, use the contact options in evDash or
[evdash.eu](https://www.evdash.eu/). Do not publish vehicle identifiers,
diagnostic recordings or licence codes in GitHub issues.
