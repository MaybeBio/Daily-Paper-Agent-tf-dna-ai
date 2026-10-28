## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, experimental design, data analysis, and interpretation as presented in the manuscript
- **Shared manuscript claim summary** The authors identify putative endothelial gene regulatory elements activated during cardiopharyngeal mesoderm differentiation by integrating bulk ATAC-seq and RNA-seq data from a mouse embryonic stem cell differentiation model with published single-cell RNA-seq data, and validate a subset using CRISPR-dCas9:LSD1 epigenetic reprogramming and CRISPR-Cas9 deletion.
- **Visible evidence base** Abstract, Results sections with Figures 1-7, Tables 1-3, Discussion, Methods, and references to Supplementary Data files
- **Missing materials affecting confidence** Supplementary Data files 1-6, Supplementary Figure 1, and the Peer Review File were not provided; raw sequencing data and detailed bioinformatics parameters are not fully described

## Reviewer
- **Overall assessment** The manuscript presents a systematic approach to identify putative endothelial regulatory elements in a cardiopharyngeal mesoderm differentiation model. The integration of ATAC-seq, RNA-seq, and published scRNA-seq data is methodologically sound, and the validation experiments provide functional support for several identified elements. However, the study is largely descriptive and the validation is limited to a small subset of elements. The claim that GATA/ETS/FOS is a "likely driver" of EC regulation in cardiopharyngeal mesoderm is plausible but not directly tested. The manuscript would benefit from more direct functional evidence linking the identified elements to lineage-specific gene regulation and from a clearer demonstration of the cardiopharyngeal specificity of these elements.

- **Who would be interested in the results, and why** Researchers studying endothelial cell differentiation, cardiopharyngeal mesoderm development, gene regulatory elements, and enhancer biology. The methodological approach combining chromatin accessibility, gene expression, and machine learning may interest those developing computational tools for enhancer prediction. The identified regulatory elements could serve as a resource for studying EC lineage specification.

- **Major strengths**
  1. The study addresses an important gap in understanding EC gene regulation in the cardiopharyngeal lineage.
  2. The integration of multiple data types (ATAC-seq, RNA-seq, scRNA-seq) is well conceived.
  3. The use of both epigenetic reprogramming and genetic deletion for validation strengthens the conclusions.
  4. The machine learning approach for enhancer prediction is a useful addition to the field.
  5. The identification of GATA/ETS/FOS motif enrichment is consistent with known EC biology.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that the identified putative regulatory elements are "activated during endothelial differentiation within the cardiopharyngeal mesoderm" and that validation using CRISPR-dCas9:LSD1 and CRISPR-Cas9 confirms their regulatory function.
- **Evidence pointer** Figures 5-6, Table 3, Methods section "CRISPR-dCas9:LSD1-mediated epigenetic reprogramming strategy"
- **Concern** The validation experiments are performed in the bulk differentiating cell population, not specifically in the EC subpopulation. The d4 time point contains only 19% VE-Cadherin+ cells, and the d6/d8 populations are enriched but not purified. Therefore, the observed changes in gene expression following enhancer perturbation could reflect effects on non-EC cell types within the differentiating culture. The authors do not demonstrate that the regulatory elements function specifically in ECs or in the cardiopharyngeal lineage.
- **Why it matters** The central claim of the paper is that these elements are associated with EC differentiation in the cardiopharyngeal mesoderm. Without cell-type-specific validation, the functional relevance of these elements to EC biology specifically remains uncertain. The elements could be active in other mesodermal derivatives present in the culture.
- **Resolution test** Perform validation experiments in purified EC populations (e.g., FACS-sorted VE-Cadherin+ cells) or use single-cell readouts following enhancer perturbation. Alternatively, demonstrate that the enhancer activity is specific to ECs using reporter assays in the differentiation system.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state that "Results showed that LSD1 targeting of the six EC-REs resulted in reduced expression of the associated genes (Fig. 5b), with the exception of the Pecam1-associated RE."
- **Evidence pointer** Figure 5b, Methods section "Quantitative RT-PCR"
- **Concern** The statistical analysis for the qPCR validation data is not clearly described. The figure legend mentions p values from a parametric paired t-test, one-tailed, but it is unclear how many independent differentiations were performed, whether technical replicates were averaged before statistical testing, and whether multiple testing corrections were applied. The use of a one-tailed test is also questionable without clear justification, as the direction of the effect could not be assumed a priori for all elements.
- **Why it matters** The validation data form the core functional evidence for the paper. Inadequate statistical reporting undermines confidence in the conclusions drawn from these experiments.
- **Resolution test** Provide complete statistical details including number of independent experiments, whether data were normally distributed, justification for one-tailed tests, and whether corrections for multiple comparisons were applied. Consider presenting individual data points in the figures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of findings
- **Claim pointer** The authors claim that the identified elements are "associated with cardiopharyngeal lineage differentiation" and that the approach identifies "cell type-specific regulatory elements."
- **Evidence pointer** Results section "An unbiased strategy identifies putative regulatory elements in early EC differentiation", Table 2
- **Concern** The specificity of the identified elements to the cardiopharyngeal lineage is not established. The comparison with Mesp1Cre-derived EC clusters includes a broader mesodermal EC population, and the overlap between Tbx1Cre and Mesp1Cre datasets is not clearly quantified. The authors do not compare their identified elements with EC regulatory elements from other lineages (e.g., lateral plate mesoderm-derived ECs) to demonstrate cardiopharyngeal specificity.
- **Why it matters** The title and framing of the paper emphasize the cardiopharyngeal lineage. Without demonstrating that these elements are specific to or enriched in this lineage, the findings may simply reflect general EC regulatory mechanisms.
- **Resolution test** Compare the identified elements with EC enhancers from other lineages or developmental origins. Use publicly available datasets to assess whether the 101 elements are enriched for cardiopharyngeal-specific regulatory activity or are shared across EC lineages.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic insight
- **Claim pointer** The authors conclude that "the core EC transcription factors GATA/ETS/FOS is a likely driver of EC regulation in cardiopharyngeal mesoderm."
- **Evidence pointer** Figure 3c, Results section "An unbiased strategy identifies putative regulatory elements in early EC differentiation", Discussion
- **Concern** The motif enrichment analysis identifies GATA, ETS, and FOS motifs, but no functional experiments are performed to test whether these transcription factors actually drive the activity of the identified elements. The claim that they are "likely drivers" is speculative and not directly supported by the data presented. Furthermore, the authors do not examine whether these factors are expressed in the EC population at the relevant time points.
- **Why it matters** The mechanistic claim is a key conclusion of the paper. Without functional validation (e.g., knockdown/overexpression of GATA/ETS/FOS factors followed by assessment of enhancer activity or target gene expression), the conclusion remains correlative.
- **Resolution test** Perform perturbation experiments targeting GATA, ETS, or FOS factors in the differentiation system and assess the impact on the activity of the identified elements or on EC gene expression. Alternatively, use chromatin immunoprecipitation to demonstrate binding of these factors to the identified elements.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data availability and reproducibility
- **Claim pointer** The authors state that "RNA-seq analysis performed on two replicates from two independent differentiation experiments confirmed the activation of an endothelial expression program."
- **Evidence pointer** Methods section "RNA-seq" and "ATAC-seq"
- **Concern** The manuscript reports only two biological replicates for both RNA-seq and ATAC-seq experiments. This is a minimal number for reliable differential expression and accessibility analysis. Additionally, the authors do not report whether the sequencing data have been deposited in a public repository, which is essential for reproducibility and for the community to fully utilize the identified elements.
- **Why it matters** The study relies heavily on the identification of differentially expressed genes and differentially accessible regions. With only two replicates, the statistical power is limited, and the reliability of the identified elements is uncertain. Public data deposition is standard practice and necessary for the scientific community to verify and build upon these findings.
- **Resolution test** Provide evidence of data deposition (e.g., GEO accession numbers) and discuss the limitations of using two biological replicates. If possible, include additional replicates or validate key findings with orthogonal methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1b
- **Evidence pointer** Figure 1b, Results section
- **Issue** The RT-PCR data in Figure 1b are presented as gel images, which are semi-quantitative. The authors do not provide quantitative RT-PCR data for the marker genes shown.
- **Required correction** Provide quantitative RT-PCR data (e.g., bar graphs with fold change) for the key marker genes to support the qualitative gel images.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Machine learning enhancer prediction
- **Evidence pointer** Methods section "Enhancer prediction"
- **Concern** The description of the machine learning approach lacks details on feature selection, model evaluation metrics, and the performance of the model on the test set. The authors mention accuracy was determined but do not report the value.
- **Required correction** Provide the accuracy and other relevant performance metrics of the model on the test set, and describe the features used in the logistic regression model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Figure 7
- **Evidence pointer** Figure 7, Results section
- **Issue** The gastruloid experiments show qualitative differences in PECAM1 staining and network complexity, but the authors state they could not quantify the differences. This limits the strength of the conclusions drawn from this experiment.
- **Required correction** Attempt to develop a quantitative method for assessing vascular network complexity in gastruloids, or acknowledge this limitation more explicitly in the discussion.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of GATA/ETS/FOS as core EC transcription factors is brief and does not fully contextualize the findings within the broader literature on EC enhancer biology.
- **Required correction** Expand the discussion to more thoroughly compare the identified elements and transcription factor motifs with previously characterized EC enhancers and regulatory mechanisms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4
- **Issue** The ATAC-seq coverage tracks in Figure 4 are difficult to interpret without clear genomic coordinates or annotation of the regions shown.
- **Required correction** Add genomic coordinates and gene annotations to the ATAC-seq tracks to improve interpretability.

## Risk / unsupported claims
1. The claim that the identified elements are specifically "associated with cardiopharyngeal lineage differentiation" is not fully supported, as the comparison with Mesp1Cre-derived ECs does not establish cardiopharyngeal specificity.
2. The conclusion that GATA/ETS/FOS is a "likely driver" of EC regulation is correlative and not directly tested.
3. The statement that the approach identifies "cell type-specific regulatory elements" is not demonstrated, as the specificity of the elements to ECs versus other cell types in the differentiation culture is not established.
4. The validation experiments do not demonstrate that the regulatory elements function specifically in ECs, as the experiments were performed in bulk differentiating cultures.
5. The claim that the modified differentiation protocol produces a "nearly homogeneous population of ECs" is based on VE-Cadherin expression and Matrigel assays, but the percentage of VE-Cadherin+ cells at d8 (91.3%) does not exclude the presence of other cell types that could influence the results.
6. The manuscript does not provide evidence that the identified elements are active in vivo in the cardiopharyngeal mesoderm lineage, as all experiments are performed in an in vitro differentiation model.