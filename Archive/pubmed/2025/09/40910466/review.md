## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose that KISS1, a metastasis suppressor, interacts with and modulates the activity of six transcription factors (SP1, CDX2, FLI1, GATA2, NMYC, HDAC2) through structural and regulatory mechanisms, and that this modulation supports anti-metastatic signaling in triple-negative breast cancer (TNBC), based on molecular docking, molecular dynamics simulations, and gene expression analysis in MDA-MB-231 cells.
- **Visible evidence base** Abstract text only; includes docking scores, simulation metrics (RMSD, Rg, hydrogen bonds), and gene expression outcomes (upregulation/downregulation) from cell treatment experiments
- **Missing materials affecting confidence** Full manuscript, methods details, docking and simulation parameters, statistical analyses, experimental replicates, control conditions, figure data, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting hypothesis linking KISS1 to transcription factor modulation in TNBC, but the evidence as summarized is insufficient to establish the mechanistic claims. The computational and experimental results are reported without statistical context, and the logical connection between docking scores, simulation stability, and gene expression changes is not clearly articulated. The claim that KISS1 "selectively modulates transcriptional activity toward anti-metastatic signaling" is not supported by the data presented, as the abstract does not demonstrate a functional link between the observed binding and the transcriptional outcomes.
- **Who would be interested in the results, and why** Researchers in cancer biology, particularly those studying metastasis suppression, TNBC therapeutics, and transcription factor networks. Computational biologists interested in protein-DNA docking and molecular dynamics approaches may also find the methodological application relevant, though the novelty of the approach is not established from the abstract.
- **Major strengths** The study combines computational and experimental approaches, which is a commendable strategy for investigating protein-DNA interactions. The use of multiple transcription factors and a clinically relevant cell line (MDA-MB-231) adds potential translational relevance. The inclusion of a dose-response metric (IC50) for Kisspeptin-10 treatment provides a quantitative anchor for the experimental component.
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
- **Technical failings that need to be addressed before the case is established** The abstract lacks statistical reporting for all quantitative claims, the docking and simulation results are not linked to functional outcomes, the gene expression data are presented without validation or context, and the mechanistic interpretation overreaches the evidence provided.
- **Assessment against Nature-style criteria** 
  - Originality: The combination of KISS1 with six specific transcription factors is somewhat novel, but the approach (docking, MD, qPCR-style expression analysis) is standard and does not demonstrate conceptual innovation from the abstract alone.
  - Scientific importance: The topic is relevant to TNBC and metastasis, but the abstract does not establish a clear advance over existing knowledge about KISS1 or these transcription factors.
  - Interdisciplinary readership: The work bridges structural biology and cancer biology, which could appeal to a broad audience, but the abstract is too specialized and lacks context for nonspecialists.
  - Technical soundness: The reported metrics (HADDOCK scores, RMSD, Rg) are plausible, but without methodological detail or error bars, technical rigor cannot be assessed.
  - Readability for nonspecialists: The abstract is dense with jargon and lacks a clear narrative that would make the findings accessible to a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents preliminary findings that could be developed into a stronger case with additional data, but as written, the claims are not supported by the visible evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The abstract reports specific numerical values for docking scores, RMSD, Rg, hydrogen bonds, and IC50 without any indication of variability, replicates, or statistical significance.
- **Evidence pointer** Abstract text, location not provided
- **Concern** All quantitative results are presented as single-point values. For example, "CDX2 showed the strongest binding (HADDOCK score: -144.2; buried surface area: 2526.5 A(2))" and "low RMSD (2.1-2.7 A)" are given without standard deviations, confidence intervals, or statistical tests. Similarly, the gene expression changes (upregulation/downregulation) are stated without fold-change values, p-values, or error bars.
- **Why it matters** Without statistical context, the reader cannot determine whether the differences between transcription factors are meaningful or within noise. The ranking of binding strengths and the stability classifications are central to the conclusions, and their reliability is unverifiable.
- **Resolution test** Provide mean and standard deviation (or equivalent) for at least three independent replicates for each docking and simulation metric, and report p-values or effect sizes for gene expression comparisons between treated and untreated cells.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic link
- **Claim pointer** The abstract states that "KISS1 selectively modulates transcriptional activity toward anti-metastatic signaling" based on the observed binding and expression changes.
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract does not establish a causal or even correlative link between the docking/simulation results and the gene expression outcomes. The docking identifies potential binding partners, and the simulations assess stability, but there is no evidence that these interactions drive the observed transcriptional changes. The expression data could be explained by indirect effects of Kisspeptin-10 treatment unrelated to direct KISS1-TF binding.
- **Why it matters** The central claim of the paper is that KISS1 acts as a transcriptional regulator through these specific TFs. Without a demonstrated mechanism (e.g., knockdown or overexpression of KISS1, chromatin immunoprecipitation, or reporter assays), the conclusion is speculative.
- **Resolution test** Include functional experiments that directly test the role of KISS1-TF interactions, such as KISS1 knockdown or overexpression followed by TF activity assays, or chromatin immunoprecipitation to show KISS1 occupancy at TF binding sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The abstract reports gene expression changes in MDA-MB-231 cells treated with Kisspeptin-10, including upregulation of SP1, NMYC, CDX2, and GATA2, and downregulation of FLI1 and HDAC2.
- **Evidence pointer** Abstract text, location not provided
- **Concern** The expression analysis is described in a single sentence with no methodological detail. It is unclear whether this was done by qPCR, RNA-seq, or another method, how many biological replicates were used, what the reference genes were, and whether the changes were statistically significant. Additionally, the choice of Kisspeptin-10 (a peptide fragment) rather than full-length KISS1 is not justified, and the relevance of this treatment to the docking studies (which used KISS1) is unclear.
- **Why it matters** The experimental component is the only direct evidence of biological relevance, and its validity is essential. If the expression changes are not robust or are artifacts of the treatment conditions, the entire translational claim collapses.
- **Resolution test** Provide full experimental details, including assay type, replicate numbers, statistical analysis, and a justification for using Kisspeptin-10. Show that the expression changes are dose-dependent and specific to KISS1 pathway activation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model relevance
- **Claim pointer** The abstract implies that the computational models of KISS1-DNA interactions with TFs are representative of the in vivo situation in TNBC.
- **Evidence pointer** Abstract text, location not provided
- **Concern** The docking was performed between KISS1-DNA and TFs, but the abstract does not clarify whether the DNA sequence used is a known KISS1 promoter region or a generic sequence. The relevance of the chosen DNA to TNBC biology is not stated. Furthermore, the TFs were "modelled using SWISS-MODEL," which suggests homology models, and the quality of these models is not discussed.
- **Why it matters** If the DNA sequence or the TF models are not biologically relevant, the docking results may be artifacts. The conclusions depend on the assumption that the modeled interactions reflect real molecular events in TNBC cells.
- **Resolution test** Specify the DNA sequence used and its source, validate the TF models (e.g., with Ramachandran plots or QMEAN scores), and discuss how the chosen sequences relate to known KISS1 regulatory regions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title and abstract framing
- **Evidence pointer** Abstract text, location not provided
- **Issue** The title and abstract imply a comprehensive study of "protein-DNA interactions," but the abstract focuses on TF binding to KISS1-DNA, which is a narrow subset. The scope is not clearly defined.
- **Required correction** Clarify in the title or abstract that the study focuses on KISS1 promoter DNA interactions with specific TFs, not general protein-DNA interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "KISS1" vs "Kisspeptin-10"
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract uses "KISS1" for the docking studies and "Kisspeptin-10" for the cell treatment, but does not explain the relationship between these two entities. Kisspeptin-10 is a 10-amino acid fragment of the KISS1 protein, and its use may not be equivalent to full-length KISS1.
- **Required correction** Define the relationship between KISS1 and Kisspeptin-10 and justify why the fragment was used for the experimental validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Simulation duration
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract states that molecular dynamics simulations were run for 150 ns, but does not provide convergence criteria or justification for this timescale. For protein-DNA complexes, longer simulations may be needed to observe stable interactions.
- **Required correction** Add a brief justification for the simulation length and include convergence metrics (e.g., RMSD plateau, energy stabilization) in the full text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** "Anti-metastatic signaling" claim
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract concludes that the observed changes suggest "anti-metastatic signaling," but the direction of regulation (e.g., upregulation of SP1, which can be oncogenic in some contexts) is not discussed. The interpretation is oversimplified.
- **Required correction** Provide a more nuanced discussion of how each TF's regulation contributes to anti-metastatic outcomes, with reference to known functions in TNBC.

## Risk / unsupported claims
- The claim that KISS1 "selectively modulates transcriptional activity toward anti-metastatic signaling" is unsupported because no functional link between binding and expression is demonstrated.
- The ranking of TF binding strengths (CDX2 strongest, FLI1 weakest) is unsupported without statistical comparison.
- The classification of complexes as "stable" or "unstable" is unsupported without quantitative thresholds or replicate simulations.
- The gene expression changes are reported without statistical validation, making their reliability unassessable.
- The relevance of Kisspeptin-10 treatment to KISS1 function is not established, and the abstract does not clarify whether the observed effects are specific to KISS1 signaling.
- The biological significance of the docking scores and simulation metrics for TNBC metastasis is not contextualized, and the abstract does not explain how these computational findings translate to in vivo mechanisms.