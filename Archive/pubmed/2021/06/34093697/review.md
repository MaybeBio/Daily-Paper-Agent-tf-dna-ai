## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report the synthesis and characterization of two ruthenium(II) diimine complexes, one bishomoleptic [Ru(bpy)2(2,2′-pq)](PF6)2 (1) and one trisheteroleptic [Ru(bpy)(phen)(2,2′-pq)](PF6)2 (2), where 2,2′-pq is 2-(2′-pyridyl)-quinoxaline. They characterize these complexes by multiple analytical techniques including single-crystal X-ray diffraction, investigate their interaction with calf thymus DNA using spectroscopic methods and molecular docking, and evaluate their anticancer activity against MCF-7 and HEK-293 cell lines.
- **Visible evidence base** Abstract, full introduction, experimental section (synthesis, electrochemistry, X-ray crystallography, DNA-binding methods, cytotoxicity, docking), results and discussion sections, conclusions, data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables (Figures S1, S3-S6, Table S1), detailed DNA-binding methodology, full molecular docking parameters and output files, crystallographic data tables (CIF files), raw spectra, cell viability data plots, confocal microscopy images

## Reviewer

- **Overall assessment** This manuscript describes a straightforward extension of well-established ruthenium polypyridyl chemistry to a ligand system, 2-(2′-pyridyl)-quinoxaline, that has been previously explored in related metal complexes. The synthetic work appears competent, and the characterization is reasonably thorough. However, the scientific advance over existing literature is incremental. The DNA-binding studies are limited to complex 2 for most experiments, despite the title and abstract implying comparative studies of both complexes. The cytotoxicity data are presented with minimal statistical detail, and the molecular docking studies are described at a level that makes independent assessment difficult. The manuscript would benefit from a clearer articulation of the novelty and from more rigorous quantitative analysis throughout.
- **Who would be interested in the results, and why** Researchers working in the field of ruthenium-based anticancer agents and metal-DNA interactions may find the comparative data on the bishomoleptic versus trisheteroleptic complexes of some interest. The study provides a useful data point for structure-activity relationships in Ru-diimine systems, particularly regarding the role of the phenanthroline ligand in modulating DNA affinity and cellular uptake. The crystallographic data for both complexes may be of value to coordination chemists.
- **Major strengths** The manuscript presents a clean synthetic route to both complexes with good yields and full characterization including single-crystal X-ray structures. The electrochemical analysis provides a clear rationale for the observed differences in reduction potentials between the two complexes. The DNA-binding studies employ multiple complementary techniques, and the consistency between spectroscopic results, viscosity measurements, and docking studies strengthens the conclusion of minor groove binding. The cytotoxicity data showing selectivity for cancer cells over healthy cells is a potentially useful finding.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract and introduction state that "various spectroscopic techniques were employed to investigate the interaction of both complexes with calf thymus DNA" and that "both complexes, 1 and 2, bind with DNA via a minor groove mode of binding."
- **Evidence pointer** Section 2.3, Section 3.5, Figures 4-8
- **Concern** The experimental section (Section 2.3) explicitly states that DNA-binding studies were performed for complex 2 only. The results section describes CD experiments, absorption titration, viscosity measurements, and EB displacement assays, but the text consistently refers to complex 2 alone. The competitive EB studies appear to include both complexes (Figure 7, Figure S3 for 1), but the other experiments are described for complex 2 only. The claim that both complexes bind via minor groove mode is therefore not supported by the presented data for complex 1.
- **Why it matters** The title and abstract promise a comparative study of both complexes. If the DNA-binding mode of complex 1 is inferred only from docking or from prior literature, this must be stated explicitly. As written, the manuscript overstates the experimental evidence.
- **Resolution test** The authors should either present the full DNA-binding dataset for complex 1 (CD, absorption titration, viscosity) or revise the claims to state that the detailed experimental DNA-binding analysis was performed for complex 2, with complex 1 studied only by EB displacement and docking.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript reports IC50 values for both complexes against MCF-7 and HEK-293 cell lines, with complex 2 showing activity "almost equal to cis-platin" (IC50 = 6.2 ± 1.2 µM for 2 versus 5.19 ± 0.8 µM for cis-platin).
- **Evidence pointer** Section 3.5.5, Table 7
- **Concern** The cytotoxicity data are presented as a single table with IC50 values and standard deviations, but no information is provided on the number of independent experiments, the number of replicates per concentration, the concentration range tested, the duration of exposure, or the statistical methods used to calculate IC50 values. The claim that both complexes "cause almost no apoptosis to HEK-293" is presented without quantitative data or statistical comparison. The statement in the conclusions that complex 2 has "better activity than 1 and cis-platin" is not supported by the data shown, since the IC50 for 2 (6.2 µM) is slightly higher than that for cis-platin (5.19 µM), and no statistical test is reported.
- **Why it matters** Cytotoxicity data are central to the claim that these complexes are "promising antitumor agents." Without proper experimental detail and statistical analysis, the reliability and significance of these results cannot be assessed.
- **Resolution test** Provide full experimental details for the MTT assay, including number of replicates, concentration ranges, exposure times, and statistical analysis. Report whether the difference between complex 2 and cis-platin is statistically significant. Provide dose-response curves.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "molecular docking studies were performed in order to identify the most preferable binding site on the biomolecule, assuming that DNA and ruthenium complexes are rigid" and reports binding energies of -7.33, -7.18, -7.03, and -6.76 kcal/mol for various complex-DNA interactions.
- **Evidence pointer** Section 3.5.6, Table 8, Figures 10-12, Figures S4-S6
- **Concern** The docking methodology is described only in the Supplementary Information, which was not provided for review. The description in the main text is insufficient to evaluate the validity of the docking results. Key parameters such as the docking algorithm, grid box dimensions, number of runs, scoring function, and treatment of the metal center are not stated. The assumption of rigidity for both DNA and the metal complex is a significant simplification that may not be appropriate for these flexible systems. The claim that docking results "confirm" the experimental binding mode is overstated given these limitations.
- **Why it matters** Molecular docking is used as corroborating evidence for the binding mode. If the methodology is not transparent or is inappropriate, the conclusions drawn from it are weakened.
- **Resolution test** Provide the full docking methodology in the main text or ensure the Supplementary Information contains sufficient detail for replication. Discuss the limitations of the rigid-body assumption and justify the choice of DNA sequences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The introduction states that "trisheteroleptic diimine Ru complexes for bioinorganic chemistry applications are quite scarce in the literature" and positions the work as addressing this gap.
- **Evidence pointer** Section 1, Introduction
- **Concern** The novelty of the trisheteroleptic complex is presented as a key motivation, but the manuscript does not clearly articulate what specific advantage or new property the trisheteroleptic architecture confers compared to the bishomoleptic analogue. The differences observed in DNA binding and cytotoxicity are modest and are attributed to the phen ligand's hydrophobicity, which is a well-known effect. The study would be strengthened by a more explicit discussion of what new insight is gained.
- **Why it matters** For a field as mature as Ru-diimine anticancer chemistry, the incremental advance must be clearly defined. Without this, the significance of the work is diminished.
- **Resolution test** Add a paragraph in the discussion that explicitly compares the properties of 1 and 2 and articulates what the trisheteroleptic design offers that the bishomoleptic does not.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "both complexes, 1 and 2, bind with DNA via a minor groove mode of binding" but the experimental section only describes DNA-binding studies for complex 2. This overstatement should be corrected.
- **Required correction** Revise the abstract to accurately reflect which experiments were performed for which complex.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.5.2
- **Evidence pointer** Section 3.5.2, Figure 5
- **Issue** The absorption titration data are described as showing "hyperchromism with a very slight blue shift," but the binding constant Kb is calculated from the plot of (DNA)/(εa-εf) vs. (DNA). The manuscript does not state the wavelength at which the binding constant was calculated or whether the data were corrected for the intrinsic absorbance of DNA.
- **Required correction** Specify the wavelength used for Kb calculation and describe any corrections applied.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.5.4
- **Evidence pointer** Section 3.5.4, Equation 2
- **Issue** The Stern-Volmer equation is presented with Ksv values of 0.87 M-1 and 0.96 M-1 for complexes 1 and 2, respectively. These values are unusually low for a quenching process and the units appear inconsistent with the equation as written, where the quencher concentration is expressed as a ratio r = (complex)/(DNA) rather than a molar concentration.
- **Required correction** Clarify the units and the meaning of the Ksv values in the context of the ratio-based Stern-Volmer plot.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.4, Table 4
- **Evidence pointer** Section 3.4, Table 4
- **Issue** The crystal structures are described, and selected bond distances are given, but no comparison is made to related Ru-diimine complexes in the literature. The claim that the elongated M-Nquinoxaline bond is due to "less σ-donating ability" would benefit from a quantitative comparison.
- **Required correction** Add a brief comparison of bond distances with literature values for related complexes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 3.5.5
- **Evidence pointer** Section 3.5.5, Figure 9
- **Issue** The confocal microscopy images are described qualitatively. No quantitative analysis of cellular uptake is provided, and the statement that complex 2 "internalizes more efficiently in MCF-7 than in HEK-293" is not supported by quantitative data.
- **Required correction** Provide quantitative fluorescence intensity measurements or state that the observation is qualitative.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1, Scheme 2
- **Issue** The synthetic route to the trisheteroleptic complex involves an intermediate cis-[Ru(bpy)(phen)Cl2] whose preparation is described only in the Supplementary Information. The main text should provide at least a brief description of this intermediate.
- **Required correction** Add a sentence describing the preparation of the intermediate or reference the Supplementary Information more explicitly.

## Risk / unsupported claims
- The claim that "both complexes, 1 and 2, bind with DNA via a minor groove mode of binding" is not fully supported by the experimental data presented, as the detailed DNA-binding studies were performed for complex 2 only.
- The statement in the conclusions that complex 2 has "better activity than 1 and cis-platin" is not supported by the IC50 values presented, which show 2 (6.2 µM) to be slightly less potent than cis-platin (5.19 µM), and no statistical analysis is provided.
- The claim that "both complexes cause almost no apoptosis to HEK-293" is presented without quantitative data or statistical comparison.
- The molecular docking results are described as "confirming" the experimental binding mode, but the methodology is not fully described in the provided material, making this claim difficult to evaluate.
- The assertion that the trisheteroleptic complex "localizes in the nucleus" of MCF-7 cells is based on qualitative confocal microscopy observations without quantitative support.
- The statement that the complexes are "promising antitumor agents" is an extrapolation from in vitro data on a single cancer cell line and requires more extensive biological evaluation to be substantiated.