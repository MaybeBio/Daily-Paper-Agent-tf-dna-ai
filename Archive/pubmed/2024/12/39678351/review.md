## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality based solely on the supplied material
- **Shared manuscript claim summary** The authors present ProSNP-DL, a deep learning approach integrating a sequence-based enhancer model with a sliding-window strategy, to identify non-coding regulatory SNPs (eSNPs) with higher alternate allele frequency in men of African ancestry that may contribute to elevated prostate cancer risk. They report approximately 2,000 such eSNPs, propose complementary oncogenic and tumor-suppressive mechanisms, validate effects on FOXA1 binding experimentally, and construct a polygenic risk score that adds predictive value beyond existing GWAS-based scores.
- **Visible evidence base** Main figures 1-6 (referenced), supplementary figures S1-S4 (referenced), supplementary tables S1-S5 (referenced), methods descriptions, and data availability statements
- **Missing materials affecting confidence** Actual figure images and supplementary files not provided; specific numerical results (effect sizes, confidence intervals, p-values) for key comparisons not fully reported in text; details of the deep learning model training and hyperparameter selection not fully described; complete PRS performance metrics not shown

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question regarding ancestry-specific genetic contributions to prostate cancer risk, with a focus on non-coding regulatory variation. The methodological approach is creative and integrates computational prediction with experimental validation. However, several technical concerns and gaps in the presented evidence limit the strength of the conclusions as currently stated. The claim of approximately 2,000 eSNPs underlying higher risk in African ancestry men requires stronger statistical support and clearer demonstration of specificity. The functional validation is limited to a single TF and two cell lines. The PRS analysis, while promising, needs more rigorous benchmarking and independent replication to establish clinical or translational utility. The manuscript would benefit from additional quantitative detail and clarification of several methodological choices.

- **Who would be interested in the results, and why** Genetic epidemiologists studying prostate cancer susceptibility across ancestral populations would find the eSNP catalog and PRS approach relevant. Researchers in regulatory genomics and gene regulation would be interested in the deep learning application to enhancer function prediction. Clinicians and translational researchers focused on reducing health disparities in prostate cancer outcomes may find the ancestry-specific risk variants valuable for future screening or risk stratification efforts. Computational biologists developing deep learning methods for variant effect prediction would also find the methodological framework of interest.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and specificity of eSNP identification
- **Claim pointer** The manuscript claims identification of approximately 2,000 eSNPs with higher alternate allele frequency in African ancestry men that potentially affect enhancer function associated with prostate cancer susceptibility.
- **Evidence pointer** Results section "ProSNP-DL identifies enhancer SNPs dominant in an African ancestral population and associated with PrCa risk and patient survival"; Figure 3
- **Concern** The selection of 491K SNPs based on top 5% FST is an arbitrary threshold that may introduce ascertainment bias. The manuscript does not report how sensitive the eSNP identification is to this threshold. Additionally, the validation using allelic imbalance in H3K27ac reads is based on only 5 European American prostate cancer patients, which is a very small sample and does not include African ancestry individuals where the eSNPs are claimed to be relevant. The statistical framework for declaring a SNP as an eSNP (EWN threshold of 5) needs justification, and the false discovery rate for the genome-wide scan is not reported.
- **Why it matters** Without demonstrating robustness to analytical choices and providing appropriate multiple testing control, the core claim of identifying a specific set of approximately 2,000 eSNPs cannot be considered firmly established. The limited validation sample undermines the generalizability of the functional evidence.
- **Resolution test** Provide sensitivity analyses varying the FST threshold and EWN cutoff. Report FDR or permutation-based significance thresholds for eSNP identification. Include allelic imbalance validation in African ancestry samples or justify why European-derived cell lines are sufficient.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation depth
- **Claim pointer** The manuscript claims experimental validation of eSNP effects on FOXA1 binding, specifically that alternate alleles at gained eSNPs show increased FOXA1 binding and at lost eSNPs show decreased binding.
- **Evidence pointer** Results section "eSNPs disrupt binding of key prostate transcription factors including the FOX and the HOX families"; Figure 5
- **Concern** The experimental validation is limited to FOXA1 in two cell lines (LNCaP and MDA PCa 2B). While FOXA1 is a relevant pioneer factor, the computational analysis identified multiple TF families (FOX, AR, HOX) as potentially disrupted. The manuscript does not validate effects on AR or HOX binding. Furthermore, the ChIP-seq comparison between cell lines of different ancestral origins confounds ancestry with cell line identity, making it difficult to attribute observed differences specifically to ancestry-related genetic effects. The manuscript does not report whether the observed binding differences at eSNP loci are statistically significant after multiple testing correction across all loci examined.
- **Why it matters** The claim of mechanistic insight through TF disruption is central to the paper's contribution. Validation limited to one TF in two cell lines with potential confounding is insufficient to support the broader mechanistic conclusions.
- **Resolution test** Validate additional TFs (at minimum AR) or provide a clear rationale for focusing solely on FOXA1. Include additional cell lines or isogenic systems to control for ancestry effects. Report multiple testing corrected significance for ChIP-seq binding comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** PRS clinical utility and generalizability
- **Claim pointer** The manuscript claims that a PRS derived from eSNPs adds value to the previously reported gold-standard PRS in assessing prostate cancer risk.
- **Evidence pointer** Results section "Polygenic risk score derived from eSNPs can be helpful to differentiate between cases and controls of PrCa"; Figure 6
- **Concern** The PRS analysis is performed using cross-validation within a European ancestry cohort and then applied to an independent African ancestry cohort. However, the manuscript does not report key performance metrics such as area under the curve (AUC), calibration, or net reclassification improvement. The claim of "adds value" requires demonstration of incremental predictive ability beyond the existing PRS, but the statistical significance of the improvement is not stated. The African ancestry cohort is described as being from Ghana, which may not represent the broader genetic diversity of African ancestry populations, particularly African Americans.
- **Why it matters** For the PRS to have translational relevance, its performance must be rigorously quantified and shown to generalize across diverse African ancestry populations. Without these metrics, the clinical utility claim is not supported.
- **Resolution test** Report AUC, calibration plots, and net reclassification improvement for eSNP-based PRS compared to PGS-545 alone. Validate in additional African ancestry cohorts, including African American populations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Causal inference
- **Claim pointer** The manuscript states that eSNPs "may influence PrCa development" through complementary mechanisms involving immune suppression, telomere elongation, de-differentiation, and inhibition of apoptosis.
- **Evidence pointer** Results section "The gained and lost activity eSNPs may facilitate carcinogenesis via complementary mechanisms"; Figure 4
- **Concern** The pathway enrichment analyses (GREAT, CancerSEA) are descriptive and correlational. The manuscript does not provide direct experimental evidence linking specific eSNPs to changes in expression of target genes or to the proposed downstream phenotypes (immune suppression, telomere elongation, etc.). The regression analysis relating eSNP categories to adult-fetal expression changes is indirect and does not establish causality. The connection between eSNP effects on enhancer activity and actual disease-relevant phenotypes remains speculative.
- **Why it matters** The proposed dual-mechanism model is intellectually appealing but requires direct functional evidence. Without causal validation, the mechanistic claims remain hypotheses rather than established findings.
- **Resolution test** Perform CRISPR-based perturbation of representative eSNP loci in relevant cell lines and measure effects on target gene expression and cellular phenotypes. Alternatively, use expression quantitative trait locus (eQTL) analyses in prostate tissue to link eSNPs to gene expression changes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Deep learning model training details
- **Evidence pointer** Methods section "A deep convolutional neural network model of prostate enhancers"
- **Issue** The manuscript states the model architecture is identical to a previous study but does not describe the training procedure, hyperparameter selection, or performance on held-out test sets in sufficient detail for reproduction.
- **Required correction** Provide a complete description of training parameters, optimization procedure, and model performance metrics (e.g., AUC on test set) either in the main text or supplementary materials.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Quantitative results
- **Evidence pointer** Throughout Results section
- **Issue** Many key results are described qualitatively without reporting specific numbers, effect sizes, or confidence intervals. For example, the degree of enrichment in Figure 3C and 3D is not quantified in the text.
- **Required correction** Add specific numerical values, confidence intervals, and p-values for all key comparisons in the text or figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Use of "eSNP" and related terms
- **Evidence pointer** Throughout manuscript
- **Issue** The term "eSNP" is used to refer to enhancer-affecting SNPs, but this abbreviation could be confused with expression SNPs (eSNPs) used elsewhere in the literature.
- **Required correction** Define the term clearly at first use and consider using a more specific abbreviation such as "enhancer-SNP" to avoid ambiguity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figure 1
- **Evidence pointer** Results section "Overview of the study"
- **Issue** The workflow figure is described but not shown in the provided text. The description is dense and may be difficult for nonspecialist readers to follow.
- **Required correction** Ensure the figure is clear and self-explanatory, with a simplified schematic that can be understood without deep familiarity with the methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion does not adequately address limitations such as the use of a single computational model, potential biases in training data, and the need for larger-scale validation.
- **Required correction** Add a dedicated limitations paragraph acknowledging these issues and suggesting directions for future work.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor of eSNP identification), R1-M2 (depth of functional validation), R1-M4 (causal evidence for proposed mechanisms). These concerns collectively undermine the central claims of the manuscript as currently presented.

- **Assessment against Nature-style criteria** 
  - **Originality** The application of a deep learning enhancer model with a sliding-window strategy to identify ancestry-specific regulatory variants is a novel contribution. The focus on African ancestry populations addresses an important gap in prostate cancer genetics. However, the conceptual framework of using functional prediction to prioritize variants is not entirely new.
  - **Scientific importance** The topic is of high importance given the substantial disparities in prostate cancer incidence and mortality affecting men of African ancestry. If the identified eSNPs and PRS prove robust, the work could have significant implications for understanding disease mechanisms and improving risk assessment. However, the current evidence does not yet establish this importance definitively.
  - **Interdisciplinary readership** The work bridges computational biology, genomics, and cancer biology, and would appeal to researchers across these fields. The clinical implications of the PRS component could extend interest to translational researchers. The technical nature of the methods may limit accessibility for some readers.
  - **Technical soundness** The computational approach is reasonable, but several technical concerns (statistical thresholds, validation depth, causal inference) need to be addressed. The experimental validation is a strength but is currently too limited in scope. The PRS analysis requires more rigorous benchmarking.
  - **Readability for nonspecialists** The manuscript is generally well-written but contains dense methodological sections that may be challenging for readers without computational genomics expertise. The abstract effectively summarizes the key findings, but the main text could benefit from clearer explanations of the approach and its significance.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem with a creative approach and has the potential to make a meaningful contribution. However, the current evidence does not fully support the strength of the claims made. The authors should address the statistical rigor of eSNP identification, expand functional validation, provide direct causal evidence for the proposed mechanisms, and strengthen the PRS benchmarking before the case is fully established.

## Risk / unsupported claims
- The claim of approximately 2,000 eSNPs underlying higher prostate cancer risk in African ancestry men is not fully supported without appropriate multiple testing correction and sensitivity analyses.
- The proposed dual-mechanism model (immune suppression/telomere elongation vs. de-differentiation/apoptosis inhibition) is presented as strongly supported but relies on indirect pathway enrichment analyses without direct causal evidence.
- The claim that eSNPs "add value" to existing PRS is not quantitatively supported as key performance metrics are not reported.
- The generalizability of the FOXA1 ChIP-seq validation from two cell lines to broader prostate cancer biology is not established.
- The statement that eSNPs "may underlie prostate-related disorders other than PrCa" is speculative and not directly tested in this study.