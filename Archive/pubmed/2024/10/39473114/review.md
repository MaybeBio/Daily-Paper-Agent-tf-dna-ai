## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report identification of two novel FUT1 variants, c.-35A>T and c.[-35A>T, 725T>G], in a patient with the para-Bombay B phenotype. They used serology, whole exome sequencing, and computational modeling to characterize the phenotype and predict functional effects of the variants.
- **Visible evidence base** Abstract text only; no raw data, sequence alignments, serological details, or model outputs are visible
- **Missing materials affecting confidence** Full methods, serological data tables, sequencing coverage and variant calling details, computational model parameters and validation, functional assays, and any confirmatory experiments

## Reviewer
- **Overall assessment** The abstract reports a clinically relevant case of para-Bombay phenotype associated with novel FUT1 variants. The serological and genotypic findings are internally consistent, and the computational predictions are plausible. However, the evidence base is limited to the abstract, and several claims regarding molecular mechanisms and functional consequences are not directly supported by experimental data. The work is of interest to transfusion medicine specialists and molecular hematologists, but the mechanistic conclusions require additional validation.
- **Who would be interested in the results, and why** Transfusion medicine specialists and blood bank scientists would be interested in the novel variants for diagnostic and screening purposes. Molecular geneticists studying glycosyltransferase mutations and their phenotypic consequences would also find the case informative. The findings may contribute to improving blood group genotyping panels and transfusion safety in populations where such variants are prevalent.
- **Major strengths** The study combines serological phenotyping with whole exome sequencing to establish a clear genotype-phenotype correlation. The identification of a compound heterozygous genotype with a novel promoter variant and a known missense variant is a meaningful contribution. The use of multiple computational tools to predict functional effects is a reasonable approach given the absence of functional assays.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The absence of functional validation for the promoter variant and the lack of experimental evidence linking the predicted structural changes to enzyme activity are the primary technical gaps. The computational predictions alone are insufficient to establish the molecular mechanism.
- **Assessment against Nature-style criteria** Originality is moderate; the finding of novel variants is incremental but useful. Scientific importance is limited to a narrow clinical and genetic context. Interdisciplinary readership is low, as the work is primarily relevant to transfusion medicine and blood group genetics. Technical soundness cannot be fully assessed from the abstract, but the described methods are appropriate. Readability for nonspecialists is adequate, though the abstract assumes familiarity with blood group genetics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly with functional validation of the promoter variant and clearer evidence for the mechanistic claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract states that the c.-35A>T promoter variant "may enable regulation of 1,2-L-FucT1 function at gene promoters" and that the p.Arg242 variant "may be detrimental, destabilizing, and probably damaging."
- **Evidence pointer** Results section, abstract; location not provided
- **Concern** The mechanistic claims regarding the promoter variant and the missense variant are based solely on computational predictions from DynaMut2, PolyPhen-2, AlphaFold2, and HDOCK. No experimental data, such as reporter assays, enzyme activity measurements, or expression studies, are presented to support these predictions.
- **Why it matters** The central conclusion that these variants cause the para-Bombay phenotype depends on demonstrating a functional effect. Without functional validation, the causal link between the identified variants and the observed phenotype remains speculative, and the clinical significance of the novel promoter variant is uncertain.
- **Resolution test** Provide experimental evidence, such as luciferase reporter assays for the promoter variant and enzyme activity assays for the missense variant, demonstrating reduced or absent 1,2-L-FucT1 function. Alternatively, present additional genetic or familial data that strengthen the association.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract states that "the genotypes of ABO, FUT1, and FUT2 were imputed using the genetic variations discovered in the whole exome sequencing data."
- **Evidence pointer** Materials and Methods section, abstract; location not provided
- **Concern** The abstract does not provide details on sequencing depth, variant calling thresholds, or how the compound heterozygous genotype was confirmed. It is unclear whether the c.-35A>T variant was validated by Sanger sequencing or other orthogonal methods, and whether the phase of the two variants on the same allele was experimentally determined.
- **Why it matters** Accurate genotyping and phasing are essential for establishing the compound heterozygous genotype and for excluding sequencing artifacts. Without these details, the reliability of the genetic findings cannot be assessed, and the conclusion that the phenotype is caused by this specific genotype is not fully supported.
- **Resolution test** Include details on sequencing quality metrics, variant validation methods, and phasing experiments. Provide confirmation of the c.-35A>T variant and the c.[-35A>T, 725T>G] allele by an independent method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive clarity
- **Claim pointer** The abstract concludes that "the phenotype is caused by a compound heterozygous genotype" and that the findings "may clarify the molecular mechanisms."
- **Evidence pointer** Results and Conclusion sections, abstract; location not provided
- **Concern** The abstract does not explain how the c.-35A>T variant alone, present on one allele, contributes to the phenotype, given that the other allele carries both c.-35A>T and c.725T>G. The relative contribution of each variant to the observed reduction in H antigen expression is not discussed.
- **Why it matters** Understanding the allelic contribution is important for interpreting the genotype-phenotype relationship and for counseling or screening purposes. The current presentation leaves ambiguity about whether the promoter variant alone is sufficient to cause the phenotype or whether it acts in combination with the missense variant.
- **Resolution test** Clarify the functional impact of each variant individually, either through experimental assays or through a more detailed discussion of predicted effects based on existing literature and computational evidence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Serological methods
- **Evidence pointer** Materials and Methods section, abstract; location not provided
- **Issue** The abstract states that ABH antigens and antibodies were detected in blood and saliva but does not specify the antibody titration results or the strength of antigen expression, which are critical for defining the para-Bombay phenotype.
- **Required correction** Include representative serological data, such as antigen typing scores and antibody titers, to substantiate the phenotype classification.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Computational modeling
- **Evidence pointer** Materials and Methods section, abstract; location not provided
- **Issue** The abstract mentions the use of AlphaFold2 and HDOCK but does not describe the modeling parameters, the template structures used, or the confidence scores of the predicted models.
- **Required correction** Provide details on model quality metrics, such as pLDDT scores for AlphaFold2 and docking scores for HDOCK, to allow assessment of the reliability of the structural predictions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Variant nomenclature
- **Evidence pointer** Title and Results section, abstract; location not provided
- **Issue** The variant notation c.[-35A>T, 725T>G] is used, but the abstract does not clarify whether this represents a single allele with both variants in cis, which is implied but not explicitly stated.
- **Required correction** Explicitly state the phase of the variants and confirm that the notation follows HGVS guidelines, to avoid ambiguity for readers.

## Risk / unsupported claims
- The claim that the c.-35A>T promoter variant "may enable regulation of 1,2-L-FucT1 function" is unsupported by experimental evidence and is based solely on computational prediction.
- The claim that p.Arg242 is "detrimental, destabilizing, and probably damaging" is based on in silico tools and lacks functional validation.
- The conclusion that the identified variants "cause" the para-Bombay phenotype is not fully established without functional or familial segregation data.
- The statement that the findings "may enhance blood transfusion safety" is speculative and not directly supported by the data presented.