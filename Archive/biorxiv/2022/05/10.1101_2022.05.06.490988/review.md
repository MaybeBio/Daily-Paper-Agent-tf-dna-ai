## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary file references.
- **Assessment boundary** Scientific validity, methodological rigor, clarity of claims, and alignment of evidence with conclusions. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors identify a minimal eight-amino-acid motif (P1411–G1418) in NUP153 that mediates binding to the HIV-1 capsid, with six residues (P1411, V1414, F1415, T1416, F1417, G1418) confirmed as critical via computational predictions and experimental validation.
- **Visible evidence base** Molecular dynamics simulations, FoldX and PyRosetta predictions, in vitro co-sedimentation assays, cell-based TRIM-NUP153C restriction assays, and statistical correlations between predictions and empirical data.
- **Missing materials affecting confidence** Supplementary figures (Fig S1A), supplementary tables (Table S1, S2), and File S1 (all modeling data) were not provided. Raw numerical data for binding percentages and statistical analyses are not fully reported in the text.

## Reviewer
- **Overall assessment** The manuscript presents a well-structured, multidisciplinary study that combines computational and experimental approaches to map the HIV-1 capsid binding site on NUP153. The identification of a minimal motif and the validation of key residues are valuable contributions. However, several technical concerns, particularly regarding the interpretation of experimental data, the handling of discrepancies between modeling and empirical results, and the generalizability of the findings, need to be addressed before the conclusions are fully established.
- **Who would be interested in the results, and why** Researchers studying HIV-1 nuclear entry, host-pathogen interactions, nucleoporin biology, and antiviral drug development. The findings may also interest computational biologists working on protein-protein interaction prediction and validation.
- **Major strengths** 1) Integration of multiple computational tools (MD, FoldX, PyRosetta) with two independent experimental assays. 2) Clear identification of a minimal binding motif with potential implications for understanding capsid-host interactions. 3) The use of naturally occurring polymorphisms to explore evolutionary and protective aspects adds depth.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (experimental validation of T1416), R1-M2 (correlation strength and interpretation), R1-M3 (generalizability of the minimal motif).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The study refines prior knowledge of the NUP153-CA interaction but does not introduce a fundamentally new concept.  
  - **Scientific importance** High for the HIV-1 field, as it narrows down critical residues and may inform therapeutic strategies.  
  - **Interdisciplinary readership** Good, as it bridges computational biology, virology, and structural biology.  
  - **Technical soundness** Generally sound, but concerns about experimental validation and statistical interpretation need resolution.  
  - **Readability for nonspecialists** Acceptable, though some sections assume familiarity with molecular modeling terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the T1416 discrepancy and the strength of the correlation claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental validation  
- **Claim pointer** The authors claim that T1416 is a critical residue for CA interaction, but both modeling tools predicted small ΔΔG values for T1416 mutations, while experimental data showed disruption.  
- **Evidence pointer** Results section, Figure 2D, Discussion  
- **Concern** The manuscript acknowledges that both FoldX and PyRosetta failed to predict the disruptive effect of T1416 mutations, attributing this to water-mediated interactions. However, this discrepancy is not resolved experimentally. The claim that T1416 is critical relies on empirical data, but the modeling tools that are central to the study's approach cannot capture this. This undermines the predictive power of the computational framework and raises questions about the reliability of other predictions.  
- **Why it matters** If the computational methods cannot accurately predict the effect of mutations at a residue that is experimentally confirmed as critical, the utility of these methods for identifying other critical residues is questionable. This affects the overall validity of the study's approach.  
- **Resolution test** Provide additional experimental validation, such as alanine scanning or structural analysis, to confirm the role of T1416. Alternatively, refine the computational methods to account for water-mediated interactions and demonstrate improved predictive accuracy.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical interpretation  
- **Claim pointer** The authors report significant correlations between modeling predictions and experimental data (Pearson's r = 0.88 for FoldX vs PyRosetta, and r = -0.54 and -0.39 for experimental correlations).  
- **Evidence pointer** Results section, Figures 1G, 2E, 3C  
- **Concern** The correlation coefficients are reported, but the manuscript does not provide confidence intervals or effect sizes. The negative correlations with experimental data are moderate, and the interpretation of "significant" is based on p-values alone. The manuscript does not discuss whether the magnitude of these correlations is biologically meaningful or sufficient to support the claim that modeling predictions are reliable.  
- **Why it matters** Overstating the strength of correlations could mislead readers about the predictive accuracy of the computational methods. A more nuanced statistical analysis would strengthen the conclusions.  
- **Resolution test** Provide confidence intervals for correlation coefficients, discuss the practical significance of the observed correlations, and consider alternative statistical approaches (e.g., Bland-Altman plots) to assess agreement.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The authors propose that the minimal motif PxxVFTFG is required for CA interaction and suggest that other FG-containing motifs could also bind the capsid.  
- **Evidence pointer** Discussion  
- **Concern** The study only tests mutations within the 1411–1418 region of NUP153. The claim that other FG motifs could interact with CA is speculative and not experimentally tested. Additionally, the study does not address whether the identified motif is sufficient for binding in isolation or whether flanking sequences are required.  
- **Why it matters** The broader implications of the study, such as the potential for other FG motifs to bind CA, are not supported by direct evidence. This limits the generalizability of the findings.  
- **Resolution test** Perform additional experiments to test whether other FG motifs in NUP153 or other nucleoporins can bind CA, and assess the sufficiency of the minimal motif in isolation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Figure 2D  
- **Evidence pointer** Results section, Figure 2D  
- **Issue** The binding percentages for wild-type and mutant NUP153C are not explicitly stated in the text, making it difficult to assess the magnitude of the effects.  
- **Required correction** Provide numerical values for binding percentages and standard deviations in the text or figure legend.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Materials and Methods, Molecular dynamics simulations  
- **Evidence pointer** Materials and Methods  
- **Issue** The manuscript states that the simulation was run for 100 ns, but it does not specify the number of replicates or the convergence criteria used.  
- **Required correction** Include details on the number of independent simulations and how convergence was assessed.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Supplementary materials  
- **Evidence pointer** Materials and Methods, File S1  
- **Issue** The manuscript references File S1 for all modeling data, but this file was not provided for review.  
- **Required correction** Ensure that all supplementary data files are made available to reviewers and readers.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Discussion, genetic variation  
- **Evidence pointer** Discussion  
- **Issue** The discussion of naturally occurring polymorphisms in gorilla and drill is interesting but speculative regarding their functional impact on HIV-1 infection.  
- **Required correction** Clarify that the functional consequences of these polymorphisms are inferred from modeling and not directly tested.

## Risk / unsupported claims
- The claim that other FG-containing motifs in NUP153 or other nucleoporins could bind CA is speculative and not experimentally supported.
- The prediction that naturally occurring polymorphisms in gorilla and drill would protect from HIV-1 infection is inferred from modeling and not validated experimentally.
- The statement that the minimal motif is "likely" eight amino acids is based on MD simulations, but the functional sufficiency of this motif in isolation is not tested.