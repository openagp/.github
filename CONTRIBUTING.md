# Contributing to OpenAGP

Thanks for your interest. AGP is an open protocol and we welcome contributions from anyone — vendors implementing receivers, customers writing policies, researchers, and engineers fixing typos.

## Ways to contribute

- **Spec changes** — open an issue first, then a PR against `openagp/spec`.
- **SDK code** — PRs against `openagp/sdk-python` or `openagp/sdk-typescript`.
- **CTS test cases** — PRs against `openagp/cts` adding edge cases or new conformance checks.
- **Registry submissions** — PRs against `openagp/registry` adding your organization's actor entry.
- **Examples** — PRs against `openagp/examples` showing end-to-end use cases.

## Sign your commits (DCO)

We use the [Developer Certificate of Origin](https://developercertificate.org) — every commit must be signed off:

```bash
git commit -s -m "your message"
```

This adds a `Signed-off-by: Your Name <email>` trailer certifying you have the right to contribute the work under the repo's license. We do **not** require a CLA.

## PR checklist

- [ ] Commits are DCO-signed (`-s`)
- [ ] CI is green
- [ ] For spec changes: rationale documented in `spec/decisions/`
- [ ] For breaking changes: explicit note in the PR description and migration path
- [ ] One logical change per PR (split unrelated changes)

## Code of conduct

We follow the [Contributor Covenant 2.1](CODE_OF_CONDUCT.md). Be kind. Disagree on technical merit, not on people.

## Review process

- Editorial PRs (typos, formatting): merged on single maintainer review.
- Substantive changes: 2-week comment period; needs maintainer approval.
- Breaking changes: 4-week comment period; needs explicit Zeron sign-off until working group is formed (see [GOVERNANCE.md](GOVERNANCE.md)).

## Scope

AGP v0.x is intentionally scoped to:
- Event emission (Flow A, L1)
- Policy delivery (Flow B, L2)
- Real-time decisions (Flow C, L3)

Out of scope for v0.x: federation between planes, GUI policy editors, vendor-specific shims (those live in vendor connectors, not the spec).

## Questions

Open an issue or start a Discussion on `openagp/spec`.
