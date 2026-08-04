# ADR-003: Keep Consequential Controls Outside the Language Model

## Status

Accepted

## Context

Language models can interpret requests and propose actions, but their output is probabilistic and can be influenced by ambiguous instructions or untrusted content. Permissions, transaction limits, human approvals, and policy enforcement are hard constraints that must remain dependable under those conditions.

## Decision drivers

- Enforceable least privilege
- Reliable transaction and workflow limits
- Meaningful human accountability
- Testable and explainable policy decisions
- Resistance to prompt injection and model error
- Complete audit evidence and safe failure behavior

## Options considered

1. Express permissions, limits, and approval requirements only in prompts
2. Let the model decide controls, with downstream logging
3. Enforce controls in deterministic services outside the model

## Decision

Keep permissions, transaction limits, approval gates, workflow transitions, and policy enforcement in deterministic services. The model may classify, extract, summarize, recommend, or propose a typed action. A policy or workflow service validates identity, purpose, parameters, limits, required approval, and current state before an operational system reauthorizes and executes the action.

## Rationale

Deterministic services can be tested against explicit invariants, fail closed, retain policy versions, and produce reproducible decisions. Separating recommendation from authorization limits the impact of model error and malicious context.

## Consequences

### Positive

- A model cannot grant itself access or approve its own action.
- Security and business rules can be tested independently of prompt behavior.
- Human approval and segregation of duties remain enforceable.
- Audit records distinguish suggestion, policy decision, approval, and execution.

### Negative

- Workflows require typed contracts and explicit state design.
- Policy services and approval systems add integration and operational work.
- Some flexible requests must be narrowed or rejected when they cannot be validated safely.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Policy and workflow drift apart | Version contracts together, test end-to-end invariants, and assign owners for each rule. |
| Approval becomes rubber-stamping | Present evidence, monitor reviewer behavior and workload, and preserve rejection and escalation paths. |
| Model manipulates tool parameters | Use strict schemas, canonicalization, allowlists, server-side validation, and business-rule checks. |
| Duplicate consequential action | Use durable state, idempotency keys, transaction boundaries, and reconciliation. |
| Service outage blocks work | Define safe degradation; do not bypass required controls during failure. |

## Revisit conditions

Revisit only if another mechanism can demonstrate equivalent deterministic enforcement, independent authorization, testability, evidence, and fail-closed behavior. Improvements in model quality alone are not sufficient.
