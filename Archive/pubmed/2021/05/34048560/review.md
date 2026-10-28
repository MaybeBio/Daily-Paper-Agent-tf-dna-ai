## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific and technical evaluation of the DeepFun web server and its underlying deep learning model, as described in the provided manuscript
- **Shared manuscript claim summary** The authors present DeepFun, a web server built on a convolutional neural network (CNN) that predicts the functional impact of non-coding genetic variants in a tissue- and cell type-specific manner, using 7,879 chromatin profiles from ENCODE and Roadmap. The server offers two analyses: screen analysis (SAD and log-odds difference scores across all chromatin features) and in silico saturated mutagenesis (scanning substitutions within 200 bp of a query variant). The authors claim independent validation using ClinVar, ASD de novo mutations, and GWAS data, and demonstrate tissue-specific enrichment of variant effects consistent with disease-relevant tissues.
- **Visible evidence base** Full text including methods, figures referenced (Figures 1–4), supplementary tables and figures referenced (Supplementary Tables S1–S2, Supplementary Figures S1–S2), and prior publication (reference 26)
- **Missing materials affecting confidence** Actual web server functionality was not tested; figure content not directly viewable; supplementary data not provided; no quantitative performance metrics (e.g., AUROC/AUPRC values per assay type) beyond median values; no comparison with other tools beyond DeepSEA; no details on hyperparameter tuning or model architecture beyond reference to prior work

## Reviewer
- **Overall assessment** The manuscript describes a useful and potentially valuable web resource for the functional annotation of non-coding variants. The underlying model builds on established CNN architectures (Basset) and expands the training data substantially. The tissue- and cell type-specific predictions are a meaningful addition to the field. However, the manuscript as presented is more of a web server report than a methodological advance. The validation is largely descriptive, and the quantitative evidence for improved performance over existing tools is thin. The claims of tissue-specific utility are supported by correlational observations but lack rigorous statistical benchmarking. The manuscript would benefit from clearer performance metrics, direct comparisons with state-of-the-art tools, and a more critical discussion of limitations.

- **Who would be interested in the results, and why** Geneticists and genomicists working on GWAS follow-up, variant prioritization, and functional interpretation of non-coding variation. Researchers studying tissue-specific gene regulation and epigenomics would also find the resource useful. The web server's user-friendly interface and broad coverage of chromatin features make it accessible to experimental biologists without deep computational expertise.

- **Major strengths**
  1. Comprehensive training data: integration of 7,879 chromatin profiles across 225 tissues/cell types is a substantial resource.
  2. User-friendly web server with two complementary analysis modes (screen and saturated mutagenesis), lowering the barrier for non-specialists.
  3. Independent validation using multiple datasets (ClinVar, ASD, GWAS) adds credibility.
  4. Demonstration of tissue-specific variant effects (e.g., immune traits in intestine/colon, neuropsychiatric traits in brain) is biologically plausible and clinically relevant.
  5. Model and scripts are deposited on GitHub, supporting reproducibility and local use.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "DeepFun achieved a median AUROC value of 0.933 over all DNase-seq assays, compared to 0.895 from the original Basset result"
  - **Evidence pointer** Materials and Methods, "DeepFun model training and functions"; location not provided
  - **Concern** The AUROC comparison with Basset is presented as evidence of improved performance, but the comparison is not controlled. It is unclear whether the same training, validation, and test splits were used, whether the same genomic regions were evaluated, and whether the improvement is statistically significant. Moreover, AUROC is a threshold-free metric that can be misleading for imbalanced datasets; the authors acknowledge this and report AUPRC, but only for DNase-seq and histone marks, not for TF binding profiles.
  - **Why it matters** The core claim of the model's utility rests on its predictive accuracy. Without a rigorous, controlled comparison against existing methods (e.g., DeepSEA, Basenji, ExPecto) using identical evaluation protocols, the added value of DeepFun over prior tools is not established.
  - **Resolution test** Provide a controlled benchmark: train and evaluate DeepFun and at least one existing tool (e.g., DeepSEA) on identical train/test splits, report AUROC and AUPRC for all assay categories, and include confidence intervals or significance tests. Alternatively, provide external validation on an independent functional assay dataset (e.g., MPRA or CRISPR screens) to demonstrate predictive utility.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** "DeepFun can effectively predict the functional impact of variants in a tissue-specific manner, as most of them are consistent with the disease symptoms"
  - **Evidence pointer** Results section, "Prior application and evaluation", Figure 4A; location not provided
  - **Concern** The tissue-specific validation is based on visual inspection of Figure 4A and qualitative statements. No statistical test is provided to show that the enrichment of high SAD scores in disease-relevant tissues is significant relative to a null expectation. The authors do not report effect sizes, confidence intervals, or multiple-testing corrections. The comparison with DeepSEA in Supplementary Figure S1 shows correlations, but these are not adjusted for the imbalance in assay numbers and do not directly validate tissue specificity.
  - **Why it matters** The central novelty of DeepFun is its tissue- and cell type-specific predictions. If this claim is not rigorously supported, the manuscript reduces to a data aggregation exercise without demonstrated added biological insight.
  - **Resolution test** Perform a formal enrichment analysis: for each disease/trait, test whether the SAD scores of associated variants are significantly higher in the predicted relevant tissue(s) compared to (a) other tissues and (b) matched control variants. Report adjusted p-values and effect sizes. Provide a quantitative comparison with DeepSEA's tissue-specific predictions using the same statistical framework.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "DeepFun does not directly predict the impact of genetic variants. For each variant, DeepFun considers its neighboring 1000 bp region for context information"
  - **Evidence pointer** Materials and Methods, "DeepFun model training and functions"; location not provided
  - **Concern** The manuscript does not describe how the model handles variants in repetitive regions, indels, or multi-allelic variants. It is also unclear how the model accounts for strand orientation and whether predictions are calibrated across different chromatin features. The choice of a fixed 1000 bp window may miss long-range regulatory effects, which the authors acknowledge in the conclusion but do not quantify.
  - **Why it matters** Users need to know the limitations of the model's input requirements and whether predictions are reliable across different genomic contexts. Without this information, the tool may be misapplied.
  - **Resolution test** Add a section describing variant preprocessing, including handling of indels, multi-allelic sites, and repetitive regions. Provide calibration plots (predicted vs. observed activity) for a subset of chromatin features. Discuss the impact of window size on prediction accuracy, possibly with a sensitivity analysis.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract; Introduction, first paragraph
  - **Issue** The abstract and introduction assume familiarity with deep learning terminology (e.g., CNN, SAD, log-odds difference) without defining these terms for a broader genetics audience.
  - **Required correction** Briefly define CNN, SAD, and log-odds difference in the abstract or introduction, or provide a glossary for non-specialist readers.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Web server construction"
  - **Evidence pointer** Materials and Methods, "Web server construction"; location not provided
  - **Issue** The description of the web server architecture is brief and lacks details on security, data privacy, and handling of user-uploaded data. Given that users may upload sensitive genetic data, this is a practical concern.
  - **Required correction** Add a paragraph on data handling, including encryption, retention policy, and compliance with relevant regulations (e.g., GDPR, HIPAA).

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Results, "Prior application and evaluation"
  - **Evidence pointer** Results section, "Prior application and evaluation"; location not provided
  - **Issue** The description of the GWAS validation is dense and assumes familiarity with specific disease datasets. A brief explanation of the disease categories and why the chosen tissues are relevant would improve accessibility.
  - **Required correction** Add a sentence or two contextualizing the disease-tissue relationships, or refer readers to Supplementary Table S1 for details.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "DeepFun model training and functions"
  - **Evidence pointer** Materials and Methods, "DeepFun model training and functions"; location not provided
  - **Issue** The manuscript states that the model was trained on "peaks" treated as binary labels, but does not describe how negative regions were selected. This is a critical detail for assessing potential training bias.
  - **Required correction** Describe the negative set construction (e.g., random genomic regions, matched by GC content and mappability) and any filtering steps applied.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Conclusion
  - **Evidence pointer** Conclusion; location not provided
  - **Issue** The conclusion mentions future improvements (e.g., incorporating quantitative signals, long-range interactions) but does not discuss how these would change the tool's utility or performance.
  - **Required correction** Briefly speculate on the expected impact of these improvements, or acknowledge that they are speculative.

## Risk / unsupported claims
- The claim of improved performance over Basset (median AUROC 0.933 vs 0.895) is not supported by a controlled comparison.
- The claim of tissue-specific predictive utility is based on qualitative observations without statistical testing.
- The claim that DeepFun "expands the functionality of existing non-coding variant prioritizing tools" is not substantiated by direct comparison with other tools beyond DeepSEA.
- The statement that "most disease-related variants have higher SAD values in relevant tissues" is not quantified or statistically validated.
- The manuscript does not provide evidence that the web server is robust to input errors or that the queue system prevents data loss, despite describing these features.
- The claim that the model can predict effects for "novel mutations" is plausible but not explicitly tested in the provided text.