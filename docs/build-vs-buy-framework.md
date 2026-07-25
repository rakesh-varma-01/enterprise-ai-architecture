# Build-versus-Buy Framework for Enterprise AI

## Decision options

1. External model API
2. Managed cloud AI platform
3. Self-hosted open model
4. SaaS AI product
5. Internally built reusable AI platform

## Evaluation matrix

| Dimension | External API | Managed cloud | Self-hosted model | SaaS product | Internal platform |
|---|---|---|---|---|---|
| Time to market | Very high | High | Low | Very high | Medium |
| Customization | Medium | High | Very high | Low–medium | High |
| Operational effort | Low | Medium | Very high | Low | High initially |
| Data-control flexibility | Medium | High | Very high | Low–medium | High |
| Portability | Low–medium | Medium | High | Low | Depends on design |
| Upfront cost | Low | Low–medium | High | Low | High |
| Unit-cost optimization | Medium | Medium | High at scale | Low | High at scale |
| Regulatory transparency | Medium | High | High | Varies | High |

## Decision drivers

### Prefer an external model API when

- Speed matters more than deep customization
- Data usage terms satisfy policy
- The workload is not tightly coupled to one vendor-specific feature
- Exit and fallback plans are defined

### Prefer a managed cloud AI platform when

- Enterprise identity, networking, logging, and regional controls are priorities
- The organization already operates in that cloud
- Managed retrieval, evaluation, guardrails, or model catalog capabilities reduce delivery risk

### Prefer self-hosting when

- Data or sovereignty constraints prevent external processing
- Predictable high volume justifies infrastructure investment
- Model-level customization is strategically important
- The organization can operate GPU capacity and model-serving systems reliably

### Prefer a SaaS product when

- The business capability is standard rather than differentiating
- Configuration is sufficient
- Vendor controls and integration meet enterprise requirements
- Fast business adoption is more valuable than platform ownership

### Build an internal platform when

- Multiple domains need the same governed capabilities
- Reuse can justify central investment
- The platform team can provide product management and service-level ownership
- The organization wants consistent model access, evaluation, policy, and observability

## Mandatory architecture questions

- What business capability is differentiating?
- Which data classifications will be processed?
- Can the service retain or train on submitted data?
- What are the exit, portability, and fallback plans?
- How are model, prompt, and platform changes detected?
- How will costs behave at expected and peak volume?
- Who owns production incidents and model-quality regressions?
- Which controls remain the organization’s responsibility?
