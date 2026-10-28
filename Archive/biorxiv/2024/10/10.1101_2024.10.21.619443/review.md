## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, methods, results and discussion, conclusions, and supplementary figure references. Figures, tables, and supplementary materials were not provided.
- **Assessment boundary** The scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence as described in the text. No assessment of data quality beyond what is described in the text is possible.
- **Shared manuscript claim summary** The authors claim that polyphosphate (polyP) discriminates protein conformational ensembles more efficiently than DNA, leading to diverse assembly and maturation behaviors (condensates, aggregates, dissolution) depending on the starting conformational state of the intrinsically disordered CytR DBD and its variants.
- **Visible evidence base** Text descriptions of turbidity measurements, fluorescence microscopy, FRAP, circular dichroism spectroscopy, and FTIR spectroscopy. Phase diagrams and kinetic traces are described but not visible.
- **Missing materials affecting confidence** All figures, supplementary figures, and movies are not provided. Raw data, statistical analyses, and detailed experimental replicates are not described. This substantially limits the ability to verify the quantitative claims and the robustness of the reported effects.

## Reviewer

- **Overall assessment** The manuscript addresses an interesting and timely question regarding the differential roles of polyphosphate versus DNA in driving phase separation and aggregation of disordered proteins. The choice of the CytR DBD system with two well-characterized mutants (DM and P33A) is logical and provides a useful platform for comparing conformational ensemble effects. However, the central claim that polyP "discriminates conformational ensembles more efficiently than DNA" is not fully established from the provided text. The evidence is largely qualitative, and key quantitative comparisons between polyP and DNA conditions are described but not shown. The mechanistic interpretation, particularly regarding polyproline II structure formation, is speculative and would benefit from additional structural validation. The manuscript is well-written and the conceptual framework is appealing, but the strength of the conclusions currently exceeds the visible evidence base.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates, phase separation, intrinsically disordered proteins, and stress response mechanisms in bacteria would find this work relevant. The comparison between polyP and DNA as polyanionic drivers of assembly is of broad interest to the fields of cellular biochemistry and biophysics. The potential link to transcription regulation under stress conditions adds significance for microbiologists and molecular biologists.
- **Major strengths**
  - The question addressed is novel and significant, as polyP is an understudied polymer in the context of condensate formation.
  - The use of a mutational series (WT, DM, P33A) with defined conformational properties provides a clean experimental design.
  - The comparison between polyP and DNA within the same protein system is a strength.
  - The combination of multiple biophysical techniques (turbidity, microscopy, FRAP, CD, FTIR) is appropriate.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** "Polyphosphate induces large secondary-structure changes, with two of the mutants adopting polyproline II-like structures within droplets, while DNA has only minimal structural effects."
- **Evidence pointer** Figure 4, described in text; figures not provided
- **Concern** The claim that polyP induces polyproline II-like structures is based on a decomposition of CD spectra using SVD, where the second component is assigned to PPII. However, the text states that the spectra are "an effective average of structural signatures from both the condensed- and dilute-phases and of different secondary-structure types," and that "the spectral shapes cannot be directly interpreted." The assignment of the second SVD component to PPII appears to be based on spectral shape alone, without independent validation (e.g., from FTIR, which is only shown for P33A, or from other structural probes). The negative amplitude of the second component in P33A is interpreted as evidence for beta-turn or polyproline I conformations, which is a substantial interpretive leap.
- **Why it matters** The structural interpretation is central to the mechanistic claim that polyP discriminates conformational ensembles. If the PPII assignment is incorrect or overinterpreted, the conclusion that polyP induces specific secondary structure changes is weakened.
- **Resolution test** Provide the SVD basis spectra and demonstrate that the second component matches a bona fide PPII spectrum (e.g., from model peptides). Show that the reconstruction accurately captures the raw data. Ideally, provide independent validation of PPII structure using a technique such as Raman spectroscopy or site-specific probes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** "Polyphosphate can more efficiently discern conformational heterogeneity in the starting protein ensemble, its structure, and compactness" and "DNA is insensitive to the starting conformational ensembles."
- **Evidence pointer** Figures 2, 5, and 6; described in text; figures not provided
- **Concern** The central comparative claim that polyP is more sensitive to conformational ensembles than DNA rests on a comparison across different experimental conditions. For polyP, the concentration used is 22 µM, while for DNA it is 1 µM (and 11.2 µM in control experiments). The authors state that the control experiments at 11.2 µM DNA showed identical trends, but the data are not shown. The comparison of "sensitivity" is therefore made across different polymer concentrations, lengths, and chemical properties, which makes the conclusion difficult to evaluate. Furthermore, the claim that DNA is "insensitive" is based on only three variants of one protein, and the time window of observation may not capture slower maturation processes.
- **Why it matters** The title and abstract emphasize the differential sensitivity of polyP versus DNA. If this comparison is not rigorously established under matched conditions, the central message of the paper is overstated.
- **Resolution test** Show the control experiments at matched negative charge concentrations for polyP and DNA. Provide quantitative metrics of "sensitivity" (e.g., differences in turbidity, FRAP recovery, or secondary structure change) across the three variants for both polymers, with appropriate statistics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** "The driving force for the different assembly processes is expected to have a strong contribution from the strength of intermolecular charge-charge interactions, the relative entropic penalty for inducing a conformational change in polyP versus that in the protein, release of counterions and restructuring of water."
- **Evidence pointer** Discussion section; location not provided
- **Concern** The mechanistic discussion is speculative and not directly supported by the experiments presented. While the authors acknowledge that "detailed molecular simulations" are required, the current text presents this as a plausible explanation without quantitative support. The claim that polyP is more flexible than DNA and can therefore "wrap around" the protein surface is plausible but untested.
- **Why it matters** The mechanistic framework is important for the broader implications of the work. Without experimental or computational support, the discussion remains at the level of hypothesis, which is acceptable for a preprint but should be clearly framed as such.
- **Resolution test** Either temper the mechanistic language to clearly indicate speculation, or provide supporting evidence (e.g., from simulations, binding assays, or osmotic stress experiments).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "Our findings reveal how polyphosphate can more efficiently discern conformational heterogeneity in the starting protein ensemble, its structure, and compactness, with broad implications in assembly mechanisms involving polyP and stress response in bacterial systems."
- **Evidence pointer** Conclusions; location not provided
- **Concern** The claim of "broad implications" is based on a single protein system (CytR DBD) and two mutants. While the authors include a second system (FruR and Y19A), the data for FruR are described only briefly and the figures are not provided. The generalizability of the findings to other disordered proteins and to in vivo conditions is not established.
- **Why it matters** The significance of the work for a broad audience depends on the generality of the observed phenomena. Overstatement of implications without additional systems or in vivo validation weakens the impact.
- **Resolution test** Either add additional protein systems or clearly frame the conclusions as specific to the systems studied, with the broader implications presented as hypotheses.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, FRAP analysis
- **Evidence pointer** Methods, "Fluorescence recovery after photobleaching (FRAP)"
- **Issue** The FRAP data analysis is described with equations, but the equations themselves are not shown in the text provided. The description of the normalization procedure is incomplete.
- **Required correction** Include the full equations and a clear description of the fitting procedure used to extract recovery half-times and mobile fractions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, CD spectroscopy
- **Evidence pointer** Methods, "Circular dichroism (CD)"
- **Issue** The text states that CD spectra were recorded at 55 µM and 25 µM protein for polyP and DNA conditions, respectively, but does not specify the pathlength of the cuvette or the exact buffer conditions for each measurement. The mean helical content estimation is described, but the reference value of −40,000 MRE units is not justified.
- **Required correction** Provide the pathlength, buffer composition, and a reference or justification for the 100% helical value used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, phase diagram
- **Evidence pointer** Figure 2A; described in text
- **Issue** The phase diagram is described as showing "consistent" turbidity for [WT]>25 µM and [polyP]>10 µM, but the boundaries of the phase-separated region are not quantitatively defined. It is unclear whether the transition is sharp or gradual.
- **Required correction** Provide a quantitative definition of the phase boundary (e.g., turbidity threshold) and indicate the error bars or replicate information.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "Maturation of polyphosphate-induced assemblies"
- **Evidence pointer** Figure 3A; described in text
- **Issue** The text states that the OD decreases in the first 10 minutes for WT-polyP, but the interpretation of this decrease is not discussed. It is unclear whether this reflects a change in the condensate properties, sedimentation, or an artifact of the measurement.
- **Required correction** Provide a brief interpretation of the initial OD decrease or acknowledge it as an unresolved observation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, FruR experiments
- **Evidence pointer** Figure 6; described in text
- **Issue** The FruR experiments are presented as supporting evidence for the generality of the findings, but the description is brief and the data are not shown. The reader cannot evaluate the quality of these experiments.
- **Required correction** Provide the full data for the FruR experiments, including time-dependent turbidity, microscopy, and CD spectra, or clearly state that these are preliminary results.

## Risk / unsupported claims

- The claim that polyP induces polyproline II-like structures in WT and DM condensates is not fully supported without the SVD basis spectra and independent validation.
- The claim that DNA is "insensitive" to conformational ensembles is not rigorously established due to unmatched experimental conditions and limited variant sampling.
- The mechanistic discussion regarding polyP flexibility and wrapping around protein surfaces is speculative and not directly tested.
- The "broad implications" for bacterial stress response and transcription regulation are presented as conclusions but are not experimentally addressed.
- The statement that "polyP is expected to be highly flexible" relative to DNA is presented as a fact but is not referenced or measured.
- The claim that "condensates are more kinetically accessible phase but which are inherently metastable" is a general statement not specifically tested in this system.