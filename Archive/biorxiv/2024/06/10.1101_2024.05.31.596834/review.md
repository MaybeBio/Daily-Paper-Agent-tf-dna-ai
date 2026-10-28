## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no supplementary figures or tables were available for direct inspection
- **Shared manuscript claim summary** The authors present a large-scale DAP-seq dataset mapping transcription factor binding sites for 200 maize TFs in two inbred lines (B73 and Mo17), identify widespread binding site divergence driven largely by structural variation, associate this variation with gene expression differences, and demonstrate that CRISPR-based editing of TF binding sites can alter gene expression and phenotype, including at the vgt1 and DICE loci.
- **Visible evidence base** Main text figures referenced (Figures 1-5), supplementary figures and tables referenced but not provided, methods section
- **Missing materials affecting confidence** Supplementary figures and tables (including all motif analyses, GO enrichments, peak counts, and CRISPR validation data), actual figure images, detailed statistical outputs, and raw data accessibility

## Reviewer
- **Overall assessment** This manuscript presents a valuable and technically impressive resource: a large-scale empirical map of TF binding sites in two maize inbred lines. The comparative approach between B73 and Mo17, combined with orthogonal functional data integration and functional validation via CRISPR editing, represents a significant advance in plant regulatory genomics. The identification of a mechanistic explanation for the vgt1 flowering time QTL through MADS69 binding disruption is particularly compelling. However, several technical concerns regarding data processing, statistical rigor, and the strength of causal claims need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Plant geneticists and breeders interested in regulatory variation and its phenotypic consequences; maize geneticists specifically; researchers studying TF binding evolution and cis-regulatory divergence; those working on functional annotation of crop genomes and QTL dissection. The resource value of the dataset itself will attract broad interest in the plant genomics community.

- **Major strengths** 1) Large-scale empirical TF binding data for 200 TFs in two diverse maize inbreds, representing a substantial resource. 2) Integration of multiple orthogonal datasets (ATAC-seq, MOA-seq, UMRs, histone marks, conserved non-coding sequences) to validate and contextualize binding events. 3) Demonstration of biological relevance through GWAS enrichment analysis across 41 traits. 4) Functional validation via CRISPR editing at multiple loci, including the important vgt1 flowering time QTL. 5) The discovery of a novel DNA-binding motif for Q-A-R type BHLHs and the demonstration of heterodimerization effects on binding specificity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "TF binding site comparison in B73 and Mo17 inbreds reveals widespread differences, driven largely by structural variation, that correlate with gene expression changes."
- **Evidence pointer** Results section "Comparative TF binding in two diverse inbred lines", Figures 4a-4g, Supplemental Figures 10-12
- **Concern** The quantification of "widespread differences" and the attribution to structural variation requires more rigorous statistical treatment. The authors report ranges of 7-72% genotype-specific peaks across TFs, but the methodology for determining genotype-specific peaks involves a complex pipeline of downsampling, peak calling, coordinate liftoff, and threshold adjustments. The choice of top 20% peaks for comparison is arbitrary and could bias results. Furthermore, the claim that structural variation is the "largest driver" of binding differences is based on overlap analysis, but no statistical model partitioning variance among SV, SNP, and indel contributions is presented. The authors need to provide a more formal statistical framework for attributing binding divergence to specific genetic causes.
- **Why it matters** The central thesis of the manuscript is that TF binding divergence drives phenotypic variation, and that structural variation is the primary cause. Without rigorous statistical support for this attribution, the conclusion is weakened. The field has moved toward more quantitative frameworks for partitioning regulatory variation, and this manuscript should meet that standard.
- **Resolution test** Provide a formal statistical analysis partitioning the contribution of SVs, SNPs, and indels to binding divergence, with appropriate controls for linkage disequilibrium and genomic background. Alternatively, use a permutation-based approach to test whether SV overlap is significantly enriched beyond what would be expected by chance given the genomic distribution of SVs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "Modification of TF binding regions via CRISPR-Cas9 mediated editing alters target gene expression and phenotype" and specifically that deletion of TF binding sites at the DICE locus causes reduced BX1 expression.
- **Evidence pointer** Results section "Induced TF binding variation impacts gene expression and phenotype for important agronomic traits", Figure 5, Supplemental Figure 13-14
- **Concern** The CRISPR validation experiments are central to the causal claims of the manuscript, but the details provided are insufficient to assess their rigor. For the DICE locus, the authors describe a 4.1kb deletion that removes 16 TF binding sites and causes a 9-fold reduction in BX1 expression. However, this large deletion removes an entire cis-regulatory module, not individual TF binding sites, making it difficult to attribute the effect to specific TF binding events. The authors also note a genome assembly error in B73v5 near the DICE locus, which raises questions about the accuracy of the binding site annotations in this region. For the TSH1 and BIF2 edits, the phenotypic descriptions are brief and the number of independent alleles and biological replicates is not clearly stated. The authors need to provide more detailed information about the CRISPR constructs, the nature of the deletions, the number of independent events analyzed, and the statistical power of the expression and phenotype measurements.
- **Why it matters** The causal link between TF binding site variation and phenotypic outcomes is the ultimate claim of the manuscript. If the CRISPR experiments are not rigorously designed and analyzed, the causal inference is compromised. The field has been moving toward more precise editing of individual binding sites to establish causality, and the large deletions presented here may not meet that standard.
- **Resolution test** Provide detailed information on the CRISPR alleles, including the exact nature and size of deletions, the number of independent events, and the statistical analysis of expression and phenotype data. Ideally, the authors should also present data from smaller deletions that isolate individual TF binding sites to establish causality more precisely.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "TF binding site presence-absence variation helps clarify complex QTL such as vgt1, an important determinant of maize flowering time."
- **Evidence pointer** Results section "Comparative TF binding in two diverse inbred lines", Figure 4c-4d, Supplemental Figure 9a
- **Concern** The vgt1 story is presented as a key finding, but the causal link between MADS69 binding disruption and flowering time variation is not fully established. The authors show that a MITE insertion disrupts a MADS69 binding site in Mo17, but they do not demonstrate that this disruption is causally responsible for flowering time differences. The vgt1 QTL has been studied extensively, and the MITE insertion has been previously associated with flowering time variation. The authors need to more carefully integrate their findings with the existing literature and provide additional evidence that MADS69 binding at this site is functionally relevant for flowering time regulation. The observation that other TF binding sites in the region remain intact complicates the interpretation.
- **Why it matters** The vgt1 example is used as a demonstration of the utility of the dataset for clarifying complex QTL. If the causal link is not firmly established, the claim is overstated. The manuscript would be strengthened by a more nuanced discussion of what the data can and cannot say about the vgt1 mechanism.
- **Resolution test** Provide additional evidence linking MADS69 binding at the vgt1 locus to flowering time, such as expression analysis of RAP2.7 in the CRISPR-edited lines, or complementation experiments. Alternatively, temper the claim to reflect the correlative nature of the association.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "doubleDAP-seq revealed that heterodimers formed by ZmSPTs and the clade VIII Q-A-R members yielded peak numbers up to 44 times higher than those formed by Q-A-R sub-clade VIII homodimers" and that a "unique motif (CCCATnCC) was identified."
- **Evidence pointer** Results section "Impact of TF heterodimerization on DNA-binding and binding site preference", Figure 2, Supplemental Figures 5-6
- **Concern** The doubleDAP-seq experiments are technically novel and interesting, but the interpretation requires more careful consideration. The claim that Q-A-R type BHLHs bind DNA is surprising given the lack of canonical basic residues, and the authors need to provide more evidence that the observed binding is specific and not an artifact of the in vitro system. The 44-fold increase in peak numbers for heterodimers could reflect differences in protein stability, DNA accessibility, or other factors rather than true binding specificity changes. The motif analysis should include appropriate controls and statistical validation. Additionally, the functional significance of the novel CCCATnCC motif is not demonstrated.
- **Why it matters** The heterodimerization findings represent a novel contribution to understanding BHLH TF biology. If the interpretation is not rigorously supported, the novelty claim is weakened. The field needs clear evidence that the observed binding events are biologically relevant.
- **Resolution test** Provide additional validation of the Q-A-R BHLH DNA binding, such as electrophoretic mobility shift assays (EMSAs) with purified proteins, or in vivo ChIP-seq data. Include appropriate negative controls and statistical analysis of motif enrichment.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "TF binding site comparison in B73 and Mo17 inbreds reveals widespread differences... that correlate with gene expression changes."
- **Evidence pointer** Results section "Correlation of genotype-specific peaks with RNA expression", Figure 4g, Supplemental Figure 12d-12e
- **Concern** The correlation between genotype-specific TF binding and gene expression changes is a key claim, but the analysis appears to be purely correlative. The authors use Fisher's exact test to assess overlap between genotype-specific peaks and differentially expressed genes, but this does not establish a causal relationship. The analysis does not account for confounding factors such as linkage disequilibrium, co-regulation by multiple TFs, or indirect effects. The authors should consider more sophisticated approaches, such as Mendelian randomization or allele-specific expression analysis, to strengthen the causal inference.
- **Why it matters** The claim that TF binding variation drives expression differences is central to the manuscript's thesis. If the correlation is not rigorously established, the conclusion is overstated. The field is moving toward more rigorous causal inference frameworks, and this manuscript should reflect that.
- **Resolution test** Provide additional analyses that strengthen the causal link, such as allele-specific expression analysis in hybrids, or a more formal mediation analysis. Alternatively, temper the claim to reflect the correlative nature of the evidence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the study provides "empirical binding site annotation for 5.3% of the maize genome." This percentage is presented without context, and it is unclear whether this is a large or small fraction relative to the total regulatory space. The authors should provide context for this number.
- **Required correction** Add a brief contextual statement, such as comparing this to the fraction of the genome that is expected to be regulatory, or noting that this is the largest such dataset for maize to date.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Genomic DNA library constructions, DAP-seq, and DoubleDAP-seq"
- **Issue** The methods for DAP-seq and doubleDAP-seq are described, but the details of the doubleDAP-seq protocol are sparse. The authors reference a previous publication for the doubleDAP-seq method, but the modifications for maize should be described more fully.
- **Required correction** Provide additional details on the doubleDAP-seq protocol, including the expression constructs, the ratio of the two proteins, and the purification steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results section "Large scale mapping of TF binding sites in maize B73"
- **Issue** The authors report that "twenty-two traits" showed significant enrichment between GWAS hits and DAP-seq peaks. The multiple testing correction is not described, and it is unclear whether the enrichment analysis accounts for the number of TFs and traits tested.
- **Required correction** Describe the multiple testing correction used in the enrichment analysis and report adjusted p-values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The authors do not state where the DAP-seq data will be deposited. Given the resource value of the dataset, data availability is critical.
- **Required correction** State the accession numbers for the raw and processed data in a public repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Results section "Comparative TF binding in two diverse inbred lines"
- **Issue** The definition of "positional variants" (PosVs) is introduced in the methods but the biological significance is not clearly explained in the results. The authors should clarify why positional variation matters for gene regulation.
- **Required correction** Add a brief explanation of the potential functional consequences of positional variation in TF binding sites.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results
- **Evidence pointer** Results section "Impact of TF heterodimerization on DNA-binding and binding site preference"
- **Issue** The authors state that "eight of nine" Q-A-R type BHLHs tested yielded peaks, but the criteria for "moderate number of peaks" is not defined. The range of 1,153 to 19,154 peaks is very broad, and it is unclear whether all of these are statistically significant.
- **Required correction** Provide the statistical thresholds used for peak calling and report the number of significant peaks for each TF.

## Risk / unsupported claims
- The claim that structural variation is the "largest driver" of TF binding divergence is not supported by a formal statistical analysis partitioning variance among variant types.
- The causal link between MADS69 binding disruption at vgt1 and flowering time variation is correlative, not causal.
- The functional significance of the novel CCCATnCC motif bound by Q-A-R BHLH heterodimers is not demonstrated.
- The claim that "modification of TF binding regions via CRISPR-Cas9 mediated editing alters target gene expression and phenotype" is based on large deletions that remove entire cis-regulatory modules, not individual binding sites, making the attribution to specific TF binding events uncertain.
- The correlation between genotype-specific TF binding and gene expression changes is purely correlative and does not establish causality.
- The percentage of the genome covered by TF binding sites (5.3%) is presented without context for its significance.
- The biological relevance of positional variants (PosVs) is asserted but not functionally validated.