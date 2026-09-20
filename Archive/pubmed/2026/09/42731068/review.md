## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract
- **Shared manuscript claim summary** The authors report two siblings from a consanguineous Kurdish family with severe short stature, biochemical features of growth hormone deficiency, microcephaly, developmental delay, and a specific facial phenotype. Whole-exome sequencing identified a homozygous ZSWIM6 variant (c.3119G>A, p.Arg1040His). Functional assays in HEK293 cells and AlphaFold structural modelling were used to compare this variant with two previously reported heterozygous variants. The authors conclude that ZSWIM6 is a transcriptional regulator of HECW2 and ZIC2 promoters, that the three variants have distinct allele-specific effects, and that this is the first homozygous ZSWIM6 variant causing a novel syndromic phenotype.
- **Visible evidence base** Abstract text only. No figures, tables, methods details, or supplementary materials were provided.
- **Missing materials affecting confidence** Full manuscript, detailed clinical phenotyping data, segregation data for the variant, raw functional assay results, statistical analyses, structural modelling outputs, and any validation experiments. The absence of these materials limits the ability to assess the robustness of the functional conclusions and the strength of the genotype-phenotype correlation.

## Reviewer

- **Overall assessment** The abstract presents a potentially novel finding of a homozygous ZSWIM6 variant associated with a distinct syndromic phenotype. The clinical description is concise but plausible, and the proposed functional distinction between three variants is intellectually interesting. However, the evidence base provided is insufficient to establish the central claims. The functional assays are described only superficially, with no quantitative data, controls, or statistical support. The structural modelling is presented as predictive without validation. The link between the observed transcriptional effects and the clinical phenotype remains speculative. The claim of a "novel phenotype" requires more detailed clinical comparison with existing ZSWIM6-related disorders. Overall, the work is promising but not yet established from the provided material.
- **Who would be interested in the results, and why** Clinicians and geneticists in pediatric endocrinology, clinical genetics, and neurodevelopmental disorders would be interested in the potential expansion of the ZSWIM6-associated phenotypic spectrum and the first report of a recessive inheritance pattern. Researchers studying transcriptional regulation and genotype-phenotype correlations in developmental disorders may also find the allele-specific functional effects of interest.
- **Major strengths** The identification of a homozygous variant in a gene previously associated only with heterozygous de novo variants is a notable observation. The use of both functional assays and structural modelling to compare three distinct variants is a commendable integrative approach. The clinical description of the siblings, including biochemical features of GH deficiency, adds a potentially new dimension to ZSWIM6-related phenotypes.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional evidence
  - **Claim pointer** "Functional assays confirmed ZSWIM6 is a transcriptional regulator of the HECW2 and ZIC2 promoters. The three variants showed different effects on transcriptional regulation."
  - **Evidence pointer** Methods and Results sections, abstract only; location not provided
  - **Concern** The abstract states that dual-luciferase reporter assays were performed, but provides no quantitative data, no effect sizes, no statistical significance, no number of replicates, and no description of controls (e.g., wild-type ZSWIM6, empty vector, or normalization strategies). The claim that the three variants have distinct effects (loss-of-function, gain-of-function, derepression) is presented without any numerical support.
  - **Why it matters** The central mechanistic conclusion of the paper rests on these functional differences. Without quantitative evidence, the reader cannot assess whether the observed effects are robust, reproducible, or biologically meaningful. The distinction between loss-of-function and gain-of-function is particularly consequential for the proposed genotype-phenotype correlation.
  - **Resolution test** Provide the full reporter assay data, including mean and standard deviation for each construct and promoter, statistical tests (e.g., ANOVA with post-hoc comparisons), and a clear description of experimental replicates and controls. The data should demonstrate consistent and significant differences between variants and the wild-type.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Genotype-phenotype correlation
  - **Claim pointer** "We report the first-ever homozygous ZSWIM6 variant, causing a novel phenotype of severe syndromic short stature with biochemical features consistent with GH deficiency and developmental delay."
  - **Evidence pointer** Introduction and Conclusion sections, abstract only; location not provided
  - **Concern** The abstract describes the siblings' phenotype as "severe short stature with biochemical features of GH deficiency, microcephaly, and developmental delay" and notes "partial overlap with prior ZSWIM6-associated phenotypes." However, no clinical details are provided, such as growth parameters, GH stimulation test results, IGF-1 levels, brain imaging findings, or developmental assessment scores. The claim of a "novel phenotype" requires a systematic comparison with the known phenotypes of AFND and intellectual disability caused by heterozygous variants.
  - **Why it matters** The novelty of the phenotype is a key claim of the paper. Without detailed clinical data and a clear delineation of how this presentation differs from or overlaps with existing ZSWIM6-related disorders, the claim of a distinct syndrome is not substantiated. The biochemical features of GH deficiency are particularly important to document, as they are not previously associated with ZSWIM6.
  - **Resolution test** Provide a detailed clinical table or case descriptions, including auxological data, hormonal workup, imaging, and developmental assessments. Include a comparison table with previously reported ZSWIM6 cases to demonstrate the distinct features.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Genetic evidence
  - **Claim pointer** "Whole-exome sequencing identified a homozygous variant (c.3119G>A, p.Arg1040His) in gene ZSWIM6."
  - **Evidence pointer** Introduction section, abstract only; location not provided
  - **Concern** The abstract does not mention segregation analysis in the family, population frequency of the variant, or bioinformatic predictions of pathogenicity (e.g., CADD, PolyPhen, SIFT). It is also unclear whether the variant is absent or rare in control databases such as gnomAD. The consanguinity of the family is stated, which supports a recessive model, but formal segregation data are not described.
  - **Why it matters** Establishing that the variant is the cause of the phenotype requires evidence that it segregates with the disease in the family and is not a benign rare variant. The lack of this information weakens the genetic claim.
  - **Resolution test** Provide segregation data for all available family members, population frequency data, and in silico pathogenicity predictions. If possible, include functional validation in patient-derived cells or a complementary model.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Structural modelling
  - **Claim pointer** "The 3D structural modelling predicted that p.Arg1040His and p.Arg1163Trp alter local surface charge without disrupting the overall fold, while p.Arg913Ter truncates ZSWIM6, potentially affecting the DNA binding interactions."
  - **Evidence pointer** Methods and Results sections, abstract only; location not provided
  - **Concern** The abstract states that AlphaFold was used for structural modelling, but no details are given on the confidence of the predictions, the specific residues affected, or how the "local surface charge" changes were quantified. The claim that p.Arg913Ter affects DNA binding is speculative and not supported by any experimental data.
  - **Why it matters** The structural predictions are used to support the functional interpretation of the variants. Without details on the modelling approach and its limitations, the reader cannot evaluate the reliability of these predictions. The link between structural changes and functional outcomes is not established.
  - **Resolution test** Provide the AlphaFold models with confidence scores, a clear description of the predicted structural changes, and ideally experimental validation (e.g., DNA binding assays or protein stability measurements) to support the claims.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clinical description
  - **Affected element** Phenotype description
  - **Evidence pointer** Introduction section, abstract only; location not provided
  - **Issue** The facial phenotype is described as "specific" but only a few features are listed. It is unclear whether this facial gestalt is truly distinct from other syndromes or from the previously described ZSWIM6 phenotypes.
  - **Required correction** Provide a more comprehensive description of the facial features, ideally with photographs or a standardized dysmorphology assessment, and compare with published ZSWIM6 cases.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Derepression" claim
  - **Evidence pointer** Results section, abstract only; location not provided
  - **Issue** The term "derepression" for the p.Arg913Ter variant implies a specific mechanistic model (i.e., that ZSWIM6 normally represses HECW2). This is not established in the abstract and may overinterpret the data.
  - **Required correction** Use more neutral language, such as "increased HECW2 activation," unless a repression mechanism is experimentally demonstrated.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** "Key transcriptional regulator" claim
  - **Evidence pointer** Conclusion section, abstract only; location not provided
  - **Issue** The claim that ZSWIM6 is a "key transcriptional regulator" is based on two promoter assays in one cell type. This may be an overstatement given the limited experimental scope.
  - **Required correction** Soften the claim to "a transcriptional regulator of the tested promoters" or provide additional evidence for broader regulatory function.

## Risk / unsupported claims

- The claim that the p.Arg1040His variant causes a "novel phenotype" is not supported by the abstract alone, as detailed clinical data and comparison with existing phenotypes are not provided.
- The claim that the three variants have distinct functional effects (loss-of-function, gain-of-function, derepression) is unsupported without quantitative reporter assay data.
- The claim that p.Arg913Trp affects DNA binding is speculative and not experimentally validated.
- The claim that ZSWIM6 is a "key transcriptional regulator" is an overgeneralization based on limited promoter-specific assays.
- The genetic causality of the homozygous variant is not established without segregation and population frequency data.