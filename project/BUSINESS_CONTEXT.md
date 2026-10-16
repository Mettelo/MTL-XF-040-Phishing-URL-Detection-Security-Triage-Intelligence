# MTL-XF-040 — Business context

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.

## Organisation and problem

Confidential Commercial SOC is the fictional organisation. SOC analysts need to prioritise suspicious-URL alerts while controlling false positives and retaining a human escalation route. Historical URL/webpage features can test offline triage, but do not establish live threat status or safe access to listed domains.

The Security Operations Centre Manager needs a daily suspicious-URL triage review supporting **Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.**

## Stakeholders

| Stakeholder | Decision | Required evidence |
| --- | --- | --- |
| Security Operations Centre Manager | Approve scope, policy assumptions and next investigation/pilot. | D7 policy comparison, D11 recommendations, workload/risk and limitations. |
| SOC and Threat Intelligence Analyst | Interpret observations and own action proposals. | K1–K7, source-supported dimensions, sensitivity and case lineage. |
| Data Governance Analyst | Approve source, freeze and interpretation rights. | S1 manifest, licence, actual schema and source-to-output support. |
| Operations / service owner | Accept workload and review/escalation responsibilities. | Action register, eligibility, owners, review dates and override reasons. |
| Security Model Assurance Analyst | Challenge correctness and release readiness. | DT1–DT10, UAT, reconciliations and clean rerun. |

## Workflow to improve

Current simulated process: separate extracts/headline totals → informal prioritisation → manual review with limited lineage. This is a teaching scenario, not an observed real client process.

Proposed process: acquire approved bytes → validate/freeze → curate at declared grain → calculate K1–K7 → compare policies → inspect uncertainty/exclusions → sponsor approves investigation/pilot → record disposition and review date. No score bypasses human approval.

## Questions to answer

1. What is the baseline phishing prevalence, and what defines its denominator?
2. Which supported groups/cases account for phishing recall, and with what sample support?
3. Which cases change between the baseline and alternative, and why?
4. How do the specified transformation, threshold, cost or capacity alternatives alter the decision?
5. Which recommendations remain unsupported and what evidence must be collected next?

## Decision and action evidence

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

Every action record contains case/group key, snapshot, observed measure, eligibility, baseline and alternative rank/policy, evidence link, uncertainty, proposed next step, accountable owner, due/review date, disposition and override rationale. Use source-row IDs; do not invent real customer identities.

## Value and limits

Delivery success is evidence-backed acceptance of D1–D12, not guaranteed model superiority. Benefits remain hypotheses until an approved pilot specifies population, comparator, outcome window and guardrails. D11 includes three next actions and a case where the evidence does not justify action.

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

**Risk to prevent:** Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage.

**Source boundary:** All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Missing mandatory support blocks G1 or a dependent output until a governed scope/source decision is recorded.
