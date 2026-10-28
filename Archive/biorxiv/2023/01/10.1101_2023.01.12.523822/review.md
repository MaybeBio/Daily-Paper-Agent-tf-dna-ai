## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplemental materials description
- **Assessment boundary** Scientific content, methodological validity, claims versus evidence, and technical soundness of the computational approach
- **Shared manuscript claim summary** The authors present Z-DNABERT, a fine-tuned DNABERT transformer model, to predict Z-flipons genome-wide. They report enrichment of Z-flipons in promoters and telomeres, overlap with quantitative trait loci, and associations with mendelian disease variants. They propose novel Z-RNA stem-loop motifs in SCARF2, SMAD1, CACNA1C, and ZNF587B that may mediate regulatory functions.
- **Visible evidence base** Abstract, full introduction, results sections, discussion, methods, supplemental materials description, figure legends referenced in text
- **Missing materials affecting confidence** Actual figures and figure panels, supplemental tables and data files, exact model hyperparameters beyond those stated, validation metrics for cross-species predictions, code repository contents

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable computational resource for Z-flipon prediction and generates numerous testable hypotheses linking Z-DNA and Z-RNA to human phenotypes. The core model development appears technically sound, and the genome-wide predictions represent a significant expansion over previous approaches. However, the manuscript attempts to cover an extremely broad range of biological claims, many of which are supported by indirect evidence or speculative interpretations. The causal link between Z-flipon variants and disease phenotypes is not firmly established from the presented analyses. The distinction between Z-DNA and Z-RNA effects is often inferred rather than directly demonstrated. The manuscript would benefit from a more focused presentation of the strongest findings and a clearer separation of established results from hypotheses.

- **Who would be interested in the results, and why** Researchers studying non-B DNA structures, Z-DNA and Z-RNA biology, ADAR1 and innate immunity, gene regulation, and computational genomics. The Z-DNABERT tool itself will be of practical use to the community. Those interested in the mechanistic basis of disease-associated variants in regulatory regions may also find the overlap analyses valuable.

- **Major strengths** The use of nucleotide-resolution experimental data for training is a clear improvement over lower-resolution approaches. The transformer architecture with attention maps provides interpretability that previous black-box models lacked. The cross-species generalization is a useful validation. The integration of multiple orthogonal datasets (GWAS, QTL, OMIM, gnomAD) is ambitious and comprehensive. The identification of specific candidate loci with detailed mechanistic hypotheses provides a roadmap for experimental validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that Z-flipons are enriched in promoters and telomeres and overlap QTLs and disease-associated variants, implying functional relevance.
- **Evidence pointer** Results sections "Whole-genome prediction of Z-flipons" and "Z-flipons are enriched in CTCF-bound proximal enhancer and promoter regions"; Figure 1C, 1D, 2A
- **Concern** The enrichment analyses appear to be descriptive overlaps without clear statistical frameworks. The authors report percentages of overlap but do not describe background models, permutation tests, or other controls that would establish whether these overlaps are significant beyond chance expectation. Given that Z-flipons cover a substantial fraction of the genome, the reported overlaps may reflect genomic distribution rather than functional enrichment.
- **Why it matters** The central claim of the manuscript is that Z-flipons are functionally relevant to gene regulation and disease. Without appropriate statistical controls, the observed overlaps cannot be distinguished from null expectations, undermining the foundation of the subsequent mechanistic interpretations.
- **Resolution test** Provide enrichment statistics with appropriate background models, such as matched random genomic regions with similar GC content, repeat density, and genic distribution. Report odds ratios or fold-enrichments with confidence intervals and multiple-testing corrections.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors state that specific SNPs disrupt Z-DNA or Z-RNA formation and that this disruption is associated with phenotypic effects, implying a causal relationship.
- **Evidence pointer** Results sections on SCARF2, SMAD1, and CACNA1C; Figures 3 and 4
- **Concern** The analyses demonstrate correlation between SNP alleles and predicted Z-flipon stability, and between those same alleles and QTL associations. However, the causal chain from Z-flipon disruption to phenotypic outcome is not established. Alternative mechanisms, such as the SNP directly affecting transcription factor binding, chromatin state, or RNA structure independent of Z-conformation, are not excluded. The authors acknowledge this for SCARF2 but do not resolve it.
- **Why it matters** The manuscript proposes a specific mechanistic model where Z-flipon disruption is the causal link between genetic variation and phenotype. If this causal relationship is not established, the biological conclusions are substantially weakened.
- **Resolution test** Provide experimental validation in at least one locus, such as reporter assays, electrophoretic mobility shift assays, or in vitro Z-conformation assays comparing reference and variant alleles. Alternatively, use statistical approaches such as Mendelian randomization or colocalization analyses to strengthen causal inference.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The authors claim Z-DNABERT significantly outperforms previous approaches with recall of 0.89, precision of 0.78, and ROC AUC of 0.99.
- **Evidence pointer** Results section "Developing generalizable deep learning model for Z-DNA prediction"; Supplemental Table 1
- **Concern** The performance metrics are reported for the test set, but the manuscript does not describe the validation strategy in sufficient detail. The authors mention five-fold stratified training, but it is unclear whether the reported metrics are averaged across folds, whether the test set is fully held out, and whether hyperparameter tuning was performed on the test set. The comparison to DeepZ and CatBoost may not be fair if those models were not tuned with the same rigor. Additionally, the precision drop from test set to whole-genome predictions is substantial and requires more discussion.
- **Why it matters** The reliability of all downstream analyses depends on the model's predictive accuracy. If the performance metrics are inflated or not generalizable, the genome-wide predictions and all derived conclusions are compromised.
- **Resolution test** Clearly describe the train-validation-test split, report metrics with confidence intervals, and provide precision-recall curves. Compare against baseline models with equivalent hyperparameter tuning. Discuss the precision drop in whole-genome predictions and its implications for downstream analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Z-DNA versus Z-RNA discrimination
- **Claim pointer** The authors state that many effects are mediated through Z-RNA formation and describe Z-RNA motifs in specific transcripts.
- **Evidence pointer** Results sections on SCARF2, SMAD1, CACNA1C, and ZNF587B; Figures 3, 4, 5, 6
- **Concern** The model is trained on Z-DNA data, yet the authors make extensive claims about Z-RNA formation. The relationship between Z-DNA prediction and Z-RNA formation is not systematically established. The authors acknowledge this limitation in the discussion but still present Z-RNA-specific mechanistic models as findings. The RNA folding analyses appear to be separate from the Z-DNA predictions, and the integration between these two approaches is not clearly described.
- **Why it matters** The manuscript's novelty partly rests on identifying Z-RNA-mediated regulatory mechanisms. If the Z-RNA predictions are not validated or systematically derived, these claims are speculative.
- **Resolution test** Provide a clear framework for how Z-DNA predictions relate to Z-RNA formation. Validate Z-RNA predictions with experimental data where available, or clearly label these as hypotheses requiring experimental testing.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability of attention maps
- **Claim pointer** The authors claim attention maps are easily interpretable and reveal sequence features important for Z-DNA formation.
- **Evidence pointer** Results section "Developing generalizable deep learning model for Z-DNA prediction"; Figure 1B, Supplemental Figure 1
- **Concern** The interpretation of attention maps as indicating sequence features important for Z-DNA formation requires more rigorous analysis. Attention weights in transformer models do not necessarily correspond to feature importance in a straightforward manner. The authors provide qualitative observations about k-mer rankings but do not provide quantitative validation that attention patterns correlate with experimentally determined Z-DNA propensity.
- **Why it matters** The interpretability claim is presented as an advantage of the approach, but if the attention analysis is not rigorously validated, this advantage is not demonstrated.
- **Resolution test** Provide quantitative analysis linking attention weights to experimentally validated Z-DNA forming sequences, such as correlation analyses or ablation studies.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "Z-flipons are enriched in promoters and telomeres" without providing quantitative context. The percentage of the genome covered by Z-flipons is not stated, making it difficult to assess the significance of this enrichment.
- **Required correction** Include the genomic coverage of Z-flipons and the fold-enrichment values in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** GO enrichment analysis
- **Evidence pointer** Results section "Overlap of Quantitative Trait Loci with Z-flipons"
- **Issue** The GO enrichment analysis reports FDR values but does not describe the background set used, the method for multiple testing correction, or the number of terms tested.
- **Required correction** Describe the GO enrichment methodology, including background set, statistical test, and multiple testing correction approach.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Model training
- **Evidence pointer** Methods section "Deep learning transformer-based model training"
- **Issue** The manuscript states "max_learnirng_rate" which appears to be a typo for "max_learning_rate". Additionally, the batch size and sequence length are stated, but the total number of training examples and the class balance are not described.
- **Required correction** Fix the typo and provide details on training set size, class balance, and any data augmentation strategies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code availability
- **Evidence pointer** Methods section "Code availability"
- **Issue** The code repository is mentioned, but it is unclear whether the trained model weights are included, whether the code is documented, and whether the exact version used for this manuscript is tagged.
- **Required correction** Provide details on the repository contents, including model weights, documentation, and version information.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** ZNF587B analysis
- **Evidence pointer** Results section "Z-flipons, Edited and Noncoding Transcripts"
- **Issue** The claim that Z-RNA formation by the HR modulates alternative splicing is speculative. The authors present the HR as containing a splicing enhancer motif, but do not demonstrate that Z-RNA formation affects splicing enhancer function.
- **Required correction** Soften the language to indicate this is a hypothesis, or provide additional evidence linking Z-RNA formation to splicing outcomes.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the approach, such as the cell-type specificity of the training data, the inability to detect short Z-RNA motifs, or the potential for false positives in whole-genome predictions.
- **Required correction** Add a limitations paragraph addressing these issues.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results and Discussion
- **Evidence pointer** Results section "Z-flipons, Edited and Noncoding Transcripts" and Discussion
- **Issue** The manuscript states that Z-DNABERT does not detect Z-RNA forming ALU sequences, yet the model is used to make claims about Z-RNA elsewhere. This inconsistency should be addressed.
- **Required correction** Clarify the relationship between Z-DNA prediction and Z-RNA detection, and explain how the model can inform Z-RNA biology despite this limitation.

## Risk / unsupported claims
- The claim that Z-flipon variants are causal for mendelian disease in 8.6% and 2.9% of OMIM genes is presented as a quantitative finding, but the statistical significance of these overlaps is not established.
- The claim that specific haplotypes are associated with increased or decreased gene expression through Z-flipon mechanisms is not supported by direct experimental evidence.
- The claim that Z-RNA formation in ZNF587B enables adaptive anti-viral intracellular defense is highly speculative and not supported by functional data.
- The claim that the HR sequence in ZNF proteins resembles a recombination recognition sequence cleaved by RAG1 is presented without direct evidence of RAG1-mediated cleavage at these loci.
- The claim that attention maps provide interpretable insights into Z-DNA formation is not quantitatively validated.
- The cross-species generalization results are mentioned but not shown in the main text, making this claim difficult to evaluate.
- The statement that Z-flipons can act by altering loop topology of chromatin domains is presented as a mechanism without direct experimental support.