# MTL-XF-040 — Team repository standard

Create **MTL-XF-040-<team-name>** under **Mettelo** and add individual member accounts. Record [master URL](https://github.com/Mettelo/MTL-XF-040-Phishing-URL-Detection-Security-Triage-Intelligence), reviewed master specification commit and final team commit/tag.

## Required areas

- README.md and CONTRIBUTIONS.md
- data/SOURCE_REGISTER.md; data/raw/README.md; data/reference/; data/metadata/; data/curated/
- docs/01-discovery/; docs/02-data-governance/; docs/03-data-model/; docs/04-data-quality/
- docs/05-kpi-catalogue/; docs/06-analysis/; docs/07-decision-framework/
- docs/08-assurance-uat/; docs/09-technical-handover/
- src/; tests/; dashboard/; deliverables/; submission/FINAL_SUBMISSION.md

Use sql/notebooks/analysis folders where useful; explain unused areas and avoid duplicate implementations. Pin free toolchain/dependencies and one documented run entry point. Keep raw payloads in approved storage outside Git, with verified manifest and reviewer access; never embed credentials.

## README and contribution evidence

State Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules. Name Security Operations Centre Manager as simulated sponsor. Include cohort, acquisition/restore, environment/run instructions, five findings, baseline/alternative, assumptions, UAT/rerun and evidence links. Preserve the simulated-client declaration and this limit: Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

Assign named people to all seven [brief roles](../project/PROJECT_BRIEF.md). Every member links authored artefacts, at least one substantive review, and demo/handover contribution. Issues, commits, PRs and review records support evidence; commit count or one person's bulk upload is insufficient.

## Project-specific handover

Create ten defanged triage cases, including false positives and false negatives, with evidence preservation, analyst action and incident-response escalation.

Maintain D1–D12/AC1–AC12/DT1–DT10 evidence index with owner, distinct reviewer, state and final-commit path. Connect numeric claims to frozen source and code/configuration. Record all manual adjustments, excluded cases and limitations; preserve an insufficient-evidence case.

## Required business-output artefacts

- **D5 Phishing population and feature-availability audit:** data/curated/phishing-population-and-feature-availability-audit.csv and docs/05-kpi-catalogue/phishing-population-and-feature-availability-audit.md.
- **D6 Offline lexical detection evaluation:** docs/06-analysis/offline-lexical-detection-evaluation.md plus machine-readable evaluation_results.csv.
- **D7 Three-band analyst triage policy:** docs/07-decision-framework/three-band-analyst-triage-policy.csv plus policy.md.
- **D8 SOC triage dashboard:** dashboard/README.md, runnable dashboard/prototype and static review export.
- **D11 SOC response playbook and tabletop:** deliverables/soc-response-playbook-and-tabletop.pdf plus editable slides and supporting cards/runbook.

Index these under SC1–SC5 with author, distinct reviewer, executed result and final commit. Treat these paths as the default delivery contract; an equivalent tool-specific format requires an explicit documented mapping.

## Team organisation

The recommended team size is **3–5 people**. Delivery roles describe responsibilities, not separate positions: members can combine complementary business analysis, governance, engineering, analysis/modelling, BI and domain responsibilities. Assign a named owner to each deliverable and use a different team member to review critical calculations and perform the final clean rerun.
