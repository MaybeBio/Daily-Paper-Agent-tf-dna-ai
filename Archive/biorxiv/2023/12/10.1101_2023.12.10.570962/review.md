## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors report the crystal structure of the Legionella collagen-like protein C-terminal domain (Lcl-CTD), showing it forms a trimer with a positively charged external surface and negatively charged internal cavity. They propose a unique GAG binding mechanism involving lysine residues on the upper surface, supported by mutagenesis, ELISA, NMR, and molecular dynamics simulations. They also present evidence for surface localization of Lcl in strain 130b and propose an N-terminal amphipathic helix as a membrane anchor.
- **Visible evidence base** SEC-MALS, rotary shadowing EM, X-ray crystallography (Se-SAD at 1.9 Å), SAXS, CD spectroscopy, NMR (including TROSY titrations), HADDOCK docking, MD simulations, whole-cell ELISA, immunoblot analysis
- **Missing materials affecting confidence** Supplementary figures and tables (including Supplementary Tables 1-9, Supplementary Figures 1-19), crystallographic refinement statistics details, NMR assignment completeness details, MD simulation convergence analyses, raw data for ELISA and binding assays, sequence alignments for phylogenetic analysis

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biophysically detailed characterization of the Lcl C-terminal domain and its interaction with glycosaminoglycans. The work addresses an important gap in understanding Legionella adhesion mechanisms. The crystallographic structure is likely novel and the combination of experimental approaches is commendable. However, several technical concerns regarding the interpretation of the binding mechanism, the strength of the MD-based conclusions, and the generalizability of the proposed model require careful consideration. The claim of a "unique binding mechanism" is not fully substantiated by the data presented, and the functional relevance of the proposed surface binding mode requires additional experimental support.
- **Who would be interested in the results, and why** Researchers studying bacterial adhesion mechanisms, particularly in Legionella pneumophila; structural biologists interested in collagen-like proteins and trimeric adhesins; glycobiologists studying protein-glycosaminoglycan interactions; and investigators working on host-pathogen interactions in the lung. The potential broader distribution of Lcl homologs across Pseudomonadota and FCB phyla may also interest evolutionary microbiologists.
- **Major strengths** 1) The crystal structure of Lcl-CTD at 1.9 Å resolution provides a solid structural foundation. 2) The combination of multiple biophysical techniques (MALS, SAXS, NMR, CD, EM) to characterize the full-length protein and its domains is thorough. 3) The identification of a potential N-terminal membrane anchor mechanism is novel and interesting. 4) The phylogenetic analysis suggesting broader distribution of Lcl-like proteins adds evolutionary context. 5) The integration of experimental and computational approaches (HADDOCK, MD) is appropriate for studying dynamic protein-carbohydrate interactions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding mechanism interpretation), R1-M2 (MD-based conclusions), R1-M3 (mutagenesis validation), R1-M4 (specificity claims)
- **Assessment against Nature-style criteria** 
  - **Originality**: The structure of Lcl-CTD appears novel, and the proposed trimeric arrangement with a charged internal cavity is unusual. However, the "unique binding mechanism" claim requires more careful benchmarking against known GAG-binding proteins. The concept of using a positively charged surface for GAG recognition is not entirely new in the field.
  - **Scientific importance**: Understanding Legionella adhesion is clinically relevant given the severity of Legionnaires' disease. However, the direct link between the structural findings and infection biology is not experimentally demonstrated, limiting the immediate translational significance.
  - **Interdisciplinary readership**: The work bridges structural biology, microbiology, and glycobiology, which could appeal to a broad audience. However, the specialized nature of some analyses (particularly the MD simulations) may limit accessibility.
  - **Technical soundness**: The experimental design is generally sound, but several concerns (detailed below) regarding data interpretation, particularly around the MD simulations and the mutagenesis validation, need to be addressed.
  - **Readability for nonspecialists**: The manuscript is reasonably well-written, but the results section would benefit from clearer explanations of the significance of key findings for readers outside the immediate field.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural data are valuable, but the central claims regarding the binding mechanism and its uniqueness require additional experimental validation and more careful interpretation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claims vs evidence
- **Claim pointer** The authors claim that Lcl-CTD employs a "unique binding mechanism" for GAG recognition, with the primary role of lysine residues being "to provide general electrostatic attraction for the GAGs, rather than specific recognition."
- **Evidence pointer** Results section "GAGs bind the charged surface of Lcl-CTD"; Figure 4b; Figure 6b,c; Supplementary Tables 6,7
- **Concern** The claim of a "unique binding mechanism" is not adequately supported by the data. The observation that lysine residues provide electrostatic attraction rather than specific recognition is not unprecedented among GAG-binding proteins. Many proteins use electrostatic complementarity as a primary driving force for GAG binding. To substantiate the "unique" claim, the authors should compare their binding mode with known GAG-binding protein structures and demonstrate how their mechanism differs fundamentally. Additionally, the MD simulations show that C4S binds to multiple locations on the surface with different modes, which suggests a relatively nonspecific electrostatic interaction rather than a defined binding mechanism. The authors should either temper their claims or provide additional data (e.g., detailed thermodynamic characterization, comparison with other GAG-binding proteins) to support the uniqueness of the mechanism.
- **Why it matters** The central claim of the manuscript rests on the novelty of the binding mechanism. If the mechanism is not truly unique, the significance of the work is substantially diminished. Overclaiming novelty without sufficient comparative analysis could mislead the field.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use MD simulations to identify "two predominant binding modes" for C4S dp8 binding to Lcl-CTD, and conclude that the protein surface "is involved in sampling" the GAG.
- **Evidence pointer** Results section "C4S binds Lcl-CTD across multiple domains"; Figure 6; Methods section "Molecular Dynamics"
- **Concern** The MD simulation methodology and analysis raise several concerns. First, the simulation time of 150 ns per replica (20 replicas) may be insufficient to achieve converged binding modes for a highly flexible GAG molecule. The authors should provide convergence analyses (e.g., RMSD vs time plots, block averaging) to demonstrate that the observed binding modes are stable. Second, the clustering analysis uses a very large cutoff (17.5 Å) on Cα RMSD, which may group structurally distinct binding modes together. The authors should justify this choice and show that the resulting clusters are meaningful. Third, the force field parameters for C4S (GLYCAM-06j) and the protein (Amber99SB*-ILDN) are appropriate, but the authors should discuss potential limitations of these force fields for studying protein-GAG interactions. Finally, the authors state that "the glycan remained in contact with Lcl-CTD in all but one replica," but the frequency of contacts (Figure 6c) appears relatively low for many residues, suggesting weak or transient interactions. The authors should provide a more quantitative analysis of binding stability.
- **Why it matters** The MD simulations are central to the proposed binding mechanism. If the simulations are not converged or the analysis is not robust, the conclusions drawn from them are unreliable. This could undermine the entire mechanistic model presented.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors created alanine mutations (R342A, K369A, K380A, K385A, K391A, D386A, E368A) in Lcl-CTD and tested their effect on GAG binding using ELISA, concluding that lysine residues on the upper surface are important for binding.
- **Evidence pointer** Results section "GAGs bind the charged surface of Lcl-CTD"; Figure 4b; Methods section "GAG binding ELISA"
- **Concern** The manuscript does not provide sufficient detail on the mutagenesis strategy and validation. Specifically: 1) Were the mutant proteins verified to be properly folded and trimeric? The authors state that SAXS was used to confirm correct folding for most mutants, but the data are only shown in Supplementary Figure 12, which was not available for review. 2) The R342A mutant dissociated into monomers, yet the authors still included it in the analysis. This is problematic because the loss of binding could be due to loss of trimeric structure rather than loss of a specific binding residue. 3) The ELISA assay uses immobilized GAGs, which may not accurately reflect the presentation of GAGs on cell surfaces. 4) The authors should provide dose-response curves or affinity measurements to quantify the effect of mutations, rather than just endpoint readings at a single concentration.
- **Why it matters** The mutagenesis data are key evidence for the proposed binding mechanism. If the mutant proteins are not properly folded or the assay is not quantitative, the conclusions about which residues are important for binding are not reliable.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claims vs evidence
- **Claim pointer** The authors state that "Lcl homologs are present across both the Pseudomonadota and Fibrobacterota-Chlorobiota-Bacteroidota phyla and suggest that Lcl may represent a versatile carbohydrate binding mechanism."
- **Evidence pointer** Results section "Overall structure of Lcl-CTD"; Supplementary Table 5
- **Concern** The phylogenetic analysis is only briefly mentioned and the supporting data (Supplementary Table 5) were not available for review. The claim of a "versatile carbohydrate binding mechanism" is speculative and not directly tested. The authors have only demonstrated binding to C4S and heparin. To support the claim of versatility, they would need to test a broader range of GAGs and other carbohydrates. Additionally, the functional significance of Lcl homologs in other bacterial species is not discussed. Are these species also pathogens? Do they interact with similar host tissues? Without this context, the evolutionary and functional implications of the homolog distribution are unclear.
- **Why it matters** The claim of versatility and broad distribution is used to suggest broader significance of the work. If this claim is not well-supported, the impact of the study is reduced.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that Lcl is an "extracellular peripheral membrane protein" but the mechanism of membrane association (via the N-terminal amphipathic helix) is only described later in the results. The abstract could be clearer about this distinction.
- **Required correction** Consider revising the abstract to briefly mention the N-terminal amphipathic helix as the membrane anchor.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Results section "Overall structure of Lcl-CTD"
- **Evidence pointer** Figure 3c
- **Issue** The authors state that the trimer is stabilized by "burial of an unusually small surface area per subunit (∼14,000 Å²)". This value seems large for a "small" surface area. Please clarify whether this is the total buried surface area per subunit or the interface area. Typical protein-protein interfaces bury approximately 1,500-2,000 Å² per subunit.
- **Required correction** Clarify the calculation and provide context for what constitutes "unusually small" in comparison to other trimeric proteins.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "GAGs bind the charged surface of Lcl-CTD"
- **Evidence pointer** Figure 4b
- **Issue** The ELISA data for mutant binding are presented as a bar graph, but the statistical analysis is not described. Were biological replicates performed? What statistical test was used?
- **Required correction** Provide details on replicates and statistical analysis in the figure legend or methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors discuss the potential role of the negatively charged internal cavity but do not propose a specific function. This is an interesting feature that warrants more speculation or experimental suggestions.
- **Required correction** Consider adding a brief discussion of potential functions for the internal cavity, such as metal ion binding or small molecule sequestration.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Molecular Dynamics"
- **Evidence pointer** Methods section
- **Issue** The methods for MD simulations lack important details, including the specific GROMACS version, the thermostat/barostat algorithms used, the equilibration protocol, and the criteria for determining when simulations reached equilibrium.
- **Required correction** Provide complete simulation parameters to ensure reproducibility.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "C4S binds Lcl-CTD across multiple domains"
- **Evidence pointer** Figure 7
- **Issue** The description of the three binding modes is somewhat confusing. The authors state that modes 1 and 3 were combined due to symmetry, but the criteria for this combination are not clearly explained.
- **Required correction** Clarify the symmetry considerations and provide a clearer description of the distinct binding modes.

## Risk / unsupported claims
- The claim of a "unique binding mechanism" is not supported by comparative analysis with known GAG-binding proteins.
- The claim that Lcl represents a "versatile carbohydrate binding mechanism" is speculative and not tested experimentally.
- The functional significance of the negatively charged internal cavity is not addressed.
- The phylogenetic distribution claim relies on Supplementary Table 5, which was not available for review.
- The statement that the N-terminal amphipathic helix acts as a membrane anchor is based on indirect evidence (NMR with SDS micelles) and requires further validation.
- The two-state unfolding model for Lcl (Tm values of 38°C and 44°C) is presented without discussion of what structural transitions these correspond to.