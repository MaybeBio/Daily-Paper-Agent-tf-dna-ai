## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) with figure legends referenced but not provided in full
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors report single-molecule observations of human DNA ligase 1 (LIG1) binding to nicked dsDNA using optical tweezers and confocal fluorescence microscopy. They claim that full-length LIG1 exhibits both specific and non-specific DNA binding, performs 1D diffusion along DNA to search for nicks, and forms stable complexes preferentially at nick sites. They further claim that the N-terminal non-catalytic region promotes nick-enriched binding and facilitates efficient nick search by enhancing 1D diffusion, based on comparisons with a C-terminal LIG1 construct lacking this region.
- **Visible evidence base** Methods section describing protein purification, fluorescent labeling, C-Trap instrumentation, and data analysis; Results section with qualitative descriptions of kymographs and quantitative binding lifetime and diffusion coefficient measurements; Figures 1-4 and Supplementary Figures 1-4 referenced but not fully visible
- **Missing materials affecting confidence** Full figure panels and raw data, exact fitting parameters and statistical details, sample sizes per condition, control experiments (e.g., no-protein or no-nick controls), validation of nick site positions, and details on protein labeling stoichiometry and activity

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in understanding how human LIG1 recognizes and binds to its nick DNA substrate. The use of single-molecule approaches is appropriate and timely. The observation that full-length LIG1 exhibits 1D diffusion and forms stable complexes at nick sites, while the C-terminal construct does not, is potentially interesting. However, the evidence as presented is incomplete in several critical respects. The quantitative analysis appears underpowered and lacks sufficient statistical detail. The claim that the N-terminal region promotes 1D diffusion is based on a comparison between constructs that differ not only in the N-terminal region but also potentially in labeling stoichiometry and DNA binding affinity. The manuscript would benefit from additional controls and a more rigorous quantitative framework before the conclusions can be fully supported.
- **Who would be interested in the results, and why** Researchers studying DNA repair mechanisms, particularly DNA ligation and strand break recognition; single-molecule biophysicists interested in protein-DNA interactions; and those working on Okazaki fragment maturation and genome stability. The findings could also be relevant to those developing LIG1 inhibitors for therapeutic purposes.
- **Major strengths** The study addresses a previously unexplored question using state-of-the-art single-molecule instrumentation. The combination of optical tweezers with confocal fluorescence microscopy is well suited to the question. The comparison between full-length and C-terminal LIG1 constructs is a reasonable approach to dissect the role of the N-terminal region. The observation of multiple binding modes and interconversion between them is a valuable contribution.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor), R1-M2 (construct comparison validity), R1-M3 (quantitative diffusion analysis), R1-M4 (binding specificity evidence)
- **Assessment against Nature-style criteria** Originality is moderate to high; the single-molecule approach to LIG1 nick binding is novel. Scientific importance is high given the fundamental role of LIG1 in DNA replication and repair. Interdisciplinary readership is plausible, spanning biophysics, DNA repair, and enzymology. Technical soundness is currently insufficient due to incomplete statistical reporting and potential confounds in the construct comparison. Readability for nonspecialists is adequate but could be improved with clearer explanations of single-molecule concepts and the significance of the findings.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible and interesting, but the quantitative support is incomplete and the key comparison between full-length and C-terminal LIG1 requires additional controls and analysis. Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reporting
- **Claim pointer** The manuscript reports binding lifetimes and diffusion coefficients for full-length and C-terminal LIG1, including specific values such as 0.08 sec (58%), 0.74 sec (27%), 11 sec (15%) for full-length and 0.25 sec (78%) and 2 sec (22%) for C-terminal, and diffusion coefficients of 3.8 ± 0.4 kbp²/s versus 0.34 ± 0.02 kbp²/s.
- **Evidence pointer** Results section, Figure 3, Supplementary Figures 3-4
- **Concern** The statistical framework for the quantitative claims is not adequately described. The number of molecules or events contributing to each distribution is not stated. The uncertainty on the fitted lifetimes and their fractions is not reported. The diffusion coefficient comparison lacks a formal statistical test. The choice of model selection via BIC is described but the actual BIC values and the criteria for unimodality are not provided. Without these details, the robustness of the quantitative conclusions cannot be assessed.
- **Why it matters** The central claims of the paper rest on quantitative differences between full-length and C-terminal LIG1. If the statistical basis is weak or the sample sizes are small, the conclusions may not be reliable.
- **Resolution test** Provide the number of events and molecules analyzed, confidence intervals for all fitted parameters, and a formal statistical comparison (e.g., permutation test or bootstrap-based test) for the diffusion coefficient difference. Report BIC values and the model selection procedure in full.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Construct comparison validity
- **Claim pointer** The manuscript claims that the N-terminal non-catalytic region promotes binding enriched at nick sites and facilitates an efficient nick search process by promoting 1D diffusion, based on comparison between full-length LIG1 and a C-terminal construct (261-919 amino acids).
- **Evidence pointer** Methods, Results sections, Figures 1-2
- **Concern** The C-terminal construct lacks the N-terminal region but also may differ in oligomeric state, post-translational modifications, and labeling efficiency. The manuscript does not report the labeling stoichiometry for each construct, nor whether the C-terminal construct retains catalytic activity or proper folding. If the C-terminal construct is labeled differently or is partially aggregated, the observed differences in diffusion and binding could be artifacts. Additionally, the C-terminal construct may have different intrinsic DNA binding affinity independent of the N-terminal region, which would confound the interpretation.
- **Why it matters** The conclusion that the N-terminal region specifically promotes 1D diffusion and nick targeting depends on the assumption that the only relevant difference between the two constructs is the presence of the N-terminal region. If other differences exist, the conclusion is not supported.
- **Resolution test** Report labeling stoichiometry for both constructs, verify that the C-terminal construct is monomeric and properly folded (e.g., by size exclusion chromatography or activity assay), and measure DNA binding affinity under equilibrium conditions to rule out intrinsic affinity differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative diffusion analysis
- **Claim pointer** The manuscript reports a ~10-fold higher diffusion coefficient for full-length LIG1 (3.8 ± 0.4 kbp²/s) compared to C-terminal LIG1 (0.34 ± 0.02 kbp²/s) and interprets this as evidence that the N-terminal region promotes efficient 1D diffusion.
- **Evidence pointer** Results section, Figure 3D
- **Concern** The method for computing diffusion coefficients from tracked events is described as using a Covariance Based Estimator, but the details of how tracks are selected, how static segments are separated from diffusive segments, and how the diffusion coefficient is extracted from the covariance are not provided. The manuscript states that events diffusing into beads or hindered by other proteins were excluded, but the criteria for these exclusions are not defined. The number of tracks contributing to the diffusion coefficient estimate is not stated. Without a clear description of the analysis pipeline and the number of events, the reliability of the diffusion coefficient values is uncertain.
- **Why it matters** The claim that the N-terminal region promotes 1D diffusion is a key mechanistic finding. If the diffusion coefficient estimates are biased or based on too few events, the conclusion may be incorrect.
- **Resolution test** Provide a detailed description of the tracking and diffusion coefficient estimation procedure, including the number of tracks analyzed, the distribution of track lengths, and a validation of the estimator on simulated data. Report the diffusion coefficient for static versus diffusive segments separately.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Binding specificity evidence
- **Claim pointer** The manuscript claims that full-length LIG1 binding is enriched at nick sites, based on binding density profiles along the DNA.
- **Evidence pointer** Results section, Figure 1C, Supplementary Figure 2
- **Concern** The binding density profiles are described as showing enrichment at nick locations, but the statistical significance of this enrichment is not assessed. The manuscript mentions that some stable binding events occur at non-predicted locations, attributed to unpredicted nicks, but no evidence is provided to support this interpretation. The number of molecules and the total observation time contributing to the density profiles are not stated. A quantitative comparison of binding density at nick versus non-nick positions, with appropriate statistical testing, is needed.
- **Why it matters** The claim of specific nick binding is central to the paper. Without statistical support, the enrichment could be due to chance or to sequence-dependent binding unrelated to nicks.
- **Resolution test** Provide a statistical comparison of binding density at nick versus non-nick positions, including the number of events and the total observation time. If possible, perform a control experiment with DNA lacking nicks to demonstrate that enrichment is nick-specific.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section, C-Trap imaging
- **Evidence pointer** Methods section
- **Issue** The description of the microfluidic flow cell and the movement of traps between channels is brief and may be difficult for readers unfamiliar with the C-Trap system to follow.
- **Required correction** Expand the methods description to include a schematic or more detailed textual explanation of the flow cell layout and the experimental workflow.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Results section, Figure 3
- **Issue** The manuscript reports binding lifetime distributions fitted with multiple exponentials, but the individual exponential components are not clearly labeled or described in the text. The biological meaning of each component is not discussed.
- **Required correction** Clearly label the exponential components in the figure and provide a brief interpretation of what each component may represent (e.g., non-specific versus specific binding).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of single-molecule studies of DNA repair proteins is brief and does not fully contextualize the findings within the broader literature on DNA damage search mechanisms.
- **Required correction** Expand the discussion to include a more thorough comparison with previous single-molecule studies of DNA repair proteins, particularly those that have observed 1D diffusion and target site recognition.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The phrase "nick DNA binding" is used throughout, but the term "nick" is not defined until later in the Introduction. Some readers may be unfamiliar with the term.
- **Required correction** Define "nick" at first use in the Abstract or Introduction.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures 1-4
- **Evidence pointer** Results section
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to fully interpret the figures.
- **Required correction** Ensure that all figure legends are included and provide sufficient detail to understand the experimental setup and data presentation.

## Risk / unsupported claims
- The claim that the N-terminal non-catalytic region promotes 1D diffusion is not fully supported because the comparison between full-length and C-terminal LIG1 may be confounded by differences in labeling, folding, or intrinsic DNA binding affinity.
- The claim that LIG1 binding is enriched at nick sites lacks statistical support.
- The quantitative values for binding lifetimes and diffusion coefficients are reported without sufficient statistical detail to assess their reliability.
- The interpretation of stable binding at non-predicted locations as "unpredicted nicks" is speculative and not supported by direct evidence.
- The working model proposed in Figure 4 is plausible but is not directly tested by the experiments presented.