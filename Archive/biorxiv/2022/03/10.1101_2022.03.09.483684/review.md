## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present a joint single-cell atlas of gene expression and chromatin accessibility from the adult human retina comprising over 50,000 cells. They integrate this atlas with HiChIP enhancer connectome data, eQTL data, and base-resolution deep learning models to prioritize noncoding SNPs from GWAS of five eye diseases, predict SNP effects on transcription factor binding, and nominate target genes. They state that this approach nominates pathogenic SNP-target gene interactions and provides a resource for interpreting noncoding variation in the eye.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data were supplied
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, model architecture and training details, validation metrics, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable resource and an integrative analytical framework for interpreting noncoding GWAS variants in eye disease. The combination of single-cell multiome data with chromatin conformation, eQTL, and deep learning predictions is conceptually strong and timely. However, the abstract alone provides no quantitative evidence, no validation of the deep learning models, no details on how causal variants were distinguished from merely associated ones, and no assessment of false positive rates. The central claims of causal nomination and target gene assignment cannot be evaluated from the supplied material. The work is likely of interest to the ophthalmic genetics and regulatory genomics communities, but the case for its conclusions is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers in ophthalmic genetics, particularly those studying age-related macular degeneration, glaucoma, diabetic retinopathy, myopia, and macular telangiectasia, would be interested in the prioritized variant-target gene pairs. Computational biologists working on noncoding variant interpretation, single-cell epigenomics, and deep learning applications to regulatory genomics would also find the resource and framework relevant. Clinicians and translational researchers seeking to bridge GWAS findings to biological mechanisms may use the nominated interactions as hypotheses for functional follow-up.
- **Major strengths** The integration of multiple complementary data types (single-cell chromatin accessibility, gene expression, HiChIP, eQTL, and deep learning) is a sophisticated and appropriate approach for the problem of noncoding variant interpretation. The focus on the human retina with over 50,000 cells provides a disease-relevant tissue context. The scope across five common eye diseases increases the potential utility of the resource. The explicit goal of moving from association to causal nomination addresses a well-recognized gap in the field.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Evidence sufficiency  
    **Claim pointer** The abstract claims that the approach "predict[s] noncoding SNPs with causal roles in eye disease" and "nominate[s] pathogenic SNP-target gene interactions."  
    **Evidence pointer** Abstract, results section not provided; location not provided  
    **Concern** The abstract provides no quantitative metrics for the deep learning model performance, no validation against known causal variants, no experimental or orthogonal confirmation of any nominated interaction, and no estimate of precision or false discovery rate. The term "causal" is used without evidence that causality was tested beyond computational prediction.  
    **Why it matters** Causal nomination is a strong claim that requires demonstration that the predictions outperform chance and that at least a subset of predictions are supported by independent evidence. Without such metrics, the reader cannot assess whether the nominated variants are likely to be true positives or artifacts of the model.  
    **Resolution test** Provide model performance metrics (e.g., AUROC, AUPRC) on held-out or independent data, benchmark against known causal variants, and include at least one orthogonal validation (e.g., reporter assay, CRISPR perturbation, or concordance with independent functional data) for a nominated interaction.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Reproducibility and transparency  
    **Claim pointer** The abstract states that the atlas contains ">50,000 cells" and that the integration includes "HiChIP enhancer connectome, eQTL data, and base-resolution deep learning models."  
    **Evidence pointer** Abstract, methods not provided; location not provided  
    **Concern** No details are given on the number of donors, cell type composition, quality control thresholds, sequencing depth, or how the HiChIP and eQTL datasets were generated or sourced. The deep learning model architecture, training data, and genomic resolution are not described.  
    **Why it matters** Reproducibility is a core requirement for a resource paper. Without these details, other groups cannot apply the same methods or assess whether the atlas is representative and of sufficient quality. The absence of model details prevents evaluation of whether the predictions are technically sound.  
    **Resolution test** Provide a full methods section with donor information, cell type annotation strategy, quality metrics, data sources for HiChIP and eQTL, and complete model architecture and training details.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** No  
    **Axis** Generalizability and disease coverage  
    **Claim pointer** The abstract claims the approach is applicable to "age-related macular degeneration, glaucoma, diabetic retinopathy, myopia, and type 2 macular telangiectasia."  
    **Evidence pointer** Abstract, results not provided; location not provided  
    **Concern** The abstract does not state how many GWAS loci or SNPs were analyzed per disease, how many were prioritized, or whether the cell types implicated by the prioritized variants are consistent with known disease biology for each condition.  
    **Why it matters** The utility of the resource depends on whether it yields disease-relevant findings across all five conditions. Without per-disease results, the reader cannot judge whether the approach is broadly applicable or only effective for a subset.  
    **Resolution test** Provide per-disease summaries of the number of loci analyzed, number of prioritized variants, and the cell types and target genes nominated, with comparison to known disease mechanisms.

- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Clarity  
    **Affected element** Terminology  
    **Evidence pointer** Abstract, "causal roles" and "pathogenic"  
    **Issue** The terms "causal" and "pathogenic" are used interchangeably but may imply different levels of evidence.  
    **Required correction** Define the criteria used to assign "causal" or "pathogenic" status and distinguish computational prediction from experimental validation.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Completeness  
    **Affected element** Resource availability  
    **Evidence pointer** Abstract, "provide a potentially powerful resource"  
    **Issue** No statement is made about data availability, accession numbers, or whether the deep learning models will be released.  
    **Required correction** State where the atlas, processed data, and model code will be deposited and how access will be provided.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Interpretation  
    **Affected element** Novelty of target genes  
    **Evidence pointer** Abstract, "define their known and novel target genes"  
    **Issue** The abstract does not indicate how many target genes are novel or how novelty was determined.  
    **Required correction** Quantify the number of novel target genes and describe the criteria for defining novelty relative to existing databases.

## Risk / unsupported claims
- The claim that the approach "predict[s] noncoding SNPs with causal roles" is unsupported without model validation metrics and independent confirmation.
- The claim that "pathogenic SNP-target gene interactions" are nominated is unsupported without per-disease results or any functional validation.
- The claim that the atlas is a "potentially powerful resource" is plausible but unverifiable from the abstract alone; no quality metrics or comparison to existing datasets are provided.
- The generalizability of the approach across all five diseases is not assessable without per-disease outcome data.
- The novelty of the resource relative to existing retinal single-cell atlases or other variant prioritization methods cannot be evaluated without a comparison to prior work.