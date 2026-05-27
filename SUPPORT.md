# Getting help with OpenAGP

There's a right place for each kind of question. Routing things to the right surface gets you a faster answer and keeps the issue tracker focused on actionable work.

## "How do I…?"

**→ [GitHub Discussions](https://github.com/openagp/spec/discussions)**

Use Discussions for:

- "How do I model X as an AGP event?"
- "What's the right L1 vs. L2 vs. L3 split for my deployment?"
- "Has anyone integrated AGP with $tool?"
- General design discussion that hasn't crystallized into a concrete proposal.

A maintainer or another community member usually replies within a few business days. If the answer turns into a clear bug or proposal, we'll convert it to an issue together.

## "I found a bug"

**→ Open a bug report on the relevant repo**

[bug_report.yml](https://github.com/openagp/.github/blob/main/ISSUE_TEMPLATE/bug_report.yml) walks you through what we need. The faster you can hand us a minimal reproduction (and ideally an `agp-cts` invocation or test-vector reference), the faster we can fix it.

If the bug is in:

- The Python SDK → [openagp/sdk-python](https://github.com/openagp/sdk-python/issues/new/choose)
- The TypeScript SDK → [openagp/sdk-typescript](https://github.com/openagp/sdk-typescript/issues/new/choose)
- The CTS / `agp-cts` → [openagp/cts](https://github.com/openagp/cts/issues/new/choose)
- An example → [openagp/examples](https://github.com/openagp/examples/issues/new/choose)
- The spec wording (not implementation) → [openagp/spec](https://github.com/openagp/spec/issues/new/choose) using the **Spec change** template

## "I want to change the spec"

**→ Open a [Spec change issue](https://github.com/openagp/.github/blob/main/ISSUE_TEMPLATE/spec_change.yml) on `openagp/spec`**

Spec changes follow the [governance comment-period model](GOVERNANCE.md): 2 weeks for substantive, 4 weeks for breaking. Opening an issue first scopes the conversation before anyone writes a PR.

## "I want to register my organization"

**→ Open a PR on `openagp/registry`** — see [the registry README](https://github.com/openagp/registry#submitting-an-entry). This is not an issue; it's a content submission.

## "I think this is a security issue"

**→ Do NOT file a public issue.** Follow [SECURITY.md](SECURITY.md) — use GitHub Private Vulnerability Reporting on the affected repo.

## "I want to contribute code or docs"

**→ [CONTRIBUTING.md](CONTRIBUTING.md)** has the DCO sign-off requirements and PR conventions. For sizeable changes, open an issue first so we can scope it together — small docs/typo PRs can go straight in.

## Response times

We're a small team. Honest expectations:

| Channel | Typical first response |
|---|---|
| Security report | 3 business days |
| Bug report | 5 business days |
| Spec change issue | 1–2 weeks (longer during active review periods) |
| Discussions | Best effort |

If something is genuinely urgent and you've heard nothing, ping `@fuax16` (or the listed maintainers in CODEOWNERS) on the issue.

## Commercial support

For organizations adopting AGP in production and wanting paid support, training, or implementation help, contact **hello@openagp.io**. This is not required for any AGP usage — the protocol and reference implementations are Apache 2.0 / CC-BY-4.0 and free to use.
