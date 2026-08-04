# Enterprise AI Platform Capability Model

## How to use this model

The model separates capabilities from products and organizational charts. An enterprise owner is accountable for the common contract and control posture; a domain owner remains accountable for business meaning and outcomes. **Shared** capabilities should be reusable across domains. **Domain-specific** capabilities encode a particular process, dataset, or decision. **Hybrid** capabilities have a shared foundation with domain-owned configuration or content.

## Maturity levels

| Level | Assessment meaning |
|---|---|
| Initial | Capability exists in isolated solutions; ownership, controls, and evidence are inconsistent. |
| Repeatable | A documented pattern is used by more than one team, with named ownership and baseline controls. |
| Managed | A supported service or governed domain practice has service objectives, release gates, metrics, and change control. |
| Optimized | Evidence drives safe automation and continuous improvement; reuse and exceptions are actively managed. |

## AI experience capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Experience integration | Embeds AI into web, mobile, API, and business-workflow channels with consistent interaction contracts. | Digital experience architecture | Hybrid | Standalone UI → shared interaction pattern → supported channel components → adaptive experiences within policy |
| Evidence presentation | Presents sources, uncertainty, limitations, and action status so users can assess output. | Domain product owners | Hybrid | Free-form answer → citation pattern → evidence UX standard → evidence quality measured and improved |
| Feedback and correction | Captures structured user feedback, corrections, and escalation without treating all feedback as ground truth. | Domain product owners | Domain-specific | Ad hoc comments → common feedback fields → triaged product workflow → feedback linked to evaluated improvements |
| Human review experience | Gives authorized reviewers evidence, decision context, approve/reject controls, and escalation paths. | Business process owners | Domain-specific | Manual handoff → standard review screen → measured review control → risk-based routing with effectiveness checks |

## Agent orchestration capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Workflow state management | Maintains explicit, durable state for multi-step AI and deterministic work. | Enterprise AI platform | Shared | In-process steps → workflow template → durable managed runtime → policy-bounded optimization |
| Tool registry and contracts | Registers approved tools, typed schemas, owners, allowed purposes, and operational metadata. | Enterprise AI platform | Hybrid | Local functions → shared schemas → governed registry → usage and risk evidence refine catalog |
| Agent runtime controls | Enforces tool allowlists, timeouts, retries, step limits, budgets, cancellation, and kill switches. | Enterprise AI platform | Shared | Prompt instructions → common library → enforced runtime service → controls tuned from operational evidence |
| Approval orchestration | Routes consequential actions to authorized reviewers and records disposition. | Business process owners | Hybrid | Informal approval → workflow gate → policy-integrated approval service → effectiveness and workload optimized |

## Model platform capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| AI gateway | Provides authenticated, authorized, observable access to approved models. | Enterprise AI platform | Shared | Direct APIs → gateway pattern → supported control boundary → evidence-based routing |
| Model catalog and lifecycle | Records approved models, intended uses, restrictions, versions, owners, and retirement status. | Model governance | Shared | Informal list → reviewed catalog → lifecycle workflow → proactive impact and retirement management |
| Routing and fallback | Selects models using explicit quality, classification, latency, availability, region, and cost rules. | Enterprise AI platform | Shared | Hard-coded model → configuration → policy-based routing → continuously evaluated routing within bounds |
| Prompt and configuration management | Versions prompts, system instructions, parameters, and dependencies as deployable artifacts. | Enterprise AI platform | Hybrid | Embedded strings → source-controlled templates → governed registry and release → measured optimization with rollback |

## Enterprise context capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Source onboarding and lineage | Registers approved sources and preserves ownership, provenance, classification, and update history. | Data and knowledge governance | Hybrid | Manual ingestion → onboarding checklist → governed pipeline → automated lineage assurance and exception handling |
| Identity-aware retrieval | Applies user, workload, purpose, and content entitlements before returning context. | Data platform security | Shared | Application filters → reusable filter pattern → deny-by-default service → continuously tested authorization policies |
| Retrieval and reranking | Uses appropriate search, vector, graph, and structured methods to return relevant evidence. | Enterprise context platform | Hybrid | Single search method → reusable pipeline → evaluated retrieval service → domain-tuned selection from measured results |
| Context packaging | Minimizes and structures evidence with citation, freshness, lineage, and access metadata for consumers. | Enterprise context platform | Shared | Raw text → common envelope → versioned evidence contract → quality and cost optimized by task |

## Data and integration capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Governed data products | Publishes trusted data through owned contracts with quality, lineage, access, and service expectations. | Domain data owners | Domain-specific | Direct source access → documented dataset → managed data product → usage-led quality improvement |
| API and event integration | Exposes stable read and event contracts without coupling AI products to internal storage. | Integration platform | Hybrid | Point integration → reusable standards → managed APIs and events → demand and reliability optimized |
| Enterprise tool execution | Executes typed business operations with validation, authorization, idempotency, and transaction controls. | Operational-system owners | Domain-specific | Agent calls backend → typed adapter → governed tool service → control effectiveness continuously verified |
| Data lifecycle management | Applies classification, retention, deletion, residency, and lawful-purpose controls across data movement. | Data governance and privacy | Shared | Local handling → documented rules → enforced lifecycle service → automated evidence and exception management |

## Security and governance capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Identity and access policy | Authenticates people and workloads and authorizes each model, context, and tool operation. | Identity and cybersecurity | Shared | App credentials → standard identity pattern → policy-enforced access → continuous entitlement assurance |
| AI use-case governance | Maintains inventory, ownership, risk tier, required controls, approvals, exceptions, and material changes. | AI governance | Shared | Spreadsheet intake → common workflow → governed system of record → portfolio evidence guides policy refinement |
| Responsible AI assessment | Assesses intended use, affected parties, fairness, transparency, human oversight, and potential harm. | Model risk and responsible AI | Hybrid | Informal review → risk questionnaire → tiered independent review → post-production evidence improves assessment |
| AI security and privacy | Applies threat modeling, secure delivery, data minimization, content defenses, egress control, and incident response. | Cybersecurity and privacy | Shared | Project controls → reference pattern → enforced control set → threats and incidents drive continuous adaptation |

## Evaluation and observability capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Offline evaluation | Tests task quality, retrieval, safety, robustness, fairness where relevant, latency, and cost on versioned cases. | AI quality engineering | Hybrid | Manual prompts → repeatable dataset → release-gated suite → targeted cases generated from reviewed failures |
| Online quality monitoring | Detects production changes in outcomes, grounding, refusal behavior, user feedback, and control performance. | Domain product owners | Domain-specific | User complaints → basic metrics → alerting and review process → risk-based sampling and improvement loop |
| End-to-end tracing | Correlates application, workflow, policy, retrieval, model, approval, tool, and infrastructure events. | Observability platform | Shared | Separate logs → correlation IDs → common trace contract → automated diagnosis with protected evidence |
| Audit evidence management | Retains tamper-evident records needed to reconstruct material requests, decisions, versions, and actions. | AI governance and cybersecurity | Shared | Best-effort logs → defined event set → retention and access controls → evidence completeness continuously tested |

## Platform engineering capabilities

| Capability | Description | Enterprise owner | Classification | Maturity path: Initial → Repeatable → Managed → Optimized |
|---|---|---|---|---|
| Secure delivery pipeline | Builds, tests, scans, approves, deploys, and rolls back AI application and platform changes. | Platform engineering | Shared | Manual deployment → pipeline template → policy-gated service → progressive delivery driven by evaluation evidence |
| Runtime and model-serving infrastructure | Provides isolated compute, networking, storage, and accelerator capacity for platform workloads. | Site reliability and platform engineering | Shared | Project environments → standard runtime → service objectives and capacity plans → workload-aware placement and scaling |
| Resilience engineering | Defines failure boundaries, timeouts, retries, recovery, safe degradation, and tested shutdown procedures. | Site reliability engineering | Shared | Ad hoc retries → resilience patterns → tested objectives → fault evidence continuously improves design |
| FinOps and capacity management | Allocates usage, sets budgets, forecasts demand, and links cost to successful tasks and service levels. | Cloud FinOps and platform engineering | Shared | Provider bill → tagged usage → budgets and showback → routing and capacity optimized within quality constraints |

## Maturity assessment

Assess evidence, not aspiration. A capability should receive the lowest level whose conditions are consistently met.

| Assessment dimension | Initial | Repeatable | Managed | Optimized |
|---|---|---|---|---|
| Ownership | Local or unclear | Named owner for a pattern | Accountable service or domain owner with decision rights | Ownership reviewed as demand and risk change |
| Adoption | One-off use | Used by multiple teams | Standard path with managed exceptions | Adoption and exceptions inform roadmap decisions |
| Controls | Primarily manual or implicit | Documented baseline | Enforced, tested, and evidenced | Effectiveness measured and controls safely refined |
| Quality | Anecdotal | Repeatable tests | Acceptance thresholds and regression gates | Production evidence improves representative evaluation |
| Operations | Reactive | Basic runbook and support | Service objectives, alerts, incident and change processes | Trend-led prevention, resilience testing, and automation |
| Cost | Unallocated | Usage visible | Budgets, ownership, and forecasts | Cost optimized against quality and business outcome |

Recommended assessment steps:

1. Select only capabilities required by the current use-case portfolio.
2. Collect an example artifact for each claimed maturity condition.
3. Record current and target levels with accountable owners and dates.
4. Prioritize gaps that block risk treatment, reuse, or reliable operations.
5. Reassess after material portfolio, provider, policy, or operating-model changes.
