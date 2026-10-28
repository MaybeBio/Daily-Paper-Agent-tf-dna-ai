## Review setup
- **Input scope** Full manuscript text (abstract, main text, results, discussion, methods, figure legends, supplementary data legends)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No figures or supplementary data files were available for direct inspection.
- **Shared manuscript claim summary** The authors identify PfAP2-HCR (PF3D7_0420300) as an essential ApiAP2 transcription factor that regulates host cell remodeling during the ring stage of Plasmodium falciparum asexual development and is also required for gametocytogenesis. Conditional truncation of pfap2-hcr leads to ring stage arrest, loss of Maurer's clefts, disruption of exported protein expression, and defective gametocyte formation. Integrated RNA-seq, ChIP-seq, and proteomics identify direct targets including EXP1 and EXP2.
- **Visible evidence base** Text descriptions of results from conditional gene truncation experiments, growth assays, RNA-seq, ChIP-seq, U-ExM imaging, transmission electron microscopy, and ChIP-MS. Figure references are provided but figures themselves were not available for review.
- **Missing materials affecting confidence** All figures, extended data figures, and supplementary data files were not provided. Statistical details, exact sample sizes, replicate numbers, and quantitative values for many experiments are not described in the text. The U-ExM methodology section is incomplete. ChIP-seq peak calling parameters and quality metrics are only partially described.

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in understanding the transcriptional regulation of host cell remodeling in P. falciparum. The identification of PfAP2-HCR as a central regulator of exported proteins is potentially significant. However, the current text does not provide sufficient quantitative detail to fully evaluate the strength of the claims. The phenotypic data are described qualitatively in several places, and key experimental details are missing. The claim that PfAP2-HCR directly regulates approximately 30% of exported proteins requires careful scrutiny given the limited description of the ChIP-seq analysis. The gametocyte experiments are described but the quantification and statistical analysis are not presented in sufficient detail. The manuscript would benefit from clearer presentation of the direct versus indirect regulatory relationships and from additional functional validation of the proposed regulatory network.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in Plasmodium, particularly those focused on ApiAP2 transcription factors, host cell remodeling, protein export, and gametocyte biology. The work may also interest those studying apicomplexan gene regulation more broadly, given the conservation of AP2 factors across the phylum. The potential identification of a master regulator of exported proteins could inform efforts to understand and disrupt parasite host remodeling as a therapeutic strategy.
- **Major strengths** The study addresses a significant and understudied question in malaria biology. The use of conditional truncation is appropriate for studying an essential gene. The integration of multiple approaches (transcriptomics, chromatin profiling, proteomics, and high-resolution imaging) is commendable. The identification of a specific transcription factor that controls a large fraction of the exportome provides a potential entry point for understanding the coordinated regulation of host remodeling. The extension to gametocyte biology broadens the significance of the findings.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The manuscript lacks sufficient quantitative detail for several key experiments. The ChIP-seq analysis is described without clear information on peak calling thresholds, reproducibility metrics, or the criteria for assigning direct targets. The RNA-seq differential expression analysis is described but the magnitude of effects and the overlap between ChIP-seq and RNA-seq targets are not quantified in the text. The U-ExM experiments are described qualitatively without quantification of fluorescence intensity or localization patterns. The gametocyte experiments lack clear quantification of the phenotypes described. The growth assay data are described but the statistical analysis is not presented.
- **Assessment against Nature-style criteria** Originality: The identification of a dedicated transcription factor controlling host cell remodeling is a novel contribution. Scientific importance: The work addresses a fundamental question in Plasmodium biology with potential implications for understanding pathogenesis and transmission. Interdisciplinary readership: The findings will interest parasitologists, cell biologists, and transcriptional regulation researchers. Technical soundness: The experimental approaches are appropriate, but the current presentation lacks sufficient quantitative detail to fully assess technical rigor. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with Plasmodium biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the current manuscript does not provide sufficient quantitative evidence to fully establish the claims. Additional detail on the ChIP-seq and RNA-seq analyses, quantification of imaging data, and clearer presentation of the gametocyte phenotypes would strengthen the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Integrated RNA-seq and ChIP-seq analyses revealed that PfAP2-HCR directly or indirectly regulates approximately 30% of exported proteins, including 27 essential exported factors, the parasitophorous vacuole membrane (PVM) resident protein EXP1, and the core PTEX component EXP2."
- **Evidence pointer** Results section "PfAP2-HCR directly regulates genes required for host cell remodeling"; Figure 3; Supplementary Data 1 and 3
- **Concern** The claim that PfAP2-HCR regulates 30% of exported proteins is central to the manuscript, but the text does not provide sufficient detail on how this number was derived. The ChIP-seq analysis is described without information on the number of peaks, the peak calling thresholds, the false discovery rate, or the criteria for assigning peaks to genes. The overlap between ChIP-seq targets and RNA-seq differentially expressed genes is not quantified. The distinction between direct and indirect regulation is not clearly operationalized. Without these details, it is difficult to evaluate whether the 30% figure is robust or an artifact of the analysis parameters.
- **Why it matters** The central claim of the manuscript rests on the identification of PfAP2-HCR as a major regulator of the exportome. If the ChIP-seq analysis is not rigorously described, the reader cannot assess whether the regulatory network proposed is accurate. The distinction between direct and indirect targets is important for understanding the mechanism of regulation and for designing follow-up experiments.
- **Resolution test** Provide a detailed description of the ChIP-seq analysis, including the number of peaks identified, the peak calling parameters, the reproducibility between biological replicates, and the criteria for assigning peaks to genes. Quantify the overlap between ChIP-seq targets and RNA-seq differentially expressed genes. Provide a clear definition of direct versus indirect regulation and justify the assignment of each category.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Conditional truncation of pfap2-hcr at cycle 0 showed that both control and Δpfap2-hcr parasites were able to proceed to the next cycle (i.e. cycle 1) without any significant difference in parasitemia between control and Δpfap2-hcr parasites suggesting that there were no issues with parasite egress and/or invasion. Interestingly, in contrast, control parasites proceeded to cycle 2 as expected whereas pfap2-hcr parasites failed to complete cycle 1 with a dramatic reduction in parasitemia compared with controls in cycle 2."
- **Evidence pointer** Results section "PfAP2-HCR is essential for ring stage development and gametocytogenesis"; Figure 1f-g
- **Concern** The growth assay data are described qualitatively. The text states there was "no significant difference" in cycle 1 and a "dramatic reduction" in cycle 2, but no quantitative values, statistical tests, or effect sizes are provided. The number of biological replicates is not stated. The timing of the growth measurement is not specified. Without these details, the reader cannot assess the robustness of the phenotype or whether the differences are statistically meaningful.
- **Why it matters** The essentiality of PfAP2-HCR for ring stage development is a key finding. If the growth assay data are not rigorously quantified and statistically analyzed, the strength of this conclusion is weakened. The distinction between effects on invasion versus intracellular development is important for understanding the mechanism of action.
- **Resolution test** Provide quantitative growth data with exact parasitemia values, standard deviations or confidence intervals, and statistical tests for each time point and condition. State the number of biological and technical replicates. Clearly describe the timing of drug addition and growth measurements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "In both experimental conditions, rapamycin-treated parasites showed a pronounced defect in gametocyte formation and maturation. By day 10 of gametocyte induction, Δpfap2-hcr cultures from the first condition contained predominantly pyknotic infected red blood cells, with only a small proportion of deformed gametocytes and almost no morphologically mature gametocytes."
- **Evidence pointer** Results section "PfAP2-HCR is essential for ring stage development and gametocytogenesis"; Figure 1h-j; Extended Data Fig. 4a-c
- **Concern** The gametocyte experiments are described qualitatively. The text states there was a "pronounced defect" and describes the presence of "pyknotic" and "deformed" gametocytes, but no quantitative data are provided. The proportion of each phenotype is not given. The number of gametocytes counted, the number of replicates, and the statistical analysis are not described. The distinction between effects on gametocyte commitment, early development, and maturation is not clearly addressed.
- **Why it matters** The claim that PfAP2-HCR is required for gametocytogenesis is a significant extension of the findings beyond asexual blood stages. If the phenotype is not rigorously quantified, the reader cannot assess the strength of this conclusion or compare it to other studies of gametocyte development.
- **Resolution test** Provide quantitative data on gametocyte numbers, morphology, and maturation stages for both control and rapamycin-treated conditions. State the number of replicates and the statistical tests used. Clearly describe the timing of drug addition relative to gametocyte induction and the criteria for classifying gametocyte stages.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** "Notably, this motif differs from the binding motifs identified in this study. This discrepancy may reflect differences between in vitro and in vivo binding contexts. The earlier study examined an isolated DNA-binding domain under in vitro conditions, whereas our analysis captures genome-wide binding of the full-length protein in the parasite nucleus."
- **Evidence pointer** Results section "PfAP2-HCR directly regulates genes required for host cell remodeling"; Figure 3d
- **Concern** The discrepancy between the in vitro binding motif (CACACA) and the in vivo motifs identified in this study is acknowledged but not experimentally addressed. The authors speculate about possible reasons for the discrepancy but do not provide evidence to support their interpretation. The possibility that the in vivo motifs represent indirect binding or that the ChIP-seq analysis has identified a different binding mode is not fully explored.
- **Why it matters** Understanding the DNA binding specificity of PfAP2-HCR is important for identifying its direct targets and for understanding its regulatory mechanism. If the in vivo motifs are not validated as direct binding sites, the assignment of direct targets may be incorrect.
- **Resolution test** Provide experimental validation of the in vivo binding motifs, such as electrophoretic mobility shift assays or reporter assays, to confirm that PfAP2-HCR binds these motifs directly. Alternatively, discuss the possibility that the in vivo motifs represent indirect binding or that the ChIP-seq analysis has limitations that could affect motif identification.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** "PfAP2-HCR also bound the putative promoters of 10 other apiap2 genes, including ap2-l, ap2-exp, ap2-g, ap2-hs, ap2-o, ap2-o3, and ap2-o5, as well as other uncharacterized members (PF3D7_0934400 and PF3D7_1115500), and its own promoter, suggesting autoregulation."
- **Evidence pointer** Results section "PfAP2-HCR directly regulates genes required for host cell remodeling"; Extended Data Fig. 8; Supplementary Data 3
- **Concern** The claim that PfAP2-HCR binds the promoters of other apiap2 genes and its own promoter is based on ChIP-seq data, but the text does not provide details on the strength of these binding events, the number of reads, or the statistical significance. The functional significance of these binding events is not explored. The observation that conditional truncation of pfap2-hcr leads to upregulation of these genes is mentioned but not quantified or discussed in detail.
- **Why it matters** The proposed autoregulatory loop and cross-regulation of other AP2 factors is an interesting finding that could have implications for understanding the regulatory network. However, without details on the strength and significance of the binding events, the reader cannot assess whether these are biologically meaningful interactions.
- **Resolution test** Provide details on the ChIP-seq signal strength and statistical significance for the binding events at these promoters. Quantify the changes in expression of these apiap2 genes upon PfAP2-HCR truncation and discuss the functional implications of the proposed regulatory network.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that PfAP2-HCR is "essential for ring stage development and parasite maturation" and later that it is "indispensable for gametocytogenesis." The use of both "essential" and "indispensable" is redundant. Consider using consistent terminology.
- **Required correction** Use "essential" consistently throughout the abstract and main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "PfAP2-HCR is essential for ring stage development and gametocytogenesis"
- **Evidence pointer** Results section; Figure 1
- **Issue** The text states that "PfAP2-HCR is readily detected within the parasite nucleus" in control cells, but the timing of this detection relative to the cell cycle is not specified. The text also states that PfAP2-HCR is "not detectable from the late ring stage until the onset of cytokinesis," but the method of detection (U-ExM) and the quantification are not described.
- **Required correction** Specify the cell cycle stages at which PfAP2-HCR is detected and provide quantification of the U-ExM signal.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "PfAP2-HCR regulates the expression of exported proteins required for host cell remodeling"
- **Evidence pointer** Results section; Figure 2
- **Issue** The text states that "the majority of affected genes were downregulated upon PfAP2-HCR truncation, suggesting PfAP2-HCR functions primarily as a transcriptional activator." The text does not provide the proportion of downregulated versus upregulated genes or the magnitude of the expression changes.
- **Required correction** Provide the number and proportion of downregulated and upregulated genes, and the range of fold changes observed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "PfAP2-HCR directly regulates genes required for host cell remodeling"
- **Evidence pointer** Results section; Figure 3
- **Issue** The text states that "PfAP2-HCR binding was highly enriched at the promoters of genes encoding exported proteins," but the enrichment score or statistical significance is not provided.
- **Required correction** Provide the enrichment score and statistical significance for the enrichment of PfAP2-HCR binding at promoters of exported protein genes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion states that "PfAP2-HCR is highly expressed in multiple life-cycle stages, including sexually committed schizonts and rings, ookinetes, and sporozoites." The source of this expression data is not clearly cited in the text.
- **Required correction** Provide a citation or reference for the expression data across life-cycle stages.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, "Ultrastructure Expansion Microscopy (U-ExM)"
- **Evidence pointer** Materials and Methods
- **Issue** The U-ExM methods section is incomplete. It states that the protocol was adapted from previous work but does not provide sufficient detail on the specific steps, reagents, or imaging parameters used.
- **Required correction** Provide a complete description of the U-ExM protocol, including all reagents, incubation times, and imaging parameters.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, "ChIP–seq library preparation, processing and analysis"
- **Evidence pointer** Materials and Methods
- **Issue** The ChIP-seq analysis section does not describe the peak calling algorithm parameters, the method for identifying reproducible peaks, or the criteria for assigning peaks to genes.
- **Required correction** Provide a detailed description of the ChIP-seq data analysis pipeline, including all parameters and thresholds used.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "PfAP2-HCR is essential for ring stage development and gametocytogenesis"
- **Evidence pointer** Results section; Extended Data Fig. 3b
- **Issue** The text describes stage-specific truncation experiments but does not provide details on how the efficiency of truncation was assessed at each stage or whether the timing of drug addition was validated.
- **Required correction** Provide details on the validation of stage-specific truncation, including the timing of drug addition and the assessment of truncation efficiency.

## Risk / unsupported claims
- The claim that PfAP2-HCR regulates approximately 30% of exported proteins cannot be fully evaluated without detailed ChIP-seq and RNA-seq analysis parameters and quantitative overlap statistics.
- The claim that PfAP2-HCR is "indispensable for gametocytogenesis" is based on qualitative descriptions of phenotypes without quantitative data or statistical analysis.
- The claim that the observed var gene downregulation is an indirect effect is speculative and not supported by direct experimental evidence.
- The claim that PfAP2-HCR functions as part of a repressive regulatory complex is based on indirect evidence and requires further validation.
- The discrepancy between the in vitro and in vivo DNA binding motifs is acknowledged but not experimentally resolved.
- The functional significance of PfAP2-HCR binding to the promoters of other apiap2 genes is not experimentally addressed.
- The claim that PfAP2-HCR is expressed in multiple life-cycle stages is not supported by data presented in the manuscript text.