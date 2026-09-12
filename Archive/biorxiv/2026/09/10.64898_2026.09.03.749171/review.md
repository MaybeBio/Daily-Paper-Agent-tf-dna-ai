## Review setup
- **Input scope** Full manuscript (abstract and significance statement)
- **Assessment boundary** Structural and biochemical analysis of the P-TEFb–BRD4 interaction
- **Shared manuscript claim summary** The authors present a cryo-EM structure of P-TEFb bound to the BRD4 PID, showing that BRD4 interacts with the CDK9 C-lobe and CYCT1 second cyclin domain, that this surface overlaps with the AFF4 binding site, that BRD4 may remodel the CDK9 αC helix to stimulate activity, and that both BRD4-PID and the AFF4 N-terminus can release P-TEFb from the 7SK RNP complex.
- **Visible evidence base** Abstract and significance statement only; no figures, tables, methods, or supplementary data provided.
- **Missing materials affecting confidence** Full manuscript text, all figures (including cryo-EM maps, model coordinates, biochemical data), methods, supplementary information, and data availability statements.

## Reviewer
- **Overall assessment** The claims presented in the abstract are potentially significant for the transcription field, but the current evidence base is insufficient to evaluate their validity. The abstract describes a cryo-EM structure and biochemical experiments, but without access to the actual data, maps, models, and experimental details, a meaningful assessment of technical soundness or support for the conclusions is impossible.
- **Who would be interested in the results, and why** Researchers in transcription regulation, structural biology of transcription complexes, and those studying CDK9/P-TEFb as a therapeutic target in cancer and HIV. The work addresses a long-standing question about how BRD4 stimulates P-TEFb, which is central to understanding Pol II elongation control.
- **Major strengths** The question is well-motivated and of high importance. The combination of cryo-EM, AlphaFold modeling, and biochemical probing is appropriate. The comparison with AFF4 binding and the 7SK RNP release experiments suggest a comprehensive approach.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "Using cryogenic-electron microscopy, AlphaFold modeling, and biochemical probing, we show that the P-TEFb interacting domain of BRD4 (BRD4-PID) interacts with P-TEFb via the C-lobe of CDK9 and the second cyclin domain of CYCT1."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The abstract states a cryo-EM structure was determined, but no resolution, map quality metrics (e.g., FSC curves, local resolution), or model validation statistics (e.g., MolProbity scores, Ramachandran statistics) are provided. Without these, the reliability of the atomic model cannot be assessed.
    - **Why it matters** The central claim of the paper rests on the structural model. If the map is of insufficient resolution to unambiguously assign side-chain interactions or if the model is overfitted, the specific binding interface described may be incorrect.
    - **Resolution test** Provide the cryo-EM map and model in a public repository (e.g., EMDB, PDB) and include key validation metrics in the main text or supplement. Show that the map supports the proposed interactions at the reported resolution.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Claim support
    - **Claim pointer** "Our analysis indicates that BRD4 may stimulate P-TEFb activity by remodeling the kinase αC helix relative to previous structures."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The claim of αC helix remodeling is based on a comparison with "previous structures," but no specific structures are cited, and no quantitative measure of the remodeling (e.g., RMSD, dihedral angle changes) is described. The word "may" indicates uncertainty, but the structural basis for this inference is unclear.
    - **Why it matters** This is a key mechanistic claim that distinguishes the BRD4-bound state from other P-TEFb complexes. Without a direct comparison to a relevant apo or inhibitor-bound structure under the same conditions, the remodeling could be an artifact of crystallization or cryo-EM conditions.
    - **Resolution test** Provide a clear superposition of the BRD4-bound structure with at least one previously published P-TEFb structure (e.g., PDB ID), and show that the αC helix conformation is significantly different (e.g., >1 Å RMSD for backbone atoms). Include a functional assay (e.g., kinase activity with αC helix mutants) to support the functional relevance.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "We show that in addition to BRD4-PID, the AFF4 N-terminus can release P-TEFb from the 7SK RNP complex."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The abstract does not describe the experimental system used to demonstrate 7SK RNP release (e.g., in vitro reconstitution, cellular assays, pull-downs). The specificity of the release (e.g., is it competitive? does it require other factors?) and the concentrations used are not mentioned.
    - **Why it matters** The 7SK RNP is a large, multi-component complex. Demonstrating that a short peptide (BRD4-PID or AFF4 N-terminus) can displace P-TEFb from this complex is a strong claim that requires rigorous controls, including showing that the release is not due to non-specific disruption of the RNP.
    - **Resolution test** Provide the experimental details (e.g., gel filtration, fluorescence anisotropy, or cellular FRET assays) and show dose-response curves, negative controls (e.g., a scrambled peptide), and evidence that the 7SK RNP remains intact after P-TEFb release.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Abstract
    - **Evidence pointer** Abstract; location not provided
    - **Issue** The abstract states "P-TEFb activity is restricted when bound to the 7SK RNP complex" but does not explain how this relates to the BRD4 structure. The logical flow from the BRD4 structure to the 7SK release experiments is unclear.
    - **Required correction** Add a sentence clarifying the connection, e.g., "Because BRD4 and AFF4 share a binding surface on CDK9, we tested whether they could compete with the 7SK RNP for P-TEFb binding."

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Abstract
    - **Evidence pointer** Abstract; location not provided
    - **Issue** The abstract mentions "AlphaFold modeling" but does not specify what was modeled (e.g., the full-length BRD4-PID, the complex, or a region not resolved in cryo-EM) or how it was used (e.g., to guide model building, to predict a flexible region).
    - **Required correction** Briefly describe the role of AlphaFold, e.g., "AlphaFold2 was used to model the BRD4-PID region not resolved in the cryo-EM map."

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. All three major concerns are blocking because the core structural and functional claims cannot be evaluated from the abstract alone.
- **Assessment against Nature-style criteria**
    - **Originality**: The claim of a BRD4-PID structure bound to P-TEFb is novel and addresses a gap in the field. The comparison with AFF4 and the 7SK release experiments adds mechanistic insight.
    - **Scientific importance**: High. Understanding how BRD4 stimulates P-TEFb is central to transcription elongation control and has implications for cancer therapeutics targeting BRD4 or CDK9.
    - **Interdisciplinary readership**: Moderate. The work will primarily interest structural biologists and transcription biochemists, but the broader implications for gene regulation and drug discovery could attract a wider audience.
    - **Technical soundness**: Cannot be assessed from the abstract. The cryo-EM resolution, model quality, and biochemical controls are not described.
    - **Readability for nonspecialists**: The abstract is clear and well-structured, but the significance statement is somewhat redundant.
- **Recommendation posture** Currently not established from the provided evidence. The claims are potentially important, but the abstract alone does not provide sufficient data to assess technical soundness or support for the conclusions. A full manuscript with figures, methods, and validation data is required for a proper evaluation.