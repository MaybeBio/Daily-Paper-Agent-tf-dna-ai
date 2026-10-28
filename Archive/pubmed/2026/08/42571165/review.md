## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusion, and figure/table legends.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the evidence presented, and alignment with Nature-style criteria. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors present a computational pipeline that filters 28,361 peptide sequences from public databases down to four candidate antimicrobial peptides predicted to be non-toxic, non-hemolytic, stable, and capable of binding the DnaA protein of multidrug-resistant *Klebsiella pneumoniae*. The central claim is that these four peptides, particularly Peptide 3, are promising candidates for experimental validation as inhibitors of DnaA-mediated DNA replication.
- **Visible evidence base** Abstract; Introduction; Methods sections 2.1–2.8; Results sections 3.1–3.7; Discussion; Conclusion; Figures 1–16; Tables 1–2; Data availability statement.
- **Missing materials affecting confidence** No supplementary data files, no raw prediction outputs from individual tools, no sequence alignments, no PDB files of predicted structures, no docking pose coordinates, no code or scripts for the filtering pipeline, and no experimental validation data. The manuscript states that data are available upon request, but none were provided for review.

## Reviewer
- **Overall assessment** This manuscript describes a straightforward, multi-step in silico filtering workflow for antimicrobial peptide discovery. The pipeline is logical and the use of consensus prediction across multiple tools is a reasonable strategy to reduce false positives. However, the study is entirely computational and the central claims of "promising candidates" and "potential inhibition" rest on docking scores and binding predictions that are not experimentally validated. The novelty is limited, as similar in silico AMP discovery pipelines have been published previously, and the specific claim of targeting DnaA is not supported by functional assays or even by rigorous binding free energy calculations beyond docking scores. The manuscript is clearly written and accessible, but the scientific impact is modest and the evidence base is insufficient to establish the stated conclusions.
- **Who would be interested in the results, and why** Researchers in antimicrobial peptide discovery, computational biology, and drug resistance may find the pipeline useful as a template for prioritizing peptide candidates. Those specifically working on *K. pneumoniae* or on DnaA as a drug target may have interest, though they would require experimental follow-up to assess relevance. The work is more likely to appeal to a specialized audience in bioinformatics and peptide engineering than to a broad interdisciplinary readership.
- **Major strengths** The filtering strategy is systematic and transparent, with clear criteria at each step. The use of three independent prediction tools for activity, toxicity, and hemolysis is a sensible consensus approach. The inclusion of membrane-binding prediction and helical wheel analysis adds a structural dimension that is often missing in similar studies. The manuscript is well organized and the figures are generally clear.
- **Major Concerns** The concerns below identify issues that, in aggregate, prevent the manuscript from establishing its central claims.
- **Minor Comments** The minor comments below address clarity, reporting, and presentation issues that should be corrected.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria**  
  **Originality** Low to moderate. In silico AMP discovery pipelines are well represented in the literature. The specific focus on DnaA of *K. pneumoniae* is somewhat distinctive, but the approach itself does not introduce a new method or conceptual advance.  
  **Scientific importance** Moderate. Antimicrobial resistance is a critical global health issue, and new therapeutic leads are needed. However, the study provides only computational predictions with no experimental validation, so the immediate importance is limited.  
  **Interdisciplinary readership** Limited. The work is primarily of interest to computational biologists and peptide researchers. It does not offer insights that would attract a broad readership across disciplines.  
  **Technical soundness** The individual computational steps are mostly standard and appropriately used, but the lack of validation, the absence of key controls, and the overinterpretation of docking results undermine the technical robustness of the conclusions.  
  **Readability for nonspecialists** The manuscript is generally readable, with clear explanations of the pipeline steps. However, some sections, particularly the docking and NMA descriptions, assume familiarity with structural biology terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a reasonable computational workflow, but the central claims of promising therapeutic candidates and DnaA inhibition are not supported by the evidence presented. Major revisions and experimental validation, or a substantial reframing of the claims, would be required before the work could be considered for publication.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract and conclusion state that the four identified peptides are "promising antimicrobial peptide candidates" and that Peptide 3 "exhibited the strongest predicted interaction" with DnaA, implying therapeutic potential.
- **Evidence pointer** Results sections 3.6.2 and 3.7; Table 2; Figures 11–14
- **Concern** The central claim of promising candidates is based entirely on docking scores and NMA, with no experimental validation of antimicrobial activity, target binding, or cytotoxicity. Docking scores are not reliable predictors of binding affinity or biological activity, and the manuscript itself acknowledges this limitation in the Discussion. Without any in vitro or in vivo data, the claim that these peptides are "promising" is overstated and not supported by the evidence.
- **Why it matters** The stated purpose of the pipeline is to prioritize candidates for experimental testing, but the manuscript goes beyond prioritization to imply therapeutic potential. This overinterpretation could mislead readers and is not consistent with the evidence level.
- **Resolution test** The authors must either provide experimental validation (e.g., MIC assays, binding assays, cytotoxicity tests) or substantially reframe the conclusions to state that these are computational predictions requiring validation, without using language that implies established efficacy.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The methods state that a three-tool consensus strategy was used for activity, toxicity, and hemolysis prediction, and that only peptides passing all three tools were retained.
- **Evidence pointer** Methods sections 2.3.1–2.3.3; Results sections 3.2 and 3.3
- **Concern** The manuscript does not report the specific prediction scores or thresholds used for each of the nine tools (three each for activity, toxicity, hemolysis). It is therefore impossible to assess how stringent or lenient the filtering was, or whether the consensus approach meaningfully reduced false positives. Additionally, the criteria for "low aggregation" and "favorable amphipathic properties" are not quantitatively defined, making the final selection of four peptides from 156 non-toxic candidates difficult to reproduce or evaluate.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without reporting the exact thresholds, scores, and tool versions, other researchers cannot replicate the pipeline or assess the robustness of the filtering.
- **Resolution test** Provide a supplementary table listing all 156 non-toxic peptides with their scores from each tool, the thresholds applied, and the specific values for aggregation, hydrophobicity, and hydrophobic moment that led to the final four selections.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural validation
- **Claim pointer** The DnaA protein structure was predicted using AlphaFold and used for docking without experimental validation.
- **Evidence pointer** Methods section 2.6; Results section 3.5; Figure 8
- **Concern** The manuscript reports quality metrics for the AlphaFold model (z-score, Errat, Ramachandran), but these are internal consistency checks, not validation against an experimentally determined structure. The authors acknowledge this limitation in the Discussion, but the docking results are still interpreted as meaningful. For a study that claims to identify inhibitors of DnaA, the use of an unvalidated predicted structure is a significant weakness, as docking against an inaccurate model can produce misleading results.
- **Why it matters** The reliability of all downstream docking and NMA results depends on the accuracy of the DnaA model. Without experimental validation or at least a comparison to a homologous experimentally determined structure, the docking results cannot be considered robust.
- **Resolution test** Compare the AlphaFold model to a known experimental structure of a homologous DnaA protein (e.g., from *E. coli*) and report RMSD values. Alternatively, use an experimentally determined structure if one becomes available, or clearly state that the docking results are contingent on the predicted model and should be interpreted with caution.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript states that "protein–peptide docking demonstrated that all four peptides interact within this region" (the DNA-binding domain) and that this "suggests the potential to interfere with bacterial DNA replication."
- **Evidence pointer** Results section 3.6.2; Table 2; Figures 11–14
- **Concern** The docking analysis shows that the peptides bind within the DNA-binding pocket, but no competitive docking or displacement assay was performed to demonstrate that the peptides can actually compete with DNA for binding. The claim of "potential to interfere" is speculative. Furthermore, the binding energies reported in Table 2 are docking scores, not free energies of binding, and the manuscript does not report any error estimates or statistical significance for these values.
- **Why it matters** The proposed mechanism of action is competitive inhibition of DnaA-DNA binding. Without evidence that the peptides can displace or prevent DNA binding, the mechanistic claim is unsupported.
- **Resolution test** Perform competitive docking experiments (e.g., docking DNA in the presence of each peptide) or molecular dynamics simulations to assess whether peptide binding is thermodynamically favorable and whether it would sterically hinder DNA binding. At minimum, the authors should clearly state that the mechanism is hypothetical and not demonstrated.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The NMA results are used to conclude that "the overall eigenvalue profiles suggest comparable dynamic stability across the systems" and that the complexes are "stable."
- **Evidence pointer** Results section 3.7; Figures 15 and 16
- **Concern** NMA provides information about intrinsic flexibility, not thermodynamic stability. The eigenvalues and variance distributions shown are typical for any folded protein complex and do not demonstrate that the peptide-protein complexes are stable in a biological sense. The interpretation of NMA results as evidence of "stability" is an overreach. Additionally, the manuscript does not report any error analysis or comparison to a control (e.g., the apo protein or a known non-binding peptide).
- **Why it matters** The conclusion that the complexes are stable is used to support the claim that the peptides are viable candidates. This conclusion is not supported by the NMA data, which only shows that the complexes have normal flexibility profiles.
- **Resolution test** Reframe the NMA results as descriptive of flexibility, not stability. If stability is to be claimed, perform molecular dynamics simulations with explicit solvent and report RMSD, RMSF, and binding free energy over time.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section 2.2
- **Evidence pointer** "Net charge was selected more than 3 to ensure sufficient positive charge to expect interaction with membrane of Gram-negative bacterial."
- **Issue** The sentence is grammatically awkward and the justification for the charge cutoff is vague. The authors cite literature but do not specify which literature or how the cutoff was derived.
- **Required correction** Rewrite for clarity and provide a specific citation or rationale for the charge threshold.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Results section 3.1
- **Evidence pointer** "To avoid repetition, the duplicate entries were removed from the combined dataset."
- **Issue** The number of duplicates removed is not reported. The reader cannot assess the degree of redundancy across the three databases.
- **Required correction** Report the number of unique sequences after duplicate removal and the number of duplicates removed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1–3
- **Evidence pointer** Figures 1, 2, and 3
- **Issue** The bar charts show counts of peptides classified as AMP/non-AMP, toxic/non-toxic, and hemolytic/non-hemolytic, but the y-axis labels are not visible in the provided text and the figure legends are minimal. It is unclear whether the bars represent counts or percentages.
- **Required correction** Ensure all axes are labeled with units and provide more detailed legends explaining what each bar represents.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section 3.6.2
- **Evidence pointer** "Peptide 3 showed the most potential binding with the protein among all the four candidates."
- **Issue** "Most potential binding" is imprecise. The authors likely mean the most favorable or strongest predicted binding.
- **Required correction** Use precise terminology, such as "the most favorable docking score" or "the strongest predicted interaction."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** "The datasets generated and/or analyzed during the current study are available from the corresponding author upon reasonable request."
- **Issue** For a computational study, it is standard practice to deposit code, scripts, and prediction outputs in a public repository. The current statement is vague and does not specify what data or code will be shared.
- **Required correction** Specify exactly what will be shared (e.g., peptide sequences, prediction scores, scripts) and consider depositing these in a public repository such as Zenodo or GitHub.

## Risk / unsupported claims
- The claim that the four peptides are "promising antimicrobial peptide candidates" is unsupported without experimental validation of antimicrobial activity.
- The claim that peptide binding to the DnaA DNA-binding domain "suggests the potential to interfere with bacterial DNA replication" is speculative and not demonstrated by the docking data.
- The interpretation of NMA results as evidence of "stability" is unsupported; NMA describes flexibility, not thermodynamic stability.
- The statement that the DnaA protein structure is reliable for docking is not fully supported, as the AlphaFold model is not validated against an experimental structure.
- The claim that the pipeline is "comprehensive" is overstated, as key steps such as MD simulation and experimental validation are absent.