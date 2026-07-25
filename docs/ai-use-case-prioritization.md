# AI Use-Case Prioritization Framework

## Purpose

This framework helps leadership compare AI opportunities using business value, feasibility, risk, and enterprise reuse rather than enthusiasm alone.

## Scoring scale

Score each criterion from 1 to 5. For risk and effort, a higher raw score means greater difficulty; the weighted formula reverses those values.

| Criterion | Weight | What a high score means |
|---|---:|---|
| Business value | 25% | Material revenue, cost, risk, or experience improvement |
| Data readiness | 15% | Relevant, accessible, governed, and sufficiently high-quality data |
| Technical feasibility | 15% | Proven methods, testable outputs, and manageable integration |
| Time to value | 10% | Benefits can be demonstrated quickly |
| Reusability | 10% | Capabilities can support multiple products or domains |
| Strategic alignment | 10% | Direct support for enterprise priorities |
| Regulatory and human-impact risk | 10% | Raw score: higher means greater risk |
| Delivery effort | 5% | Raw score: higher means greater effort |

## Formula

```text
Priority Score =
  0.25 × Business Value
+ 0.15 × Data Readiness
+ 0.15 × Technical Feasibility
+ 0.10 × Time to Value
+ 0.10 × Reusability
+ 0.10 × Strategic Alignment
+ 0.10 × (6 - Risk)
+ 0.05 × (6 - Effort)
```

## Example assessment

| Use case | Value | Data | Feasibility | Speed | Reuse | Alignment | Risk | Effort | Score / 5 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Employee knowledge assistant | 4 | 4 | 5 | 4 | 5 | 4 | 2 | 3 | 4.25 |
| Customer-service copilot | 5 | 4 | 4 | 3 | 4 | 5 | 4 | 4 | 3.95 |
| Autonomous transaction investigator | 5 | 3 | 3 | 2 | 4 | 5 | 5 | 5 | 3.30 |

## Recommended portfolio sequence

1. Begin with the employee knowledge assistant to establish retrieval, access control, evaluation, and observability.
2. Reuse those controls for the customer-service copilot, adding workflow integration and stronger human review.
3. Treat autonomous investigation as a later-stage controlled-agent program, not a first release.

## Stage gates

A use case should not enter production unless it passes:

- Named business owner and measurable outcome
- Data-owner approval
- Security and privacy review
- Evaluation dataset and acceptance thresholds
- Human-impact assessment
- Operating support model
- Cost and capacity estimate
- Incident and rollback process
