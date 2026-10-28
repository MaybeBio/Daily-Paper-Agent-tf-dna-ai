## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report that the isolated DNA-binding domain (DBD) of Escherichia coli HigA antitoxin is well-folded, binds specifically to palindromic operator DNA sequences from the HigBA promoter region, and that NMR chemical shift perturbation (CSP) experiments identified residues involved in DNA recognition. AlphaFold 3 models of HigA-DNA complexes are stated to match NMR CSP-derived HADDOCK models, revealing the DNA recognition mode.
- **Visible evidence base** Abstract text only; no experimental details, spectra, ITC data, model statistics, or validation metrics are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, NMR assignment completeness, ITC fitting parameters, AlphaFold 3 confidence metrics, HADDOCK model statistics, and any validation of the DNA sequences used

## Reviewer
- **Overall assessment** The abstract presents a focused and potentially useful biophysical characterization of the HigA DBD interaction with its operator DNA. The combination of NMR CSP and ITC with computational modeling is appropriate for the stated goal. However, the abstract alone does not provide sufficient quantitative evidence to assess the robustness of the binding measurements, the specificity claims, or the quality of the structural models. Several key claims, particularly regarding the match between AlphaFold 3 and HADDOCK models, cannot be evaluated without model statistics and comparison metrics.
- **Who would be interested in the results, and why** Researchers studying bacterial toxin-antitoxin systems, transcriptional regulation, and protein-DNA recognition mechanisms. The work may also interest those applying AlphaFold 3 to protein-DNA complex prediction, as it provides a test case comparing computational models with experimental NMR data.
- **Major strengths** The study addresses a clear biological question regarding the molecular basis of operator recognition by a TA system antitoxin. The use of multiple complementary techniques (NMR, ITC, and computational modeling) is methodologically sound. The identification of specific residues involved in DNA recognition via CSP provides residue-level information that is valuable for understanding the interaction.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative binding evidence), R1-M2 (specificity evidence), R1-M3 (model validation)
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The study applies established biophysical methods to a specific TA system; the novelty lies in the specific system and the AlphaFold 3 comparison, but the approach is not methodologically new.  
  - Scientific importance: Moderate. The results contribute to understanding HigBA regulation but do not appear to reveal a fundamentally new mechanism or principle beyond what is known for other TA antitoxins.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to structural biologists and microbiologists working on TA systems; the broader impact beyond these fields is not evident from the abstract.  
  - Technical soundness: Cannot be fully assessed from the abstract. The methods are appropriate, but quantitative results and validation metrics are not provided.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terminology (e.g., CSP, HADDOCK) without explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible study, but the absence of quantitative data and model validation metrics prevents assessment of whether the core claims are supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims that the HigA DBD "binds specifically to the palindromic operator DNA sequences" and that ITC was used to study this binding.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract reports ITC experiments but provides no quantitative binding parameters, such as dissociation constants (Kd), stoichiometry, or thermodynamic parameters (ΔH, ΔS). Without these values, the affinity and the nature of the interaction cannot be assessed.  
- **Why it matters** A central claim of the study is that the DBD binds to the operator DNA. Quantitative binding data are essential to establish that the interaction is specific and biologically relevant, and to compare with other TA antitoxin-DNA interactions.  
- **Resolution test** Provide Kd values with errors from ITC experiments, including the number of replicates, and state whether binding is saturable and consistent with a single-site model.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Specificity of binding  
- **Claim pointer** The abstract claims that the DBD binds "specifically to the palindromic operator DNA sequences."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** Specificity is claimed but no control experiments are described, such as binding to non-specific or mutated DNA sequences. Without such controls, it is unclear whether the observed binding is sequence-specific or merely electrostatic.  
- **Why it matters** The biological function of HigA as a transcriptional repressor depends on sequence-specific recognition of its operator. If specificity is not demonstrated, the relevance of the observed binding to the in vivo function is uncertain.  
- **Resolution test** Include ITC or NMR experiments with non-specific DNA (e.g., a scrambled sequence or a known non-operator sequence) and show that binding is significantly weaker or absent. Alternatively, show that mutations in the palindromic sequence abolish or reduce binding.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model validation  
- **Claim pointer** The abstract claims that "High-confidence AlphaFold 3 models of the HigA-DNA complexes matched well with the NMR CSP-derived HADDOCK models."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The claim of a good match between AlphaFold 3 and HADDOCK models is stated without any quantitative comparison metrics, such as RMSD values, interface overlap, or contact maps. The term "high-confidence" for AlphaFold 3 models is also not defined with specific confidence scores.  
- **Why it matters** The structural models are used to propose the DNA recognition mode. Without quantitative validation, the reliability of the proposed interaction interface is unknown, and the match between the two modeling approaches cannot be independently assessed.  
- **Resolution test** Provide RMSD values between the AlphaFold 3 and HADDOCK models for the protein and DNA components, list the AlphaFold 3 confidence scores (e.g., pLDDT, PAE) for the interface residues, and show a superposition figure or interface residue comparison.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract text  
- **Issue** The abstract states that the DBD is "well-folded in solution" but does not specify the NMR techniques used to assess folding (e.g., 2D 1H-15N HSQC) or the criteria for "well-folded."  
- **Required correction** Specify the NMR experiments used to assess folding and provide a brief description of the spectral characteristics that support the conclusion.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Residue-level information  
- **Evidence pointer** Abstract text  
- **Issue** The abstract mentions that CSP experiments "revealed the residues of the HigA DBD involved in DNA recognition" but does not indicate how many residues were identified or whether they form a contiguous binding surface.  
- **Required correction** State the number of residues with significant CSPs and whether they cluster on a single face of the DBD, as this would support the proposed binding mode.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** DNA sequence definition  
- **Evidence pointer** Abstract text  
- **Issue** The abstract refers to "palindromic operator DNA sequences" but does not provide the actual sequence or its length. This information is necessary for reproducing the experiments and for assessing the biological relevance of the chosen sequence.  
- **Required correction** Include the operator DNA sequence used in the study, or refer to a specific figure or table in the full manuscript where it is provided.

## Risk / unsupported claims
- The claim that the DBD binds "specifically" to the operator DNA is unsupported without control experiments showing lack of binding to non-specific sequences.
- The claim that AlphaFold 3 models "matched well" with HADDOCK models is unsupported without quantitative comparison metrics.
- The claim that the DBD is "well-folded" is weakly supported without spectral data or criteria.
- The biological relevance of the observed binding to transcriptional repression in vivo is not addressed and cannot be assessed from the abstract.