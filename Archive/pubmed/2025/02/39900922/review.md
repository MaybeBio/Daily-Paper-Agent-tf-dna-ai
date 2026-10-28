## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with Nature-style criteria. No line numbers were provided; references to specific locations are by section or figure name.
- **Shared manuscript claim summary** The authors present regX, a mechanism-informed deep neural network that incorporates gene-level regulatory processes (via a learnable transcriptional activity matrix, TAM) and gene-gene interactions (via graph neural networks) to predict cell states from single-cell multi-omics data. The model is used for in-silico perturbation to prioritize potential driver transcription factors (TFs) and cis-regulatory elements (cCREs) underlying cell state transitions. Applications to type 2 diabetes (T2D) and hair follicle development datasets yield prioritized regulators with reported therapeutic, drug repurposing, and putative causal SNP implications.
- **Visible evidence base** Abstract, Introduction, Results (including Figures 1–5 and Tables 1–2), Discussion, Methods, and Supplementary figure/table references.
- **Missing materials affecting confidence** Full figure panels and supplementary figures/tables were not provided in the submitted text. Exact hyperparameters, model architecture details (e.g., layer sizes, activation functions), and code availability are not fully described. Details of the external TF perturbation dataset benchmarking (Supplementary Figs. 5, 6) and the full results of ablation studies are not visible. Statistical test details for some comparisons (e.g., Fig. 2a) are only partially described.

## Reviewer
- **Overall assessment** The manuscript presents a novel and potentially valuable framework for integrating regulatory mechanisms into deep learning models for cell state prediction and regulator prioritization. The two-step training strategy and the design of the TAM are thoughtful and represent a meaningful advance over existing biologically informed neural networks. The applications to T2D and hair follicle development demonstrate the model's utility and generate biologically plausible hypotheses, including drug repurposing and causal SNP identification. However, several technical aspects require clarification and additional validation to fully establish the model's advantages over existing methods and the robustness of the reported findings. The claims of "mechanistic interpretation" and "driver" prioritization need to be more carefully qualified given the in-silico nature of the perturbations and the lack of direct experimental validation for most predictions.
- **Who would be interested in the results, and why** Computational biologists developing interpretable deep learning models for single-cell multi-omics data; researchers studying gene regulatory networks and cell fate decisions; investigators in diabetes research and developmental biology interested in identifying key transcriptional regulators and potential therapeutic targets; and researchers in the post-GWAS field seeking to prioritize causal variants and genes.
- **Major strengths**
  1. The mechanism-informed design of regX, particularly the TAM, is a novel and principled approach to modeling transcriptional regulation, moving beyond simple feature concatenation.
  2. The two-step training strategy is practical and addresses the challenge of learning TF-cCRE interactions in a high-dimensional space.
  3. The model's flexibility is demonstrated through its application to two distinct biological contexts (disease and development) and its adaptation to different knowledge bases (PPI and GO).
  4. The downstream analyses, including drug repurposing and pcSNP identification, provide translational relevance and generate testable hypotheses.
  5. The benchmarking against external datasets (TF perturbation, ChIP-seq) adds credibility to the model's predictive performance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness and validation
  - **Claim pointer** The authors claim that regX "reliably prioritizes key transcription factors and candidate cis-regulatory elements" and that the model provides "mechanistic interpretations."
  - **Evidence pointer** Results sections "regX prioritizes TFs that potentially drive beta cell transitions during T2D progression" and "regX prioritizes cCREs that potentially drive beta cell transitions during T2D progression"; Figure 3; Table 1.
  - **Concern** The primary evidence for the validity of the prioritized regulators is literature-based correlation. While this is a reasonable first step, it does not constitute a rigorous validation of the model's ability to identify *drivers* of cell state transitions. The in-silico perturbation approach predicts the effect of a regulator on the model's output, but this is not equivalent to demonstrating a causal role in the actual biological process. The authors acknowledge this limitation in the Discussion, but the Results section presents these findings with strong language ("reliably prioritizes", "drive"). A more rigorous validation would involve comparing predictions against a larger set of experimentally validated regulators (e.g., from Perturb-seq or CRISPR screens) or demonstrating that the model's predictions are robust to different training data splits and model initializations. The benchmarking against the external TF perturbation dataset (Supplementary Figs. 5, 6) is a step in this direction, but the details and results are not fully visible in the provided text.
  - **Why it matters** The central claim of the manuscript is that regX can identify potential driver regulators. If the validation is only correlative, the scientific impact is significantly diminished, and the model's utility for generating novel, reliable hypotheses is questionable. The distinction between correlation and causation is critical for the credibility of the findings.
  - **Resolution test** The authors should provide a more comprehensive validation of the prioritized regulators. This could include: (1) a quantitative comparison of regX's top-ranked regulators against a gold-standard set of known drivers for the specific cell state transitions studied; (2) an analysis of the robustness of the prioritization to different random seeds and data splits; (3) a demonstration that the model's predictions are not simply recapitulating known biology but can identify novel regulators that are subsequently validated experimentally (or at least through independent computational methods). The details of the external benchmarking (Supplementary Figs. 5, 6) must be clearly presented in the main text or supplementary materials.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness and clarity
  - **Claim pointer** The authors claim that the TAM is more informative than concatenated features and that the learned TF-cCRE interactions contain "extra regulatory information."
  - **Evidence pointer** Results section "Data-driven transcriptional regulatory modeling captures TF-cCRE interactions"; Figure 2.
  - **Concern** The improvement in gene expression prediction (average PCC 0.83 vs. 0.76) is statistically significant but modest. The biological significance of this improvement is not fully discussed. More importantly, the claim that the learned interactions contain "extra regulatory information" is based on a comparison with TFBS, which is a sequence-based prediction. The TAM learns interactions from expression and accessibility data, so it is expected to capture information beyond sequence motifs. The analysis of motif consistency (Fig. 2c–e) is interesting but only covers a small fraction of TF-cCRE pairs (6.1% on average). The interpretation of the motif characteristics (length, GC-content) is speculative and requires further investigation. The comparison with ChIP-seq data (Supplementary Fig. 3) is valuable, but the overall F1 scores are not reported in the main text, making it difficult to assess the absolute performance.
  - **Why it matters** The novelty of the TAM is a key contribution of the paper. If the improvement is marginal and the learned interactions are not demonstrably more accurate or biologically meaningful than existing methods, the significance of this contribution is weakened. The authors need to more clearly articulate the specific advantages of the TAM over simpler alternatives.
  - **Resolution test** The authors should provide a more detailed analysis of the learned TF-cCRE interactions. This could include: (1) a comparison of the TAM's performance against a wider range of baseline models, including more sophisticated feature engineering; (2) an analysis of the biological relevance of the learned interactions, e.g., by examining whether they are enriched for known regulatory elements or eQTLs; (3) a clearer presentation of the ChIP-seq benchmarking results, including the F1 scores and a discussion of the trade-offs between precision and recall.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance and generalizability
  - **Claim pointer** The authors claim that regX is a "flexible" framework that can be "tailored to study different biological problems," as demonstrated by its application to hair follicle development.
  - **Evidence pointer** Results section "regX prioritizes TFs in cell fate determinations during hair follicle development"; Figure 5.
  - **Concern** The application to hair follicle development is presented as a demonstration of the model's versatility. However, the analysis is less detailed than the T2D analysis. The key finding, that different upregulation levels of the same TF (Lef1) can lead to distinct cell fates, is interesting but is only shown for a single TF. The model's performance on this dataset is compared to a linear layer baseline, but the improvement is not always significant. The generalizability of the framework to other types of cell state transitions (e.g., continuous processes without clear discrete states) is not fully addressed. The model's reliance on pre-defined cell states and knowledge bases (PPI, GO) may limit its applicability to less well-characterized systems.
  - **Why it matters** The claim of flexibility and generalizability is important for the broader impact of the work. If the model only works well on well-annotated systems with clear cell states, its utility is limited. The authors should provide a more thorough demonstration of the model's adaptability and discuss its potential limitations in other contexts.
  - **Resolution test** The authors should expand the hair follicle analysis to include a more comprehensive validation of the prioritized TFs, perhaps by comparing them to known regulators of hair follicle development. They should also discuss the model's applicability to other types of data and biological questions, and clearly state any assumptions or limitations.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and reproducibility
  - **Affected element** Methods section "regX training"
  - **Evidence pointer** Methods, "regX training"
  - **Issue** The description of the two-step training strategy is clear, but some hyperparameters (e.g., learning rate, number of epochs, early stopping criteria) are not fully specified. The exact architecture of the gene subnet (e.g., number of layers, hidden units) is also not detailed.
  - **Required correction** Provide a complete list of hyperparameters and a detailed description of the network architecture, or refer to a publicly available code repository where these details are documented.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Figure 2a
  - **Evidence pointer** Figure 2a
  - **Issue** The p-values for the comparison of TAM vs. control groups are reported, but the effect sizes are not. The boxplots show the distribution of PCCs, but it would be helpful to report the mean and standard deviation for each group.
  - **Required correction** Report the mean and standard deviation of the PCCs for each feature type in the text or figure legend.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity of claims
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion
  - **Issue** The Discussion states that regX "computationally reproduced the repurposing of BROMOCRIPTINE." This is a strong claim. The model identified FOS as a top regulator, and BROMOCRIPTINE is known to interact with FOS-related pathways. However, this is a post-hoc interpretation, not a prospective prediction. The language should be softened to reflect this.
  - **Required correction** Rephrase to "the model's predictions are consistent with the known repurposing of BROMOCRIPTINE" or similar.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1
  - **Issue** The figure is complex and contains a lot of information. The text in the figure legend is helpful, but the figure itself may be difficult to interpret without a more detailed explanation.
  - **Required correction** Consider simplifying the figure or providing a more detailed step-by-step explanation in the legend.

## Risk / unsupported claims
- The claim that regX "reliably prioritizes" driver regulators is not fully supported by the evidence presented, which is primarily correlative and literature-based.
- The claim that the model provides "mechanistic interpretations" is an overstatement. The model provides a pathway from regulator to cell state via learned interactions, but this is a computational inference, not a validated mechanism.
- The specific claim that "different upregulation levels of the same TF can result in entirely different cell fates" is based on a single example (Lef1) and requires further validation.
- The identification of five pcSNPs is based on a specific analytical pipeline and assumptions; the functional significance of these SNPs is not experimentally validated.
- The generalizability of the framework to other biological systems and data types is not fully established.