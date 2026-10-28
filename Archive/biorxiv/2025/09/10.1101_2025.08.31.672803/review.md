## Review setup

- **Input scope** Full manuscript text, abstract, and methods sections as provided. Figures, figure legends, and supplementary materials were not provided.
- **Assessment boundary** Assessment is limited to the claims and evidence described in the text. Experimental results are referenced to figures that were not available for direct inspection.
- **Shared manuscript claim summary** The authors report the development of TEAi, a 64-amino acid peptide derived from Drosophila Nerfin-1, which binds the TEA DNA-binding domain of TEAD. They claim that TEAi suppresses TEAD-YAP transcriptional activity, inhibits TEAD DNA binding without direct DNA interaction, induces nuclear export of TEAD2, and suppresses cancer cell proliferation in vitro and tumor growth in vivo.
- **Visible evidence base** Text descriptions of luciferase reporter assays, qPCR, co-immunoprecipitation, immunofluorescence, DNA pulldown, colony formation, and subcutaneous xenograft experiments. No actual data panels, numerical values, or statistical outputs were visible.
- **Missing materials affecting confidence** All figures and supplementary figures, including Figure 1A-H and Figure S1A-C. Detailed experimental protocols for the xenograft model, colony formation assay, and peptide delivery method. Information on peptide stability, dosage, and administration route. Statistical details beyond p-value thresholds.

## Reviewer

- **Overall assessment** The manuscript presents a potentially interesting approach to inhibiting TEAD function by targeting its DNA-binding domain rather than the YAP-binding interface. The concept is scientifically sound and the preliminary data described are consistent with the stated conclusions. However, the absence of all primary data figures makes it impossible to evaluate the quality, rigor, and statistical validity of the experimental results. The claim of a non-canonical mechanism involving nuclear export of TEAD2 is intriguing but requires substantially more mechanistic depth. The in vivo data are described only in a single sentence, which is insufficient to assess therapeutic potential. The manuscript is at an early stage and would benefit from additional mechanistic and functional validation before it could be considered for a high-impact venue.
- **Who would be interested in the results, and why** Researchers in the Hippo signaling field, cancer biologists studying TEAD-YAP/TAZ transcriptional programs, and drug discovery groups focused on transcription factor targeting. The potential advantage of blocking all TEAD-dependent transcription rather than only YAP/TAZ interaction would be of interest to those developing next-generation cancer therapeutics.
- **Major strengths** The conceptual advance of targeting the TEA DNA-binding domain is a distinct and potentially valuable approach. The use of a natural peptide scaffold from Drosophila Nerfin-1 provides a biologically informed starting point. The observation that TEAi induces nuclear export of TEAD2 suggests a mechanism beyond simple competitive DNA binding blockade, which could open new avenues for therapeutic intervention.
- **Major Concerns** The concerns below are listed in order of priority.
- **Minor Comments** The minor comments below are listed in order of priority.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality is moderate to high, as the concept of targeting the TEA DNA-binding domain with a peptide is not widely explored. Scientific importance is potentially high given the central role of TEAD in cancer, but the current evidence is preliminary. Interdisciplinary readership is limited at this stage, as the work is primarily of interest to Hippo signaling and cancer biology specialists. Technical soundness cannot be fully assessed without the primary data figures. Readability for nonspecialists is acceptable, though the mechanistic sections assume familiarity with the Hippo pathway.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising, but the absence of primary data and the limited mechanistic and in vivo depth prevent a supportive recommendation at this stage.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity
- **Claim pointer** TEAi potently suppressed TEAD-YAP-driven transcriptional activity, as evidenced by luciferase reporter and qPCR assays.
- **Evidence pointer** Figure 1A, Figure 1B, Figure S1B. Location not provided.
- **Concern** The manuscript states that TEAi completely abolished TEAD-YAP activation of the CTAD-luc reporter and significantly suppressed CTGF and CYR61 expression, but no actual data panels, numerical values, or statistical outputs are visible. The magnitude of suppression, the number of replicates, and the variability are not reported.
- **Why it matters** The central claim of transcriptional inhibition rests entirely on these assays. Without visible data, the reader cannot assess whether the effect is robust, dose-dependent, or specific to TEAD-YAP-driven transcription.
- **Resolution test** Provide the full figure panels with error bars, individual data points, replicate numbers, and statistical test results. Include a dose-response experiment if available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support
- **Claim pointer** TEAi inhibited the DNA-binding capacity of TEAD2 without direct DNA interaction, thereby abolishing promoter recruitment of the TEAD-YAP complex.
- **Evidence pointer** Figure 1D, Figure 1E, Figure S1C. Location not provided.
- **Concern** The DNA pulldown assay is described as showing that TEAi abolished TEAD/YAP recruitment to the CTGF promoter, but the data are not shown. The claim that TEAi does not bind DNA is based on an unspecified assay. The co-immunoprecipitation data with TEA domain mutants are described but not displayed.
- **Why it matters** The mechanistic model depends on demonstrating both that TEAi binds the TEA domain and that this binding prevents DNA interaction. Without visible pulldown and binding data, the mechanism remains unverified.
- **Resolution test** Show the DNA pulldown gels, the TEA domain mutant co-immunoprecipitation results, and a direct binding assay such as electrophoretic mobility shift assay or surface plasmon resonance to confirm TEAi-TEAD interaction and lack of TEAi-DNA interaction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support
- **Claim pointer** TEAi induced nuclear export and cytoplasmic accumulation of TEAD2, suggesting a non-canonical mechanism distinct from native Nerfin-1 function.
- **Evidence pointer** Figure 1C. Location not provided.
- **Concern** The immunofluorescence data are described in a single sentence. No quantification of nuclear versus cytoplasmic fluorescence is provided, and the specificity of the effect to TEAD2 versus other TEAD family members is not addressed. The connection between nuclear export and transcriptional inhibition is not mechanistically explored.
- **Why it matters** This is presented as a surprising and novel finding, but the evidence is thin. If TEAi merely displaces TEAD from chromatin, nuclear export would be an expected consequence rather than a distinct mechanism. The claim of non-canonical action requires direct evidence.
- **Resolution test** Provide quantified immunofluorescence images with statistical analysis, time-course experiments, and experiments testing whether nuclear export is required for transcriptional inhibition, for example using leptomycin B or nuclear export signal mutants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo evidence
- **Claim pointer** TEAi significantly suppressed cancer cell proliferation in vitro and tumor growth in vivo.
- **Evidence pointer** Figure 1F-1H. Location not provided.
- **Concern** The colony formation and xenograft data are described in two sentences. No tumor growth curves, tumor weights, animal numbers, or statistical analyses are provided. The cancer cell lines used for the in vivo study are not specified.
- **Why it matters** The therapeutic potential of TEAi is a key selling point of the manuscript. Without visible in vivo data, the claim of tumor suppression is unsubstantiated.
- **Resolution test** Provide the full xenograft dataset including tumor growth curves, endpoint tumor weights, animal numbers per group, and statistical analysis. Specify the cell lines and the route of TEAi administration.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity
- **Claim pointer** TEAi directly binds the TEA DNA-binding domain of TEAD and blocks all TEAD-dependent transcriptional programs.
- **Evidence pointer** Figure 1D, Figure S1A. Location not provided.
- **Concern** The manuscript does not demonstrate selectivity of TEAi for TEAD family members over other TEA domain-containing proteins or unrelated transcription factors. The binding affinity of TEAi for TEAD is not reported. The claim that all TEAD-dependent transcription is blocked is an extrapolation from data on two target genes.
- **Why it matters** Off-target effects are a major concern for peptide therapeutics. Without selectivity data, the specificity of TEAi for TEAD cannot be established.
- **Resolution test** Perform binding assays against all four TEAD family members and unrelated DNA-binding proteins. Test the effect of TEAi on a panel of TEAD target genes and on global transcription. Report binding affinity constants.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided.
- **Issue** The abstract states "unexpectedly, TEAi induced nuclear export" but the preceding text does not establish why this is unexpected. The connection to the Nerfin-1 mechanism is not explained in the abstract.
- **Required correction** Briefly state the expected behavior based on Nerfin-1 function before introducing the unexpected observation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Methods, DNA pulldown
- **Evidence pointer** Methods, DNA pulldown section.
- **Issue** The DNA pulldown method does not specify the amount of biotinylated probe used, the concentration of competitor DNA, or the washing stringency. The method for preparing the short actin probe for pre-clearing is described but the purpose is not stated.
- **Required correction** Add the missing experimental details and explain the purpose of the pre-clearing step.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Statistics section
- **Evidence pointer** Statistics section.
- **Issue** The statistics section states that a two-tailed unpaired Student's t-test was used for all biochemical experiments, but the number of replicates for each experiment is not stated in the text.
- **Required correction** State the number of independent biological replicates for each experiment in the corresponding figure legend or methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** In vivo methods
- **Evidence pointer** Methods section, location not provided.
- **Issue** No methods are provided for the subcutaneous xenograft model, including animal strain, cell number injected, treatment schedule, or tumor measurement protocol.
- **Required correction** Add a detailed xenograft methods section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and text
- **Evidence pointer** Abstract, location not provided.
- **Issue** The term "designated" is used where "designed" is likely intended. The phrase "exdogenous" appears in the text and should be "exogenous."
- **Required correction** Correct the typographical errors.

## Risk / unsupported claims

- The claim that TEAi "potently suppressed" TEAD-YAP-driven transcriptional activity is unsupported without visible quantitative data.
- The claim that TEAi "completely abolished" TEAD-YAP activation of the CTGF-luc reporter is unsupported without visible data.
- The claim that TEAi induces nuclear export of TEAD2 is unsupported without quantified immunofluorescence data.
- The claim that TEAi "significantly suppressed" tumor growth in vivo is unsupported without visible xenograft data.
- The claim that TEAi blocks "all TEAD-dependent oncogenic transcription" is an overgeneralization based on data from two target genes.
- The claim that TEAi offers a potential advantage over YAP-binding inhibitors is speculative and not directly tested in this manuscript.
- The binding affinity of TEAi for TEAD is not reported, making the claim of direct binding unquantified.
- The selectivity of TEAi for TEAD over other DNA-binding proteins is not demonstrated.