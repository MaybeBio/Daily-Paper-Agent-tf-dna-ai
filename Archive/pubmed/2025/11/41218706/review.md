## Review setup
- **Input scope** Full manuscript text including graphical abstract, introduction, materials and methods, results and discussion, conclusion, ethical approval, declaration of competing interest, supplementary data note, and acknowledgements.
- **Assessment boundary** Scientific content, methodological soundness, data interpretation, and internal consistency of the reported findings. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors report that two types of carbon dots (CDs), Y15-CDs and B-CDs, with positive and negative surface charges respectively, bind to DNA through distinct mechanisms. Y15-CDs bind via intercalation and groove binding, while B-CDs bind primarily via groove binding. The authors further claim that Y15-CDs induce S-phase cell cycle arrest, DNA damage, and growth inhibition in zebrafish embryos, whereas B-CDs do not. The study combines experimental assays (competitive displacement, circular dichroism) with computational methods (molecular docking, MD simulations, MMPBSA) and in vitro/in vivo models.
- **Visible evidence base** Figures 1-10, Figure S1-S7, Table S1, and text descriptions of all experimental procedures and results.
- **Missing materials affecting confidence** Raw numerical data for fluorescence intensities, cell cycle percentages, survival rates, and morphometric measurements are not provided. Statistical details (number of replicates, error bar definitions, exact p-values) are incomplete. The supplementary data file is referenced but not accessible for review. Details of MD simulation parameters, force field choices, and convergence criteria are not fully described.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely question in nanomedicine: whether carbon dots can directly bind DNA and thereby influence the cell cycle. The combination of experimental and computational approaches is commendable and appropriate for the research question. However, several technical concerns limit the strength of the conclusions. The competitive displacement assays show modest effects, the circular dichroism data are described qualitatively without quantitative analysis, and the link between DNA binding affinity and cell cycle arrest is inferred rather than mechanistically demonstrated. The zebrafish experiments are descriptive and lack robust statistical reporting. The computational models, while useful, rely on simplified representations of CDs that may not fully capture their heterogeneous nature. The manuscript would benefit from additional controls, quantitative analyses, and a more cautious interpretation of the causal relationship between DNA binding and observed biological effects.
- **Who would be interested in the results, and why** Researchers in nanomedicine, particularly those working on carbon-based nanomaterials for cancer therapy, would find this study relevant. The work also speaks to the broader community investigating nanoparticle-nucleic acid interactions and the design of nucleus-targeting therapeutic agents. The comparative analysis of positively and negatively charged CDs provides useful structure-property relationships that could inform future materials design.
- **Major strengths** The study combines multiple complementary techniques to characterize DNA binding, which strengthens the internal validity of the binding mode assignments. The use of both in vitro (U2OS cells) and in vivo (zebrafish) models provides a breadth of evidence. The computational work adds molecular-level insight that is often missing in CD-DNA interaction studies. The choice of two CDs with contrasting surface charges is a logical experimental design that allows for meaningful comparison.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of DNA binding assays
- **Claim pointer** The authors claim that Y15-CDs bind DNA via intercalation and groove binding, while B-CDs bind via groove binding, based on competitive displacement assays and circular dichroism.
- **Evidence pointer** Figure 3, Figure 4, Results section "Competitive displacement studies" and "Circular dichroism studies"
- **Concern** The competitive displacement assays show fluorescence quenching of 30.6% for Y15-CDs with EB, 51% with DAPI, and 56% with MG at the highest concentration tested. These values indicate partial displacement, not complete displacement, and the interpretation assumes that quenching is solely due to displacement. However, CDs themselves can quench fluorophore fluorescence through inner filter effects, static quenching, or Förster resonance energy transfer, independent of DNA binding. No control experiments are described to account for direct quenching of EB, DAPI, or MG fluorescence by the CDs in the absence of DNA. Additionally, the circular dichroism data are described only qualitatively ("slight decrease", "significant perturbations") without quantitative analysis of molar ellipticity changes or calculation of binding constants. The concentration ranges used in the CD experiments are not stated.
- **Why it matters** The central claim of the manuscript rests on the correct assignment of DNA binding modes. If the observed fluorescence changes are partly or wholly due to non-specific quenching rather than displacement, the binding mode assignments would be incorrect. Without quantitative CD analysis, the structural interpretation is not supported by the data.
- **Resolution test** Provide control experiments showing the effect of CDs on the fluorescence of EB, DAPI, and MG in the absence of DNA. Include quantitative analysis of CD spectra (e.g., changes in molar ellipticity at characteristic wavelengths) with appropriate statistical treatment. State the concentration ranges used and demonstrate that the observed effects are concentration-dependent in a manner consistent with binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link between DNA binding and cell cycle arrest
- **Claim pointer** The authors claim that Y15-CDs induce S-phase arrest and DNA damage in U2OS cells, and that this is due to their DNA binding ability.
- **Evidence pointer** Figure 7D-F, Figure 8, Figure S3-S6, Results section "Cell cycle analysis" and "DNA damage detection"
- **Concern** The manuscript establishes that Y15-CDs bind DNA in vitro and that they cause S-phase arrest and DNA damage in cells. However, no experiment directly links these two observations. The Y15-CDs contain Y15, which the authors note is a focal adhesion kinase inhibitor. This small molecule itself could be responsible for the observed cell cycle effects, independent of the CD-DNA interaction. The authors acknowledge this possibility in the discussion but do not provide control experiments with free Y15 or with Y15-CDs that lack DNA binding ability. Furthermore, the DNA damage detection relies solely on γH2AX staining, which is a sensitive but non-specific marker. No assessment of cell viability under the exact conditions of the cell cycle analysis is provided, and the relationship between the concentrations used for cytotoxicity (Figure 7C) and those used for cell cycle analysis is not clearly stated.
- **Why it matters** The manuscript's title and central thesis claim that DNA binding mechanisms affect cell cycle arrest. Without direct evidence that the DNA binding is the causative factor, the conclusion is not established. The presence of Y15, a known bioactive molecule, confounds the interpretation.
- **Resolution test** Include experiments with free Y15 at equivalent concentrations to determine its contribution to cell cycle arrest and DNA damage. Alternatively, use a control CD that does not bind DNA but has similar surface properties. Provide additional DNA damage markers (e.g., comet assay, 53BP1 foci) and demonstrate that the observed effects are dependent on the DNA binding ability of the CDs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and data reporting
- **Claim pointer** The authors report quantitative differences in cell cycle distribution, survival rates, and morphometric parameters between treatment groups.
- **Evidence pointer** Figure 7C-F, Figure 9D-E, Figure 10B-D, Figure S5-S6
- **Concern** The statistical reporting is incomplete. The number of independent replicates for each experiment is not stated. Error bars are shown in figures but their definition (standard deviation, standard error, confidence interval) is not provided in the figure legends or methods. The statistical test used is mentioned only for the zebrafish morphometry (one-way ANOVA), but not for the cell cycle analysis, cytotoxicity, or γH2AX quantification. Exact p-values are not reported; only asterisks are used. For the zebrafish survival curves, no statistical comparison between groups is described. The sample sizes for zebrafish experiments are not stated.
- **Why it matters** The conclusions regarding differential effects of Y15-CDs versus B-CDs depend on the reliability of the quantitative comparisons. Without proper statistical reporting, the reader cannot assess the robustness of the findings.
- **Resolution test** Provide complete statistical details for all quantitative experiments: number of replicates, error bar definitions, statistical tests used, and exact p-values. For survival data, provide appropriate survival analysis with hazard ratios or log-rank tests.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational model validity
- **Claim pointer** The authors claim that molecular docking and MD simulations support the experimental binding mode assignments and provide binding free energy values.
- **Evidence pointer** Figure 5, Figure 6, Table S1, Results section "Modeling of CDs-DNA interactions"
- **Concern** The computational models of CDs are simplified representations. B-CDs are modeled as graphene-like layers with carboxyl groups, and Y15-CDs as structures with benzenetetramine groups. Real CDs are heterogeneous mixtures with varied sizes, shapes, and surface chemistries. The manuscript does not describe how the model structures were validated against experimental characterization data beyond size and zeta potential. The force field parameters for the CD models are not described. The MMPBSA calculations are mentioned but the methodological details (e.g., number of frames used, entropy contributions, dielectric constants) are not provided. The RMSD values are reported in Table S1 but not discussed in the text.
- **Why it matters** The computational results are used to support the experimental binding mode assignments. If the models are not representative of the actual CDs, the computational conclusions may not be applicable. The lack of methodological detail prevents assessment of the reliability of the binding free energy calculations.
- **Resolution test** Provide full details of the computational methodology, including force field parameters, simulation length, equilibration criteria, and MMPBSA calculation parameters. Validate the CD models against experimental data (e.g., elemental analysis, XPS, NMR). Discuss the limitations of the simplified models in the text.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Zebrafish developmental study interpretation
- **Claim pointer** The authors claim that Y15-CDs inhibit the growth of zebrafish embryos, as evidenced by reduced body length, eye size, and head size, and that this is due to cell cycle arrest.
- **Evidence pointer** Figure 9, Figure 10, Results section "Zebrafish embryonic development study"
- **Concern** The zebrafish experiments show that Y15-CDs reduce survival at high concentrations and reduce morphometric parameters in surviving embryos. However, the manuscript does not report whether the observed growth inhibition is due to general toxicity, developmental delay, or specific effects on cell division. No histological or molecular analysis is provided to support the claim that growth inhibition corresponds to cell cycle arrest. The concentrations used in zebrafish (up to 100 µg/mL) are high, and the manuscript does not discuss whether these concentrations are physiologically relevant. The observation that B-CDs do not affect growth is attributed to weak DNA binding, but alternative explanations (e.g., differences in uptake, metabolism, or excretion) are not considered.
- **Why it matters** The in vivo data are used to support the translational relevance of the findings. If the growth inhibition is due to non-specific toxicity rather than cell cycle arrest, the conclusions would be overstated.
- **Resolution test** Provide additional analyses of zebrafish embryos, such as histological sections, proliferation markers (e.g., PCNA, pHH3), or apoptosis assays. Discuss the potential for non-specific toxicity and provide evidence that the observed effects are specifically due to cell cycle arrest.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Materials and methods, "Fluorometric competitive displacement experiments"
- **Evidence pointer** Methods section
- **Issue** The concentrations of CDs used in the competitive displacement assays are not stated. The text says "varying concentrations" but does not specify the range or the increments.
- **Required correction** Provide the exact concentration ranges and the number of concentrations tested for each assay.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3
- **Issue** The fluorescence spectra in Figure 3 are shown as raw spectra, but the quenching percentages are only mentioned in the text. It would be helpful to show a dose-response curve or a Stern-Volmer plot to demonstrate the concentration dependence of the displacement.
- **Required correction** Add a quantitative representation of the displacement data, such as a plot of fluorescence intensity versus CD concentration.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section, "Circular dichroism studies"
- **Evidence pointer** Results section
- **Issue** The term "perturbated" is used, which is non-standard. The correct term is "perturbed".
- **Required correction** Correct the terminology throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Issue** The representative structures of CDs in Figure 5 are described but the figure itself is not available for review. The text should describe the key structural features more clearly so the reader can interpret the figure without seeing it.
- **Required correction** Provide a more detailed description of the structural models in the text or figure legend.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section, "Zebrafish embryonic development study"
- **Evidence pointer** Results section
- **Issue** The text states that "no significant decrease in survival rate was observed as the incubation time increased from 24 to 72 h", but this is not supported by any statistical analysis. The survival curves in Figure 9D-E appear to show a decrease over time at high concentrations.
- **Required correction** Provide statistical analysis of the survival data over time or revise the statement to be descriptive rather than inferential.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion and Conclusion
- **Evidence pointer** Conclusion section
- **Issue** The manuscript does not discuss the heterogeneity of CDs as a limitation. Real CD preparations contain a distribution of particle sizes and surface chemistries, which could affect the interpretation of the results.
- **Required correction** Add a paragraph discussing the limitations of the study, including CD heterogeneity, the simplified computational models, and the use of a single cell line.

## Risk / unsupported claims
- The claim that Y15-CDs bind DNA via intercalation is supported by competitive displacement and CD data, but the quantitative analysis is insufficient to fully establish this mode. The claim is partially supported but requires additional controls.
- The claim that DNA binding is the mechanism underlying S-phase arrest is not directly supported by any experiment. This is an inference that requires causal testing.
- The claim that Y15-CDs inhibit zebrafish growth due to cell cycle arrest is not supported by direct evidence. Alternative mechanisms such as general toxicity are not excluded.
- The claim that B-CDs do not affect the cell cycle is based on a single cell line and a single time point. This negative result is not fully established.
- The computational binding free energy values are reported but the methodological details are insufficient to assess their reliability. These values should be treated as preliminary.
- The statement that "both B-CDs and Y15-CDs are capable of penetrating the nuclear membrane" is based on fluorescence microscopy, but the images are not quantified and the possibility of artifacts (e.g., non-specific adsorption) is not addressed.