## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full-text, figures, tables, or supplementary materials were provided for assessment
- **Shared manuscript claim summary** The authors report that two C-terminal truncations of the MarA transcription factor, each containing a single helix-turn-helix (HTH) motif and differing by seven residues (IRSRKMT), retain specific DNA-binding to the marbox sequence as reconstituted dimers. The longer construct (MarA64) supports transcriptional activation and erythromycin tolerance, while the shorter construct (MarA57) forms a transcriptionally inactive complex that suppresses reporter expression below baseline. Computational analyses suggest that the IRSRKMT extension stabilizes a productive dimer interface, and that DNA engagement is required for functional dimerization.
- **Visible evidence base** Abstract text only; no experimental figures, methods details, statistical analyses, or computational model validation are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, statistical details, computational model parameters and validation, strain and construct information, and supplementary materials

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting finding regarding the minimal requirements for DNA binding and transcriptional activation by a single HTH domain from the AraC/XylS family. The central claim, that seven residues gate the transition between a DNA-binding-only state and a transcriptionally active state, is conceptually appealing and could have implications for understanding TF evolution and for synthetic biology applications. However, the evidence base available for assessment is limited to the abstract, which precludes verification of the experimental rigor, the quantitative support for the claims, and the validity of the computational models. The claim that a single HTH domain is sufficient for both DNA binding and transcriptional activation is strong and would require robust experimental demonstration, including appropriate controls and functional assays in vivo. The abstract does not provide sufficient detail to assess whether these standards are met.
- **Who would be interested in the results, and why** Researchers in prokaryotic gene regulation, antimicrobial resistance mechanisms, and transcription factor evolution would find these results relevant. The potential for a minimal, tuneable DNA-binding domain could also interest synthetic biologists working on engineered transcriptional circuits. The structural and mechanistic insights into dimerization and DNA bending may appeal to structural biologists studying protein-DNA interactions.
- **Major strengths** The conceptual framing is clear and addresses an interesting evolutionary question about the origin of two-motif HTH domains. The design of two truncation constructs differing by a defined seven-residue sequence provides a clean experimental variable. The combination of biochemical, biophysical, and computational approaches is appropriate for the question posed.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that a single, correctly dimerized HTH domain is sufficient for both DNA binding and transcriptional activation.
  - **Evidence pointer** Abstract, Results section (location not provided)
  - **Concern** The central claim of the manuscript is that one HTH motif, when properly dimerized, can support both DNA binding and transcriptional activation. The abstract reports EMSA and SEC data supporting DNA binding and dimerization, and functional assays for transcriptional activation. However, the abstract does not provide quantitative data, statistical significance, or details on the controls used to establish that the observed transcriptional activity is specifically due to the MarA64 construct and not to artifacts such as non-specific protein effects, contamination, or indirect effects on reporter expression. The claim that MarA57 suppresses reporter expression below baseline is presented without supporting data or a proposed mechanism that is experimentally tested beyond a suggestion of competitive promoter occupancy.
  - **Why it matters** This claim is the central conclusion of the manuscript. If the evidence is not robust, the conclusion that a single HTH domain is sufficient for transcriptional activation is not established. The field has long considered the two-motif architecture as the minimal functional unit, so overturning this requires high-quality, well-controlled evidence.
  - **Resolution test** Provide quantitative reporter assay data with appropriate positive and negative controls, including a DNA-binding-deficient mutant of MarA64, a non-specific DNA-binding protein control, and statistical analysis across biological replicates. Demonstrate that the transcriptional activation is dependent on the marbox sequence and on the IRSRKMT extension. Show that the suppressive effect of MarA57 is competitive and specific.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract states that molecular dynamics simulations and AlphaFold models suggest that the IRSRKMT extension forms an α-helical element stabilizing a transcriptionally productive dimer interface, and that its loss disrupts quaternary assembly, alters DNA bending, and misaligns RNA polymerase-contacting residues.
  - **Evidence pointer** Abstract, Computational analysis section (location not provided)
  - **Concern** The computational claims are presented as supporting the experimental findings, but the abstract provides no details on the simulation protocols, force fields, simulation timescales, convergence criteria, or the confidence of the AlphaFold models. The claim that free dimers explore non-productive conformations and that functional dimerization occurs upon DNA engagement is a strong mechanistic statement that requires careful validation. Without these details, the reliability of the computational predictions cannot be assessed.
  - **Why it matters** The computational results are used to provide a structural rationale for the experimental observations. If the simulations are not well-converged or the models are low-confidence, the proposed mechanism may be speculative. The claim that DNA engagement drives functional dimerization is particularly important and needs robust support.
  - **Resolution test** Provide details on simulation setup, length, convergence, and replica analyses. Show that the AlphaFold models have high confidence scores for the relevant interfaces. If possible, validate the predicted conformational changes with experimental approaches such as cross-linking, FRET, or hydrogen-deuterium exchange.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and completeness
  - **Claim pointer** The abstract reports that MarA64 confers regular erythromycin tolerance while MarA57 does not.
  - **Evidence pointer** Abstract, Functional assays section (location not provided)
  - **Concern** The functional consequence of the truncations is a key part of the story, linking the biochemical findings to a phenotypic outcome. However, the abstract does not provide any details on the erythromycin tolerance assay, including the strains used, the concentration range of erythromycin, the growth conditions, or the statistical significance of the differences observed. Without these details, the phenotypic claim cannot be evaluated.
  - **Why it matters** The phenotypic data connects the molecular mechanism to a biologically relevant outcome. If the assay is not well-controlled or the effect is small, the biological significance of the finding is weakened.
  - **Resolution test** Provide a full description of the erythromycin tolerance assay, including dose-response curves, statistical analysis, and appropriate controls such as a marA deletion strain and a strain expressing wild-type MarA.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, first sentence
  - **Evidence pointer** Abstract, Introduction (location not provided)
  - **Issue** The opening sentence states that prokaryotic TFs lie at the core of antimicrobial resistance, which is a broad generalization. While MarA is indeed linked to resistance, not all prokaryotic TFs are involved in resistance.
  - **Required correction** Rephrase to specify that certain prokaryotic TFs, such as those in the AraC/XylS family, are involved in antimicrobial resistance.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Abstract, Results
  - **Evidence pointer** Abstract, Results section (location not provided)
  - **Issue** The term "reconstituted dimers" is used to describe the EMSA results. This term is ambiguous and could be interpreted as the dimers being artificially assembled in vitro rather than forming naturally in solution.
  - **Required correction** Clarify whether the dimers form spontaneously in solution or require specific conditions, and use more standard terminology such as "dimerized upon DNA binding" or "formed dimers in solution."
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract, Conclusions
  - **Evidence pointer** Abstract, Conclusions (location not provided)
  - **Issue** The abstract mentions offering a tuneable scaffold for synthetic biology and novel anti-virulence strategies, but no specific examples or potential applications are given.
  - **Required correction** Either provide a brief example of how the scaffold could be tuned or remove the speculative application statement to keep the abstract focused on the findings.

## Risk / unsupported claims

- The claim that a single HTH domain is sufficient for both DNA binding and transcriptional activation is not fully supported by the abstract-level evidence provided. Quantitative functional data and controls are missing.
- The claim that the IRSRKMT extension stabilizes a transcriptionally productive dimer interface is based on computational models whose details and validation are not provided.
- The claim that free dimers explore non-productive conformations and that functional dimerization occurs upon DNA engagement is a mechanistic statement that requires more robust experimental or computational support.
- The phenotypic claim regarding erythromycin tolerance is presented without experimental details and cannot be evaluated.
- The suggestion of competitive promoter occupancy for MarA57 is presented as a hypothesis without direct experimental evidence.