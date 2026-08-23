# Research-Only Evidence Summaries for the Four-Variant UHN Portfolio Case Study

**Prepared:** August 23, 2026  
**Use:** Educational portfolio and interview preparation only.

> **Critical boundary:** The text below does **not** independently classify any variant under ACMG/AMP, AMP/ASCO/CAP, or UHN procedures. It reports publicly available database assertions, predicted molecular consequences, and literature context. It must not be used for diagnosis, patient-specific risk assessment, treatment selection, or clinical reporting.

## How to label evidence in this repository

Use the following labels instead of calling your own conclusion an “evidence classification.” This is more accurate and professionally safer for a research portfolio.

| Label | Meaning in this project | What it is not |
|---|---|---|
| **Published source assertion** | The current classification and review status displayed by ClinVar, with source/date recorded | Your own clinical classification |
| **Molecular annotation** | Consequence, HGVS, transcript, and genome-build information returned by Ensembl VEP | Proof of disease causality |
| **Population context** | A documented gnomAD frequency observation, build, dataset/version, and retrieval date | A standalone pathogenicity conclusion |
| **Functional or literature context** | A precise statement of what a cited study or ClinVar functional-data submission reports | A substitute for a laboratory’s evidence-weighting process |
| **Cancer-resource context** | Exact-variant, gene-level, or no matching evidence in CIViC/cBioPortal, with a stable link/date | A therapy recommendation or somatic classification |
| **Research-only synthesis** | A short description of concordance and remaining limits | A diagnosis, clinical report, or new classification |

## Evidence summary table

| ID | Variant and VEP target | Published source assertion to record | Functional/literature context | Recommended research-only synthesis |
|---|---|---|---|---|
| **V1** | **BRCA1**; GRCh38 `17:43106478 A>C`; `NM_007294.4:c.190T>G`; p.Cys64Gly | ClinVar Variation ID **17660** displayed **Pathogenic**, “criteria provided, multiple submitters, no conflicts” when checked on 2026-08-23.[1] | The ClinVar record includes a functional-data entry marked “functionally abnormal” and cites the BRCA1 saturation-genome-editing study (PMID 30209399).[1] The study evaluated BRCA1 SNVs in functionally critical RING/BRCT exons and reports high concordance of its functional scores with established assessments; it must not be interpreted outside its defined assay context.[5] | “VEP annotates this GRCh38 SNV as a BRCA1 missense change, p.Cys64Gly. The live ClinVar record reports a pathogenic germline assertion with multiple submitters and no conflicts, and it links functional-data context. This portfolio records those source findings and does not independently assign an ACMG/AMP classification or infer patient-specific risk.” |
| **V2** | **BRCA1**; GRCh38 `17:43106487 A>C`; `NM_007294.4:c.181T>G`; p.Cys61Gly | ClinVar Variation ID **17661** displayed an expert-panel germline assertion for familial breast–ovarian cancer when checked on 2026-08-23.[2] | p.Cys61Gly lies within BRCA1’s N-terminal RING domain (amino acids 8–96). A peer-reviewed functional-analysis review reports that p.Cys61Gly, previously classified by genetic studies, showed loss of E2-enzyme interaction and ubiquitin-ligase activity in the cited experimental framework.[6] The ClinVar record also includes a “functionally abnormal” saturation-genome-editing submission.[2] | “VEP annotates this GRCh38 SNV as the BRCA1 missense change p.Cys61Gly. The ClinVar record provides an expert-panel source assertion, while published functional work describes impaired activity in an assay context. These findings are summarised as public evidence context only; no independent clinical classification is made.” |
| **V3** | **BRCA1**; GRCh38 VCF representation `17:43124027 ACT>A`; `NM_007294.4:c.68_69del`; p.Glu23fs | ClinVar Variation ID **17662** displayed an expert-panel assertion for BRCA1-related cancer predisposition when checked on 2026-08-23.[3] | ClinVar describes this as a two-base deletion with a frameshift protein consequence, and lists the expert-panel source.[3] The ClinGen ENIGMA BRCA1/2 VCEP paper states that BRCA1/2 loss of function is an established disease mechanism and discusses gene-specific evidence specifications, including the need to calibrate evidence strength.[7] | “VEP annotates this GRCh38 deletion as a BRCA1 frameshift. The live ClinVar record reports an expert-panel source assertion and the published gene-specific literature supports the relevance of loss-of-function mechanisms for BRCA1/2. This project reports that concordance but does not independently apply PVS1, assign a pathogenicity class, or issue clinical advice.” |
| **V4** | **BRCA2**; GRCh38 VCF representation `13:32340629 CTT>C`; `NM_000059.4:c.6275_6276del`; p.Leu2092fs | ClinVar Variation ID **9318** displayed an expert-panel germline assertion for familial breast–ovarian cancer when checked on 2026-08-23.[4] | ClinVar describes a two-base deletion with a BRCA2 frameshift consequence and displays linked population-frequency fields; record the **live gnomAD observation separately** with dataset/build/date rather than copying a static value.[4] A 2025 open-access BRCA2 study notes that germline BRCA2 loss-of-function variants predispose to several cancers and illustrates how functional evidence is integrated with other evidence types in formal clinical classification workflows.[8] | “VEP annotates this GRCh38 deletion as a BRCA2 frameshift. The live ClinVar record reports an expert-panel source assertion, and published BRCA2 literature provides broader loss-of-function context. This repository records source assertions and current population/cancer-resource observations without independently classifying the variant or making a treatment recommendation.” |

## Evidence notes for the completed CSV

The final evidence table should contain a short, attributable entry in each cell. The following pattern is recommended.

| Column | Example of safe wording |
|---|---|
| `source_clinvar_assertion` | `ClinVar Variation ID 17661: expert-panel germline assertion displayed on 2026-08-23; see stable URL.` |
| `vep_consequence_after_run` | `missense_variant; record raw VEP output filename and retrieval date.` |
| `gnomad_frequency_observation` | `Reviewed gnomAD [dataset/build/version] on [date]; [exact observation]. Population data are recorded as context only.` |
| `cancer_evidence_summary_or_gap` | `cBioPortal [study/URL] provided [exact-variant/gene-level] context; this is not a therapy recommendation.` |
| `research_only_interpretation` | `Published source assertion, VEP annotation, and publicly accessible literature/context were concordant at a high level. This portfolio does not independently classify the variant or make diagnostic, risk, or treatment conclusions.` |

## Source use guidance

Do not cite a paper merely because it discusses BRCA1/2 generally. In the completed repository, use the following approach:

1. Cite the **ClinVar variation page** for the current, variant-specific source assertion and review status.
2. Cite the **Findlay study** for the saturation-genome-editing functional-data context of the BRCA1 missense variants.
3. Cite the **Millot review** only for the specific RING-domain and p.Cys61Gly functional-assay context.
4. Cite the **ClinGen ENIGMA VCEP paper** to explain why this portfolio does not mechanically assign evidence codes or conduct its own clinical classification.
5. Cite the **Huang BRCA2 study** only for broader BRCA2 loss-of-function/function-assessment context; it does not itself evaluate the V4 frameshift.

## Recommended `scientific_sources.md` entries

The following sources are publicly accessible and verifiable. At least three should be included in the repository; using all five creates a better evidence trail.

[1]: https://www.ncbi.nlm.nih.gov/clinvar/variation/17660/ "ClinVar Variation ID 17660: BRCA1 c.190T>G (p.Cys64Gly)"

[2]: https://www.ncbi.nlm.nih.gov/clinvar/variation/17661/ "ClinVar Variation ID 17661: BRCA1 c.181T>G (p.Cys61Gly)"

[3]: https://www.ncbi.nlm.nih.gov/clinvar/variation/17662/ "ClinVar Variation ID 17662: BRCA1 c.68_69del (p.Glu23fs)"

[4]: https://www.ncbi.nlm.nih.gov/clinvar/variation/9318/ "ClinVar Variation ID 9318: BRCA2 c.6275_6276del (p.Leu2092fs)"

[5]: https://pmc.ncbi.nlm.nih.gov/articles/PMC6181777/ "Findlay et al. (2018), Accurate classification of BRCA1 variants with saturation genome editing"

[6]: https://pmc.ncbi.nlm.nih.gov/articles/PMC3470782/ "Millot et al. (2012), A Guide for Functional Analysis of BRCA1 Variants of Uncertain Significance"

[7]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11393667/ "Parsons et al. (2024), Gene-specific ACMG/AMP variant classification recommendations from the ClinGen ENIGMA BRCA1/2 VCEP"

[8]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11821525/ "Huang et al. (2025), Functional evaluation and clinical classification of BRCA2 variants"

[9]: https://www.ensembl.org/info/docs/tools/vep/index.html "Ensembl Variant Effect Predictor documentation"

[10]: https://gnomad.broadinstitute.org/help "gnomAD documentation"

[11]: https://docs.civicdb.org/ "CIViC documentation"

[12]: https://docs.cbioportal.org/web-api-and-clients/ "cBioPortal documentation"
