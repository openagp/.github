# OpenAGP

**The open Agent Governance Protocol — vendor-neutral standard for AI agent governance.**

The way SAML standardized "who is this user" across identity vendors, and MCP standardized "what tools can an agent call" across model vendors — AGP standardizes **what an agent is allowed to do, who said so, and what it actually did** across every AI agent vendor a customer uses.

## The repos

| Repo | Purpose |
|---|---|
| [`spec`](https://github.com/openagp/spec) | Protocol specification, JSON Schemas, fixtures |
| [`sdk-python`](https://github.com/openagp/sdk-python) | Reference vendor + plane SDK (Python) |
| [`sdk-typescript`](https://github.com/openagp/sdk-typescript) | Reference vendor + plane SDK (TypeScript) |
| [`cts`](https://github.com/openagp/cts) | Conformance Test Suite — `agp-cts validate-vendor --endpoint ...` |
| [`registry`](https://github.com/openagp/registry) | Public directory of AGP-compliant actors |
| [`examples`](https://github.com/openagp/examples) | End-to-end worked examples — mock vendor, mock plane |

## Conformance levels

- **L1** — vendor emits AGP-canonical signed events for every agent action
- **L2** — vendor accepts AGP policy and reflects decisions in events (L1 + policy enforcement)
- **L3** — vendor calls back to the plane synchronously for high-stakes decisions (L1 + L2 + real-time)

## Status

v0.1 working draft. Spec, SDKs, and CTS targeted for public release.

## Governance

AGP is initially developed and maintained by [Zeron](https://securezeron.com), with the explicit intent to transfer governance to a vendor-neutral working group by v1.0. See [GOVERNANCE.md](GOVERNANCE.md).

## License

- Spec: **CC-BY 4.0**
- SDKs and CTS: **Apache-2.0**
- Registry data: **CC0**
