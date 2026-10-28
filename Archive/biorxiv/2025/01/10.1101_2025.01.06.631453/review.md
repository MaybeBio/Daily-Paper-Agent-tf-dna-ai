## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text; no external data or supplementary figures were available for independent verification
- **Shared manuscript claim summary** The authors propose that Lsr2, a nucleoid-associated protein from Mycobacterium tuberculosis, compacts DNA via sequence-dependent co-condensation, where Lsr2 and AT-rich DNA form phase-separated condensates that sense the average binding energy landscape rather than individual motifs, offering a novel mechanism for gene regulation
- **Visible evidence base** Abstract, Introduction, Results (narrative form), Discussion, Materials and Methods; figure references cited but figures not provided
- **Missing materials affecting confidence** All figures, supplementary figures, tables, and raw data; detailed simulation parameters and model equations; statistical analysis details; experimental replicates and controls

## Reviewer
- **Overall assessment** This manuscript addresses an important question in bacterial genome organization and presents a potentially novel mechanism for Lsr2-mediated DNA compaction. The combination of biochemical assays, single-molecule imaging, and simulations is appropriate and ambitious. However, the current version lacks sufficient experimental detail and quantitative rigor to fully support the central claims. The key finding of sequence-dependent co-condensation is intriguing but requires stronger evidence, particularly regarding the distinction between co-condensation and simple protein-DNA binding, and the claim of "sensing" the average binding energy landscape needs more direct validation. The manuscript would benefit from clearer presentation of quantitative data and statistical analyses.
- **Who would be interested in the results, and why** Researchers in bacterial chromatin biology, nucleoid-associated protein function, phase separation in biological systems, and tuberculosis pathogenesis would find these results relevant. The proposed mechanism of sequence-dependent co-condensation could have broad implications for understanding how NAPs regulate gene expression and organize genomes, potentially extending to other bacterial species and eukaryotic systems.
- **Major strengths** The study addresses a fundamental question in bacterial chromosome organization using a multi-pronged approach. The combination of biochemical, single-molecule, and computational methods is commendable. The observation that DNA lowers the concentration required for Lsr2 phase separation is interesting and potentially significant. The authors also appropriately acknowledge the distinction between individual protein-DNA binding and collective co-condensation behavior.
- **Major Concerns** The manuscript lacks quantitative details for key experiments, particularly the single-molecule imaging data. The claim of sequence-dependent co-condensation is based on limited constructs (one AT-rich, one moderate AT-content control), and the statistical power is unclear. The simulation model parameters appear to be tuned to match experimental observations, raising concerns about circularity. The physiological relevance of the observed co-condensation is not adequately discussed, and the connection to gene regulation remains speculative.
- **Minor Comments** Several methodological details are missing, including buffer conditions for phase separation assays, protein labeling efficiency effects, and DNA surface density in single-molecule experiments. The manuscript would benefit from a more thorough discussion of alternative explanations for the observed phenomena.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The concept of sequence-dependent co-condensation is novel and extends current understanding of NAP-mediated DNA compaction. Scientific importance: The work addresses a significant gap in understanding bacterial genome organization and gene regulation, with potential implications for tuberculosis pathogenesis. Interdisciplinary readership: The topic bridges microbiology, biophysics, and computational biology, making it of interest to a broad audience. Technical soundness: The experimental design is generally sound, but the current presentation lacks sufficient quantitative rigor and controls to fully validate the claims. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections could be clearer for readers outside the immediate field.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that Lsr2 forms condensates with long stretches of AT-rich DNA, providing evidence for sequence-dependent co-condensation
- **Evidence pointer** Results section, Figures 3 and 4 (figures not provided)
- **Concern** The central claim of sequence-dependent co-condensation is based on a limited number of DNA constructs: one with a 3 kb AT-rich segment, one with moderate AT-content, and λ-phage DNA. The authors report that 86.4% of condensates formed at the AT-rich region, but no statistical analysis is provided to establish significance. Additionally, the distinction between co-condensation and simple protein-DNA binding followed by local compaction is not clearly demonstrated. The authors should provide quantitative comparisons across multiple DNA sequences with varying AT-content distributions, including appropriate statistical tests, and demonstrate that the observed phenomenon is indeed co-condensation rather than protein aggregation on DNA.
- **Why it matters** The sequence-dependent co-condensation is the central novel claim of the manuscript. Without robust quantitative evidence and appropriate controls, the claim is not sufficiently supported, and the proposed mechanism cannot be distinguished from alternative explanations such as preferential binding followed by protein-mediated DNA bridging.
- **Resolution test** Provide quantitative analysis of condensate positions across multiple DNA constructs with systematically varied AT-content, including statistical comparisons. Include control experiments with proteins lacking the DNA-binding domain or with DNA sequences lacking AT-rich regions. Demonstrate that condensate formation is reversible and that DNA is encapsulated within the condensate rather than merely decorated by protein.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that both multivalent binding and intrinsically disordered regions are required for phase separation of Lsr2
- **Evidence pointer** Results section, Figure 2 (figure not provided)
- **Concern** The mutational analysis is described narratively without quantitative data. The authors state that dimerization mutants (D28A, R45A) and the ΔN1-11 mutant failed to form condensates, and that the RRR mutant required higher concentrations, but no quantitative thresholds, concentration-response curves, or statistical comparisons are provided. The truncation mutant is described as "N-terminus truncation (1-52)" in the methods, which is inconsistent with the ΔN1-11 description in the results. This discrepancy needs clarification. Furthermore, the authors do not demonstrate that the mutants are properly folded or that their DNA-binding properties are unaffected, which is essential for attributing the loss of phase separation specifically to the mutated regions.
- **Why it matters** The claim that specific structural features are required for phase separation is important for the mechanistic model. Without quantitative data and proper controls, the conclusions from the mutational analysis are not robust, and alternative explanations (e.g., protein misfolding) cannot be excluded.
- **Resolution test** Provide quantitative phase separation assays with concentration-response curves for all mutants, including proper protein folding controls (e.g., circular dichroism or size-exclusion chromatography). Clarify the truncation mutant description and ensure consistency between results and methods. Include DNA-binding assays for all mutants to demonstrate that the DNA-binding domain remains functional.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors claim that their simulation model predicts sequence-dependent co-condensation in agreement with experimental observations
- **Evidence pointer** Results section, Figure 4 (figure not provided), Materials and Methods (simulation parameters)
- **Concern** The simulation model uses interaction energies between Lsr2 and DNA that are explicitly varied from 3 to 5 kBT based on AT-content, with the authors stating this "ensured preferential binding of Lsr2 to AT-rich regions." This parameterization appears to build the observed behavior into the model, making the agreement between simulations and experiments potentially circular. The authors need to demonstrate that the model can predict experimental outcomes without prior knowledge of the results, or provide a systematic parameter exploration showing that the observed behavior is robust across a range of reasonable parameters. Additionally, the model assumes a specific relationship between AT-content and binding energy (power law) without justification from independent measurements.
- **Why it matters** The simulation-experiment dialogue is presented as a key strength of the study. If the model is parameterized to reproduce the experimental results, the agreement does not provide independent validation of the proposed mechanism.
- **Resolution test** Provide a systematic parameter sensitivity analysis, showing that the qualitative predictions (sequence-dependent co-condensation) hold across a range of interaction energies and model parameters. Justify the power-law relationship between AT-content and binding energy using independent data or theoretical arguments. Consider testing the model against additional experimental conditions not used for parameterization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance
- **Claim pointer** The authors propose that sequence-dependent co-condensation of Lsr2 with DNA explains gene regulation and genome organization in M. tuberculosis
- **Evidence pointer** Discussion section
- **Concern** The connection between the in vitro observations and in vivo function is largely speculative. The authors do not discuss how the concentrations used in their experiments (1-10 µM Lsr2) compare to physiological concentrations in M. tuberculosis. The relationship between the observed co-condensation and the previously reported punctate localization of Lsr2 in live cells is mentioned but not rigorously connected. The authors also do not address how co-condensation would lead to gene silencing, beyond stating that genes would be sequestered. The model presented in Figure 5 is not described in sufficient detail to evaluate its predictive power.
- **Why it matters** The broader significance of the work depends on the relevance of the proposed mechanism to bacterial physiology. Without addressing physiological concentrations and providing a more concrete link to gene regulation, the significance of the findings remains unclear.
- **Resolution test** Provide estimates of Lsr2 concentration in M. tuberculosis and discuss whether the observed phase separation occurs at physiologically relevant concentrations. Discuss how co-condensation would specifically lead to silencing of AT-rich genes, and consider whether the model makes testable predictions that could be validated in vivo.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Phase separation assays
- **Evidence pointer** Materials and Methods, Phase separation assay
- **Issue** The buffer conditions for phase separation assays are not fully specified. The authors mention 50 mM Tris-HCl (pH 7.5), 50 mM NaCl, 1 mM EDTA, and 5% PEG, but do not specify the PEG molecular weight or the temperature at which experiments were performed. These parameters can significantly affect phase separation behavior.
- **Required correction** Specify PEG molecular weight, temperature, and any other relevant buffer components. Provide justification for the chosen conditions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Single-molecule imaging
- **Evidence pointer** Results section, Figure 3 (figure not provided)
- **Concern** The authors describe "rapid increase in fluorescence intensity at specific locations" and "coating of Lsr2 along the length of DNA" but do not provide quantitative measures of these phenomena. The number of molecules analyzed, the reproducibility across experiments, and the criteria for identifying condensates are not stated.
- **Required correction** Provide quantitative data on the number of condensates per DNA molecule, the kinetics of condensate formation, and the fraction of DNA molecules showing condensate formation. Include information on the number of independent experiments and molecules analyzed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Condensate position analysis
- **Evidence pointer** Results section, Figure 4 (figure not provided)
- **Concern** The authors report a Pearson correlation of 0.9 between DNA sequence and Lsr2-mediated compaction, but do not provide confidence intervals or p-values. The correlation is based on averaged data, and the variability across individual molecules is not reported.
- **Required correction** Provide statistical measures of correlation with confidence intervals, and report the variability across individual molecules. Consider using bootstrap or other resampling methods to assess the robustness of the correlation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors state that their findings are "contrary to the classical view of sequence-dependent binding of individual protein molecules to DNA," but do not thoroughly discuss how their observations relate to previous studies on Lsr2-DNA interactions, particularly those using structural and force-spectroscopy methods. The relationship to H-NS, a functional ortholog, is mentioned but could be expanded.
- **Required correction** Expand the discussion to more thoroughly contextualize the findings within the existing literature on Lsr2 and related proteins, addressing both similarities and differences with previous models.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** All figures
- **Evidence pointer** Figures 1-5 (not provided)
- **Issue** The figures are not available for review, making it impossible to assess the quality of the data presentation, the clarity of the images, or the appropriateness of the controls shown.
- **Required correction** Ensure that all figures are of high quality, clearly labeled, and include appropriate controls and scale bars. Provide figure legends that are self-explanatory.

## Risk / unsupported claims
- The claim that Lsr2-DNA co-condensates "sense" the average binding energy landscape is not directly supported by the data presented; this is an interpretation that requires additional validation.
- The physiological relevance of the observed co-condensation to gene regulation in M. tuberculosis is speculative and not supported by direct in vivo evidence.
- The statement that the findings are "contrary to the classical view" of sequence-dependent binding is an overstatement, as the authors do not directly compare their results to single-molecule binding studies at the individual protein level.
- The simulation model's agreement with experiments is potentially circular due to parameterization, and the predictive power of the model is not demonstrated.
- The claim that Lsr2 phase separation occurs at "about 1 µM" in the presence of DNA is based on limited data, and the physiological relevance of this concentration is not established.