## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report an integrated in-silico workflow (molecular docking, molecular dynamics simulation, MM/PBSA binding free energy calculations) to design beta(3)-amino acid peptidomimetic foldamers targeting the N-terminal domains (NTDs) of STAT3 and STAT4. They claim that three designed peptidomimetics (Peptide-A, Peptide-B, Peptide-C) bind to and impede dimerization of both NTDs, and suggest these compounds merit further exploration in cancer prevention and management.
- **Visible evidence base** Abstract text only; no quantitative results, structural data, simulation parameters, or statistical measures are provided
- **Missing materials affecting confidence** Full manuscript, methods section, docking scores, MD trajectory analyses, MM/PBSA energy components, structural figures, validation metrics, and any experimental or orthogonal validation data

## Reviewer
- **Overall assessment** The abstract presents a plausible computational workflow for designing peptidomimetic inhibitors against STAT3 and STAT4 NTD dimerization. However, the claims of binding and functional inhibition are supported only by qualitative statements with no quantitative data. The absence of docking scores, simulation stability metrics, energy values, and comparative baselines prevents independent evaluation of the central conclusions. The work may be of interest to computational drug discovery groups, but the current evidence base is insufficient to establish the stated claims.
- **Who would be interested in the results, and why** Computational chemists and structural biologists working on protein-protein interaction inhibitors, particularly those targeting STAT signaling pathways in oncology. Researchers developing peptidomimetic scaffolds or foldamer-based therapeutics may also find the design strategy relevant. The potential translational angle toward cancer therapy could attract medicinal chemists, though the current abstract does not provide enough detail to assess practical utility.
- **Major strengths** The study addresses a relevant biological target (STAT NTD dimerization) with a rational design strategy based on interface mimicry. The use of beta(3)-amino acid foldamers is a creative approach that may offer improved proteolytic stability over natural peptides. The integrated computational pipeline (docking, MD, MM/PBSA) is a standard and appropriate combination for initial binding assessment.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative binding data), R1-M2 (no functional inhibition evidence), R1-M3 (no validation of computational predictions), R1-M4 (no comparative or selectivity analysis)
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The use of beta(3)-amino acid foldamers to target STAT NTD dimerization is a novel combination, but the overall approach (docking plus MD plus MM/PBSA) is routine in computational drug discovery.  
  - Scientific importance: Moderate. STAT signaling is a validated cancer target, but the abstract does not demonstrate that the designed compounds offer advantages over existing inhibitors or that the NTD is a druggable interface with proven therapeutic relevance.  
  - Interdisciplinary readership: Limited. The abstract is written for a specialist computational biology audience; the lack of biological validation and quantitative context reduces broader appeal.  
  - Technical soundness: Not assessable from the abstract. No parameters, convergence criteria, force fields, or error estimates are provided.  
  - Readability for nonspecialists: Acceptable but vague. Terms such as "foldamers" and "MM/PBSA" are used without explanation, and the qualitative language ("unequivocally demonstrate") overstates the evidence presented.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a reasonable computational study, but the central claims of binding and dimerization inhibition require quantitative support and ideally orthogonal validation. A revised manuscript with full data could change this assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Our findings unequivocally demonstrate that the peptidomimetic foldamers we have devised (Peptide-A, Peptide-B, and Peptide-C) exhibit a propensity to bind to and impede the dimerization process of the NTDs of both STAT3 and STAT4."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative binding data. No docking scores, binding energies, IC50 values, or affinity constants are reported. The phrase "unequivocally demonstrate" is not supported by any numerical evidence in the abstract.  
- **Why it matters** Without quantitative measures of binding affinity or interaction strength, the claim that these peptidomimetics "bind to" the NTDs is unverifiable. A reader cannot assess whether the binding is specific, strong, or merely a computational artifact.  
- **Resolution test** Provide docking scores (e.g., Glide score, AutoDock Vina score) for each peptidomimetic against both STAT3 and STAT4 NTDs, along with MM/PBSA binding free energies (with standard deviations) and, if available, experimental binding constants.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim scope  
- **Claim pointer** "impede the dimerization process of the NTDs of both STAT3 and STAT4"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract claims that the peptidomimetics impede dimerization, but no functional assay, dimerization assay, or even a computational measure of dimer disruption (e.g., free energy of dimerization in the presence versus absence of the ligand) is described. Docking to a monomeric NTD does not directly demonstrate inhibition of dimer formation.  
- **Why it matters** The stated therapeutic rationale depends on disrupting dimerization. If the compounds only bind to the monomer without affecting the dimer interface, the proposed mechanism of action is not established.  
- **Resolution test** Include a computational or experimental assay that directly measures dimerization inhibition, such as a dimer interface competition assay, a free energy perturbation calculation for dimer stability, or a surface plasmon resonance (SPR) experiment with the dimeric NTD.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation  
- **Claim pointer** "we have deployed an integrated in-silico methodology to rationally design Peptidomimetic foldamers as inhibitors"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No validation of the computational predictions is presented. There is no comparison to known inhibitors, no positive or negative controls in the docking or MD simulations, and no experimental confirmation of binding or activity. The abstract does not mention any attempt to validate the designed compounds in vitro or in vivo.  
- **Why it matters** Computational predictions are hypothesis-generating. Without validation, the claim that these are "potential candidates meriting further exploration" is speculative and does not meet the standard for a conclusive finding.  
- **Resolution test** Add a validation section with either (a) experimental binding or activity data, or (b) a rigorous computational benchmark showing that the docking and MD protocol correctly predicts binding for known STAT NTD ligands or related protein-protein interaction inhibitors.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Selectivity and specificity  
- **Claim pointer** "targeting STAT3 and STAT4 N-terminal domain dimerization"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not address selectivity of the designed peptidomimetics for STAT3 and STAT4 over other STAT family members (STAT1, STAT5, STAT6) or other proteins with similar NTD folds. No off-target analysis or selectivity data are mentioned.  
- **Why it matters** For a therapeutic candidate, selectivity is critical. If the compounds also bind to other STATs or unrelated proteins, the proposed cancer relevance is weakened and potential toxicity increases.  
- **Resolution test** Include a selectivity assessment, such as docking or MD against other STAT NTDs, or a panel of unrelated proteins, and report comparative binding energies or selectivity scores.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "peptidomimetic foldamers" is used without definition or structural context. Readers unfamiliar with foldamer chemistry may not understand what these molecules are.  
- **Required correction** Provide a brief definition or a schematic representation of the foldamer backbone and the beta(3)-amino acid substitution pattern.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No simulation parameters are given, such as force field, water model, simulation length, temperature, or pressure coupling. This prevents replication of the MD simulations.  
- **Required correction** In the full manuscript, specify all MD parameters and software versions. In the abstract, at least mention the simulation timescale and force field.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical rigor  
- **Affected element** Binding free energy reporting  
- **Evidence pointer** Abstract; location not provided  
- **Issue** MM/PBSA calculations are known to be sensitive to the choice of dielectric constant, entropy contributions, and trajectory length. The abstract does not mention any error estimates or replicate runs.  
- **Required correction** Report mean and standard deviation of binding free energies from multiple independent MD runs, and state the entropy treatment or note its omission.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Biological relevance  
- **Affected element** Translational claim  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states these compounds merit exploration in "cancer prevention and management," but no cellular or in vivo context is provided. The link between NTD dimerization inhibition and cancer outcomes is not established in the abstract.  
- **Required correction** Either temper the translational claim or add a brief statement on known functional consequences of STAT NTD dimerization in cancer models.

## Risk / unsupported claims
- The claim that the peptidomimetics "impede the dimerization process" is unsupported by any direct evidence in the abstract.
- The claim of "unequivocally demonstrate" is overstated given the absence of quantitative data.
- The translational relevance to "cancer prevention and management" is not supported by any biological or clinical data in the abstract.
- The selectivity of the compounds for STAT3 and STAT4 over other STATs is not addressed and cannot be assessed.
- The overall binding affinity and stability of the complexes are not quantifiable from the abstract alone.