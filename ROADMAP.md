# OpenAGP roadmap

This document tracks **what's being worked on right now**. For the strategic / multi-year view (working group, foundation hand-off, conformance adoption curve), see the [org profile page](profile/README.md#roadmap) and [§5 of the spec](https://github.com/openagp/spec/blob/main/concept-and-spec.md#5-adoption-strategy).

Per-repo milestones mirror the cross-cutting tracks below, so you can also see the v0.2 / v0.3 plan from inside any repo's **Milestones** tab.

---

## Where we are — v0.1.0-rc.1 (shipped 2026-05-04)

| Phase | Deliverable | Status |
|---|---|---|
| **α / Phase 0** | RFC 8785 canonicalization + Ed25519 sign/verify in `sdk-python`, `sdk-typescript`, and `cts` — cross-language byte-identical | ✅ shipped |
| **β** | Policy DSL evaluator in both SDKs, cross-language test vectors for Flow B / L2 | ✅ shipped |
| **δ** | Acme walkthrough end-to-end demo — runnable Appendix-A example | ✅ shipped |
| **η** | `agp-cts` v0.1 — embedded vectors, Go static binary, schema/canonicalization/signature verification | ✅ shipped |
| Spec | Concept and spec v0.1 working draft, ADR 0001 (signing), 6 JSON Schemas, 4 event fixtures, 5 policy fixtures, 23 cross-language test vectors | ✅ shipped |

What this gives you today: a vendor or plane can implement AGP **L1 in-process** with either reference SDK and prove conformance via `agp-cts vectors`. **L2 evaluation** works in-process. **HTTP transport, registry resolution, and L3 are not yet shippable.**

---

## v0.2 — HTTP layer + L2 in production · target Q3 2026

The point of v0.2: **L1 and L2 are usable over the wire**, not just in-process. After v0.2 you can stand up a vendor and a plane, run a policy through them, and watch the signed events flow.

Per-repo milestones: [spec](https://github.com/openagp/spec/milestone/1) · [sdk-python](https://github.com/openagp/sdk-python/milestone/1) · [sdk-typescript](https://github.com/openagp/sdk-typescript/milestone/1) · [cts](https://github.com/openagp/cts/milestone/1) · [registry](https://github.com/openagp/registry/milestone/1) · [examples](https://github.com/openagp/examples/milestone/1)

### Spec

- [`openagp/spec#2`](https://github.com/openagp/spec/issues/2) — Add `schemas/actor.json` for registry actor entries. Unblocks full registry CI validation and first real submissions.
- [`openagp/spec#5`](https://github.com/openagp/spec/issues/5) — **[OPEN]** Formalize policy DSL grammar (substantive change, 2-week comment period).
- [`openagp/spec#7`](https://github.com/openagp/spec/issues/7) — **[OPEN]** CTS administration model — central vs. client-side.

### SDKs

- [`openagp/sdk-python#2`](https://github.com/openagp/sdk-python/issues/2) — HTTP scaffolds (FastAPI vendor + plane apps) — Phase γ.
- [`openagp/sdk-typescript#2`](https://github.com/openagp/sdk-typescript/issues/2) — HTTP scaffolds (Express / Fastify vendor + plane apps) — Phase γ.
- [`openagp/sdk-python#5`](https://github.com/openagp/sdk-python/issues/5) — Replay-cache / `event_id` deduplication on the plane side.

### CTS

- [`openagp/cts#2`](https://github.com/openagp/cts/issues/2) — `validate-vendor --endpoint` over HTTPS.
- [`openagp/cts#3`](https://github.com/openagp/cts/issues/3) — `validate-plane --endpoint` over HTTPS.
- [`openagp/cts#5`](https://github.com/openagp/cts/issues/5) — Go policy DSL evaluator (third reference implementation for Flow B). Blocked on the DSL grammar RFC.

### Examples

- [`openagp/examples#2`](https://github.com/openagp/examples/issues/2) — `mock-vendor` (L1 HTTP service emitting events). 🌱 *good first issue*
- [`openagp/examples#3`](https://github.com/openagp/examples/issues/3) — `mock-plane` (L1 HTTP service receiving + verifying). 🌱 *good first issue*
- [`openagp/examples#4`](https://github.com/openagp/examples/issues/4) — `policy-roundtrip` (L2 policy delivery end-to-end).

---

## v0.3 — L3 + registry resolution · target Q4 2026

The point of v0.3: **L3 is shippable in production**, vendors discover plane keys via the registry instead of out-of-band config.

Per-repo milestones: [spec](https://github.com/openagp/spec/milestone/2) · [sdk-python](https://github.com/openagp/sdk-python/milestone/2) · [sdk-typescript](https://github.com/openagp/sdk-typescript/milestone/2) · [cts](https://github.com/openagp/cts/milestone/2) · [registry](https://github.com/openagp/registry/milestone/2) · [examples](https://github.com/openagp/examples/milestone/2)

### SDKs

- [`openagp/sdk-python#3`](https://github.com/openagp/sdk-python/issues/3) — Real-time decision callback (Flow C / L3).
- [`openagp/sdk-typescript#3`](https://github.com/openagp/sdk-typescript/issues/3) — Real-time decision callback (Flow C / L3).
- [`openagp/sdk-python#4`](https://github.com/openagp/sdk-python/issues/4) — Registry resolution + key rotation.
- [`openagp/sdk-typescript#4`](https://github.com/openagp/sdk-typescript/issues/4) — Registry resolution + key rotation.

### CTS

- [`openagp/cts#4`](https://github.com/openagp/cts/issues/4) — `run-implementation --sign-script --verify-script` — generic-language conformance wrapper. **The portability multiplier**: any language can claim AGP conformance with ~50 lines of glue.

### Examples

- [`openagp/examples#5`](https://github.com/openagp/examples/issues/5) — `realtime-decision` (L3 Flow C end-to-end with explicit timeout / fallback handling).

---

## Always open, no milestone

Work that's valuable and welcome any time, but not blocking a release.

- [`openagp/spec#3`](https://github.com/openagp/spec/issues/3) — Expand event fixtures to cover every `action.type`. 🌱 *good first issue*
- [`openagp/spec#4`](https://github.com/openagp/spec/issues/4) — Expand policy fixtures to cover remaining rule patterns. 🌱 *good first issue*
- [`openagp/spec#6`](https://github.com/openagp/spec/issues/6) — **[OPEN]** Registry governance RFC. Triggered when 5+ external implementers ship, or when a real duplicate-FQDN / revocation incident forces the question.

---

## Open RFCs (decisions pending)

These are spec-level decisions still on the table. Comment periods follow [GOVERNANCE.md](GOVERNANCE.md): 2 weeks for substantive, 4 weeks for breaking.

| RFC | Status | Why it matters |
|---|---|---|
| [Policy DSL grammar](https://github.com/openagp/spec/issues/5) | open | Pins the DSL surface so third-party evaluators can build against a contract, not an illustration. |
| [Registry governance](https://github.com/openagp/spec/issues/6) | open · waiting on 5+ implementers | Defines merge authority, conflict resolution, and federation posture for the registry. |
| [CTS administration model](https://github.com/openagp/spec/issues/7) | open | Affirms or flips the client-side default for the conformance suite; defines what a "conformant report" means precisely. |

---

## Where to contribute

AGP is a multi-repo protocol, so "where do I start?" depends on what you want to do. The right repo depends on your profile and the kind of change you have in mind.

### By contributor profile

**First-time or casual contributor.**
→ [`examples`](https://github.com/openagp/examples) and [`spec`](https://github.com/openagp/spec) fixtures.
The labeled [`good first issue`](https://github.com/search?q=org%3Aopenagp+is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22&type=issues) tickets in `examples` (mock-vendor, mock-plane) and `spec` (fixture expansion) are scoped for a single self-contained PR. Best place to start.

**Sustained code contributor.**
→ [`sdk-python`](https://github.com/openagp/sdk-python) and [`sdk-typescript`](https://github.com/openagp/sdk-typescript).
Feature work happens here — HTTP scaffolds, Flow C, registry resolver, replay-cache. SDK changes that touch bytes / canonicalization should land in both SDKs in lockstep; CI fails if they diverge.

**Strategic / design contributor.**
→ [`spec`](https://github.com/openagp/spec).
Author RFCs, file ADRs, propose schema changes. The three [open RFCs](#open-rfcs-decisions-pending) above (DSL grammar, registry governance, CTS admin) are the highest-leverage strategic questions waiting for a champion.

**Specialized contributor (Go, crypto, conformance).**
→ [`cts`](https://github.com/openagp/cts).
The endpoint-probe commands and the Go policy DSL evaluator need someone comfortable with Go and protocol-level reasoning. A third independent implementation is what makes AGP a real protocol rather than just a Python + TypeScript dialect.

**New organization adopting AGP.**
→ [`registry`](https://github.com/openagp/registry).
Open one PR with your signed actor entry. This is a one-time onboarding contribution, not a recurring surface.

### By contribution type

| You want to… | Go here |
|---|---|
| Add an example showing AGP in action | [`examples`](https://github.com/openagp/examples) |
| Add an event or policy fixture | [`spec/fixtures/`](https://github.com/openagp/spec/tree/main/fixtures) |
| Add a cross-language test vector | [`spec/test-vectors/`](https://github.com/openagp/spec/tree/main/test-vectors) |
| Fix a bug in the Python SDK | [`sdk-python`](https://github.com/openagp/sdk-python/issues/new/choose) |
| Fix a bug in the TypeScript SDK | [`sdk-typescript`](https://github.com/openagp/sdk-typescript/issues/new/choose) |
| Propose a wire-format change | [`spec` — Spec change template](https://github.com/openagp/spec/issues/new/choose) |
| Add a new `agp-cts` subcommand | [`cts`](https://github.com/openagp/cts) |
| Register your organization in the public actor directory | [`registry`](https://github.com/openagp/registry) |
| Improve org-level docs (templates, governance, this file) | [`.github`](https://github.com/openagp/.github) |
| Ask a question or discuss design | [Discussions on `openagp/spec`](https://github.com/openagp/spec/discussions) |
| Report a security vulnerability | [SECURITY.md](SECURITY.md) — **do not** file a public issue |

### Cross-repo changes

AGP is a protocol, so many changes touch multiple repos at once. A typical example: adding a new `action.type` enum value means a PR on [`spec`](https://github.com/openagp/spec) (schema + fixture + test vector), then matching PRs on [`sdk-python`](https://github.com/openagp/sdk-python) and [`sdk-typescript`](https://github.com/openagp/sdk-typescript) syncing the bundled schemas, possibly a PR on [`cts`](https://github.com/openagp/cts), and an [`examples`](https://github.com/openagp/examples) PR showing the new type in context.

The **cross-language impact** checklist on the [PR template](PULL_REQUEST_TEMPLATE.md) is there to flag exactly this. CI enforces cross-language parity: if Python and TypeScript disagree on bytes for the same input, the build fails.

### Read first

- [CONTRIBUTING.md](CONTRIBUTING.md) — DCO sign-off (`git commit -s`), PR conventions, scope statement.
- [SUPPORT.md](SUPPORT.md) — where to ask questions vs. file bugs vs. propose spec changes.
- [GOVERNANCE.md](GOVERNANCE.md) — for spec/RFC work specifically, the comment-period rules (2 weeks substantive, 4 weeks breaking).
- [Issue templates](ISSUE_TEMPLATE) — bug, feature, spec change (RFC), documentation. Picks the right repo automatically.

---

This roadmap is updated as milestones close and new work is scoped. The authoritative source of "what's actually in flight" is always the per-repo milestones and the open issues — this file is the navigable summary.
