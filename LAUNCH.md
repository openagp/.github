# OpenAGP — v0.1.0-rc.1 launch announcement

**The Agent Governance Protocol is now public.**

After several weeks of design and reference-implementation work, OpenAGP — the open standard for AI agent governance — is published as v0.1.0-rc.1 for community review.

If you ship AI agents, govern AI agents, audit AI agents, or write the rules they have to follow, this concerns you.

## What it is

> The way **SAML** standardized "who is this user" across identity vendors,
> and **MCP** standardized "what tools can an agent call" across model vendors —
> **AGP** standardizes "what an agent is allowed to do, who said so, and what it actually did"
> across every AI agent vendor a customer uses.

A vendor-neutral, signed, schema-defined wire protocol with three flows: events (L1), policy delivery (L2), and real-time decisions (L3). Customers author one policy and have it enforced across every conformant vendor. Vendors implement one protocol and become governable by every conformant plane. Auditors verify signed evidence without trusting either party.

Spec: [openagp/spec/concept-and-spec.md](https://github.com/openagp/spec/blob/main/concept-and-spec.md).

## What's in this release

### Specification

- [`spec/concept-and-spec.md`](https://github.com/openagp/spec/blob/main/concept-and-spec.md) — the full protocol spec
- [`spec/decisions/0001-signature-canonicalization.md`](https://github.com/openagp/spec/blob/main/decisions/0001-signature-canonicalization.md) — RFC 8785 JCS + Ed25519, byte-precisely defined
- [`spec/schemas/`](https://github.com/openagp/spec/tree/main/schemas) — 6 JSON Schemas (Draft 2020-12) for every wire message
- [`spec/fixtures/`](https://github.com/openagp/spec/tree/main/fixtures) — 4 event fixtures + 5 policy fixtures
- [`spec/test-vectors/`](https://github.com/openagp/spec/tree/main/test-vectors) — 23 deterministic byte-level test vectors that every conformant implementation must pass

### Reference implementations

- [`sdk-python`](https://github.com/openagp/sdk-python) — Python SDK · `pip install openagp`
- [`sdk-typescript`](https://github.com/openagp/sdk-typescript) — TypeScript SDK · `npm install @openagp/sdk`
- [`cts`](https://github.com/openagp/cts) — `agp-cts` Go binary, conformance test suite

**Three independent language implementations of the protocol's cryptographic core agree on every byte.** 151 tests passing across the project. Run `agp-cts vectors` to confirm yours does too.

### Worked example

[`examples/acme-walkthrough`](https://github.com/openagp/examples/tree/main/acme-walkthrough) — a runnable end-to-end demo of §9 Appendix A. Acme blocks an external email through the full flow: policy delivery → action attempt → evaluation → signed event → ledger anchor. Three signed JSON artifacts an auditor can verify independently.

```bash
git clone https://github.com/openagp/examples
cd examples/acme-walkthrough && make demo
```

About 0.2 seconds. No HTTP, no external services — the cryptographic flow is the demo.

## Status — read this before contributing

This is **v0.1.0-rc.1, a release candidate**, not a final v0.1 release. The "rc" exists to be explicit:

- The spec is **frozen for review**, not frozen for production.
- Substantive feedback is invited — and expected — over a 4-week public review window before v0.1.0 (no `-rc` suffix) is tagged.
- Implementations should pin to the rc tag if they want stability now; expect an additive-only bump to 0.1.0 final.
- Breaking changes after 0.1.0 will require a 12-month deprecation runway per spec §3.9.

**What's deliberately NOT in this release** (none of these block adoption — they're just honest about scope):

- HTTP transport scaffolds (FastAPI vendor + Express plane apps) — Phase γ
- ADR 0002: policy canonicalization for signing (YAML wire form, `policy_hash` derivation) — needed before policy signatures interoperate strictly
- 50-fixture canonicalization edge-case suite (Unicode supplementary plane, large numbers, deeply nested) — Phase ζ
- `agp-cts validate-vendor --endpoint <url>` HTTP black-box probe — CTS v0.2
- Public `agp-registry` with first vendor entries — Phase 4
- A working group — see governance section

## Honest disclosure on stewardship

OpenAGP is initially developed and stewarded by **[Zeron](https://securezeron.com)**, the company behind ZAK (the canonical reference implementation of an AGP plane). Zeron created AGP because the fragmentation of agent governance is a problem its customers face directly.

**The explicit roadmap is to transfer governance to a vendor-neutral working group by v1.0.** Trigger: 5+ external implementers shipping AGP-compliant systems. Composition: 1 plane + 2 vendors + 2 customers + 1 academic. Candidate permanent homes (chosen by the working group): Linux Foundation, OpenSSF, OASIS, IETF.

We are transparent about this rather than pretending neutrality on day one. Full details: [GOVERNANCE.md](GOVERNANCE.md).

## How to engage

### If you want to use AGP

- Try the demo: [`examples/acme-walkthrough`](https://github.com/openagp/examples/tree/main/acme-walkthrough)
- Read the spec: [`spec/concept-and-spec.md`](https://github.com/openagp/spec/blob/main/concept-and-spec.md)
- Run `agp-cts vectors` against your own implementation
- Open issues in the relevant repo

### If you want to contribute

- See [CONTRIBUTING.md](CONTRIBUTING.md)
- DCO sign-off (`git commit -s`); no CLA
- Substantive spec changes go through the [decision-record process](https://github.com/openagp/spec/tree/main/decisions) — RFC PR with a 2-week comment period, 4 weeks for breaking changes
- Best low-friction starting points: more event/policy fixtures, JCS edge cases for the CTS, language ports (Rust, Go SDK, Java)

### If you want to govern AGP

- We're not yet at the working-group threshold (5 external implementers shipping)
- Open an issue or email **hello@openagp.io** if your organization wants to be among the first vendors, customers, or academics seated on the working group when it forms

### If you found a security issue

- Email **hello@openagp.io** with the subject `[SECURITY]`
- Do not file public GitHub issues for vulnerabilities in the spec or reference implementations
- We will respond within 48 hours and coordinate disclosure

## What we believe

1. **Open beats proprietary in the long run, even with a strong sponsor.** The Okta playbook works: reference implementation quality is the moat, not the spec.

2. **Cryptographic provenance is the right primitive for trust.** Compliance teams shouldn't have to take a vendor's word that an agent did or didn't do something. They should be able to verify signatures.

3. **The buyer pull will exist.** EU AI Act, NIST AI RMF, ISO 42001, HIPAA AI guidance — every framework demands evidence customers cannot produce without cross-vendor unification. AGP is the unification.

4. **First-mover sets the spec.** Anthropic's MCP captured tool-calling by being the first credible attempt to standardize, even though MCP is technically arguable. The same window is open for governance.

5. **Honest about what's not done is more credible than spin.** This document leads with caveats deliberately.

## Acknowledgments

Engineering: built with [Claude Code](https://claude.com/claude-code) (Opus 4.7, 1M context). Every commit signed off; every line auditable in the public history.

## Links

- **Project home:** https://openagp.io
- **GitHub org:** https://github.com/openagp
- **Spec (start here):** https://github.com/openagp/spec/blob/main/concept-and-spec.md
- **Worked example:** https://github.com/openagp/examples/tree/main/acme-walkthrough
- **Contact:** hello@openagp.io

---

*v0.1.0-rc.1 · 4 May 2026 · CC-BY 4.0 spec, Apache-2.0 implementations, CC0 registry data*
