## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, figure legends, and footnotes. Figures themselves were not provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment of evidence with conclusions. No assessment of formatting or editorial style.
- **Shared manuscript claim summary** The authors train a gapped k-mer support vector machine (GKM-SVM) on adult human retinal ATAC-seq data to distinguish putative cis-regulatory elements from genomic background, and use deltaSVM to score all possible single nucleotide variants within a hold-out set of 3,773 retinal CREs. They report that predicted impact scores correlate with population allele frequency, phylogenetic conservation, transcription factor motif disruption, and existing massively parallel reporter assay data, and they provide a UCSC genome browser track ("VISIONS") covering approximately 39,000 putative retinal CREs.
- **Visible evidence base** Abstract, Introduction, Methods, Results, Discussion, Author Contributions, Acknowledgements, Footnotes. Figure legends are present but figure images are not. Supplementary figure legends are referenced but not provided.
- **Missing materials affecting confidence** Figure images and supplementary figures are not available. The MPRA dataset used for external validation is described but not shown in detail. The exact composition of the negative training set after GC-matching is not fully described. The custom saturation mutagenesis script is not provided. The full list of hyperparameters tested is not given.

## Reviewer
- **Overall assessment** This manuscript presents a straightforward application of an established machine learning framework (GKM-SVM/deltaSVM) to a new tissue type, the adult human retina. The work is technically competent and the results are largely consistent with prior applications of this method in other tissues. The main contributions are the tissue-specific model and the publicly available variant scoring resource. However, the novelty is incremental, and several validation steps are either missing or under-described. The correlation with MPRA data is a key claim but is presented with limited quantitative detail. The manuscript would benefit from clearer reporting of validation metrics and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Researchers in ophthalmic genetics, particularly those studying non-coding variants in inherited retinal diseases, would find the VISIONS track useful for variant prioritization. Computational biologists working on regulatory genomics and machine learning applications to non-coding variation may also be interested, though the methodological novelty is limited. Clinical geneticists seeking to interpret variants of uncertain significance in retinal disease genes could use this resource as a secondary filter.
- **Major strengths** The use of adult human retinal ATAC-seq data is appropriate and addresses a gap in tissue-specific regulatory annotation. The GKM-SVM/deltaSVM approach is well-established and the authors correctly apply it with standard hyperparameters. The validation against allele frequency, conservation, and MPRA data is a reasonable multi-pronged strategy. The public availability of the VISIONS track is a practical contribution.
- **Major Concerns** The MPRA validation is described qualitatively with a single Pearson correlation coefficient of 0.506, but the number of variants compared, the source of the MPRA data, and the statistical significance of the correlation are not reported. The claim of tissue specificity is supported by comparison to non-retinal ATAC-seq datasets, but the choice of comparators (RPE, PVC, fibroblasts) is limited and the interpretation of "neutral" scoring for RPE is not discussed. The manuscript does not compare the performance of this model to existing models such as DeepSEA or Enformer, which limits the assessment of added value. The saturation mutagenesis is performed only on the hold-out set of 3,773 CREs, but the final resource covers 39,000 CREs; the scoring for the additional CREs is not described or validated.
- **Technical failings that need to be addressed before the case is established** The MPRA correlation analysis needs full reporting of sample size, statistical test, and confidence intervals. The method for extending predictions from 3,773 to 39,000 CREs must be described. The absence of comparison to existing predictive models weakens the claim of utility.
- **Assessment against Nature-style criteria** Originality: moderate. The application to human retina is new, but the method is not. Scientific importance: moderate. The resource may be useful, but the biological insights are limited. Interdisciplinary readership: limited. The work is primarily of interest to ophthalmic genetics and regulatory genomics specialists. Technical soundness: adequate but with gaps in validation reporting. Readability for nonspecialists: the manuscript is generally clear, though some methods details assume familiarity with the GKM-SVM framework.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the MPRA validation reporting and the description of the extended scoring pipeline.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that predicted impact scores correlate with massively parallel reporter assay data, citing a Pearson correlation coefficient of 0.506.
- **Evidence pointer** Results section, Figure 5, location not provided
- **Concern** The MPRA validation is a central piece of evidence for the biological relevance of the deltaSVM scores, but the reporting is insufficient. The number of variants compared, the source and species of the MPRA data, the statistical significance of the correlation, and the confidence intervals are not provided. The figure is referenced but not available for review.
- **Why it matters** Without full reporting of the MPRA comparison, the reader cannot assess whether the correlation is robust or driven by a small number of outliers. The claim of cross-species and cross-assay validity is a key part of the paper's argument.
- **Resolution test** Provide the full MPRA comparison details, including the number of variants, the statistical test used, the p-value, and a scatter plot with confidence intervals. If the MPRA data are from a published study, cite it explicitly and describe how the comparison was performed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors state that the VISIONS resource covers approximately 39,000 putative retinal CREs, but the saturation mutagenesis and scoring are described only for the 3,773 CREs in the hold-out set.
- **Evidence pointer** Methods section, Results section, location not provided
- **Concern** The manuscript does not describe how the deltaSVM scores were generated for the additional approximately 35,000 CREs beyond the hold-out set. It is unclear whether the same model was applied, whether the same saturation mutagenesis procedure was used, and whether any additional validation was performed on this larger set.
- **Why it matters** The VISIONS resource is a major deliverable of the paper. If the scoring pipeline for the full set is not described, the resource cannot be reproduced or evaluated.
- **Resolution test** Add a clear description of the pipeline used to generate scores for all 39,000 CREs, including any filtering steps, and state whether the hold-out set was included in the final resource.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparative benchmarking
- **Claim pointer** The authors imply that their model provides a useful tool for variant prioritization in retinal CREs, but they do not compare its performance to existing predictive models.
- **Evidence pointer** Results section, Discussion section, location not provided
- **Concern** Several models exist for predicting the functional impact of non-coding variants, including DeepSEA, Enformer, and CADD. The manuscript does not compare the performance of the GKM-SVM model to these alternatives on the same hold-out set or on the MPRA data.
- **Why it matters** Without a benchmark comparison, the reader cannot determine whether this model offers any advantage over existing tools, which is important for assessing its practical utility.
- **Resolution test** Add a comparison of the deltaSVM scores to at least one or two existing models on the same variant set, reporting correlation or classification metrics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, negative training set generation
- **Evidence pointer** Methods section, Supplementary Figure 1, location not provided
- **Issue** The description of the negative training set states that 1,000,000 random regions were generated and filtered against positive data, but the final number of negative regions used for training is not stated. The GC-matching procedure is referenced but not detailed.
- **Required correction** State the final number of negative regions used and briefly describe the GC-matching procedure or cite the relevant tool.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, allele frequency and conservation analyses
- **Evidence pointer** Results section, Figure 3, location not provided
- **Issue** The manuscript reports p-values for pairwise comparisons but does not state the statistical test used for the allele frequency and conservation comparisons. The number of variants in each bin is not reported.
- **Required correction** Specify the statistical tests used and report the number of variants in each bin.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, saturation mutagenesis script
- **Evidence pointer** Methods section, location not provided
- **Issue** The custom script used for in silico saturation mutagenesis is described but not provided or referenced.
- **Required correction** Provide the script as supplementary material or deposit it in a public repository.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, tissue specificity
- **Evidence pointer** Discussion section, location not provided
- **Issue** The authors state that the model is tissue-specific, but the comparison to RPE, PVC, and fibroblasts is limited. The RPE scores are described as "neutral," but the implications of this are not discussed.
- **Required correction** Clarify what "neutral" means in this context and discuss whether the model is truly retina-specific or simply trained on retina-derived data.

## Risk / unsupported claims
- The claim that the model "accurately predicted" MPRA expression changes is not fully supported without detailed statistical reporting.
- The claim that the model is "robust across species" is based on a single comparison to a mouse Rhodopsin promoter and may be overstated.
- The claim that the VISIONS resource can "assist in identifying and interpreting variants of interest" is plausible but not directly demonstrated with a clinical or functional example.
- The statement that the model "specifically distinguishes retinal CREs versus genomic background" is supported by cross-validation, but the biological meaning of this distinction is not deeply explored.