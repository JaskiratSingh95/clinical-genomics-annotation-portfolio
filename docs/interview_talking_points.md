# Interview Talking Points: Variant Annotation Case Study

## A 45-second answer

“I completed a small research-only variant-annotation case study to build practical familiarity with the workflow behind NGS interpretation. I selected four documented BRCA1 and BRCA2 variants from a public breast-cancer mutation dataset, ensured that the inputs were in GRCh38 VCF format, and used Ensembl VEP to obtain transcript-level consequences. I then structured a review of the published ClinVar assertion, gnomAD population-frequency context, and cancer evidence from CIViC or cBioPortal. I was careful to separate source database classifications from my own research evidence summary and to state that it is not a clinical diagnostic report.”

## Questions you may be asked

| Interview question | Accurate answer direction |
|---|---|
| Why did you choose only four variants? | The aim was to demonstrate end-to-end rigor, reproducibility, and careful documentation in a feasible portfolio project rather than to make broad claims from a large unreviewed set. |
| What did VEP contribute? | VEP translated the GRCh38 variants into predicted transcript/protein consequences and returned useful co-located variant information. I treated it as an annotation resource, not a clinical classification engine. |
| What did ClinVar contribute? | I recorded the published assertion, review status, condition context, and retrieval date. I did not call the ClinVar value my own classification. |
| How did you use gnomAD? | I recorded allele-frequency context and dataset/build information, then noted that population frequency is supporting evidence and must be interpreted with phenotype, mechanism, assay, and broader evidence. |
| What did cancer resources add? | CIViC can provide curated cancer-variant evidence, while cBioPortal can provide cohort-level cancer-genomics context. I documented whether information was variant-specific, gene-level, or unavailable. |
| What are the project’s limitations? | It uses public, pre-curated data; it does not start from raw sequencing reads; it does not validate a calling pipeline; it does not perform a clinical classification; and it does not provide patient-level interpretation or treatment advice. |

## Do not say

Do not say that you “clinically classified” the variants, “validated an NGS pipeline,” or “made treatment recommendations.” The credible claim is that you built a **research portfolio demonstrating structured, reproducible use of public annotation resources and appropriate limits of interpretation**.
