# Scientific Sources and Research-Only Evidence Ledger

**Last reviewed:** August 23, 2026  
**Scope:** Public evidence context for a four-variant educational BRCA1/BRCA2 annotation case study.

> This document records sources used to understand and describe public evidence. It does not apply clinical evidence codes, establish a diagnosis, reclassify a variant, or recommend clinical action.

## How sources are used

| Source category | Role in this repository | Boundary |
|---|---|---|
| ClinVar variation record | Current published assertion, review status, variant identity, and source-linked functional-data entry | A database assertion is attributed to ClinVar/submitters, not to this portfolio author |
| Ensembl VEP | Molecular-consequence annotation of the exact GRCh38 representation | A predicted consequence is not a clinical classification |
| gnomAD | Current population-frequency observation with data version/build/date | Frequency is recorded as evidence context, not used as a standalone decision rule |
| CIViC/cBioPortal | Exact-variant or gene-level cancer context | No therapy conclusion, somatic tier, or patient-level conclusion |
| Scientific literature | Assay, mechanism, or framework context | The wording must match what the cited study evaluated |

## Variant-to-source map

| Variant | Primary variant-specific source | Supporting scientific context | Research-only wording rule |
|---|---|---|---|
| BRCA1 c.190T>G (p.Cys64Gly), V1 | ClinVar Variation ID 17660 | Findlay et al. saturation genome editing | Attribute the pathological assertion and functional-data record to the source; do not make a new classification. |
| BRCA1 c.181T>G (p.Cys61Gly), V2 | ClinVar Variation ID 17661 | Millot et al. functional-assay review; Findlay et al. | State that the published review describes loss of activity in its experimental context. |
| BRCA1 c.68_69del (p.Glu23fs), V3 | ClinVar Variation ID 17662 | ClinGen ENIGMA BRCA1/2 VCEP recommendations | Describe the source-recorded frameshift and established loss-of-function mechanism context; do not apply PVS1 yourself. |
| BRCA2 c.6275_6276del (p.Leu2092fs), V4 | ClinVar Variation ID 9318 | Huang et al. BRCA2 functional/classification study | Separate the exact ClinVar record from broader BRCA2 loss-of-function literature context. |

## Publicly accessible sources

1. **ClinVar Variation ID 17660: BRCA1 c.190T>G (p.Cys64Gly).** Provides a current source assertion, review status, identity/coordinates, and a linked functional-data entry.  
   https://www.ncbi.nlm.nih.gov/clinvar/variation/17660/

2. **ClinVar Variation ID 17661: BRCA1 c.181T>G (p.Cys61Gly).** Provides an expert-panel source assertion and a linked functional-data entry.  
   https://www.ncbi.nlm.nih.gov/clinvar/variation/17661/

3. **ClinVar Variation ID 17662: BRCA1 c.68_69del (p.Glu23fs).** Provides an expert-panel source assertion, the frameshift identity, and linked curation context.  
   https://www.ncbi.nlm.nih.gov/clinvar/variation/17662/

4. **ClinVar Variation ID 9318: BRCA2 c.6275_6276del (p.Leu2092fs).** Provides an expert-panel source assertion, the frameshift identity, and source-linked population data fields.  
   https://www.ncbi.nlm.nih.gov/clinvar/variation/9318/

5. **Findlay GM et al. Accurate classification of BRCA1 variants with saturation genome editing. Nature. 2018.** The study assayed 96.5% of possible SNVs in 13 BRCA1 exons and reported strong concordance between its functional scores and established variant assessments. It is relevant to the BRCA1 missense functional-data context.  
   https://pmc.ncbi.nlm.nih.gov/articles/PMC6181777/

6. **Millot GA et al. A Guide for Functional Analysis of BRCA1 Variants of Uncertain Significance. Human Mutation. 2012.** The review explains BRCA1 functional-assay concepts, including the RING domain and published p.Cys61Gly assay findings.  
   https://pmc.ncbi.nlm.nih.gov/articles/PMC3470782/

7. **Parsons MT et al. Evidence-based recommendations for gene-specific ACMG/AMP variant classification from the ClinGen ENIGMA BRCA1 and BRCA2 VCEP. American Journal of Human Genetics. 2024.** This paper explains gene-specific evidence specifications and why formal classification requires calibrated, structured application of evidence.  
   https://pmc.ncbi.nlm.nih.gov/articles/PMC11393667/

8. **Huang H et al. Functional evaluation and clinical classification of BRCA2 variants. Nature. 2025.** This study provides BRCA2 loss-of-function and functional-classification context but does not itself evaluate the V4 frameshift.  
   https://pmc.ncbi.nlm.nih.gov/articles/PMC11821525/

9. **Ensembl Variant Effect Predictor documentation.**  
   https://www.ensembl.org/info/docs/tools/vep/index.html

10. **gnomAD documentation.**  
    https://gnomad.broadinstitute.org/help

11. **CIViC documentation.**  
    https://docs.civicdb.org/

12. **cBioPortal documentation.**  
    https://docs.cbioportal.org/web-api-and-clients/

## Citation example for the final evidence table

> “ClinVar Variation ID 17661 reports an expert-panel source assertion for BRCA1 c.181T>G (p.Cys61Gly), checked on 2026-08-23. Published functional literature describes p.Cys61Gly as disrupting activity in a defined assay setting; this portfolio reports the source context and does not independently classify the variant.” [2] [6]

## References

[1]: https://www.ncbi.nlm.nih.gov/clinvar/ "ClinVar"

[2]: https://pmc.ncbi.nlm.nih.gov/articles/PMC6181777/ "Findlay et al. (2018)"

[3]: https://pmc.ncbi.nlm.nih.gov/articles/PMC3470782/ "Millot et al. (2012)"

[4]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11393667/ "Parsons et al. (2024)"

[5]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11821525/ "Huang et al. (2025)"
