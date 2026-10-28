## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality; not copyediting or formatting
- **Shared manuscript claim summary** The authors generated matched single-cell RNA-seq and ATAC-seq atlases of human scalp from healthy controls and alopecia areata patients, integrated these data across multiple cellular resolutions to infer enhancer-gene links, identified highly regulated genes and cell-type-specific regulatory programs, and used these maps to prioritize cell types, genes, and candidate causal variants for hair and skin diseases including androgenetic alopecia, eczema, and hair color.
- **Visible evidence base** Main figures 1–6, extended data figures 1–10, supplementary tables referenced (Table S1, S29), methods section, and data availability statement
- **Missing materials affecting confidence** Raw sequencing data not inspected; supplementary tables not provided in full; detailed quality control metrics for each sample not shown; exact parameters for some analyses (e.g., chromVAR background peaks, Milo k values) not fully specified; no validation experiments for predicted enhancer-gene links or SNP effects

## Reviewer

### Overall assessment
This manuscript presents a substantial and well-executed resource: paired single-cell chromatin and transcriptomic atlases of human scalp, with careful integration across multiple cellular resolutions. The methodological advance of performing peak-to-gene linkage analysis on subclustered populations to recover more links than prior approaches is credible and likely useful to the field. The disease-focused analyses, particularly the enrichment of androgenetic alopecia heritability in dermal papilla open chromatin and the nomination of candidate functional SNPs, are of interest. However, several claims are stronger than the evidence supports, particularly regarding the predictive power of aggregate enhancer accessibility for gene expression and the functional interpretation of prioritized SNPs. The manuscript would be strengthened by additional validation, clearer presentation of limitations, and more rigorous statistical treatment of some enrichment analyses.

### Who would be interested in the results, and why
Researchers studying gene regulation in skin and hair follicles, those interested in single-cell multi-omic integration methods, and investigators working on the genetics of complex traits in skin and hair diseases. The resource itself (the atlases and the interactive browser) will be of broad utility. The methodological approach of hierarchical linkage analysis may be adopted by others working with similar multi-omic datasets in other tissues.

### Major Strengths
1. The generation of matched scRNA-seq and scATAC-seq data from the same tissue, with careful quality control and annotation, is a valuable resource.
2. The hierarchical approach to peak-to-gene linkage analysis, performed on both full and subclustered datasets, is a thoughtful methodological contribution that demonstrably increases the number of links recovered.
3. The integration of GWAS data with cell-type-specific open chromatin to nominate disease-relevant cell types is well executed and yields biologically plausible results, particularly for AGA and dermal papilla cells.
4. The machine learning approach to prioritize functional SNPs, with validation against known eQTLs, adds a useful layer of analysis.
5. The manuscript is generally clearly written and the figures are informative.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The authors state that "the aggregate accessibility at linked enhancers for highly-regulated genes predicts expression" and that this supports an additive model of enhancer activity.
- **Evidence pointer** Results section "Highly regulated genes use distinct enhancer modules to tune gene expression", Figure 2F–I, Extended Data Fig. 5F
- **Concern** The correlation between aggregate accessibility and expression is presented as evidence for an additive model, but the analysis appears to be purely correlational and may be confounded by the fact that both accessibility and expression are measured in the same cell types. The authors do not demonstrate that the relationship is causal or that it outperforms simpler models (e.g., accessibility at the promoter alone). The claim of "additive" enhancer activity is a strong mechanistic interpretation that is not directly tested.
- **Why it matters** If the claim is overstated, it could mislead readers into thinking the model is more established than it is. The additive model has implications for how enhancer mutations are interpreted, so it is important to be precise about the strength of evidence.
- **Resolution test** The authors should either temper the language to "correlated with" rather than "predicts," or provide additional analyses, such as comparing the predictive power of aggregate accessibility to promoter accessibility alone, or testing whether the relationship holds in a held-out set of cell types.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report "47, 19, and 19 prioritized SNPs for AGA, eczema, and hair color respectively" based on their gkm-SVM and GkmExplain pipeline.
- **Evidence pointer** Results section "Machine learning models prioritize potential functional noncoding SNPs for skin and hair phenotypes", Methods section "Estimation of candidate SNP effectsizes using gkm-SVM models"
- **Concern** The multiple testing burden is not addressed. With thousands of SNPs tested across many cell types, the expected number of false positives is high. The authors use a delta score p-value < 0.05 and prominence p-value < 0.05, but it is unclear whether these are corrected for multiple comparisons. Additionally, the choice of a random set of 2,500 SNPs as background is not well justified; a more appropriate null might be matched for minor allele frequency and LD.
- **Why it matters** If the prioritized SNP lists contain many false positives, the downstream interpretation of specific SNPs (e.g., rs2058622, rs72966077) as causal is weakened. The field is moving toward more rigorous statistical thresholds for fine-mapping and functional prioritization.
- **Resolution test** The authors should apply a multiple testing correction (e.g., Benjamini-Hochberg) across all SNP-cell type pairs and report how many SNPs survive. They should also consider using a more matched background set and report the sensitivity of their results to this choice.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that "GWAS signals associated with AGA were strongly and specifically enriched in dermal papilla open chromatin regions, and linked to target genes enriched for roles in WNT-signaling."
- **Evidence pointer** Results section "Cell type–specific open chromatin regions in scalp are enriched for skin and hair GWAS traits", Figure 5A
- **Concern** The LD score regression analysis identifies enrichment of heritability in dermal papilla peaks, but the link to WNT signaling is based on the target genes of linked peaks. The authors do not demonstrate that the WNT pathway genes are specifically driving the enrichment signal, nor do they account for the possibility that the enrichment is driven by a small number of loci with large effects. The claim of "strongly and specifically enriched" should be supported by a formal test comparing the enrichment in dermal papilla to other fibroblast subtypes.
- **Why it matters** The interpretation that dermal papilla cells are the key drivers of AGA pathogenesis is a central conclusion of the paper. If the evidence is not robust, the conclusion is weakened.
- **Resolution test** The authors should perform a formal test of whether the enrichment in dermal papilla is significantly greater than in other fibroblast subtypes, and should examine whether the WNT pathway enrichment is robust to excluding the most significant loci.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "we infer 50–100% more enhancer-gene links than prior approaches."
- **Evidence pointer** Results section "A paired transcriptomic and epigenetic atlas reveals cellular diversity of human scalp", Figure 2A, Extended Data Fig. 5A
- **Concern** The comparison to "prior approaches" is not clearly defined. It is unclear which specific prior studies or methods are being compared against, and whether the comparison is apples-to-apples (e.g., same number of cells, same peak-to-gene correlation threshold, same genomic window). The claim of 50–100% more links is central to the methodological contribution, but the basis for this comparison is not transparent.
- **Why it matters** If the comparison is not well-defined, the claim is difficult to evaluate and could be misleading. The field needs clear benchmarks to assess methodological improvements.
- **Resolution test** The authors should specify exactly which prior methods and datasets they are comparing against, and should provide a table showing the number of links recovered by each method under matched conditions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "identify gene-regulatory programs and critical cell types for hair and skin diseases" is vague. The abstract would benefit from specifying which diseases and which cell types.
- **Required correction** Revise to mention androgenetic alopecia, eczema, and hair color, and to name dermal papilla cells and specific immune cell types.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Single Cell Dissociation" section
- **Evidence pointer** Methods section "Single Cell Dissociation and Fluorescent Activated Cell Sorting (FACS)"
- **Issue** The dissociation protocol uses a 3-hour incubation at 37°C, which may introduce transcriptional and chromatin artifacts. The authors do not discuss this potential limitation.
- **Required correction** Add a sentence acknowledging the potential for dissociation-induced artifacts and cite relevant literature.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Milo analysis
- **Evidence pointer** Results section "Preservation of HFSCs and depletion of bulbar HF keratinocytes in alopecia areata", Figure 4E
- **Issue** The Milo analysis is described as confirming depletion of inferior segment sheath populations, but the effect sizes and confidence intervals are not reported.
- **Required correction** Report the log2 fold change and confidence intervals for the differentially abundant neighborhoods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, WNT signaling
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion of WNT signaling in AGA is somewhat speculative and does not fully acknowledge the complexity of WNT pathway regulation, including the role of inhibitors and the potential for context-dependent effects.
- **Required correction** Add a sentence acknowledging the complexity and noting that the data support a hypothesis rather than a definitive mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, gkm-SVM training
- **Evidence pointer** Methods section "gkm-SVM machine learning classifier training and testing"
- **Issue** The exact number of training and test sequences per cluster is not stated, and the hyperparameter selection procedure is not described.
- **Required correction** Provide the number of sequences used for training and testing, and describe how hyperparameters were chosen.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 5
- **Evidence pointer** Figure 5A
- **Issue** The heatmap of heritability enrichment is difficult to read because the color scale is not intuitive and the cell type labels are small.
- **Required correction** Consider using a different visualization, such as a forest plot with confidence intervals, and increase font size for cell type labels.

### Technical failings that need to be addressed before the case is established
- R1-M1: The claim that aggregate accessibility "predicts" expression is not sufficiently supported; the analysis is correlational and may be confounded.
- R1-M2: The multiple testing burden in the SNP prioritization is not addressed; the reported lists may contain many false positives.
- R1-M4: The comparison to "prior approaches" for the number of enhancer-gene links is not well-defined, making the central methodological claim difficult to evaluate.

### Assessment against Nature-style criteria
- **Originality** The work is original in its application of hierarchical peak-to-gene linkage analysis to a multi-omic skin dataset, and in the integration of these maps with GWAS data. The concept of analyzing multiple cellular resolutions is not entirely new, but its systematic application here is a contribution.
- **Scientific importance** The resource itself is valuable, and the disease-focused analyses provide testable hypotheses for AGA and eczema. The finding that dermal papilla cells are the primary cell type for AGA heritability is consistent with prior knowledge and adds confidence to the approach. However, the lack of experimental validation limits the immediate impact.
- **Interdisciplinary readership** The work will appeal to skin biologists, computational biologists, and geneticists. The methods are described in sufficient detail for specialists, but the broader significance is made accessible through the disease-focused framing.
- **Technical soundness** The computational methods are largely sound, but the statistical rigor of the SNP prioritization and the interpretation of the aggregate accessibility analysis need strengthening. The quality control and integration of the single-cell data appear careful.
- **Readability for nonspecialists** The manuscript is generally well-written, but the results section is dense and would benefit from more signposting of the main takeaways. The abstract is accessible, but the main text assumes familiarity with single-cell and GWAS methods.

### Recommendation posture
Supportive if technical concerns are resolved. The resource and the analytical framework are valuable, and the disease-focused results are of interest. However, the claims regarding the predictive power of aggregate accessibility and the prioritized SNP lists need to be tempered or supported by additional analysis. The comparison to prior methods should be made explicit. If these issues are addressed, the manuscript would be a strong contribution to the field.