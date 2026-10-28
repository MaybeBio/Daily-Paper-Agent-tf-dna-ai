## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplemental figure descriptions
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present the first DAP-seq profiles of three GRAS family transcription factors (SHR, SCL23, SCL3) from Sorghum bicolor applied to sorghum, maize, and rice genomic DNA. They report genome-wide binding peaks, identify putative novel DNA-binding motifs, integrate transcriptomic and chromatin accessibility data to nominate root-specific regulatory targets, and propose that GRAS TFs can bind DNA without heterodimerization partners.
- **Visible evidence base** Results sections describing peak counts, overlap statistics, motif enrichment analyses, PWM projection frequencies, and integration with H3K4me3 data. Methods sections describing DAP-seq pulldown, sequencing, bioinformatic analysis, and motif frequency projection. Supplemental figure and table references.
- **Missing materials affecting confidence** All supplemental figures and tables, including peak lists, motif logos, PWM projection data, and gene lists. No quantitative statistical values for overlap comparisons. No genome browser images. No raw data quality metrics beyond read counts. No validation experiments for novel motifs.

## Reviewer
- **Overall assessment** This manuscript provides a useful descriptive resource for GRAS family TF binding in three grass species. The DAP-seq approach is appropriate and the integration with public epigenomic and transcriptomic data is a strength. However, the central claims regarding novel motif discovery and functional significance rest on bioinformatic inference without experimental validation. The cross-species comparisons are confounded by the use of sorghum proteins on heterologous genomes, and the interpretation of reduced peak numbers in maize and rice is underdeveloped. The manuscript would benefit from clearer quantitative reporting, validation of at least one novel motif, and a more rigorous treatment of the limitations of the PWM projection approach.
- **Who would be interested in the results, and why** Researchers studying GRAS transcription factor biology, grass genome regulation, root development, and nutrient stress responses. The resource value of DAP-seq profiles in sorghum will interest plant genomics groups working on cereal crops. Those using comparative genomics to understand cis-regulatory evolution may also find the cross-species binding data useful despite its limitations.
- **Major strengths** First DAP-seq dataset for GRAS TFs in sorghum. Multi-species comparative design using sorghum proteins on maize and rice DNA. Integration of H3K4me3 and expression data to filter candidate regulatory targets. Identification of specific candidate genes for root-related traits with potential breeding applications.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the novel motifs identified in SHR and SCL23 peaks are "likely real" GRAS family recognition sites based on their frequency profiles across promoter regions.
- **Evidence pointer** Results section "Discovery of Novel DNA-binding Motifs in GRAS Family Transcription Factors", Figure 3
- **Concern** The claim that uncharacterized motifs are genuine TF binding sites rests entirely on a computational frequency distribution argument. The authors note that DAP-seq is noisy, yet provide no experimental validation such as EMSA, reporter assays, or orthogonal binding data. The frequency profile argument is circumstantial and could be produced by other sequence features such as GC content or nucleosome positioning biases. The authors themselves list four alternative explanations for the observed frequency patterns, which undermines the confidence of the claim.
- **Why it matters** The identification of novel motifs is a central contribution of the paper. If these motifs are not validated, the downstream PWM projections and candidate gene lists built upon them lose their foundation. The paper currently does not establish that these motifs are recognized by GRAS TFs.
- **Resolution test** Provide at least one experimental validation of a novel motif, such as electrophoretic mobility shift assay with the recombinant TF protein, or a reporter assay in a heterologous system. Alternatively, demonstrate that the motif occurs in a functionally relevant context such as a validated enhancer element.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors interpret the reduced number of peaks in maize and rice compared to sorghum as evidence of regulatory rewiring and sequence divergence.
- **Evidence pointer** Results section "Sorghum GRAS Transcription Factor Binding in Maize and Oryza", Figure 2
- **Concern** The cross-species DAP-seq uses sorghum TF proteins on maize and rice genomic DNA. Reduced binding could reflect genuine regulatory divergence, but it could also result from technical factors including suboptimal protein folding, post-translational modification differences, or reduced affinity for divergent DNA sequences that are nonetheless functional in vivo. The authors do not control for these possibilities. The sequence identity ranges provided (59-97 percent) are broad and not linked to the observed peak numbers in a quantitative way.
- **Why it matters** The comparative conclusions about binding conservation and divergence across species are a stated aim of the study. Without addressing technical confounds, the interpretation of fewer peaks in maize and rice as evidence of regulatory rewiring is not established.
- **Resolution test** Include a control experiment such as DAP-seq with the orthologous maize or rice TF proteins on their cognate genomes, or demonstrate that the sorghum proteins bind known positive control sequences in maize and rice with expected affinity. Alternatively, present a quantitative model linking sequence identity to peak numbers.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report that 77 of 257 overlapping peaks showed statistically significant differential expression in root tissues under limiting phosphorus conditions.
- **Evidence pointer** Results section "Shared Peaks Highlight Tissue-specific Gene Expression", Figure 4
- **Concern** The statistical methods for differential expression analysis are not described. The authors reference data from a prior publication but do not state what test was used, how multiple testing was controlled, what the significance threshold was, or what the effect sizes were. The statement that "the majority of this significant differential gene expression occurred in the lateral root region" is vague without quantitative support.
- **Why it matters** The integration of expression data is used to support the biological relevance of the identified binding peaks. Without clear statistical reporting, the strength of this support cannot be evaluated.
- **Resolution test** Provide the statistical details for the differential expression analysis, including the test used, multiple testing correction method, significance thresholds, and effect size distributions. Present the number of genes per root region with direction of change.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that the presence of H3K4me3 marks at shared peak regions indicates active gene expression and supports the identification of tissue-specific regulatory targets.
- **Evidence pointer** Results section "Shared Peaks Highlight Tissue-specific Gene Expression", Figure 4
- **Concern** H3K4me3 is associated with active promoters, but its presence alone does not establish that the GRAS TFs are functionally regulating the associated genes. The authors do not test whether the H3K4me3 marks are dependent on GRAS TF activity, nor do they assess whether the marked regions are actually accessible in the relevant cell types. The claim that these are "tissue-specific regulatory targets" is stronger than the evidence supports.
- **Why it matters** The paper proposes candidate genes for breeding and genome editing. Overinterpretation of correlative epigenomic data could misdirect follow-up studies.
- **Resolution test** Provide additional evidence such as ATAC-seq data from the same root regions showing accessibility, or expression data from grAS mutant lines showing altered expression of the target genes.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors claim that the GRAS TFs bind to 3' UTR regions across hundreds of genes, and that this binding may have regulatory significance.
- **Evidence pointer** Results section "SCL23 Occupancy Around 3'UTR regions"
- **Concern** The 3' UTR binding observation is presented as a distinct finding, but the analysis is superficial. The authors do not report how many genes have 3' UTR peaks for each TF, whether the binding is enriched relative to genomic background, what motifs are present in these regions, or what the functional consequences might be. The manual curation of a few examples does not constitute a systematic analysis.
- **Why it matters** 3' UTR binding by TFs is an unusual finding that could have implications for post-transcriptional regulation. If this is to be a claim of the paper, it needs proper quantitative treatment.
- **Resolution test** Provide a systematic analysis of 3' UTR peaks including enrichment statistics, motif analysis, and comparison to appropriate genomic background. If the finding is preliminary, state it as such and remove the implied significance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "crop manipulation" is vague and could encompass genetic modification approaches that are not the focus of this study.
- **Required correction** Replace with a more specific term such as "crop improvement through targeted trait modification."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 2
- **Issue** The manuscript states "Oryza" in the title but uses "Oryza sativa japonica" in the abstract and "oryza" throughout the text. The inconsistent naming could confuse readers.
- **Required correction** Use the full species name "Oryza sativa" at first mention and define the abbreviation "rice" for subsequent use.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Methods
- **Evidence pointer** Methods section "DAP-seq Bioinformatic Analysis"
- **Issue** The methods state that "default values for intergenic space was defined was used" which is grammatically incorrect and unclear. The definition of intergenic space is important for interpreting peak annotations.
- **Required correction** Rewrite as "Intergenic space was defined using the default parameters of the ChipSeeker package, which classifies regions greater than 10 kb upstream or greater than 300 bp downstream of gene elements as intergenic."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section "DAP-seq Bioinformatic Analysis"
- **Issue** The gene ontology analysis is described as using "only the Fisher's Exact statistical test... without any correction." This is statistically problematic for large gene sets.
- **Required correction** State the rationale for not applying multiple testing correction, or apply a correction such as Benjamini-Hochberg and report adjusted p-values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Results section "GRAS Family Transcription Factor Selection and Expression"
- **Issue** The statement that proteins were selected "based on their ability to be stably expressed and remain soluble" is presented without data. It is unclear whether this was a systematic screen or a trial-and-error process.
- **Required correction** Briefly describe the expression testing process or reference a supplemental figure showing expression and solubility data.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion of reduced cross-species binding presents two hypotheses but does not acknowledge that both could be partially correct or that the result could be an artifact of the assay.
- **Required correction** Add a sentence acknowledging that the reduced binding could also reflect technical limitations of using sorghum proteins on heterologous DNA.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Results
- **Evidence pointer** Results section "Sorghum GRAS Transcription Factor Binding in Maize and Oryza"
- **Issue** The number of shared orthologs with peaks is reported as specific integers (76, 17, 15, 9, 22, 6) but the total number of orthologous gene pairs considered is not stated. This makes the proportions impossible to evaluate.
- **Required correction** Report the total number of orthologous gene pairs analyzed for each comparison.

- **Technical failings that need to be addressed before the case is established** The absence of experimental validation for the novel motifs is the most significant technical gap. The lack of statistical detail for the differential expression analysis and the unaddressed technical confounds in the cross-species comparisons also need resolution. The manuscript does not provide quality metrics for the DAP-seq data such as FRiP scores, peak reproducibility across replicates, or signal-to-noise ratios, which are standard for this assay type.
- **Assessment against Nature-style criteria** Originality: The work is original in providing the first DAP-seq profiles for GRAS TFs in sorghum and applying them across three grass species. However, the conceptual advance beyond generating new data is limited. Scientific importance: The resource value for the grass genomics community is real, but the functional insights are largely correlative and the novel motif claims are unvalidated. Interdisciplinary readership: The work will primarily interest plant molecular biologists and crop geneticists. The broader cell biology or gene regulation community is unlikely to find the findings sufficiently mechanistically deep. Technical soundness: The DAP-seq methodology is sound, but the bioinformatic inference of novel motifs and the cross-species comparisons have unresolved technical issues. Readability for nonspecialists: The manuscript is generally readable, but the results section assumes familiarity with DAP-seq and motif analysis terminology without sufficient explanation for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The descriptive resource is valuable, but the central claims about novel motif discovery and functional significance require experimental validation and more rigorous quantitative reporting. The manuscript could become suitable for publication after substantial revision and additional experiments.

## Risk / unsupported claims
- The claim that novel motifs are "likely real" GRAS recognition sites is unsupported without experimental validation.
- The interpretation of reduced cross-species peak numbers as evidence of regulatory rewiring is not established due to unaddressed technical confounds.
- The claim that H3K4me3 marks at shared peak regions indicate tissue-specific regulatory targets is correlative and not causally supported.
- The statement that GRAS TFs have "innate DNA-binding activity without interacting with other protein cofactors" is not directly tested in this study, as DAP-seq uses recombinant protein in vitro and does not exclude the possibility that in vivo binding requires cofactors.
- The assertion that the PWM projection approach "improves the validation of new binding sites" is not supported by any benchmark or comparison to experimentally validated sites.
- The claim that specific genes are "strong candidates for EMS mutagenesis or CRISPR genome editing" is speculative without functional validation.