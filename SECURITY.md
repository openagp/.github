# Security policy

OpenAGP is a **signed** protocol — its security guarantees rest on correct cryptography and faithful canonicalization. Bugs in those areas matter even when the surrounding code looks fine. We take security reports seriously and will respond promptly.

## Reporting a vulnerability

**Do not file a public issue.** Public disclosure before a fix is available can put downstream users (vendors, planes, customers) at risk.

Use **GitHub Private Vulnerability Reporting** on the affected repository:

1. Go to the repo's **Security** tab.
2. Click **Report a vulnerability**.
3. Fill in the form. The disclosure is visible only to project maintainers until we coordinate a release.

Direct links:

- [openagp/spec](https://github.com/openagp/spec/security/advisories/new)
- [openagp/sdk-python](https://github.com/openagp/sdk-python/security/advisories/new)
- [openagp/sdk-typescript](https://github.com/openagp/sdk-typescript/security/advisories/new)
- [openagp/cts](https://github.com/openagp/cts/security/advisories/new)
- [openagp/registry](https://github.com/openagp/registry/security/advisories/new)
- [openagp/examples](https://github.com/openagp/examples/security/advisories/new)

If GitHub is unavailable to you, email **security@securezeron.com** (Zeron, the current steward). Encrypt with the PGP key linked from [securezeron.com/.well-known/security.txt](https://securezeron.com/.well-known/security.txt) if the contents are sensitive.

## What to include

- Affected component and version (or commit SHA).
- A minimal reproduction — for crypto issues, the exact input bytes, key, and observed vs. expected output.
- Impact — what an attacker can do, and under what assumptions (network position, key access, etc.).
- Suggested fix, if any.

## Response

- **Acknowledgement:** within **3 business days**.
- **Initial assessment:** within **7 business days** — severity, scope across SDKs/CTS, whether a wire-format change is required.
- **Coordinated disclosure:** we aim to ship fixes within **30 days** for high-severity issues. We'll keep you informed and credit you in the advisory unless you ask us not to.
- **Public advisory:** GitHub Security Advisory + entry in each affected repo's `CHANGELOG.md`.

We will not pursue legal action against researchers who report in good faith under this policy.

## Scope

In scope:

- Cryptographic vulnerabilities in signing, verification, key handling.
- Canonicalization (RFC 8785 JCS) bugs that cause cross-implementation byte divergence.
- Schema-validation bypasses that could be used to mint malformed-but-accepted events or policies.
- Test-vector or fixture content that, if blindly trusted, leads to insecure implementations.
- Supply-chain issues — compromised dependencies in any SDK or the CTS.

Out of scope:

- Vulnerabilities in third-party libraries that we depend on — please report to the upstream project. If they affect us, do also let us know so we can pin or patch.
- Issues in non-reference implementations (vendors / planes built by other parties).
- Best-practice deviations that do not result in an exploitable condition.

## Supported versions

While the spec is at v0.x, only the **latest tagged release** of each SDK and the CTS is supported with security fixes. Older `0.0.z` releases will not be patched — pin to the latest tag.

When v1.0 is cut, this policy will be updated with an explicit version-support matrix.

## Crypto-specific guidance

If your report involves signatures or canonicalization:

- The reference algorithm is **Ed25519 over RFC 8785 (JCS)** — see [ADR 0001](https://github.com/openagp/spec/blob/main/decisions/0001-signature-canonicalization.md).
- Cross-implementation divergence is **always** a bug, even if both sides "verify" — divergence breaks the auditability guarantee.
- Test vectors under `spec/test-vectors/` are the source of truth. A new vector demonstrating divergence is the cleanest possible report.

Thanks for helping keep AGP trustworthy.
