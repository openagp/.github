# OpenAGP Governance

AGP is an **open protocol with a clear path to vendor-neutral governance**. This document explains how decisions are made today, who makes them, and the explicit roadmap to neutralization.

## Honest disclosure

OpenAGP is initially developed, maintained, and stewarded by [Zeron](https://securezeron.com), the company behind ZAK — the canonical reference implementation of an AGP plane. Zeron created AGP because the fragmentation of AI agent governance is a problem its customers face directly, and because no incumbent (hyperscaler, foundation model vendor, or compliance vendor) is structurally positioned to ship a vendor-neutral protocol.

Zeron's commercial interest is in shipping the best AGP plane implementation. AGP itself is open, and Zeron benefits more from broad adoption of AGP than from sole control of the spec.

We are transparent about this rather than pretending neutrality on day one.

## Phased governance roadmap

### Phase 1 — Stewardship (today through v0.x)

- Zeron drives the spec. PRs reviewed by Zeron engineering.
- Open contribution model: anyone may submit issues, PRs, RFCs.
- Decisions documented publicly in [`spec/decisions/`](https://github.com/openagp/spec/tree/main/decisions).
- Working group not yet formed. The bar for forming one: 5+ committed external implementers.

### Phase 2 — Working group (target: v0.2, ~Q1 2027)

- Working group formed once 5 external implementers ship AGP-compliant systems.
- Initial composition: Zeron + 2 vendor representatives + 2 customer representatives + 1 academic.
- Decisions move from Zeron-unilateral to working-group consensus.
- Zeron retains chair until v1.0.

### Phase 3 — Neutralization (target: v1.0)

- Spec ownership transfers to a vendor-neutral foundation (candidates: Linux Foundation, OpenSSF, OASIS, IETF — to be selected by working group).
- Trademarks, domains, and registry assets transfer with the spec.
- Zeron continues as one contributor among many.
- Working group elects new chair.

## Decision-making (today)

- **Editorial decisions** (typos, formatting, clarifications): merged on review by any maintainer.
- **Substantive spec changes** (semantics, new fields, conformance changes): require an RFC PR with a 2-week comment period and explicit Zeron sign-off.
- **Breaking changes**: require an RFC PR with a 4-week comment period and rationale for why the change cannot be additive.

All decisions and rationales are recorded in `spec/decisions/`.

## Conflict resolution

Disagreements are resolved by, in order:
1. Discussion on the relevant issue or PR.
2. Escalation to Zeron's working-group representative for a decision and written rationale.
3. Once the working group exists: simple majority of the working group, with the chair holding a tiebreaking vote.

## Becoming a maintainer

Maintainers are added by existing maintainers, based on demonstrated sustained contribution. There is no minimum contribution threshold — quality matters more than count.

## Contact

- General discussion: GitHub Discussions on `openagp/spec`
- Security issues: see [SECURITY.md](SECURITY.md)
- Governance questions: open an issue on `openagp/.github`
