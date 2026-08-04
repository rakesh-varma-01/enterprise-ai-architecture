# ADR-002: Use Centralized Shared Capabilities with Federated Domain Ownership

## Status

Accepted

## Context

AI delivery requires common technical controls and domain-specific knowledge. Full centralization separates solutions from business and data owners; full federation causes repeated infrastructure, inconsistent controls, and fragmented provider management.

## Decision drivers

- Business and data accountability close to the domain
- Consistent enterprise control boundaries
- Reuse of scarce platform and risk expertise
- Faster onboarding through supported patterns
- Clear decision rights and production ownership
- Cross-domain scale without a central feature-delivery queue

## Options considered

1. Central team owns platform, use cases, data decisions, and operations
2. Every domain builds and governs its own complete AI stack
3. Centralized shared platform capabilities with federated domain-owned use cases and data

## Decision

Adopt a federated operating model. The enterprise AI platform team owns shared model access, orchestration foundations, common evaluation and telemetry services, reference patterns, and platform service levels. Domain teams own business outcomes, workflows, domain tools, prompts, evaluation cases, data products, user adoption, and business-quality operations. Enterprise control functions retain their independent decision rights.

## Rationale

Common services benefit from consistent policy, scale, and specialized operations. Business workflows and data require domain meaning and accountable owners. The split aligns each decision with the group best able to make and operate it.

## Consequences

### Positive

- Domains can deliver without rebuilding core platform controls.
- Data access and quality remain with accountable source owners.
- Shared services can provide consistent evidence and provider management.
- Enterprise architecture can identify reuse and manage exceptions.

### Negative

- Joint planning and funding are required across organizational boundaries.
- Ambiguous service contracts can produce gaps or duplicated work.
- Domain maturity and capacity may vary.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Platform team becomes a bottleneck | Offer versioned self-service contracts, paved roads, onboarding automation, and transparent roadmaps. |
| Domains bypass shared controls | Enforce technical boundaries and use documented, time-bounded exception decisions. |
| Ownership gaps | Publish RACI, service catalog, escalation paths, and production support responsibilities. |
| Inconsistent domain quality | Require common evidence formats and release criteria while domains own their acceptance thresholds. |
| Unfunded shared services | Establish platform product management, capacity forecasts, and transparent allocation or showback. |

## Revisit conditions

Revisit when the number or diversity of domains changes materially, shared services no longer provide reuse, decision latency becomes unacceptable, regulatory obligations require a different separation of duties, or repeated ownership disputes show that the operating model is unclear.
