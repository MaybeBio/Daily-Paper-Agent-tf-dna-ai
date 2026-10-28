## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table references.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence. Editorial or stylistic issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors propose a computational-experimental workflow combining all-atom structure-based molecular dynamics simulations, AlphaFold2 structure prediction, and in vivo luminescence assays to identify C-terminal domain residues that stabilize the autoinhibited state of the metamorphic protein RfaH. They report that residues I129 and L142, located at the tip of the α-helical hairpin, contribute to stabilizing the autoinhibited state, with L142A and I129A showing ops-independent activation in vivo.
- **Visible evidence base** Main text figures 1–4 (referenced), supplementary figures S1–S30 (referenced), supplementary tables S1–S3 (referenced), methods section, and data availability statement with Zenodo link.
- **Missing materials affecting confidence** Actual figure images and supplementary files were not provided. Numerical values for luminescence assays, statistical test details, AlphaFold2 confidence metrics (pLDDT, PAE), and simulation convergence criteria are referenced but not visible. The Zenodo data repository contents were not accessed.

## Reviewer

- **Overall assessment** This manuscript presents a well-structured, multi-method approach to a biologically relevant question in the field of metamorphic proteins. The combination of simulation, prediction, and experiment is commendable and the identification of I129 and L142 as functionally relevant residues is a useful contribution. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. The lack of visible quantitative data for the in vivo assays, the absence of statistical detail, and the limited discussion of AlphaFold2 prediction reliability for metamorphic proteins are notable weaknesses. The workflow itself is potentially valuable for the community, but the manuscript would benefit from clearer presentation of the experimental data and a more critical interpretation of the computational predictions.

- **Who would be interested in the results, and why** Researchers studying metamorphic or fold-switching proteins, particularly those interested in the NusG/RfaH family of transcription factors. The methodological workflow combining SBM simulations, AlphaFold2, and in vivo assays could be of interest to computational biologists and experimentalists working on protein conformational switching. The specific residues identified may inform future mutagenesis studies and mechanistic investigations of RfaH regulation.

- **Major strengths** The study integrates three complementary approaches, which is a methodological strength. The use of all-atom SBMs to identify candidate residues is well-reasoned and builds on prior work. The inclusion of both positive (E48A) and negative (F126, V154) controls in the AlphaFold2 predictions is appropriate. The in vivo assay is functionally relevant, directly measuring RfaH activity in a physiological context. The authors are appropriately cautious in acknowledging discrepancies between computational methods and in noting limitations of AlphaFold2 for metamorphic proteins.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and reproducibility
  - **Claim pointer** The claim that "I129A and L142A dramatically activate RfaH independently of the ops signal" is central to the paper's conclusions.
  - **Evidence pointer** Figure 4a,b; Results section "In vivo assays validate the role of these CTD residues in stabilizing the autoinhibited state of RfaH"; location not provided for numerical values.
  - **Concern** The in vivo luminescence data are described qualitatively ("dramatically activate", "higher luminescence") but no numerical values, fold-changes, error bars, or statistical significance levels are provided in the visible text. The figure is referenced but not shown. Without these data, the reader cannot assess the magnitude of the effect or its reliability.
  - **Why it matters** The experimental validation is the cornerstone of the paper's conclusion. If the effect sizes are small or the variability high, the conclusion that these residues "control" the fold-switch would be overstated. Reproducibility requires access to the actual data.
  - **Resolution test** Provide the numerical luminescence values for all variants tested, including WT, E48A, I129A, L142A, E136A, S139A, and V154, for both opsWT and opsG8C conditions. Include error bars, number of replicates, and appropriate statistical tests (e.g., ANOVA with post-hoc comparisons). State the threshold for "activation" and justify it.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretation of computational predictions
  - **Claim pointer** The statement that AlphaFold2 predictions "confirm the relevance of CTD residues for RfaH fold-switch" and that specific variants "led to several models with mixed α/β secondary structure."
  - **Evidence pointer** Figure 3a,b; Results section "AlphaFold2 predictions confirm the relevance of CTD residues for RfaH fold-switch"; Supplementary Figures S2–S28.
  - **Concern** The manuscript reports that AlphaFold2 predicted mixed α/β structures for certain variants, but the criteria for classifying a prediction as "mixed" are not fully described. The k-means clustering based on RMSD of residues 126–131 is a local measure and may not capture global fold changes. The hierarchical clustering using TM-score is mentioned but the threshold of 0.12 is not justified. The number of structures classified as mixed for each variant is not reported numerically, only described qualitatively ("similar or higher number").
  - **Why it matters** AlphaFold2 is not designed to predict alternative conformations of metamorphic proteins, and its reliability for this purpose is debated. The authors acknowledge this but then use the predictions as supporting evidence. Without clear, quantitative criteria for what constitutes a "mixed" prediction and how many structures fall into this category, the claim that these predictions "confirm" the relevance of the residues is not well-supported.
  - **Resolution test** Provide a clear definition of the classification criteria for mixed α/β structures. Report the number (and percentage) of structures classified as mixed for each variant under each condition. Show representative structures with clear secondary structure assignments. Discuss the limitations of using AlphaFold2 for this purpose more critically, perhaps by comparing predictions to known experimental structures of the active state.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological rigor of simulations
  - **Claim pointer** The claim that MD simulations "identified eight CTD residues with high interdomain contact probability" and that these are "expected to play a crucial role in stabilizing the autoinhibited state."
  - **Evidence pointer** Figure 2c,d; Results section "All-atom SBM simulations identify residues with high interdomain contact probability"; Methods section "All-atom SBM-based MD simulations".
  - **Concern** The manuscript states that simulations were run at 31 temperatures, but the analysis of contact probabilities is only described for "the transition state" (Q ~ 0.35). The selection of this specific Q value is not justified. The convergence of the simulations is not discussed. The contact probability threshold of 0.4 is stated but not justified. The relationship between contact probability in the transition state and functional importance is assumed but not directly tested.
  - **Why it matters** The simulation results form the basis for selecting residues for further study. If the transition state ensemble is not well-defined or the simulations are not converged, the identified residues may not be reliable. The field of protein folding simulations requires careful attention to sampling and convergence.
  - **Resolution test** Provide evidence of simulation convergence (e.g., block averaging, multiple independent runs). Justify the choice of Q = 0.35 as representing the transition state. Show the distribution of contact probabilities and explain why 0.4 is a meaningful threshold. Consider testing the robustness of the identified residues to changes in these parameters.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1; Introduction section.
  - **Issue** The manuscript refers to Figure 1 for a schematic of the RfaH fold-switch, but the figure is not visible. The text description is brief.
  - **Required correction** Ensure the figure clearly shows the two states of RfaH, the ops element, RNAP, and the ribosome, with labels for the NTD, CTD, and the interdomain interface. Add a more detailed legend.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure 4
  - **Evidence pointer** Figure 4a,b; Results section "In vivo assays validate the role of these CTD residues in stabilizing the autoinhibited state of RfaH".
  - **Issue** The statistical analysis of the luminescence data is not described. It is unclear how many biological replicates were performed and what statistical test was used.
  - **Required correction** Add a statistical methods subsection describing the tests used, the number of replicates, and the criteria for significance. Report p-values or confidence intervals in the figure or its legend.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness of methods
  - **Affected element** AlphaFold2 predictions
  - **Evidence pointer** Methods section "In silico alanine scanning mutagenesis and AlphaFold2 protein structure prediction".
  - **Issue** The methods for AlphaFold2 predictions are described, but the specific version of ColabFold and the parameters used (e.g., number of recycles, dropout rate) are not fully specified. The criteria for selecting the "best" predicted structure (Rank 1) are not stated.
  - **Required correction** Provide the exact version of ColabFold/AlphaFold2 used, all non-default parameters, and the ranking criteria. Consider depositing the prediction scripts or providing a link to them.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section.
  - **Evidence pointer** Discussion section; location not provided.
  - **Issue** The discussion of why E136A did not show an effect in vivo despite computational predictions is brief. The possibility of compensatory mutations or alternative mechanisms is not explored.
  - **Required correction** Expand the discussion of discrepancies between computational predictions and experimental results. Consider whether the computational methods are sensitive to the specific role of E136 or whether the in vivo assay is insensitive to its loss.

- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of visible quantitative data for the in vivo experiments (R1-M1). Without these data, the central claim of the paper cannot be fully evaluated. The criteria for classifying AlphaFold2 predictions as "mixed" also need to be more rigorously defined and justified (R1-M2). The simulation analysis would benefit from a more detailed description of convergence and transition state identification (R1-M3).

- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its specific combination of methods applied to RfaH, though individual components (SBM simulations, AlphaFold2, in vivo assays) are established. The identification of specific residues is a new contribution.
  - **Scientific importance** The findings are of moderate importance. They advance understanding of a specific metamorphic protein but do not yet provide a general principle or mechanism that would broadly impact the field. The workflow may be of interest to others studying similar systems.
  - **Interdisciplinary readership** The work bridges computational biophysics, structural biology, and microbiology. It would appeal to researchers in these areas but may be less accessible to a broader audience.
  - **Technical soundness** The technical approach is generally sound, but the lack of visible quantitative data and the uncritical use of AlphaFold2 for a metamorphic protein are concerns. The simulation methods are appropriate but need more detail on convergence.
  - **Readability for nonspecialists** The manuscript is clearly written but assumes familiarity with the RfaH system and computational methods. The abstract is accessible, but the results section would be challenging for a nonspecialist. The lack of visible figures makes it difficult to follow the argument.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the combination of methods is valuable. However, the manuscript in its current form does not fully establish the central claim due to the lack of visible quantitative data and the need for more rigorous analysis of the computational predictions. The authors should be encouraged to revise and resubmit with the requested data and clarifications.