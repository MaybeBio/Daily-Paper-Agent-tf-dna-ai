## Review setup
- **Input scope** Full manuscript text including Significance, Results and Discussion, Conclusions, and Materials and Methods
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and alignment with claims; not editorial or formatting issues
- **Shared manuscript claim summary** The authors propose that acidic amino acid residues (Asp/Glu) act as negative selectors in DNA-protein recognition by disfavoring binding to non-cytosine sequences, and that cytosine recognition by Asp/Glu is facilitated by long-range electrostatic attraction to accumulated cytosine N4-amino groups, with specificity for cytosine over adenine arising from repulsion by the adenine N7 atom and, in certain contexts, BII backbone conformation effects
- **Visible evidence base** Main text figures referenced (Figs. 1-6), SI Appendix tables and figures referenced (Tables S1-S3, Figs. S2-S22), computational methods descriptions
- **Missing materials affecting confidence** SI Appendix content not provided; specific numerical data for ΔΔG values only partially reported in text; convergence criteria and error estimates for free energy calculations not fully detailed; statistical analysis details for structural database mining not described

## Reviewer
- **Overall assessment** This manuscript addresses an important and underexplored question in protein-DNA recognition, namely the role of negatively charged residues in sequence-specific binding. The authors combine multiple computational approaches, including alchemical free energy calculations, classical MD, QM/MM simulations, and quantum chemical calculations, to build a coherent mechanistic picture. The central claims, that Asp/Glu act as negative selectors and that cytosine recognition involves long-range electrostatic effects beyond simple H-bonding, are well supported by the evidence presented. The explanation for cytosine over adenine preference, involving N7 repulsion and BII conformational effects, is novel and mechanistically plausible. However, several technical aspects require clarification, particularly regarding convergence of free energy calculations, the statistical significance of correlations, and the generalizability of conclusions drawn from a limited set of protein-DNA complexes. The manuscript is clearly written and accessible to a broad readership.

- **Who would be interested in the results, and why** Researchers in the fields of protein-DNA recognition, transcription factor biology, computational biophysics, and molecular recognition would find these results valuable. The work challenges conventional assumptions about acidic residues in DNA binding and provides mechanistic insights that could inform protein engineering, drug design, and understanding of transcription factor specificity. The methodological framework combining multiple computational approaches may also interest computational biologists developing predictive models of binding specificity.

- **Major strengths** The study addresses a genuinely overlooked aspect of DNA-protein recognition with a well-designed multi-scale computational approach. The negative selection hypothesis is clearly articulated and tested through systematic mutagenesis calculations. The combination of classical and ab initio methods provides complementary evidence. The identification of long-range electrostatic effects as a key determinant of cytosine recognition is a significant conceptual advance. The explanation for cytosine versus adenine preference is mechanistically detailed and experimentally testable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that computed ΔΔG values support the negative selection mechanism, with average ΔΔG of 1.10 ± 0.74 kcal/mol for A, 0.65 ± 0.36 kcal/mol for G/T, and −1.41 ± 0.60 kcal/mol for C sequences.
- **Evidence pointer** Results and Discussion, first subsection; SI Appendix Table S3
- **Concern** The manuscript reports mean ΔΔG values with standard deviations but does not provide information on the statistical significance of differences between sequence categories. With only five protein-DNA complexes and 24 total systems, it is unclear whether the observed differences between C and non-C sequences are statistically robust. Additionally, the uncertainty estimates for individual ΔΔG values from alchemical free energy calculations are not reported, making it difficult to assess whether the differences between categories exceed the underlying computational error.
- **Why it matters** The central conclusion that acidic residues act as negative selectors depends on the statistical reliability of the ΔΔG comparisons. If the differences between C and non-C sequences are within computational uncertainty, the negative selection hypothesis would not be supported.
- **Resolution test** Provide per-system ΔΔG values with associated statistical errors (e.g., from block averaging or bootstrapping), and perform a statistical test (e.g., t-test or Mann-Whitney U test) comparing C versus non-C categories. Report effect sizes and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the number of cytosines in the local sequence of Asp/Glu (#C) is the best predictor of ΔΔG, with predictive power twice that of #Hb-C in a nonlinear model.
- **Evidence pointer** Results and Discussion, first subsection; Fig. 3A; SI Appendix Fig. S4
- **Concern** The correlation analysis and random forest feature importance ranking are described only briefly. The Pearson correlation coefficients are mentioned but not reported numerically. The random forest approach is stated to use Shapley values, but details on model training, hyperparameters, cross-validation, and the significance of feature importance rankings are not provided. With only 24 data points, the risk of overfitting in a nonlinear model is substantial.
- **Why it matters** The claim that #C is a superior predictor to #Hb-C is a key mechanistic conclusion. If the analysis is not statistically robust, this conclusion may not be reliable.
- **Resolution test** Report all Pearson correlation coefficients with p-values. Provide details of the random forest model including number of trees, feature set, cross-validation strategy, and confidence intervals for Shapley values. Consider simpler linear models with proper multiple testing correction given the small sample size.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that QM/MM simulations and quantum chemical calculations confirm the origin of Asp/Glu preference for cytosine over adenine, with a free energy difference of approximately 2 kcal/mol and repulsion from N7 accounting for roughly half of the binding energy difference.
- **Evidence pointer** Results and Discussion, fourth subsection; Fig. 6; SI Appendix Figs. S18-S19
- **Concern** The QM/MM free energy profiles are based on only 27 umbrella sampling windows with 30 ps of simulation per window (15 ps used for analysis). This is a very short simulation time for converged free energy estimates, particularly for a system involving a charged species interacting with DNA. The manuscript does not report convergence tests, autocorrelation analysis, or statistical uncertainties for the free energy profiles. The quantum chemical calculations on model systems, while informative, use a simplified representation that may not capture the full electrostatic environment of the DNA-protein interface.
- **Why it matters** The quantitative claims about the magnitude of cytosine preference and the contribution of N7 repulsion depend on the reliability of these calculations. If the QM/MM free energies are not converged, the quantitative conclusions are not supported.
- **Resolution test** Provide convergence analysis for the umbrella sampling calculations, including time evolution of free energy estimates, autocorrelation times, and statistical uncertainties. Report the full free energy profiles with error bars. For the quantum chemical calculations, discuss the sensitivity of results to the choice of model system and solvation model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "cytosines are almost exclusively recognized by Asp/Glu" and that "the direct readout of cytosine by DNA-binding proteins occurs almost exclusively through Asp or Glu."
- **Evidence pointer** Significance section; Conclusions; Fig. 1
- **Concern** This claim appears to be based on statistical analysis of known protein-DNA structures, but the details of this analysis are not presented in the main text. The criteria for defining "recognition" and the database used are not described. The claim of "almost exclusively" is strong and would require comprehensive structural analysis to support.
- **Why it matters** This is a headline claim of the manuscript. If the structural database analysis is not comprehensive or the criteria are too restrictive, the claim may be overstated.
- **Resolution test** Provide details of the structural database analysis, including database version, search criteria, definition of Asp/Glu-cytosine interactions, and the full statistics. Discuss potential biases in the structural database and how they were addressed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors propose that the negative selection mechanism "might accelerate target search by destabilizing transient binding complexes at off-target sites."
- **Evidence pointer** Conclusions
- **Concern** This hypothesis is presented without direct evidence. While it is a reasonable speculation, it is not tested in this work. The connection between the equilibrium binding free energy calculations and kinetic target search processes is not established.
- **Why it matters** This claim extends the findings to a broader biological context. If presented as a hypothesis, it should be clearly labeled as such; if presented as a conclusion, it requires supporting evidence.
- **Resolution test** Clearly label this as a hypothesis or speculation. If the authors wish to make this claim, they should provide additional evidence or cite relevant literature supporting the connection between negative selection and target search kinetics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Fig. 1
- **Evidence pointer** Fig. 1
- **Issue** The manuscript refers to "known nucleobase propensities (Fig. 1)" but does not describe how these propensities were derived or what exactly is plotted. The figure is not visible in the provided text.
- **Required correction** Provide a clear description of Fig. 1 in the text, including the source of the data and the definition of "propensity."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Molecular Systems
- **Evidence pointer** Materials and Methods, Molecular Systems
- **Issue** The selection criteria for the five protein-DNA complexes are described, but it is unclear how representative these are of the broader population of DNA-binding proteins. The authors note the limited dataset may not capture all factors, but a more systematic selection strategy would strengthen the conclusions.
- **Required correction** Discuss the rationale for selecting these specific complexes and acknowledge potential limitations in generalizability. Consider whether additional complexes from diverse structural families would strengthen the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Alchemical Free Energy Calculations
- **Evidence pointer** Materials and Methods, Alchemical Free Energy Calculations
- **Issue** The manuscript states that systems were simulated for at least 300 ns per lambda window, but does not report the number of lambda windows, the total simulation time per system, or the convergence criteria used. The acceptance rate for replica exchange is mentioned but not quantified.
- **Required correction** Provide details on the number of lambda windows, total simulation time, convergence metrics, and replica exchange acceptance rates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results and Discussion, first subsection
- **Evidence pointer** Results and Discussion, first subsection
- **Issue** The transition from discussing correlation analysis to discussing outliers is abrupt. The logic connecting the random forest results to the interpretation of outliers is not fully explained.
- **Required correction** Add a brief transitional paragraph explaining how the feature importance analysis informs the interpretation of individual outliers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Quantum Chemical Calculations
- **Evidence pointer** Materials and Methods, Quantum Chemical Calculations
- **Issue** The QM region includes "several water molecules in between the propionate and DNA" but the exact number and selection criteria are not specified. The sensitivity of results to the number of explicit water molecules is not discussed.
- **Required correction** Specify the number of water molecules in the QM region and discuss the sensitivity of the calculated binding energies to this choice.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The final paragraph introduces speculation about protein design and machine learning that, while interesting, is not directly connected to the findings of this work.
- **Required correction** Either remove this paragraph or connect it more explicitly to the implications of the findings for protein design.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Simulation Details
- **Evidence pointer** Materials and Methods, Simulation Details
- **Issue** The manuscript states that the temperature was kept at 300 K for classical simulations but 310 K for QM/MM simulations. The reason for this difference is not explained.
- **Required correction** Justify the different temperatures used in the two simulation approaches.

## Risk / unsupported claims
- The claim that "cytosines are almost exclusively recognized by Asp/Glu" is not fully supported by the evidence presented, as the structural database analysis is not described in detail.
- The hypothesis that negative selection accelerates target search kinetics is speculative and not directly tested.
- The quantitative claim that N7 repulsion accounts for "roughly half" of the binding energy difference between cytosine and adenine is based on QM/MM calculations with limited sampling and may not be robust.
- The generalizability of the negative selection mechanism beyond the five examined protein-DNA complexes is uncertain given the limited dataset.
- The claim that the cumulative effect of cytosine arises from "long-range electrostatic attraction" is supported by correlation analysis but the causal relationship is not definitively established.