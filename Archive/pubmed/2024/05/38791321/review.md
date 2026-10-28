## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, materials and methods, and conclusions. No supplementary materials were provided.
- **Assessment boundary** The scientific claims, experimental design, computational methodology, and interpretation of results as presented in the manuscript text. No assessment of editorial quality or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors report the synthesis and characterization of three hesperetin Schiff base Cu(II) complexes, and evaluate their interaction with calf thymus DNA using UV-Vis spectroscopy, thiazole orange displacement assays, DFT calculations, and molecular docking. They claim that intercalative binding is preferred over minor groove binding, that the amido tautomer and S-coordination mode are favored, and that the computational approach can predict binding affinity trends consistent with experimental Kb values.
- **Visible evidence base** Abstract, Sections 1, 2.1.1, 2.1.2, 2.1.3, 2.2.1, 2.2.2, 3.1, 3.2, 3.3, 3.4, and 4. Figures 1-11 and Tables 1-5 are referenced but not visible in the provided text. Supplementary materials are referenced but not provided.
- **Missing materials affecting confidence** Figures 1-11, Tables 1-5, all supplementary materials (Sections S1-S5, Tables S1.1-S4.1, S5.1-S5.34, Figure S1), and the ioChem-BD repository data. Without these, the quantitative results, spectral data, docking scores, and structural coordinates cannot be independently verified.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant topic in bioinorganic chemistry, namely the DNA binding properties of copper(II) Schiff base complexes derived from a natural flavonoid. The combination of experimental spectroscopic methods with DFT and docking calculations is a reasonable approach to characterize the solution speciation and DNA binding mode of these complexes. However, the manuscript has several significant weaknesses. The experimental section is thin, with limited methodological detail and no visible data presentation. The computational work, while potentially valuable, is not sufficiently validated against experimental results, and the docking methodology raises concerns about the interpretation of binding modes. The claim that the computational approach should be recommended for predicting DNA binding is overstated given the limited scope of the validation. The manuscript would benefit from a more critical discussion of the limitations of both the experimental and computational methods, and from a clearer presentation of the data supporting the main conclusions.

- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, medicinal inorganic chemistry, and DNA-targeting drug design would be the primary audience. The work is relevant to those studying copper-based anticancer agents, Schiff base metal complexes, and the application of computational methods to predict DNA binding. The methodological approach, combining DFT speciation analysis with docking, may be of interest to computational chemists working on metal complex-DNA interactions. However, the interest is somewhat limited by the incremental nature of the findings and the lack of novel biological data beyond DNA binding constants.

- **Major strengths**
  1. The combination of experimental and computational methods to address the solution speciation of copper complexes is a commendable approach, as it acknowledges the complexity of these systems in aqueous media.
  2. The consideration of tautomeric forms, enantiomers, and different donor sets in the computational analysis is thorough and demonstrates awareness of the chemical complexity involved.
  3. The comparison of the complexes' binding affinity with known DNA intercalators such as ethidium bromide and thiazole orange provides useful context for evaluating the significance of the measured binding constants.
  4. The manuscript is generally well-written and logically organized, with a clear progression from experimental results to computational analysis and conclusions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the intercalative binding is stronger than minor groove interaction" based on docking results, and that this is "in line with the experimental binding constants, Kb, obtained from the UV-Vis spectroscopy."
- **Evidence pointer** Section 2.2.2, Table 5, Table 1 (not visible)
- **Concern** The docking methodology used to distinguish intercalative versus minor groove binding is not adequately validated. The authors used two different DNA structures (PDB codes 2K4L and 108D) as models for groove and intercalative binding, respectively. This approach is problematic because the two structures are not directly comparable, and the difference in Fitness scores between the two binding modes may reflect differences in the DNA structures themselves rather than genuine binding preferences. Furthermore, the claim that the docking results are "in line with" the experimental Kb values is not substantiated, as the Kb values are not presented in the visible text, and the correlation between docking Fitness scores and experimental binding constants is not quantitatively assessed. The authors should provide a more rigorous validation of the docking approach, such as redocking known intercalators and groove binders to establish a calibration curve, and should present the experimental and computational data side-by-side for direct comparison.
- **Why it matters** The central conclusion of the manuscript, that these complexes bind to DNA via intercalation, rests on the docking results. If the docking methodology cannot reliably distinguish between binding modes, the main conclusion is not supported. This is critical because the experimental data alone (UV-Vis hypochromism and TO displacement) are consistent with but not definitive evidence for intercalation, as groove binding can also cause hypochromism and TO displacement can occur through non-intercalative mechanisms.
- **Resolution test** The authors should validate their docking protocol by docking a series of known intercalators and minor groove binders into both DNA structures and demonstrating that the Fitness scores correctly discriminate between the two binding modes. They should also provide a quantitative comparison between the docking Fitness scores and the experimental Kb values, including a statistical analysis of the correlation. If such validation is not possible, the claims about binding mode preference should be substantially softened.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DFT calculations demonstrate that "the amido and not imido tautomer of HHSB, HIN, and HTSC binds CuII ion" and that the coordination mode of HTSC is "(O−, N, S) and not (O−, N, NH2)."
- **Evidence pointer** Section 2.2.1, Equations 2-4, Table 3 (not visible)
- **Concern** The DFT calculations are used to draw definitive conclusions about the tautomeric form and coordination mode of the complexes in solution. However, the free energy differences reported (2.0, 7.8, 2.1, and 9.3 kcal/mol for various equilibria) are relatively small, and the accuracy of DFT for such transition metal complexes is known to be limited, particularly with the B3LYP functional. The authors do not report any benchmarking of their computational protocol against known experimental data for similar systems, nor do they discuss the potential errors associated with their methodology. Additionally, the claim that the imido tautomer can be "excluded" based on a free energy difference of 7.8 kcal/mol is too strong, as this corresponds to an equilibrium constant of approximately 5 x 10^5, which means a small but non-negligible fraction of the imido form could still be present. The authors should acknowledge the limitations of their computational approach and temper their conclusions accordingly.
- **Why it matters** The identification of the active species in solution is crucial for understanding which complex interacts with DNA. If the DFT predictions are incorrect, the docking calculations may have been performed on the wrong species, invalidating the binding mode conclusions. The overstatement of computational certainty could mislead readers who are not specialists in computational chemistry.
- **Resolution test** The authors should benchmark their DFT protocol against experimentally characterized copper complexes with known tautomeric preferences and coordination modes. They should also report the computed free energy differences with error estimates, and discuss the sensitivity of their conclusions to the choice of functional, basis set, and solvation model. If the imido tautomer or N-coordination mode cannot be definitively excluded, these species should be included in the docking calculations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the synthesis and characterization of the CuHHSB complex have been presented in ref. [65], while the synthesis and description of the complexes CuHIN and CuHTSC were reported in ref. [66]."
- **Evidence pointer** Section 3.1
- **Concern** The manuscript relies entirely on previous publications for the synthesis and characterization of the three copper complexes under study. While this is acceptable practice, it means that the current manuscript does not provide any independent evidence of the identity and purity of the complexes used in the DNA binding studies. The authors do not report any characterization data (e.g., elemental analysis, mass spectrometry, IR, EPR) in the current manuscript to confirm that the complexes used in the DNA binding experiments are indeed the expected species. This is particularly concerning given that the manuscript emphasizes the importance of speciation in solution, and the authors themselves note that multiple species can coexist. Without confirming the identity of the complexes in the conditions used for the DNA binding studies, the interpretation of the experimental results is uncertain.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publication. If the complexes are not fully characterized in the conditions of the DNA binding experiments, other researchers cannot reproduce the work or build upon it. Moreover, if the complexes undergo hydrolysis or ligand exchange under the experimental conditions, the measured binding constants may not reflect the properties of the intended complexes.
- **Resolution test** The authors should provide characterization data for the complexes under the conditions used in the DNA binding studies (e.g., UV-Vis spectra in Tris buffer, EPR spectra, or mass spectrometry). At minimum, they should confirm that the complexes are stable under the experimental conditions and that no significant hydrolysis or ligand exchange occurs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "when different donor sets for the ligands, isomers, enantiomers, and tautomers for the metal complexes are possible, a computational approach should be recommended to predict the type and strength of binding to DNA, and in general, to macromolecules."
- **Evidence pointer** Section 4
- **Concern** This general conclusion is not supported by the data presented. The study examines only three related complexes with a single DNA sequence (calf thymus DNA), and the computational predictions are validated against only one experimental observable (Kb values from UV-Vis). The claim that a computational approach "should be recommended" for predicting DNA binding in general is an overgeneralization from a limited case study. The authors do not demonstrate that their approach works for other types of metal complexes, other DNA sequences, or other binding modes. Furthermore, the docking method used (GOLD with GoldScore) has known limitations for metal complexes, and the authors do not discuss these limitations or compare their approach to alternative methods.
- **Why it matters** Overstated conclusions can mislead other researchers into applying methods that are not adequately validated, potentially leading to incorrect results in their own work. The scientific community benefits from measured, well-supported conclusions that accurately reflect the scope and limitations of a study.
- **Resolution test** The authors should either provide additional validation data demonstrating the general applicability of their approach, or substantially temper their conclusion to reflect the specific scope of their study. For example, they could state that their approach "may be useful" for predicting DNA binding in similar systems, rather than making a general recommendation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1.2, Equation 1
- **Evidence pointer** Equation 1
- **Issue** The Benesi-Hildebrand equation (Equation 1) is presented without derivation or explanation of its applicability to this system. The authors do not discuss the assumptions underlying this equation, such as the formation of a 1:1 complex and the requirement that the concentration of DNA be much greater than that of the compound.
- **Required correction** Add a brief explanation of the equation and its assumptions, or provide a reference where this is discussed in detail.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.1.3, Table 2
- **Evidence pointer** Table 2 (not visible)
- **Issue** The authors report Stern-Volmer quenching constants (KSV) and apparent binding constants (Kapp) from the TO displacement assay, but do not discuss the limitations of this method. The TO displacement assay is an indirect method that can overestimate binding affinity if the compound quenches fluorescence through mechanisms other than displacement, such as energy transfer or collisional quenching.
- **Required correction** Add a discussion of the limitations of the TO displacement assay and consider whether the inner filter correction adequately accounts for all potential artifacts.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.2.2, Figure 11
- **Evidence pointer** Figure 11 (not visible)
- **Issue** The authors describe a "multistep process" for DNA adduct formation, with minor groove binding as the first step followed by evolution to the intercalated adduct. This is presented as a conclusion, but it appears to be a hypothesis based on the docking results. The experimental data do not provide evidence for this kinetic or mechanistic pathway.
- **Required correction** Clearly distinguish between the docking-based hypothesis and experimentally supported conclusions. If this is a hypothesis, it should be presented as such.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1.2, Figure 5
- **Evidence pointer** Figure 5 (not visible)
- **Issue** The authors state that "a linear correlation was found between the values of the Kb binding constants and the DNA double strain breaks (DNA-DSBs)" for the complexes but not for the ligands. This is an interesting observation, but the authors do not provide the correlation coefficient, the number of data points, or a statistical significance test. Without this information, the strength of the correlation cannot be assessed.
- **Required correction** Report the correlation coefficient, p-value, and number of data points for the linear correlation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The DFT calculations use the B3LYP functional with Grimme's D3 correction. While this is a reasonable choice, the authors do not justify this choice or discuss its limitations for copper complexes. B3LYP is known to have issues with transition metal systems, particularly regarding the description of electron correlation and spin states.
- **Required correction** Add a brief justification for the choice of functional and a discussion of its known limitations for copper complexes, or cite benchmark studies that validate this choice for similar systems.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1.2, Table 1
- **Evidence pointer** Table 1 (not visible)
- **Issue** The authors compare their Kb values with those of "other copper-based compounds" from the literature, but the comparison is not systematic. The cited references cover a wide range of experimental conditions, and the authors do not discuss how differences in ionic strength, pH, temperature, or DNA sequence might affect the comparison.
- **Required correction** Provide a more careful comparison, noting the experimental conditions of the cited studies and discussing potential sources of variation.

## Risk / unsupported claims

1. The claim that "the intercalative binding is stronger than minor groove interaction" is not supported by the visible evidence, as the docking results are not validated and the experimental data are not presented in a way that allows direct comparison.
2. The claim that the computational approach "should be recommended" for predicting DNA binding is an overgeneralization not supported by the limited scope of the study.
3. The claim that the imido tautomer and N-coordination mode can be "excluded" based on DFT calculations is too strong given the known limitations of DFT for such systems and the relatively small free energy differences.
4. The statement that "the values found for CuII complexes... were higher than other copper-based compounds" is not fully supported, as the comparison is not systematic and the experimental conditions of the cited studies are not discussed.
5. The claim that "the results suggest that when different enantiomers, tautomers, and donor sets are possible for a metal complex, a computational approach should be recommended" is not supported by the data, as the study does not demonstrate the predictive power of the computational approach across a range of systems.
6. The assertion that the TO displacement assay results indicate intercalation is not definitive, as TO displacement can occur through other mechanisms, and the authors do not rule out alternative explanations.
7. The statement that "the extent of the aromaticity seems to play a major role in binding stabilization" is based on only three complexes and is not supported by a systematic structure-activity analysis.