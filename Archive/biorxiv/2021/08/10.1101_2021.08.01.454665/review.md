## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure/table references
- **Assessment boundary** Technical validity of the 3D-seq method as described, evidence supporting claims of DPI mapping capability, comparison to existing methods, and reproducibility of the presented data
- **Shared manuscript claim summary** The authors present 3D-seq, a method for genome-wide mapping of DNA-protein interactions in living bacterial cells, based on fusing the dsDNA-specific cytosine deaminase DddA to a DNA-binding protein of interest, followed by whole-genome sequencing to detect C-to-T mutations at binding sites. The method is claimed to be simpler, faster, and potentially applicable at single-cell resolution compared to existing approaches such as ChIP-seq and DamID.
- **Visible evidence base** Main text figures 1-3 (referenced but not fully visible), supplementary tables S1-S6 (referenced but not visible), methods section, statistical analysis description (partially provided)
- **Missing materials affecting confidence** Actual figure images and data plots, supplementary tables S1-S6 with peak lists and statistical values, complete statistical analysis methods, raw sequencing data, and detailed parameters for filtering thresholds

## Reviewer
- **Overall assessment** The manuscript describes a conceptually novel approach to DPI mapping that leverages the unique biochemical properties of DddA. The core idea is elegant and the proof-of-concept data for three transcription factors in P. aeruginosa is encouraging. However, the manuscript as presented has several critical gaps in the evidence base that prevent full assessment of the method's validity, sensitivity, and specificity. The statistical framework is only partially described, the filtering criteria appear somewhat arbitrary, and the comparison to ChIP-seq is limited to a single transcription factor. The claims of single-cell resolution and broad applicability are speculative at this stage. The work is potentially important but requires substantial additional validation and clearer presentation of data before the claims can be fully supported.

- **Who would be interested in the results, and why** Researchers in bacterial gene regulation, transcription factor biology, and microbial genomics would be the primary audience. The method could also interest those developing new tools for epigenomics and chromatin biology, particularly in organisms where ChIP-grade antibodies are unavailable. The potential for single-cell DPI mapping would attract researchers studying cellular heterogeneity in gene expression. The simplicity of the approach may also appeal to laboratories with limited specialized equipment.

- **Major strengths**
  1. Conceptual novelty: Using a dsDNA-specific cytosine deaminase for DPI mapping is a genuinely new idea that exploits the unique biochemistry of DddA.
  2. In vivo applicability: Unlike ChIP-seq and Cut&Run, the method captures interactions in living cells without crosslinking or cell lysis.
  3. Technical simplicity: The workflow from cell growth to sequencing is substantially simpler than ChIP-seq, requiring no antibodies or immunoprecipitation.
  4. Demonstrated utility across three transcription factors from different families, suggesting generalizability.
  5. The use of native promoters and chromosomal fusions reduces overexpression artifacts.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 3D-seq can identify DPI sites with high sensitivity and specificity, supported by the identification of 14 peaks for FleQ and 2 for GacA.
- **Evidence pointer** Figures 2-3, Table S1, location not provided
- **Concern** The statistical framework for peak calling is only partially described in the main text and the methods section is cut off mid-sentence. The description mentions a null hypothesis test with maximum likelihood fitting, but the specific model, parameters, and thresholds are not fully detailed. Without a complete description of the statistical methodology, it is impossible to assess whether the peak calling is rigorous, reproducible, or appropriately controlled for multiple testing. The filtering criteria (minimum read count threshold of ~1%, requirement for neighboring transition events within 100 bp, and reproducibility across 3 of 4 replicates) appear somewhat arbitrary and their impact on sensitivity and specificity is not systematically evaluated.
- **Why it matters** The core claim of the paper is that 3D-seq can reliably identify DPI sites. If the statistical framework is not fully described and validated, the identified peaks cannot be considered robust. This is particularly important given that the method relies on detecting rare mutation events that could arise from sequencing errors, PCR artifacts, or spontaneous deamination.
- **Resolution test** Provide a complete description of the statistical model, including the likelihood function, parameter estimation procedure, and threshold selection. Include a detailed analysis of the false discovery rate, perhaps using simulated data or spike-in controls. Demonstrate that the method can distinguish true binding sites from background mutations with known positive and negative controls.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 3D-seq offers advantages over ChIP-seq, including ease of implementation and the possibility of single-cell resolution.
- **Evidence pointer** Main text, "To benchmark the 3D-seq approach..." section, Table S2, location not provided
- **Concern** The comparison to ChIP-seq is limited to a single transcription factor (GcsR) and the results are only presented in supplementary tables. The manuscript does not provide a systematic comparison of sensitivity, specificity, or resolution between the two methods. The claim of single-cell resolution is purely speculative, as no single-cell experiments are presented. The authors state that "the lower limit on material for a 3D-seq study is defined only by the terminal DNA sequencing technology" but provide no experimental evidence to support this claim. Additionally, the ChIP-seq experiments appear to have been performed with a different strain background (VSV-G tagged vs. DddA fusion), which may introduce confounding variables.
- **Why it matters** The authors explicitly position 3D-seq as an alternative to ChIP-seq, and the claims of superiority in terms of simplicity and single-cell capability are central to the paper's significance. Without a rigorous head-to-head comparison and experimental demonstration of single-cell capability, these claims are not supported.
- **Resolution test** Perform a systematic comparison of 3D-seq and ChIP-seq for multiple transcription factors, including quantitative metrics of sensitivity, specificity, and resolution. Provide experimental evidence for single-cell DPI mapping, perhaps using a dilution series or single-cell sorting followed by sequencing. If single-cell capability is not demonstrated, temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 3D-seq can capture DPI dynamics under different regulatory states, specifically citing the GacS/GacA two-component system.
- **Evidence pointer** Figure 3, Table S1, location not provided
- **Concern** The experiments with GacA were performed in ΔretS and ΔgacS backgrounds to assess the effects of posttranslational regulation. However, the manuscript does not provide a clear demonstration that the differences in DPI patterns between these backgrounds are due to changes in GacA binding rather than indirect effects on protein stability, expression levels, or chromatin structure. The authors do not show that GacA protein levels are comparable between the two backgrounds, nor do they validate the predicted differences in binding using an independent method (e.g., electrophoretic mobility shift assay or reporter gene assays). The claim that 3D-seq can "capture a snapshot of the protein-DNA landscape during a fixed period of time" is not directly demonstrated.
- **Why it matters** The ability to measure DPI dynamics is presented as a key advantage of 3D-seq. If the method cannot reliably distinguish between different regulatory states, this claim is weakened. The lack of independent validation for the GacA results raises concerns about the method's ability to detect biologically meaningful changes in binding.
- **Resolution test** Provide quantitative measurements of GacA protein levels in the different backgrounds (e.g., Western blot). Validate the predicted differences in GacA binding using an independent method. Include time-course experiments to demonstrate the ability to capture dynamic changes in DPI patterns.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors claim that 3D-seq is reproducible, as evidenced by replicate experiments.
- **Evidence pointer** Figures 1-2, Methods section, location not provided
- **Concern** The manuscript mentions that "transition events observed in at least three of the samples were highly enriched in the peak region" but does not provide quantitative measures of reproducibility, such as correlation coefficients between replicates or a formal assessment of inter-replicate variability. The number of biological replicates is not clearly stated for all experiments, and the criteria for including or excluding replicates are not described. The manuscript also does not address potential batch effects or day-to-day variability in the protocol.
- **Why it matters** Reproducibility is a fundamental requirement for any genomic method. Without clear evidence of reproducibility, the reliability of the identified peaks is uncertain, and the method cannot be confidently recommended for routine use.
- **Resolution test** Provide quantitative measures of reproducibility, such as scatter plots of mutation frequencies between replicates, correlation coefficients, and a description of how many replicates were performed and how outliers were handled. Include a discussion of potential sources of variability and how they are controlled.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 3D-seq has high resolution, with the ability to identify binding sites within a 200 bp region.
- **Evidence pointer** Figure 2c-d, location not provided
- **Concern** The resolution of 3D-seq is stated to be limited by the frequency of 5'-TC-3' motifs, which occur on average every 12 bp in P. aeruginosa. However, the manuscript does not provide a systematic analysis of the resolution achieved in practice. The peak shown in Figure 2c-d appears to span a 200 bp region, which is comparable to the resolution of ChIP-seq. The authors do not demonstrate that 3D-seq can achieve higher resolution than existing methods, nor do they discuss how the distribution of 5'-TC-3' motifs within a binding region affects the precision of peak calling.
- **Why it matters** The resolution of a DPI mapping method determines its ability to distinguish closely spaced binding sites and to precisely localize the binding motif. If 3D-seq does not offer improved resolution over existing methods, this weakens the case for its adoption.
- **Resolution test** Provide a detailed analysis of the spatial distribution of mutations around known binding sites, including the distance between the peak center and the known binding motif. Compare the resolution of 3D-seq to ChIP-seq for the same transcription factor. Discuss how the local density of 5'-TC-3' motifs affects resolution.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, statistical analysis
- **Evidence pointer** Methods, "Statistical analysis" section, location not provided
- **Issue** The methods section is incomplete, with the statistical analysis description ending mid-sentence. This is a significant omission that prevents full evaluation of the methodology.
- **Required correction** Complete the methods section with a full description of the statistical analysis, including the model, parameters, and implementation details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figures 1-3
- **Evidence pointer** Figures 1-3, location not provided
- **Issue** The figures are referenced but not visible in the provided manuscript. It is impossible to assess the quality of the data presentation, the clarity of the peaks, or the appropriateness of the visualization.
- **Required correction** Ensure that all figures are included in the manuscript and that they clearly show the data, including genome browser views, peak distributions, and statistical significance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary tables
- **Evidence pointer** Tables S1-S6, location not provided
- **Issue** The supplementary tables are referenced but not provided. These tables contain critical data, including peak lists, statistical values, strain lists, and primer sequences.
- **Required correction** Include all supplementary tables in the manuscript submission and ensure they are complete and well-formatted.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** DddA activity modulation
- **Evidence pointer** Main text, "To capture a snapshot..." section, location not provided
- **Concern** The manuscript describes modulating DddA activity via its natural inhibitor protein, DddA I, but does not provide details on the kinetics of DddA inhibition or the time window over which mutations accumulate. This is important for understanding the temporal resolution of the method.
- **Required correction** Provide data on the time course of mutation accumulation and the effectiveness of DddA I in stopping further mutations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion of eukaryotic applications
- **Evidence pointer** Main text, final paragraph, location not provided
- **Issue** The authors suggest that 3D-seq could be applied to organisms with larger genomes but do not discuss the potential challenges, such as the need for higher sequencing depth, the presence of endogenous 5'-TC-3' methylation, or the delivery of DddA fusions into eukaryotic cells.
- **Required correction** Add a discussion of the potential challenges and limitations of applying 3D-seq to eukaryotic systems.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and discussion
- **Evidence pointer** Main text, introduction, location not provided
- **Issue** The introduction mentions ChIP-seq and DamID but does not discuss other emerging methods for in vivo DPI mapping, such as CUT&Tag or targeted cleavage-based approaches. A more comprehensive comparison would strengthen the novelty claims.
- **Required correction** Expand the introduction and discussion to include a more thorough comparison with other recent DPI mapping technologies.

## Risk / unsupported claims
1. The claim that 3D-seq can achieve single-cell resolution is unsupported by any experimental evidence in the manuscript.
2. The claim that 3D-seq is "the first method for high-resolution genome-wide recording of DPIs in living cells" is not fully substantiated, as the manuscript does not provide a comprehensive review of all existing methods.
3. The claim that 3D-seq can capture DPI dynamics under different regulatory states is only weakly supported by the GacA data, which lacks independent validation.
4. The claim that 3D-seq offers advantages over ChIP-seq in terms of ease of implementation is supported only by anecdotal comparison, not by a systematic quantitative assessment.
5. The generalizability of 3D-seq to organisms with larger genomes is speculative and not supported by data.
6. The statement that "the lower limit on material for a 3D-seq study is defined only by the terminal DNA sequencing technology" is not experimentally demonstrated.
7. The manuscript does not provide a full description of the statistical model, making the significance of the identified peaks unassessable.
8. The comparison between 3D-seq and ChIP-seq for GcsA is presented only in supplementary tables, and the manuscript does not provide a detailed discussion of the concordance or discordance between the two methods.