# ADR-001: Use Retrieval-Augmented Generation Before Fine-Tuning

## Status

Accepted

## Context

Enterprise knowledge changes frequently and answers must be traceable to authorized sources. The initial use case requires current policy and procedure information rather than changes to general model behavior.

## Decision drivers

- Information freshness
- Source traceability
- Access control
- Lower initial cost
- Faster content updates
- Reduced training-data management

## Options considered

1. Prompt-only generation
2. Retrieval-Augmented Generation
3. Fine-tuning
4. RAG combined with fine-tuning

## Decision

Use RAG as the primary grounding method. Consider fine-tuning later only for stable behavior, formatting, classification, or domain-language improvements that evaluation shows cannot be achieved reliably through prompts and retrieval.

## Consequences

### Positive

- Updated content can be indexed without retraining
- Answers can include evidence and citations
- Access filters can be applied during retrieval
- Evaluation can separate retrieval and generation quality

### Negative

- Retrieval quality becomes a critical dependency
- Chunking, metadata, and indexing require ongoing operations
- Retrieved content can contain malicious or misleading instructions

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Poor retrieval | Hybrid search, reranking, benchmark queries |
| Unauthorized context | Identity-aware filters and deny-by-default policy |
| Indirect prompt injection | Content sanitization, instruction hierarchy, tool isolation |
| Stale index | Change-data capture and freshness monitoring |

## Revisit conditions

Revisit when evaluation shows consistent behavior gaps that retrieval and prompting cannot address, or when volume economics justify model customization.
