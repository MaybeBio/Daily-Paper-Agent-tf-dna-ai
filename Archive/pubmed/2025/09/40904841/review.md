## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, experimental, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors report synthesis and characterization of ten novel cyclopropyl-linked guanidine derivatives (7a–j), evaluate their DNA-binding via UV-Vis spectroscopy, and support findings with molecular docking, DFT calculations, and ADMET predictions. Compound 7i is claimed as the best binder with Kb = 3.49 × 10^5 M^-1, comparable to cabozantinib.
- **Visible evidence base** Abstract, introduction, results and discussion (chemistry, DNA binding, DFT, docking, SAR, ADMET), experimental protocols, conclusions
- **Missing materials affecting confidence** Supplementary figures (Fig. S31), full spectra for all compounds, raw UV-Vis titration data, docking pose images, complete DFT output tables, ADMET raw predictions, purity/characterization data for all compounds beyond representative example 7a

## Reviewer
- **Overall assessment** The manuscript presents a straightforward synthesis and characterization study of guanidine derivatives with preliminary DNA-binding evaluation. The experimental design is conventional and the data interpretation is largely consistent with the presented results. However, several technical concerns regarding data completeness, methodological rigor, and overinterpretation of computational results limit the strength of the conclusions. The claim of "mechanistic scaffolds" is not fully supported by the evidence provided, as only one experimental technique (UV-Vis) is used for DNA-binding assessment and no biological activity data are presented.
- **Who would be interested in the results, and why** Medicinal chemists and researchers in anticancer drug discovery, particularly those focused on DNA-targeting small molecules and guanidine-containing pharmacophores. The synthetic methodology and preliminary biophysical characterization may be of interest to groups working on minor groove binders.
- **Major strengths** 1) Novel scaffold combining cyclopropyl and guanidine moieties, which is underexplored in DNA-binding studies. 2) Systematic SAR analysis correlating substituent effects with binding affinity. 3) Integration of experimental and computational approaches. 4) Clear synthetic protocols with reasonable yields reported.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (single-technique binding assessment), R1-M2 (incomplete characterization data), R1-M3 (docking methodology concerns), R1-M4 (overinterpretation of DFT and ADMET)
- **Assessment against Nature-style criteria** Originality: Moderate. The scaffold is novel but the approach (synthesis plus UV-Vis binding plus docking) is routine. Scientific importance: Limited. No biological activity data, no selectivity studies, and the binding affinities are modest. Interdisciplinary readership: Narrow. Primarily of interest to medicinal chemists; limited broader appeal. Technical soundness: Partially adequate. Synthetic chemistry appears sound, but biophysical characterization is incomplete and computational methods have limitations. Readability for nonspecialists: Acceptable. The manuscript is clearly written, though some sections assume familiarity with computational chemistry terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core claim that these compounds are "mechanistic scaffolds for anticancer agents" requires additional experimental validation, particularly biological activity data and more rigorous DNA-binding characterization.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence
- **Claim pointer** "Their DNA-binding potential was assessed through electronic absorption spectroscopy, revealing characteristic hypochromic shifts indicative of minor groove-binding interactions with salmon sperm DNA (SS-DNA)."
- **Evidence pointer** DNA binding studies section, Table 1, Fig. S31
- **Concern** The DNA-binding mode is concluded solely from UV-Vis spectroscopy. Hypochromism without significant red shift is interpreted as groove binding, but this is an indirect inference. No competitive displacement assays (e.g., with Hoechst 33258 or methyl green), circular dichroism, viscosity measurements, or thermal denaturation studies are presented to corroborate the binding mode. Additionally, the claim of "minor groove" binding specifically is not justified by the data presented, as hypochromism can also result from electrostatic interactions or partial intercalation.
- **Why it matters** The central mechanistic claim of the manuscript depends on establishing the DNA-binding mode. Without orthogonal experimental techniques, the conclusion that these compounds are minor groove binders is not rigorously supported. This weakens the entire premise of the study.
- **Resolution test** Provide additional biophysical evidence such as competitive displacement assays, CD spectroscopy, viscosity measurements, or DNA melting studies. Alternatively, temper the claims to state that groove binding is "suggested" rather than "confirmed."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data completeness
- **Claim pointer** "The structural characterization for synthesized compounds (7a–j) was carried out through different spectroscopic techniques i.e. FTIR and NMR."
- **Evidence pointer** Chemistry section, experimental section
- **Concern** Only compound 7a is discussed in detail for characterization. Full characterization data (FTIR, 1H NMR, 13C NMR, elemental analysis) for compounds 7b–j are not presented in the main text. While supplementary material is mentioned, the manuscript should include at least a summary table of key characterization data for all compounds. Additionally, no mass spectrometry data or melting points are reported for most compounds.
- **Why it matters** The identity and purity of all synthesized compounds must be established for the study to be reproducible and for structure-activity relationships to be meaningful. Incomplete characterization data undermines confidence in the reported results.
- **Resolution test** Include a comprehensive characterization table for all compounds 7a–j in the main text or clearly reference specific supplementary tables with complete data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational methodology
- **Claim pointer** "Molecular docking studies further supported these experimental findings, with compound (7i) displaying a favorable docking score of −8.9 kcal mol−1 and forming hydrogen bonding and hydrophobic interactions within the DNA minor groove."
- **Evidence pointer** Molecular docking section, Table 4, Fig. 6
- **Concern** The docking methodology is described only briefly. Key details are missing: the specific DNA structure used (PDB ID 3EY0 is mentioned, but the sequence and conformation should be described), the grid box dimensions and coordinates, the exhaustiveness parameter, and the validation approach. The manuscript states that AutoDock Vina was used, but no information is provided about how the docking protocol was validated (e.g., redocking of co-crystallized ligands). Furthermore, the correlation between docking scores and experimental Kb values is presented as supportive, but the statistical significance of this correlation is not assessed.
- **Why it matters** Docking results are used to support the experimental findings and to rationalize SAR. Without proper methodological detail and validation, the computational results cannot be evaluated for reliability, and the claimed correlation may be coincidental.
- **Resolution test** Provide complete docking parameters, describe the DNA structure preparation, include a validation step (e.g., redocking a known binder), and report statistical measures for the correlation between docking scores and experimental binding constants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of computational results
- **Claim pointer** "DFT calculations and ADMET predictions provided insights into the electronic features and pharmacokinetic attributes of novel guanidine derivatives (7a–j), establishing DNA binding as a mechanistic foundation and reinforcing their rationale for future evaluation in anticancer drug discovery."
- **Evidence pointer** DFT section, ADMET section, Table 3, Table 5, Figs. 3-5, 8
- **Concern** The DFT analysis reports global reactivity parameters (HOMO, LUMO, energy gap, etc.) but does not establish a clear link between these parameters and the observed DNA-binding affinities. The correlation analysis (Fig. 5) shows moderate correlations, but the interpretation is largely qualitative. Similarly, ADMET predictions are presented as favorable, but the manuscript acknowledges toxicity risks (AMES positive for some compounds) without discussing how these would be addressed in the context of the "anticancer agent" claim. The statement that these computational results "establish DNA binding as a mechanistic foundation" overstates what can be concluded from in silico predictions alone.
- **Why it matters** Overinterpretation of computational results can mislead readers about the strength of the evidence. The manuscript should clearly distinguish between hypothesis-generating computational predictions and experimentally validated findings.
- **Resolution test** Reframe the conclusions to acknowledge that DFT and ADMET results are predictive and require experimental validation. Discuss the implications of predicted toxicity more critically.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** DNA binding studies
- **Evidence pointer** DNA binding studies section
- **Issue** The UV-Vis titration experiments were performed in duplicate (n = 2), which is a very small sample size for reporting binding constants with standard errors. The manuscript reports Kb values with SEM, but the reliability of these measurements is questionable with only two replicates.
- **Required correction** Increase the number of replicates (at least n = 3) or acknowledge the limitation of duplicate measurements in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The binding constants are reported with units of M^-1, but the precision of the reported values (e.g., 3.49 × 10^5 ± 0.04 M^-1) implies a level of accuracy that may not be justified given the experimental approach. The error value of 0.04 × 10^5 M^-1 seems small for UV-Vis titration data.
- **Required correction** Report binding constants with appropriate significant figures and discuss the sources of error in the measurements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction cites general references for cancer and DNA-binding agents but does not provide a focused review of recent guanidine-based DNA binders or minor groove binders. This limits the ability to assess the novelty of the present work in context.
- **Required correction** Add a brief discussion of recent related work on guanidine-based DNA-binding agents and clearly state the specific gap this study addresses.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental section
- **Evidence pointer** DNA binding protocol
- **Issue** The DNA binding protocol states that experiments were performed in duplicate, but the buffer conditions, ionic strength, and temperature are not specified. These parameters significantly affect DNA-binding measurements.
- **Required correction** Provide complete experimental conditions including buffer composition, pH, temperature, and incubation time.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** SAR analysis
- **Evidence pointer** SAR section, Fig. 7
- **Issue** The SAR analysis is based on a small series of compounds with multiple simultaneous structural variations. It is difficult to attribute observed differences in binding affinity to specific substituent effects without systematic variation.
- **Required correction** Acknowledge the limitations of the SAR analysis given the limited compound set and suggest that more systematic structural variation is needed to draw definitive conclusions.

## Risk / unsupported claims
- The claim that these compounds are "mechanistic scaffolds for anticancer agents" is not supported by any biological activity data (no cytotoxicity, no antiproliferative assays, no selectivity studies).
- The specific claim of "minor groove-binding" is not rigorously established, as only UV-Vis spectroscopy was used and the interpretation is indirect.
- The statement that DFT calculations and ADMET predictions "establish DNA binding as a mechanistic foundation" overstates the role of computational predictions.
- The comparison of compound 7i to cabozantinib as a "reference groove binder" is presented without experimental comparison under identical conditions.
- The claim that the cyclopropyl-linked guanidine scaffold is "novel" and "has not been previously reported" cannot be fully verified from the provided material, as the literature search is not comprehensive.
- The correlation between docking scores and experimental Kb values is presented as supportive evidence, but the statistical significance and robustness of this correlation are not established.