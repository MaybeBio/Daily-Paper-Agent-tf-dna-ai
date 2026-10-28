## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary figure legends referenced but not provided)
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that sequence-specific transcription factor (ssTF) binding induces characteristic UV-induced cyclobutane pyrimidine dimer (CPD) patterns ("fingerprints") that can be learned by machine learning algorithms to map transcription factor binding sites (TFBS) genome-wide. They demonstrate this in yeast for Hap2/3/5 and Gcr1, and extend to human NF-Y using CPD-capture-seq data.
- **Visible evidence base** Main text figures referenced (Figs 1-7), supplementary figures referenced (S1-S13), supplementary tables referenced (S1), methods descriptions, statistical results reported in text
- **Missing materials affecting confidence** Supplementary figures and tables not provided; detailed model hyperparameters not fully specified; precise performance metrics for some analyses not reported; raw data not accessible for independent verification

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach that leverages UV damage patterns as a readout of transcription factor occupancy. The core idea is novel and potentially valuable, as it offers an orthogonal alternative to ChIP-based methods. The yeast Hap2/3/5 analysis is reasonably well supported, with multiple lines of evidence including a genetic control (hap5Δ). However, several technical concerns need to be addressed, particularly regarding the generalizability of the approach, the robustness of the machine learning methodology, and the strength of the human NF-Y extension. The claim that this method can "simultaneously elucidate the genome-wide binding profiles of many (or all) ssTFs" is speculative and not directly demonstrated.

- **Who would be interested in the results, and why** Researchers in transcriptional regulation, chromatin biology, and DNA repair would find this work of interest. The method offers a potential alternative to ChIP-based approaches for mapping TFBS, which could be particularly valuable in contexts where ChIP-grade antibodies are unavailable or where crosslinking artifacts are a concern. The demonstration that UV damage patterns are TF-specific and learnable could also interest computational biologists working on regulatory genomics.

- **Major strengths** 
  1. The core concept is novel and creative, repurposing UV damage data for TFBS mapping
  2. The yeast Hap2/3/5 analysis includes a strong genetic control (hap5Δ) that directly supports the causal link between TF binding and the observed CPD fingerprint
  3. The authors provide functional validation through gene expression analysis, showing that newly identified targets are downregulated in TF mutants
  4. The comparison with ChIP-based methods and the identification of potential ChIP artifacts in highly transcribed genes is a valuable contribution
  5. The extension to a second TF (Gcr1) with a different machine learning approach (NN) suggests some generalizability

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of machine learning methodology
- **Claim pointer** The authors claim that the Random Forest and neural network classifiers can accurately identify TFBS based on CPD fingerprints, with reported cross-validation performance (e.g., >90% sensitivity, ~99.99% specificity for Hap2/3/5).
- **Evidence pointer** Results sections "Mapping Hap2/3/5 binding sites based on their CPD fingerprint using the Random Forest algorithm" and "Mapping binding sites of other yeast ssTFs by CPD fingerprinting"; Supplementary Fig. S9
- **Concern** The machine learning methodology has several potential issues. First, the training set for Hap2/3/5 consists of only 35 positive examples, and for Gcr1 only 6. With such small training sets, the reported cross-validation performance (AUC of 0.977 and 1.0, respectively) is likely optimistic and may not generalize. Second, the negative examples are all drawn from intragenic CCAAT motifs, which may not be representative of all unbound motifs (e.g., intergenic unbound motifs may have different chromatin contexts). Third, the feature selection (positions -1.5, +0.5, +2.5, +3.5, +4.5 for Hap2/3/5) appears to be based on the observed fingerprint in known binding sites, which could introduce circularity when evaluating performance on those same sites. Fourth, the authors do not report how the classification threshold was chosen, nor do they provide precision-recall curves, which would be more informative than ROC curves given the extreme class imbalance (33,720 potential sites, only ~75 predicted bound).
- **Why it matters** The central claim of the paper is that machine learning can reliably identify TFBS from CPD data. If the methodology has inherent biases or the performance metrics are inflated due to small training sets or circular feature selection, the conclusions may not hold when applied to new data or new TFs.
- **Resolution test** The authors should provide: (1) external validation using held-out ChIP-exo data not used in training; (2) precision-recall curves and calibration analysis; (3) analysis of how performance varies with training set size (learning curves); (4) validation using negative examples from intergenic regions; (5) demonstration that the selected features are not simply the most discriminative positions in the training set but generalize to independent data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality for the human NF-Y extension
- **Claim pointer** The authors claim that "similar analysis of the other 25 newly discovered Hap2/3/5 binding sites" and that the RF model developed for yeast Hap2/3/5 can be used to identify NF-Y binding sites in human CPD-capture-seq data, identifying 337 predicted NF-Y binding sites.
- **Evidence pointer** Results section "Using CPD-capture-seq to map NF-Y binding sites in human promoter regions"; Fig. 7
- **Concern** The human NF-Y analysis is substantially weaker than the yeast analysis. The authors apply a model trained on yeast Hap2/3/5 data to human NF-Y binding sites, but the transferability of the CPD fingerprint across species is not well established. The authors do not provide a genetic control for human cells (e.g., NF-Y knockdown), nor do they validate the newly identified NF-Y binding sites through an independent method. The comparison with ENCODE ChIP-seq data shows only 134 of 337 predicted sites (40%) are within 50 bp of a known NF-Y binding site, leaving 203 predictions unvalidated. The authors do not report whether the 203 unvalidated sites show any evidence of NF-Y binding (e.g., motif conservation, chromatin features, or expression correlation). The claim that the method identifies "new sites" in human cells is therefore not well supported.
- **Why it matters** The human extension is important for demonstrating the generalizability of the approach beyond yeast. If the human results are not rigorously validated, the broader applicability of the method remains uncertain.
- **Resolution test** The authors should: (1) validate a subset of newly identified human NF-Y binding sites using an independent method (e.g., ChIP-qPCR, electrophoretic mobility shift assay, or reporter assays); (2) provide a genetic control (e.g., NF-Y knockdown followed by CPD-seq) to confirm that the fingerprint is dependent on NF-Y binding; (3) analyze the genomic features of the 203 unvalidated sites to assess their plausibility as NF-Y targets; (4) discuss the potential reasons for the 60% discordance with ENCODE ChIP-seq data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the approach to other TFs
- **Claim pointer** The authors state that "different classes of ssTFs induce distinct patterns of UV damage at their DNA binding sites and most have sufficient numbers of lesion-forming dipyrimidine sequences to learn ssTF-specific CPD fingerprints" and suggest that "a single UV damage mapping experiment could simultaneously elucidate the genome-wide binding profiles of many (or all) ssTFs."
- **Evidence pointer** Results section "Mapping binding sites of other yeast ssTFs by CPD fingerprinting"; Fig. 5; Discussion
- **Concern** The UMAP analysis of 78 TFs shows diversity in CPD patterns, but the authors only demonstrate successful TFBS mapping for two TFs (Hap2/3/5 and Gcr1). The claim that the approach is generalizable to "many (or all) ssTFs" is speculative. Some TFs may bind to motifs lacking dipyrimidines at informative positions, or their binding may not induce sufficient conformational changes to create a detectable CPD fingerprint. The authors do not provide a systematic analysis of which TFs are amenable to this approach based on their motif composition or binding mode.
- **Why it matters** The broad applicability of the method is a key selling point. If the approach only works for a subset of TFs, the practical utility is more limited than claimed.
- **Resolution test** The authors should: (1) systematically analyze the dipyrimidine content of binding motifs for all 78 TFs; (2) test the approach on additional TFs with different DNA-binding domains and motif compositions; (3) provide a framework for predicting which TFs are likely to be amenable to CPD fingerprinting.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of reported results
- **Claim pointer** The authors report various quantitative results, including ">90% of the positive examples" correctly predicted, "~99.99% specificity," "P < 1 × 10−14" for functional enrichment, and "P = 9.6 × 10−9" for expression analysis.
- **Evidence pointer** Throughout Results; specific locations not provided
- **Concern** Several quantitative results are reported without sufficient methodological detail. The authors do not specify: (1) the exact number of true positives, false positives, true negatives, and false negatives for the Hap2/3/5 and Gcr1 predictions; (2) how the 50 bp distance threshold for matching ChIP-exo peaks was chosen; (3) the statistical test used for functional enrichment and whether multiple testing correction was applied; (4) the exact criteria for calling a gene "down-regulated" in the expression analysis; (5) the number of genes in each category for the Venn-like analyses in Fig. 4F. Without these details, the robustness of the reported statistics cannot be assessed.
- **Why it matters** The paper makes quantitative claims about the performance of the method and the biological significance of the findings. Without adequate methodological detail, these claims cannot be independently evaluated or reproduced.
- **Resolution test** The authors should provide: (1) a confusion matrix for each classifier; (2) justification for the 50 bp threshold; (3) details of statistical tests used, including multiple testing corrections; (4) explicit criteria for defining differentially expressed genes; (5) the number of genes in each category for all overlap analyses.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Machine learning feature description
- **Evidence pointer** Methods section "Random forest analysis of CPD-seq data"
- **Issue** The authors state that CPD induction values and log2 ratios were determined at positions -1.5, +0.5, +2.5, +3.5, and +4.5 for Hap2/3/5, and -1.5, -0.5, +0.5, +1.5 for Gcr1. It is unclear why different positions were used for the two TFs and how these positions were selected.
- **Required correction** The authors should explain the rationale for selecting these specific positions and whether the positions were chosen a priori or based on the observed fingerprint in the training data.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of results
- **Affected element** Supplementary figure references
- **Evidence pointer** Throughout Results; Supplementary Figs S1-S13
- **Issue** The manuscript references 13 supplementary figures and 1 supplementary table, but these are not provided in the submitted text. Several key analyses appear to be relegated to supplementary material (e.g., the UMAP analysis of 78 TFs, the comparison of machine learning algorithms, the analysis of ChIP-exo only peaks in highly transcribed genes).
- **Required correction** The authors should ensure that all supplementary materials are available for review, or move key analyses into the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Discussion of ChIP artifacts
- **Evidence pointer** Results section "Hap2/Hap3/Hap5 binding peaks identified by ChIP-exo only are enriched in the coding regions of highly transcribed genes"; Supplementary Fig. S6
- **Issue** The authors suggest that ChIP-exo peaks in coding regions of highly transcribed genes may be artifacts, but they do not provide a direct test of this hypothesis. The alternative explanation that these represent genuine but non-functional binding events is not discussed.
- **Required correction** The authors should acknowledge alternative interpretations and, if possible, provide additional evidence supporting the artifact hypothesis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 4F and related text
- **Evidence pointer** Results section "Function and regulation of new Hap2/3/5 target genes"; Fig. 4F
- **Issue** The overlap analysis between CPD-identified targets and ChIP-identified targets is presented as a Venn diagram, but the text does not clearly explain the significance of the non-overlapping sets. The statement "None of the remaining 25 down-regulated genes were identified as bound by ChIP-exo only" is presented without discussion of what this implies.
- **Required correction** The authors should provide a more detailed interpretation of the overlap and non-overlap between methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Data availability section
- **Issue** The authors state that custom Perl scripts were used for analysis, and code is available through Zenodo. However, the specific version of the code, dependencies, and usage instructions are not described.
- **Required correction** The authors should provide a brief description of the code structure and requirements to facilitate reuse.

## Risk / unsupported claims
- The claim that "a single UV damage mapping experiment could simultaneously elucidate the genome-wide binding profiles of many (or all) ssTFs" is speculative and not directly demonstrated by the data presented.
- The claim that the RF model trained on yeast Hap2/3/5 can be directly applied to human NF-Y binding sites is not well supported, as the cross-species transferability of CPD fingerprints is not established.
- The identification of 203 human NF-Y binding sites not confirmed by ChIP-seq is presented as a finding, but these sites are not validated by any independent method.
- The suggestion that ChIP-exo peaks in coding regions of highly transcribed genes are artifacts is presented as a conclusion, but the evidence is indirect.
- The reported performance metrics (AUC values, sensitivity, specificity) for the machine learning classifiers may be optimistic given the small training sets and potential circularity in feature selection, and should be interpreted with caution.
- The functional significance of newly identified TFBS is inferred from gene expression data, but the causal link between binding at these specific sites and gene expression changes is not directly tested.