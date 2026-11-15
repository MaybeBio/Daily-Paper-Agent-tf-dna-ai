## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, appendices, and supplementary figure references.
- **Assessment boundary** Scientific validity, technical soundness, and conceptual contribution of the claims as presented. The review does not assess the suitability of the target journal or the novelty relative to unpublished work.
- **Shared manuscript claim summary** The manuscript argues that single-locus information (SI) encoding in transcription factor binding motifs is evolutionarily favored over correlation-based (multi-locus) encoding because SI is more robust to mutation and enhances the navigability of the affinity landscape. The authors support this with analytical derivations, numerical simulations, evolutionary simulations, and an analysis of the genetic code, concluding that SI preference may be a general property of biological codes.
- **Visible evidence base** Abstract, full main text (Sections 1-4), Appendices A-E, figure legends (Figures 1-7), and references to supplementary figures (S1-S11). Code availability statement provided.
- **Missing materials affecting confidence** Supplementary figures (S1-S11) and any supplementary text are not provided. The manuscript references a companion paper (Mascolo et al. 2026) for the diPWM model, which is not available. The GitHub repository is not reviewed.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental and timely question in molecular evolution and regulatory genomics: why do transcription factor binding motifs predominantly use independent position contributions rather than correlations? The authors provide a rigorous information-theoretic framework, supported by analytical results, numerical experiments, and evolutionary simulations. The finding that SI is more robust to mutation and that this property drives its evolution is compelling and well-argued. The extension to the genetic code is a valuable and thought-provoking generalization. The work is technically sound in its core derivations and simulations, though several aspects require clarification and additional validation. The manuscript is well-written and accessible to a broad audience, though some sections are dense. Overall, this is a strong contribution with the potential for high impact, but the case would be strengthened by addressing the concerns below.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, molecular evolution, information theory applied to biology, and biophysics of protein-DNA interactions. The work is also relevant to those studying the evolution of genetic codes and the general principles of information encoding in biological sequences. The conceptual bridge between TF motifs and the genetic code will appeal to a broad interdisciplinary audience.
- **Major strengths**
  1. The manuscript provides a clear and formal information-theoretic decomposition of total information into SI and correlation terms, which is a valuable conceptual contribution.
  2. The analytical derivation of asymptotic information loss rates for SI and MI encodings is elegant and provides a solid theoretical foundation.
  3. The use of multiple complementary approaches (analytical, numerical, evolutionary simulation, landscape analysis) strengthens the conclusions.
  4. The extension to the genetic code is a novel and insightful generalization that significantly broadens the scope and impact of the work.
  5. The manuscript is generally well-structured and clearly written, with helpful figures.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of the evolutionary simulation
  - **Claim pointer** The manuscript claims that "SI strategists systematically outcompeted MI strategists and reached fixation in the vast majority of the simulations" (Section 2.3), and that this demonstrates that SI is evolutionarily favored.
  - **Evidence pointer** Section 2.3, Figure 4A, Methods Section 4.3
  - **Concern** The evolutionary simulation methodology is described only briefly. The fitness function is stated to be based on AUPRC, but the details of how AUPRC is calculated from the diPWM model, how the genome is structured, how mutations are applied (rate, type), and how selection strength is set are not fully specified. The manuscript states that the mutation rate was "set well above biologically realistic values for computational tractability," but the specific value and its potential impact on the qualitative results are not discussed. Furthermore, the initial conditions for the competition experiments (e.g., how the SI and MI strategists are generated, their initial frequencies) are not described. Without these details, it is difficult to assess whether the simulation results are robust to parameter choices and whether the conclusion of SI outcompeting MI is a general result or an artifact of specific simulation settings.
  - **Why it matters** The evolutionary simulation is a central piece of evidence for the manuscript's main claim. If the simulation methodology is not transparent or the results are sensitive to arbitrary parameter choices, the conclusion that SI is evolutionarily favored is not firmly established.
  - **Resolution test** Provide a complete description of the simulation parameters (mutation rate, selection coefficient, population size, genome length, number of generations) and the initial conditions. Perform and report a sensitivity analysis showing that the qualitative outcome (SI fixation) is robust to variations in these parameters. If the outcome is not robust, discuss the implications for the conclusions.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validity of the genetic code analysis
  - **Claim pointer** The manuscript claims that the standard genetic code has a high percent SI (97.39%) and that this is consistent with the proposed evolutionary advantage of SI encoding (Section 2.5).
  - **Evidence pointer** Section 2.5, Figure 6, Methods Section 4.1
  - **Concern** The analysis of the genetic code is presented as a key generalization, but the methodology is not fully clear. The manuscript states that the genetic code is treated as a set of 21 motifs (20 amino acids and stop), but it is not specified how the "motif" for each amino acid is defined. Is it the set of all codons encoding that amino acid? If so, the length L is 3, and the SI and MI are computed over the three positions of the codon. However, the manuscript does not specify the null distribution used for the genetic code analysis. The main text uses a uniform null distribution for TF motifs, but for the genetic code, the null distribution should arguably reflect the underlying mutational process (e.g., a uniform distribution over all 64 codons, or a distribution reflecting transition/transversion biases). The choice of null distribution will directly affect the computed SI and MI values. Furthermore, the comparison to randomized codes is described, but the method for generating these randomized codes (preserving degeneracy structure) is not detailed. The claim that the genetic code is "consistent" with the proposed theory requires a more rigorous statistical comparison.
  - **Why it matters** The genetic code analysis is a major part of the manuscript's claim of generality. If the methodology is not transparent or the null distribution is inappropriate, the conclusion that the genetic code shows a preference for SI is not well-supported.
  - **Resolution test** Clearly define the motifs for each amino acid and the null distribution used. Justify the choice of null distribution. Provide a detailed description of the randomization procedure for generating the null distribution of codes. Report the distribution of percent SI for the randomized codes and the statistical significance of the observed value for the standard genetic code.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the analytical results
  - **Claim pointer** The manuscript derives analytical information loss rates for SI and MI encodings for L=2 motifs and shows that SI is more robust (Section 2.1). It then generalizes this to longer motifs numerically (Section 2.2).
  - **Evidence pointer** Section 2.1, Section 2.2, Appendix B
  - **Concern** The analytical results are derived for the minimal case of L=2. The numerical results for longer motifs (Figure S4) are mentioned but not shown in the main text. The manuscript would be strengthened by a more detailed presentation of the numerical results for longer motifs, including the range of parameters tested (e.g., motif length, information density, distribution of SI across positions). It is not clear whether the qualitative advantage of SI over MI holds for all motif lengths and information densities, or whether there are regimes where MI is more robust. The claim that "SI is intrinsically more robust to mutation" is presented as a general property, but the evidence for this beyond L=2 is not fully presented.
  - **Why it matters** The generality of the main claim depends on the results extending beyond the minimal L=2 case. If the advantage of SI is not universal, the conclusions need to be qualified.
  - **Resolution test** Present the numerical results for longer motifs in the main text or a main-text figure. Show the information loss rates for SI and MI as a function of motif length and information density. Discuss any regimes where the relative robustness of SI and MI changes.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of the relationship between information loss and fitness
  - **Affected element** Section 2.2, Figure 3B
  - **Evidence pointer** Section 2.2
  - **Issue** The manuscript equates information loss with a decrease in AUPRC, which is used as a proxy for fitness. However, the relationship between information content and AUPRC is not explicitly derived or discussed. It is plausible that a small information loss does not immediately translate into a significant AUPRC decrease, and that the relationship is nonlinear.
  - **Required correction** Briefly discuss the relationship between information loss and AUPRC, and justify the use of AUPRC as a fitness proxy. If the relationship is nonlinear, discuss the implications for the evolutionary dynamics.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Presentation of the phase diagram
  - **Affected element** Section 2.3, Figure 4B
  - **Evidence pointer** Section 2.3
  - **Issue** The phase diagram in Figure 4B is described as showing a "steady-state attractor at ~75% SI". However, the axes and the meaning of the vector field are not fully explained in the main text. It is unclear what the x and y axes represent and how the vectors are computed.
  - **Required correction** Provide a clear description of the axes and the vector field in the figure legend and in the main text. Explain how the vectors are estimated and what the attractor represents.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Discussion of alternative explanations
  - **Affected element** Section 3 (Discussion)
  - **Evidence pointer** Section 3
  - **Issue** The discussion focuses on the mutational robustness advantage of SI. However, other potential explanations for the prevalence of SI in TF motifs, such as the simplicity of the regulatory code for evolutionary innovation or the biophysical constraints of protein-DNA recognition, are not discussed in depth.
  - **Required correction** Add a brief discussion of alternative or complementary explanations for the observed prevalence of SI, and how the proposed framework relates to them.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Accessibility of the analytical derivations
  - **Affected element** Appendix B
  - **Evidence pointer** Appendix B
  - **Issue** The analytical derivations in Appendix B are dense and may be difficult for a non-specialist reader to follow. The main text refers to these derivations but does not provide an intuitive explanation of why SI is more robust than MI.
  - **Required correction** Add a short intuitive explanation in the main text of why SI encoding is more robust to mutation than MI encoding, perhaps using a simple example.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking concerns. The evolutionary simulation methodology must be fully described and shown to be robust, and the genetic code analysis must be rigorously defined and statistically validated. R1-M3 is a major concern that should be addressed to strengthen the generality of the claims.
- **Assessment against Nature-style criteria**
  - **Originality** High. The manuscript presents a novel information-theoretic framework to address a long-standing question in regulatory genomics. The connection between SI encoding, mutational robustness, and the structure of the genetic code is original and insightful.
  - **Scientific importance** High. The question of why TF motifs are predominantly additive is fundamental to our understanding of gene regulation and molecular evolution. The proposed framework has the potential to unify observations across different biological codes.
  - **Interdisciplinary readership** High. The work bridges information theory, evolutionary biology, and genomics, and will be of interest to researchers in all three fields. The conceptual message is broadly accessible.
  - **Technical soundness** The core analytical derivations and numerical experiments appear sound. However, the technical soundness of the evolutionary simulations and the genetic code analysis is not fully established due to missing methodological details (R1-M1, R1-M2). The landscape analysis is well-described.
  - **Readability for nonspecialists** The manuscript is generally well-written and the main argument is clear. However, some sections, particularly the analytical derivations and the description of the phase diagram, are dense and would benefit from additional explanatory text for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core conceptual contribution is strong and the analytical results are compelling. However, the manuscript's main claims regarding evolutionary outcomes and the generality to the genetic code are not fully established from the provided evidence due to the methodological gaps identified in R1-M1 and R1-M2. Addressing these concerns is essential before the case is fully made.

## Risk / unsupported claims
- The claim that SI strategists "systematically outcompeted" MI strategists is not fully supported without a complete description of the simulation methodology and a sensitivity analysis (R1-M1).
- The claim that the standard genetic code's high percent SI is "consistent" with the proposed theory is not rigorously supported without a clear definition of the null distribution and a statistical comparison to randomized codes (R1-M2).
- The claim that SI is "intrinsically more robust to mutation" is well-supported for L=2 analytically, but the generalization to longer motifs relies on numerical results that are not fully presented in the main text (R1-M3).
- The relationship between information loss and AUPRC (fitness) is assumed but not explicitly demonstrated (R1-m1).