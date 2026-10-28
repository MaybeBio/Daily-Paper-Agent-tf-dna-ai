## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, conflict of interest, author contributions, and supplementary table descriptions. No figures or supplementary data files were provided for inspection.
- **Assessment boundary** The review is limited to the textual content supplied. Claims referring to figures, tables, and supplementary materials are assessed based on their description in the text only, as the actual data displays were not available.
- **Shared manuscript claim summary** The authors propose that the SNP rs11573156 in the 5' UTR of PLA2G2A creates an allele-specific binding site for the transcription factor SP1, with higher affinity for the alternative C allele than the reference G allele. They further propose that this differential binding affinity modulates PLA2G2A transcript levels in a tissue-dependent manner, with the effect most pronounced in tissues with lower SP1 protein levels. A mathematical model based on Michaelis-Menten kinetics is used to formalize this relationship, and predictions are compared with GTEx eQTL data and Human Protein Atlas (HPA) protein data.
- **Visible evidence base** Text descriptions of: GTEx eQTL analysis (234 eQTLs across 18 tissues); SNP2TFBS predictions (9 of 37 eQTLs associated with TF binding sites; 7 eQTLs predicted to affect 8 TFs); ENCODE ChIP-seq validation (SP1 binding to rs11573156 in liver); correlation analysis between SP1 and PLA2G2A in liver (r = 0.31); comparison of correlation coefficients between top 11 and bottom 11 tissues; mathematical model with stated parameter values; HPA categorical SP1 protein levels for top 11 tissues.
- **Missing materials affecting confidence** Figures 1-4, Supplementary Tables 1-2, the full mathematical model derivation, parameter estimation procedures, statistical test details, and the complete list of 37 eQTLs with their tissue distributions. The methods section is incomplete in the provided text, with equations referenced but not shown.

## Reviewer

- **Overall assessment** The manuscript addresses a clinically relevant question: how genetic variation at rs11573156 influences PLA2G2A expression and thus circulating sPLA2-IIA levels. The authors combine publicly available genomic, transcriptomic, and proteomic datasets to build a plausible mechanistic hypothesis involving allele-specific SP1 binding. The integration of eQTL data, ChIP-seq evidence, and a kinetic model is a reasonable approach. However, the evidence as presented is largely correlative, the model is not rigorously validated, and several key analyses are described only in text without supporting data displays. The central claim that differential SP1 binding affinity is the primary mechanism driving PLA2G2A expression differences requires direct experimental validation, which is absent. The manuscript is of interest to researchers in genetic regulation, lipid biology, and inflammation, but the current evidence base is insufficient to fully establish the proposed mechanism.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation by common SNPs, particularly those interested in allele-specific transcription factor binding as a mechanism for eQTL effects. Investigators working on PLA2G2A biology, secreted phospholipases, and their roles in sepsis, cardiovascular disease, and COVID-19 would find the genetic regulatory insights relevant. The modeling approach may interest computational biologists working on gene expression regulation. Clinicians or translational researchers focused on biomarkers for inflammatory conditions may also find the connection between genotype, transcription factor levels, and protein output relevant.
- **Major strengths** The study addresses a clinically important gene with established disease associations. The use of multiple public datasets (GTEx, ENCODE, HPA) to triangulate evidence is commendable. The focus on protein levels rather than mRNA levels for SP1 is a thoughtful choice, acknowledging potential discordance between transcript and protein abundance. The mathematical model provides a formal framework for understanding how binding affinity differences translate into expression differences, and the prediction that the allelic effect diminishes at high SP1 concentrations is testable and interesting. The authors acknowledge limitations regarding tissue coverage and alternative mechanisms.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the binding affinity differences of SP1 for the different rs11573156 alleles can influence PLA2G2A expression" and that this "likely constitutes a primary genetic/molecular mechanism affecting circulating sPLA2-IIA levels."
- **Evidence pointer** Results sections "SP1 Bound to rs11573156 as a Transcriptional Activator of PLA2G2A" and "SP1 Differential Binding to rs11573156 Alleles Influences PLA2G2A Expression Variation"; Figure 3 and Figure 4 descriptions
- **Concern** The central mechanistic claim rests on correlative evidence. The ChIP-seq data show SP1 binds near rs11573156 in liver cells, but no experiment demonstrates that the C allele binds SP1 with higher affinity than the G allele in a direct binding assay. The correlation between SP1 and PLA2G2A levels (r = 0.31) is modest and does not establish causality. The model is fitted with "loosely selected" parameters and is not validated against independent data. No reporter assays, electrophoretic mobility shift assays, or CRISPR-based allele editing experiments are presented to directly test the allele-specific binding hypothesis.
- **Why it matters** Without direct experimental evidence of differential binding affinity, the proposed mechanism remains speculative. The claim of a "primary" mechanism is not supported by the data presented, which are consistent with but do not prove the hypothesis. Alternative explanations, such as linkage disequilibrium with a causal variant elsewhere, are not excluded.
- **Resolution test** The authors should provide direct biochemical evidence of allele-specific SP1 binding (e.g., EMSA or surface plasmon resonance with allele-specific oligonucleotides), or functional evidence from reporter assays or allele-specific gene editing in a relevant cell line. Alternatively, they should temper the claim to reflect that the data are consistent with, but do not establish, this mechanism.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The authors state that "the model predicts that the discrepancy in [G2A]ss between the two alleles, represented as Δ[G2A]ss, becomes more pronounced at lower concentrations of SP1 protein levels" and that this prediction is validated by HPA data.
- **Evidence pointer** Methods section "Modeling the correlation between SP1 levels and PLA2G2A gene expression"; Results section "Validation of the Model Predictions Using SP1 Protein Levels Across Tissues"; Figure 4 descriptions
- **Concern** The model parameters are described as "loosely selected to fit the observed trend," which raises concerns about circularity. The model is not derived from independent measurements of binding kinetics, and no sensitivity analysis is presented. The validation uses categorical HPA data (Low, Medium, High) with only 11 tissues, and the statistical significance of the trend in Figure 4B and 4C is not reported. The model assumes Michaelis-Menten kinetics for transcription, which is a simplification that may not capture the complexity of transcriptional regulation.
- **Why it matters** A model with parameters chosen to fit the data cannot serve as independent validation of the hypothesis. The predictive power of the model is therefore unclear. The small number of tissues and categorical nature of the protein data limit the strength of the validation.
- **Resolution test** The authors should estimate model parameters from independent experimental data, perform a sensitivity analysis, and report statistical tests for the trends in Figure 4B and 4C. Ideally, the model should be validated on a larger set of tissues or with quantitative protein measurements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "in the majority (if not all) of the top 11 tissues, SP1 binds to the eQTL rs11573156, thereby affecting (transactivating) PLA2G2A expression."
- **Evidence pointer** Results section "SP1 Bound to rs11573156 as a Transcriptional Activator of PLA2G2A"; Figure 3B description
- **Concern** The ChIP-seq validation of SP1 binding is only available for liver. The authors extrapolate this mechanism to other tissues based on correlation patterns alone. The correlation between SP1 and PLA2G2A in other tissues could arise from indirect effects or confounding factors. The authors acknowledge this limitation in the Discussion, but the claim as stated in the Results overreaches.
- **Why it matters** The generalizability of the mechanism to multiple tissues is a key part of the paper's significance. If the mechanism is only validated in liver, the broader claims about tissue-specific regulation are weakened.
- **Resolution test** The authors should either obtain ChIP-seq data for additional tissues, perform allele-specific expression analysis in multiple tissues, or revise the claim to be explicitly limited to liver with other tissues described as consistent with but not confirmatory of the mechanism.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report that "the correlation coefficients between SP1 and PLA2G2A in these top 11 tissues were significantly higher (p = 0.03) than in the control tissues."
- **Evidence pointer** Results section "SP1 Bound to rs11573156 as a Transcriptional Activator of PLA2G2A"; Figure 3B description
- **Concern** The statistical comparison between top 11 and bottom 11 tissues is described with a single p-value, but the test used is not specified. The selection of tissues based on eQTL effect size introduces potential selection bias, and the comparison may not be independent. The number of tissues is small, and the correlation coefficients themselves are not reported with confidence intervals.
- **Why it matters** The statistical robustness of this comparison underpins the claim that SP1 is a relevant regulator across tissues. Without proper statistical detail, the strength of this evidence is unclear.
- **Resolution test** The authors should specify the statistical test used, report effect sizes with confidence intervals, and consider whether the tissue selection procedure requires correction for multiple comparisons or a permutation-based approach.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Modeling the correlation between SP1 levels and PLA2G2A gene expression"
- **Evidence pointer** Methods section, equation descriptions
- **Issue** The differential equation and its derivation are referenced but not shown in the provided text. The parameters k, K, n, and dG2A are defined only briefly.
- **Required correction** Provide the full equation, define all variables and parameters explicitly, and describe how parameter values were selected.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Collection of PLA2G2A eQTLs in different tissues"
- **Evidence pointer** Methods section, first paragraph
- **Issue** The criteria for selecting the 18 tissues and the specific eQTL significance thresholds are not fully described. The filtering process from 234 eQTLs to 37 eQTLs is not detailed.
- **Required correction** Describe the tissue selection criteria, the eQTL significance thresholds, and the exact filtering steps used to arrive at the 37 eQTLs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary Table 1 and Supplementary Table 2
- **Evidence pointer** Supplementary table descriptions
- **Issue** The supplementary tables are described but not provided. The content of Supplementary Table 2, which is central to the validation, is not fully described.
- **Required correction** Ensure the supplementary tables are available and clearly formatted, with column headers explained in the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section, limitations paragraph
- **Evidence pointer** Discussion, final paragraph
- **Issue** The authors note that ChIP-seq data were only available in a liver cell line, but they do not specify which cell line was used or whether it is a primary cell or immortalized line.
- **Required correction** Specify the cell line used in the ENCODE ChIP-seq analysis and note any potential limitations of using a cell line versus primary tissue.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction, references [1-4]
- **Issue** The introduction provides a broad overview of sPLA2 biology but does not discuss prior work on the regulation of PLA2G2A expression or previous studies of rs11573156 function.
- **Required correction** Add a brief discussion of prior studies on PLA2G2A regulation and any previous functional characterization of rs11573156 to contextualize the novelty of this work.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract, Results section "SP1 Differential Binding to rs11573156 Alleles Influences PLA2G2A Expression Variation"
- **Issue** The term "primary genetic/molecular mechanism" is used in the Discussion, but the evidence does not exclude other regulatory mechanisms. The term "primary" may overstate the findings.
- **Required correction** Consider replacing "primary" with "a" or "one" to avoid overstatement, or provide additional evidence to support the primacy claim.

## Risk / unsupported claims

- The claim that rs11573156 is "the most associated" SNP for sPLA2-IIA levels is stated without a systematic comparison of all associated SNPs.
- The claim that the proposed mechanism "likely constitutes a primary genetic/molecular mechanism affecting circulating sPLA2-IIA levels" is not supported by direct experimental evidence.
- The model prediction that Δ[G2A]ss diminishes at high SP1 concentrations is presented as validated, but the statistical significance of the trend in Figure 4B and 4C is not reported.
- The statement that "the correlation coefficients between SP1 and PLA2G2A in these top 11 tissues were significantly higher (p = 0.03) than in the control tissues" lacks specification of the statistical test and effect sizes.
- The claim that SP1 acts as a transcriptional activator of PLA2G2A is inferred from correlation and ChIP-seq binding data, but no functional perturbation experiments are presented.
- The assertion that the allele-specific effect is due to differential binding affinity is inferred from in silico predictions (SNP2TFBS) and ChIP-seq, but no direct binding measurements are provided.
- The statement that "the primary organ thought to produce sPLA2-IIA released into circulation is the liver" is presented without supporting citation or data in the provided text.
- The claim that deceased COVID-19 patients exhibited "considerably elevated levels of circulating, catalytically active sPLA2-IIA" is referenced to prior work but not detailed in this manuscript.