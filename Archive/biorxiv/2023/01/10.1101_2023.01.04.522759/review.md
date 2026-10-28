## Review setup

- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusion, contributions, acknowledgments) as provided by the user. Supplementary Information referenced but not provided.
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text. No assessment of formatting, grammar, or editorial style beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors report that tetracationic Au and Ag pillarplexes, a class of organometallic supramolecular complexes, bind to DNA Holliday 4-way junctions (4WJ) in their open cruciform conformation, a binding mode not previously achieved by synthetic agents. They also report binding to 3-way junctions (3WJ) and Y-shaped forks, with a preference for 4WJ over 3WJ, and demonstrate that the Au pillarplex can enter cells and reach the nucleus with antiproliferative activity comparable to cisplatin.
- **Visible evidence base** Gel electrophoresis data (Figures 3, 5, 6, S2, S6, S13–S15), UV-melting experiments (Figures S3, S4), molecular dynamics simulations (Figures 4, 7, 9, S11, S12), circular dichroism and linear dichroism spectroscopy (Figure 8, S17–S18), ICP-MS cellular uptake data, and antiproliferative activity data (Table ST1). All figures and tables referenced but not directly viewable in the provided text.
- **Missing materials affecting confidence** All figures, tables, and Supplementary Information (including experimental methods, full simulation parameters, and raw data) are not provided. This limits verification of quantitative claims, statistical significance, and experimental reproducibility.

## Reviewer

- **Overall assessment** This manuscript presents a novel and potentially significant finding: the first synthetic agent reported to bind the open form of a DNA Holliday junction. The combination of experimental and computational approaches is appropriate and the results are internally consistent. However, the absence of the actual figures, tables, and supplementary data prevents full verification of the claims. The distinction between the pillarplex binding mode and that of previously reported junction binders is conceptually important, and the cellular data, while preliminary, adds translational relevance. The work is likely to interest the nucleic acid chemistry, chemical biology, and DNA nanotechnology communities. The main concerns relate to the strength of the evidence for the claimed 4WJ binding mode, the interpretation of the gel data, and the limited cellular characterization.

- **Who would be interested in the results, and why** Researchers in nucleic acid recognition and chemical biology, particularly those studying DNA junction structures and their roles in recombination and repair. The DNA nanotechnology community will be interested in the ability to modulate junction conformations. Inorganic and organometallic chemists designing metal-based DNA binders will find the design principles valuable. The cellular uptake and antiproliferative data may attract interest from those working on metal-based anticancer agents.

- **Major strengths**
  1. The claim of binding to the open form of a 4WJ is novel and, if substantiated, represents a significant advance in the field of synthetic DNA junction binders.
  2. The combination of gel electrophoresis, UV-melting, and MD simulations provides a multi-pronged approach to studying the interaction.
  3. The comparison with the previously characterized metallo-supramolecular cylinders provides a useful contrast and highlights the unique properties of the pillarplex.
  4. The cellular uptake and antiproliferative studies, while preliminary, extend the relevance of the work beyond in vitro biophysics.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** "an Au pillarplex can bind DNA 4-way junctions (Holliday junctions) in their open form, a binding mode not accessed by synthetic agents before"
- **Evidence pointer** Figure 5, Figure 7, location not provided
- **Concern** The central claim of open-form 4WJ binding rests on a gel shift assay (Figure 5) and MD simulations (Figure 7). The gel data show a band shift consistent with an open conformation, but the interpretation relies on the assumption that the shifted band corresponds to an open 4WJ rather than a non-specific aggregate or a partially melted structure. The MD simulations, while supportive, are based on a starting structure that is already partially open (pdb 1XNS with Cre proteins removed), and the authors note that the starting cavity has only two of four potential base pairings. This raises the question of whether the simulations demonstrate induced opening or simply stabilization of a pre-existing open state. The authors do not provide a control simulation with a fully closed 4WJ starting structure to show that the pillarplex can actively open a closed junction.
- **Why it matters** The novelty of the work hinges on the claim that the pillarplex binds the open form of a 4WJ. If the evidence only shows binding to a pre-existing open state or a non-specific interaction, the significance is substantially diminished.
- **Resolution test** Provide a gel shift assay with a 4WJ that is locked in the closed conformation (e.g., by sequence design or chemical crosslinking) to demonstrate that the pillarplex can actively open and bind a closed junction. Alternatively, provide MD simulations starting from a fully closed 4WJ structure showing spontaneous opening upon pillarplex binding. Include a quantitative analysis of the gel bands (e.g., densitometry) to support the claim of a discrete bound species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative support for binding preferences
- **Claim pointer** "the pillarplex prefers 4WJ over 3WJ" and "the pillarplex would rather bind forks than be unbound"
- **Evidence pointer** Figures 3, 5, 6, location not provided
- **Concern** The claim of preferential binding to 4WJ over 3WJ is based on qualitative gel observations. The authors note that at high loading, the 4WJ band is still present while the 3WJ band has disappeared, but no quantitative binding affinities or competition experiments are provided. The statement that the pillarplex "would rather bind forks than be unbound" is speculative and not directly tested. The preference for 4WJ over 3WJ is a key differentiator from the cylinder, but the evidence is not quantitative.
- **Why it matters** A quantitative comparison of binding affinities (e.g., by ITC, fluorescence anisotropy, or competition assays) would strengthen the claim of selectivity and provide a more rigorous basis for the proposed design principles.
- **Resolution test** Perform competition experiments where the pillarplex is titrated into a mixture of 4WJ and 3WJ, with quantification of the bound species. Alternatively, measure binding constants for each junction type using a solution-based method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Cellular data interpretation
- **Claim pointer** "confirm that the pillarplexes do reach the nucleus, with antiproliferative activity at levels similar to those of cisplatin"
- **Evidence pointer** ICP-MS data and Table ST1, location not provided
- **Concern** The cellular studies are presented as confirmatory, but the data are preliminary. Only one cell line (A549) is used for uptake studies, and the nuclear fractionation shows only ~10% of intracellular Au in the nucleus. The antiproliferative activity is reported as IC50 values at 24 and 72 h, but the mechanism of action is not explored. The claim that the activity is "similar to cisplatin" is based on a single comparison and lacks statistical context. The authors do not address whether the observed activity is due to DNA binding or other off-target effects.
- **Why it matters** The translational relevance of the work depends on the cellular data. Without a clearer understanding of the mechanism and a more robust statistical comparison, the claim of cisplatin-like activity is not fully supported.
- **Resolution test** Provide dose-response curves with multiple replicates and statistical analysis. Include a mechanistic study (e.g., γ-H2AX staining for DNA damage, or a reporter assay for junction resolution) to link the antiproliferative effect to DNA junction binding.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of experimental conditions
- **Affected element** Gel electrophoresis experiments
- **Evidence pointer** Figures 3, 5, 6, location not provided
- **Issue** The text does not specify the buffer conditions, temperature, or incubation times for the gel experiments. The stability of the 4WJ and 3WJ structures is highly dependent on ionic strength and temperature.
- **Required correction** Add a brief description of the gel electrophoresis conditions in the main text or refer to the Supplementary Information with specific details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Simulation details
- **Affected element** MD simulations
- **Evidence pointer** Figures 4, 7, 9, location not provided
- **Issue** The force field parameters, water model, and simulation length are not described in the main text. The authors mention "three at 2 μs each" for the 4WJ simulations, but the equilibration protocol and the number of replicates for the 3WJ and duplex simulations are not stated.
- **Required correction** Provide a summary of the simulation parameters in the main text or refer to the Supplementary Information with full details.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Comparison with cylinder
- **Affected element** Discussion of cylinder vs. pillarplex
- **Evidence pointer** Figures 3, 5, location not provided
- **Issue** The contrast between the pillarplex and the cylinder is a key point, but the discussion is largely qualitative. The authors state that the cylinder rearranges 4WJ into 3WJ, but the evidence for this is not shown in the main text.
- **Required correction** Include a direct comparison of the cylinder and pillarplex in the same gel experiment, or provide a reference to previously published data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Y-shaped forks"
- **Evidence pointer** Abstract, Results and Discussion
- **Issue** The term "Y-shaped forks" is used to describe a 2-stranded structure, but "fork" in DNA biology typically refers to a replication fork with three strands. The authors should clarify the nomenclature to avoid confusion.
- **Required correction** Define "Y-shaped fork" explicitly in the text, or use a more precise term such as "Y-shaped duplex junction."

## Risk / unsupported claims

1. The claim that the pillarplex binds the open form of a 4WJ "a binding mode not accessed by synthetic agents before" is not fully supported without a comprehensive literature comparison and direct structural evidence (e.g., co-crystal structure or NMR).
2. The statement that the pillarplex "would rather bind forks than be unbound" is speculative and not directly tested.
3. The claim that the pillarplex "can rearrange 4-way junctions into 3-way junction structures" (attributed to the cylinder) is not shown in the provided text.
4. The cellular data are described as "confirmatory," but the evidence is preliminary and lacks mechanistic depth.
5. The statement that the pillarplex is "a little small to completely fill an open 4WJ cavity" is based on MD simulations and is not experimentally validated.
6. The claim of "antiproliferative activity at levels similar to those of cisplatin" is based on a single comparison and lacks statistical context.