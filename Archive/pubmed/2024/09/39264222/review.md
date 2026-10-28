## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with stated conclusions; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors use four computational tools (SIFT, PolyPhen-2, PhD-SNP, MutPred2) to screen 58 p53 nsSNPs, identify three variants (C141Y, C238S, L265P) as deleterious, and use MD simulations, MM/GBSA binding free energy calculations, and Rosetta Flex-ddG to show these mutations destabilize p53 and reduce DNA binding affinity, with L265P showing the largest effect.
- **Visible evidence base** Abstract, introduction, methodology, results and discussion sections, tables referenced (Tables 1–4), figures referenced (Figures 1–8), supplementary material referenced (Tables S1–S7, Figure S1)
- **Missing materials affecting confidence** Actual data tables and figures not provided; supplementary tables and figures not accessible; experimental validation data not included; specific numerical values for RMSD, RMSF, Rg, and binding free energies only partially reported in text

## Reviewer
- **Overall assessment** The manuscript presents a systematic computational workflow to identify and characterize potentially deleterious p53 mutations. The combination of multiple prediction tools, MD simulations, and binding free energy calculations is appropriate and generally well-executed. However, several technical concerns limit the strength of the conclusions. The lack of experimental validation, incomplete reporting of simulation parameters, and the use of a single crystal structure without considering conformational diversity weaken the generalizability of the findings. The claim that L265P poses "significant risk to humans" is not adequately supported by the computational evidence presented. The manuscript would benefit from clearer presentation of error estimates, convergence criteria, and a more nuanced discussion of the limitations of computational predictions.

- **Who would be interested in the results, and why** Computational biologists and structural biologists studying p53 mutations and their functional consequences would find this work relevant. Researchers in cancer genomics and precision medicine may also be interested in the identification of potentially deleterious variants. The methodological framework combining multiple prediction tools with MD simulations could serve as a template for similar studies on other proteins. However, the lack of experimental validation limits the direct translational relevance.

- **Major Strengths**  
  The study uses a multi-tiered computational approach, combining sequence-based predictors with structure-based simulations, which is methodologically sound. The inclusion of MM/GBSA binding free energy calculations and pairwise decomposition analysis provides mechanistic insight into how mutations affect DNA binding. The comparison with experimentally characterized mutations (G245S, R249S, R273H) helps contextualize the findings. The use of Rosetta Flex-ddG as an orthogonal method strengthens the binding affinity predictions.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript claims that MD simulations revealed "all three variants exhibited heightened structural flexibility compared to the native protein" and that binding free energy calculations confirm "reduced binding of mutant proteins to DNA."  
- **Evidence pointer** Results section, Figures 3–5, Table 2; location not provided for specific numerical values  
- **Concern** The manuscript does not report error estimates or standard deviations for the RMSD, RMSF, Rg, or binding free energy values. For MD simulations, ensemble averages require statistical analysis across independent trajectories or block averaging. The claim that three independent 200 ns simulations were performed for the complex systems is stated, but no convergence criteria or error bars are presented. Without these, it is impossible to assess whether the observed differences between wild-type and mutants are statistically significant or within thermal fluctuations.  
- **Why it matters** The central conclusion that these mutations reduce DNA binding affinity depends on the statistical reliability of the computed free energy differences. MM/GBSA is known to have systematic errors, and without error analysis, the reported differences (e.g., −59.2 vs −36.9 kcal/mol) cannot be evaluated for significance.  
- **Resolution test** Provide standard deviations or standard errors for all reported binding free energies and structural metrics. Include convergence plots for RMSD and binding free energy as a function of simulation time. Perform at least three independent simulations per system and report the spread of results.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The conclusion states that "the presence of the L265P mutation in p53 could pose a substantial risk to humans" and that the study "carries significant implications for surveillance efforts and the development of anticancer therapies."  
- **Evidence pointer** Conclusion section; location not provided  
- **Concern** The leap from computational predictions to clinical risk assessment is not justified. The manuscript does not provide epidemiological, clinical, or functional experimental data linking L265P to cancer risk. While computational predictions can generate hypotheses, they cannot establish risk without validation. The claim of "substantial risk" is an overstatement given the purely in silico nature of the study.  
- **Why it matters** Overstating the clinical implications of computational findings can mislead readers and potentially influence clinical decision-making. The scientific community requires experimental or epidemiological evidence before such claims are made.  
- **Resolution test** Either temper the language to clearly state that these are predictions requiring experimental validation, or provide additional evidence (e.g., population frequency data, clinical association studies, or functional assays) supporting the risk claim.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript states that "the corrected binding free energies for C141Y, C238S, and L265P are −5.95 kcal/mol, −6.16 kcal/mol, and −5.01 kcal/mol" and corresponding KD values of 25.4, 17.5, and 135.2 μM.  
- **Evidence pointer** Results section, Table 2, Equation 4; location not provided  
- **Concern** The calibration procedure using Equation 4 with an arbitrary correction factor X = 1.22 is not adequately justified. The equation appears to be an ad hoc scaling method, and the choice of X is not explained or derived from first principles. The manuscript does not describe how the correction factor was optimized or validated. Additionally, the conversion from binding free energy to KD assumes a two-state model that may not be valid for a tetrameric protein binding to DNA.  
- **Why it matters** The quantitative KD values are presented as meaningful predictions, but the calibration method introduces uncontrolled uncertainty. If the correction factor is arbitrary, the absolute KD values are not reliable, and only relative comparisons may be meaningful.  
- **Resolution test** Justify the choice of X through a systematic calibration against a training set of known p53-DNA binding affinities. Alternatively, present the raw MM/GBSA values without conversion to KD and discuss relative differences rather than absolute values.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript states that "the L265P mutation exhibited the highest ddG_Gam value (1.64 REU)" and interprets this as indicating the greatest reduction in binding capacity.  
- **Evidence pointer** Results section, Table 4, Figure 8E; location not provided  
- **Concern** Rosetta Flex-ddG is designed for protein-protein interactions, and its applicability to protein-DNA interactions is not well established. The manuscript does not discuss the limitations of using a protein-protein interaction scoring function for a protein-DNA complex. Additionally, the convergence analysis for the Flex-ddG calculations is only referenced in supplementary material, and the criteria for convergence are not described in the main text.  
- **Why it matters** If the scoring function is not appropriate for protein-DNA systems, the Flex-ddG results may not be meaningful. The manuscript uses these results to corroborate the MM/GBSA findings, but if the method is not validated for this system, the corroboration is weak.  
- **Resolution test** Validate Flex-ddG performance on a set of known p53-DNA binding mutants with experimental affinity data. Discuss the applicability of the method to protein-DNA complexes and acknowledge limitations.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript claims that "the DNA binding affinity of all three variants decreased by approximately 1.8 to 9.7 times compared to wildtype p53 binding with DNA (14 μM)."  
- **Evidence pointer** Results section, Table 2; location not provided  
- **Concern** The wild-type KD of 14 μM is stated, but the source of this value is not clearly identified. The manuscript references experimental values for G245S, R249S, and R273H from Ang et al., but the wild-type value of 14 μM appears to be from a different source or calculated. The manuscript does not clarify whether this is an experimentally determined value or a computed one.  
- **Why it matters** The fold-change comparisons depend on the accuracy of the wild-type reference value. If the 14 μM value is not well-established, the reported fold-changes are uncertain.  
- **Resolution test** Clearly state the source of the 14 μM wild-type KD value. If it is from a different experimental study, provide the citation. If it is computed, describe the method and its validation.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Introduction  
- **Evidence pointer** Introduction, paragraph 1; location not provided  
- **Issue** The introduction provides extensive background on cancer statistics and p53 function but does not clearly state the specific gap in knowledge that this study addresses. The rationale for screening 58 specific nsSNPs is not explained.  
- **Required correction** Add a clear statement of the knowledge gap and justify the selection of the 58 nsSNPs.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Methodology, MD simulations  
- **Evidence pointer** Methodology section, "Molecular Dynamics Simulations"; location not provided  
- **Issue** The manuscript states that simulations were performed at 303.15 K, which is slightly above physiological temperature (310 K). The choice of temperature is not justified.  
- **Required correction** Explain the choice of simulation temperature or use physiological temperature (310 K) for greater biological relevance.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Methodology, MD simulations  
- **Evidence pointer** Methodology section, "Molecular Dynamics Simulations"; location not provided  
- **Issue** The manuscript states that the SHAKE algorithm was applied to constrain bonds involving hydrogen atoms, but the integration time step of 2 fs is standard for SHAKE. The equilibration protocol is described, but the production run length (450 ns) is stated without justification for why this length is sufficient.  
- **Required correction** Provide a brief justification for the simulation length, referencing convergence of structural properties.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Results, hydrogen bonding analysis  
- **Evidence pointer** Results section, "Examining mutational impact through intramolecular hydrogen bonding"; location not provided  
- **Issue** The manuscript reports hydrogen bond frequencies but does not specify the criteria used to define a hydrogen bond (e.g., distance and angle cutoffs).  
- **Required correction** State the geometric criteria used for hydrogen bond detection.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Results, pairwise decomposition analysis  
- **Evidence pointer** Results section, "Pairwise decomposition analysis"; location not provided  
- **Issue** The pairwise decomposition analysis identifies key residue-base pairs but does not explain the biological significance of these specific interactions in the context of p53-DNA recognition.  
- **Required correction** Briefly discuss why these specific interactions are important for p53 function and how their disruption relates to the observed binding affinity changes.

- **Concern ID** R1-m6  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Methodology, Rosetta Flex-ddG  
- **Evidence pointer** Methodology section, "Rosetta Flex ddG"; location not provided  
- **Issue** The manuscript states that 35,000 backrub steps were performed for each mutation but does not describe how the number of steps was determined to be sufficient for convergence.  
- **Required correction** Reference the convergence analysis in supplementary material and briefly describe the convergence criteria in the main text.

- **Concern ID** R1-m7  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Discussion  
- **Evidence pointer** Results and Discussion section; location not provided  
- **Issue** The discussion does not compare the predicted effects of C141Y, C238S, and L265P with any known functional data for these specific mutations, if available in the literature.  
- **Required correction** Add a brief comparison with any published experimental or clinical data on these mutations, or explicitly state that no such data are available.

## Risk / unsupported claims
- The claim that L265P "could pose a substantial risk to humans" is unsupported by the computational evidence alone and requires experimental or epidemiological validation.
- The quantitative KD values (25.4, 17.5, 135.2 μM) derived from the calibration procedure with arbitrary correction factor X = 1.22 are not reliable as absolute values.
- The statement that "all three variants exhibited heightened structural flexibility" is presented without statistical error analysis, making the claim not fully supported.
- The claim that the findings "are in alignment with the experimentally determined values of three other cancer-causing mutations" is only indirect validation and does not directly validate the predictions for C141Y, C238S, and L265P.
- The applicability of Rosetta Flex-ddG to protein-DNA interactions is not established, and the results from this method should be interpreted with caution.
- The manuscript does not provide evidence that the 58 nsSNPs selected for screening are representative of the full spectrum of p53 variants in human populations.