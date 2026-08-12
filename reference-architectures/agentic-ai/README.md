# Agentic AI Reference Architecture

This package documents practical patterns for introducing agentic AI into enterprise workflows without allowing model reasoning to become enterprise authority.

The current focus is **controlled autonomy**: agents may interpret tasks, propose plans, and prepare actions, while identity, authorization, policy, approval, execution, and audit controls remain outside the model.

## Current artifacts

- [Controlled Agent Flow](controlled-agent-flow.md) — end-to-end flow from user request through policy, tool access, approval, deterministic execution, and audit.
- [Agent Authority Model](agent-authority-model.md) — five progressive levels of autonomy from answer-only behavior to bounded execution.
- [Controlled Agent Flow Diagram](diagrams/controlled-agent-flow.mmd) — Mermaid source for the architecture flow.
- [Agent Orchestration ADR](../../decision-records/ADR-003-agent-orchestration.md) — architecture decision record covering orchestration direction.

## Core principle

> Allow the model to reason within a boundary, but do not allow the model to define the boundary.

This principle separates probabilistic model behavior from deterministic enterprise controls such as permissions, transaction limits, policy enforcement, approvals, and execution.

## Planned expansion

Future iterations will add:

- component responsibilities and logical architecture;
- agent identity and delegated authorization patterns;
- tool registry and least-privilege access model;
- memory and state boundaries;
- threat model and prompt-injection controls;
- evaluation and observability patterns;
- retry, recovery, and idempotency guidance;
- cost and operating-model considerations;
- delivery roadmap.

## What this architecture demonstrates

This package demonstrates how agentic AI can be designed as an enterprise system rather than as an unconstrained model-to-tool connection. The emphasis is on measurable autonomy, explicit authority, safe execution, and traceability.
