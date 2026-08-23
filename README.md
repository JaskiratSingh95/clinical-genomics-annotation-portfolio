# clinical-genomics-annotation-portfolio
A reproducible, research-only portfolio for genomic variant annotation and evidence review, demonstrating GRCh38 inputs, Ensembl VEP, ClinVar source assertions, gnomAD context, cancer-resource review, QC, provenance, and transparent limitations—not clinical reporting or diagnosis.


# Clinical Genomics Annotation Portfolio: Full-Dataset ETL and Research-Only Evidence Review

> **Portfolio purpose:** This repository demonstrates a reproducible, research-only data workflow for a public BRCA1/BRCA2 mutation dataset. It ingests two full upstream CSV files, profiles and standardises their schema, preserves source provenance, extracts a documented GRCh38 review subset, and supports a small variant-annotation/evidence-review exercise. It is **not** a clinical laboratory pipeline, diagnostic report, independent variant classification, or treatment recommendation.

## Project overview

This project is organised as a data-engineering and annotation-review workflow rather than as a four-row demonstration alone. The full public dataset is retained under `data/raw/`; the curated four-variant subset is the final, traceable review stage.

**Research question:** How can a public, pre-annotated BRCA1/BRCA2 dataset be ingested, quality-profiled, standardised, and narrowed to a transparent GRCh38 review subset while preserving the distinction between upstream source assertions and independent clinical judgement?

## Scope and boundaries

| This repository demonstrates | This repository does not demonstrate |
|---|---|
| Full-dataset ingestion, schema profiling, data standardisation, provenance, and quality checks | Clinical sample receipt, DNA extraction, sequencing, alignment, variant calling, or assay validation |
| GRCh38 subset selection, Ensembl VEP molecular annotation, and public evidence review | Independent ACMG/AMP, AMP/ASCO/CAP, or clinical-laboratory variant classification |
| Explicit source attribution and research-only interpretation boundaries | Diagnosis, patient-specific risk assessment, treatment selection, or clinical sign-out |
| Reproducible Python ETL and documentation | Production deployment or continuous clinical database curation |

> **Required boundary:** Upstream ClinVar- and VEP-derived fields are preserved as **source data**. This repository does not independently reclassify variants or turn a source label into a clinical conclusion.

## Source data

The source is the [Kaggle Breast Cancer MutationAnalysis ClinVar Ensembl VEP dataset][1], which displayed an MIT licence when accessed on August 23, 2026. The pinned local archive contains `filtered_mutations.csv` and `pathogenic_mutations.csv`, each with **33,645 data rows**. Their source hashes, observed schemas, and processing date are written to `data/processed/data_manifest.json`.

The complete downloaded CSV files are included in `data/raw/` so that the ETL workflow can be run without an additional download. Do not replace them silently: use the manifest to identify the exact source version and hashes used by this portfolio. The upstream source may change over time.

| Source file | Role in this project |
|---|---|
| `data/raw/filtered_mutations.csv` | Full upstream source input, retained unchanged. |
| `data/raw/pathogenic_mutations.csv` | Full upstream source input, retained unchanged. |
| `data/processed/full_variants_canonical.csv` | Provenance-preserving standardisation and concatenation of both source files. It is generated locally and ignored by Git by default because the raw full source files are already included. |
| `data/processed/schema_profile.json` | Per-file columns, missingness, duplicate-key checks, and observed distribution metadata. |
| `data/processed/data_manifest.json` | Source URL, retrieval/version metadata, SHA-256 hashes, row counts, and output paths. |

## ETL architecture

```text
Full public CSV files (data/raw/)
             │
             ▼
Schema validation + column-name standardisation + SHA-256 provenance
             │
             ▼
Canonical full table + quality profile + ETL report (data/processed/, reports/)
             │
             ▼
All linked source/build records for four explicit ClinVar AlleleIDs
             │
             ▼
One documented GRCh38 row per selected AlleleID
             │
             ▼
Research-only VEP annotation and public-evidence review
```

The ETL stage retains all source/build records for the four selected upstream ClinVar AlleleIDs (`32699`, `32700`, `32701`, and `24357`) in `review_subset_all_source_records.csv`. It then produces one GRCh38 representation per AlleleID in `review_subset_grch38_unique.csv`. The source priority and selection rule are recorded in `data_manifest.json`.

## Repository structure

```text
.
├── data/
│   ├── raw/                         # Full public source CSV files
│   ├── processed/                   # ETL outputs, manifest, schema profile, review subsets
│   ├── input_variants.csv           # Original compact reference input
│   ├── selected_variants_grch38.vcf
│   └── processed/annotation_input_from_etl.csv  # Compact GRCh38 VEP input derived from ETL
├── docs/
│   ├── research_evidence_summaries.md
│   ├── scientific_sources.md
├── reports/
│   ├── full_dataset_etl_report.md
│   ├── portfolio_data_summary.md
│   ├── portfolio_data_summary.png
│   ├── exploratory_statistical_analysis.md
│   ├── exploratory_statistics.json
│   └── visualization_qc_notes.md
├── results/
│   ├── research_evidence_summary_template.csv
│   └── methods_and_limitations.md
├── src/
│   ├── etl_full_dataset.py
│   ├── create_annotation_input.py
│   ├── annotate_variants.py
│   ├── build_research_evidence_draft.py
│   ├── generate_portfolio_report.py
│   ├── generate_exploratory_statistics.py
│   └── validate_evidence_table.py
├── README.md
├── ATTRIBUTION.md
└── requirements.txt
```

## Reproducible workflow

### 1. Set up the environment

Use Python 3.10+ in Google Colab or a local environment.

```bash
pip install -r requirements.txt
```

### 2. Run the full-dataset ETL process

```bash
python src/etl_full_dataset.py \
  --input-dir data/raw \
  --output-dir data/processed \
  --report-dir reports
```

This step produces the canonical full table, data manifest, machine-readable schema profile, ETL report, all source/build trace records for the review variants, and the unique GRCh38 review subset. The canonical table is intentionally ignored by Git because it is reproducible from the committed raw sources; the smaller manifest, profile, report, and review-subset outputs should be committed. Read `reports/full_dataset_etl_report.md` before proceeding.

### 3. Derive and annotate the focused GRCh38 review subset

Generate a compact annotation input directly from the unique GRCh38 subset. This preserves the link between the full source data, ETL outputs, and focused evidence review.

```bash
python src/create_annotation_input.py \
  --subset data/processed/review_subset_grch38_unique.csv \
  --output data/processed/annotation_input_from_etl.csv

python src/annotate_variants.py \
  --input data/processed/annotation_input_from_etl.csv \
  --output-dir results
```

The script saves both raw VEP JSON and a flattened output table. VEP is used here for **molecular annotation only**.[2]

### 4. Complete the public-evidence log

Create `results/research_evidence_summary.csv` from the template or draft. For each review variant, document the live ClinVar source assertion, gnomAD observation, cancer-resource result, literature context, stable identifier or URL, and retrieval date.

```bash
python src/build_research_evidence_draft.py \
  --vep results/vep_flattened_YYYY-MM-DD.csv \
  --output results/research_evidence_summary.csv
```

The drafted table is intentionally incomplete until a human performs live, documented CIViC and/or cBioPortal review. Use **only** `variant-specific`, `gene-level`, or `no exact record` in the `cancer_evidence_type` column.

### 5. Validate documentation completeness

```bash
python src/validate_evidence_table.py \
  --evidence results/research_evidence_summary.csv
```

A passing result checks for missing fields, unresolved placeholders, retrieval-date format, and required research-only wording. It does **not** validate clinical correctness or assign a clinical classification.

## Quality controls

| Control | Implementation |
|---|---|
| Full-data provenance | Input filename, source SHA-256 hash, row number, and source version metadata are retained. |
| Schema drift visibility | The ETL profiles each raw file separately rather than assuming their schemas are identical. |
| Variant traceability | The review subset is selected by explicit upstream ClinVar AlleleID and retains all linked source/build records. |
| Genome-build control | The final review subset requires GRCh38; non-GRCh38 trace records remain available for comparison. |
| Transcript-context control | Raw VEP JSON is preserved. A `most_severe_consequence` can differ from the selected MANE transcript consequence, so the selected transcript is documented. |
| Evidence boundary | Published resource assertions are attributed to their sources and are not presented as independent clinical conclusions. |

## Data presentation and final findings report

The repository includes a publication-ready descriptive dashboard and an accompanying Markdown report:

![Portfolio descriptive dashboard](reports/portfolio_data_summary.png)

The dashboard presents four **source-data and ETL** views: source-file volume versus unique upstream AlleleIDs, the distribution of upstream clinical-significance source fields, genome-build composition, and gene-symbol composition. The detailed narrative, reproducible summary statistics, and presentation wording are in [`reports/portfolio_data_summary.md`](reports/portfolio_data_summary.md).

The report is designed to communicate the project’s findings accurately:

> “The ETL workflow processed two full public, pre-annotated source tables; preserved each source file, hash, and row lineage; standardised the schema; profiled source-field distributions; compared cross-file overlap; and selected a documented GRCh38 subset for focused annotation review. The final evidence table records source assertions, molecular annotation, and current public-resource context while preserving a research-only boundary.”

These charts describe the **composition and provenance of the public source data**. They are not prevalence estimates, diagnostic-performance measures, new pathogenicity claims, or treatment findings.

Regenerate the dashboard and report after running the ETL workflow:

```bash
python src/generate_portfolio_report.py \
  --input data/processed/full_variants_canonical.csv \
  --report-dir reports
```

## Exploratory statistical analysis

The repository also contains a duplicate-aware exploratory analysis in [`reports/exploratory_statistical_analysis.md`](reports/exploratory_statistical_analysis.md). It reports Pearson chi-square statistics, degrees of freedom, p-values, and Cramér’s V effect sizes for **source-data composition questions**.

| Exploratory source-data comparison | Analysis unit | N | χ² | df | p-value | Cramér’s V |
|---|---|---:|---:|---:|---:|---:|
| Gene symbol × upstream clinical-significance source field | One row per upstream AlleleID; GRCh38/source-priority selection | 16,977 | 2,228.20 | 10 | <0.001 | 0.362 |
| Gene symbol × source genome build | One row per upstream AlleleID and build; duplicate source-file copies removed | 33,645 | 1.28 | 2 | 0.526 | 0.006 |

> **How to interpret p-values here:** These tests are exploratory diagnostics of **upstream source-data structure**, not patient-level or clinical tests. The two source files contain repeated upstream variant representations and are not independent patient cohorts. Therefore, a small p-value does **not** establish biological, clinical, diagnostic, prognostic, or treatment significance. Cramér’s V is included so that the report does not rely on p-values alone.

Regenerate the statistical report after ETL:

```bash
python src/generate_exploratory_statistics.py \
  --input data/processed/full_variants_canonical.csv \
  --report-dir reports
```

## Research-only evidence framework

| Evidence category | What is recorded | What is not inferred |
|---|---|---|
| Published source assertion | ClinVar status, review level, stable identifier, and retrieval date | A new clinical classification |
| Molecular annotation | VEP consequence, selected transcript, HGVS, and raw-output filename | Disease causality from consequence alone |
| Population context | Versioned gnomAD observation | A standalone pathogenicity conclusion |
| Cancer-resource context | Exact-variant, gene-level, or no-record outcome with date | Treatment or patient-level recommendation |
| Literature context | What the cited study actually evaluated | A substitute for formal laboratory evidence weighting |

## Limitations

The source data are public and pre-annotated. This project does not process FASTQ/BAM files, perform alignment or variant calling, evaluate coverage, conduct orthogonal confirmation, apply a validated laboratory assay, use patient phenotype or family-history data, or perform clinical sign-out. The full data files should not be treated as continuously current; the repository documents a pinned source version and local hashes.

The final four-variant evidence review is intentionally small. It demonstrates traceability, build-aware selection, public-resource review, and scientific communication; it is not representative of all BRCA1/BRCA2 variation and cannot establish performance, sensitivity, specificity, or clinical utility.

## Further development

Future work may add a data dictionary, automated schema-drift tests, explicit variant-normalisation demonstrations, a documented transcript-selection policy, broader non-pathogenic/VUS/conflicting-assertion sampling, and supervised review by qualified clinical laboratory personnel.

## Portfolio relevance

This portfolio demonstrates the combination of data engineering, genomic-data QC, reproducibility, structured evidence review, and cautious scientific communication that supports entry-level work in clinical-genomics annotation environments. It does not claim clinical NGS sign-out or independent interpretation authority.

## Data attribution and licence

See `ATTRIBUTION.md`. Do not upload patient data, identifiable genetics information, employer-proprietary materials, or source material whose licence or terms do not permit redistribution.

## References

[1]: https://www.kaggle.com/datasets/mannekuntanagendra/breast-cancer-mutationanalysis-clinvar-ensembl-vep "Kaggle source dataset"

[2]: https://www.ensembl.org/info/docs/tools/vep/index.html "Ensembl Variant Effect Predictor documentation"

[3]: https://www.ncbi.nlm.nih.gov/clinvar/ "ClinVar"

[4]: https://gnomad.broadinstitute.org/help "gnomAD documentation"

[5]: https://docs.civicdb.org/ "CIViC documentation"

[6]: https://docs.cbioportal.org/web-api-and-clients/ "cBioPortal documentation"
