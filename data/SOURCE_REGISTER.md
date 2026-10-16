# MTL-XF-040 — Source register

## S1 — PhiUSIIL Phishing URL (Website)

| Field | Approved definition |
| --- | --- |
| Provider | UCI Machine Learning Repository; preserve original creator attribution |
| Documentation | https://archive.ics.uci.edu/dataset/967 |
| Exact download | https://archive.ics.uci.edu/static/public/967/phiusiil+phishing+url+dataset.zip |
| Required inputs | PhiUSIIL_Phishing_URL_Dataset.csv |
| Source population | 235,795 URLs: 134,850 legitimate and 100,945 phishing |
| Decision owner | Security Operations Centre Manager |
| Status | Official archive/feed retrieved and inspected; team freeze/sign-off and analysis remain to be completed. No raw data uploaded. |

Persistent citation: https://doi.org/10.1016/j.cose.2023.103545

## Checked byte reference

Official archive retrieved and inspected on **2026-10-16**. Archive size **15376007 bytes**; SHA-256 **0a639fd03aea6308c5b1c10c92aa23c2ce1505447a9137271865cd0badc9a59a**.

| Archive member | Bytes | SHA-256 |
| --- | --- | --- |
| PhiUSIIL_Phishing_URL_Dataset.csv | 56854345 | a236549cd369cd80bd478ff8e1779cbf44c58d5c3f79f7a51a1adbed7d06d1c6 |

Member names and byte hashes were inspected; CSV record counts were checked where present. Actual cohort transformations and business analysis remain team delivery work.

Preserve actual header spellings, field types and original row order; distinguish identifiers, predictors and outcomes.

## Cohort and field support

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

**Grain:** One observed URL/webpage feature record. Use normalised URL grouping and registrable-domain groups for partitioning; record public-suffix-list version offline.

**Required mapping:** label, URL, Domain, FILENAME, URLLength, DomainLength, IsDomainIP, TLD and remaining provided URL/webpage numeric features; maintain availability and derivation classification for every predictor.

**Interpretation limits:** Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

## Rights and attribution

Publisher page declares [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Cite original creators, UCI and [dataset DOI](https://doi.org/10.1016/j.cose.2023.103545); preserve notices and state transformations.

## Team acquisition record required at G1

Record source/freeze ID, requested/resolved URL, retrieval UTC, release/feed timestamp, archive/member filename, actual bytes/checksum, encoding/delimiter/worksheet/schema, row count, date bounds, included/excluded scope, licence/citation evidence, storage/access and retention owner, verification checks, analyst and reviewer approval/date. Unknown or unexecuted fields remain explicitly pending.

## Raw-data durability

Preserve original archive, required members and documentation in a read-only S1-v1 snapshot in approved durable storage outside Git with a second recoverable copy. Record reviewer access and restore instructions without credentials. Provider/DOI URLs locate the source; retained checksum-addressed bytes define reproducibility. Stable URLs do not guarantee immutable contents or perpetual availability.

No raw data are committed by this master update. Restore verified retained bytes if the provider becomes unavailable. If no approved copy exists, block G1; do not substitute an unofficial mirror, another variant or guessed schema. A new official version requires rights/schema/scope review, new freeze ID and rerun of affected tests.

## Refresh and supplementary inputs

Do not stack overlapping UCI samples/variants. Required publisher codebooks remain source references. Business costs, capacities and pilot outcomes absent from S1 are synthetic assumptions, not measured facts.

Every added reference/supplement needs ID, official source/version/URL, rights, grain/coverage, purpose, join key/cardinality, effect on K/D/AC/DT and reviewer approval. Optional extensions cannot replace core requirements silently.
