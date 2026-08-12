# Controlled Agent Flow

## Purpose

This reference flow shows how an enterprise AI agent can reason and use tools without being allowed to define its own authority. The core principle is simple: the model may propose an action, but deterministic enterprise controls decide whether that action is allowed and how it is executed.

## Flow

1. **User request** — A user or application initiates a task.
2. **Identity verification** — The platform establishes who is requesting the action and the identity under which the agent is operating.
3. **Intent interpretation** — The agent interprets the request and determines the business task.
4. **Plan proposal** — The agent proposes a sequence of steps; this is a recommendation, not authorization.
5. **Policy and permission check** — Deterministic services evaluate role, data classification, tool permissions, transaction limits, and applicable policy.
6. **Approved tool exposure** — Only the tools required for the current task are made available, with the minimum permissions needed.
7. **Action preparation** — The agent prepares the proposed action and supporting evidence.
8. **Risk and impact assessment** — The platform evaluates the business impact, reversibility, and need for additional review.
9. **Human approval when required** — High-impact or policy-sensitive actions are routed to an authorized reviewer.
10. **Deterministic execution** — A controlled service executes the approved action. The model does not bypass this boundary.
11. **Audit and observability** — The platform records the requesting identity, agent, model, tools, policy result, approval, action, and outcome.

## Architecture principle

> Allow the model to reason within a boundary, but do not allow the model to define the boundary.

The boundary should be enforced outside the model through identity, authorization, policy, workflow, and execution services.

## Control points

| Control point | Responsibility | Why it matters |
|---|---|---|
| Identity | Bind the request to a human, service, and agent identity | Prevents anonymous or shared authority |
| Authorization | Determine what data and tools may be accessed | Enforces least privilege |
| Policy | Apply deterministic business and risk rules | Keeps non-negotiable controls outside model reasoning |
| Tool scope | Expose only task-specific tools and permissions | Reduces blast radius |
| Human approval | Require accountable review for consequential actions | Preserves human ownership where needed |
| Execution | Perform the approved action through deterministic services | Separates reasoning from authority |
| Audit | Capture the complete request and action path | Supports traceability, investigation, and improvement |

## Failure behavior

A production agent should have explicit stopping conditions. The workflow should stop or escalate when:

- identity cannot be established;
- the requested tool is not authorized;
- policy rejects the action;
- required evidence is missing;
- a high-impact action lacks approval;
- a tool call repeatedly fails;
- the agent exceeds its iteration or time limit;
- the system cannot determine whether a prior action completed successfully.

Retries should be bounded. Actions should be idempotent where possible, and recovery paths should be documented for partially completed workflows.

## What this demonstrates

This pattern demonstrates controlled autonomy: flexible model reasoning combined with deterministic identity, policy, tool authorization, approval, execution, and audit controls.
