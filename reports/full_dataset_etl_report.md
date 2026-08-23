# Full-Dataset ETL Report

**Generated:** 2026-08-23T21:38:55.344682+00:00  
**Purpose:** Reproducible, research-only ingestion and quality profiling of the public Kaggle BRCA mutation dataset.

> This report describes public, pre-annotated source data. It does not validate clinical significance, independently classify variants, or establish diagnosis, risk, or treatment recommendations.

## Source-file profile

| Source file | Rows | Columns | Unique upstream AlleleID values | Rows duplicated on variant key |
|---|---:|---:|---:|---:|
| filtered_mutations.csv | 33,645 | 46 | 16,977 | 0 |
| pathogenic_mutations.csv | 33,645 | 50 | 16,977 | 0 |

## Cross-file comparison

| Measure | Value |
|---|---:|
| Combined canonical-table rows | 67,290 |
| Upstream AlleleIDs observed in both files | 16,977 |
| Review records retained across source files/builds | 16 |
| Unique GRCh38 review variants selected | 4 |

## Outputs

| Output | Purpose |
|---|---|
| `data_manifest.json` | Pinned source filenames, SHA-256 hashes, source schema, row counts, and ETL metadata. |
| `full_variants_canonical.csv` | Standardised, provenance-preserving concatenation of both full source files. |
| `review_subset_all_source_records.csv` | All source-file/build records linked to the four selected upstream AlleleIDs. |
| `review_subset_grch38_unique.csv` | One GRCh38 row per selected upstream AlleleID, chosen with documented source priority. |
| `schema_profile.json` | Machine-readable per-source quality profile. |

## Interpretation boundary

The full data files contain upstream ClinVar-derived and VEP-derived fields. This ETL workflow preserves those labels as source data. It does not turn source labels into new clinical conclusions.
