# Enterprise AI Architecture Principles

These principles turn broad intentions into design tests. Exceptions should identify the affected principle, accountable owner, compensating controls, and revisit date.

## 1. Business outcomes before model selection

**Definition:** Define the process outcome, user, success measure, and operating constraint before choosing a model or AI technique.

**Why it matters:** A model benchmark does not establish that a workflow is useful, supportable, or worth its cost.

**Example:** A service team defines reduced rework with maintained review quality, then evaluates retrieval and model options against representative tasks.

**Architecture implication:** Use-case intake and evaluation criteria precede provider integration; components remain traceable to a business capability.

**Anti-pattern:** Selecting a preferred model first and searching for a business problem that justifies it.

## 2. Deterministic controls around nondeterministic behavior

**Definition:** Use explicit services and code for permissions, limits, state transitions, approvals, and transactions; use models for bounded interpretation or generation.

**Why it matters:** Probabilistic output cannot reliably enforce a hard business or security invariant.

**Example:** A model proposes a refund category, while a policy service checks eligibility and a workflow service enforces the approval threshold.

**Architecture implication:** Separate model inference from policy decisions and action execution, with typed contracts and fail-closed behavior.

**Anti-pattern:** Instructing the model in a prompt to approve only permitted transactions.

## 3. Least-privilege tool access

**Definition:** Grant each workflow state only the tools and operations needed for the authenticated user, purpose, and task.

**Why it matters:** Tool access converts generated output into real-world effects and expands the impact of errors or malicious content.

**Example:** A research step may read an account summary but cannot update it; a later approved step receives a narrow update operation.

**Architecture implication:** Use per-state allowlists, workload identity, scoped credentials, parameter validation, and authorization at the tool boundary.

**Anti-pattern:** Giving a general-purpose agent one privileged credential and a catalog of every enterprise tool.

## 4. Trusted and authorized context

**Definition:** Supply context only from approved, current, attributable sources that the requesting identity may access for the stated purpose.

**Why it matters:** Relevant but unauthorized, stale, or untraceable content can produce harmful answers and data leakage.

**Example:** A policy assistant retrieves current documents after entitlement filtering and returns source and effective-date metadata.

**Architecture implication:** Context services preserve provenance, apply access filters before retrieval, monitor freshness, and isolate untrusted instructions.

**Anti-pattern:** Indexing a shared drive into one unrestricted vector collection.

## 5. Evaluation before production

**Definition:** Establish representative datasets, acceptance criteria, and control tests before releasing an AI-enabled workflow.

**Why it matters:** Demonstrations hide edge cases, subgroup impacts, retrieval failures, and operational trade-offs.

**Example:** A knowledge assistant must pass groundedness, citation, access-control, latency, and cost tests on versioned cases before release.

**Architecture implication:** Evaluation becomes a delivery-stage gate with retained results and regression testing for material changes.

**Anti-pattern:** Releasing after a few hand-picked prompts because responses appear convincing.

## 6. Human accountability for consequential decisions

**Definition:** Assign a named person or role to decisions with material impact and provide the evidence, authority, and time needed for meaningful review.

**Why it matters:** Human presence is not effective oversight unless the reviewer can understand, challenge, reject, and escalate the recommendation.

**Example:** A case owner reviews sources and policy results before an action affecting a customer or employee is executed.

**Architecture implication:** Workflows include risk-based approval gates, reviewer interfaces, segregation of duties, and recorded disposition.

**Anti-pattern:** A reviewer clicks approve on a high-volume queue without evidence or a practical rejection path.

## 7. Reusable platform capabilities over isolated solutions

**Definition:** Build common model access, context, evaluation, identity, policy, and telemetry capabilities once when multiple products need them.

**Why it matters:** Repeated local implementations create inconsistent controls and slow down both delivery and remediation.

**Example:** Domain teams use a shared gateway and trace schema while owning their prompts, workflows, evaluation cases, and business outcomes.

**Architecture implication:** Provide documented service contracts and paved roads with product ownership and service expectations.

**Anti-pattern:** Every team creates its own model credentials, logging format, retrieval stack, and safety checks.

## 8. Model and provider portability

**Definition:** Keep business workflows and evidence contracts separable from provider-specific interfaces where switching has plausible value.

**Why it matters:** Quality, terms, regional availability, cost, and model lifecycles change independently of business processes.

**Example:** A gateway normalizes core invocation metadata while allowing an explicit extension for a justified provider feature.

**Architecture implication:** Isolate adapters, version prompts and evaluations, retain routing metadata, and test viable fallback paths.

**Anti-pattern:** Assuming all models are interchangeable or, conversely, spreading one provider's types through every application layer.

## 9. Governance proportional to business impact

**Definition:** Apply review depth, evidence, monitoring, and human oversight according to intended use, affected parties, autonomy, and potential harm.

**Why it matters:** Uniform heavy review blocks low-impact work, while uniform light review leaves serious risks untreated.

**Example:** An internal drafting aid receives baseline controls; a consequential recommendation receives independent validation and stronger monitoring.

**Architecture implication:** Intake assigns a documented risk tier that maps to review paths, required controls, and revalidation triggers.

**Anti-pattern:** Treating every chatbot as equally risky or exempting a high-impact workflow because a person appears at the end.

## 10. Observability across the complete AI request path

**Definition:** Correlate identity, application, workflow, policy, retrieval, model, tool, approval, and infrastructure events for each request.

**Why it matters:** Model output alone cannot explain a failure caused by stale context, denied policy, tool latency, or version change.

**Example:** An incident trace identifies the prompt version, retrieved sources, routing decision, policy result, approver, tool outcome, latency, and cost.

**Architecture implication:** Use shared correlation identifiers, structured events, protected evidence, retention policy, and end-to-end service objectives.

**Anti-pattern:** Monitoring only provider uptime and aggregate token usage.
