# Exploratory Statistical Analysis of Source-Data Composition

**Generated:** 2026-08-23T21:48:48.295071+00:00  
**Input:** `data/processed/full_variants_canonical.csv`

> **Critical interpretation boundary:** These are exploratory chi-square tests of associations among **public, upstream source-data fields**. The data are not an independent patient cohort, and some variants occur in more than one source/build representation. The p-values do not indicate clinical, biological, diagnostic, prognostic, or treatment significance.

## Why these tests are included

The purpose is to document whether the ETL pipeline preserves measurable differences in **source-data composition** after duplicate-aware analysis. Each test reports an effect size, Cramér’s V, because a p-value alone can overstate importance in a large dataset.

## Duplicate-aware analysis design

| Test | Analysis unit | Duplicate handling |
|---|---|---|
| Gene symbol × upstream clinical-significance source field | One row per upstream AlleleID | GRCh38 is preferred where available, then a defined source-file priority is applied. |
| Gene symbol × source genome build | One row per upstream AlleleID and build combination | Duplicate source-file copies of the same AlleleID/build combination are removed. |

Rare categories with fewer than 10 observations are collapsed into `Other / rare source values` before calculation. The number of cells with expected count below five is reported as a diagnostic.

## Results

| Test | Analysis unit | N | χ² | df | Exploratory p-value | Cramér’s V | Expected-count cells <5 |
|---|---|---:|---:|---:|---:|---:|---:|
| gene_symbol × clinical_significance | One row per upstream AlleleID, preferring GRCh38 and then the defined source-file priority | 16,977 | 2228.20 | 10 | <0.001 | 0.362 | 2 |
| gene_symbol × assembly | One row per upstream AlleleID and genome-build combination; duplicate source-file copies removed | 33,645 | 1.28 | 2 | 0.526 | 0.006 | 0 |

## How to present these results

Use this phrasing in your portfolio or interview:

> “I included exploratory, duplicate-aware association tests to show that my reporting distinguishes statistical output from scientific interpretation. The tests describe associations among upstream source-data fields after ETL; I report both p-values and Cramér’s V, and I explicitly avoid treating those results as clinical significance or patient-level evidence.”

## Limitations

The tests use pre-annotated public source fields and not independent patient observations. The two source files share substantial upstream AlleleID overlap. A small p-value can reflect large source-record counts or data-capture structure rather than a meaningful biological effect. The reported Cramér’s V should be read as a descriptive measure of source-field association, not as evidence of clinical relevance.

## Reference

The calculations use Pearson’s chi-square contingency-table test and Cramér’s V effect size, implemented with SciPy’s `chi2_contingency` routine.[1]

[1]: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.contingency.chi2_contingency.html "SciPy chi2_contingency documentation"
