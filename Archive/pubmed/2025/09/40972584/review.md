## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends)
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors present a network-based drug repurposing framework that integrates single-cell genomics data from the PsychENCODE2 cohort to identify cell-type-specific drug candidates for schizophrenia, bipolar disorder, and autism spectrum disorder. They construct gene regulatory networks across 23 cell types, apply graph neural networks to predict novel risk genes, use network proximity to nominate 220 drug molecules, identify 37 drugs with transcriptional reversal evidence, and report 335 drug-cell eQTLs.
- **Visible evidence base** Main text figures (Figures 1-6), supplementary figure references (Figures S1-S14), supplementary tables (Tables S1-S12), methods section, and data availability statements
- **Missing materials affecting confidence** Actual figure images, supplementary tables, detailed statistical outputs, validation metrics for GNN models, complete drug lists, and the web application interface were not available for direct inspection

## Reviewer

- **Overall assessment** This manuscript presents a technically ambitious and potentially valuable computational framework for cell-type-specific drug repurposing in psychiatric disorders. The integration of single-cell genomics with network medicine principles is timely and addresses a genuine gap in the field. However, several methodological concerns and validation gaps need to be addressed before the claims are fully supported. The work is likely to be of interest to the psychiatric genomics and computational drug discovery communities, but the current evidence base does not fully establish the clinical or translational utility of the proposed framework.

- **Who would be interested in the results, and why** Researchers in psychiatric genomics, computational drug repurposing, and single-cell biology would find this work relevant. The framework offers a template for integrating single-cell regulatory networks with drug-target databases, which could be adapted to other complex disorders. The drug-cell eQTL analysis may interest pharmacogenomics researchers. Clinicians and pharmaceutical researchers focused on psychiatric indications may also find the nominated drug candidates worth pursuing, though the translational gap remains substantial.

- **Major strengths**
  1. The use of population-scale single-cell data from the PsychENCODE2 cohort provides a robust and uniformly processed foundation for network construction.
  2. The integration of proximal and distal regulatory links (from snRNA-seq and snATAC-seq) to build composite GRNs is methodologically sound and leverages complementary data modalities.
  3. The GNN framework for predicting novel risk genes addresses a real limitation of module-based approaches that assume all genes within a module are equally relevant.
  4. The drug-cell eQTL analysis represents a novel contribution that connects drug targets to genetic variation at cell-type resolution.
  5. The sensitivity analyses (edge downsampling, alternative GRN inference methods) demonstrate awareness of methodological robustness.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of GNN predictions
- **Claim pointer** The authors claim that the GNN framework "predicts novel cell-type-disorder genes" and that these predictions are reliable based on the SFARI category 2 validation.
- **Evidence pointer** Figure 4, Section "Graph neural networks predict novel cell-type-disorder genes"
- **Concern** The validation strategy for the GNN model is incomplete. The authors validate by showing that withheld SFARI category 2 genes are enriched in the top decile of predictions, but this only demonstrates that the model can rank known risk genes highly. It does not validate that the novel predictions (genes not in any training set) are genuinely disease-relevant. The authors report AUPRC values but do not provide a clear baseline comparison or discuss the absolute performance in the context of class imbalance. Additionally, the claim that 249 genes are "novel" needs clarification: are these genes absent from all psychiatric disorder gene databases, or just from the specific training labels?
- **Why it matters** The entire drug repurposing pipeline depends on the reliability of the predicted risk genes. If the GNN predictions are not validated against independent biological evidence, the downstream drug nominations may be built on unreliable foundations. The current validation only shows that the model can identify known genes, not that it can identify genuinely novel ones.
- **Resolution test** Provide independent validation of novel predictions, such as: (1) enrichment of novel predictions in independent GWAS datasets not used in training, (2) evidence from single-cell perturbation experiments, (3) replication in an independent single-cell cohort, or (4) at minimum, a detailed analysis of the functional coherence of novel predictions. Also report precision-recall curves with clear baseline comparisons and discuss the expected AUPRC under random guessing.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical significance of drug proximity
- **Claim pointer** The authors claim to identify 220 drug molecules that are "significantly proximal" to predicted risk genes in cell-type-specific networks.
- **Evidence pointer** Section "Network-based drug repurposing", Figure 5, Table S8
- **Concern** The statistical framework for determining significant drug proximity is not fully described. The authors mention permutation-based tests with Z score ≤ -3, but the details of the permutation procedure are unclear. Specifically: (1) What is being permuted (drug targets, risk genes, network edges)? (2) How is the null distribution constructed? (3) How is multiple testing correction applied across 802 drugs and 23 cell types? (4) What is the false discovery rate? The choice of Z score ≤ -3 corresponds to a very stringent threshold, but without knowing the null distribution, it is impossible to assess whether this is appropriate or overly conservative.
- **Why it matters** The identification of 220 drug candidates is a central claim of the manuscript. If the statistical framework is not transparent or is flawed, the drug list cannot be interpreted. The lack of multiple testing correction details is particularly concerning given the large number of comparisons.
- **Resolution test** Provide a complete description of the permutation procedure, including the exact algorithm, number of permutations, and how the null distribution is calibrated. Report the number of significant drugs at different thresholds and provide FDR estimates. Consider using established methods for network proximity significance testing (e.g., from the network medicine literature) and compare results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Drug-cell eQTL methodology
- **Claim pointer** The authors report 335 drug-cell eQTLs and claim these reveal "genetic variation's influence on drug target expression at the cell-type level."
- **Evidence pointer** Section "Drug-cell eQTLs", Figure 6, Table S10
- **Concern** The drug-cell eQTL analysis has several methodological issues. First, the composite expression value is calculated as the mean of log-normalized expression of drug targets within each cell type, which may obscure target-specific effects. Second, the analysis uses a very small sample size (n=125), which raises concerns about statistical power. Third, the authors state that "each DrugCell comprises multiple genes" and that the analysis was performed "by placing each DrugCell in each of the 22 autosomal human chromosomes" - this is confusing and needs clarification. Fourth, the Bonferroni correction is applied at the level of each phenotype (drug-cell combination), but it is unclear how many phenotypes were tested and whether this adequately controls the family-wise error rate across all tests. Finally, the authors do not report effect sizes or directions for the significant eQTLs, making it difficult to assess biological relevance.
- **Why it matters** The drug-cell eQTL analysis is presented as a novel contribution with implications for precision medicine. If the methodology is not sound, these claims are not supported. The small sample size and potential for false positives are particularly concerning.
- **Resolution test** Clarify the analysis pipeline, including how drug targets are aggregated, how the composite phenotype is constructed, and how many independent tests are performed. Report effect sizes, directions, and standard errors for significant eQTLs. Consider using a more conservative multiple testing correction that accounts for the number of drug-cell combinations tested. If sample size is limiting, acknowledge this as a limitation and discuss power considerations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** External validation of drug predictions
- **Claim pointer** The authors claim their framework identifies drugs with potential for repurposing in psychiatric disorders, including 37 drugs with evidence of reversing disease-associated transcriptional phenotypes.
- **Evidence pointer** Section "Network-based drug repurposing", Figure 5C, Table S9
- **Concern** The manuscript lacks external validation of the drug predictions. The authors use LINCS data to identify reversers and mimickers, but this is an in silico validation that relies on cell lines (which may not recapitulate the relevant cell types). There is no validation using: (1) independent patient-derived data, (2) animal models, (3) electronic health records, or (4) clinical trial data. The authors mention that their approach was "cross-validated using EHR data" in a previous study, but this does not validate the current predictions.
- **Why it matters** Drug repurposing predictions are only useful if they can be validated in real-world settings. The lack of external validation limits the translational significance of the findings. The authors acknowledge this in the discussion but do not provide any interim validation.
- **Resolution test** Provide at least one form of external validation, such as: (1) comparison with known drug-disease associations from clinical databases, (2) validation in an independent patient cohort with treatment response data, or (3) evidence from animal models. If external validation is not possible, clearly state this as a limitation and discuss what additional evidence would be needed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and resource availability
- **Claim pointer** The authors state that "all original code has been deposited" and that data are publicly available.
- **Evidence pointer** Section "Data and code availability"
- **Concern** While the authors provide links to code and data repositories, the manuscript does not include sufficient detail for independent replication of the analyses. Key parameters, thresholds, and decision points in the pipeline are not fully specified. For example, the exact procedure for constructing co-regulatory networks from GRNs, the hyperparameters for the GNN, and the criteria for selecting drug targets are not described in sufficient detail. The web application is mentioned but its functionality and underlying data are not described.
- **Why it matters** Reproducibility is a core requirement for computational biology research. Without complete methodological detail, other groups cannot verify or build upon these findings. The field would benefit from a more detailed methods section or a step-by-step protocol.
- **Resolution test** Provide a complete computational pipeline description, including all parameters and thresholds. Consider depositing the full analysis pipeline in a version-controlled repository with clear documentation. Describe the web application's features and data sources in more detail.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure descriptions
- **Affected element** Figure 2C and Figure 4E
- **Evidence pointer** Figure legends
- **Issue** The figure legends state that "TF names are hidden for ease in visualization" and "cell types... are hidden for ease in visualization." This makes it impossible for readers to interpret the figures without accessing supplementary materials.
- **Required correction** Provide the full versions of these figures in the main text or ensure that the supplementary figures are clearly referenced and accessible. Consider using labels for the most important TFs or cell types.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "Drug-cell eQTL" terminology
- **Evidence pointer** Section "Drug-cell eQTLs"
- **Issue** The term "drug-cell eQTL" is used throughout, but the analysis appears to test associations between genetic variants and composite expression of drug target genes, not drug response itself. This terminology could be misleading.
- **Required correction** Consider using a more precise term such as "drug-target eQTL" or "drug-target gene expression QTL" to accurately reflect what is being measured.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** GNN performance metrics
- **Evidence pointer** Figure 4B, Section "Graph neural networks predict novel cell-type-disorder genes"
- **Issue** The authors report AUPRC values but do not provide confidence intervals or variability across cross-validation folds. The comparison between model 1 and model 2 performance is described qualitatively.
- **Required correction** Report mean and standard deviation of AUPRC across folds, and provide statistical tests for the comparison between models.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Section "Discussion"
- **Issue** The discussion does not adequately address the limitations of using LINCS cell line data for validating drug effects in brain cell types, nor the potential confounding effects of medication in the patient samples used for GRN construction.
- **Required correction** Add a more comprehensive limitations paragraph that addresses these and other potential sources of bias.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference to previous work
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The authors reference their previous work on EHR-based validation but do not provide sufficient context for readers unfamiliar with this work.
- **Required correction** Briefly describe the previous validation approach and how it relates to the current study.

## Risk / unsupported claims

1. The claim that 37 drugs "reverse" psychiatric disorder-associated transcriptional phenotypes is based on in silico analysis of LINCS cell line data and may not translate to human brain cell types. This is acknowledged as a limitation but the claim is stated strongly in the abstract.

2. The claim of identifying "novel" risk genes (249 genes) is not fully supported without demonstrating that these genes are absent from all relevant databases and without independent validation.

3. The drug-cell eQTL analysis with n=125 samples is likely underpowered for detecting robust associations, and the biological interpretation of composite drug-target expression phenotypes requires further justification.

4. The claim that GRNs are "insensitive to sampling bias" based on cross-cohort concordance is only partially supported by the described analysis.

5. The translational potential of the framework for "advancing treatment options" is speculative and not directly supported by the data presented.