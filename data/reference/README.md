# MTL-XF-040 — References and mappings

Retain source documentation, licence/citation notices and required codebooks for PhiUSIIL Phishing URL (Website). Preserve actual header spellings, field types and original row order; distinguish identifiers, predictors and outcomes.

Version each reference with ID, official URL, retrieval date/version, content checksum, rights, raw→display mapping, rationale, owner and reviewer. Unknown categories remain visible; validate mapping completeness/uniqueness and all many-to-many joins.

**Interpretation rule:** Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

**Project policy assumptions:** Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

Keep choices separate from publisher facts. Pin an offline public suffix list from its official provider with version, licence and checksum for registrable-domain partitioning. Do not resolve domains or browse listed URLs. Defang all displayed examples.

A reference explains the source; it cannot supply an unmeasured outcome. Register supplements and scope changes in [SOURCE_REGISTER.md](../SOURCE_REGISTER.md) before dependent work.
