## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific soundness, technical rigor, and internal consistency of the claims as supported by the presented evidence
- **Shared manuscript claim summary** The authors evaluate five frequent ARID1A missense mutations (R1020S, M1022K, K1047Q, G1063V, A1089T) using computational predictors, rexDMD simulations, and thermal/chemical denaturation experiments, concluding that R1020S is the most destabilizing mutation and that this approach can categorize pathogenic mutations for potential therapeutic targeting
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, figure references (Figures 1-6, S1-S12), data availability statement
- **Missing materials affecting confidence** Figures and supplementary materials referenced but not provided; raw fluorescence data, rexDMD output files, CD spectra, and AlphaMissense comparison data not accessible; no statistical analysis details or replicate numbers provided

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in cancer biology, namely whether frequent ARID1A missense mutations destabilize the ARID domain and whether this correlates with pathogenicity. The hybrid computational-experimental approach is commendable in principle. However, the evidence as presented has several critical gaps. The most significant issue is that the experimental thermal denaturation data are described as irreversible, yet the authors fit these data to a two-state equilibrium model to extract apparent Tm values. This is thermodynamically questionable and requires justification. Additionally, the conversion of Tm shifts and D1/2 shifts into ΔΔG values using equations (3)-(5) is not rigorously derived, and the "overall impact" metric is not clearly defined or validated. The claim that R1020S is "most destabilizing" is supported across methods, but the quantitative agreement between methods is not shown. The manuscript would benefit from clearer presentation of raw data, error analysis, and a more cautious interpretation of the pathogenicity implications.

- **Who would be interested in the results, and why** Researchers in cancer genomics, chromatin remodeling, and protein biophysics would find this work relevant. The identification of specific destabilizing mutations in a frequently mutated tumor suppressor could inform functional studies and potentially guide patient stratification in clinical trials. The methodological combination of computational prediction and experimental validation is of general interest to the protein stability community.

- **Major strengths** 
  1. The study addresses a clinically relevant question with a clear hypothesis
  2. The combination of multiple computational tools with experimental validation is a strength
  3. The use of rexDMD simulations provides a molecular-level perspective
  4. The authors acknowledge limitations of web server tools and emphasize the need for experimental validation
  5. The data availability statement provides access to raw simulation and fluorescence data

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of thermodynamic analysis
- **Claim pointer** "Given the irreversible nature of thermal unfolding, we analyzed the fluorescence data by fitting it to a two-state unfolding model to determine the apparent melting temperature Tm,app"
- **Evidence pointer** Results section, Thermal stability subsection; Materials and Methods, Fluorescence measurements
- **Concern** The authors explicitly state that thermal unfolding is irreversible, yet they fit the data to a two-state equilibrium model (Eq. 1) to extract apparent Tm values. For irreversible transitions, the application of equilibrium thermodynamics is not valid, and the extracted Tm values are kinetically controlled rather than thermodynamically defined. The manuscript does not address this fundamental issue or provide justification for why the two-state model is appropriate under irreversible conditions.
- **Why it matters** The central quantitative claim of the paper, that R1020S reduces Tm by approximately 10 K relative to WT, rests on this analysis. If the fitting model is inappropriate, the reported Tm values and all subsequent ΔΔG calculations derived from them are not physically meaningful.
- **Resolution test** The authors must either (a) demonstrate that the thermal unfolding is at least partially reversible under their conditions, (b) use an appropriate kinetic model for irreversible unfolding, or (c) clearly state that the reported Tm values are apparent and kinetically controlled, and temper the quantitative conclusions accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of ΔΔG conversion
- **Claim pointer** "We calculated the overall impact by first converting all effects into the same unit, kcal/mol, using equations (3), (4) and (5)"
- **Evidence pointer** Materials and Methods, Overall Impact subsection
- **Concern** The conversion of Tm shifts to ΔΔG values using Eq. (3) and (4) assumes a specific relationship that is not derived or referenced. The standard relationship between Tm shift and ΔΔG requires knowledge of the enthalpy change at the melting temperature and assumes a two-state transition. The manuscript does not provide the ΔHm values used, how they were obtained, or whether they were assumed or measured. Similarly, Eq. (5) converts D1/2 shifts to ΔΔG using the m-value, but the m-values are not reported. The "overall impact" metric, which sums these converted values, is not defined with clear weighting factors.
- **Why it matters** The "overall impact" categorization is a key output of the paper and is used to rank the mutations. If the conversion equations are not rigorously justified or the input parameters are not reported, the resulting rankings cannot be evaluated or reproduced.
- **Resolution test** Provide the ΔHm and m-values used in the conversions, derive or reference the conversion equations, and clearly define the weighting scheme for the "overall impact" metric. Alternatively, present the raw Tm and D1/2 values without conversion and discuss the qualitative agreement across methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and error analysis
- **Claim pointer** "The extracted Tm,app varied among the mutants, with WT displaying the highest thermal stability at Tm,app of 333±1 K"
- **Evidence pointer** Results section, Thermal stability subsection; Materials and Methods, Fluorescence measurements
- **Concern** The manuscript reports a Tm value with an uncertainty (333±1 K) but does not describe how this uncertainty was determined. No replicate numbers, standard deviations, or statistical tests are reported for any of the experimental measurements. The differences between mutants are described qualitatively (e.g., "R1020S, K1034Q, and G1063V mutants exhibited the lowest stabilities") without statistical support.
- **Why it matters** Without error bars and statistical analysis, the reader cannot assess whether the reported differences between mutants are significant or within experimental noise. This is particularly important given the small expected differences in stability between some mutants.
- **Resolution test** Report the number of independent replicates, the standard deviation or standard error for each measurement, and perform appropriate statistical tests (e.g., ANOVA with post-hoc comparisons) to support claims of differential stability between mutants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency of results
- **Claim pointer** "Most mutations predominantly resulted in destabilization, although a few exhibited minor stabilizing effects" and "Only the R1020S mutation showed a destabilizing effect" (referring to rexDMD)
- **Evidence pointer** Results, first and second subsections
- **Concern** There is an apparent inconsistency between the computational predictor results and the rexDMD simulation results. The predictors show variable effects across mutations, with some stabilizing, while the rexDMD simulations show that only R1020S is destabilizing and all other mutations are stabilizing relative to WT. The manuscript does not reconcile these discrepancies or discuss what this means for the reliability of either method.
- **Why it matters** The paper claims a "hybrid approach" that combines methods, but if the methods disagree, the reader needs to understand how the authors weighted or interpreted conflicting evidence. The current presentation appears to selectively emphasize results that support the main conclusion.
- **Resolution test** Provide a direct comparison of predictions from all methods for each mutation, discuss the discrepancies, and justify the interpretation. If the rexDMD results contradict the predictors, this should be addressed explicitly rather than presented as consistent.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Relevance of the ARID domain construct
- **Claim pointer** "We analyzed five frequent missense mutations R1020S, M1022K, K1047Q, G1063V, and A1089T identified in The Cancer Genome Atlas (TCGA) to assess their effects on the stability of the ARID domain"
- **Evidence pointer** Abstract; Materials and Methods, Protein expression and purification
- **Concern** The study uses an isolated ARID domain construct, not the full-length ARID1A protein. The authors do not discuss whether the stability of the isolated domain reflects the stability of the domain within the full-length protein context, where neighboring domains and protein-protein interactions could modulate folding stability. Additionally, the construct boundaries are not clearly defined.
- **Why it matters** The clinical relevance of the findings depends on whether the observed stability changes in the isolated domain translate to the full-length protein in cells. Without discussion of this limitation, the conclusions may be overextended.
- **Resolution test** Acknowledge this limitation explicitly and discuss the potential impact of domain context on the findings. If possible, provide preliminary data on the full-length protein or justify why the isolated domain is a valid model.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section
- **Evidence pointer** Figures 1-6, S1-S12
- **Issue** The manuscript references many figures, but the figures themselves are not provided in the submitted material. It is impossible to verify the claims made about the data without seeing the actual figures.
- **Required correction** Ensure all figures are included in the submission and that the figure captions are sufficiently detailed to understand the data presented.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Nomenclature consistency
- **Affected element** Results, Thermal stability subsection
- **Evidence pointer** "K1034Q" mentioned in text
- **Issue** The manuscript lists the five mutations as R1020S, M1022K, K1047Q, G1063V, and A1089T, but in the thermal stability results, "K1034Q" is mentioned. This appears to be a typo for K1047Q, but it creates confusion.
- **Required correction** Correct the mutation name to K1047Q throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, Fluorescence measurements
- **Evidence pointer** "response 0.5 sec"
- **Issue** The integration time for fluorescence measurements is reported as 0.5 sec, but it is unclear whether this is the integration time per wavelength point or the total acquisition time per spectrum. This detail affects the signal-to-noise ratio and comparability of measurements.
- **Required correction** Clarify the acquisition parameters, including the number of scans averaged and the step size for wavelength scanning.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Materials and Methods, Circular dichroism experiments
- **Evidence pointer** "recording the spectra from 200 to 260 nm at different 2,2,2-trifluoroethanol (TFE) concentrations"
- **Issue** The CD experiments are described in the methods but the results are not presented in the Results section. It is unclear what conclusion is drawn from these experiments and how they support the main findings.
- **Required correction** Either present the CD results in the Results section and discuss their relevance, or remove the methods description if the data are not used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference to supplementary data
- **Affected element** Results, Chemical stability subsection
- **Evidence pointer** "Figure S8A and B"
- **Issue** The manuscript states that the unfolding and refolding pathways differed based on D1/2 values, but the actual D1/2 values are not reported in the text. The reader must rely on the supplementary figures, which are not provided.
- **Required correction** Report the D1/2 values for all mutants in the text or a table, and ensure the supplementary figures are available.

## Risk / unsupported claims
- The claim that the "overall impact" categorization agrees with AlphaMissense predictions (Pearson coefficient 0.66) cannot be evaluated because the AlphaMissense data and the comparison analysis are not shown
- The claim that R1020S disrupts salt bridges with negatively charged residues is based on structural models from DDMut, but the specific interactions are not described in detail and the figures are not available
- The statement that "this research paves the way for identifying and categorizing which ARID1A mutations are most pathogenic" is an overstatement given that the study only measures stability in an isolated domain and does not directly assess pathogenicity
- The claim that the findings "potentially guiding the development of targeted therapies tailored to specific mutation profiles" is speculative and not supported by the data presented
- The manuscript does not provide evidence that the five mutations studied are indeed the "most frequent" ARID1A mutations, as claimed in the title and abstract, beyond a general reference to TCGA