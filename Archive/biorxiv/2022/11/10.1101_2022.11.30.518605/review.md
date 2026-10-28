## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, theoretical background, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and theoretical framework as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose that direct transfer of polynucleotides between nucleic acid-binding proteins is a general phenomenon, demonstrated through fluorescence polarization and single-molecule experiments on TREX1, hnRNP-U, FBF-2, and MS2-CP, with implications for target site search and in vivo complex lifetimes
- **Visible evidence base** Fluorescence polarization binding and competition assays, TIRF microscopy single-molecule experiments, kinetic modeling, and correlation analysis of rate constants
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; companion manuscript on PRC2 not available for verification; raw single-molecule data not directly inspectable

## Reviewer
- **Overall assessment** The manuscript presents a potentially significant finding that direct transfer of polynucleotides is a general property of nucleic acid-binding proteins, extending previous observations on PRC2. The experimental approach combining ensemble fluorescence polarization with single-molecule TIRF microscopy is appropriate and the data appear internally consistent. However, the breadth of the claim regarding generality is not fully supported by the limited number of proteins tested, and the mechanistic interpretation for TREX1 relies on a small number of direct transfer events. The theoretical framework is well developed but requires careful scrutiny regarding assumptions. The biological implications, while intriguing, are largely speculative and would benefit from more direct experimental support or clearer framing as hypotheses.
- **Who would be interested in the results, and why** Researchers studying nucleic acid-protein interactions, particularly those interested in target site search mechanisms, chromatin biology, RNA-mediated regulation, and the biophysics of protein-nucleic acid complexes. The findings may also be relevant to those studying facilitated dissociation and competition phenomena in gene regulation.
- **Major strengths** The study addresses an important and under-explored question about the generality of direct transfer. The combination of multiple biochemical techniques and the inclusion of diverse protein systems strengthens the conclusions. The theoretical framework provides a useful quantitative basis for interpreting competition kinetics. The correlation analysis across multiple studies is compelling and suggests a universal relationship between dissociation and transfer rates.
- **Major Concerns** The claim of generality is based on a small number of proteins, and the selection may not be representative of the broader class of nucleic acid-binding proteins. The single-molecule evidence for direct transfer in TREX1 is based on a limited number of events and requires more robust statistical support. The mechanistic model for how direct transfer occurs at the molecular level is not directly tested. The biological implications, while interesting, are largely speculative and not experimentally validated.
- **Minor Comments** Several methodological details require clarification, including the specific conditions for fluorescence polarization experiments and the criteria for event selection in single-molecule analyses. The presentation of the theoretical background is dense and could be streamlined for readability. The discussion of biological relevance would benefit from more concrete examples or testable predictions.
- **Technical failings that need to be addressed before the case is established** The statistical power of the single-molecule direct transfer event detection needs to be more rigorously demonstrated. The correlation analysis in Figure 5 includes data from different experimental systems and conditions, which may introduce confounding variables. The theoretical model assumes certain simplifications that may not hold for all protein-nucleic acid interactions.
- **Assessment against Nature-style criteria** Originality: The concept of direct transfer as a general property of nucleic acid-binding proteins is novel and extends previous work in a meaningful way. Scientific importance: The findings have broad implications for understanding how proteins search for and interact with their nucleic acid targets, which is fundamental to many biological processes. Interdisciplinary readership: The work bridges biophysics, biochemistry, and molecular biology, and should appeal to a wide audience. Technical soundness: The experimental approaches are generally well executed, but some concerns about statistical power and model assumptions need to be addressed. Readability for nonspecialists: The manuscript is clearly written, but the theoretical sections may be challenging for readers without a strong biophysics background.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the statistical robustness of single-molecule data and the generalizability of the findings.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim generality
- **Claim pointer** The authors claim that "direct transfer is a common phenomenon utilized by the majority of NBPs" based on testing four proteins.
- **Evidence pointer** Results section, Figure 1, Table 1
- **Concern** The claim of generality is based on a limited and potentially biased sample of proteins. The four proteins tested (TREX1, hnRNP-U, FBF-2, MS2-CP) represent a narrow range of nucleic acid-binding protein families, and all are relatively well-characterized with known binding properties. The selection does not include proteins with very high affinity binding, very large binding interfaces, or those that bind structured nucleic acids in fundamentally different ways. The authors acknowledge this limitation in the discussion but do not adequately address how the sample size affects the strength of the general claim.
- **Why it matters** The central thesis of the manuscript is that direct transfer is a general property of nucleic acid-binding proteins. If the claim is overstated, the significance of the work is substantially diminished. The authors need to either provide a more compelling argument for why these four proteins are representative, or temper the claim to reflect the limited sample size.
- **Resolution test** The authors should either test additional proteins with diverse binding properties, or revise the claim to state that direct transfer is observed in a range of nucleic acid-binding proteins and may be common, rather than asserting it is a general property.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness of single-molecule data
- **Claim pointer** The authors state that "multiple (n = 36; p < 0.01 by Monte-Carlo simulation) instances where the binding of one ssDNA coincided with the release of a differentially labeled ssDNA" were identified.
- **Evidence pointer** Results section, Figure 2, Methods section on single-molecule experiments
- **Concern** The detection of direct transfer events in single-molecule experiments relies on identifying coincident binding and release events. The statistical analysis uses Monte-Carlo simulations, but the details of how the simulations were parameterized and how the threshold for event detection was set are not fully described. The number of events (n = 36) is relatively small, and the analysis appears to be from a single experiment. The authors note that they likely classified events within two exposure frames, which introduces uncertainty in the timing of events.
- **Why it matters** The single-molecule data provide the most direct evidence for the direct transfer mechanism. If the event detection is not robust, the mechanistic interpretation is weakened. The authors need to demonstrate that their event detection criteria are reliable and that the observed events are not due to artifacts such as photobleaching or transient dissociation.
- **Resolution test** The authors should provide more detailed information on the Monte-Carlo simulation parameters, conduct additional replicate experiments, and perform control experiments to rule out artifacts. They should also provide a more rigorous statistical analysis of the event detection threshold.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Correlation analysis interpretation
- **Claim pointer** The authors present a correlation between kθD and k-1P across multiple studies (R² = 0.91) and interpret this as support for their mechanistic model.
- **Evidence pointer** Results section, Figure 5, Methods section on rate constant correlation analysis
- **Concern** The correlation analysis combines data from different experimental systems, including different proteins, different nucleic acid substrates, and potentially different buffer conditions. The authors do not account for potential confounding variables such as temperature, ionic strength, or protein concentration. The correlation is driven by a small number of data points, and the inclusion of data from the companion manuscript (not available for review) makes it difficult to assess the robustness of the analysis.
- **Why it matters** The correlation is presented as strong evidence for the universality of the relationship between dissociation and transfer rates. If the correlation is not robust, the mechanistic implications are weakened. The authors need to demonstrate that the correlation holds across a wider range of conditions and is not an artifact of the specific data included.
- **Resolution test** The authors should provide a more detailed description of the data included in the correlation, perform sensitivity analyses excluding individual data points, and ideally include additional data from independent studies to strengthen the correlation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The authors speculate that direct transfer could allow proteins to conduct one-dimensional searches for target sites and that complex lifetimes in vivo can be regulated by free ligand concentrations.
- **Evidence pointer** Discussion section
- **Concern** The biological implications are presented as logical consequences of the in vitro findings, but no direct experimental evidence is provided to support these claims. The authors do not discuss potential alternative explanations for their observations or consider how cellular factors such as molecular crowding, post-translational modifications, or the presence of competing binding partners might affect direct transfer in vivo.
- **Why it matters** The significance of the work depends on the biological relevance of direct transfer. If the in vivo implications are overstated, the impact of the study is reduced. The authors should either provide experimental evidence supporting the biological relevance or clearly frame these implications as hypotheses that require further testing.
- **Resolution test** The authors should either conduct experiments to test the biological relevance of direct transfer (e.g., in cell-based assays) or revise the discussion to clearly distinguish between established findings and speculative implications.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Fluorescence polarization competition experiments
- **Evidence pointer** Methods section, Supplementary Figure 1
- **Issue** The description of the FP-based competition experiments lacks sufficient detail on how the concentration of the decoy ligand was varied and how the data were fit to distinguish between one- and two-rate-constant models. The criteria for model selection using the Bayesian Information Criterion are mentioned but not fully explained.
- **Required correction** Provide a more detailed description of the experimental design, including the range of decoy concentrations used, the number of replicates, and the specific criteria for model selection. Consider including representative raw data and fits.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Results section, Figure 2
- **Issue** The single-molecule data in Figure 2 are presented as representative traces, but the full distribution of residence times and the criteria for event selection are not shown. The authors state that "distributions of residence times across all individual binding events" were used, but the figure does not display these distributions.
- **Required correction** Include histograms or cumulative distributions of residence times for each condition, and clearly indicate how direct transfer events were identified in the traces.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Theoretical model validation
- **Affected element** Theoretical background section
- **Evidence pointer** Theoretical background, Equations 1-6
- **Issue** The theoretical model is presented in a highly condensed form, and the assumptions underlying the simplifications are not fully justified. The relationship between the model parameters and the experimentally measured quantities could be clarified.
- **Required correction** Expand the theoretical background to provide a more accessible derivation of the key equations and clearly state the assumptions and their validity for the systems studied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The authors cite previous work on direct transfer and facilitated dissociation but do not provide a comprehensive comparison of their findings with those in the literature. The relationship between direct transfer and facilitated dissociation is mentioned but not explored in depth.
- **Required correction** Add a more thorough discussion of how the present findings relate to and extend previous studies on direct transfer and facilitated dissociation, including any discrepancies or unresolved questions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table reports Kd and rate constants but does not include confidence intervals or measures of variability for the reported values. The number of independent experiments for each measurement is not stated.
- **Required correction** Include confidence intervals or standard errors for all reported values, and specify the number of independent experiments performed.

## Risk / unsupported claims
- The claim that direct transfer is a "general property" of nucleic acid-binding proteins is not fully supported by the limited number of proteins tested.
- The biological implications regarding one-dimensional search and in vivo regulation of complex lifetimes are speculative and not directly tested.
- The correlation between kθD and k-1P across studies may be influenced by confounding variables that are not fully accounted for.
- The single-molecule evidence for direct transfer in TREX1 is based on a small number of events and requires more robust statistical support.
- The theoretical model relies on assumptions that are not fully validated experimentally.