# ADR-002: Start with PostgreSQL and pgvector

## Status

Accepted for the initial implementation

## Context

The first implementation needs metadata filtering, relational access-control data, vector similarity search, transactional behavior, and a low operational footprint.

## Options considered

1. PostgreSQL with pgvector
2. Dedicated vector database
3. Search engine with vector capabilities
4. Managed cloud knowledge-base service

## Decision

Use PostgreSQL with pgvector for the initial platform. Introduce a dedicated vector or search platform only when scale, hybrid-search quality, regional architecture, or operational requirements justify it.

## Rationale

- One platform can store content metadata, authorization relationships, evaluation data, and vectors
- Familiar backup, transaction, and security controls
- Lower complexity for a portfolio-scale implementation
- Clear migration boundary through a retrieval-service interface

## Consequences

- Advanced search and very large-scale vector workloads may require another engine
- Index and query tuning remain important
- Portability depends on maintaining a storage abstraction rather than exposing database-specific queries throughout the application
