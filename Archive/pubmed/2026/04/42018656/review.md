## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, experimental design, data analysis, interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that FOSL2, an AP-1 family transcription factor, drives endothelial cell state changes and chromatin accessibility alterations in systemic sclerosis-associated pulmonary hypertension, based on human multiome data, transgenic mouse models, and in vitro overexpression studies
- **Visible evidence base** Single-cell multiome sequencing (human), single-cell RNA sequencing (mouse models), ChromBPNet analysis, SCARNA/SCENIC+ regulatory network inference, CellOracle in silico perturbations, SuHx mouse model with AP-1 inhibitor treatment, histology, and gene expression analyses
- **Missing materials affecting confidence** Figures and supplementary figures/tables referenced but not provided; detailed statistical outputs; raw data; complete methods for some analyses; information on sample sizes for some experiments; details on antibody validation and specificity

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive multi-omics investigation into the role of FOSL2 in systemic sclerosis-associated pulmonary vascular remodeling. The integration of human multiome data, transgenic mouse models, and in silico perturbation analyses provides a multi-layered approach that is commendable. However, several concerns regarding the causal inference, the specificity of FOSL2 versus other AP-1 family members, the interpretation of the ChromBPNet results, and the negative therapeutic intervention data need to be addressed before the central claims can be fully established.

- **Who would be interested in the results, and why** Researchers in pulmonary hypertension, systemic sclerosis, vascular biology, and transcriptional regulation would find this work relevant. The study addresses a clinically important complication (SSc-PH) with limited therapeutic options, and the identification of FOSL2 as a potential driver of endothelial dysfunction could inform future therapeutic strategies. The methodological integration of single-cell multiome, chromatin accessibility modeling, and in silico perturbation is also of interest to computational biologists working on gene regulatory networks.

- **Major strengths**
  1. The study leverages a multi-layered approach combining human multiome data, transgenic mouse models, and in vitro experiments, providing complementary lines of evidence.
  2. The use of ChromBPNet for base-pair resolution chromatin accessibility analysis is a sophisticated and appropriate application of a state-of-the-art computational tool.
  3. The comparison between Fosl2tg and SuHx mouse models, and their overlap with human SSc-ILD-PH, strengthens the translational relevance of the findings.
  4. The inclusion of a therapeutic intervention study (T-5224), even with negative hemodynamic results, adds rigor and transparency to the work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The manuscript claims that FOSL2 is a key driver of the altered endothelial cell state in SSc-ILD-PH, based on correlation between FOSL2 expression, AP-1 motif accessibility, and disease phenotype.
- **Evidence pointer** Results sections "Gene regulatory network analysis of vascular ECs in SSc-ILD-PH and healthy control lungs shows an enrichment of FOSL2 regulatory network" and "Elucidating the epigenomic landscape of FOSL2-overexpressing primary ECs"
- **Concern** The causal relationship between FOSL2 and the observed endothelial changes is inferred primarily from correlative data (increased FOSL2 expression, increased AP-1 motif accessibility) and from the Fosl2tg mouse model. However, the Fosl2tg model overexpresses FOSL2 under a heterologous promoter, which may not recapitulate the precise spatiotemporal expression pattern in human disease. The in vitro overexpression experiments in primary ECs demonstrate that FOSL2 can bind to AP-1 motifs, but this does not establish that FOSL2 is necessary for the disease phenotype. Loss-of-function experiments (e.g., FOSL2 knockdown or knockout in ECs, or genetic rescue in the mouse model) are not presented.
- **Why it matters** Without loss-of-function data, the claim that FOSL2 "drives" the pathological changes remains correlative. The field of transcriptional regulation in disease has been plagued by claims of causality based on overexpression or correlation alone. Establishing necessity is critical for proposing FOSL2 as a therapeutic target.
- **Resolution test** Provide loss-of-function data (e.g., EC-specific FOSL2 knockout in the Fosl2tg background, or siRNA/shRNA knockdown in primary ECs followed by assessment of the pathological gene expression program and chromatin accessibility changes). Alternatively, demonstrate that a FOSL2 dominant-negative or a specific AP-1 inhibitor reverses the EC phenotype in the mouse model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of FOSL2 vs. other AP-1 members
- **Claim pointer** The manuscript attributes the observed AP-1 binding and downstream effects specifically to FOSL2, but AP-1 complexes are composed of multiple Jun and Fos family members that can form various homo- and heterodimers.
- **Evidence pointer** Results sections "Gene regulatory network analysis of vascular ECs in SSc-ILD-PH and healthy control lungs shows an enrichment of FOSL2 regulatory network" and "Elucidating the epigenomic landscape of FOSL2-overexpressing primary ECs"
- **Concern** The ChromBPNet analysis identifies AP-1 motif binding, and the authors infer FOSL2 as the key factor based on its increased expression. However, other AP-1 members (e.g., FOS, FOSB, FOSL1, JUN, JUNB, JUND) are also part of the AP-1 family and could bind to the same or similar motifs. The manuscript does not systematically assess the expression and binding of other AP-1 members in the same datasets. The in vitro overexpression of FOSL2 demonstrates that it can bind, but does not exclude that other AP-1 dimers are the functional entities in the disease context.
- **Why it matters** The therapeutic implication is that targeting FOSL2 specifically (rather than AP-1 broadly) would be effective. If other AP-1 members are equally or more important, a FOSL2-specific approach may fail. The manuscript's discussion of "AP-1 inhibition" with T-5224 is broad and does not address FOSL2 specificity.
- **Resolution test** Perform a comprehensive analysis of all AP-1 family member expression in the human multiome data and in the mouse models. Use computational approaches (e.g., motif footprinting with factor-specific models) or experimental approaches (e.g., ChIP-seq for multiple AP-1 members) to determine which family members are actually bound at the identified loci. If FOSL2 is claimed to be the primary driver, show that other AP-1 members are not upregulated or not bound at the same sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of ChromBPNet results
- **Claim pointer** The manuscript states that ChromBPNet inferred "increased AP-1 binding at base pair resolution in SSc-ILD-PH ECs" and that FOSL2 overexpression leads to binding to the same motifs.
- **Evidence pointer** Results section "Elucidating the epigenomic landscape of FOSL2-overexpressing primary ECs"
- **Concern** ChromBPNet is a model that predicts chromatin accessibility from DNA sequence, and TF-MoDISco identifies motifs with high attribution scores. However, the inference of "binding" from these models is indirect. The models predict accessibility, not actual protein-DNA binding. The claim of "increased AP-1 binding" should be more carefully worded as "increased predicted AP-1 motif accessibility" or "increased model-predicted AP-1 occupancy." Direct evidence of binding (e.g., ChIP-seq for FOSL2 or other AP-1 members) is not provided. Additionally, the comparison between the in vitro FOSL2 overexpression and the human disease data relies on the assumption that the same motifs are being bound, but the manuscript does not show a quantitative comparison of the motif usage or the genomic contexts.
- **Why it matters** Overstating the inference from computational models can mislead readers into thinking that direct binding evidence exists. The distinction between predicted and experimentally validated binding is crucial for the strength of the claims. If the authors wish to claim FOSL2 binding, ChIP-seq data are needed.
- **Resolution test** Provide ChIP-seq data for FOSL2 (and ideally other AP-1 members) in the in vitro overexpressing ECs and, if possible, in human SSc-ILD-PH lung tissue or isolated ECs. Alternatively, rephrase all claims to clearly state that the findings are based on computational predictions of accessibility and motif activity, not direct binding measurements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Therapeutic intervention interpretation
- **Claim pointer** The manuscript reports that T-5224, an AP-1 inhibitor, did not reduce pulmonary artery pressure in the SuHx model but did partially reverse the molecular changes in ECs.
- **Evidence pointer** Results section "AP-1 inhibitor treatment of Sugen-hypoxia"
- **Concern** The negative hemodynamic result is presented as a partial molecular reversal. The authors acknowledge the lack of effect on pulmonary pressures but do not fully explore why the molecular changes did not translate to functional improvement. Possible explanations include: (1) the dose or duration of T-5224 was insufficient; (2) the molecular changes are not causally linked to hemodynamic changes; (3) the SuHx model is not fully representative of SSc-PH; or (4) the molecular changes measured are not the rate-limiting step. The manuscript does not provide sufficient discussion of these possibilities.
- **Why it matters** The therapeutic relevance of targeting AP-1/FOSL2 is a key translational claim. A negative hemodynamic result, even with molecular changes, weakens the case for therapeutic efficacy. The authors need to address this discrepancy more thoroughly to avoid overinterpreting the molecular data.
- **Resolution test** Provide additional data on the extent of AP-1 inhibition achieved by T-5224 in the lung tissue (e.g., target engagement assays). Discuss alternative dosing regimens or combination approaches. Consider whether the molecular changes observed are sufficient to expect hemodynamic improvement, or whether longer treatment or earlier intervention might be needed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Sample size and statistical power
- **Claim pointer** The study uses human multiome data from 9 SSc-ILD-PH patients and 6 controls, and mouse scRNA-seq from 3 WT and 3 Fosl2tg mice.
- **Evidence pointer** Results sections "Single-cell multiome sequencing of SSc-ILD-PH and healthy control lungs can identify different subtypes of ECs" and "Single-cell RNA-Seq identifies cellular and transcriptomic changes in ECs from Fosl2tg mice"
- **Concern** The sample sizes are relatively small, particularly for the human multiome data. While single-cell approaches can be powerful, the small number of biological replicates may limit the generalizability of the findings and the robustness of the differential expression and accessibility analyses. The manuscript does not report how many cells were analyzed per sample, which is critical for assessing the statistical power of the single-cell analyses.
- **Why it matters** Small sample sizes can lead to false positives or false negatives, and the lack of reporting on cell numbers makes it difficult to assess the reliability of the conclusions. The field is increasingly aware of the importance of adequate sample sizes and reporting standards in single-cell studies.
- **Resolution test** Report the number of cells per sample and per cell type for all single-cell datasets. Provide power calculations or at least a discussion of the limitations imposed by the sample sizes. If possible, validate key findings in an independent cohort or using additional publicly available datasets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction are dense and use specialized terminology without sufficient context for a broad readership. For example, the term "multiome" is used without explanation, and the distinction between group 1 and group 3 PH in SSc is not clearly explained for non-specialists.
- **Required correction** Provide brief definitions or explanations for key terms and concepts, particularly for readers who may not be experts in pulmonary hypertension or single-cell genomics. Consider adding a sentence in the introduction that clearly distinguishes the clinical contexts of group 1 and group 3 PH in SSc.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures referenced throughout the Results
- **Issue** The figures are not provided in the manuscript text, making it impossible to assess the quality of the data visualization, the appropriateness of the statistical tests, or the clarity of the figure legends.
- **Required correction** Ensure that all figures are clearly labeled, with informative legends that explain the experimental design, the number of replicates, and the statistical tests used. Consider adding schematic diagrams to help readers navigate the multi-omics workflow.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methods completeness
- **Affected element** Methods section
- **Evidence pointer** Methods sections "Single-cell multiome sequencing nuclei isolation and data analysis" and "Construction of GRNs using SCENIC+"
- **Issue** The methods for some analyses are described at a high level, and it is unclear whether all parameters and thresholds are fully specified. For example, the criteria for selecting the number of topics in the LDA model (60 topics) and the specific parameters for the SCENIC+ and CellOracle analyses are not fully detailed.
- **Required correction** Provide more detailed descriptions of the computational parameters and thresholds used, or reference the relevant publications and software documentation more explicitly. This will allow other researchers to reproduce the analyses.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Methods section "Data availability"
- **Issue** The data availability statement mentions deposition in GEO, but the accession numbers are not provided in the manuscript text. This makes it difficult for readers to access the data immediately.
- **Required correction** Include the GEO accession numbers in the data availability statement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Results sections
- **Issue** The manuscript uses "Fosl2tg" and "Fostg" interchangeably in the Results section, which could cause confusion.
- **Required correction** Use a single, consistent abbreviation for the transgenic mouse model throughout the manuscript.

## Risk / unsupported claims
- The claim that FOSL2 is a "key driver" of the EC phenotype is not fully supported without loss-of-function data (R1-M1).
- The inference of "increased AP-1 binding" from ChromBPNet is an overstatement; the model predicts accessibility, not direct binding (R1-M3).
- The claim that the overlap between Fosl2tg and SSc-ILD-PH EC gene expression supports a shared mechanism is weakened by the lack of direct comparison of the chromatin accessibility landscapes between the two systems.
- The statement that "FOSL2 regulates both hypoxia-dependent and -independent pathways" is based on indirect comparisons between models and lacks direct experimental validation of hypoxia dependence.
- The negative hemodynamic result with T-5224 is not fully reconciled with the claim of molecular reversal, and the therapeutic implications are therefore not clearly established (R1-M4).
- The manuscript does not provide evidence that the FOSL2-driven changes in ECs are specific to SSc-ILD-PH as opposed to other forms of pulmonary hypertension, as no comparator PH groups (e.g., idiopathic PAH) are included.