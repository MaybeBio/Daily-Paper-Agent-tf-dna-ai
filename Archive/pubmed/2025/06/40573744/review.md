## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions) as provided by the user.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by the reported evidence. Editorial or stylistic issues are noted only where they affect clarity or reproducibility.
- **Shared manuscript claim summary** The authors used AlphaFold2-predicted structures and HawkDock molecular docking to identify putative protein–protein interaction (PPI) sites in the bHLH transcription factors SPATULA (SPT), HECATE1 (HEC1), and INDEHISCENT (IND). Site-directed mutagenesis of predicted interface residues, followed by BiFC assays, showed complete loss of SPT–HEC1 interaction and approximately 50% reduction of SPT–IND interaction. Overexpression of the mutated versions in Arabidopsis produced phenotypes consistent with reduced PPI function, supporting the biological relevance of the predicted sites.
- **Visible evidence base** Main text figures (Figures 1–7), supplementary figure references (Figures S1–S13), supplementary tables (Tables S1, S2, S5), statistical descriptions, and methodological descriptions in Section 4.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S13, S1, S2, S5) were referenced but not provided. Raw numerical data for BiFC quantification, statistical outputs, and full details of docking model selection criteria were not available. Primer sequences and vector maps were not shown.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward application of structure prediction and docking to generate testable hypotheses about PPI interfaces, followed by functional validation. The logic is clear and the work is potentially useful to the plant development community. However, several technical issues limit the strength of the conclusions. The docking-based interface predictions are not validated by any structural or biophysical method, the mutagenesis strategy is not fully justified, and the phenotypic analyses are largely descriptive with limited mechanistic depth. The claim that the predicted sites are "relevant" is supported for SPT–HEC1 but only weakly for SPT–IND. The manuscript would benefit from additional controls, clearer quantification, and a more cautious interpretation of the docking results.
- **Who would be interested in the results, and why** Researchers studying gynoecium and fruit development in Arabidopsis, particularly those interested in bHLH transcription factor function and dimerization. The work also speaks to the broader community using AlphaFold2 and docking tools for hypothesis generation in plant biology. The demonstration that predicted interface residues can be functionally validated by mutagenesis and BiFC may be of interest to method-oriented readers.
- **Major strengths** The study addresses a relevant biological question with a clear pipeline from prediction to functional test. The use of alanine scanning at predicted interface residues is a reasonable approach. The phenotypic analyses, while not exhaustive, are appropriate for an initial functional assessment. The authors are appropriately cautious in some interpretations, particularly regarding the weaker SPT–IND effect.
- **Major Concerns** See items R1-M1 to R1-M5 below.
- **Minor Comments** See items R1-m1 to R1-m5 below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (docking validation), R1-M2 (mutagenesis rationale), R1-M3 (BiFC quantification), R1-M4 (phenotypic specificity), R1-M5 (statistical reporting).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of AlphaFold2 plus docking to bHLH transcription factors in plant development is not entirely new, and the conceptual advance is limited.  
  *Scientific importance*: Moderate. The work provides functional evidence for specific residues in known PPIs, but the broader significance for understanding gynoecium development is incremental.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to plant developmental biologists and computational structural biologists.  
  *Technical soundness*: Weak to moderate. The computational pipeline is reasonable but lacks validation; the functional assays are appropriate but under-quantified.  
  *Readability for nonspecialists*: Acceptable. The manuscript is generally clear, though some sections assume familiarity with plant anatomy and bHLH biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is sound and the data are suggestive, but the current evidence does not fully establish the biological relevance of the predicted sites, particularly for SPT–IND.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that HawkDock molecular docking enabled identification of potential interaction sites that are biologically relevant.  
- **Evidence pointer** Section 2.1, Figures 1, Tables 1 and 2, Tables S1 and S2  
- **Concern** The docking results are presented as the basis for selecting mutation sites, but no validation of the docking predictions is provided. The authors do not compare their predicted interfaces with any known experimental structures or cross-linking data, nor do they assess the reliability of the docking models (e.g., via cluster analysis, scoring function benchmarks, or alternative docking tools). The selection of "model 4" and "model 2" based on binding free energy is not justified beyond a single metric, and no error estimates or confidence measures are given.  
- **Why it matters** Without validation, the predicted interfaces could be artifacts of the docking procedure. The subsequent mutagenesis and BiFC results are interpreted as confirming the predictions, but they could also be explained by non-specific disruption of protein folding or stability. The central claim of the paper depends on the reliability of the docking predictions.  
- **Resolution test** Provide additional evidence that the predicted interfaces are credible, such as (i) comparison with known homologous complex structures, (ii) independent docking with a second algorithm, (iii) molecular dynamics simulations to assess interface stability, or (iv) alanine scanning of control residues outside the predicted interface to show specificity. At minimum, report docking scores for all generated models and justify the selection criteria.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that alanine substitutions were made to residues predicted to be involved in dimer formation, and that these substitutions disrupted PPIs.  
- **Evidence pointer** Section 2.1, Section 2.2, Section 4.2  
- **Concern** The manuscript does not demonstrate that the alanine mutations do not globally disrupt protein structure or stability. The authors note that AlphaFold2 modeling of the mutated versions showed "slight changes" for SPT-4A and no changes for HEC1-2A and IND-3A (Section 3.3, Figure S13), but this is not shown in the main text and the criteria for "slight changes" are not defined. No experimental assessment of protein stability (e.g., thermal shift assays, circular dichroism) or expression levels of the mutant proteins in the BiFC system is provided.  
- **Why it matters** If the mutations cause misfolding or degradation, the loss of BiFC signal could be due to lack of protein rather than loss of interaction. This would undermine the conclusion that the specific residues are important for PPI formation.  
- **Resolution test** Provide experimental evidence that the mutant proteins are expressed at comparable levels to wild-type in the BiFC assay (e.g., western blot or quantitative fluorescence of the fusion protein). Alternatively, perform a control with a structurally neutral mutation (e.g., alanine at a surface-exposed, non-interface residue) to show that the effect is specific to the predicted interface.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors report quantitative BiFC frequencies (e.g., 34.22% for SPT–HEC1, 14.91% for SPT-4A–IND-3A) and claim significant differences.  
- **Evidence pointer** Section 2.2, Figures 2 and 3  
- **Concern** The BiFC quantification is described only as "average frequency of protoplasts with YFP signal" with no indication of the number of independent experiments, the number of protoplasts counted per replicate, or the statistical test used. The figure legends are not provided, so it is unclear whether error bars represent standard deviation or standard error. The statement "significant differences" is not supported by any reported p-values or test statistics.  
- **Why it matters** Without proper statistical reporting, the reader cannot assess the robustness of the observed differences. This is particularly important for the SPT–IND interaction, where the reduction is only about 50% and could be within experimental variability.  
- **Resolution test** Report the number of biological replicates, the total number of protoplasts counted per condition, the statistical test used, and the exact p-values. Provide a clear description of how the frequency was calculated and whether the data were normally distributed.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Scientific importance  
- **Claim pointer** The authors claim that overexpression of the mutated versions affects gynoecium and fruit development, and that the 35S::SPT-4A line phenocopies the spt-2 loss-of-function mutant.  
- **Evidence pointer** Sections 2.4–2.6, Figures 4–6, Figure S7  
- **Concern** The phenotypic analyses are largely descriptive. For the 35S::SPT-4A line, the authors report shorter fruits, reduced seed number, and apical fusion defects, but they do not quantify the penetrance of these phenotypes across independent transgenic lines. For the 35S::HEC1-2A and 35S::IND-3A lines, the effects are modest and the authors do not provide a clear mechanistic explanation. The comparison to the spt-2 mutant is based on visual similarity, but no direct side-by-side comparison or quantitative trait analysis is shown.  
- **Why it matters** The phenotypic data are used to argue for biological relevance, but without quantification and line-to-line consistency, the strength of this claim is limited. The lack of a clear mechanistic link between the molecular interaction defect and the observed phenotypes weakens the overall conclusion.  
- **Resolution test** Provide quantitative data on fruit length, seed number, and gynoecium morphology for multiple independent transgenic lines, with statistical comparisons to wild-type and to the corresponding overexpression of the non-mutated gene. If possible, include a direct comparison with the spt-2 mutant under the same growth conditions.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that the predicted interaction sites are relevant for PPI formation and that the approach is a viable strategy for understanding PPIs.  
- **Evidence pointer** Sections 3.1–3.3, Section 5  
- **Concern** The manuscript does not address the possibility that the observed effects are due to altered DNA binding rather than altered protein–protein interactions. The bHLH domain is involved in both DNA binding and dimerization, and the mutations in HEC1-2A are located in the basic region, which is known to mediate DNA contact. The authors do not test whether the mutant proteins retain DNA-binding activity.  
- **Why it matters** If the mutations affect DNA binding, the phenotypic effects could be due to loss of transcriptional activity rather than loss of dimerization. This would change the interpretation of the results and the conclusions about PPI relevance.  
- **Resolution test** Perform DNA-binding assays (e.g., EMSA) with wild-type and mutant proteins to determine whether the mutations affect DNA binding. Alternatively, use a dimerization-specific assay that does not depend on DNA binding, such as co-immunoprecipitation or a mammalian two-hybrid system.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 4.1  
- **Evidence pointer** Section 4.1  
- **Issue** The description of the AlphaFold2 modeling is brief. The authors state that "default MSA settings were applied" and that "advanced settings were adjusted to set the maximum interactions to 0," but it is unclear what this parameter controls and why it was changed.  
- **Required correction** Provide a more detailed description of the modeling parameters, including the version of ColabFold used, the number of recycles, and the rationale for changing the "maximum interactions" setting.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 4.2  
- **Evidence pointer** Section 4.2, Table S1  
- **Issue** The primer sequences are listed in Table S1, but this table is not provided. The authors also do not specify the template concentration or the PCR cycling conditions for the mutagenesis.  
- **Required correction** Include the primer sequences in the main text or a supplementary table that is available. Provide the full PCR protocol, including annealing temperatures and extension times.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.2, Figures 2 and 3  
- **Evidence pointer** Section 2.2  
- **Issue** The figure legends are not provided, so it is unclear what the error bars represent and what the asterisks (if any) indicate. The text mentions "significant differences" but does not specify which comparisons were significant.  
- **Required correction** Provide complete figure legends with definitions of error bars and significance levels. In the text, specify which pairwise comparisons were tested and report the p-values.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.7, Figure 7  
- **Evidence pointer** Section 2.7  
- **Issue** The style width measurements are reported in micrometers, but the text in Section 2.7 states "288.7 ± 8.71.mm" and "240.4 ± 14.51 mm" for the IND lines, which appears to be a typo (should be µm).  
- **Required correction** Correct the units in the text to µm for consistency.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 4.6  
- **Evidence pointer** Section 4.6  
- **Issue** The statistical analysis section states that "6 fruits from ten homozygous plants of each line (n = 60) were collected," but it is unclear whether the ten plants were independent transgenic lines or ten plants from a single line.  
- **Required correction** Clarify whether the ten plants were from independent transgenic events or from a single homozygous line. If from a single line, the statistical analysis should account for the lack of independent transformation events.

## Risk / unsupported claims
- The claim that the predicted interaction sites are "biologically relevant" is supported for SPT–HEC1 by the complete loss of BiFC signal, but the lack of protein-level controls makes this claim not fully established.
- The claim that the 35S::SPT-4A line phenocopies the spt-2 loss-of-function mutant is based on visual similarity and is not quantitatively supported.
- The claim that the approach is a "viable strategy" for understanding PPIs is not supported by comparison with alternative methods or by validation of the docking predictions.
- The statement that "the predicted interaction sites are relevant and, when modified, affect gynoecium development" is an overgeneralization, as the effects on gynoecium development were only observed for SPT-4A and HEC1-2A, and the link to the specific interaction defect is not demonstrated.
- The docking results (Tables S1 and S2) and the AlphaFold2 confidence scores (Figures S1–S3) are referenced but not available for assessment.