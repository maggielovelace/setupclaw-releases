# Security

## Reporting a Vulnerability

If you discover a security issue in SetupClaw, please **do not** file a public GitHub issue. Instead, email **security@setupclaw.uk** with:

- A description of the vulnerability
- Steps to reproduce
- The version of SetupClaw you are running (visible in the About dialog)
- Your disclosure timeline preferences

We will acknowledge receipt within 72 hours.

## Release Integrity

Every release in this repository is:

1. **Code-signed** with an Apple Developer ID certificate.
2. **Notarized** by Apple's notary service, stapled to the `.dmg`.
3. **Integrity-checked** at auto-update time via SHA-512 hashes embedded in `latest-mac.yml`.

Users can independently verify a downloaded `.dmg` using:

```bash
codesign --verify --deep --strict --verbose=2 /Applications/SetupClaw.app
spctl --assess --type execute --verbose /Applications/SetupClaw.app
```

Both commands should report success with the expected Team ID.

## Auto-Update Trust Model

SetupClaw's auto-updater fetches release metadata directly from this public GitHub repository over HTTPS and verifies every downloaded artifact's SHA-512 hash before installing. An attacker who compromised this repository would still be blocked by the notarization check — Apple's Gatekeeper refuses to launch a `.dmg` that does not trace back to the registered Developer ID.

If you suspect a release in this repository has been tampered with, please report it via the email above immediately.
