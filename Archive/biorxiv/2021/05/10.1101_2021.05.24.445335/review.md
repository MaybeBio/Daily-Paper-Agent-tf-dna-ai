## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency based solely on the supplied text; no external literature or unpublished data consulted
- **Shared manuscript claim summary** The authors argue that the RGD motif (residues 403-405) in the SARS-CoV-2 spike RBD is unlikely to bind integrins, based on structural analysis, normal mode analysis, accelerated molecular dynamics (aMD) simulations, and protein-protein docking. They report that the RGD motif is conformationally rigid, does not sample integrin-compatible extended geometries, and fails to dock favorably to three RGD-binding integrins.
- **Visible evidence base** Methods sections 2.1-2.5; Results sections 3.1-3.5; Figures 1-5 referenced; Supplementary data 1 and 2 mentioned but not provided
- **Missing materials affecting confidence** Supplementary data files (1 and 2); actual figures and their content; PDB structure list; simulation parameter details; docking scoring data; convergence metrics beyond text description; no raw trajectory or cluster data

## Reviewer
- **Overall assessment** The manuscript addresses a timely and relevant question regarding the putative role of the SARS-CoV-2 RBD RGD motif in integrin binding. The authors combine multiple computational approaches to challenge a previously proposed hypothesis. However, the evidence presented is largely indirect and the manuscript suffers from several technical and presentational weaknesses that limit the strength of the conclusions. The central claim that the RGD motif is unlikely to bind integrins is plausible but not fully established from the provided evidence, particularly given the absence of quantitative docking results and the limited discussion of alternative binding modes.
- **Who would be interested in the results, and why** Researchers studying SARS-CoV-2 entry mechanisms, integrin biology, viral-host interactions, and computational structural biology. The findings could inform experimental studies on alternative receptors or co-receptors and may have implications for therapeutic targeting of the spike protein.
- **Major strengths** The manuscript addresses a specific and testable hypothesis with clear relevance to SARS-CoV-2 pathogenesis. The use of multiple complementary computational methods (NMA, aMD, docking) is appropriate. The authors acknowledge limitations and avoid overclaiming, particularly in the conclusion where they note that integrins may still be receptors via other regions. The discussion of integrin expression patterns in lung epithelium adds biological context.
- **Major Concerns** See items R1-M1 to R1-M5 below.
- **Minor Comments** See items R1-m1 to R1-m5 below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (docking methodology and results), R1-M2 (aMD convergence and validation), R1-M3 (geometric criteria justification), R1-M4 (generality of structural analysis), R1-M5 (lack of quantitative free energy data)
- **Assessment against Nature-style criteria** Originality: Moderate. The question is important but the approach is largely confirmatory of prior structural observations. Scientific importance: Potentially high if the conclusion holds, but the evidence is not yet definitive. Interdisciplinary readership: The topic could appeal to virologists, structural biologists, and cell biologists, but the presentation is heavily computational and may not be accessible to nonspecialists. Technical soundness: Several methodological concerns (see below) undermine confidence. Readability for nonspecialists: The manuscript is generally readable but includes jargon and lacks clear explanations of some computational methods and their limitations.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if technical concerns are resolved and additional quantitative data are provided.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that protein-protein docking shows the inability of the RGD motif to interact with integrins (Section 3.5).
- **Evidence pointer** Section 3.5, Figure 5
- **Concern** The docking results are described only qualitatively. No docking scores, cluster sizes, or statistical measures are provided. The authors state that the RGD motif "was not capable of reaching its native binding site" but do not report any quantitative comparison with positive controls or known integrin-RGD complexes.
- **Why it matters** Without quantitative docking data, the reader cannot assess whether the failure to dock is due to genuine incompatibility or to methodological artifacts (e.g., poor sampling, incorrect active site definition, or scoring function limitations). The claim of "inability" is therefore not supported by the evidence presented.
- **Resolution test** Provide docking scores (e.g., HADDOCK scores, Z-scores) for all three integrins, compare with a positive control (e.g., a known RGD-containing ligand), and report cluster populations and interface statistics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that aMD simulations show no significant conformational shift in the RGD motif or its microenvironment (Sections 3.2, 3.3).
- **Evidence pointer** Section 3.2, Section 3.3, Figures 2 and 3
- **Concern** The aMD methodology is described but key validation metrics are missing. The authors report convergence of cumulative cluster counts and entropy, but do not provide quantitative thresholds or comparisons. The boost parameters are mentioned but not fully specified. The simulation length (1 μs per replicate) is stated, but no assessment of equilibration or sampling adequacy is given.
- **Why it matters** aMD is an enhanced sampling method, but its results depend critically on the choice of boost parameters and the adequacy of sampling. Without validation that the simulations have converged to a representative ensemble, the conclusion that no integrin-compatible conformations are sampled is not robust.
- **Resolution test** Provide boost parameter values, show convergence plots with quantitative criteria, and demonstrate that the simulations sample known functional states (e.g., by comparison with experimental structures of up/down RBD conformations).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the RGD motif cannot acquire an optimal geometry for integrin binding based on the free energy landscape (Section 3.4).
- **Evidence pointer** Section 3.4, Figure 4
- **Concern** The geometric criteria used to define "optimal" integrin-binding geometry (θ angle and Cβ-Cβ distance) are based on prior studies of RGD peptides, but the authors do not justify that these criteria are applicable to the RBD context. The free energy landscape is shown qualitatively, but no error bars or statistical uncertainties are provided. The threshold values for favorable binding (e.g., θ > 140°, distance > 8 Å) are not explicitly stated as criteria for rejection.
- **Why it matters** The conclusion that the RGD motif cannot adopt a binding-competent conformation depends entirely on the chosen geometric descriptors and their thresholds. If these are not well-justified or are too restrictive, the conclusion may be invalid.
- **Resolution test** Justify the geometric criteria with reference to known integrin-RGD complex structures, provide error estimates for the free energy landscape, and show that the criteria are robust to reasonable variations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors generalize from three integrin types (α5β1, αIIbβ3, αVβ8) to conclude that the RGD motif is unlikely to bind integrins (Sections 3.5, 4).
- **Evidence pointer** Section 3.5, Section 4
- **Concern** Only three integrin types were tested, and the authors acknowledge that other RGD-binding integrins (e.g., αVβ5, αVβ6) are expressed in lung epithelium. The homology argument is mentioned but not substantiated with structural alignments or sequence comparisons. The conclusion that the RGD motif is "unlikely" to bind integrins is therefore broader than the evidence supports.
- **Why it matters** The manuscript's central claim is about integrins in general, but the evidence is limited to a small subset. If other integrins have different binding site geometries or accommodate different RGD conformations, the conclusion may not hold.
- **Resolution test** Include additional integrin types, or provide structural evidence that the tested integrins are representative of all RGD-binding integrins relevant to SARS-CoV-2 infection.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors suggest that other residues may stabilize integrin binding if integrins are confirmed as receptors (Abstract, Section 4).
- **Evidence pointer** Abstract, Section 4
- **Concern** This suggestion is speculative and not supported by any data in the manuscript. No alternative binding sites or residues are identified or tested.
- **Why it matters** While speculative suggestions can be valuable, this claim is presented without any supporting evidence or proposed mechanism, which weakens the overall scientific rigor.
- **Resolution test** Either remove the speculation or provide preliminary data (e.g., docking with alternative RBD regions, mutational analysis) to support the suggestion.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The aMD boost equation is mentioned but not shown. The text states "as follows" but the equation is missing.
- **Required correction** Include the equation for the boost potential or refer to a specific equation number.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5
- **Issue** The definition of active and passive residues for docking is incomplete. The authors state that residues within 7 Å of the bound RGD were used, but do not specify which atoms or how the bound RGD was defined for each integrin.
- **Required correction** Provide a clear description of active/passive residue selection for each integrin, including the reference structure used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1, Figure 1
- **Issue** The PCA plot in Figure 1C is described but the interpretation is unclear. The authors state that "variances along PC1 and PC2 can be attributed to few structures" but do not explain which structures or why.
- **Required correction** Clarify which structures contribute to the variance and what this implies for the conformational analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Section 4
- **Evidence pointer** Section 4
- **Issue** The discussion of integrin expression patterns is useful but lacks citations for several key claims (e.g., "αVβ6 is poorly expressed in lung epithelium cells").
- **Required correction** Add appropriate references for all expression and functional claims.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The criteria for selecting the 90 PDB structures are not described. The authors state "all the structures with complete 3D coordinates of the RBD were explored" but do not specify the search strategy or inclusion/exclusion criteria.
- **Required correction** Describe the database search, filters, and any redundancy removal steps.

## Risk / unsupported claims
- The claim that the RGD motif "could not acquire an optimal geometry" for integrin binding is not fully supported because the geometric criteria are not justified and the free energy landscape lacks error estimates.
- The claim that docking shows "inability" of the RGD motif to interact with integrins is unsupported without quantitative docking scores and positive controls.
- The suggestion that "other residues" may stabilize integrin binding is speculative and not backed by any data.
- The generalization from three integrin types to a broad conclusion about integrin binding is not fully supported.
- The statement that the RGD motif is "unlikely" to bind integrins is presented as a strong conclusion, but the evidence is indirect and computational only; no experimental validation is provided.