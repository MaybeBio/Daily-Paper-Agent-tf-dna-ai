## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific content, experimental logic, technical soundness, and interpretation as presented in the provided text; no assessment of supplementary figures beyond what is referenced
- **Shared manuscript claim summary** The authors propose a mechanistic model for how a single ORC molecule releases from its initial high-affinity DNA binding site (ACS) and rebinds a weaker, inverted secondary site (B2) during helicase loading. Using single-molecule FRET, they report that DNA unbending, Cdc6 release, and sliding of an ORC-Cdt1-Mcm2-7 complex sequentially reduce ORC stability on DNA, facilitating ORC dissociation and "flipping" to the opposite orientation.
- **Visible evidence base** Main text figures 1-7 (referenced), supplementary figures S1-S11 (referenced), supplementary tables S1-S3 (referenced); no raw data or full figure panels visible in the provided text
- **Missing materials affecting confidence** Full figure panels and legends, supplementary figure content, detailed statistical methods, raw single-molecule traces, and complete experimental protocols for some assays

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in eukaryotic DNA replication: how ORC switches between DNA binding sites during helicase loading. The single-molecule approach is well-suited to the problem, and the authors present a coherent model supported by multiple complementary assays. The finding that an ORC-Cdt1-Mcm2-7 complex slides on DNA after Cdc6 release is novel and mechanistically important. However, several technical concerns regarding the interpretation of FRET states, the specificity of the sliding assay, and the quantitative support for key claims need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers in DNA replication, single-molecule biophysics, and protein-DNA interaction dynamics. The work provides mechanistic insight into helicase loading and ORC site selection, which is relevant to understanding origin licensing regulation and replication initiation. The single-molecule methodology may also interest biophysicists studying dynamic protein-DNA interactions.

- **Major strengths** The study uses a powerful single-molecule approach to directly observe dynamic protein-DNA interactions in real time. The authors combine multiple FRET configurations to monitor different aspects of the process, and they validate their assignments with mutant controls. The temporal ordering of events (DNA unbending, Cdc6 release, sliding) is well-supported by the data presented. The model proposed is consistent with existing structural data and provides a clear framework for future studies.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of FRET interpretation
- **Claim pointer** The authors claim that low FRET values in the ORC C •+51 assay represent an "unbent" DNA state while high FRET values represent a "bent" state, and that transitions between these states reflect loss of ORC-BPR interaction.
- **Evidence pointer** Figure 1C-D, Figure 2A-B, SI Appendix Figures S1B, S2
- **Concern** The assignment of FRET states to specific DNA conformations relies on the assumption that the donor-acceptor distance changes primarily due to DNA bending. However, the ORC C label is on a truncated Orc6 N-terminus, and the acceptor is 51 bp from the ACS. The authors do not provide a calibration of FRET efficiency to actual distances, nor do they rule out that the low FRET state could arise from alternative ORC binding modes, partial dissociation, or conformational changes in ORC itself rather than DNA unbending. The control experiments described (SI Appendix Fig. S2) apparently rule out sliding but may not exclude other explanations.
- **Why it matters** The central conclusion that DNA unbending precedes and promotes ORC dissociation depends critically on the correct assignment of FRET states to DNA conformations. If the low FRET state reflects something other than unbent DNA, the mechanistic model would need revision.
- **Resolution test** Provide a distance calibration for the FRET pair (e.g., using DNA constructs with known bend angles or comparing to structural models). Include control experiments with ORC mutants that cannot bend DNA but still bind, or use an orthogonal readout of DNA bending (e.g., Förster resonance energy transfer to a second acceptor at a different position, or atomic force microscopy).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of sliding assay
- **Claim pointer** The authors claim that the OC 1 M complex slides bidirectionally on dsDNA after Cdc6 release, based on FRET changes detected with acceptors at positions -4 and +82 relative to the ACS.
- **Evidence pointer** Figure 4C-F, SI Appendix Figures S5-S7
- **Concern** The sliding assay relies on detecting FRET between Mcm2-7 3N-550 and DNA acceptors at positions -4 and +82. However, the authors do not demonstrate that the observed FRET peaks are specifically due to sliding of the intact OC 1 M complex rather than dissociation and rebinding of individual components, partial complex disassembly, or DNA looping. The statement that "the first sliding complex includes ORC, Mcm2-7, and Cdt1" is inferred from timing correlations but direct evidence for the composition of the sliding complex is not presented. Additionally, the possibility that the observed FRET changes reflect rotation or conformational changes of Mcm2-7 rather than translational movement is not fully excluded.
- **Why it matters** The claim that a ternary OC 1 M complex slides is a key novel finding. If the FRET changes are due to other processes, the model of how ORC accesses B2 elements would be incorrect.
- **Resolution test** Perform two-color co-localization experiments to directly demonstrate that ORC, Mcm2-7, and Cdt1 remain co-associated during the sliding events. Use DNA constructs with multiple acceptors at defined intervals to map the trajectory of the complex. Include controls with cross-linked or otherwise immobilized complexes to rule out dissociation-rebinding artifacts.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative support for kinetic claims
- **Claim pointer** The authors state that DNA unbending increases the rate of ORC dissociation by more than 40-fold (Figure 1E) and that Cdc6 release precedes sliding.
- **Evidence pointer** Figure 1E, Figure 5D, 5G, SI Appendix Table S1
- **Concern** The 40-fold difference in dissociation rate between high and low FRET states is a striking claim, but the statistical basis for this comparison is not fully described. The number of events analyzed, the method for determining dissociation rates from single-molecule data, and the confidence intervals are not provided in the main text. Similarly, the temporal ordering of Cdc6 release relative to sliding is based on comparing time distributions, but the statistical test used and the effect sizes are not clearly stated.
- **Why it matters** The quantitative claims are central to the proposed model of progressive ORC destabilization. Without proper statistical support, the strength of the conclusions is unclear.
- **Resolution test** Provide detailed statistical analysis including event counts, confidence intervals, and appropriate hypothesis tests for all rate comparisons. Show representative raw traces and the criteria used to identify dissociation and sliding events.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** The authors propose that the mechanism of ORC site exchange via sliding is general, citing variable distances between ACS and B2 elements across origins.
- **Evidence pointer** Discussion section, Figure 7
- **Concern** The experiments are performed exclusively on the ARS1 origin. While the authors discuss implications for other origins, no data are presented to show that the same mechanism operates at origins with different ACS-B2 distances or arrangements. The claim that sliding "enables ORC to search for another near-ACS sequence in the inverted orientation" is plausible but not directly tested.
- **Why it matters** The broader significance of the work depends on whether the mechanism is general or specific to ARS1. If the mechanism is origin-specific, the conclusions would be more limited.
- **Resolution test** Repeat key experiments (at minimum, the sliding assay) on at least one additional origin with a different ACS-B2 spacing. Alternatively, use a synthetic origin with variable B2 positioning to test the model's predictions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1A schematic
- **Evidence pointer** Figure 1A
- **Issue** The schematic in Figure 1A is described in the text but the figure itself is not visible in the provided material. The step numbering in the text (steps 1-6) is not fully aligned with the described events.
- **Required correction** Ensure the figure legend clearly maps each step to the corresponding text description and that the numbering is consistent.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** FRET threshold determination
- **Evidence pointer** Methods section, SI Appendix Table S1
- **Issue** The method for determining the FRET threshold (0.28) used to distinguish high and low FRET states is described as "the position of the trough in the fit," but the fitting procedure and the criteria for choosing between one- and two-component models are not fully specified.
- **Required correction** Provide additional detail on the fitting procedure, including the software used, the number of components tested, and the criteria for model selection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Timing comparisons in Figure 5D and 5G
- **Evidence pointer** Figure 5D, 5G
- **Issue** The percentages reported (80/84 and 89/91) are clear, but the statistical significance of the timing differences is not stated.
- **Required correction** Add p-values or confidence intervals for the comparisons between timing distributions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of ATPase mutant data
- **Affected element** Figure 5A
- **Evidence pointer** Figure 5A, SI Appendix Figure S7
- **Issue** The authors state that ATPase mutants show "prolonged duration of the high FRET state," but the quantitative extent of this prolongation and whether it is statistically significant across all six mutants is not reported.
- **Required correction** Provide a quantitative comparison of dwell times in the high FRET state for each mutant versus wild-type, with statistical tests.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of how ORC remains tethered after Cdc6 release is speculative and does not fully consider alternative possibilities, such as ORC remaining bound to DNA through weak, non-specific interactions without sliding.
- **Required correction** Briefly acknowledge and address alternative models for ORC retention, even if the data favor the sliding model.

- **Technical failings that need to be addressed before the case is established** R1-M1 (FRET state assignment) and R1-M2 (sliding complex composition) are the most critical. Without resolving these, the central claims of the paper are not fully supported. R1-M3 (statistical support) is also important for establishing the quantitative basis of the model.

- **Assessment against Nature-style criteria** 
  - **Originality**: High. The study provides the first real-time observation of ORC site exchange during helicase loading and identifies a sliding intermediate. This is a novel contribution.
  - **Scientific importance**: High. Understanding how ORC switches binding sites is fundamental to origin licensing and has implications for replication regulation. The findings address a key gap in the field.
  - **Interdisciplinary readership**: Moderate. The work will primarily interest DNA replication and single-molecule biophysics communities. The significance may be less immediately apparent to a broader biological audience, though the general principle of protein sliding on DNA has wider relevance.
  - **Technical soundness**: Moderate. The single-molecule assays are well-designed, but the interpretation of FRET states and the composition of the sliding complex require additional validation. Statistical reporting needs improvement.
  - **Readability for nonspecialists**: Good. The manuscript is clearly written, and the model is presented in an accessible way. The significance statement is helpful for a general audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important and the experimental approach is powerful, but the interpretation of key FRET data and the demonstration of the sliding complex composition need to be strengthened. The manuscript would be suitable for a high-impact journal after these issues are addressed.