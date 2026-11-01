## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, materials and methods, conclusions) without figures, schemes, tables, or supplementary materials
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency as presented in the provided text
- **Shared manuscript claim summary** The authors report synthesis and characterization of two heterometallic pyrazolate-bridged complexes, PdCo and PdCu, and propose a dual mechanism of anticancer action involving DNA binding and ROS-driven oxidative stress, supported by cytotoxicity assays, spectroscopic DNA-binding studies, chemiluminescence-based enzyme-mimetic activity measurements, and molecular docking simulations
- **Visible evidence base** Textual descriptions of SC-XRD, PXRD, FTIR, UV-Vis, ESI-MS, CD spectroscopy, fluorescence spectroscopy, chemiluminescence assays, molecular docking, and MTT cytotoxicity assays; numerical values for IC50, Kd, binding affinities, and selectivity indices are reported in text
- **Missing materials affecting confidence** All figures, schemes, tables, and supplementary materials; raw experimental data; statistical analysis details; docking coordinates and parameters; cell line authentication documentation; compound purity data beyond elemental analysis

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting contribution to the field of heterometallic anticancer agents, with a plausible dual-action hypothesis. However, the evidence as presented in the text is insufficient to fully establish the proposed mechanism. Key concerns include the absence of direct cellular ROS measurements, limited DNA-binding characterization (only one complex tested), and a lack of mechanistic experiments linking the observed enzyme-mimetic activities to cytotoxicity. The synthetic and structural work appears sound based on the textual description, but the biological claims require additional experimental support.
- **Who would be interested in the results, and why** Researchers in bioinorganic chemistry, anticancer drug development, and metallodrug mechanism-of-action studies would find this work relevant. The heterometallic design concept and the attempt to combine DNA targeting with ROS generation address an active area of inquiry in inorganic medicinal chemistry.
- **Major strengths** The heterometallic scaffold design is conceptually interesting and addresses a gap in the literature. The characterization appears thorough, combining multiple complementary techniques. The comparative analysis of PdCo versus PdCu provides insight into how the identity of the second metal influences biological activity. The selectivity indices reported for certain cell lines are notable and suggest potential therapeutic windows.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (cellular ROS not measured), R1-M2 (DNA-binding data incomplete), R1-M3 (mechanistic link between enzyme-mimetic activity and cytotoxicity not established), R1-M4 (docking methodology and interpretation require clarification)
- **Assessment against Nature-style criteria** Originality: moderate. The heterometallic approach is not entirely new, but the specific combination of Pd with Co or Cu in a pyrazolate-bridged scaffold for dual DNA/ROS action has limited precedent. Scientific importance: moderate. The findings could inform future metallodrug design, but the mechanistic evidence is currently incomplete. Interdisciplinary readership: limited. The work is primarily of interest to specialists in inorganic medicinal chemistry. Technical soundness: the synthetic and structural characterization appears sound, but the biological and mechanistic experiments are insufficiently developed. Readability for nonspecialists: the manuscript is generally readable, though some sections assume familiarity with coordination chemistry terminology.
- **Recommendation posture** Currently not established from the provided evidence. The synthetic and structural work is promising, but the biological mechanism claims require substantial additional experimental support before the dual-action hypothesis can be considered validated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** The manuscript claims that ROS-mediated oxidative stress constitutes a "second, complementary cytotoxic pathway" and that the complexes' peroxidase-like and SOD-like activities "implicate" this mechanism in the observed cytotoxicity
- **Evidence pointer** Section 2.3, Figures 3 and 4 (described in text)
- **Concern** The enzyme-mimetic activities were measured in cell-free, buffered solutions using chemiluminescence probes. No experiments were performed to demonstrate that these activities translate to increased ROS levels inside cells, nor was any correlation established between the magnitude of enzyme-mimetic activity and the degree of cytotoxicity across the two complexes. The claim that ROS generation contributes to the cytotoxic mechanism is therefore speculative at this stage.
- **Why it matters** The dual-action mechanism is the central thesis of the manuscript. Without direct evidence of ROS production in cellular systems, the proposed mechanism remains an inference from cell-free assays, which may not reflect the intracellular environment due to factors such as cellular uptake, compartmentalization, and endogenous antioxidant defenses.
- **Resolution test** The authors should measure intracellular ROS levels (e.g., using DCFH-DA or MitoSOX probes) in treated cells, ideally with and without ROS scavengers (e.g., NAC or vitamin E), and demonstrate that scavenging attenuates cytotoxicity. Alternatively, they could show a correlation between the complexes' enzyme-mimetic activities and their cytotoxic potencies across a broader panel of complexes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that PdCo binds to DNA with a preference for minor groove binding (Kd = 7.6 μM) over intercalation (Kd = 26.1 μM), and that molecular docking confirms the dissociated [Pd(phen)(µ-dmpz)2] fragment is capable of binding to DNA
- **Evidence pointer** Section 2.4, Figures 5, 6, and 7 (described in text); Section 2.5, Figures 8 and 9 (described in text)
- **Concern** DNA-binding studies were performed only for PdCo, not for PdCu, despite both complexes being evaluated for cytotoxicity. The claim of a "dual DNA-binding and ROS-driven" mechanism for both complexes is therefore only partially supported. Additionally, the CD spectral changes described are characterized as "slight," which raises questions about the significance of the conformational changes. The molecular docking was performed on a dissociated fragment rather than the intact complex, and the relevance of this fragment under physiological conditions is not established.
- **Why it matters** The comparative analysis of the two complexes is a stated strength of the work, but the DNA-binding data are incomplete. Without PdCu DNA-binding data, it is unclear whether the proposed dual mechanism applies to both complexes or only to PdCo. The use of a dissociated fragment for docking also requires justification, as the intact complex may behave differently.
- **Resolution test** The authors should perform the same DNA-binding experiments (CD, fluorescence displacement) with PdCu. They should also justify the use of the dissociated fragment in docking studies, or provide evidence that this fragment is the biologically relevant species under assay conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic link
- **Claim pointer** The manuscript states that "the differences in cytotoxicity between the structurally similar PdCo and PdCu are determined by the nature of the partner metal" and attributes PdCu's higher activity to its greater ROS-generating capacity
- **Evidence pointer** Section 2.2, Table 1 (described in text); Section 2.3, Figures 3 and 4 (described in text)
- **Concern** The manuscript does not provide a direct experimental link between the ROS-generating capacity of each complex and its cytotoxic potency. While PdCu shows higher enzyme-mimetic activity and lower IC50 values, this correlation is based on only two data points and could be coincidental. Other factors, such as cellular uptake, intracellular distribution, or differential DNA-binding affinity, could equally explain the observed differences in cytotoxicity.
- **Why it matters** The central claim of the manuscript is that the heterometallic design enables a synergistic dual mechanism. To support this, the authors need to demonstrate that the ROS pathway contributes meaningfully to the overall cytotoxicity, not merely that the complexes possess enzyme-mimetic activity in isolation.
- **Resolution test** The authors should conduct experiments that isolate the contribution of the ROS pathway, such as comparing cytotoxicity under normoxic versus hypoxic conditions, or using ROS scavengers to determine the fraction of cytotoxicity attributable to oxidative stress. Cellular uptake studies would also help rule out alternative explanations for the differential activity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodology and interpretation
- **Claim pointer** The manuscript reports molecular docking results with binding affinities of −8.9 kcal/mol for intercalation and −6.4 kcal/mol for minor groove binding, and interprets these as supporting the experimental DNA-binding findings
- **Evidence pointer** Section 2.5, Figures 8 and 9 (described in text); Section 3.8
- **Concern** The docking methodology is described only briefly. The use of AutoDock Vina with default parameters for a metal-containing fragment is concerning, as force-field parameters for transition metals are not standard in this software and may not accurately represent the coordination chemistry. The choice of PDB structures (4HLI and 1Z3F) and the use of ellipticine as a reference for binding site determination require justification. The relationship between the docking scores and the experimentally determined Kd values is not discussed.
- **Why it matters** Docking results are used to support the proposed DNA-binding mode. If the methodology is not appropriate for metal-containing systems, the conclusions drawn from these calculations may not be reliable. The lack of correlation between docking scores and experimental binding affinities weakens the interpretive value of the computational results.
- **Resolution test** The authors should provide details on how metal parameters were handled in the docking calculations, validate the docking protocol against known DNA-binding structures, and discuss the relationship between the calculated binding energies and the experimentally determined Kd values.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Cell line panel description
- **Evidence pointer** Section 2.2, Section 3.4
- **Issue** The abstract and results section mention three cancer cell lines (colon, A549 lung, and breast), while the Materials and Methods section lists four cancer cell lines (HCT116, A549, SKBR3, and NCI-H1299). The results section does not report data for NCI-H1299.
- **Required correction** Clarify whether NCI-H1299 was tested and, if so, report the results. If not, remove it from the Methods section or explain its inclusion.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Cytotoxicity data
- **Evidence pointer** Section 2.2, Table 1 (described in text)
- **Issue** The manuscript reports IC50 values with standard deviations but does not state the number of independent experiments or the statistical tests used to compare the complexes with cisplatin or with each other. The p-values mentioned for selectivity indices are not accompanied by details of the statistical analysis.
- **Required correction** Provide the number of replicates, the statistical tests used, and the exact p-values for all comparisons. State whether the reported p-values are adjusted for multiple comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** ROS activity quantification
- **Evidence pointer** Section 2.3, Figures 3 and 4 (described in text)
- **Issue** The text describes the ROS activity qualitatively (e.g., "intensity increases significantly," "two orders of magnitude higher") but does not provide quantitative values for the chemiluminescence intensities or the calculated enzyme-mimetic activities. The units and normalization procedures are not described.
- **Required correction** Report quantitative values for the chemiluminescence intensities or derived kinetic parameters, including units and normalization methods. Provide a clear description of how the "orders of magnitude" differences were calculated.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** DNA binding experiments
- **Evidence pointer** Section 3.6
- **Issue** The DNA-binding experiments are described without specifying the buffer composition, ionic strength, or pH for the CD and fluorescence measurements. The DNA concentration is given, but the dye-to-DNA ratios and the range of complex concentrations used in the displacement assays are not stated.
- **Required correction** Provide full experimental conditions for the DNA-binding assays, including buffer composition, pH, dye-to-DNA ratios, and the concentration range of the complexes tested.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Solubility and stability
- **Affected element** Compound behavior in assay media
- **Evidence pointer** Section 2.1, Section 3.4
- **Issue** The manuscript states that UV-Vis spectra were recorded in 1% DMSO/H2O to confirm stability, but the cytotoxicity assays are described as using DMSO as a vehicle. The final DMSO concentration in the cell assays is stated as not exceeding 1.0%, but the solubility and stability of the complexes under the full assay conditions (including cell culture media) are not addressed.
- **Required correction** Discuss the solubility and stability of the complexes in cell culture media at the concentrations used in the cytotoxicity assays. If precipitation or degradation occurs, this should be acknowledged and its potential impact on the results discussed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and discussion
- **Evidence pointer** Section 1, Section 2.2
- **Issue** The introduction cites references on heterometallic complexes and pyrazolate-bridged systems, but the discussion of prior work on PdCo or PdCu complexes with similar biological activity is limited. The claim that this is the "first systematic investigation of the bioactivity of heterometallic pyrazolate-bridged complexes" requires careful qualification, as related systems may have been studied.
- **Required correction** Provide a more comprehensive review of prior work on heterometallic pyrazolate-bridged complexes with biological activity, and qualify the novelty claim accordingly.

## Risk / unsupported claims
- The claim that ROS-mediated oxidative stress is a "complementary cytotoxic pathway" is unsupported by direct cellular evidence; the cell-free enzyme-mimetic assays do not establish that ROS generation occurs in cells or contributes to cytotoxicity.
- The claim that the dissociated [Pd(phen)(µ-dmpz)2] fragment is the DNA-binding species is not experimentally verified; the manuscript does not demonstrate that this fragment forms under physiological conditions or that it is responsible for the observed DNA binding.
- The claim that the difference in cytotoxicity between PdCo and PdCu is "determined by the nature of the partner metal" is an inference based on two complexes and is not supported by systematic variation or mechanistic experiments.
- The molecular docking results are presented as supporting evidence for DNA binding, but the methodology is not validated for metal-containing systems, and the relationship between docking scores and experimental Kd values is not established.
- The selectivity indices reported for PdCo toward SKBR3 cells are based on a single cell line comparison and require validation with additional breast cancer cell lines and normal cell types.
- The manuscript states that PdCu exhibits "peroxidase-like activity (20 times higher than that of PdCo)" in the conclusions, but the results section reports "two orders of magnitude higher" for the same comparison. This numerical discrepancy needs to be resolved.