# Agent Authority Model

## Purpose

Agentic AI should not be treated as a binary choice between a chatbot and a fully autonomous system. Enterprise teams can introduce autonomy in controlled stages, increasing the agent's authority only when the business value, evaluation evidence, and control maturity justify it.

This model separates what an agent can **reason about** from what it is **authorized to do**.

## Five levels of autonomy

| Level | Name | What the agent can do | Typical control posture |
|---|---|---|---|
| 1 | Answer | Provide information or summarize approved context | Identity, retrieval authorization, grounding, citations |
| 2 | Recommend | Suggest a next action without changing enterprise state | All Level 1 controls plus recommendation traceability and clear ownership |
| 3 | Prepare | Assemble a proposed action, transaction, response, or workflow for review | Least-privilege tool access, validation, preview, mandatory reviewer decision |
| 4 | Execute with approval | Execute only after an authorized human or deterministic policy approves the prepared action | Strong identity binding, approval evidence, idempotent execution, full audit trail |
| 5 | Execute within limits | Perform approved classes of actions without per-action human confirmation, but only inside explicit boundaries | Policy enforcement, transaction limits, continuous monitoring, kill switch, exception routing |

## Level 1 — Answer

The agent provides information using trusted and authorized context. It does not propose or perform changes to enterprise systems.

**Suitable for:** knowledge assistants, policy lookup, document summarization, internal research.

**Key question:** Can the system reliably retrieve and ground the information it presents?

## Level 2 — Recommend

The agent interprets context and recommends a next action, but a human or downstream system remains responsible for deciding what happens next.

**Suitable for:** case prioritization, operational recommendations, next-best-action support, investigation summaries.

**Key question:** Is the recommendation explainable enough for an accountable decision-maker to challenge it?

## Level 3 — Prepare

The agent prepares an action but does not execute it. Examples include drafting a customer response, assembling a service request, preparing a configuration change, or creating a transaction payload for review.

**Suitable for:** processes where AI can reduce manual preparation effort while a reviewer retains final authority.

**Key question:** Can the reviewer clearly see what will change before approving it?

## Level 4 — Execute with approval

The agent can initiate execution only after explicit approval by an authorized reviewer or an external deterministic approval service.

The approval should bind to the exact proposed action. If the action materially changes after approval, a new approval should be required.

**Suitable for:** higher-impact workflows where AI provides meaningful automation but final accountability should remain explicit.

**Key question:** Is approval meaningful, traceable, and attached to the exact action being executed?

## Level 5 — Execute within limits

The agent can execute a defined category of actions without individual human approval. Its authority remains constrained by deterministic policies such as allowed tools, transaction limits, data boundaries, time windows, and exception rules.

**Suitable for:** repetitive, low-to-moderate-impact actions with strong evaluation evidence, mature controls, and clear recovery procedures.

**Key question:** Can the organization define a safe operating envelope and reliably detect when the agent leaves it?

## Promotion criteria

An agent should not move to a higher autonomy level merely because the model is more capable. Promotion should require evidence across several dimensions:

- stable task performance on representative evaluation cases;
- clear identity and ownership;
- least-privilege access to data and tools;
- deterministic enforcement of policy and transaction limits;
- defined human escalation and exception handling;
- end-to-end auditability;
- bounded retries and safe stopping behavior;
- operational monitoring and incident response;
- measurable business value that justifies the added autonomy.

## Design principle

> Autonomy should be earned through evidence and controls, not granted by default because a model can call tools.

The enterprise should be able to reduce or revoke an agent's authority without redesigning the reasoning layer. This keeps authorization, policy, and accountability independent from model behavior.

## What this demonstrates

This model provides a practical way to discuss agent autonomy with engineering, security, risk, architecture, and business teams without reducing the decision to "human versus autonomous." It creates intermediate stages where value can increase while authority remains intentionally bounded.
