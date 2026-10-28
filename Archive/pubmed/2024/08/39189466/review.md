## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the provided text. No external validation or replication was performed.
- **Shared manuscript claim summary** The authors present a systematic pipeline combining computational prediction (PLM-DBPPred) and experimental screening (B1H, SELEX, BLI) to discover novel DNA-binding tandem repeat proteins (TRPs). They report 11 novel DNA-binding TRPs, six with sequence specificity, and characterize four families (STAR, MOON, pTERF, NORD, MIRAGE) with structural, biochemical, and functional evidence.
- **Visible evidence base** Computational analyses of public databases (UniRef100, NCBI-nr), protein language model predictions, B1H and SELEX screening, BLI binding assays, EMSA, GFP activation/repression assays, CUT&Tag in human cells, AlphaFold2 structure predictions, phylogenetic analyses, negative-stain EM.
- **Missing materials affecting confidence** Figures and supplementary tables referenced but not provided. Raw data (SELEX, B1H, CUT&Tag, RNA-seq) deposited but not accessible in this review. Detailed model architecture and hyperparameters for PLM-DBPPred not fully described. No information on replicate numbers for several key experiments. No negative control data for some screening steps.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious effort to systematically discover novel DNA-binding tandem repeat proteins. The combination of deep learning-based prediction with multiple orthogonal experimental validation approaches is commendable and has yielded several potentially novel protein families. The STAR protein family, in particular, shows promise as a programmable DNA-binding tool with advantages over canonical TALEs. However, several technical concerns must be addressed to fully establish the claims, particularly regarding the specificity of the screening methods, the statistical robustness of the binding data, and the functional significance of the identified proteins in their native contexts.
- **Who would be interested in the results, and why** Researchers in genome engineering and synthetic biology will be interested in the STAR proteins as potential new scaffolds for programmable DNA binding. Evolutionary and structural biologists studying repeat proteins will value the identification of novel families (MOON, pTERF) and the phylogenetic analyses. Computational biologists working on protein function prediction will be interested in the PLM-DBPPred approach. Additionally, researchers studying host-pathogen interactions and marine biology may find relevance in the STAR and MOON families.
- **Major strengths**
  1. The study addresses a significant gap: the vast majority of TRPs are uncharacterized, and the systematic approach is novel.
  2. The integration of multiple computational and experimental methods provides a robust pipeline for discovery.
  3. The identification and characterization of STAR proteins with high affinity, short recognition sites, and lack of T0 dependence represents a potentially important advance for DNA-binding tool development.
  4. The discovery of pTERF as a prokaryotic mTERF-like protein has evolutionary implications.
  5. The authors are transparent about limitations, including the poor performance of a TRP-specific model and the challenges of predicting disordered proteins.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We established a protein language model for DNA-binding protein prediction (PLM-DBPPred), and predicted a large number of DNA-binding TRPs."
- **Evidence pointer** Methods: "DBP prediction model construction"; Results: "Prediction of DNA-binding TRPs" (location not provided)
- **Concern** The description of PLM-DBPPred is insufficient to evaluate its validity. The authors state it integrates three pre-trained models (ProteinBERT, ProtT5, ESM) by averaging probabilities, but critical details are missing: (1) the exact architecture of the classification layers for each model, (2) the training procedure (e.g., learning rates, epochs, batch sizes for each model), (3) how the final ensemble was calibrated, and (4) the threshold for calling a protein a "DNA-binding TRP." More importantly, the evaluation on the PDB600 test set is described only by an AUC of 0.90. While AUC is useful, it does not convey precision, recall, or F1 at the operating threshold used for screening. The authors should report a confusion matrix and precision-recall curve, as the class imbalance in real-world prediction (vastly more non-DBPs than DBPs) makes AUC potentially misleading.
- **Why it matters** The entire discovery pipeline depends on the reliability of PLM-DBPPred. If the model has poor precision at the chosen threshold, many false positives will be carried into the experimental screening, wasting resources and potentially biasing the discovery toward artifacts. Conversely, if recall is low, true positives may be missed. Without a clear understanding of the model's operating characteristics, the validity of the 8,865 predicted DNA-binding TRPs cannot be assessed.
- **Resolution test** Provide a detailed description of the model architecture, training, and hyperparameters. Report precision, recall, F1, and a precision-recall curve for PLM-DBPPred on the PDB600 test set. Additionally, provide a calibration plot showing the relationship between predicted probability and actual frequency of DNA binding. If possible, validate the model on an independent, non-redundant test set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We first selected 51 clusters with DBP function enrichment. We next selected 15 clusters with DRD/DBGO functional enrichment. In addition, considering that all of these functional annotations relied on existing knowledge, we further selected nine clusters without any functional annotation and based solely on basic protein features such as small size."
- **Evidence pointer** Results: "Selecting TRP candidates for experimental screening" (location not provided)
- **Concern** The criteria for selecting the 75 clusters (and 100 genes) for experimental screening are not fully transparent. The authors mention three categories (DBP-enriched, DRD/DBGO-enriched, and unannotated), but the specific thresholds for "enrichment" (e.g., the LR score cutoff) and the "basic protein features" for the unannotated clusters are not defined. More critically, the number of clusters in each category (51, 15, 9) sums to 75, but it is unclear whether these are disjoint sets. The selection process appears to be a critical funnel in the pipeline, and any bias here will propagate to the final results. The authors should provide a flow diagram showing the number of clusters/TRPs at each stage of filtering, with explicit criteria for each step.
- **Why it matters** The selection process determines which candidates are experimentally tested. If the criteria are arbitrary or not reproducible, the entire study cannot be replicated. Moreover, the balance between known-function and unknown-function clusters affects the novelty of the discoveries. A clear, quantitative selection protocol is essential for the scientific community to assess and build upon this work.
- **Resolution test** Provide a detailed flow diagram (e.g., in a supplementary figure) showing the number of TRPs, clusters, and candidates at each filtering step, with the exact thresholds used. Clarify whether the three selection categories are mutually exclusive. If possible, perform a sensitivity analysis showing how varying the selection thresholds would affect the final list of candidates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "In total, we identified 11 proteins with DNA-binding activity, six of which displayed sequence specificity of DNA binding under the specific screening conditions."
- **Evidence pointer** Results: "DNA-binding TRPs identified by B1H screening" and "DNA-binding TRPs identified by SELEX" (location not provided)
- **Concern** The criteria for classifying a protein as a "DNA-binding TRP" and for "sequence specificity" are not clearly defined. For B1H, the authors state they identified "specific binding motifs" but do not specify the enrichment threshold (e.g., fold enrichment over background, number of reads, statistical significance). For SELEX, the criteria for "enriched DNA sequence motifs" are similarly vague. The BLI-based screening used a "0.1 nm binding response" cutoff, but it is unclear how this cutoff was determined and whether it is statistically meaningful. The authors should provide explicit, pre-defined criteria for positive hits in each assay, including statistical thresholds and replicate requirements.
- **Why it matters** The central claim of the paper is the identification of novel DNA-binding TRPs. If the criteria for "positive" are too lenient, false positives will be reported. If too stringent, true positives may be missed. The lack of clear criteria makes it impossible to evaluate the robustness of the findings and to compare them with other screening studies.
- **Resolution test** Provide explicit, quantitative criteria for each screening assay (B1H, SELEX, BLI), including thresholds for enrichment, statistical significance, and replicate consistency. Show the distribution of scores for all tested candidates (e.g., a scatter plot of BLI responses) to demonstrate that the chosen cutoff is appropriate. For B1H and SELEX, report the number of independent biological replicates and the consistency of motif enrichment across replicates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Notably, members of the STAR (Short TALE-like Repeat proteins) family can be programmed to target specific 9 bp DNA sequences with high affinity."
- **Evidence pointer** Results: "Characterization of STAR proteins" (location not provided)
- **Concern** The claim that STAR proteins can be "programmed" to target specific sequences is based on the RVD code analogy with TALEs. However, the evidence presented is limited. The authors show that modifying RVDs changes binding specificity, but they do not demonstrate that the RVD code is generalizable across all possible nucleotide sequences. Specifically, they tested only a few RVD variants and a limited set of target sequences. The claim of "programmability" implies a predictable, modular code, which requires a more systematic demonstration. The authors should test a larger panel of RVD-nucleotide combinations and show that the code is consistent and predictable.
- **Why it matters** The potential utility of STAR proteins as a DNA-binding tool depends on the reliability and predictability of the RVD code. If the code is not generalizable, the practical value of STAR proteins is significantly diminished. A more thorough characterization of the RVD code would strengthen the claim and increase the impact of the work.
- **Resolution test** Perform a systematic analysis of RVD-nucleotide specificity using a comprehensive library of RVD variants and target sequences (e.g., using a high-throughput binding assay). Show that the binding specificity of STAR proteins can be predicted from the RVD sequence with high accuracy. If possible, demonstrate that STAR proteins can be programmed to bind a wide range of 9 bp sequences with high specificity and affinity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The identification of pTRF proteins indicates the potential prokaryotic homologs of mTRF proteins."
- **Evidence pointer** Results: "Characterization of pTRF proteins" (location not provided)
- **Concern** The evolutionary claim that pTRF is a prokaryotic homolog of mTRF is based on structural similarity and limited sequence identity (9-18%). This is a weak basis for establishing homology. The authors should perform a more rigorous phylogenetic analysis, including a broader sampling of mTRF and pTRF sequences, and use appropriate statistical tests (e.g., bootstrap support) to assess the robustness of the inferred relationship. Additionally, the functional significance of pTRF in prokaryotes is unclear. The authors should discuss alternative explanations for the observed structural similarity, such as convergent evolution.
- **Why it matters** The claim of a prokaryotic origin for mTRF-like proteins has significant evolutionary implications. If the homology is not well-supported, the conclusion is overstated. A more rigorous analysis would either strengthen the claim or appropriately temper it.
- **Resolution test** Perform a comprehensive phylogenetic analysis of mTRF and pTRF sequences, including a diverse set of taxa and appropriate outgroups. Use multiple methods (e.g., maximum likelihood, Bayesian inference) and assess statistical support. Discuss alternative scenarios, such as horizontal gene transfer or convergent evolution, and provide evidence to distinguish between them.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We then focused our efforts on identifying novel TRPs possessing DNA-binding capabilities."
- **Evidence pointer** Results: "Prediction of DNA-binding TRPs" (location not provided)
- **Concern** The authors state that they focused on TRPs with a period of 15-35 amino acids and 6-40 repeats, based on known nucleic acid binding families. This is a reasonable starting point, but it may exclude novel DNA-binding TRPs with different repeat architectures. The authors should justify this choice more thoroughly and discuss the potential for missing relevant families. Additionally, the NSS > 0.6 cutoff for diversity is arbitrary and should be justified.
- **Why it matters** The scope of the discovery is defined by these filters. If the filters are too restrictive, the study may miss important novel families. A clear justification of the chosen parameters, along with a discussion of their limitations, would help the reader understand the scope and potential biases of the study.
- **Resolution test** Provide a more detailed justification for the chosen period and repeat number ranges, citing specific examples of known DNA-binding TRPs that fall within these ranges. Discuss the potential for DNA-binding TRPs outside these ranges and, if possible, perform a sensitivity analysis to show how the results would change with different parameters.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses specialized terminology (e.g., "TRPs," "PLM-DBPPred") without sufficient context for a general scientific audience. The key finding (11 novel DNA-binding TRPs) is buried in the middle of the abstract.
- **Required correction** Consider restructuring the abstract to more clearly state the problem, the approach, the key findings, and the implications. Define acronyms on first use and provide a brief explanation of why DNA-binding TRPs are important.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods: "BLI-based screening"
- **Evidence pointer** Methods: "Bio-layer interferometry (BLI)-based screening"
- **Issue** The description of the BLI-based screening method is brief. It is unclear how the "response score" is calculated and how the 0.1 nm cutoff was determined. The authors state that the method was "developed based on the findings of Marklund et al.," but the specific adaptation is not described.
- **Required correction** Provide a more detailed description of the BLI-based screening protocol, including how the response score is calculated, how the cutoff was determined, and how many replicates were performed. If the method is adapted from a published protocol, clearly state the modifications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results: "Characterization of STAR proteins"
- **Evidence pointer** Results: "Characterization of STAR proteins" (location not provided)
- **Issue** The binding affinity (Kd) for PqSTAR1 is reported as 3.8 nM, but it is unclear how this was measured. The BLI assay is mentioned, but the details of the kinetic analysis (e.g., fitting model, association/dissociation rates) are not provided.
- **Required correction** Provide details of the BLI kinetic analysis, including the fitting model used, the association and dissociation rate constants, and the number of independent experiments. If the Kd was determined by a different method, describe it fully.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results: "Characterization of MOON proteins"
- **Evidence pointer** Results: "Characterization of MOON proteins" (location not provided)
- **Issue** The comparison between SpMOON1 and human Ki67 is interesting but brief. The authors state that they share a similar architecture (FHA-PP1-repeat) but do not discuss the functional implications of this similarity in detail.
- **Required correction** Expand the discussion of the SpMOON1-Ki67 comparison, including the potential functional significance of the shared architecture and the differences in the repeat regions. This would provide more biological context for the discovery.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods: "Construction of phylogenetic trees"
- **Evidence pointer** Methods: "Construction of phylogenetic trees"
- **Issue** The method for constructing phylogenetic trees is described in a single sentence. It is unclear what alignment method was used, what evolutionary model was assumed, and how statistical support was assessed.
- **Required correction** Provide a more detailed description of the phylogenetic analysis, including the alignment method, the model selection, the tree-building algorithm, and the method for assessing statistical support (e.g., bootstrap).

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the limitations of the study is brief and focuses primarily on computational and screening aspects. The authors do not discuss the potential limitations of the experimental validation methods (e.g., the use of E. coli for functional assays, the lack of in vivo functional data for most candidates).
- **Required correction** Expand the discussion of limitations to include the experimental validation methods and the potential for artifacts. Discuss the extent to which the findings can be generalized to native contexts.

## Risk / unsupported claims
- The claim that PLM-DBPPred achieves "state-of-the-art performance" is not fully supported, as the comparison to existing methods is not described in detail.
- The claim that STAR proteins can be "programmed" to target specific sequences is not fully established, as only a limited number of RVD variants were tested.
- The claim that pTRF is a "prokaryotic homolog" of mTRF is based on weak sequence similarity and requires more rigorous phylogenetic analysis.
- The claim that the identified proteins are "novel" is based on the absence of prior characterization, but the authors do not provide a comprehensive search of the literature to confirm this.
- The functional significance of the identified proteins in their native contexts is not established, as most experiments were performed in vitro or in heterologous systems.
- The statement that "approximately half of the TR clusters are species-specific" is presented without statistical support or a clear definition of "species-specific."