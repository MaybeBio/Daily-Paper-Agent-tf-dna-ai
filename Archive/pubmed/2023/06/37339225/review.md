## Review setup
- **Input scope** Full manuscript text (main text, methods summary, significance statement; supplementary material referenced but not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and generalizability as presented in the provided text; no assessment of supplementary figures, tables, or detailed methods beyond what is described
- **Shared manuscript claim summary** The authors propose that direct transfer of polynucleotides between nucleic acid-binding proteins (NBPs) is a general phenomenon, demonstrated through fluorescence polarization-based competitive dissociation (FPCD) experiments on four diverse NBP–ligand systems, supported by single-molecule TIRF microscopy for TREX1, and mechanistically linked to dynamic protein–polynucleotide interfaces. They further propose a hand-off proficiency (HOP) score to quantify direct transfer efficiency and discuss biological implications for target-site search.
- **Visible evidence base** Main text figures (Figs. 1–5), Table 1, and descriptions of FPCD, equilibrium binding, stoichiometry, and single-molecule experiments; references to SI Appendix for theoretical background, supplementary figures (S1–S4), and equations
- **Missing materials affecting confidence** SI Appendix (theoretical background, equations, supplementary figures, detailed methods), raw data files, and the specific regression models used for FPCD analysis; these are essential for fully evaluating the kinetic modeling and statistical comparisons

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially significant hypothesis: that direct transfer of polynucleotides between nucleic acid-binding proteins is a widespread phenomenon, not limited to the few oligomeric systems previously studied. The experimental approach is thoughtful, combining ensemble FPCD kinetics with single-molecule validation, and the inclusion of a non-NBP control (streptavidin–biotin) strengthens the argument. The correlation between dissociation and direct transfer rate constants across multiple systems is striking and provides a unifying framework. However, the strength of the conclusions depends heavily on the kinetic modeling and the interpretation of FPCD data, and the absence of the SI Appendix limits full assessment. The claim of generality, while intriguing, is based on a small number of systems, and the authors appropriately acknowledge this limitation. The biological implications, while speculative, are framed cautiously. Overall, this is a well-written and thought-provoking study, but the case for a universal mechanism would be strengthened by additional systems and a more detailed exposition of the modeling assumptions.
- **Who would be interested in the results, and why** Researchers in nucleic acid biochemistry, protein–nucleic acid interactions, biophysics of target-site search, and chromatin biology. The findings have implications for understanding how proteins find their targets in crowded cellular environments, and for the design of experiments measuring protein–nucleic acid binding kinetics. The proposed HOP score could be a useful metric for the community.
- **Major strengths**
  1. The hypothesis is clearly stated and tested across a diverse set of NBP–ligand pairs, including RNA and DNA binders, sequence-specific and non-specific interactions, and varying binding site sizes.
  2. The combination of ensemble FPCD kinetics with single-molecule TIRF microscopy provides orthogonal evidence for direct transfer, addressing potential methodological artifacts.
  3. The inclusion of a non-NBP control (streptavidin–biotin) that shows classic competition is a strong negative control.
  4. The correlation between k−1 and kθ across multiple systems (Fig. 5) is a powerful and novel observation that suggests a common underlying mechanism.
  5. The discussion of methodological implications for measuring dissociation rates is valuable and practically relevant.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of kinetic modeling
  - **Claim pointer** The authors claim that FPCD experiments can distinguish direct transfer from classic competition and that the derived rate constants (k−1, kθ) are accurate.
  - **Evidence pointer** Fig. 2, Table 1, SI Appendix (Theoretical Background, Table S1)
  - **Concern** The distinction between direct transfer and classic competition relies on the shape of the koffobs versus competitor concentration curve. The authors state that they used custom regression models and BIC to select the superior model, but the details of these models, the assumptions made (e.g., regarding the partial association state), and the sensitivity of the fits to experimental noise are not presented in the main text. Without this information, it is difficult to assess whether the observed "direct transfer" kinetics could be an artifact of the fitting procedure or of non-specific effects not fully controlled for.
  - **Why it matters** The central claim of the paper—that direct transfer is a general property of NBPs—rests entirely on the correct interpretation of the FPCD data. If the kinetic modeling is flawed or the data are ambiguous, the conclusion would be unsupported.
  - **Resolution test** The authors must provide the full theoretical derivation, the explicit regression models, and a demonstration of the robustness of the model selection (e.g., via simulations or error analysis) in the SI Appendix. They should also show that the direct transfer model fits the data significantly better than alternative models (e.g., a model with two independent binding sites or a conformational change).
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability of the claim
  - **Claim pointer** The authors state that "direct transfer might be widespread among NBPs" and that their findings "suggest that direct transfer could be a common capability among NBPs."
  - **Evidence pointer** Fig. 2, Table 1
  - **Concern** The claim of generality is based on only four NBP–ligand systems, all of which are relatively simple, monomeric or dimeric proteins binding to short polynucleotides. While the authors acknowledge this limitation, the title and significance statement imply a broader conclusion. The lack of testing on more complex systems, such as multi-domain proteins, proteins with multiple binding sites, or proteins that bind structured nucleic acids (e.g., ribosomes, spliceosomes), weakens the generality claim.
  - **Why it matters** The title and significance statement are the most visible parts of the paper. If the claim of generality is overstated, it could mislead readers and overstate the novelty of the finding.
  - **Resolution test** The authors should either (a) temper the language in the title and significance statement to reflect the preliminary nature of the generality claim, or (b) include at least one or two additional, more complex NBP systems to demonstrate broader applicability.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological relevance
  - **Claim pointer** The authors speculate that direct transfer could reduce the dimensionality of target-site search and explain why many DNA-binding proteins also bind RNA.
  - **Evidence pointer** Discussion section
  - **Concern** The biological implications are speculative and not directly tested. While the authors are appropriately cautious, the leap from in vitro kinetics to in vivo relevance is large. The concentrations at which direct transfer becomes significant (low micromolar) may or may not be relevant in the cellular context, and the authors do not provide any quantitative estimates of local concentrations or crowding effects.
  - **Why it matters** The significance of the paper is enhanced if the findings have clear biological implications. Without any experimental or theoretical support for the in vivo relevance, the discussion remains speculative.
  - **Resolution test** The authors should either (a) provide a more quantitative framework for when direct transfer would be biologically significant (e.g., using known cellular concentrations of proteins and nucleic acids), or (b) clearly state that the biological implications are purely speculative and require further testing.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Fig. 2
  - **Evidence pointer** Fig. 2
  - **Issue** The figure legend is not provided in the text, and it is unclear how the data are presented (e.g., are the curves fits to the direct transfer model or just guides to the eye?).
  - **Required correction** Provide a complete figure legend that clearly describes the data points, error bars, and the lines shown.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Materials and Methods
  - **Evidence pointer** Materials and Methods section
  - **Issue** The description of the FPCD experiments is brief. The concentrations of protein, labeled ligand, and competitor used, the buffer conditions, and the time course of the experiments are not specified in the main text.
  - **Required correction** Provide these details in the main text or refer explicitly to the SI Appendix for the complete experimental protocol.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical analysis
  - **Affected element** Fig. 5
  - **Evidence pointer** Fig. 5
  - **Issue** The correlation between k−1 and kθ is reported with an R2 value, but no confidence intervals or statistical significance are given.
  - **Required correction** Report the p-value and, if possible, confidence intervals for the correlation.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** HOP score
  - **Evidence pointer** Discussion section
  - **Issue** The term "hand-off proficiency (HOP) score" is introduced, but its precise definition and calculation are not provided in the main text.
  - **Required correction** Define the HOP score explicitly, either in the main text or by referencing the SI Appendix equation.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (kinetic modeling details) is the primary technical concern. Without the full model and its validation, the central claim is not fully established.
  - The lack of detail on the single-molecule data analysis (e.g., how binding events were identified, how koffobs was calculated from residence times) is also a concern, though less critical given the ensemble data.
- **Assessment against Nature-style criteria**
  - **Originality** High. The idea that direct transfer is a general property of NBPs, rather than a special case, is novel and challenges the classic view of protein–ligand complex lifetimes as intrinsic properties.
  - **Scientific importance** Potentially high. If confirmed, this work could change how researchers think about protein–nucleic acid interactions and target-site search. The proposed HOP score could be a useful quantitative tool.
  - **Interdisciplinary readership** Moderate to high. The findings are relevant to biophysics, biochemistry, molecular biology, and chromatin biology. The writing is accessible to a broad scientific audience, though the kinetic details may be challenging for non-specialists.
  - **Technical soundness** The experimental design is sound, and the use of orthogonal methods is a strength. However, the lack of detail on the kinetic modeling and the small number of systems tested are weaknesses that need to be addressed.
  - **Readability for nonspecialists** The manuscript is generally well-written and the significance statement is clear. The main text is accessible, but the theoretical background and kinetic equations are relegated to the SI Appendix, which is appropriate.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the data are suggestive, but the case for generality is not fully established from the provided evidence. The authors must provide the full kinetic modeling details and ideally test additional NBP systems to strengthen the claim.

## Risk / unsupported claims
- The claim that "direct transfer might be widespread among NBPs" is not fully supported by the data, as only four systems were tested.
- The biological implications (e.g., reduced dimensionality of target-site search, RNA–DNA direct transfer) are speculative and not directly tested.
- The HOP score is proposed as a metric, but its utility and validity are not demonstrated beyond the current dataset.
- The statement that "direct transfer significantly affects our NBPs only at low-micromolar or higher effective concentrations" is based on the derived rate constants and the specific model, which is not fully described.