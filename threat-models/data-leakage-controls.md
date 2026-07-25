# Data-Leakage Control Pattern

## Control points

1. Classify the user request and intended purpose
2. Resolve user and workload entitlements
3. Filter data before retrieval
4. Minimize and redact context before model access
5. Route only to providers approved for the classification
6. Validate output before display or downstream use
7. Redact logs while preserving audit metadata
8. Apply retention and deletion policy

## Defense in depth

No single prompt or guardrail should be treated as a data-protection boundary. Authorization, network controls, provider contracts, DLP, output validation, and monitoring must operate together.
