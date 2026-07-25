# Enterprise AI Operating Model

## Objective

Enable fast domain innovation while maintaining enterprise-wide security, governance, reuse, and accountability.

## Core organizational components

### Enterprise AI platform team

Owns reusable technical capabilities:

- AI gateway and approved-model catalog
- Agent runtime and tool registry
- Retrieval and context services
- Evaluation framework
- Observability and cost controls
- Reference implementations and paved roads

### Domain AI product teams

Own business outcomes:

- Use-case definition
- Domain workflows and tools
- Domain evaluation datasets
- User adoption and feedback
- Product operations
- Benefits realization

### Data and knowledge owners

Own:

- Data products and contracts
- Access policy
- Quality and lineage
- Domain terminology and ontology
- Retention and classification

### Cybersecurity and privacy

Own or approve:

- Threat models
- Identity and network patterns
- Secrets, encryption, and egress controls
- Privacy and data-protection requirements
- Security testing and incident response

### Model risk and responsible AI

Provide independent challenge for:

- Intended use and prohibited use
- Validation approach
- Fairness and human impact
- Explainability and evidence
- Monitoring and change control

### Enterprise architecture

Owns:

- Target-state architecture
- Standards and reference patterns
- Architecture decisions
- Technology lifecycle and duplication management
- Cross-domain integration principles

## Decision rights

| Decision | Accountable | Consulted |
|---|---|---|
| Business outcome and use | Domain product owner | Risk, architecture, users |
| Model approval | Model owner / risk | Platform, security, domain |
| Data access | Data owner | Privacy, security, product |
| Shared platform standards | AI platform owner | Architecture, domains |
| Production release | Product owner | Engineering, risk, security |
| Emergency shutdown | Product and operational owner | Platform, security, risk |

## Delivery lifecycle

1. Discover and prioritize
2. Validate data and risk
3. Prototype with bounded scope
4. Establish evaluation baseline
5. Productionize using approved patterns
6. Complete independent review where required
7. Release with monitoring and rollback
8. Measure business outcome
9. Revalidate after material change

## Platform product metrics

- Time to onboard a new use case
- Percentage of applications using approved gateway and evaluation controls
- Reuse rate of platform capabilities
- Unit cost per successful task
- Evaluation pass rate
- Mean time to detect and resolve AI incidents
- Percentage of high-risk actions requiring human approval
