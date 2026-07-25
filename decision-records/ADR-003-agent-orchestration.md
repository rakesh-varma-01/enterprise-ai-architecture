# ADR-003: Use Explicit Stateful Workflows for High-Impact Agents

## Status

Accepted

## Context

The agent may retrieve evidence, call business tools, request approval, and prepare an action. Unbounded autonomous loops would make control, testing, and audit difficult.

## Decision

Model the process as an explicit state machine. The model may classify, extract, summarize, or recommend within a state, while deterministic code controls transitions, authorization, retries, budgets, and action execution.

## Required controls

- Typed tool contracts
- Tool allowlist per workflow state
- Maximum step and cost limits
- Human approval before consequential actions
- Durable audit log
- Idempotency for external actions
- Timeout, retry, and compensation behavior
- Kill switch
