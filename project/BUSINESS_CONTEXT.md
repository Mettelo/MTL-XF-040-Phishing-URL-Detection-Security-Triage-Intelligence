# MTL-XF-040 — Business context and practical use case

## Organisation and accountable decision

Confidential Commercial SOC is the simulated sponsor. The Security Operations Centre Manager owns the daily suspicious-URL triage review and must decide: **Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.**

## The operational problem

The SOC manager needs a triage workflow that captures suspicious URLs without overwhelming analysts with legitimate alerts. An apparently strong classifier can be misleading if legitimate and phishing labels are reversed, domains appear in both training and test, or webpage-derived signals are presented as available when the URL first arrives. The team must evaluate an offline receipt-time feature set, quantify review burden and define human escalation for uncertain and missed cases.

## How the finished product will be used

At daily SOC review, an analyst inspects high-risk and intermediate bands, reviews defanged examples and false positives/negatives, and follows a documented evidence-preservation and incident-response handoff. No listed URL is opened.

**Current approach:** Treat a single accuracy score as sufficient for alert prioritisation without domain isolation or analyst-workload controls.

**Required future approach:** Use domain-disjoint evaluation, a declared false-positive target and governed human triage with offline evidence.

The review starts with a verified frozen population and measured baseline. The domain analyst demonstrates the specified business outputs, the operational owner challenges workload and feasibility, assurance challenges correctness, and the sponsor records accept/defer/override. Each action records a source/configuration reference, rationale, accountable role, next step and review date. Uncertain cases remain in a visible manual-review/defer route.

## Stakeholder responsibilities

| Stakeholder | Responsibility | Decision evidence |
| --- | --- | --- |
| Security Operations Centre Manager | Approve scope, project assumptions, acceptance contract and final recommendation. | SC1–SC5 outputs; baseline/alternative trade-offs; pilot/investigation actions. |
| SOC and Threat Intelligence Analyst | Create ten defanged triage cases, including false positives and false negatives, with evidence preservation, analyst action and incident-response escalation. | Domain scorecard, worked cases, supported interpretation and source lineage. |
| Operational service owner | Accept workload, assignment and escalation route. | Case register, capacity/threshold comparison, due dates and overrides. |
| Data Governance Analyst | Confirm source identity, rights, exact freeze and required fields. | S1 manifest and source→field→measure→deliverable matrix. |
| Security Model Assurance Analyst | Approve evidence quality and independently challenge the release. | Executed SC/AC/DT checks, three UAT tasks and rerun. |

## Business questions tied to outputs

1. Can the sponsor use **Phishing population and feature-availability audit** to support the stated decision, with this evidence: 235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier.
2. Can the sponsor use **Offline lexical detection evaluation** to support the stated decision, with this evidence: Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used.
3. Can the sponsor use **Three-band analyst triage policy** to support the stated decision, with this evidence: Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records.
4. Can the sponsor use **SOC triage dashboard** to support the stated decision, with this evidence: Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views.
5. Can the sponsor use **SOC response playbook and tabletop** to support the stated decision, with this evidence: Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers.

## Concrete outputs and required success

| Deliverable | What the team must hand over | Required contents |
| --- | --- | --- |
| D5 | Phishing population and feature-availability audit | 235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier. |
| D6 | Offline lexical detection evaluation | Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used. |
| D7 | Three-band analyst triage policy | Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records. |
| D8 | SOC triage dashboard | Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views. |
| D11 | SOC response playbook and tabletop | Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers. |

| Success ID | Required deliverable | Specific pass condition |
| --- | --- | --- |
| SC1 | D5 — Phishing population and feature-availability audit | label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core. |
| SC2 | D6 — Offline lexical detection evaluation | Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed. |
| SC3 | D7 — Three-band analyst triage policy | Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking. |
| SC4 | D8 — SOC triage dashboard | Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports. |
| SC5 | D11 — SOC response playbook and tabletop | Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status. |

## Benefit and adoption boundary

Assessment success means the required outputs are correct, reproducible and usable in the specified review. It does not mean a model must win, a customer must buy, a fault must disappear or a security incident must be prevented. The executive pack must name the measured baseline, alternative, operating trade-off, recommendation and evidence still required for a real pilot. Do not invent commercial savings or success percentages to make the business case appear complete.

At G1 record simulated sponsor approval of the requirements and criteria. At G3 record the policy recommendation and unresolved evidence gaps. At G4 record an actual team reviewer and simulated sponsor role separately; template text is not an approval.

## Source and scope limits

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

**Failure to prevent:** Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage.

Missing mandatory support blocks dependent acceptance until an explicit source/scope decision updates the affected deliverables and tests.

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.
