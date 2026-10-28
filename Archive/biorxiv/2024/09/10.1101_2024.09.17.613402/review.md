## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological soundness, validity of claims relative to presented evidence; not language editing or formatting
- **Shared manuscript claim summary** The authors use residue-resolution coarse-grained molecular dynamics simulations to predict DNA binding patches on human cohesin subunits (SMC1, SMC3, STAG1, NIPBL), validate these against prior mutagenesis data, and construct a whole-complex model to propose cooperative DNA binding and bending during loop extrusion
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Materials and Methods; Figures 1-5 referenced but not provided; Tables 1-2 referenced but not provided; Supplementary figures referenced but not provided
- **Missing materials affecting confidence** Figures, tables, and supplementary materials are referenced but not included in the provided text; simulation trajectories and analysis code not provided; specific numerical results for dissociation rate constants are partially given in text but full dataset is in Table 1

## Reviewer

### Overall assessment
This manuscript presents a computational study aimed at identifying DNA binding sites on human cohesin subunits using residue-resolution coarse-grained MD simulations. The work addresses an important question in the field of SMC biology, namely the molecular basis of DNA loop extrusion. The methodological approach is reasonable and builds on established coarse-grained models. However, the manuscript as presented has several significant limitations. The absence of figures and tables makes it impossible to fully evaluate the structural models, the predicted binding patches, and the quantitative results. The validation against mutagenesis data is described but the specific comparisons are not shown. The connection between predicted binding patches and the proposed loop extrusion mechanism is largely speculative. The authors acknowledge several important caveats, including the use of elevated ionic strength and the lack of direct timescale correspondence, but the implications of these choices for the biological relevance of the findings are not fully addressed. The manuscript would benefit from a more critical discussion of model limitations and a clearer presentation of the evidence supporting the central claims.

### Who would be interested in the results, and why
Researchers studying SMC complexes, cohesin biology, chromatin organization, and DNA loop extrusion would be the primary audience. The predicted DNA binding sites provide testable hypotheses for experimental validation, which could be of interest to both computational and experimental groups working on these systems. The methodological approach may also be of interest to those developing coarse-grained models for protein-DNA interactions.

### Major strengths
1. The study addresses a biologically important and timely question regarding the molecular mechanism of cohesin-mediated DNA loop extrusion
2. The use of residue-resolution coarse-grained MD simulations is appropriate for studying large protein-DNA systems where all-atom simulations would be computationally prohibitive
3. The authors validate their predictions against previously published mutagenesis data, which strengthens the credibility of their approach
4. The construction of a whole-complex model and the analysis of cooperative DNA binding provide a useful framework for understanding how multiple binding sites may function together
5. The study generates experimentally testable predictions, which is a valuable contribution to the field

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim to have identified and quantified DNA binding patches on each cohesin subunit, with dissociation rate constants used as a proxy for affinity
- **Evidence pointer** Results section, Figures 2-4, Table 1; figures and table not provided
- **Concern** The central quantitative results of this study, namely the identified binding patches and their dissociation rate constants, are presented in figures and tables that are not included in the provided material. Without these data, it is impossible to evaluate the robustness of the binding patch identification, the statistical significance of the affinity differences between patches, or the validity of the ranking of patch strengths. The text describes the methodology but does not provide sufficient numerical detail to assess the results independently.
- **Why it matters** The identification and ranking of DNA binding patches is the foundational claim of the manuscript. If this evidence cannot be evaluated, the entire study rests on unverifiable assertions.
- **Resolution test** Provide the figures and tables with clear annotations, including the specific residues in each patch, the dissociation rate constants with error estimates, and the statistical comparison between patches.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation adequacy
- **Claim pointer** The authors state that predicted DNA binding patches overlap with residues identified in previous mutagenesis studies, validating their simulation results
- **Evidence pointer** Results section, Figure 4F-H, Table 2; figure and table not provided
- **Concern** The validation against mutagenesis data is described qualitatively in the text, but the specific comparisons are not shown. It is unclear how many of the predicted patches overlap with mutagenesis-identified residues, whether the overlap is statistically significant, and whether the mutagenesis data were used to calibrate or select the simulation parameters. The claim of validation requires a systematic and quantitative comparison.
- **Why it matters** Validation against experimental data is a key strength of the study. Without a clear and quantitative presentation of this comparison, the claim of validation is not substantiated.
- **Resolution test** Provide a systematic comparison table or figure showing the overlap between predicted patches and mutagenesis-identified residues, with statistical analysis of the significance of the overlap.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model limitations
- **Claim pointer** The authors use elevated ionic strength (300 mM) and a low friction parameter to speed up simulations, and state that the timescales do not represent actual in vivo timescales
- **Evidence pointer** Materials and Methods, DNA binding simulation assays section
- **Concern** The use of 300 mM ionic strength, which is higher than physiological conditions, could significantly affect electrostatic interactions between the protein and DNA. The authors acknowledge this but do not discuss the potential impact on the identified binding sites or their relative affinities. The low friction parameter in Langevin dynamics can also affect the dynamics and kinetics of binding. The manuscript does not address how these choices might bias the results or whether control simulations at physiological ionic strength were performed.
- **Why it matters** The quantitative claims about binding affinities and the ranking of patches could be affected by the non-physiological simulation conditions. Without addressing this, the biological relevance of the findings is uncertain.
- **Resolution test** Discuss the potential effects of elevated ionic strength and low friction on the results, or provide control simulations at physiological conditions to demonstrate the robustness of the findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors propose that a group of DNA binding patches on SMC1, SMC3, STAG1, and NIPBL forms a "DNA clamping patch group" that facilitates DNA bending and capture during loop extrusion
- **Evidence pointer** Results section, Figure 5; figure not provided
- **Concern** The proposed mechanistic role of the identified patch group is based on the spatial arrangement of patches in the whole-complex model and on simulations with a single DNA placement. The authors do not test alternative DNA binding modes or provide evidence that the observed bending is specifically due to the patch group rather than to the intrinsic flexibility of DNA or non-specific electrostatic interactions. The connection between the predicted patch group and the loop extrusion mechanism remains speculative.
- **Why it matters** The mechanistic interpretation is a major conclusion of the study. Without additional evidence, such as mutational analysis in silico or simulations with modified patch residues, the proposed role of the patch group is not established.
- **Resolution test** Perform additional simulations with mutated patch residues to demonstrate that the DNA bending and binding stability depend specifically on the identified patches, or provide alternative evidence supporting the proposed mechanism.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Model construction
- **Claim pointer** The authors constructed a whole-cohesin complex model using AlphaFold predictions and steered MD simulations to assemble the complex in the gripping state
- **Evidence pointer** Materials and Methods, Modeling of the whole cohesin complex in gripping state section
- **Concern** The construction of the whole-complex model involves multiple steps of steered MD with harmonic restraints and potential switching. The text describes the protocol but does not provide validation of the final model, such as comparison with the cryo-EM structure in terms of root-mean-square deviation, contact maps, or other structural metrics. The reliability of the model depends on the accuracy of the assembly procedure.
- **Why it matters** The whole-complex model is used to map the predicted binding patches and to draw conclusions about their spatial relationships. If the model is not validated, the conclusions based on it are uncertain.
- **Resolution test** Provide structural validation of the final model against the cryo-EM reference, including quantitative metrics of structural similarity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, DNA binding-patch calling section
- **Evidence pointer** Materials and Methods, DNA binding-patch calling and dissociation rate constant calculation section
- **Issue** The description of the Jaccard distance-based clustering is incomplete. The formula is partially given but the full definition is not provided. The choice of clustering parameters and the criteria for defining a "patch" are not fully specified.
- **Required correction** Provide the complete formula for the Jaccard distance, specify the clustering algorithm parameters, and define the minimum number of residues and the spatial criteria for a patch.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, DNA binding simulation assays section
- **Evidence pointer** Materials and Methods, DNA binding simulation assays section
- **Issue** The simulation time for each trajectory is given as 10^8 steps with a timestep of 0.15 fs, but the total simulated time is not stated. The equilibration protocol and the criteria for reaching steady state are not described.
- **Required correction** State the total simulated time per trajectory, describe the equilibration procedure, and specify how the authors determined that the simulations reached a steady state for the binding analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results, dissociation rate constant calculations
- **Evidence pointer** Results section, Figure 3D, Figure S5
- **Issue** The fitting of survival probabilities to a sum of two exponentials is described, but the criteria for selecting the breakpoint between transient and stable binding modes are not fully detailed. The error estimates for the dissociation rate constants are not reported in the text.
- **Required correction** Describe the breakpoint selection procedure in more detail and report the dissociation rate constants with confidence intervals or standard errors.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors discuss the implications of their findings for the DNA segment capture model but do not compare their results with other proposed models of loop extrusion in sufficient detail. The relationship between their predicted binding sites and those identified in other computational or experimental studies is not discussed.
- **Required correction** Expand the discussion to include a more comprehensive comparison with other models and with binding sites identified in other studies.

### Technical failings that need to be addressed before the case is established
R1-M1 (missing quantitative evidence), R1-M2 (incomplete validation), R1-M3 (unaddressed model limitations), R1-M4 (speculative mechanistic interpretation), R1-M5 (unvalidated complex model)

### Assessment against Nature-style criteria
**Originality** The study applies established coarse-grained MD methods to a new system, human cohesin, and provides predictions of DNA binding sites. While the approach is not entirely novel, the specific application and the whole-complex modeling are of interest. The originality is moderate.

**Scientific importance** The question of how cohesin mediates DNA loop extrusion is of high importance in chromosome biology. The predicted binding sites provide testable hypotheses. However, the study is purely computational and the biological significance of the findings depends on experimental validation. The importance is potentially high but not yet established.

**Interdisciplinary readership** The topic is relevant to researchers in molecular biology, biophysics, and computational biology. The manuscript is written in a way that is accessible to these communities, though some technical details of the simulation methods may be challenging for non-specialists.

**Technical soundness** The methodological approach is reasonable, but several concerns remain. The use of elevated ionic strength and low friction parameters may affect the results. The validation of the whole-complex model is not presented. The statistical analysis of binding patch identification and rate constant estimation is not fully described. The technical soundness is currently not fully established.

**Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. However, the results section relies heavily on figures and tables that are not provided, making it difficult to follow the narrative. The methods section is detailed but assumes familiarity with coarse-grained simulation techniques.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important question and the methodological approach is reasonable, but the absence of figures and tables prevents evaluation of the central results. The validation against mutagenesis data is described but not shown. The model limitations are acknowledged but not adequately addressed. The mechanistic interpretation is speculative. The manuscript has potential but requires substantial revision and additional analysis before the claims can be considered established.

## Risk / unsupported claims
1. The claim that specific DNA binding patches were identified and ranked by affinity is not supported by the provided evidence, as the relevant figures and tables are missing.
2. The claim that predicted patches overlap with mutagenesis-identified residues is not quantitatively supported, as the comparison is not shown.
3. The claim that the identified patch group facilitates DNA bending and capture is not directly supported by the simulations, as alternative explanations are not excluded.
4. The claim that the whole-cohesin complex model accurately represents the gripping state is not supported by structural validation data.
5. The claim that the study provides experimentally testable predictions is reasonable, but the specificity and novelty of these predictions relative to existing knowledge cannot be fully assessed without the missing data.