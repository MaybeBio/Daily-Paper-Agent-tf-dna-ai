## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions) without supplementary material or figures
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided text; no assessment of supplementary data or unpublished experimental details
- **Shared manuscript claim summary** The authors report that cobalt(III) Schiff-base complexes (Co(III)-sb) inhibit the zinc finger transcription factor Gli1 by displacing Zn(II) from the Cys2His2 binding site via direct coordination to histidine residues, leading to alpha-helix destabilization and loss of DNA recognition. This is supported by molecular dynamics simulations, circular dichroism spectroscopy, mass spectrometry, NMR, and DNA binding assays.
- **Visible evidence base** Text descriptions of MD simulations (Figures 1, 3, 4; SI Figures 1, 2, 8), spectroscopic data (Figure 2), recombinant expression (Figure 5), and DNA binding assays (Figures 6, 7; SI Table 1)
- **Missing materials affecting confidence** Figures and supplementary information referenced but not provided; experimental methods section absent; no raw data or statistical details; no sequence information for peptides or constructs

## Reviewer

- **Overall assessment** The manuscript presents a plausible mechanism for Gli1 inhibition by Co(III)-sb complexes, combining computational predictions with experimental validation. The work extends prior studies from the same group to a therapeutically relevant target. However, the evidence as presented has several gaps that limit confidence in the central claims, particularly regarding the stoichiometry of Co(III)-sb binding, the specificity of the effect, and the quantitative interpretation of the DNA binding data. The manuscript would benefit from additional experimental detail and more rigorous controls.

- **Who would be interested in the results, and why** Researchers in inorganic medicinal chemistry, transcription factor drug discovery, and Hedgehog pathway biology would find this work relevant. The approach of targeting zinc finger transcription factors with cobalt complexes is a niche but growing area, and Gli1 is a validated cancer target. The computational framework for modeling Co(III)-sb binding to zinc fingers may also be of interest to computational chemists.

- **Major strengths**
  1. The combination of MD simulations with experimental validation is a strong approach that provides mechanistic insight at multiple levels.
  2. The use of a minimal zinc finger model (Gli1-ZF1) for detailed spectroscopic characterization is pragmatic and well justified.
  3. The dose-dependent inhibition data from both CD and DNA binding assays are internally consistent and support the proposed mechanism.
  4. The authors acknowledge limitations of their system (solubility, lack of high-resolution structural data for the full domain) and provide reasonable justification for their extrapolations.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that Co(III)-sb displaces Zn(II) from the Cys2His2 binding site of Gli1 through direct coordination to histidine residues, and that this is the mechanism of inhibition.
  - **Evidence pointer** Figure 2 (NMR, MS), Figure 5 (CD), location not provided for raw data
  - **Concern** The evidence for direct Co(III)-sb coordination to histidine residues in Gli1-ZF1 is based on 2D-NMR chemical shift changes and MS peak assignments. However, the manuscript does not provide details on how the MS peaks were assigned to specific Co(III)-sb adducts, nor does it show control experiments with histidine-mutated peptides to confirm binding specificity. The NMR data show shifts in imidazole protons, but the interpretation that this reflects Co(III)-sb coordination rather than non-specific binding or sample condition changes is not fully established.
  - **Why it matters** The central mechanism of the paper rests on the specificity of Co(III)-sb binding to the zinc finger histidines. Without direct evidence of coordination geometry or mutagenesis controls, alternative explanations (e.g., non-specific aggregation, oxidation, or buffer effects) cannot be excluded.
  - **Resolution test** Provide mutagenesis data (e.g., His-to-Ala substitutions) showing loss of Co(III)-sb binding, or high-resolution structural data (X-ray, NMR structure) of the Co(III)-sb/peptide complex. Alternatively, provide MS/MS fragmentation data confirming the binding site.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative rigor
  - **Claim pointer** The authors report a Kd increase from 74 nM to 850 nM upon treatment with 1.0 equivalent of Co(III)-sb, and state that 2.5, 5, and 10 equivalents yield Kd values greater than 1 µM, implying negligible binding.
  - **Evidence pointer** Figure 7, location not provided for raw binding curves or fitting details
  - **Concern** The BLItz experiments are described qualitatively, with no information on the fitting model, number of replicates, error bars, or how the Kd values were calculated. The statement that Kd values greater than 1 µM imply "negligible binding" is an oversimplification; a Kd of 1 µM still represents measurable binding. Additionally, the relationship between the observed Kd changes and the fraction of Co(III)-sb-bound protein is not modeled.
  - **Why it matters** The quantitative claim of inhibition potency is central to the paper's conclusion that Co(III)-sb is a "potent inhibitor." Without proper error analysis and fitting details, the reported Kd values cannot be evaluated, and the comparison to GANT-61 (mentioned in the Discussion) is not quantitatively supported.
  - **Resolution test** Provide full binding curves, fitting equations, replicate numbers, and error estimates. Model the expected Kd change as a function of Co(III)-sb occupancy to demonstrate that the observed changes are consistent with the proposed mechanism.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Specificity
  - **Claim pointer** The authors state that Co(III)-sb complexes are "selectively binding to the consensus DNA sequence necessary for Hh pathway activation" and imply specificity for Gli1 over other zinc finger proteins.
  - **Evidence pointer** Discussion section, location not provided
  - **Concern** No experiments are presented that test selectivity of Co(III)-sb for Gli1 over other zinc finger transcription factors. The authors previously demonstrated inhibition of Snail1 and Ci, which suggests broad reactivity rather than selectivity. The claim of selectivity appears in the Conclusions but is not supported by any data in this manuscript.
  - **Why it matters** If Co(III)-sb inhibits multiple zinc finger proteins, the therapeutic relevance for Gli1-specific inhibition is weakened. The manuscript should either temper this claim or provide selectivity data.
  - **Resolution test** Perform DNA binding or transcription assays with a panel of zinc finger proteins (e.g., Sp1, Gli2, Gli3) to demonstrate preferential inhibition of Gli1, or revise the claim to acknowledge broad-spectrum zinc finger inhibition.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Computational validation
  - **Claim pointer** The MD simulations predict that Co(III)-sb binding reduces alpha-helix content in a dose-dependent manner and that this effect is localized to the bound zinc finger without allosteric effects on other fingers.
  - **Evidence pointer** Figures 1, 3, 4; SI Figures 1, 2
  - **Concern** The MD simulations are described as starting with Co(III)-sb already coordinated to the zinc finger, but no details are provided on how the initial coordinates were generated, how the force field parameters for Co(III)-sb were validated, or how convergence was assessed. The claim that no allosteric effects occur is based on two specific configurations (adjacent vs. distant fingers) but the statistical power of this comparison is unclear.
  - **Why it matters** The computational predictions are a key pillar of the paper's mechanistic argument. If the simulations are not well validated, the agreement between simulation and experiment could be coincidental.
  - **Resolution test** Provide details on parameterization, equilibration, and convergence criteria. Include additional replicates or longer timescales to strengthen the statistical comparison of different Co(III)-sb occupancy patterns.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 2E description
  - **Evidence pointer** Figure 2E, location not provided
  - **Issue** The text states that "a ~0.5–0.7 ppm upfield shift in the aromatic imidazole protons was observed" but does not specify which protons (H2 vs. H5) shift by which amount, nor whether the shift is uniform across both.
  - **Required correction** Provide a table or detailed description of chemical shift changes for each imidazole proton, with assignments.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Experimental methods
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The manuscript lacks a detailed methods section. Key parameters such as peptide synthesis conditions, CD buffer composition, MD simulation length, and BLItz experimental setup are not described.
  - **Required correction** Add a comprehensive methods section or reference prior publications for standard protocols.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of GANT-61 comparison
  - **Evidence pointer** Discussion section, location not provided
  - **Issue** The comparison to GANT-61 potency is made without direct head-to-head experiments under identical conditions. The cited IC50 values may not be directly comparable due to different assay formats.
  - **Required correction** Either include a direct comparison experiment or soften the comparative claim.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 6 (EMSA)
  - **Evidence pointer** Figure 6, location not provided
  - **Issue** The EMSA data are described as showing "dose-dependent" inhibition, but the quantification method (e.g., densitometry) and the number of replicates are not stated.
  - **Required correction** Provide quantification details and error bars for the EMSA data.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of direct evidence for specific Co(III)-sb-histidine coordination in Gli1-ZF1
  - R1-M2: Insufficient quantitative detail for BLItz binding data
  - R1-M3: Unsupported claim of selectivity for Gli1

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The application of Co(III)-sb to Gli1 is novel, but the mechanism (Zn displacement from zinc fingers) has been previously reported by the same group for other transcription factors. The incremental advance is the target protein, not the fundamental chemistry.
  - **Scientific importance** Moderate. Gli1 is a relevant cancer target, and the demonstration that a cobalt complex can inhibit its DNA binding is of interest. However, the lack of cellular or in vivo data limits the translational significance.
  - **Interdisciplinary readership** Limited. The work will appeal primarily to inorganic chemists and transcription factor biologists. The clinical relevance to Hedgehog pathway cancers is mentioned but not explored experimentally.
  - **Technical soundness** The computational and experimental approaches are generally sound in concept, but the lack of methodological detail and the gaps in quantitative analysis (noted above) prevent full assessment.
  - **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. However, some jargon (e.g., "Schiff-base complexes," "Cys2His2") is not defined for a general audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the preliminary data are promising, but the manuscript requires additional experimental evidence (particularly regarding binding specificity and quantitative analysis) before the claims can be fully accepted.

## Risk / unsupported claims
- The claim that Co(III)-sb is "selectively binding to the consensus DNA sequence" (Conclusions) is not supported by any selectivity experiments.
- The statement that "very low molar equivalents of Co(III)-sb" inhibit DNA binding is not quantitatively supported without knowing the fraction of bound protein at each concentration.
- The extrapolation of Gli1-ZF1 binding data to the full five-finger domain is reasonable but not experimentally verified; the authors acknowledge this limitation.
- The claim that Co(III)-sb binding is "irreversible under biological conditions" is stated without experimental evidence in this manuscript (referenced to prior work).
- The dose-dependent decrease in alpha-helix content in MD simulations is presented as a key finding, but the statistical significance of the differences between 1, 3, and 5 Co(III)-sb bound states is not reported.