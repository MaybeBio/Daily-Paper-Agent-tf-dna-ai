## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific validity, technical soundness, logical coherence, and support of claims by the presented evidence. No assessment of editorial fit or language polish beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors propose that integrating chromatin conformation data (DLO Hi-C) with epigenomic marks (ATAC-seq, H3K27ac ChIP-seq) and gene expression (RNA-seq) from a human oral epithelial cell line can identify sub-threshold GWAS variants associated with non-syndromic cleft palate only (NSCPO) that are missed by conventional significance thresholds. They report 254 candidate SNPs in active enhancers/promoters interacting with 1718 promoters, and functionally validate two SNPs (rs560789, rs174570) as reducing enhancer activity via disruption of transcription factor binding, with a putative target gene (FADS1) implicated in epithelial cell migration and proliferation.
- **Visible evidence base** Main text figures 1–7, supplementary figures 1–4 (as referenced), supplementary tables 1–6 (as referenced), methods descriptions for all experimental procedures.
- **Missing materials affecting confidence** Raw sequencing data files, processed data matrices, complete supplementary tables (only referenced, not provided in the submitted text), detailed gapped k-mer SVM parameters and training/testing splits, statistical analysis code, and full lists of the 254 SNPs and 1718 target genes. The manuscript states supplementary materials are available online, but they are not included in the provided scope.

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable resource and a systematic framework for prioritizing sub-threshold GWAS variants in orofacial clefts using oral epithelial cell-specific functional genomics. The integration of multiple epigenomic modalities is conceptually sound and the functional validation of two SNPs is a strength. However, several technical and analytical concerns undermine the robustness of the central claims. The statistical framework for selecting sub-threshold variants is not rigorously justified, the comparison with other Hi-C datasets is incomplete, and the functional validation, while suggestive, does not fully establish causality for the cleft phenotype. The claim that this approach can "identify missing functional variants" is overstated given the limited validation and the lack of a clear demonstration that these variants would be missed by other approaches.
- **Who would be interested in the results, and why** Researchers in craniofacial development, orofacial cleft genetics, and functional genomics of non-coding variants. The chromatin conformation dataset of oral epithelial cells is a novel resource that could be reused by the community. The analytical framework for integrating GWAS with cell-type-specific epigenomics may also interest those studying other complex diseases where sub-threshold variants are suspected to contribute to heritability.
- **Major strengths** 1) The generation of a new DLO Hi-C dataset from a relevant cell type (oral epithelium) fills a gap in available chromatin conformation resources for craniofacial research. 2) The multi-layered integration of chromatin accessibility, histone modification, and 3D conformation to prioritize variants is a logical and potentially powerful approach. 3) The functional validation using both in vivo zebrafish reporter assays and in vitro luciferase assays, along with ChIP-qPCR for SOX2, provides direct evidence for the regulatory impact of the tested SNPs. 4) The identification of FADS1 as a potential target gene with effects on cell migration and proliferation offers a plausible biological link to palatogenesis.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and variant prioritization
  - **Claim pointer** The authors claim that dropping the GWAS significance threshold to P < 10^-3 and applying their functional filter can identify "missing functional variants" for NSCPO.
  - **Evidence pointer** Results section "3 664 NSCPO-related SNPs with sub-threshold were identified as candidate variants"; Figure 1a
  - **Concern** The choice of P < 10^-3 as the sub-threshold is arbitrary and not statistically justified. With ~3664 SNPs at this threshold, the expected number of false positives is substantial. The authors do not provide any estimate of the false discovery rate (FDR) or demonstrate that their functional filtering (enhancer/promoter location, chromatin interaction) reduces the false positive rate beyond what would be expected by chance. The comparison with random SNPs in Figure 1f is underpowered and does not address the enrichment of functional variants specifically.
  - **Why it matters** The central premise of the paper is that these sub-threshold variants are biologically meaningful. Without a statistical framework to control for the high prior probability of false positives, the 254 prioritized SNPs may largely represent noise, undermining the validity of the entire pipeline.
  - **Resolution test** The authors should provide an FDR estimate for the 254 prioritized SNPs, perhaps by permuting case-control labels or by applying the same functional filter to a set of matched null SNPs. They should also demonstrate that the enrichment of their prioritized SNPs in relevant functional categories is significantly greater than expected by chance, using a proper background model.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation and causal inference
  - **Claim pointer** The authors state that the risk alleles of rs560789 and rs174570 "reduced the epithelial-specific enhancer activity by preventing the binding of transcription factors related to epithelial development" and that FADS1 is a potential risk gene for cleft palate.
  - **Evidence pointer** Results sections "Risk allele of rs560789 and rs174570 reduced the activity of epithelial-specific enhancer and prevented the binding of transcription factors related to epithelial development" and "A potential target gene of rs560789 and rs174570 affected cell migration and proliferation"; Figures 5, 6, 7
  - **Concern** The functional validation is limited to two SNPs out of 254 prioritized. While the assays are appropriate, the link to the cleft phenotype is indirect. The knockdown of FADS1 in an immortalized cell line shows effects on migration and proliferation, but this does not demonstrate a role in palatogenesis in vivo. The authors acknowledge that FADS1 knockout mice do not show clefting, which significantly weakens the claim that FADS1 is a risk gene. The ChIP-qPCR for SOX2 shows binding, but the functional consequence of reduced SOX2 binding on downstream gene expression in a relevant developmental context is not shown.
  - **Why it matters** The paper's title and abstract imply that the pipeline can identify variants that cause orofacial clefts. The evidence presented only shows that two variants can alter enhancer activity in vitro and in zebrafish, and that one putative target gene affects cell behavior in culture. This is a long way from establishing a causal role in human clefting.
  - **Resolution test** The authors should either temper their claims to reflect the preliminary nature of the functional validation, or provide additional evidence linking the prioritized variants and target genes to clefting, such as demonstrating altered expression of FADS1 or SOX2 targets in cleft patient tissues, or showing that the risk allele is associated with differential gene expression in a relevant cell type.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparative analysis and dataset utility
  - **Claim pointer** The authors claim that HIOEC DLO Hi-C data were "able to more effectively identify NSCPO-related SNPs and AEs of oral epithelial cells" compared to Hi-C data from other cell types.
  - **Evidence pointer** Results section "HIOEC DLO Hi-C data were able to identify NSCPO-related SNPs and AEs of oral epithelial cells"; Figure 4b
  - **Concern** The comparison with hESC and IMR90 Hi-C data is not a fair or comprehensive test of cell-type specificity. These are very different cell types, and the comparison is made at a single resolution. The authors do not compare with other relevant craniofacial or epithelial cell types. The metric used (ability to capture SNPs/AEs per interaction) is not clearly defined and may be biased by the number of interactions or the genomic coverage of each dataset.
  - **Why it matters** A key selling point of the paper is the cell-type specificity of the chromatin conformation data. If the advantage over other datasets is marginal or not robust, the claim of a unique resource is weakened.
  - **Resolution test** The authors should compare their data with a broader panel of cell types, including other epithelial cells and craniofacial-relevant cell types. They should also use a more standard and well-defined metric for comparing the relevance of chromatin interactions, such as the enrichment of prioritized variants in interacting regions relative to a genomic background.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and reproducibility
  - **Affected element** Methods, machine learning section
  - **Evidence pointer** Materials and methods, "Machine learning"
  - **Issue** The description of the gapped k-mer SVM is brief. The parameters (k = 6, L = 10) are given, but the training procedure, the number of positive and negative examples, and the cross-validation strategy are not fully described. The statement "we generated scoring vector using two training sets" is ambiguous about how the final score for a SNP is derived.
  - **Required correction** Provide a more detailed description of the SVM training, including the exact number of positive and negative sequences, the source of negative sequences, and how the deltaSVM score is calculated for a given SNP. This is essential for reproducibility.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 4b
  - **Evidence pointer** Results section, Figure 4b
  - **Issue** The y-axis label "relative ability" is vague. It is unclear what the absolute values represent and how the normalization was performed.
  - **Required correction** Clarify the y-axis label and describe the normalization procedure in the figure legend or methods.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure 1f
  - **Evidence pointer** Results section, Figure 1f
  - **Issue** The Kolmogorov-Smirnov test is used to compare expression levels of 34 genes with SNPs in coding regions versus 34 random genes. The selection of the random genes is not described, and the power of this comparison is limited by the small sample size.
  - **Required correction** Describe how the random genes were selected and consider using a more robust statistical comparison or a larger set of control genes.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, FADS1
  - **Evidence pointer** Discussion section
  - **Issue** The authors discuss FADS1 as a potential target but note that FADS1 knockout mice do not show clefting. This contradiction is acknowledged but not resolved. The discussion would benefit from a more nuanced interpretation of what the FADS1 result means in the context of the proposed pipeline.
  - **Required correction** Add a sentence or two discussing the implications of the mouse knockout data for the interpretation of FADS1 as a cleft risk gene, and whether this suggests the pipeline may identify genes with redundant or non-essential functions.

## Risk / unsupported claims
- The claim that the pipeline can "identify orofacial cleft missing functional variants" is not fully supported. The pipeline identifies candidate variants, but only two are functionally tested, and the link to clefting is indirect.
- The claim that HIOEC DLO Hi-C is superior to other Hi-C datasets for identifying NSCPO-related SNPs is based on a limited and potentially biased comparison.
- The statement that the prioritized SNPs "exert a higher risk of NSCPO" is not supported by any direct genetic association data; the SNPs were selected based on sub-threshold P-values, and no replication or fine-mapping is presented.
- The functional significance of the 254 prioritized SNPs as a group is not assessed. It is unclear if they are enriched for known regulatory variants or eQTLs.
- The relevance of the HIOEC cell line to the in vivo palatal epithelium, particularly at different developmental stages, is not discussed in detail. The authors note the limitation of cell lines but do not provide evidence that HIOEC recapitulates the relevant chromatin state of embryonic palatal epithelium.

## Assessment against Nature-style criteria
- **Originality** Moderate. The combination of DLO Hi-C with other epigenomic marks in a disease-relevant cell type is a useful contribution, but the overall concept of integrating GWAS with functional genomics is not new. The specific application to oral epithelium and the focus on sub-threshold variants provides some novelty.
- **Scientific importance** Moderate. If the pipeline is robust, it could help uncover missing heritability in orofacial clefts and provide a template for other diseases. However, the current evidence is insufficient to demonstrate that the approach yields biologically meaningful results beyond what is already known.
- **Interdisciplinary readership** Limited. The work is primarily of interest to craniofacial biologists and those working on functional interpretation of GWAS. The methods are specialized and may not appeal to a broad interdisciplinary audience.
- **Technical soundness** The generation of the DLO Hi-C dataset appears technically sound, and the integration of datasets is logical. However, the statistical framework for variant prioritization is weak, and the comparative analysis is incomplete. The functional assays are well-executed but limited in scope.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is easy to follow. However, the methods section is dense and assumes familiarity with multiple genomics techniques. The abstract is clear but overstates the conclusions relative to the evidence.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a potentially useful resource and a reasonable framework, but the central claims are not sufficiently supported by the statistical and functional evidence presented. The authors should address the major concerns, particularly the statistical rigor of the variant prioritization and the strength of the causal claims, before the work can be considered for publication in a high-impact venue.