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

## Where to start contributing

- **Read** [CONTRIBUTING.md](CONTRIBUTING.md) (DCO sign-off, PR conventions) and [SUPPORT.md](SUPPORT.md) (where to ask questions vs. file bugs vs. propose changes).
- **Pick a starter issue:**
  - [Good first issues across the org](https://github.com/search?q=org%3Aopenagp+is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22&type=issues)
  - [Help wanted across the org](https://github.com/search?q=org%3Aopenagp+is%3Aopen+is%3Aissue+label%3A%22help+wanted%22&type=issues)
- **Propose a change** via the [issue templates](ISSUE_TEMPLATE) — bug, feature, spec change (RFC), or documentation.
- **Discuss** designs in [Discussions on `openagp/spec`](https://github.com/openagp/spec/discussions).

---

This roadmap is updated as milestones close and new work is scoped. The authoritative source of "what's actually in flight" is always the per-repo milestones and the open issues — this file is the navigable summary.
