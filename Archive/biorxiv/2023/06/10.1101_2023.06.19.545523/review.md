## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, author contributions, data availability, funding, competing interests)
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, reproducibility, and alignment with Nature-style criteria based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present KaScape, a sequencing-based method for exhaustive characterization of protein-DNA binding affinity across all possible sequences of a given length. They apply it to 12 Arabidopsis WRKY family DNA binding domains, report a conserved core GAC motif, and introduce KGViewer, a K-mer-based 3D visualization tool.
- **Visible evidence base** Abstract, introduction, methods sections 2.1-2.5, results sections 3.1-3.3, figure references (Fig 1-5, Fig S1-S9), tables referenced (Table S1-S9), author contributions, data availability, funding, competing interests
- **Missing materials affecting confidence** Figures and tables are referenced but not provided; supplementary materials (Table S1-S9, Fig S1-S9) are not included; sequencing data and analysis scripts are not directly assessable; no quantitative error bars or statistical tests are described in the text

## Reviewer

- **Overall assessment** The manuscript describes a conceptually interesting approach to exhaustively measure protein-DNA binding affinities using randomized DNA libraries and NGS. The method has potential utility for the transcription factor community. However, the current text lacks critical quantitative details, validation metrics, and direct comparisons to established methods. The claims of exhaustiveness and quantitative accuracy are not fully supported by the evidence presented. The writing is often informal and imprecise, and several methodological steps are under-specified. The work is potentially publishable in a specialized journal after substantial revision, but the current version does not meet the standards of a high-impact general journal.

- **Who would be interested in the results, and why** Researchers studying transcription factor-DNA interactions, particularly those interested in comprehensive binding affinity landscapes, weak or non-canonical binding sites, and quantitative models of gene regulation. The method could also appeal to computational biologists developing binding site prediction algorithms, as KaScape provides empirical affinity data for all possible k-mers. The KGViewer tool may be of interest to the broader genomics community for visualizing high-dimensional sequence-function relationships.

- **Major strengths**  
  1. The conceptual advance of measuring binding to all possible sequences in a single experiment is genuinely useful and addresses a real limitation of existing methods like SELEX.  
  2. The use of a randomized DNA library with controlled length (4-7 nt) is a clean design that allows exhaustive coverage.  
  3. The normalization of bound sequences against the input library to compute relative affinities is a sound principle that accounts for synthesis bias.  
  4. The application to 12 WRKY family proteins provides a systematic dataset that could be valuable for understanding family-wide binding specificity.  
  5. The development of KGViewer as an open-source visualization tool is a practical contribution.

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The method "quantitatively characterize[s] the relative binding strength of a TF to all possible binding sequences" (abstract) and "robustly characterized the binding landscape of all possible TFBS" (section 3.1).  
  - **Evidence pointer** Section 2.3, Section 3.1, Figure 2  
  - **Concern** The manuscript does not provide a clear definition of the "relative intensity" metric beyond a ratio of proportions (section 2.3.5). Critically, the text does not explain how background or non-specific binding is distinguished from specific binding, how the washing steps affect the equilibrium measurements, or whether the measured values correspond to equilibrium dissociation constants. The claim of quantitative characterization requires a validated relationship between the relative intensity and a thermodynamic or kinetic binding constant.  
  - **Why it matters** Without a clear biophysical interpretation of the measured values, the method cannot be compared to established quantitative approaches (e.g., SELEX-seq, MITOMI, or SPR). The claim of "quantitative" characterization is central to the paper's novelty and utility.  
  - **Resolution test** The authors should provide a calibration experiment comparing KaScape-derived relative intensities to independently measured binding affinities (e.g., by EMSA or SPR) for a set of sequences. They should also define the mathematical relationship between relative intensity and binding affinity, including error propagation.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Reproducibility  
  - **Claim pointer** "KaScape provides a high-throughput, easy-to-operate, sensitive, and exhaustive method" (abstract).  
  - **Evidence pointer** Section 2.3, Section 3.1  
  - **Concern** The methods section lacks critical experimental parameters: protein concentration, DNA concentration, binding buffer composition, incubation time and temperature (only "on ice for 30 minutes" is stated), the number of replicates, and the criteria for read filtering beyond the reverse-complement check. The washing procedure is described but the number of washes and their stringency are not quantified. The PCR amplification steps (extension, indexing) are described with reagent tables but no cycle numbers or error rates are given.  
  - **Why it matters** Reproducibility is a core requirement for a methods paper. Without these details, other laboratories cannot implement KaScape, and the robustness of the results cannot be assessed.  
  - **Resolution test** Provide a complete step-by-step protocol with all buffer compositions, concentrations, incubation times, temperatures, and quality control metrics. Include a section on expected yields and failure modes.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Validation  
  - **Claim pointer** "The EMSA results are consistent with the KaScape results" (section 3.3).  
  - **Evidence pointer** Section 3.3, Figure S7  
  - **Concern** The validation is limited to 8 sequences tested by EMSA for one protein (At WRKY1N). The text states that one sequence (CGACC) had a relative intensity of 0.75 and did not bind, while the other 7 had relative intensities above 1.0 and did bind. This is a very small validation set, and the correlation between relative intensity magnitude and EMSA binding strength is not quantified. No statistical analysis is provided.  
  - **Why it matters** The claim of consistency requires a quantitative comparison across a range of affinities, not just a binary bound/unbound assessment. The method's ability to rank affinities, not just identify binders, is a key selling point.  
  - **Resolution test** Expand the validation to include at least 20-30 sequences spanning a wide range of relative intensities, and provide a quantitative correlation (e.g., Spearman or Pearson) between KaScape relative intensity and EMSA-derived binding strength (e.g., fraction bound or Kd).

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Scientific importance  
  - **Claim pointer** "KaScape can identify not only high-affinity binding sequences but also low-affinity binding sequences that are specific to the transcription factors being studied" (section 3.3).  
  - **Evidence pointer** Section 3.3, Figure 5, Figure S9  
  - **Concern** The application to 12 WRKY proteins is presented as a demonstration, but the biological insights are limited. The finding that all proteins bind a GAC core is not novel, as this was already known for WRKY proteins. The claim about non-canonical motifs is based on a single example (CAACA for Th WRKY4) with a relative intensity of 1.55, which is barely above the non-specific threshold of 1.0. The functional significance of such weak binding is not discussed.  
  - **Why it matters** For a high-impact journal, the demonstration should reveal new biology or provide a resource that enables new discoveries. The current analysis does not go beyond confirming known motifs.  
  - **Resolution test** Provide a deeper analysis of the WRKY dataset, such as identifying novel motifs, comparing binding specificity across family members, or linking affinity differences to known functional divergence. Alternatively, apply KaScape to a less well-characterized TF family where the results would be more informative.

  - **Concern ID** R1-M5  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Technical soundness  
  - **Claim pointer** "The results of the correlation coefficient analysis suggest that the KaScape experiments conducted for random base lengths of 5, 6, and 7 are highly consistent" (section 3.3).  
  - **Evidence pointer** Section 3.3, Figure S6  
  - **Concern** The correlation coefficients between k-mer and (k+1)-mer derived landscapes are reported as 0.292, 0.865, and 0.74 for n=4 vs 5, 5 vs 6, and 6 vs 7, respectively. The n=4 vs 5 correlation is low, yet the text claims high consistency. The authors do not explain this discrepancy or discuss the expected correlation given the different sequence lengths.  
  - **Why it matters** The consistency across different random lengths is used to support the robustness of the method. A low correlation for the n=4 vs 5 comparison undermines this claim and suggests potential length-dependent artifacts.  
  - **Resolution test** Provide a detailed explanation for the low n=4 vs 5 correlation, including possible sources of bias (e.g., library complexity, sequencing depth, or binding site length preferences). Re-analyze the data with appropriate statistical tests and discuss the implications.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Readability  
  - **Affected element** Section 2.3.5  
  - **Evidence pointer** Section 2.3.5  
  - **Issue** The equations for calculating proportions and relative intensity are referenced but not shown in the text. The sentence "Then the proportion of the sequence S i in the random dsDNA pool was calculated as ; whereas, the proportion of the sequence S i in the bound dsDNAs was calculated as . Finally, the relative intensity which represents the relative affinity of the sequence S i among all possible DNA sequences was calculated as ." contains empty placeholders.  
  - **Required correction** Include the actual mathematical formulas for all calculations, with clear definitions of each variable.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Section 3.1  
  - **Evidence pointer** Section 3.1  
  - **Issue** The sentence "we found that one time, two times, and three times of washing in KaScape did not significantly change the results (Fig. S2 b)" is vague. It is unclear what "significantly" means statistically and whether this was tested for all proteins or just one.  
  - **Required correction** Provide statistical details (e.g., p-values, effect sizes) and specify the conditions under which washing had no effect.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Section 2.2  
  - **Evidence pointer** Section 2.2  
  - **Issue** The protein purification description is brief and references a previous report. The text does not state the purity of the proteins, the yield, or how protein concentration was determined.  
  - **Required correction** Add details on protein purity assessment (e.g., SDS-PAGE), concentration measurement method, and storage conditions.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Data presentation  
  - **Affected element** Section 3.3, Figure 5  
  - **Evidence pointer** Section 3.3, Figure 5  
  - **Issue** The text states that "most correlation coefficients of relative intensity between each At WRKY family protein pair are more than 0.9" but does not provide the full correlation matrix or the range of values.  
  - **Required correction** Include the full correlation matrix as a supplementary table or figure, with confidence intervals.

  - **Concern ID** R1-m5  
  - **Severity** Minor  
  - **Axis** Language  
  - **Affected element** Throughout  
  - **Evidence pointer** Abstract, Section 3.1  
  - **Issue** Several sentences are grammatically awkward or unclear, e.g., "It is difficult to exhaustively screen all possible DNA binding sequences for a given transcription factor" (abstract) and "we developed a method, named KaScape, which determined the relative binding affinities" (Section 3.1).  
  - **Required correction** Revise for clarity and grammatical correctness. Consider professional language editing.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (quantitative interpretation of relative intensity), R1-M2 (incomplete methods), R1-M3 (insufficient validation)

- **Assessment against Nature-style criteria**  
  - **Originality** The concept of exhaustive binding affinity measurement using randomized libraries is not entirely new (SELEX-seq and similar approaches exist), but the specific design of KaScape with adjustable random lengths and the normalization strategy has some novelty. However, the originality is incremental rather than transformative.  
  - **Scientific importance** The method could be useful for the TF community, but the demonstrated biological insights are limited. The paper does not yet show that KaScape reveals new biology or enables discoveries that other methods cannot.  
  - **Interdisciplinary readership** The method combines molecular biology, sequencing, and bioinformatics, which could appeal to a broad audience. However, the current presentation is too specialized and lacks the broader context needed for a general journal.  
  - **Technical soundness** The core principle is sound, but the lack of quantitative validation, incomplete methods, and unclear statistical treatment undermine confidence. The low correlation for n=4 vs 5 is a specific concern.  
  - **Readability for nonspecialists** The abstract is accessible, but the methods and results sections are dense and assume significant prior knowledge. The empty equation placeholders and informal language further reduce readability.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the technical concerns, particularly the lack of quantitative validation and incomplete methods, must be addressed before the claims can be accepted. A revised version with expanded validation, complete methods, and clearer biological insights could be reconsidered.

## Risk / unsupported claims
- The claim that KaScape "quantitatively characterize[s]" binding affinity is unsupported without a demonstrated relationship to thermodynamic constants.
- The claim of "exhaustive" characterization is not fully supported, as the completeness of the random library and sequencing coverage is not demonstrated.
- The claim that "all At WRKY proteins bind to the core sequence GAC with similar profiles" is based on visual inspection of figures and correlation coefficients, but no statistical test for profile similarity is provided.
- The claim that KaScape can identify "non-canonical" motifs is based on a single example with marginal enrichment.
- The statement that "KaScape method robustly characterized the binding landscape" is not supported by a formal robustness analysis (e.g., replicate variability, batch effects).