# Enterprise AI Reference Architecture

## Executive summary

This reference architecture separates user experiences, AI applications, orchestration, model access, enterprise context, governed data, and cross-cutting controls. The separation lets organizations evolve models and tools without weakening security, accountability, or domain ownership.

## Architecture layers

### 1. Channels and user experiences

Examples include employee copilots, customer-service workbenches, APIs, mobile applications, and embedded workflow assistants.

Responsibilities:

- Capture user intent and business context
- Display citations, confidence indicators, and approval prompts
- Enforce session controls and user experience policies
- Collect explicit feedback

### 2. AI applications and copilots

Responsibilities:

- Implement use-case-specific behavior
- Apply business rules and user context
- Coordinate retrieval, generation, and workflow services
- Present traceable outputs rather than raw model responses

### 3. Agent and workflow orchestration

Responsibilities:

- Decompose tasks into controlled steps
- Invoke approved tools through typed contracts
- Enforce time, cost, and action limits
- Insert human approval at defined control points
- Maintain auditable state transitions

Recommended principle: models may recommend an action, but deterministic services authorize and execute it.

### 4. AI gateway and model services

Responsibilities:

- Provide a controlled entry point to models
- Authenticate workloads and authorize model access
- Route requests by sensitivity, quality, latency, and cost
- Apply prompt templates, safety checks, quotas, and logging
- Support hosted, managed, and self-hosted models

### 5. Context, retrieval, and knowledge layer

Responsibilities:

- Retrieve authorized enterprise context
- Combine vector, keyword, graph, and structured-data access
- Preserve source metadata and lineage
- Apply document-, row-, field-, and purpose-level filters
- Package evidence for applications and agents

### 6. Enterprise data products, APIs, and events

Responsibilities:

- Publish trusted data with accountable owners
- Expose stable contracts rather than physical-storage details
- Maintain quality rules, lineage, retention, and classifications
- Support batch, API, event, and analytical access patterns

### 7. Cross-cutting controls

#### Identity, security, policy, and guardrails

- Workload and user identity
- Least-privilege authorization
- Secrets and key management
- Data-loss prevention
- Prompt-injection defenses
- Tool allowlists
- Network and egress controls
- Policy-as-code

#### Evaluation, observability, audit, and FinOps

- Offline benchmark suites
- Online quality metrics
- Model, prompt, retrieval, and tool traces
- Cost, token, and latency budgets
- User feedback
- Incident investigation evidence
- Release gates and rollback criteria

### 8. Cloud, AI, and data infrastructure

- Containers and Kubernetes
- Serverless and managed AI services
- GPU compute
- Object, relational, vector, graph, and search stores
- Streaming and batch platforms
- Infrastructure as code
- CI/CD and software supply-chain controls

## Ownership model

| Capability | Primary owner | Key partners |
|---|---|---|
| AI gateway | Enterprise AI platform | Security, infrastructure, FinOps |
| Agent runtime | AI platform or domain platform | Application teams, risk |
| Context services | Data/knowledge platform | Domain data owners, governance |
| Business tools | Domain product teams | Security, architecture |
| Model risk controls | Independent risk function | Model owners, compliance |
| Evaluation platform | AI platform | Product owners, QA, risk |
| Data products | Domain owners | Data platform, governance |

## Centralized versus federated design

Centralize capabilities that benefit from consistent policy and scale:

- Model gateway
- Identity integration
- Evaluation framework
- Observability
- Secrets and key management
- Common guardrails
- Approved model catalog

Federate capabilities requiring domain meaning and accountability:

- Business tools
- Domain prompts and workflows
- Data products
- Evaluation datasets
- Domain ontologies
- Business approval rules

## Non-functional requirements

Every production AI solution should define:

- Availability and recovery objectives
- Maximum latency by workflow step
- Cost budget per request and per business outcome
- Data-retention and deletion requirements
- Explainability and evidence expectations
- Human-review conditions
- Security classification
- Evaluation thresholds
- Rollback and kill-switch procedures
