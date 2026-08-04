# Enterprise AI Platform Architecture

## Scope

This document expands the repository's [enterprise AI reference architecture](../../docs/enterprise-ai-reference-architecture.md) into six platform layers with explicit contracts and operational concerns. The layers are logical boundaries, not mandatory deployment units. A product may combine components when scale and risk permit, but it should preserve the responsibilities and control points.

## Layered architecture

### Layer 1: Channels and AI experiences

**Purpose:** Provide the business-facing interaction through which people and systems request, review, and act on AI-assisted work.

| Concern | Description |
|---|---|
| Responsibilities | Capture intent; authenticate sessions; communicate limitations; present evidence, citations, approval prompts, and outcomes; collect user feedback. |
| Inputs | User requests, application events, channel metadata, identity and session context. |
| Outputs | Normalized requests, user decisions, feedback, and responses appropriate to the channel. |
| Ownership | Domain product teams, with experience and accessibility standards from enterprise functions. |
| Security considerations | Prevent session leakage, unsafe rendering, prompt disclosure, and exposure of restricted content; preserve the user's identity and purpose. |
| Scalability considerations | Isolate channels from downstream latency, stream long responses carefully, apply backpressure, and degrade gracefully when AI services are unavailable. |
| Common failure modes | Treating model text as trusted markup; hiding citations; losing user identity between channel and application; presenting uncertain output as a completed decision. |

### Layer 2: Agent and workflow orchestration

**Purpose:** Coordinate bounded AI and deterministic workflow steps while maintaining explicit state, limits, and approval points.

| Concern | Description |
|---|---|
| Responsibilities | Decompose tasks; manage workflow state; invoke approved retrieval, models, and tools; enforce step, time, token, and cost budgets; route high-impact actions for approval. |
| Inputs | Normalized request, identity and purpose, workflow definition, policy decisions, model suggestions, and tool results. |
| Outputs | State transitions, retrieval and model requests, proposed or executed actions, evidence, and final task status. |
| Ownership | Shared orchestration runtime by the AI platform team; domain workflows and business rules by domain product teams and process owners. |
| Security considerations | Use typed tool contracts, per-state allowlists, service-side authorization, idempotency, input validation, and untrusted-output handling. |
| Scalability considerations | Use durable state for long-running work, asynchronous queues for variable workloads, bounded concurrency, cancellation, and retry policies that avoid duplicate actions. |
| Common failure modes | Unbounded agent loops; trusting the model to authorize itself; approval bypass; duplicate tool execution; hidden workflow state; cascading retries. |

### Layer 3: AI gateway and model services

**Purpose:** Provide one governed access boundary for approved models and model-adjacent services.

| Concern | Description |
|---|---|
| Responsibilities | Authenticate workloads; authorize model use; route by policy, quality, latency, region, and cost; enforce quotas; apply request and response controls; record model and prompt versions. |
| Inputs | Model task, minimized context, workload identity, data classification, routing constraints, and correlation identifiers. |
| Outputs | Model response, usage and latency metadata, safety signals, provider metadata, and normalized errors. |
| Ownership | Enterprise AI platform team, with cybersecurity, model risk, infrastructure, procurement, and FinOps partners. |
| Security considerations | Protect credentials; restrict egress; prevent sensitive-data routing to unapproved services; redact logs; fail closed on authorization and classification errors. |
| Scalability considerations | Apply rate and concurrency limits, caching only within authorization boundaries, provider failover, capacity reservations where justified, and load shedding. |
| Common failure modes | Direct provider integration; silent model-version changes; retry storms; fallback to a noncompliant provider; logging sensitive prompts; treating every model as interchangeable. |

### Layer 4: Enterprise context and knowledge

**Purpose:** Resolve and package current, authorized, traceable evidence for AI tasks.

| Concern | Description |
|---|---|
| Responsibilities | Ingest approved sources; apply metadata, lineage, retention, and access policy; perform keyword, vector, graph, and structured retrieval; rerank and package evidence. |
| Inputs | Authenticated identity, purpose, query, source entitlements, content updates, and retrieval policy. |
| Outputs | Ranked evidence with source, freshness, lineage, access, and confidence metadata. |
| Ownership | Shared context services by data or knowledge platforms; source quality and access by domain data and knowledge owners. |
| Security considerations | Filter before retrieval; isolate tenants; treat retrieved instructions as untrusted; minimize content; enforce deletion and purpose restrictions. |
| Scalability considerations | Partition by domain and access boundary, use incremental indexing, separate ingestion from serving, monitor freshness, and select stores by access pattern. |
| Common failure modes | Stale indexes; missing entitlement filters; poor chunking; poisoned content; citation mismatch; retrieval caches that cross authorization boundaries. |

### Layer 5: Data products, APIs, and operational systems

**Purpose:** Expose trusted enterprise facts and controlled business actions through stable contracts.

| Concern | Description |
|---|---|
| Responsibilities | Publish governed data products, APIs, and events; validate action parameters; enforce transaction rules; maintain system-of-record integrity and data contracts. |
| Inputs | Authorized queries or typed action requests, business identity and purpose, source data, and policy decisions. |
| Outputs | Data with quality and lineage metadata, action results, events, and authoritative transaction records. |
| Ownership | Domain data owners, API and integration teams, and business process owners; operational-system owners retain execution accountability. |
| Security considerations | Reauthorize at the system boundary; apply least privilege, transaction limits, segregation of duties, schema validation, and tamper-evident records. |
| Scalability considerations | Protect systems of record with quotas and queues, use stable APIs and events, design for idempotency, and avoid AI-driven fan-out to fragile dependencies. |
| Common failure modes | Letting generated text become an executable command; bypassing system authorization; coupling to physical schemas; duplicate transactions; undocumented data semantics. |

### Layer 6: Cloud, compute, and AI infrastructure

**Purpose:** Supply reliable, secure, observable runtime, network, storage, and delivery foundations for all platform layers.

| Concern | Description |
|---|---|
| Responsibilities | Provide compute and model serving, network boundaries, storage, secrets, CI/CD, infrastructure as code, software supply-chain controls, backup, and recovery. |
| Inputs | Deployment artifacts, infrastructure definitions, capacity demand, policy configuration, and operational telemetry. |
| Outputs | Running services, approved environments, capacity, platform telemetry, recovery evidence, and deployment records. |
| Ownership | Site reliability and platform engineering, with cloud, data platform, cybersecurity, and AI platform teams. |
| Security considerations | Harden workloads; isolate environments; manage keys and secrets; scan artifacts; restrict network paths; patch dependencies; preserve evidence. |
| Scalability considerations | Autoscale on appropriate signals, plan scarce accelerator capacity, test recovery, control noisy neighbors, and balance availability against cost. |
| Common failure modes | Capacity exhaustion; configuration drift; regional dependency concentration; weak secret rotation; untested recovery; scaling on token count alone. |

## Cross-cutting capabilities

| Capability | Application across the architecture |
|---|---|
| Identity and access management | Propagates verified user and workload identity; separates authentication from authorization; applies least privilege at each boundary. |
| AI governance | Maintains use-case inventory, ownership, risk tier, approved patterns, exceptions, evidence, and change controls. |
| Responsible AI | Assesses intended use, human impact, fairness, transparency, contestability, and appropriate oversight. |
| Security | Applies threat modeling, secure delivery, secrets and egress controls, content defenses, incident response, and supply-chain protection. |
| Evaluation | Tests task quality, retrieval, safety, robustness, latency, cost, and control effectiveness before and after release. |
| Observability | Correlates application, workflow, policy, retrieval, model, tool, and infrastructure signals across one request. |
| Auditability | Records who requested what, which versions and evidence were used, what policy decided, what action occurred, and who approved it. |
| FinOps and cost management | Assigns usage, enforces budgets and quotas, compares routing choices, forecasts capacity, and links cost to successful business tasks. |
| Resilience | Defines timeouts, retries, circuit breakers, fallback constraints, recovery objectives, safe degradation, and kill switches. |
| Data privacy | Minimizes data, enforces purpose and residency, controls retention and deletion, redacts telemetry, and supports rights obligations. |

Controls must be implemented at the layers where they can enforce an outcome. A policy banner in the user interface cannot replace authorization at a tool or data boundary, and a model instruction cannot replace a transaction limit.

## Why direct connections do not scale

AI applications should not independently connect to every model, database, document repository, or enterprise tool. Point-to-point integration multiplies credentials, network paths, provider-specific code, policy interpretations, and audit formats. It also makes a single user request difficult to trace and makes model or source changes risky.

Shared gateways, context services, data products, and typed tool interfaces provide controlled seams. They centralize mechanics that require consistency while leaving business rules and domain meaning with accountable teams. These intermediaries are not permission shortcuts: every downstream service must still authorize the caller and requested action.

Exceptions may be reasonable for isolated experiments or specialized workloads, but they should be time-bounded, documented, and reviewed against the same data, security, evaluation, and operational requirements.

## Related decisions

- [ADR-001: Use a layered enterprise AI platform architecture](decisions/ADR-001-layered-platform.md)
- [ADR-002: Use centralized shared capabilities with federated domain ownership](decisions/ADR-002-centralized-vs-federated.md)
- [ADR-003: Keep consequential controls outside the language model](decisions/ADR-003-deterministic-controls.md)
