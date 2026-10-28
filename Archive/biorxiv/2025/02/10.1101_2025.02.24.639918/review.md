## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific validity, technical soundness, and claims as presented in the provided text; no supplementary figures or tables were available for direct inspection
- **Shared manuscript claim summary** The authors present a modular computational workflow that combines existing machine learning models for protein function prediction and MHC-II peptide presentation prediction to simultaneously optimize protein function and minimize immunogenicity. They apply this workflow to transcriptional activation domains, RNA-binding domains, and zinc finger arrays, and demonstrate functional deimmunized transcription factors targeting UTRN and SCN1A.
- **Visible evidence base** Main text figures referenced (Figs. 1–6), supplementary figures and tables referenced but not provided, methods section, data availability statement
- **Missing materials affecting confidence** Supplementary figures (S1–S6), supplementary tables (S1–S4), RNA-seq data, flow cytometry data, plasmid maps, and code repository contents were not available for review

## Reviewer

- **Overall assessment** This manuscript presents a timely and conceptually valuable framework for addressing immunogenicity in engineered therapeutic proteins. The modular design, emphasizing replaceable prediction algorithms, is a strength. However, the evidence provided in the main text is insufficient to fully evaluate the robustness of the claims. Key quantitative data, statistical details, and validation of computational predictions against experimental outcomes are largely absent from the visible text. The workflow is demonstrated on a small number of examples, and the generalizability claims require stronger support. The manuscript would benefit from clearer presentation of experimental results and a more critical discussion of the limitations of the prediction algorithms used.

- **Who would be interested in the results, and why** Researchers in protein engineering, synthetic biology, and cell and gene therapy development would be interested. The work addresses a practical problem in the field: reducing immunogenicity of engineered proteins derived from human scaffolds. The modular workflow is potentially useful for groups working on transcription factors, RNA-binding proteins, and other therapeutic proteins. The demonstration of deimmunized zinc finger arrays targeting endogenous genes is relevant to gene therapy applications.

- **Major strengths**
  1. The conceptual framework of dual-objective optimization (function and immunogenicity) is well articulated and addresses a real gap in current practice.
  2. The emphasis on modularity, allowing substitution of prediction algorithms, is forward-looking and practical.
  3. The application to multiple protein types (activation domain, RNA-binding domain, DNA-binding domain) demonstrates breadth.
  4. The use of human-derived components throughout is a principled approach to reducing immunogenicity risk.
  5. The demonstration of functional deimmunized transcription factors targeting therapeutically relevant genes (UTRN, SCN1A) is a meaningful proof of concept.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that deimmunized variants of NZF and PUF-9R retain function comparable to the original proteins (Figs. 1e, 2f).
- **Evidence pointer** Figures 1e and 2f, described in text; quantitative values not provided in text
- **Concern** The main text states that deimmunized NZF "could induce transcription of BFP... to a level equal to the original version" and that deimmunized PUF-9R "restored the function... to a level comparable to the original domain." However, no quantitative data, effect sizes, or statistical comparisons are presented in the text. The figures are referenced but not visible in the provided material.
- **Why it matters** The central claim of the workflow is that deimmunization can be achieved without compromising function. Without quantitative evidence, this claim cannot be assessed. The PUF-9R case explicitly shows a reduction in function after deimmunization, which is then rescued by optimization, but the magnitude of the initial loss and the degree of rescue are not stated.
- **Resolution test** Provide quantitative measurements (e.g., mean fluorescence intensity, fold activation) with error bars and statistical tests for all functional assays. State the effect sizes for the deimmunized versus original constructs and for the optimized versus deimmunized constructs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the workflow produces proteins with "no nonhuman peptides that are predicted to be presented by the MHC alleles" at a false omission rate threshold of 0.001.
- **Evidence pointer** Methods section "MHC presentation prediction and threshold determination"; Figures 1d, 1f, 6h
- **Concern** The threshold definition and its application are not fully transparent. The text states that the threshold corresponds to a false omission rate of 0.001, derived from ROC data obtained via personal communication. The prevalence of presented peptides was assumed to be 1%. This assumption is critical and not justified. Furthermore, the text notes that the threshold lies at about the 63rd percentile of peptide scores, which seems counterintuitive for a stringent threshold. The choice of 15mer peptides and the focus on HLA-DRB1*01:01 are reasonable but limit generalizability.
- **Why it matters** The entire deimmunization claim rests on the validity of the threshold and the prediction algorithm. If the threshold is not appropriately calibrated, the claim of "deimmunized" proteins is unsupported. The reliance on personal communication for ROC data is a reproducibility concern.
- **Resolution test** Provide the ROC data or a clear derivation of the threshold. Justify the prevalence assumption. Show the distribution of peptide scores for the constructs and the number of peptides above and below the threshold. Discuss the sensitivity of the results to the threshold choice.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the zinc finger arrays are "largely orthogonal to one another" and that off-target effects for ZNF35/IKZF1 may be due to expression level or integration site.
- **Evidence pointer** Figure 3e, 3g; text in Results and Discussion
- **Concern** The off-target analysis relies on RNA-seq data from stable cell lines. The text mentions variable results, with ZNF35/IKZF1 having widespread off-target effects. The authors offer possible explanations (integration site, expression level) but do not provide data to distinguish these possibilities. The claim of orthogonality is based on reporter assays with synthetic binding sites, not on genome-wide specificity.
- **Why it matters** For therapeutic applications, off-target effects are a critical safety concern. The current evidence does not establish that the deimmunized zinc finger arrays are sufficiently specific for endogenous gene regulation. The difference between the modest off-target effects of some constructs and the widespread effects of another is not explained.
- **Resolution test** Provide RNA-seq data analysis showing the number and identity of differentially expressed genes for each construct. Correlate off-target effects with expression levels of the transcription factors. Perform chromatin binding assays (e.g., ChIP-seq) to assess genome-wide binding specificity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the workflow is "future-proof" and "modular" because prediction algorithms can be swapped.
- **Evidence pointer** Introduction, Discussion
- **Concern** While the modularity is conceptually appealing, the manuscript does not demonstrate that the workflow functions effectively with alternative algorithms. The choice of MARIA and ZifRC/DeepZF is specific, and the results are dependent on these choices. The claim of future-proofing is speculative.
- **Why it matters** The utility of the workflow depends on its adaptability to improved algorithms. Without a demonstration of how the workflow performs with different algorithm combinations, the claim is not supported.
- **Resolution test** Perform a sensitivity analysis using at least one alternative MHC-II prediction algorithm and one alternative zinc finger specificity prediction algorithm. Show that the workflow still produces functional deimmunized constructs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Flow cytometry and data analysish"
- **Evidence pointer** Methods section
- **Issue** The section title contains a typo ("analysish").
- **Required correction** Correct the typo to "analysis".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "MHC presentation prediction and threshold determination"
- **Evidence pointer** Methods section
- **Issue** The ROC data used to determine the threshold was obtained via personal communication. This is not a reproducible source.
- **Required correction** Provide the ROC data as a supplementary file or cite a public source. Alternatively, describe the derivation of the threshold in sufficient detail to be reproducible.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Figure 6
- **Evidence pointer** Figure 6b, 6d, 6e
- **Issue** The text states that UTRN-14 was selected for being adjacent to another targetable site, but the co-binding construct was not functional. The rationale for selecting UTRN-14 over other possible sites is not fully explained.
- **Required correction** Clarify the selection criteria for the final UTRN and SCN1A target sites, including a discussion of why the adjacent site strategy was abandoned.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of off-target effects for ZNF35/IKZF1 mentions an "earlier version of this construct" with seven rather than six zinc fingers. This is confusing because the main text describes the final construct.
- **Required correction** Clearly distinguish between the preliminary and final versions of the constructs and explain why the preliminary version was used in the RNA-seq experiment.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Quantitative functional data are missing.
  - R1-M2: Threshold derivation and calibration are not transparent.
  - R1-M3: Off-target analysis is incomplete and does not establish specificity.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of combining existing prediction tools for dual-objective protein engineering is not entirely new, but the specific application to deimmunization of human-derived therapeutic proteins is a useful contribution. The work does not introduce fundamentally new methods but rather a new workflow.
  - **Scientific importance** The problem of immunogenicity in cell and gene therapy is important and timely. The workflow addresses a practical need. However, the demonstrated impact is limited by the small number of examples and the lack of in vivo validation.
  - **Interdisciplinary readership** The work bridges computational biology, protein engineering, and immunology. It would be of interest to researchers in these fields. The writing is generally accessible, though some sections assume familiarity with specific prediction tools.
  - **Technical soundness** The computational predictions are plausible, but the experimental validation is incomplete. The lack of quantitative data and the unresolved off-target issues weaken the technical case.
  - **Readability for nonspecialists** The abstract and introduction are clear. The results section is dense and would benefit from more explicit explanations of the experimental setups and outcomes. The methods section is standard.

- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising, and the work addresses an important problem. However, the evidence presented in the main text is insufficient to support the central claims of functional equivalence after deimmunization and genomic specificity. The manuscript requires substantial revision, including the addition of quantitative data, a more rigorous treatment of the prediction thresholds, and a more complete analysis of off-target effects, before the case is established.

## Risk / unsupported claims
- The claim that deimmunized NZF retains function "equal to the original version" is unsupported without quantitative data.
- The claim that deimmunized PUF-9R function is "comparable to the original domain" after optimization is unsupported without quantitative data.
- The claim that the workflow produces proteins with no predicted immunogenic peptides is dependent on the unvalidated threshold and the specific prediction algorithm.
- The claim of "largely orthogonal" zinc finger arrays is not supported by genome-wide specificity data.
- The claim that the workflow is "future-proof" is speculative and not demonstrated.
- The generalizability of the workflow to other protein types beyond the examples shown is not established.