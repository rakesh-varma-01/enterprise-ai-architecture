# ADR-004: Support Multiple Model Hosting Patterns Behind an AI Gateway

## Status

Proposed

## Context

Different workloads have different requirements for quality, data sensitivity, latency, cost, and customization.

## Decision

Expose approved models through an AI gateway rather than allowing applications to integrate directly with model providers. The gateway will support external APIs, managed cloud models, and self-hosted models where justified.

## Gateway responsibilities

- Workload authentication
- Model authorization
- Routing policy
- Request and response controls
- Quotas and budgets
- Version and provider metadata
- Trace correlation
- Fallback policy

## Trade-off

The gateway introduces an additional platform dependency, but it reduces uncontrolled provider coupling and creates a consistent policy boundary.
