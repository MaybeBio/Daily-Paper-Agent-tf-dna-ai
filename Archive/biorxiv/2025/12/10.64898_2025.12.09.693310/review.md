## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, supplementary file list)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose that Kar4 acts as a regulator of Ste12, promoting Ste12 binding to a specific DNA motif (H-T 4) genome-wide during the yeast pheromone response, and that in the absence of Kar4, Ste12 binds alternative motifs (e.g., T-T 3) leading to aberrant gene expression.
- **Visible evidence base** RNA-seq data (differential expression, clustering, GO analysis), ChIP-exo data (peak calling, motif discovery, occupancy comparisons), AlphaFold3 structural predictions, and reanalysis of published overexpression data
- **Missing materials affecting confidence** All figures, tables, supplementary files, and the Appendix are referenced but not provided. No raw data, quality metrics, or statistical details are directly visible. The ChIP-exo and RNA-seq datasets are deposited in GEO but not accessible from this submission.

## Reviewer
- **Overall assessment** This manuscript addresses an important and unresolved question in yeast mating biology: how the auxiliary factor Kar4 modulates the genome-wide DNA-binding specificity of the master transcription factor Ste12. The authors present a comprehensive dataset combining transcriptomics and chromatin binding profiling, and they propose a novel model in which Kar4 directs Ste12 toward a specific DNA motif configuration (H-T 4) while suppressing binding to alternative configurations. The central claim is plausible and potentially significant, but the evidence as presented in the text is incomplete. Key figures, statistical details, and the Appendix are not available for evaluation, which limits the ability to assess the robustness of the conclusions. The manuscript is well written and the logical flow is clear, but several technical concerns need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers studying eukaryotic transcription factor regulation, particularly those interested in how accessory proteins modulate DNA-binding specificity and how combinatorial control of gene expression is achieved. The yeast pheromone response is a classic model system, and the findings may have broader implications for understanding how transcription factors achieve target specificity in other organisms. The identification of a prevalent H-T 4 motif and the proposed role of Kar4 in enforcing this specificity will be of interest to the yeast community and to those studying signal-dependent gene regulation.

- **Major strengths** The study uses orthogonal approaches (RNA-seq and ChIP-exo) to address the question, which is a strength. The use of pre-synchronized cells for RNA-seq is a methodological improvement over prior work. The identification of a specific DNA motif (H-T 4) associated with Kar4-dependent Ste12 binding is a concrete and testable finding. The integration of published data (Ste12 overexpression) to support the model is a good use of existing resources. The AlphaFold3 prediction of a Kar4-Ste12 interaction provides a structural hypothesis that can be tested experimentally.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** The authors claim that Kar4 promotes Ste12 binding to nearly all Ste12 DNA-binding sites associated with transcriptionally upregulated genes, and that this is reflected in ChIP-exo data.
  - **Evidence pointer** Results section "Kar4 promotes Ste12's DNA association at most transcriptionally pheromone-induced genes"; Figures 4 and 5; Supplementary Files S7 and S8
  - **Concern** The central claim of the paper relies on ChIP-exo data, but no figures, peak counts, occupancy values, or statistical comparisons are visible in the provided text. The authors state that 86% of Ste12-bound genes are also associated with Kar4 after pheromone treatment, but the basis for this percentage, the thresholds used, and the reproducibility across replicates are not described in sufficient detail. Without access to the actual data or figures, it is impossible to evaluate whether the claim is supported.
  - **Why it matters** The conclusion that Kar4 globally promotes Ste12 binding is the foundation of the proposed model. If the ChIP-exo data are not robust or the analysis is flawed, the entire model collapses.
  - **Resolution test** Provide the ChIP-exo figures and detailed statistical analysis, including peak calling thresholds, reproducibility metrics, and a clear comparison of Ste12 occupancy between wild-type and kar4Δ cells at all identified sites.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support
  - **Claim pointer** The authors propose that Kar4 functions by increasing the DNA-binding specificity of Ste12, promoting binding to H-T 4 motifs and preventing binding to non-H-T 4 motifs such as T-T 3.
  - **Evidence pointer** Results sections "Ste12 binds a PRE di-motif with 4 nucleotide spacing and head-to-tail orientation" and "kar4Δ-only genes are primarily Ste12 targets..."; Figures 6, 8, and 9; Supplementary Files S9 and S10
  - **Concern** The distinction between Kar4-dependent and Kar4-independent Ste12 binding sites is based on motif analysis, but the text does not provide sufficient detail on how the H-T 4 motif was defined, how the "best motif" was assigned to each site, and how the statistical significance of motif enrichment was calculated. The claim that Kar4 "prevents" binding to T-T 3 motifs is a strong mechanistic statement that requires direct evidence, such as showing that Ste12 binding to T-T 3 sites is increased in kar4Δ cells. The text mentions this but does not provide quantitative data.
  - **Why it matters** The proposed mechanism is the key novelty of the paper. If the motif analysis is not rigorous or the evidence for a switch in specificity is weak, the conclusion is not established.
  - **Resolution test** Provide the full motif discovery and scanning results, including the definition of H-T 4 and T-T 3 motifs, the statistical significance of enrichment, and a direct comparison of Ste12 occupancy at T-T 3 sites between wild-type and kar4Δ cells.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors use AlphaFold3 to predict that Kar4 and Ste12 form a continuous interchain beta-sheet, and they use this to support their model of Kar4 as a Ste12 regulator.
  - **Evidence pointer** Results section "Ste12 and Kar4 are predicted to form a continuous beta-sheet"; Figure 3; Supplementary File S5
  - **Concern** The AlphaFold3 prediction is presented as a supporting piece of evidence, but the text does not provide details on the confidence of the prediction, the specific residues involved, or whether the predicted interface is consistent with known functional mutations in Kar4 or Ste12. The authors mention that function-disrupting mutations in Kar4 localize to the predicted interface, but this is not shown or quantified.
  - **Why it matters** Structural predictions can be useful, but they are not experimental evidence. If the prediction is not validated or contextualized, it adds little to the argument.
  - **Resolution test** Provide the AlphaFold3 confidence metrics, a figure showing the predicted interface with the relevant mutations mapped, and a discussion of whether the prediction is consistent with existing experimental data.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental design
  - **Claim pointer** The authors state that the RNA-seq and ChIP-exo experiments used different yeast strain backgrounds and different pheromone treatment durations (60 min vs. 90 min), and that general conclusions should be transferable.
  - **Evidence pointer** Results section "Analysis of the transcriptional response to mating pheromone using pre-synchronized cells"; Materials and Methods
  - **Concern** The use of different strain backgrounds and treatment times between the two main datasets is a significant limitation. The authors acknowledge this but do not provide a rigorous justification for why the conclusions should be transferable. Differences in strain background can affect chromatin state and transcription factor occupancy, and the difference in treatment time could capture different phases of the response.
  - **Why it matters** The integration of RNA-seq and ChIP-exo data is central to the paper's conclusions. If the two datasets are not directly comparable, the correlations drawn between transcription and binding may be misleading.
  - **Resolution test** Provide a direct comparison of the transcriptional response in the two strain backgrounds under the same conditions, or at least a discussion of the potential confounding effects and why they are unlikely to affect the conclusions.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Definition of gene classes
  - **Evidence pointer** Results section "Identification of three gene-expression patterns related to Kar4"; Supplementary Figure S4
  - **Issue** The definitions of Kar4-dependent, Kar4-independent, and kar4Δ-only gene classes are described in the text, but the exact criteria (fold-change thresholds, statistical significance) are not fully specified in the main text. The reader is referred to the Methods and Supplementary Files, but these are not available.
  - **Required correction** Provide a clear and concise summary of the classification criteria in the main text or a table.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** GO analysis
  - **Evidence pointer** Results section "RNA-seq analysis of synchronized wild-type, kar4Δ, and ste12Δ cells reveals novel patterns of gene expression"; Supplementary File S4
  - **Issue** The GO analysis identifies several categories unique to the kar4Δ response, including ribosome biogenesis and stress responses. The authors interpret these as consequences of an elevated global pheromone response, but this interpretation is not directly tested.
  - **Required correction** Clarify whether these categories are simply a result of the higher overall response magnitude in kar4Δ cells, or whether they represent qualitatively different regulatory programs.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Novel pheromone-responsive intergenic transcripts
  - **Evidence pointer** Abstract; Results section "Analysis of the transcriptional response to mating pheromone using pre-synchronized cells"
  - **Issue** The abstract mentions the identification of pheromone-responsive intergenic transcripts, but this is not discussed in the main text provided. It is unclear whether these are coding or non-coding, and what their significance might be.
  - **Required correction** Either elaborate on this finding in the main text or remove it from the abstract if it is not a central claim.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** ChIP-exo peak calling
  - **Evidence pointer** Materials and Methods section "ChIP-exo data processing and peak calling"
  - **Issue** The description of peak calling with ChExMix is brief. The text mentions "significant peaks" but does not specify the significance threshold or how multiple peaks per gene were handled.
  - **Required correction** Provide more detail on the peak calling parameters and the criteria for associating peaks with genes.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 11 model
  - **Evidence pointer** Results section "Interactions between H-T 4 and T-T 3 motifs during the pheromone response"; Figure 11
  - **Issue** The model presented in Figure 11 is described in the text, but the figure itself is not available. The text refers to "a simple model" and "another model," but it is not clear which is favored or how the data distinguish between them.
  - **Required correction** Clarify which model is best supported by the data and what specific evidence distinguishes it from alternatives.

- **Technical failings that need to be addressed before the case is established** R1-M1 (ChIP-exo evidence not visible), R1-M2 (motif analysis details missing), R1-M4 (strain background and treatment time mismatch between datasets)

## Risk / unsupported claims
- The claim that Kar4 promotes Ste12 binding to "nearly all" Ste12 binding sites associated with upregulated genes is not verifiable without the ChIP-exo data.
- The claim that Kar4 "prevents" Ste12 binding to T-T 3 motifs is a mechanistic statement that is not directly supported by the text.
- The claim that the AlphaFold3-predicted Kar4-Ste12 interaction is functionally relevant is based on indirect evidence (localization of mutations) that is not shown.
- The claim that the RNA-seq and ChIP-exo datasets are directly comparable despite differences in strain background and treatment time is not rigorously justified.
- The identification of novel pheromone-responsive intergenic transcripts is mentioned but not described or analyzed in the provided text.