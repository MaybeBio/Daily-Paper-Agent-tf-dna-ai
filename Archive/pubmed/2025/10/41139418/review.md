## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; supplementary figures and tables referenced but not independently verified
- **Shared manuscript claim summary** The authors use AlphaFold-Multimer to predict a binding interface between MYC and Miz-1 MID2 that overlaps with the MYC/MAX dimerization domain. They design stapled peptidomimetics based on this prediction, validate binding via biolayer interferometry, perform alanine scanning to identify hotspots, and demonstrate that optimized variants disrupt MYC/MAX/DNA complex formation in vitro with submicromolar potency, while noting some unspecific effects on MAX/MAX/DNA complexes.
- **Visible evidence base** Main text figures (Figures 1-4), supplementary figures and tables (Figures S1-S18, Tables S1-S4) as referenced; numerical values for AlphaFold confidence scores, binding affinities, helicity percentages, and IC50 values as stated in text
- **Missing materials affecting confidence** Full experimental methods section, actual BLI sensorgrams, CD spectra, EMSA gel images, AlphaFold confidence plots (PAE, MSA coverage), peptide synthesis and characterization data, protein expression and purification details, statistical analysis details, and complete supplementary information

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting application of AlphaFold-Multimer to a challenging intrinsically disordered protein target, with a logical workflow from prediction to experimental validation. The finding that Miz-1 MID2 binds at a site overlapping the MYC/MAX dimerization interface is potentially significant, and the demonstration that peptidomimetics derived from this interface can disrupt MYC/MAX/DNA complexes is noteworthy. However, several technical concerns limit the strength of the conclusions. The BLI data are acknowledged by the authors to be non-ideal, with observed affinities that may not reflect true values. The mechanism by which Mizmetic 16 and 20 inhibit MAX/MAX/DNA complexes is not explained, despite no direct binding to MAX being detected. The AlphaFold confidence scores are modest (ipTM values of 0.33-0.67), and the manuscript lacks orthogonal validation of the predicted binding mode, such as mutagenesis of the MYC interface or structural studies. The claim of "submicromolar potency" is based on EMSA competition assays that are not fully described. Overall, the work is promising but requires additional experimental rigor to fully establish the case.

- **Who would be interested in the results, and why** Researchers in the fields of intrinsically disordered proteins, transcription factor targeting, peptide therapeutics, and computational structural biology would find this work of interest. The demonstration that AlphaFold can predict druggable interfaces on disordered proteins has broad implications for drug discovery. Those working on MYC as a therapeutic target would specifically be interested in the potential new modality for disrupting MYC function. The peptidomimetic approach and the identification of hotspots via alanine scanning would appeal to peptide medicinal chemists.

- **Major strengths** The manuscript addresses a significant problem (targeting MYC, a challenging IDP) with a novel approach (AlphaFold-guided peptidomimetic design). The workflow is logical and integrates computational prediction with experimental validation. The identification of an overlapping interface between Miz-1 and MAX binding on MYC is an interesting finding that could have biological implications. The alanine scanning data appear to support the AlphaFold predictions, providing some validation of the computational model. The authors are transparent about the limitations of their BLI data and the unspecific effects observed in EMSA.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding affinity measurements
- **Claim pointer** The manuscript claims observed binding affinities of 4.6 ± 1.3 µM for Mizmetic WT, 176 ± 1 nM for Mizmetic 1, and 76 ± 1 nM for Mizmetic 2, and uses these to support the conclusion that stapling improves binding.
- **Evidence pointer** Figure 2c, 2g; Figure S11; Table S2; "location not provided" for BLI methods
- **Concern** The authors explicitly state that the BLI binding curves were non-ideal and that "further attempts to optimize the binding behavior... did not improve the shapes of the BLI curves, thereby limiting us in finding the true affinity value toward MYC." Despite this acknowledged limitation, the manuscript reports specific Kd values with small errors (e.g., 176 ± 1 nM) and uses these to make quantitative comparisons (26-fold improvement). Reporting precise affinity values from non-ideal binding data is problematic. The observed Kd values may be influenced by avidity effects, aggregation, or non-specific binding, as the authors themselves suggest. The relative comparisons between Mizmetic variants may still be valid if the artifacts are consistent across measurements, but this is not demonstrated. The manuscript needs to either provide a more rigorous analysis of the binding data (e.g., global fitting, alternative models) or present the affinities as approximate with appropriate caveats and error estimates that reflect the uncertainty.
- **Why it matters** The quantitative claims of binding affinity and the improvement upon stapling are central to the manuscript's narrative. If the affinity values are not reliable, the conclusions about stapling improving binding and the subsequent optimization are weakened. The "submicromolar potency" claim in the abstract and conclusion is based on these measurements.
- **Resolution test** Provide representative BLI sensorgrams with fits, describe the fitting model used, report confidence intervals or errors that reflect the non-ideal behavior, and demonstrate that the relative ranking of affinities is robust to different analysis methods. Alternatively, use an orthogonal binding assay (e.g., ITC, MST, or fluorescence polarization) to validate the affinity improvements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic interpretation of MYC/MAX/DNA disruption
- **Claim pointer** The manuscript claims that select Mizmetic variants (13, 16, 19-21) disrupt MYC/MAX/DNA complex formation, and that this is due to binding at the overlapping Miz-1/MAX interface on MYC.
- **Evidence pointer** Figure 4c-f; Figure S14-S17; "location not provided" for EMSA methods
- **Concern** The mechanism by which Mizmetics disrupt MYC/MAX/DNA complexes is not clearly established. The authors note that Mizmetic 16 inhibits both MYC/MAX and MAX/MAX complexes with similar IC50s (3 and 2 µM, respectively), yet no direct binding to MAX was detected by BLI. This is a contradiction that is not resolved. If Mizmetic 16 does not bind MAX, how does it inhibit MAX/MAX/DNA complex formation? The authors speculate about "unspecific binding" but do not provide evidence for this. Furthermore, for Mizmetic 20, which shows 4-fold selectivity for MYC/MAX over MAX/MAX, the mechanism of MYC/MAX disruption is not demonstrated to be through competition at the Miz-1 site. The EMSA experiments do not distinguish between (a) Mizmetic binding to MYC and preventing MAX dimerization, (b) Mizmetic binding to the MYC/MAX complex and causing dissociation, or (c) Mizmetic binding to DNA and preventing protein binding. Control experiments (e.g., Mizmetic alone with DNA, Mizmetic with MAX alone) are referenced but not described in sufficient detail.
- **Why it matters** The central claim of the manuscript is that targeting the Miz-1 interface on MYC can disrupt MYC/MAX function. If the mechanism is not established, the therapeutic relevance of the approach is unclear. The unspecific effects on MAX/MAX complexes raise concerns about selectivity and could indicate a non-specific mode of action.
- **Resolution test** Perform competition experiments with a Mizmetic variant that cannot bind MYC (e.g., a scrambled sequence or a mutant with disrupted hotspot residues) to demonstrate specificity. Use a direct binding assay (e.g., fluorescence anisotropy or MST) to test whether Mizmetics bind to the MYC/MAX complex or to MAX alone. Perform EMSA with varying order of addition to determine if Mizmetics prevent complex formation or promote dissociation. Consider testing whether Mizmetics bind to DNA directly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation of the AlphaFold-predicted interface
- **Claim pointer** The manuscript claims that AlphaFold-Multimer predicts a 28-amino acid region of Miz-1 MID2 binding to the MYC HLH domain, and that this prediction is validated by alanine scanning.
- **Evidence pointer** Figure 1d-f; Figure 3a-c; "location not provided" for AlphaFold methods
- **Concern** The AlphaFold confidence scores reported (ipTM = 0.33-0.67) are modest. For protein-protein complexes, ipTM values above 0.8 are generally considered high confidence, while values in the 0.3-0.6 range indicate uncertain predictions. The authors do not report PAE plots, MSA depth, or other confidence metrics that would help assess the reliability of the prediction. The alanine scanning data show that three hydrophobic residues (Leu7, Ile11, Val15) are important for binding, which is consistent with the prediction, but this is a limited validation. The authors do not perform mutagenesis on the MYC side of the interface to confirm that the predicted MYC residues are indeed the binding site. Without this orthogonal validation, the possibility remains that the Mizmetic peptides bind to a different site on MYC.
- **Why it matters** The entire approach is predicated on the accuracy of the AlphaFold prediction. If the predicted interface is incorrect, the design rationale for the peptidomimetics is undermined, even if the peptides happen to bind MYC. The manuscript's claim that AlphaFold can "illuminate disordered protein interactions" requires stronger validation of the specific prediction.
- **Resolution test** Provide PAE plots and per-residue confidence scores for the predicted complex. Perform mutagenesis on MYC residues predicted to be at the interface (e.g., the hydrophobic groove of the HLH domain) and test whether these mutations affect Mizmetic binding. Consider using HDX-MS or NMR to map the binding site experimentally. If possible, obtain a co-crystal structure or cryo-EM structure of the Mizmetic-MYC complex.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity and selectivity of Mizmetic compounds
- **Claim pointer** The manuscript claims that Mizmetic 20 inhibits MYC/MAX with an IC50 of 560 nM and is 4-fold more potent against MYC/MAX than MAX/MAX, suggesting some selectivity.
- **Evidence pointer** Figure 4e-f; Figure S15-S17; "location not provided" for EMSA methods
- **Concern** The selectivity data are limited to two protein complexes (MYC/MAX and MAX/MAX). The manuscript does not test whether Mizmetics bind to other bHLH-LZ proteins or other proteins with similar hydrophobic grooves. Given that the Mizmetic peptides are derived from a natural protein sequence and are relatively short (24 amino acids), they may have off-target effects. The authors note that Mizmetic 16 shows no selectivity between MYC/MAX and MAX/MAX, which is concerning. The manuscript does not address the potential for non-specific hydrophobic interactions, which could be a significant issue for a peptide with a large hydrophobic surface.
- **Why it matters** For a therapeutic application, selectivity is critical. If Mizmetics inhibit other bHLH-LZ proteins or have non-specific effects, their utility as research tools or therapeutic leads is limited. The manuscript's claim of a "novel mode of intervention" requires evidence that the intervention is specific.
- **Resolution test** Test Mizmetic 20 against a panel of bHLH-LZ proteins (e.g., Mad/Max, Mnt/Max, USF, TFE3) in EMSA or binding assays. Perform a pull-down or proteomics experiment to identify potential off-targets. Test Mizmetic 20 in a cellular context to assess selectivity and toxicity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance and cellular activity
- **Claim pointer** The manuscript claims that the findings "offer a promising foothold for future therapeutic development against MYC-driven cancers" and that the approach "highlights a novel mode of intervention against a transcription factor long considered 'undruggable'."
- **Evidence pointer** Conclusion section; "location not provided" for any cellular experiments
- **Concern** The manuscript contains no cellular or in vivo experiments. All data are from in vitro biochemical assays (BLI, EMSA, CD). While the authors appropriately describe the work as "proof-of-concept," the therapeutic implications are overstated without any demonstration that the Mizmetic peptides can penetrate cells, maintain stability in biological environments, or affect MYC-driven transcription in a cellular context. The lack of cellular data is a significant gap for a manuscript that discusses therapeutic development.
- **Why it matters** Many peptides that show promising in vitro activity fail in cellular or in vivo settings due to poor cell permeability, metabolic instability, or lack of efficacy. The therapeutic claims in the abstract and conclusion are not supported by the presented data.
- **Resolution test** Perform cellular experiments with a cell-permeable version of Mizmetic 20 (e.g., with a cell-penetrating peptide tag or using a stapled peptide with enhanced cell permeability). Assess effects on MYC target gene expression, cell proliferation, and apoptosis in MYC-driven cancer cell lines. If cellular activity is demonstrated, the therapeutic claims would be substantially strengthened.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** AlphaFold methods
- **Evidence pointer** "location not provided" for AlphaFold methods
- **Issue** The manuscript does not describe the AlphaFold-Multimer parameters used, the multiple sequence alignment generation, the number of models generated, or the selection criteria for the final model. This limits reproducibility.
- **Required correction** Provide a detailed description of the AlphaFold-Multimer protocol, including software version, databases used, number of recycles, and model selection criteria. Consider depositing the models in a public repository.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** BLI binding data
- **Evidence pointer** Figure 2c, 2g; Figure S11; Table S2
- **Issue** The manuscript reports Kd values with very small errors (e.g., 176 ± 1 nM) that are inconsistent with the acknowledged non-ideal binding behavior. The errors appear to be fitting errors rather than reflecting experimental variability.
- **Required correction** Report the errors as confidence intervals from the fitting or as standard deviations from independent replicates. Clearly state the limitations of the affinity measurements in the figure legends and text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of CD data
- **Affected element** Figure 2d-e; Figure S12
- **Evidence pointer** "location not provided" for CD methods
- **Issue** The CD data are used to support the claim that stapling increases helicity, but the analysis is limited. The manuscript reports helicity percentages from BestSEL analysis but does not show the raw CD spectra or describe the fitting procedure in detail. The increase from 3.0% to 11.6% helicity is modest, and the biological significance is unclear.
- **Required correction** Show representative CD spectra with the fits overlaid. Describe the BestSEL analysis parameters. Discuss whether the observed helicity increase is consistent with the expected effect of stapling on a short peptide.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** EMSA quantification
- **Evidence pointer** Figure 4e-f; Figure S15-S17
- **Issue** The manuscript reports IC50 values for EMSA inhibition but does not describe how the data were quantified, how many independent replicates were performed, or how the IC50 values were calculated. Error bars are not shown in the described figures.
- **Required correction** Describe the EMSA quantification method (e.g., densitometry), the number of replicates, and the curve-fitting procedure. Show error bars and individual data points in the figures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Overlapping MYC/Miz-1 Interface"
- **Evidence pointer** Title, Abstract, Introduction
- **Issue** The title and text describe the Miz-1 binding site as "overlapping" with the MYC/MAX dimerization domain. However, the manuscript does not provide structural evidence for the overlap beyond the AlphaFold prediction. The term "overlapping" implies a specific spatial relationship that is not experimentally demonstrated.
- **Required correction** Consider using more cautious language such as "predicted to overlap" or "proximal to" in the title and abstract, or provide additional experimental evidence for the spatial relationship.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness of references
- **Affected element** Introduction, Discussion
- **Evidence pointer** "location not provided" for references
- **Issue** The introduction cites recent in silico strategies for IDP interaction prediction but does not provide a comprehensive comparison with other computational approaches for IDP druggability. The discussion of MYC/Miz-1 biology could be more complete.
- **Required correction** Expand the discussion of prior computational approaches to IDP targeting and provide a more thorough review of the MYC/Miz-1 literature.

## Risk / unsupported claims
- The claim that Miz-1 binds at a site "overlapping with the MYC/MAX dimerization domain" is based solely on AlphaFold-Multimer predictions with modest confidence scores (ipTM = 0.33-0.67) and is not experimentally validated by mutagenesis or structural studies.
- The reported Kd values (4.6 µM, 176 nM, 76 nM) are described by the authors as "observed" affinities from non-ideal BLI data, yet are presented with precision that implies reliability. The true affinity values are not established.
- The claim of "submicromolar potency" for MYC/MAX/DNA disruption is based on EMSA competition assays that are not fully described, and the mechanism of inhibition is not established.
- The inhibition of MAX/MAX/DNA complexes by Mizmetic 16 and 20 is not explained, and the authors' speculation about "unspecific binding" is not supported by direct evidence.
- The therapeutic implications stated in the conclusion ("promising foothold for future therapeutic development") are not supported by any cellular or in vivo data.
- The statement that "AlphaFold-Multimer is a powerful platform to analyze IDRs and their PPIs" is a general claim that is not fully supported by the single example presented, particularly given the modest confidence scores and lack of orthogonal validation.