# Responsible AI Control Catalog

## Lifecycle controls

| Stage | Control | Evidence |
|---|---|---|
| Intake | Document intended and prohibited uses | Approved use-case record |
| Data | Verify lawful access, quality, lineage, and retention | Data assessment |
| Design | Identify affected users and potential harm | Impact assessment |
| Build | Apply secure coding, dependency, and secret controls | CI evidence |
| Evaluate | Test quality, bias, robustness, privacy, and safety | Evaluation report |
| Approve | Independent review proportional to risk | Approval record |
| Deploy | Enforce identity, policy, quotas, and rollback | Release evidence |
| Operate | Monitor quality, drift, incidents, cost, and abuse | Dashboards and alerts |
| Change | Reassess material model, data, prompt, or tool changes | Change record |
| Retire | Remove access, retain evidence, and dispose of data | Retirement record |

## GenAI-specific controls

- Grounded answers for knowledge-intensive tasks
- Source citation and evidence retention
- Prompt-injection and indirect-injection testing
- Sensitive-data filtering before model calls
- Output validation before downstream execution
- Tool allowlists and typed schemas
- Human approval for consequential actions
- Model and prompt version tracking
- Regression testing after any material change
- Cost and token limits per workflow

## Risk-tier concept

| Tier | Example | Required treatment |
|---|---|---|
| Low | Internal drafting assistant | Baseline security and quality testing |
| Moderate | Employee policy assistant | Grounding, access control, citations, monitoring |
| High | Customer recommendation or investigation support | Independent review, human oversight, expanded testing |
| Prohibited/exception | Fully autonomous consequential decision | Executive and risk exception or disallowance |
