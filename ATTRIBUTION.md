# Attribution, Provenance, and Safe Publication

## Source dataset

This repository includes the two full public source CSV files from the Kaggle dataset **Breast Cancer MutationAnalysis ClinVar Ensembl VEP** by Dr. Nagendra:[1]

- `data/raw/filtered_mutations.csv`
- `data/raw/pathogenic_mutations.csv`

The Kaggle listing displayed an **MIT licence** when accessed on August 23, 2026. The local source filenames, SHA-256 hashes, observed schema, row counts, and source-version metadata are pinned in `data/processed/data_manifest.json`. If you update or replace the source data, rerun the ETL workflow and commit the regenerated manifest and report.

> **Versioning boundary:** The included files are a pinned local copy of the source dataset, not a continuously refreshed mirror. Do not imply that the repository is synchronised with current ClinVar, Ensembl, gnomAD, CIViC, or cBioPortal content.

## Derived outputs

The ETL process creates provenance-preserving derived tables and reports. The canonical full table includes source filename, source SHA-256 hash, and original source-row number. It is generated from the two raw CSV files and may be regenerated locally rather than committed if repository size becomes inconvenient.

The focused review subset is derived by explicit upstream ClinVar **AlleleID** values. The repository preserves both all linked source/build records and one documented GRCh38 representation per selected AlleleID. This preserves traceability while making the later VEP exercise reproducible.

## Evidence-resource attribution

The project records upstream labels as source data and may include live observations from ClinVar, gnomAD, CIViC, and cBioPortal. Any live observation must include the resource, stable identifier or URL, data version/build where shown, and retrieval date, because public resources change over time.[2] [3] [4] [5]

## Publication boundary

Do not upload a patient VCF, an identifiable individual’s genetic information, employer or client materials, passwords, API keys, or other restricted data. This repository is limited to supplied public, de-identified source data and research-only evidence review.

It must not state or imply that the author independently performed clinical variant classification, diagnostic testing, risk assessment, treatment selection, or clinical sign-out.

## References

[1]: https://www.kaggle.com/datasets/mannekuntanagendra/breast-cancer-mutationanalysis-clinvar-ensembl-vep "Kaggle source dataset"

[2]: https://www.ncbi.nlm.nih.gov/clinvar/ "ClinVar"

[3]: https://gnomad.broadinstitute.org/help "gnomAD"

[4]: https://docs.civicdb.org/ "CIViC"

[5]: https://docs.cbioportal.org/ "cBioPortal"
