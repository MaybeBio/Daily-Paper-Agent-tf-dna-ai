## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and conclusions as presented in the provided manuscript
- **Shared manuscript claim summary** The authors use three deep learning-based structure prediction tools (AlphaFold 3, RoseTTAFold2NA, Chai-1) and one docking platform (HADDOCK) to model the interaction between the Type IV minor pilin ComP and its cognate DNA uptake sequences (DUS) in seven Neisseriaceae species. They report six distinct binding modes, of which two (Epsilon and Gamma) were robustly predicted across platforms. The authors assess platform performance, discuss DUS specificity, and propose that the two robust modes may represent initial DNA binding states.
- **Visible evidence base** Full manuscript text including abstract, methods, results, discussion, and supporting information references
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S7 Figs, S1-S2 Tables, S1-S3 Code Output) are referenced but not provided; experimental validation data are not included; structural coordinates of predicted models are not provided

## Reviewer
- **Overall assessment** This manuscript presents a systematic in silico comparison of three deep learning-based structure prediction platforms and one docking tool for modeling the ComP-DUS DNA interaction. The work addresses a relevant biological question regarding the DNA binding mode of an important competence protein. The systematic approach across multiple platforms is commendable, and the identification of two robust binding modes (Epsilon and Gamma) is potentially interesting. However, the manuscript has significant limitations: the lack of experimental validation, the absence of key supplementary data, and the somewhat speculative interpretation of platform-specific differences weaken the overall impact. The claim that two distinct binding modes exist is supported by the modeling data, but the biological significance of these modes remains unclear.
- **Who would be interested in the results, and why** Researchers studying natural transformation in Neisseriaceae, structural biologists interested in protein-DNA interactions, and computational biologists evaluating deep learning-based structure prediction tools for nucleic acid complexes. The comparative platform assessment may also interest developers and users of AlphaFold 3, RoseTTAFold2NA, and Chai-1.
- **Major strengths** 1) Systematic comparison of three state-of-the-art deep learning platforms plus docking for a biologically relevant protein-DNA complex. 2) The identification of two robustly predicted binding modes across multiple platforms provides a useful hypothesis for future experimental work. 3) The authors acknowledge limitations of confidence metrics and platform-specific biases. 4) The inclusion of scrambled DUS controls to assess DUS specificity is a thoughtful experimental design element.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The lack of experimental validation for the predicted binding modes; the absence of key supplementary data (figures, tables, code outputs) that are referenced throughout; the inability to assess the quality of structural models without coordinates or validation metrics
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Currently not established from the provided evidence

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that two binding modes, Epsilon and Gamma, represent robust and inherent DNA binding properties of ComP, and suggest these may be biologically relevant.
- **Evidence pointer** Discussion section, Summary of conclusions
- **Concern** The manuscript relies entirely on computational predictions without any experimental validation. While the authors acknowledge this limitation, the central claim that Epsilon and Gamma represent biologically meaningful binding modes is not supported by direct evidence. Previous experimental work (Berry et al., Hughes-Games) is cited for docking support, but no new experimental data are presented. The predicted binding modes could be artifacts of the prediction algorithms or represent non-physiological states.
- **Why it matters** Without experimental validation (e.g., mutagenesis, crosslinking, NMR, or biophysical binding assays), the biological significance of the predicted binding modes remains speculative. The manuscript's main contribution is computational, but the conclusions extend beyond what the data can support.
- **Resolution test** Provide experimental validation of at least one predicted binding mode, or substantially temper the conclusions to reflect the purely computational nature of the findings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability
- **Claim pointer** The authors reference multiple supplementary figures, tables, and code outputs to support their analyses and conclusions.
- **Evidence pointer** Methods section, Results section, Supporting information
- **Concern** The manuscript references S1-S7 Figs, S1-S2 Tables, and S1-S3 Code Output, but none of these are provided in the submitted material. This makes it impossible to verify the analyses, assess the quality of structural models, or evaluate the statistical tests performed. Key data such as sequence alignments, PAE plots, and code outputs are essential for evaluating the validity of the claims.
- **Why it matters** The inability to access supplementary data prevents proper peer review and reproducibility assessment. The manuscript's conclusions depend heavily on these data, and without them, the evidence base is incomplete.
- **Resolution test** Provide all referenced supplementary materials, including figures, tables, and code outputs, for review.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model quality assessment
- **Claim pointer** The authors assess the quality of predicted models using PAE, pLDDT, and DockQ scores, and compare platform performance.
- **Evidence pointer** Results section, Figures 4-5
- **Concern** The manuscript does not provide structural validation metrics beyond the confidence scores reported by the prediction tools themselves. No comparison to experimental structures (where available) is presented, and the DockQ analysis is limited to cross-platform comparisons rather than comparison to known structures. The authors note that RF2NA models lack disulfide bridges, which is a significant structural defect, yet they still include these models in their binding mode analysis.
- **Why it matters** Confidence scores from prediction tools do not guarantee structural accuracy. The inclusion of models with known structural defects (missing disulfide bridges) in the binding mode analysis could compromise the conclusions about which binding modes are robust.
- **Resolution test** Provide additional validation of model quality, such as comparison to experimental structures where available, or clearly separate analysis of models with known structural defects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of DUS specificity
- **Claim pointer** The authors use scrambled DUS controls to assess DUS specificity and interpret differences in binding mode propensities between native and scrambled DUS.
- **Evidence pointer** Results section, Figure 6, Table 4
- **Concern** The interpretation of the scrambled DUS experiments is somewhat circular. The authors argue that since Epsilon and Gamma are both predicted with scrambled DUS, the modes may represent initial non-specific contacts. However, this interpretation assumes that the prediction tools can distinguish specific from non-specific binding, which is not established. The finding that AF3 predicts better models with native DUS for some ComPs but not others is interesting but not mechanistically explained.
- **Why it matters** The conclusions about DUS specificity and the potential role of the two binding modes in specific versus non-specific DNA binding are central to the manuscript's significance. Without a clearer mechanistic framework, these interpretations remain speculative.
- **Resolution test** Provide a more rigorous framework for interpreting scrambled DUS results, or temper conclusions about DUS specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, Modeling of ComPnats
- **Evidence pointer** Methods section
- **Issue** The description of the number of models generated is confusing. The text states "A minimum of 20 native AF3 replicates (33 for B. dennat and 37 for N. subnat) and 100 native runs with different seeds in RF2NA and Chai-1 were performed for each ComPnat," but later states "This generated a grand total of 3500 mmCIF/PDB models in Chai-1 (500 per ComPnat), 850 models in AF3, with more than 100 models per ComPnat, and 700 models in RF2NA, with 100 models per ComPnat." The relationship between the initial replicates and the final model counts is unclear.
- **Required correction** Clarify the relationship between the number of runs and the number of models generated, and ensure the numbers are consistent throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout manuscript
- **Issue** The term "robustly modeled" is used frequently but not precisely defined. Does it mean consistently predicted across platforms, high confidence scores, or both? The criteria for calling a binding mode "robust" should be explicitly stated.
- **Required correction** Define the criteria for "robust" modeling early in the manuscript and apply consistently.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, AF3 modeling quality
- **Evidence pointer** Figure 6, S3 Code Output
- **Issue** The Wilcoxon rank sum tests are mentioned, but the effect sizes and exact p-values are not reported in the text. The practical significance of the statistical differences is unclear.
- **Required correction** Report effect sizes and exact p-values, and discuss the practical significance of the findings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 3
- **Evidence pointer** Figure 3
- **Issue** The description of the structural overlays in Figure 3 is limited. It is unclear how the reader should interpret the overlays and what specific structural features distinguish the different binding modes.
- **Required correction** Provide more detailed figure legends and consider highlighting key structural features that distinguish the binding modes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of previous docking studies (Berry et al., Hughes-Games) is brief and does not critically evaluate how the current results compare to or extend these earlier findings.
- **Required correction** Expand the comparison to previous computational and experimental studies of ComP-DNA interactions.

## Risk / unsupported claims
- The claim that Epsilon and Gamma represent "robust and inherent DNA binding properties" of ComP is not supported by experimental evidence and should be framed as a computational prediction.
- The interpretation that the two binding modes may explain DUS-specific versus DUS-independent transformation is speculative and not directly supported by the data.
- The statement that "all tested proteins likely were functionally conserved as DUS specific receptors" extends beyond what structural prediction alone can establish.
- The claim that Chai-1's ability to model DNA structural changes "sets it apart" from other platforms is based on limited observations and requires more systematic evaluation.
- The assertion that the Epsilon mode has "previous docking support" from Berry et al. and Hughes-Games is based on the authors' interpretation of published figures and may not reflect the original authors' conclusions.