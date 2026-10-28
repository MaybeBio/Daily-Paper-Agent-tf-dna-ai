## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript text; no external data or unpublished materials were consulted
- **Shared manuscript claim summary** The authors propose that moderate drought priming enhances acquired drought tolerance in tea plants (Camellia sinensis) through flavonoid accumulation, and that two transcription factors, CsYABBY1 and CsMYB114, coordinately activate flavonoid biosynthetic genes to confer this tolerance via reactive oxygen species scavenging.
- **Visible evidence base** Physiological measurements (LRWC, chlorophyll fluorescence, Fv/Fm, MDA, H2O2, O2−), metabolomic and transcriptomic profiling, transgenic overexpression in tea, Y1H, dual-LUC, EMSA, molecular docking, and AsODN-based silencing experiments
- **Missing materials affecting confidence** Supplementary figures (Figure S1–S9), Supplementary tables (Table S1–S9), detailed methods (Methods S1–S13), raw RNA-seq data, and statistical details for several experiments are referenced but not provided; this limits full verification of experimental design, replicates, and data quality

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in tea plant drought resilience, and the integration of multi-omics with functional validation is commendable. The identification of CsYABBY1 and CsMYB114 as cooperative regulators of flavonoid biosynthesis is potentially novel and of interest to the plant stress and secondary metabolism communities. However, several technical concerns, particularly around the specificity of the Y1H and EMSA results, the lack of genetic evidence for the cooperative model, and incomplete presentation of statistical and methodological details, prevent the case from being fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying drought stress memory and priming in perennial crops, plant secondary metabolism and flavonoid regulation, transcription factor networks in stress responses, and those interested in breeding strategies for climate-resilient tea cultivars. The work may also appeal to the broader plant abiotic stress community given the general relevance of priming mechanisms.
- **Major strengths** 1) The systematic screening of priming intensities to identify moderate priming as optimal is a practical and valuable contribution. 2) The multi-omics approach linking metabolomic and transcriptomic data to a specific pathway (flavonoid biosynthesis) is well executed. 3) Functional validation through overexpression in tea plants, rather than heterologous systems, strengthens the relevance of the findings. 4) The combination of Y1H, dual-LUC, EMSA, and molecular docking provides multiple lines of evidence for direct TF-promoter interactions. 5) The AsODN silencing experiments provide loss-of-function evidence supporting the role of the two TFs.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (Y1H specificity), R1-M2 (cooperative model evidence), R1-M3 (statistical transparency), R1-M4 (molecular docking validation)
- **Assessment against Nature-style criteria** Originality: The study is original in its focus on the combinatorial role of a YABBY and an R2R3-MYB TF in drought memory, which has not been previously reported in tea or other crops. Scientific importance: The work has clear applied relevance for tea breeding and provides mechanistic insight into priming-induced stress memory, which is a topic of broad significance. Interdisciplinary readership: The findings will appeal to plant molecular biologists, stress physiologists, and crop scientists, though the scope is somewhat narrow for a general audience. Technical soundness: The experimental design is generally sound, but several technical concerns (see below) need to be resolved to fully support the conclusions. Readability for nonspecialists: The manuscript is clearly written and logically structured, though some sections assume familiarity with specific molecular techniques.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the specificity of DNA-binding assays, the evidence for the cooperative model, and the transparency of statistical reporting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that CsYABBY1 and CsMYB114 directly bind to the promoters of flavonoid biosynthetic genes based on Y1H, dual-LUC, EMSA, and molecular docking results.
- **Evidence pointer** Results section "CsYABBY1 and CsMYB114 Could Promote the Expression of CsCHS, CsCHI, CsFLS, CsDFR, CsANS and CsANR"; Figure 6; Figure S9; Table S8 and S9
- **Concern** The Y1H assay is prone to false positives, particularly when TFs are expressed at high levels or when yeast cells are grown under stringent selection. The manuscript does not report the concentration of aureobasidin A (AbA) used, nor does it describe the construction of the reporter strains (e.g., whether the promoter fragments were cloned upstream of the reporter gene in the correct orientation and copy number). Additionally, the EMSA results are described but not shown in the main figures; the authors state that CsYABBY1 and CsMYB114 "respectively bound" to core cis-elements, but the specificity of binding (e.g., competition with unlabeled probes, mutation of binding sites) is not described. The molecular docking results are presented as supporting evidence, but docking alone cannot confirm physical binding and should be treated as predictive rather than confirmatory.
- **Why it matters** The central claim of the paper rests on the direct regulation of flavonoid biosynthetic genes by these two TFs. If the binding assays are not rigorously controlled, the conclusion that CsYABBY1 and CsMYB114 directly activate these genes is not fully supported, which would weaken the proposed regulatory model.
- **Resolution test** Provide details on AbA concentration and reporter strain construction for Y1H. Include EMSA data with appropriate controls (e.g., unlabeled competitor DNA, mutant probes) in the main figures. Clarify the limitations of molecular docking and, if possible, validate binding using an independent method such as chromatin immunoprecipitation (ChIP) or a plant-based one-hybrid assay.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors propose a "synergistic regulatory model" in which CsYABBY1 and CsMYB114 "coordinately upregulate" flavonoid biosynthesis genes, implying a cooperative or additive effect.
- **Evidence pointer** Results sections "Identification of a Regulatory Network..." and "Overexpression of CsYABBY1 and CsMYB114..."; Figures 4 and 5
- **Concern** The evidence for coordination is based on co-expression analysis and the observation that both TFs can activate the same target genes. However, no experiment directly tests whether the two TFs act synergistically, additively, or independently. For example, co-overexpression of both TFs compared to each alone, or a genetic interaction study, would be needed to support the claim of coordination. The current data show that each TF can activate the promoters individually, but this does not demonstrate a cooperative mechanism.
- **Why it matters** The proposed model of cooperative regulation is a key conceptual advance of the paper. Without direct evidence for synergy or physical interaction, the model remains speculative and the claim of "coordination" is overstated relative to the data presented.
- **Resolution test** Perform co-overexpression experiments (both TFs together vs. individually) and measure target gene expression and flavonoid content. Alternatively, test for physical interaction between CsYABBY1 and CsMYB114 (e.g., co-immunoprecipitation or yeast two-hybrid) to support a cooperative mechanism.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript reports numerous physiological, metabolomic, and transcriptomic comparisons across multiple treatment groups and time points.
- **Evidence pointer** Results sections "Moderate Drought Priming Enhanced..." and "Flavonoids Are the Key Imprinted Metabolites..."; Figures 1 and 2; Tables S1, S3, S4
- **Concern** The number of biological replicates for each experiment is not consistently stated. For example, the physiological measurements (LRWC, Fv/Fm, MDA, etc.) are described as having "at least three separate biological replicates," but it is unclear whether this applies to all time points and treatment groups. The metabolomic and transcriptomic analyses do not specify the number of replicates per condition, nor the statistical tests used to identify differential metabolites and genes (e.g., fold-change thresholds, FDR-corrected p-values). Without this information, the robustness of the differential abundance and expression claims cannot be assessed.
- **Why it matters** Reproducibility is a core requirement for high-impact publications. The lack of explicit replicate numbers and statistical thresholds undermines confidence in the reliability of the multi-omics datasets and the conclusions drawn from them.
- **Resolution test** Clearly state the number of biological replicates for each experiment in the figure legends and methods. Provide the statistical criteria used for defining differentially accumulated metabolites and differentially expressed genes, including thresholds and multiple-testing corrections.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors use molecular docking to support the binding of CsYABBY1 and CsMYB114 to promoter cis-elements.
- **Evidence pointer** Results section "CsYABBY1 and CsMYB114 Could Promote the Expression..."; Figure S9; Table S9
- **Concern** Molecular docking is a computational prediction method and is not a substitute for experimental validation of protein-DNA interactions. The manuscript does not describe the docking methodology in sufficient detail (e.g., software used, scoring function, how the DNA structures were generated, whether the predicted binding poses were consistent across multiple runs). The ΔiG values are reported, but the significance of these values is not contextualized against known positive and negative controls.
- **Why it matters** While docking can provide supporting evidence, it cannot confirm that the TFs actually bind these promoters in vivo. Over-reliance on docking results without appropriate experimental validation could mislead readers about the strength of the evidence.
- **Resolution test** Provide full methodological details for the docking analysis, including software parameters and validation against known binding events. If possible, include a positive control (e.g., a known TF-DNA interaction) and a negative control (e.g., a scrambled or mutated binding site) to demonstrate the specificity of the predictions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Results section "Moderate Drought Priming Enhanced..."; Figure 1
- **Issue** The figure legend does not clearly define the abbreviations used for the treatment groups (e.g., C1-T1, C1-T2, R-T1, R-T2, R-T3, C2-T1, C2-T2). While the text explains these, a concise definition in the legend would improve readability.
- **Required correction** Add a brief description of the treatment group abbreviations in the Figure 1 legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Materials and Methods, "Measurement of Drought-Related Indicators"
- **Issue** The methods for measuring MDA, H2O2, and O2− are referenced to "Methods S2" but are not described in the main text. Given the importance of these measurements to the conclusions, at least a brief description of the protocols should be included in the main methods.
- **Required correction** Provide a brief summary of the protocols for MDA, H2O2, and O2− measurements in the main text, with full details in the supplementary methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, "Drought Priming Enhances the Acquired Drought Tolerance..."
- **Issue** The discussion of the "stress memory" concept would benefit from a more explicit link to the specific molecular memory markers (e.g., epigenetic marks or sustained transcriptional changes) that were or were not examined in this study. The authors mention epigenetic regulation as a future direction but do not discuss whether any of their data (e.g., sustained gene expression changes) could be interpreted as memory markers.
- **Required correction** Add a brief paragraph discussing which aspects of the data support a memory-like mechanism and which remain unresolved, to strengthen the conceptual framing.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Results section "High Expression Levels of Six Flavonoid Biosynthetic Genes..."; Figure 3
- **Issue** The overexpression data are presented as fold-changes relative to control, but the baseline expression levels of the six genes in wild-type plants are not shown. This makes it difficult to assess the magnitude of overexpression in absolute terms.
- **Required correction** Include a panel showing the absolute expression levels (e.g., RPKM or qPCR Ct values) of the six genes in control and overexpression lines.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 7
- **Evidence pointer** Results section "Silencing the Expression of Either CsYABBY1 or CsMYB114..."; Figure 7
- **Issue** The statistical comparisons for the AsODN silencing experiments are not fully described. It is unclear whether the comparisons are between silenced and control (sODN) plants within each treatment, or between different treatment groups.
- **Required correction** Clarify the statistical comparisons and the specific p-values in the figure legend or methods.

## Risk / unsupported claims
- The claim that CsYABBY1 and CsMYB114 "coordinately" or "synergistically" regulate flavonoid biosynthesis is not directly supported by the experimental data, as no co-overexpression or interaction studies were performed.
- The claim of direct binding of CsYABBY1 and CsMYB114 to promoter regions is supported by Y1H and EMSA, but the lack of detailed controls and the reliance on molecular docking as a confirmatory method weaken this claim.
- The statement that "moderate drought priming specifically conferred superior drought tolerance" is based on physiological comparisons, but the statistical robustness of these comparisons cannot be fully assessed without explicit replicate numbers and effect sizes.
- The generalizability of the findings to field conditions is not addressed; all experiments appear to have been conducted under controlled greenhouse conditions, and the authors do not discuss potential limitations of this approach.