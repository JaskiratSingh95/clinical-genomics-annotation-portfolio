# Two-to-Three-Hour Execution Plan

This plan gives you a realistic, end-to-end portfolio project without pretending it is a clinical laboratory validation. Stop and record any unexpected issue rather than forcing a result; that is a good scientific habit and will strengthen the final README.

| Time | Activity | Deliverable |
|---:|---|---|
| 0:00–0:15 | Create a GitHub repository, upload this project folder, and open the notebook in Google Colab. Review the source dataset page and this project’s disclaimer. | Repository scaffold and provenance understood. |
| 0:15–0:40 | Run the Ensembl VEP notebook cells against the four supplied GRCh38 variants. Save the raw JSON and flattened consequence table. | Reproducible VEP results in `results/`. |
| 0:40–1:15 | Review each variant in ClinVar by variation ID / rsID. Record the live assertion, review status, condition context, and retrieval date. | Completed ClinVar columns in evidence table. |
| 1:15–1:35 | Review each variant in gnomAD. Record the build/dataset used and a brief frequency observation. Do not apply a frequency threshold mechanically. | Completed gnomAD columns with retrieval dates. |
| 1:35–2:10 | Search CIViC and/or cBioPortal. Capture cancer-specific evidence/context, including a stable URL or accession where available. If no exact evidence is found, document that fact neutrally. | Completed cancer-evidence columns. |
| 2:10–2:35 | Write one two-sentence research interpretation per variant. Verify that the wording does not claim a diagnosis, clinical classification, or treatment action. | Completed research-only interpretation table. |
| 2:35–3:00 | Add methods, limitations, and a short interview summary; commit the final materials. | A publishable, honest portfolio repository. |

## Evidence-review rules

The source dataset already contains ClinVar-derived assertions. Treat those as **database source fields**, not as the result of your own classification. VEP provides predicted molecular consequences and can provide co-located population-frequency information, but prediction and frequency data do not independently establish a clinical classification.[1] ClinVar itself warns that its information is not intended for direct diagnostic use without genetics-professional review.[2]

For cancer context, CIViC is a public cancer-variant evidence knowledgebase and cBioPortal provides cohort-level cancer genomics data and a public REST API.[3] [4] Capture the exact source, date, and whether the evidence is variant-specific, gene-level, or only cohort context. Do not elevate gene-level facts into a variant-specific conclusion.

## Minimum quality checklist

| Check | Pass condition |
|---|---|
| Genome build | Every input coordinate is clearly GRCh38. |
| Variant representation | VCF ref/alt alleles and VEP-normalised output are both retained, especially for deletions. |
| Provenance | Kaggle record, ClinVar identifier, rsID, VEP retrieval date, and cancer-resource URL are documented. |
| Scope | The source classification is labelled as published/database-derived; no independent clinical classification is claimed. |
| Cancer context | CIViC/cBioPortal evidence is identified as exact-variant, gene-level, or unavailable. |
| Limitations | The project notes its four-variant, public-data, research-only scope. |

## References

[1]: https://www.ensembl.org/info/docs/tools/vep/index.html "Ensembl VEP"
[2]: https://www.ncbi.nlm.nih.gov/clinvar/ "ClinVar"
[3]: https://docs.civicdb.org/ "CIViC"
[4]: https://docs.cbioportal.org/web-api-and-clients/ "cBioPortal"
