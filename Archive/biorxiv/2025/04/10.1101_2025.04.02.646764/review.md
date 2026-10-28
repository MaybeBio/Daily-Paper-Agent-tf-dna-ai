## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence consistency, and alignment with stated conclusions; no assessment of editorial fit or publication policy
- **Shared manuscript claim summary** The authors use extensive classical MD simulations (73 µs total) to characterize the binding modes of the SIRT6 C-terminal domain (CTD) to a nucleosome core particle (NCP), and report that specific CTD binding modes at the DNA entry/exit promote DNA unwrapping and increase H3K27 accessibility to the SIRT6 active site, suggesting a functional role for the CTD in H3K27 deacetylation.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (systems setup, MD protocols, analysis descriptors), Results and Discussion (two subsections), Conclusions, Supporting Information references, figure citations (Figures 1-3, Table S1, Figure S1)
- **Missing materials affecting confidence** Figures and tables themselves (Figures 1-3, Table S1, Figure S1) are not provided; no trajectory analysis details beyond descriptor definitions; no convergence metrics for the 6 µs replicates; no error estimates or statistical analysis for binding free energies; no control simulation details beyond reference to prior work; no force field validation or sensitivity analysis

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question regarding the role of the SIRT6 CTD in nucleosome binding and histone deacetylation, using state-of-the-art MD simulations. The central claim that specific CTD binding modes correlate with enhanced DNA unwrapping and H3K27 accessibility is plausible and mechanistically interesting. However, the evidence as presented is incomplete. The absence of the actual figures and tables, the lack of quantitative convergence and statistical analyses, and the reliance on a single long trajectory per starting pose (with only one extended replicate) limit the robustness of the conclusions. The distinction between "promoting" unwrapping and merely "correlating with" unwrapping is not clearly established. The manuscript would benefit from clearer operational definitions of binding modes, quantitative comparisons across replicates, and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Researchers in chromatin biology, epigenetic regulation, and sirtuin enzymology would find these results relevant. The study provides a structural dynamics perspective on how a disordered protein domain (SIRT6 CTD) may modulate nucleosome stability and substrate accessibility, which is of interest to those studying chromatin remodeling, histone deacetylation mechanisms, and the development of SIRT6-targeting therapeutics. Computational biophysicists working on protein-DNA interactions and disordered protein behavior may also find the methodological approach informative.
- **Major strengths** The study addresses a genuine gap in understanding the structural role of the SIRT6 CTD, which has been refractory to experimental structural characterization. The use of multiple starting orientations (8 poses) to sample the disordered CTD conformational space is a reasonable strategy. The total simulation time (73 µs) is substantial. The connection to prior cryoEM structures and the identification of specific basic residues (R343, K346, R347, K349, K352) as potential key mediators of DNA interaction provide testable hypotheses. The observation that CTD binding modes have differential effects on DNA unwrapping is an interesting and non-obvious finding.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative convergence and statistical robustness), R1-M2 (insufficient evidence for causal claim regarding CTD promoting unwrapping), R1-M3 (incomplete reporting of methods and missing figures/tables), R1-M4 (overinterpretation of a single trajectory event as a "pre-reactive state")
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The question of SIRT6 CTD function is not new, but the specific focus on CTD binding modes and their differential effects on nucleosome dynamics is a novel angle. The use of MD to address this is not unprecedented but is applied to a system of current interest.  
  - Scientific importance: Moderate. If the claims are robust, the findings would contribute to understanding SIRT6 substrate specificity and the role of disordered domains in chromatin interactions. However, the study is purely computational and lacks experimental validation, which limits the immediate impact.  
  - Interdisciplinary readership: Limited. The manuscript is written primarily for a computational biophysics and chromatin biology audience. The level of detail in MD methodology and the lack of experimental context may reduce accessibility for a broader readership.  
  - Technical soundness: The simulation protocols are generally sound, but the analysis and reporting are incomplete. The lack of convergence metrics, statistical error estimates, and sensitivity analyses weakens the technical foundation.  
  - Readability for nonspecialists: The abstract and introduction are accessible, but the results section assumes familiarity with MD descriptors and nucleosome structural terminology. The absence of figures in the provided material makes it difficult to assess clarity.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but not sufficiently supported by the data as presented. The manuscript requires substantial revision, including the provision of missing figures and tables, quantitative convergence and statistical analyses, and a more cautious interpretation of the causal relationship between CTD binding modes and DNA unwrapping. If these concerns are addressed, the study could become a valuable contribution.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the CTD preferentially interacts with DNA at the entry/exit near the enzyme's docking site, exhibiting a variety of different binding modes" and that these modes have "contrasted effects on DNA unwrapping."
- **Evidence pointer** Results and Discussion, first subsection; Figure 2; Table S1; location not provided for specific data points
- **Concern** The manuscript does not provide quantitative convergence metrics for the 6 µs simulations. It is unclear whether the observed binding modes and unwrapping angles have converged within the simulation time. Additionally, only one replicate per starting pose is reported (with one extended to 11 µs), which is insufficient to assess run-to-run variability. The MMGBSA binding free energy estimates are reported without standard errors or confidence intervals, and the method is known to be sensitive to the choice of internal dielectric constant and entropy contributions, which are not discussed. Without these analyses, the robustness of the classification of binding modes and their effects on unwrapping cannot be evaluated.
- **Why it matters** The central conclusions depend on the ability to distinguish genuine binding preferences and their functional consequences from stochastic fluctuations in a single trajectory. If the simulations have not converged or if the results are not reproducible across replicates, the claims about preferential binding and differential effects on unwrapping are not supported.
- **Resolution test** Provide block-averaged or time-series analyses of the unwrapping angles (φ and θ) for each replicate to demonstrate convergence. Run at least 2-3 additional independent replicates for each pose (or a subset of key poses) to assess variability. Report MMGBSA values with standard deviations and discuss the sensitivity of the results to methodological choices. If convergence cannot be demonstrated, temper the claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors state that "the CTD participates to the promotion of DNA unwrapping and promotes H3K27 accessibility to SIRT6's active site, suggesting a pivotal role of this domain for H3K27 deacetylation."
- **Evidence pointer** Results and Discussion, both subsections; Figure 3; location not provided
- **Concern** The causal language ("promotes") is not justified by the data presented. The simulations show correlations between certain CTD binding modes and increased unwrapping angles, but there is no perturbation analysis (e.g., CTD deletion or mutation) within this study to demonstrate that the CTD is causally responsible for the observed unwrapping. The comparison to "control simulations lacking this domain" is mentioned, but the results of these controls are not shown in the provided material, and it is unclear whether the comparison is direct and quantitative. Furthermore, the claim that H3K27 accessibility is "promoted" rests on a single trajectory (pose 1) where the lysine approaches the active site; this is a single event and may not be representative.
- **Why it matters** The title and abstract assert a functional role for the CTD in promoting unwrapping and accessibility. If the evidence only supports a correlative relationship, the claims are overstated. This distinction is critical for the interpretation of the study's contribution to understanding SIRT6 function.
- **Resolution test** Show the control simulation data (without CTD) side-by-side with the CTD-containing simulations for the same descriptors. If possible, perform additional simulations with a truncated CTD or with mutations of the key basic residues to test causality. If such simulations are not feasible, revise the language to "correlates with" or "is associated with" and clearly state the limitation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of reporting
- **Claim pointer** The methods and results reference specific figures and tables (Figures 1-3, Table S1, Figure S1) that are not included in the provided material.
- **Evidence pointer** Materials and Methods; Results and Discussion; figure and table citations throughout
- **Concern** The manuscript cannot be fully evaluated without the figures and tables. The text refers to "Figure 2-a", "Table S1", "Figure S1", etc., but these are not available. Key quantitative data, such as the distribution of unwrapping angles, the binding free energy values, and the distance distributions for lysine accessibility, are only described qualitatively in the text. Without these data, the reader cannot assess the magnitude of the effects or the validity of the comparisons.
- **Why it matters** The claims are quantitative in nature (e.g., "φ max = 57° and θ max = 59°", "d min = 15.5 Å vs 21.2 Å"), and these numbers need to be presented in a clear, visual format to be interpretable. The absence of figures undermines the ability to verify the results.
- **Resolution test** Provide the figures and tables as part of the manuscript submission. Ensure that all data points mentioned in the text are clearly presented in the figures with appropriate labels and error bars where applicable.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that the pose 1 conformation "exhibits structural determinants that could resemble a pre-reactive state of the active site" with H3K27@NZ positioned 12.9 Å from NAD+@C15 and H133 nitrogen 3.1 Å away.
- **Evidence pointer** Results and Discussion, second subsection; Figure 3-c; location not provided
- **Concern** The interpretation of a single snapshot as a "pre-reactive state" is speculative. The distances reported are from one frame in one trajectory and do not account for the dynamic fluctuations of the disordered CTD, the histone tail, or the active site residues. The term "pre-reactive state" implies a specific functional relevance that is not supported by the data. Additionally, the simulations do not include the acetylated lysine substrate, which is the actual substrate for deacetylation, so the relevance of this conformation to the catalytic process is unclear.
- **Why it matters** This interpretation may overstate the significance of a single observation and could mislead readers into thinking that a catalytically relevant state has been captured. A more cautious interpretation would acknowledge the limitations of the model system.
- **Resolution test** Either provide additional evidence (e.g., multiple independent observations of this conformation, or free energy calculations showing a stable basin) or revise the language to describe the conformation as "a possible approach geometry" without implying functional relevance. Clearly state that the simulations lack the acetylated substrate and that further studies are needed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract begins with a general statement about sirtuins that is not specific to the study. This is acceptable for context, but the abstract could more quickly focus on the specific question addressed.
- **Required correction** Consider condensing the introductory sentence to allow more space for the specific findings and their implications.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The term "zing finger" appears in the text (likely a typo for "zinc finger"). This appears twice in the introduction.
- **Required correction** Correct the typo to "zinc finger".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, Systems setup
- **Evidence pointer** Materials and Methods, first paragraph
- **Issue** The description of the system setup mentions that the CTD residues were taken from the AlphaFold model, but it is not specified which residues were included (the text says 286 to 355, which is 70 residues, but the CTD is described as 83 amino acids). The discrepancy is not explained.
- **Required correction** Clarify the exact residue range of the CTD and whether any residues were omitted or modeled differently.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results and Discussion, first subsection
- **Evidence pointer** Results and Discussion, first subsection; Table S1
- **Issue** The binding free energy estimates are described as "more favorable" for certain poses, but no numerical values or uncertainties are given in the text.
- **Required correction** Provide the numerical values and associated errors in the text or refer explicitly to the table with a summary of the range of values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison with literature
- **Affected element** Results and Discussion, first subsection
- **Evidence pointer** Results and Discussion, first subsection, last paragraph
- **Issue** The comparison with the prior study on redox modification of histone H3 (reference 21) is brief and does not explain why the difference in unwrapping direction (in-plane vs out-of-plane) is mechanistically significant.
- **Required correction** Expand the comparison to explain the potential implications of the different unwrapping modes for SIRT6 function.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility of data
- **Affected element** Associated Content
- **Evidence pointer** Associated Content, Supporting Information
- **Issue** The trajectory files are deposited on Zenodo, but the link is provided only in the Supporting Information section. It would be helpful to also include the DOI in the main text or at least in the abstract for visibility.
- **Required correction** Consider adding the data availability statement to the main text.

## Risk / unsupported claims
- The claim that the CTD "promotes" DNA unwrapping and H3K27 accessibility is not supported by causal evidence; the data only show correlations in specific trajectories.
- The interpretation of a single snapshot as a "pre-reactive state" is speculative and not supported by the data.
- The claim that the CTD "preferentially interacts" with the DNA entry/exit is based on binding free energy estimates that lack statistical error analysis and may be method-dependent.
- The statement that the CTD binding modes "can facilitate the accessibility to H3K27" is based on a single trajectory (pose 1) and is not generalized across replicates.
- The comparison to control simulations without the CTD is mentioned but not shown, making the claim of a CTD-specific effect unverifiable from the provided material.