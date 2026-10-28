## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, experimental logic, evidence quality, and internal consistency of the claims as presented in the supplied text
- **Shared manuscript claim summary** The authors reconstitute ATP-dependent topological DNA loading by the Smc5/6 holo-complex, identify the neck gate (Smc6/Nse4 interface) as the DNA entry gate, demonstrate that DNA is captured as a looped segment within the SMC compartment, and show that this entrapment occurs in vivo
- **Visible evidence base** Figures 1-6 and supplementary figures S1-S8 are referenced; however, only the main text is provided, with no figure panels, numerical data, or supplementary material included
- **Missing materials affecting confidence** All figure images, numerical quantifications, supplementary tables (S1-S4), and detailed experimental protocols for key assays (e.g., topological DNA binding, mini-chromosome entrapment) are not available for inspection

## Reviewer
- **Overall assessment** This manuscript presents a well-designed biochemical reconstitution study that addresses a fundamental question in SMC biology, namely how Smc5/6 complexes engage DNA topologically. The experimental strategy using site-specific cysteine cross-linking to create covalently closed compartments is elegant and appropriate. The central claims, that DNA is entrapped within the kleisin compartment and that a looped DNA segment is captured in the SMC compartment, are logically derived from the described experiments. However, the absence of quantitative data, figure panels, and detailed controls in the provided material prevents full verification of the conclusions. The in vivo entrapment experiment is particularly important but its description is incomplete. The mechanistic model proposed, unifying DNA loading and translocation via a segment-capture intermediate, is intellectually appealing but remains speculative given the evidence presented.

- **Who would be interested in the results, and why** Researchers studying SMC complexes (cohesin, condensin, Smc5/6), chromosome organization, DNA repair, and genome stability. The findings are also relevant to those interested in ATP-dependent molecular motors and DNA topology. The proposed unified mechanism for SMC ATPase function could influence models of loop extrusion and DNA translocation across the SMC family.

- **Major strengths** The experimental design is rigorous, using a combination of structure prediction, site-specific cross-linking, and biochemical assays to dissect DNA topology. The use of multiple cysteine combinations to create distinct compartments is a powerful approach. The inclusion of in vivo validation strengthens the physiological relevance. The authors address alternative interpretations and discuss differences between SMC complexes, showing balanced scientific judgment.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that "topological DNA loading by the Smc5/6 holo-complex is a robust and efficient reaction" and that a "large fraction of Smc5/6 entraps plasmid DNA under our experimental conditions"
- **Evidence pointer** Figure 1C-D, Figure S2D; location not provided
- **Concern** The quantification of DNA entrapment efficiency is described only qualitatively ("large fraction", "little or no DNA laddering"). No numerical values, error bars, or statistical analyses are provided. The laddering pattern is stated to be "fully dependent on ATP" and absent with linear DNA, but the actual gel images and densitometry data are not available for assessment. Without quantitative data, the efficiency claim cannot be evaluated.
- **Why it matters** The efficiency of entrapment is central to the claim that this is a physiologically relevant reaction. If the fraction of entrapped complexes is low, the biological significance could be questioned.
- **Resolution test** Provide densitometric quantification of laddering from at least three independent experiments, with statistical comparison between conditions (e.g., ATP vs. no ATP, wild-type vs. EQ/EQ, with vs. without Nse5/6). Show representative gels with molecular weight markers and loading controls.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental logic
- **Claim pointer** The authors conclude that "DNA segment capture" occurs in the SMC compartment based on experiments where the S compartment is split into S_up and S_lo sub-compartments using Nse3 cross-links
- **Evidence pointer** Figure 2A-B, Figure S4; location not provided
- **Concern** The logic that splitting the S compartment into two sub-compartments demonstrates a looped DNA segment relies on the assumption that each sub-compartment entraps a single DNA double helix. However, the authors do not provide direct evidence that the cross-linking of Nse3 to Smc5 and Smc6 is complete or that the sub-compartments are fully sealed. Partial cross-linking could produce artifactual results. Additionally, the efficiency of the Nse3 cross-links is not quantified.
- **Why it matters** The conclusion that DNA is held as a loop with one passage in S_up and another in S_lo is a key mechanistic claim. If the sub-compartment cross-linking is incomplete, the observed laddering could arise from alternative configurations.
- **Resolution test** Quantify cross-linking efficiency for each Nse3 pair. Include a control where only one of the two Nse3 cross-links is present to show that both are required for the observed laddering. Consider using a DNA substrate with a defined nick or gap to distinguish topological from pseudo-topological entrapment.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that "the loader Nse5/6 opens the neck gate" based on reduced cross-linking of the Smc6/Nse4 interface in the presence of the loader
- **Evidence pointer** Figure 3, Figure S6; location not provided
- **Concern** The cross-linking efficiency at the neck gate is used as a proxy for gate opening, but the authors do not demonstrate that reduced cross-linking directly corresponds to physical separation of the Smc6 and Nse4 proteins. Alternative explanations, such as conformational changes that alter cysteine accessibility without gate opening, are not excluded. The restoration of cross-linking by ATP and DNA is interpreted as gate closure, but the kinetics and stoichiometry of this process are not characterized.
- **Why it matters** The identity of the DNA entry gate is a central claim. If the neck gate is not truly the entry gate, the proposed model for DNA loading would be incorrect.
- **Resolution test** Use an orthogonal method, such as FRET or single-molecule imaging, to directly monitor gate opening and closing. Alternatively, show that a covalently sealed neck gate (via the Smc6-Nse4 fusion) completely abolishes DNA entrapment, which the authors partially address but the data are not fully shown.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim "DNA entrapment is also detectable in vivo" using a mini-chromosome entrapment assay
- **Evidence pointer** Figure 6; location not provided
- **Concern** The in vivo experiment is described in a single paragraph with minimal detail. The method is referenced as "previously used for cohesin" but the specific adaptations for Smc5/6 are not described. The efficiency of entrapment, the specificity of the signal, and the controls (e.g., 5C control strain) are not quantified or shown. The statement that the control "did not show DNA entrapment" is not supported by data.
- **Why it matters** The in vivo validation is crucial for establishing physiological relevance. Without proper controls and quantification, the claim that Smc5/6 entraps DNA in cells is not substantiated.
- **Resolution test** Provide full experimental details, including the number of biological replicates, the efficiency of entrapment relative to a positive control (e.g., cohesin), and statistical analysis. Show the Southern blot images with appropriate loading controls and a titration of input DNA.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors propose that "DNA segment capture" during loading is structurally related to the segment-capture state during translocation/loop extrusion, offering "a unified framework for SMC ATPase function"
- **Evidence pointer** Discussion; location not provided
- **Concern** This is a speculative extrapolation. The authors do not provide direct evidence that the segment-capture state observed in loading is the same as that proposed for translocation. The connection is based on structural similarity arguments, but no structural data are presented to support this claim.
- **Why it matters** The unified model is a major conceptual contribution, but if it is not supported by evidence, it could be seen as overreach and may distract from the solid biochemical findings.
- **Resolution test** Either provide structural or biophysical evidence for the segment-capture state during translocation, or clearly frame this as a hypothesis requiring future testing. Consider softening the language in the discussion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "we describe the reconstitution of ATP-dependent topological DNA loading by Smc5/6 rings" but does not mention the key finding that the neck gate is the entry gate, which is a major conclusion of the paper.
- **Required correction** Include a brief mention of the entry gate identification in the abstract to accurately summarize the main findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section, "Mini-chromosome entrapment assays"; location not provided
- **Issue** The methods section contains a typo ("folliwng") and an incomplete reference ("Srinivasan, Cell paper 2018?"). The description of the in vivo assay is insufficient for reproduction.
- **Required correction** Fix the typo, provide the full citation for the original protocol, and expand the methods to include all critical steps, buffer compositions, and incubation times.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1A; location not provided
- **Issue** The schematic in Figure 1A is described as showing possible modes of DNA interaction, but the figure itself is not available. The text refers to "topological DNA entrapment, DNA loop entrapment, and exclusively external DNA association" but does not clearly define these in the text.
- **Required correction** Ensure the figure legend clearly defines each mode and that the text provides sufficient explanation for readers who may not be familiar with the terminology.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section
- **Evidence pointer** Results, "DNA segment capture in the SMC compartment"; location not provided
- **Issue** The authors state that "no loader-dependent DNA entrapment was observed for the S compartment" but later propose that DNA segment capture occurs in the S compartment. This apparent contradiction is not fully resolved in the text.
- **Required correction** Clarify the distinction between entrapment in the full S compartment versus the sub-compartments, and explain why the S compartment alone does not show entrapment while the sub-compartments do.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction cites a reference as "reviewed in 1" but does not provide a full citation. The reference list is not included in the provided material.
- **Required correction** Ensure all references are complete and properly formatted.

## Risk / unsupported claims
- The claim that "a large fraction of Smc5/6 entraps plasmid DNA" is unsupported without quantitative data.
- The claim that the neck gate is the "major and likely only entry gate" is not fully established, as alternative entry routes are not exhaustively excluded.
- The proposal that DNA segment capture during loading is structurally related to the segment-capture state during translocation is speculative and not directly supported by the data.
- The in vivo entrapment claim is not verifiable from the provided text due to insufficient methodological detail and missing data.
- The statement that "the loader Nse5/6 opens the neck gate" is inferred from cross-linking efficiency changes and lacks direct physical evidence.