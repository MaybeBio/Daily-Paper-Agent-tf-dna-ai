## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, methods, and supplementary figure legends.
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based on the provided text. No line numbers were provided; evidence pointers refer to sections, figures, or tables as named in the manuscript.
- **Shared manuscript claim summary** The manuscript claims that the Type IV restriction enzyme SauUSI, upon recognizing 5-methylcytosine (5mC), initiates ATP-driven unidirectional 3'–5' translocation by a single helicase-like subunit, displacing its target recognition domain (TRD). The partner TRD can then bind the liberated modified site, stabilizing a growing DNA loop. On symmetrically methylated DNA, both subunits engage in bidirectional loop translocation. Cleavage is triggered by distal methylated sites, preferred DNA sequences, or DNA ends, and repeated cycles of binding, translocation, and cleavage by individual enzymes result in shredding of modified DNA. The authors propose that interactions between SauUSI dimers or roadblocks are not required for nuclease activation.
- **Visible evidence base** Abstract, Introduction, Results and Discussion sections, Methods, and references to figures (Figs. 1–6), Extended Data figures, and Supplementary figures. No raw data, full figure panels, or supplementary files were provided for direct inspection.
- **Missing materials affecting confidence** Full figure panels, raw single-molecule traces, nanopore sequencing data, statistical analysis details, and the supplementary information (including protein purification details and oligonucleotide sequences) were not available. This limits the ability to fully assess data quality, reproducibility, and the robustness of the quantitative claims.

## Reviewer
- **Overall assessment** This manuscript presents a detailed and technically sophisticated study of the molecular mechanism of SauUSI, a Type IV restriction enzyme. The combination of ensemble biochemistry, single-molecule approaches, and nanopore sequencing is powerful and appropriate for dissecting the translocation and cleavage dynamics of this enzyme. The proposed model, involving unidirectional and bidirectional loop translocation and a role for individual enzymes in DNA shredding, is novel and mechanistically interesting. However, several claims, particularly regarding the trigger for cleavage and the role of roadblocks, are not fully supported by the evidence presented in the text. The manuscript would be significantly strengthened by a more quantitative and rigorous presentation of the single-molecule data and a clearer distinction between direct observations and inferred mechanisms.
- **Who would be interested in the results, and why** Researchers in the fields of bacterial defense systems, restriction-modification enzymes, DNA translocases, and single-molecule biophysics. The work provides new insights into the mechanism of a clinically relevant enzyme from *Staphylococcus aureus* and contributes to the broader understanding of how ATP-dependent motors can be coupled to nuclease activity for DNA degradation. The findings may also be of interest to those studying horizontal gene transfer and the evolution of bacterial immunity.
- **Major strengths**
    1. The use of orthogonal techniques (ensemble, single-molecule, and nanopore) to address the mechanism is a major strength and provides a multi-scale view of the process.
    2. The identification of unidirectional and bidirectional loop translocation modes is a significant and novel finding that advances the field.
    3. The study directly challenges the previous "pile-up" model for SauUSI cleavage, proposing a new paradigm where individual enzymes are sufficient for DNA shredding.
    4. The manuscript is generally well-written and the logic of the experiments is clear, making the complex single-molecule data accessible to a broad audience.
- **Major Concerns**
    - **R1-M1** (Blocking: Yes)
    - **R1-M2** (Blocking: Yes)
    - **R1-M3** (Blocking: No)
    - **R1-M4** (Blocking: No)
- **Minor Comments**
    - **R1-m1**
    - **R1-m2**
    - **R1-m3**
    - **R1-m4**
- **Technical failings that need to be addressed before the case is established**
    - The evidence for the "trigger" of cleavage is indirect and relies on inference from cleavage site distributions rather than direct observation of the nuclease activation event.
    - The quantitative analysis of single-molecule data, particularly regarding the distinction between different translocation modes and the calculation of rates, is not fully described in the text provided.
    - The role of roadblocks in modulating cleavage is presented as a negative result, but the statistical power and controls for these experiments are not fully detailed.
- **Assessment against Nature-style criteria**
    - **Originality** High. The proposed mechanism of individual SauUSI dimers performing multiple rounds of translocation and cleavage to shred DNA is a novel concept for Type IV restriction enzymes.
    - **Scientific importance** High. The work provides a mechanistic understanding of a key bacterial defense system and has implications for horizontal gene transfer and the evolution of restriction-modification systems.
    - **Interdisciplinary readership** Moderate. The topic is of primary interest to specialists in DNA repair, recombination, and bacterial immunity. The single-molecule approaches may appeal to biophysicists, but the broader significance for fields like microbiology and infectious disease is somewhat implicit.
    - **Technical soundness** The combination of methods is appropriate and powerful. However, the lack of full methodological detail and raw data in the provided text prevents a complete assessment of the technical soundness of every claim.
    - **Readability for nonspecialists** The abstract and introduction are clear and accessible. The results section is dense but logically structured. The authors make a good effort to explain the significance of their single-molecule observations.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are likely to be of significant interest, but the manuscript requires substantial revision to fully support the mechanistic claims with the presented evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim Support
- **Claim pointer** The manuscript claims that "Cleavage is triggered by binding a distal methylated site, by preferred DNA sequences, or upon reaching a DNA end." This is a central claim of the paper.
- **Evidence pointer** Results & Discussion sections "SauUSI can change motor activity upon reaching a 5mC site" and "Secondary cleavage results from cycles of site-binding, translocation and cleavage"; Figures 4, 5, and 6.
- **Concern** The evidence for the "trigger" of cleavage is largely indirect. The data show that cleavage occurs at certain locations (e.g., near roadblocks, at preferred sequences, or after encountering a second 5mC site), but this does not directly demonstrate that these events are the *trigger* for nuclease activation. For example, the increased cleavage near a roadblock could be due to the motor stalling there, increasing the residence time and thus the probability of a stochastic cleavage event, rather than the roadblock actively "triggering" the nuclease. Similarly, the role of "preferred DNA sequences" is based on a correlation with cleavage site distribution, not a direct test of sequence-dependent activation. The claim that a distal methylated site triggers cleavage is based on the observation of cleavage in the arc between two sites, but this could also be explained by the motor stalling at the second site after translocating from the first. The authors need to provide more direct evidence, such as single-molecule experiments that directly correlate the moment of stalling or site encounter with the moment of DNA cleavage, to support this strong mechanistic claim.
- **Why it matters** This is the central mechanistic question of the paper. If the trigger for cleavage is not correctly identified, the proposed model for how SauUSI functions is incorrect. The distinction between a stochastic event and a specific trigger is fundamental to the proposed mechanism.
- **Resolution test** Provide direct experimental evidence, e.g., from high-speed AFM or single-molecule FRET, that shows the nuclease domain is activated specifically upon the motor encountering a roadblock, a preferred sequence, or a second site. Alternatively, perform experiments with a nuclease-dead mutant to show that the motor stalls at these locations but no cleavage occurs, and then demonstrate that the addition of a specific trigger (e.g., a second site) leads to cleavage.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical Soundness
- **Claim pointer** The manuscript claims that "unidirectional loop translocation" and "bidirectional loop translocation" are distinct modes of action, and that the rate of bidirectional loop translocation is "slightly more than double" the unidirectional rate.
- **Evidence pointer** Results & Discussion sections "SauUSI can initiate unidirectional loop translocation on hemimethylated DNA" and "SauUSI can initiate bidirectional loop translocation on dimethylated DNA"; Figures 2 and 3; Extended Data Figure 3.
- **Concern** The distinction between unidirectional and bidirectional loop translocation is a key finding. However, the evidence for this distinction, particularly in the magnetic tweezers (MT) data, is not fully convincing from the text. The authors state that "DNA shortening events consistent with directional loop translocation were observed" but do not provide a clear description of how they distinguished between a single motor translocating and looping out DNA versus two motors translocating in opposite directions. The rate comparison is also concerning. The claim that the bidirectional rate is "slightly more than double" the unidirectional rate is based on a comparison of rates measured in different experimental setups (C-trap vs. MT) and at different temperatures. This comparison is not valid without a proper temperature correction and a clear demonstration that the two assays are measuring the same fundamental process. The authors do mention a Q10 correction, but the details are not provided in the text.
- **Why it matters** The proposed model of two distinct translocation modes is central to the paper's novelty. If the data do not robustly support this distinction, the model is weakened. The rate comparison is used to support the idea of two independent motors, and an invalid comparison would undermine this conclusion.
- **Resolution test** Provide a more detailed and quantitative analysis of the single-molecule traces, including example traces that clearly show the difference between unidirectional and bidirectional looping. The rate comparison should be performed under identical conditions (e.g., same temperature, same assay) or with a rigorous and clearly described correction for the different conditions. Ideally, the rates of the two modes should be measured in the same experimental setup.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim Support
- **Claim pointer** The manuscript claims that "Interactions with other SauUSI dimers or protein roadblocks affect cleavage site distributions but are not required for nuclease activation."
- **Evidence pointer** Results & Discussion sections "SauUSI can change motor activity upon reaching a 5mC site" and "Secondary cleavage results from cycles of site-binding, translocation and cleavage"; Figures 5 and 6.
- **Concern** The conclusion that roadblocks are not required for activation is based on experiments where cleavage still occurs in the presence of a roadblock. However, the data also show that roadblocks bias the cleavage site distribution. The authors interpret this as a "corralling effect." This is a reasonable interpretation, but it is not the only one. It is possible that the roadblock does activate the nuclease, but that this activation is not absolute, and cleavage can also occur stochastically. The data as presented do not rule out a model where roadblock stalling *increases* the probability of activation, even if it is not strictly required. The distinction between "not required" and "modulates the probability of" is important and is not clearly resolved by the data.
- **Why it matters** This claim is used to differentiate SauUSI from other restriction enzymes that require motor-motor collisions for activation. If the data do not strongly support this distinction, the novelty of the mechanism is reduced.
- **Resolution test** Perform a more quantitative analysis of the cleavage site distribution in the presence and absence of roadblocks. If the roadblock is not required for activation, the rate of cleavage at a given site should be independent of the presence of a roadblock, even if the distribution of sites is altered. A detailed kinetic analysis of cleavage rates in the presence and absence of roadblocks would help to resolve this issue.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical Soundness
- **Claim pointer** The manuscript claims that "a single helicase-like ATPase motor is active during unidirectional dsDNA translocation" and that the coupling is "~1 ATP per bp".
- **Evidence pointer** Results & Discussion section "A single helicase-like ATPase motor is active during unidirectional dsDNA translocation"; Figure 1E and 1F; Extended Data Figure 2.
- **Concern** The conclusion that only one motor is active is based on the ATP coupling ratio. The authors measured the ATPase rate and the translocation rate and found a coupling of ~1 ATP per bp. They argue that this is consistent with a single motor, as two motors would be expected to consume 2 ATP per bp. This is a reasonable argument, but it relies on the accuracy of both rate measurements. The ATPase rate is corrected for the fraction of enzymes that initiate, which is estimated from the triplex displacement burst size. This correction is indirect and could introduce significant error. Furthermore, the translocation rate is measured at a single temperature (25°C), while the ATPase rate is measured at a different temperature (37°C). The authors do not mention a temperature correction for this comparison. This is a significant issue that could affect the calculated coupling ratio.
- **Why it matters** The number of active motors is a key mechanistic detail. If the coupling ratio is incorrect, the conclusion that only one motor is active could be wrong.
- **Resolution test** Measure the ATPase and translocation rates under identical conditions (same temperature, same buffer). Provide a more direct measurement of the number of active motors, for example, by using a fluorescently labeled ATP analog to count the number of ATP molecules hydrolyzed per translocation event in a single-molecule assay.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1D
- **Evidence pointer** Results & Discussion section "SauUSI is a directional dsDNA translocase that initiates upstream of 5-methylcytosine"
- **Issue** The description of the AlphaFold3 model is brief. It is unclear how the model was used to determine the "upstream initiation" and the "~22 bp" distance. A more detailed explanation of the modeling and its interpretation would be helpful.
- **Required correction** Provide a more detailed description of the AlphaFold3 model, including the input sequences, the confidence of the model, and how the DNA-binding interface was identified. A figure panel showing the model with the relevant distances and domains labeled would be beneficial.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical Soundness
- **Affected element** Methods, "Methylation of DNA substrates"
- **Evidence pointer** Methods section
- **Issue** The methods for methylation state that M1.BfuAI and M2.BfuAI are promiscuous and methylate "star sites". The authors state that these were removed from the DNA substrates. However, it is not clear how the removal of these sites was verified, nor is it clear whether the presence of these star sites could have affected the results of the experiments where these substrates were used.
- **Required correction** Clarify how the removal of star sites was verified (e.g., by sequencing or restriction digest). Discuss the potential impact of any residual star site methylation on the interpretation of the results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 4G
- **Evidence pointer** Results & Discussion section "SauUSI can change motor activity upon reaching a 5mC site"
- **Issue** The text states that "DNA with sites in HtH repeat were more frequently cleaved than DNA with sites in direct repeat" in the C-trap. It is unclear what "direct repeat" refers to in this context. Does it mean the TtT or TtH configuration?
- **Required correction** Define "direct repeat" clearly in the text or figure legend. Use the same terminology (HtH, TtH, TtT) throughout for consistency.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results & Discussion section "SauUSI can initiate bidirectional loop translocation on dimethylated DNA"
- **Evidence pointer** Figure 3A
- **Issue** The description of the C-trap experiment in Figure 3A is complex. It is stated that "four labelled SauUSI are visible... one 5mC-bound and three non-specific." The interpretation of the force trace and the assignment of which motor is doing what is not entirely clear from the text alone.
- **Required correction** Provide a more detailed, step-by-step interpretation of the example trace in the figure legend, clearly explaining the events and how they support the conclusion of bidirectional translocation.

## Risk / unsupported claims
- The claim that "Cleavage is triggered by binding a distal methylated site, by preferred DNA sequences, or upon reaching a DNA end" is not fully supported by the evidence presented. The data show correlations but do not directly demonstrate a causal trigger.
- The claim that "Interactions with other SauUSI dimers or protein roadblocks... are not required for nuclease activation" is a strong negative claim that is difficult to prove. The data are consistent with this, but do not rule out a modulatory role for these interactions.
- The quantitative comparison of unidirectional and bidirectional loop translocation rates is not valid as presented, due to differences in experimental conditions (temperature, setup) that are not rigorously controlled for.
- The claim that "a single helicase-like ATPase motor is active" is based on an indirect calculation of the ATP coupling ratio, which is sensitive to errors in the rate measurements and corrections.
- The statement that "the motor likely cannot bypass the TRD without displacing it" is a speculation based on a structural model and is not directly tested.