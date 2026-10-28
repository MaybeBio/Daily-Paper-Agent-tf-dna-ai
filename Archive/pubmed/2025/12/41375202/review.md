## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and conclusions. Figures, schemes, and tables are referenced but not fully provided.
- **Assessment boundary** Scientific content, technical soundness, interpretation of results, and alignment with stated claims. Not assessed: editorial quality, formatting, or literature completeness beyond what is visible.
- **Shared manuscript claim summary** The authors report synthesis of three novel styryl hemicyanine dyes with substituted N-phenylpiperazine end groups, characterization of their photophysical properties, and evidence for DNA minor groove binding. They propose a PET-based fluorescence modulation mechanism responsive to pH, with potential application as fluorescent probes for nucleic acid environments.
- **Visible evidence base** Synthetic procedures and characterization data (NMR), UV/VIS absorption and fluorescence spectra in various solvents and in presence of HCl and DNA, DFT/TDDFT calculations, molecular docking, and CD spectroscopy for one dye.
- **Missing materials affecting confidence** Full figures and tables (referenced but not included), supplementary information, raw titration data, DNA sequence and source details, docking validation metrics, and complete computational output.

## Reviewer
- **Overall assessment** The manuscript presents a systematic study of three new hemicyanine dyes with interesting photophysical properties. The synthetic approach is commendable for its environmental friendliness and high yields. The combination of experimental spectroscopy with computational modeling is appropriate. However, several technical concerns regarding data interpretation, experimental controls, and the strength of claims about DNA binding mode and PET mechanism require clarification before the conclusions can be fully supported.
- **Who would be interested in the results, and why** Researchers in fluorescent probe design, DNA-binding small molecules, and bioimaging applications would find this work relevant. The pH-responsive fluorescence modulation and minor groove binding properties could be of interest to those developing tools for cancer diagnostics or cellular imaging, given the acidic tumor microenvironment.
- **Major strengths** The synthetic methodology is efficient and environmentally conscious, with high purity products. The study integrates multiple complementary techniques (spectroscopy, computation, docking, CD) to address the research questions. The observation of fluorescence restoration upon acid addition to dye-DNA complexes is a potentially useful finding for probe design.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of DNA binding mode claim
  - **Claim pointer** The manuscript states that "CD spectroscopy and molecular docking further reveal that the dyes interact with DNA via a minor-groove binding mode."
  - **Evidence pointer** Section 2.4, Figure 11, Section 2.3, Figure 10
  - **Concern** The CD data are presented for dye 4c only, and the interpretation relies on the appearance of induced CD signals. However, the manuscript does not provide a detailed analysis of the ICD sign pattern or its relationship to known minor groove binders versus intercalators. The docking study uses a single DNA structure (1G3X) which contains an intercalated ligand, and the validation with thiazole orange confirms intercalation but does not establish that the docking protocol can distinguish minor groove binding from intercalation for the new dyes. The binding energies in Table 6 are not compared with any threshold or known minor groove binder control.
  - **Why it matters** The minor groove binding mode is a central claim of the manuscript and underpins the proposed application as DNA-targeting probes. If the binding mode is not rigorously established, the mechanistic interpretation and potential applications are weakened.
  - **Resolution test** Provide CD spectra for all three dyes with quantitative analysis of ICD magnitude and sign. Include a known minor groove binder (e.g., DAPI or Hoechst 33258) as a positive control in docking and CD experiments. Show that the docking protocol can reproduce the minor groove binding of a control compound. Present binding free energies with error estimates and statistical significance.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretation of fluorescence data and PET mechanism
  - **Claim pointer** The manuscript claims that "the dyes show fluorescence quenching upon DNA binding" and that "titration with acid of the dye-DNA complexes restores fluorescence, indicating suppression of the PET and, at the same time, rigidizing of the chemical structure."
  - **Evidence pointer** Section 2.2.2, Table 5, Figures 9, S12, S13
  - **Concern** The fluorescence data are presented as intensity values in Table 5, but no quantum yields are reported. The claim that DNA binding causes quenching is based on intensity changes, which could be affected by inner filter effects, aggregation, or changes in refractive index. The restoration of fluorescence upon acid addition is attributed to PET suppression, but alternative explanations such as dye release from DNA or conformational changes are not excluded. The manuscript does not provide titration curves showing the relationship between acid concentration and fluorescence intensity, nor does it report the stoichiometry of protonation events.
  - **Why it matters** The PET mechanism is central to the proposed pH-sensing function. Without rigorous evidence excluding alternative explanations and quantifying the fluorescence changes, the mechanistic claim is not fully supported.
  - **Resolution test** Report fluorescence quantum yields for all dyes under all four conditions. Provide complete acid titration curves with fitted pKa values. Perform control experiments with a non-DNA-binding analog to confirm that the fluorescence changes are DNA-dependent. Use time-resolved fluorescence or transient absorption to directly evidence PET.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative analysis of DNA binding affinity
  - **Claim pointer** The manuscript states that the dyes "show fluorescence quenching upon DNA binding" and implies binding affinity through titration experiments, but no binding constants are reported.
  - **Evidence pointer** Section 2.2.1, Figure 5, Table 1
  - **Concern** The UV/VIS titration data in Figure 5 show spectral changes upon DNA addition, but no binding constants (Kb) or binding site sizes are calculated. The manuscript does not specify the DNA sequence or length used, which is critical for interpreting binding affinity and mode. The concentration range of DNA used in titrations is not clearly stated.
  - **Why it matters** Quantitative binding parameters are essential for comparing these dyes to existing DNA probes and for assessing their practical utility. Without these data, the claim of "excellent binding affinities" (mentioned in the introduction as prior work) cannot be evaluated for the new compounds.
  - **Resolution test** Calculate binding constants from UV/VIS or fluorescence titration data using appropriate models (e.g., McGhee-von Hippel). Specify DNA sequence, length, and concentration. Provide Scatchard or equivalent analysis.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of synthetic procedure
  - **Affected element** Section 2.1
  - **Evidence pointer** Scheme 1, Section 3.1
  - **Issue** The synthetic procedure mentions "grinding together in a mortar" but the exact conditions (time, temperature, atmosphere) are only partially described in Section 3.1. The role of DIPEA as a "sterically hindered base" is mentioned but not explained mechanistically.
  - **Required correction** Clarify the purpose of DIPEA in the condensation reaction and provide complete reaction conditions including time, temperature, and any inert atmosphere requirements.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Table 5
  - **Evidence pointer** Table 5
  - **Issue** The fluorescence intensity values are presented without error estimates or replicates. The statement about "apparent average values" is vague.
  - **Required correction** Report standard deviations or standard errors for fluorescence measurements, and specify the number of replicates.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Computational methodology
  - **Affected element** Section 2.2.1
  - **Evidence pointer** Section 2.2.1, Table 2
  - **Concern** The DFT calculations use B3LYP for geometry optimization and PBE0 for TDDFT, but the manuscript does not justify this combination. Solvent effects are mentioned but the specific solvation model (e.g., PCM, SMD) is not stated.
  - **Required correction** Specify the solvation model used and provide a brief justification for the functional/basis set combination.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Docking methodology
  - **Affected element** Section 3.3
  - **Evidence pointer** Section 3.3
  - **Issue** The docking protocol uses a rigid receptor, which may not account for DNA flexibility. The grid box dimensions and spacing are not reported.
  - **Required correction** Report grid box parameters and discuss the limitations of rigid receptor docking for DNA-ligand interactions.

## Technical failings that need to be addressed before the case is established
- R1-M1: DNA binding mode not rigorously established due to lack of positive controls and quantitative CD analysis.
- R1-M2: PET mechanism not directly evidenced; alternative explanations for fluorescence changes not excluded.
- R1-M3: No quantitative binding constants reported, limiting assessment of practical utility.

## Assessment against Nature-style criteria
- **Originality** Moderate. The combination of halochromic hemicyanine dyes with DNA minor groove binding and PET-based fluorescence modulation is somewhat novel, but builds closely on prior work by the same group. The specific substituent effects explored are incremental.
- **Scientific importance** Moderate. The findings could contribute to the design of pH-responsive DNA probes, but the practical advantages over existing probes are not clearly demonstrated. The study is primarily descriptive rather than providing new mechanistic insights.
- **Interdisciplinary readership** Limited. The work bridges synthetic chemistry, photophysics, and DNA binding, but the presentation is specialized and may not attract broad interdisciplinary interest without clearer demonstration of application potential.
- **Technical soundness** Partially adequate. The synthetic and spectroscopic methods are appropriate, but key claims about binding mode and mechanism lack rigorous quantitative support. Computational methods are standard but not fully described.
- **Readability for nonspecialists** Acceptable. The manuscript is generally clear, but some sections assume familiarity with photophysical concepts and docking methodology. The abstract effectively summarizes the work.

## Risk / unsupported claims
- The claim that dyes "have the potential to serve as functional fluorescent probes for monitoring pH variations and nucleic acid dynamics in cancer cells" is speculative and not supported by any cellular or in vivo data.
- The statement that "the obtained results represent an initial step in an ongoing investigation aimed at optimizing the PET-related properties" is appropriate, but the current data do not yet establish practical utility.
- The assertion that fluorescence restoration upon acid addition indicates "suppression of the PET and, at the same time, rigidizing of the chemical structure" is not directly evidenced by the data presented.
- The claim of "excellent binding affinities" for prior compounds (mentioned in the introduction) is not substantiated with data in this manuscript.

## Recommendation posture
**Currently not established from the provided evidence.** The manuscript presents interesting preliminary findings, but the central claims regarding DNA minor groove binding mode and PET-based fluorescence modulation require additional experimental evidence and quantitative analysis. The synthetic work is solid, and the photophysical characterization is systematic, but the mechanistic interpretation and application potential are not yet fully supported. The authors should address the major concerns regarding binding mode validation, fluorescence quantum yields, and direct evidence for PET before the conclusions can be considered robust.