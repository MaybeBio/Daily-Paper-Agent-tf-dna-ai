## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Methods, Results, Discussion, Conclusion, Data availability, Author contributions, Conflict of interest, Generative AI statement, Publisher's note, Supplementary material notice)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims relative to presented evidence, and alignment with Nature-style criteria. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors apply GENIE3 to a curated multi-source RNA-seq dataset (selongEXPRESS, 330 samples) from *Synechococcus elongatus* PCC 7942 to infer a gene regulatory network (GRN). They report limited accuracy in predicting direct transcription factor-gene interactions (micro-averaged F1 = 0.11) but argue that network topology and centrality analysis reveal biologically meaningful regulatory modules coordinating day-night metabolic transitions. They identify HimA, TetR, and SrrB as potentially important but understudied regulators, alongside known global regulators RpaA and RpaB.
- **Visible evidence base** Main text figures (Figures 1–5 referenced), Methods equations (Equations 1.1–1.3, 2–7), Table 1 (referenced), Supplementary Tables S1–S12 (referenced but not provided in the submitted material)
- **Missing materials affecting confidence** All supplementary tables (S1–S12), all figures (Figures 1–5), the full list of 123 predicted TFs, the validation set details for 24 TFs, the 497 experimentally validated interactions, the Vijayan et al. (2009) circadian expression dataset, and code/parameter settings for GENIE3 and network analysis. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in systems biology: extracting regulatory insight from gene expression data when direct interaction prediction is inaccurate. The authors' pivot to network-level topology and centrality as the primary analytical lens is a reasonable and potentially valuable strategy. However, the manuscript as presented has several critical weaknesses. The central claims regarding the biological roles of HimA, TetR, and SrrB rest on network centrality metrics and community assignments that are not shown or fully described. The validation approach, while honestly reporting low F1, does not establish that the network topology itself is reliable enough to support the specific regulatory hypotheses proposed. The absence of all figures and supplementary tables in the submitted material makes it impossible to assess the evidence base directly. The writing is generally clear but the manuscript would benefit from more precise operational definitions of key terms (e.g., "day-phase regulators," "coordination") and a more explicit treatment of how circadian phase was assigned to network nodes.
- **Who would be interested in the results, and why** Researchers studying circadian regulation in cyanobacteria, particularly those interested in the regulatory architecture beyond the core KaiABC clock. The methodological framing (network centrality as a discovery tool despite low edge-level accuracy) may also interest computational biologists working on GRN inference in organisms with limited regulatory annotation. The potential implications for metabolic engineering of photosynthetic organisms could attract applied biotechnology researchers.
- **Major strengths** 1) The manuscript honestly reports the limited accuracy of direct TF-gene prediction, which is a common but often understated limitation in GRN studies. 2) The focus on network-level properties (centrality, community structure) as opposed to individual edges is a sensible and potentially more robust analytical approach. 3) The integration of circadian expression phase with network topology is a useful conceptual framework. 4) The identification of specific candidate regulators (HimA, TetR, SrrB) provides testable hypotheses for experimental validation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that network centrality analysis identifies HimA, TetR, and SrrB as "key regulators" and "potential coordinators" of day-night metabolic transitions.
  - **Evidence pointer** Results sections 3.3, 3.4, 3.5; Figures 3–5 (not provided); Supplementary Tables S8–S11 (not provided)
  - **Concern** The central biological claims of the paper rest on the identification of these three regulators as high-centrality nodes in specific day- or night-associated communities. However, the figures and supplementary tables that would show these centrality rankings, community assignments, and circadian phase associations are not included in the submitted material. Without these, the reader cannot evaluate whether the centrality differences are meaningful, whether the community assignments are robust, or whether the circadian phase associations are statistically supported. The reported Mann-Whitney U test results (Table 1, not provided) are referenced but not shown.
  - **Why it matters** The paper's primary contribution is the identification of these candidate regulators. If the supporting evidence is not visible or is weak, the central claims are unsubstantiated. The authors themselves note that direct interaction prediction is inaccurate, so the burden of proof shifts to the network-level metrics; these must be shown to be robust and meaningful.
  - **Resolution test** Provide all figures and supplementary tables. Show the distribution of centrality metrics for all TFs, with the candidate regulators highlighted. Demonstrate that the day/night community assignments are stable (e.g., via bootstrap or alternative community detection algorithms). Provide statistical support for the claim that these regulators are significantly more central than expected by chance or compared to other TFs.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** The manuscript claims that the GRN, despite low F1 for direct interactions, has a topology that "successfully revealed the organizational principles of circadian regulation."
  - **Evidence pointer** Results section 3.1; Figures 1E, 1F (not provided); Methods section 2.2
  - **Concern** The authors validate their network by showing that it "modeled the distribution of known regulatory interactions" (Figures 1E, 1F), but these figures are not provided. More importantly, the manuscript does not establish that the network topology is accurate enough to support the higher-order claims. A network with low edge-level precision could still have meaningful community structure, but this needs to be demonstrated explicitly. For example, are the day and night communities enriched for known functionally related genes beyond what would be expected by chance? Is the centrality ranking stable to perturbations in the input data or to the choice of edge cutoff? The manuscript does not report any such robustness analyses.
  - **Why it matters** The entire premise of the paper is that network-level analysis can extract meaningful biology despite poor edge-level prediction. This premise requires direct evidence that the network topology is biologically informative. Without this, the identified regulators could be artifacts of the inference method.
  - **Resolution test** Provide Figures 1E and 1F. Add robustness analyses: e.g., assess community stability under node/edge perturbation, compare centrality rankings across different edge cutoffs, or benchmark the community structure against randomized networks with the same degree distribution. Show that the day/night communities are significantly enriched for known metabolic pathways (e.g., photosynthesis, glycogen metabolism) using a proper background model.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and transparency
  - **Claim pointer** The manuscript describes a multi-source data curation effort (selongEXPRESS, 330 samples) and a multi-method TF prediction approach.
  - **Evidence pointer** Methods sections 2.1, 2.2; Supplementary Tables S1–S5 (not provided)
  - **Concern** The Methods section describes the data curation and TF prediction but lacks critical details needed for reproducibility. The specific accessions for all 330 samples are not listed in the main text (presumably in Supplementary Table S3, not provided). The criteria for "sufficient experimental metadata" are not defined. The parameters used for GEN3 (e.g., number of trees, random seed, feature selection) are not stated. The handling of batch effects or technical variation across the 330 samples from different studies is not described. The manuscript states that the GRN was reduced to 3,102 edges based on an F1-optimized cutoff, but the range of cutoffs tested and the shape of the F1 curve are not shown.
  - **Why it matters** Reproducibility is a core requirement for computational biology. Without full details on data, parameters, and analysis choices, other researchers cannot replicate or build upon this work. The lack of detail also makes it difficult to assess potential biases in the network construction.
  - **Resolution test** Provide all supplementary tables. Add a detailed Methods subsection with all software versions, parameters, and analysis scripts (or a link to a public repository). Specify the exact criteria for sample inclusion and the handling of multi-study batch effects. Show the F1 curve used to select the edge cutoff.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation and overreach
  - **Claim pointer** The manuscript states that HimA "may act as a repressor of the photosynthesis chain through modification of DNA topology" and that TetR and SrrB are "key coordinators of nighttime metabolism."
  - **Evidence pointer** Results sections 3.4, 3.5; Discussion section 4.1
  - **Concern** The functional interpretations of the candidate regulators go beyond what the network analysis can support. The claim about HimA's mechanism (DNA topology modification) is speculative and is presented with limited caveats. The manuscript does not provide any experimental evidence for these functional roles, nor does it adequately discuss alternative explanations (e.g., the centrality of these nodes could reflect indirect effects or inference artifacts). The term "key regulators" implies a causal role that is not established by correlation-based network inference.
  - **Why it matters** Overinterpretation of computational predictions can mislead the field and lead to wasted experimental effort. The manuscript should clearly distinguish between hypothesis generation and validated findings.
  - **Resolution test** Soften the language throughout the Results and Discussion to clearly frame these as hypotheses. Add a paragraph explicitly discussing alternative interpretations and the need for experimental validation. If possible, cite any existing experimental evidence for the roles of HimA, TetR, or SrrB in cyanobacteria.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "precise temporal control of metabolism significantly impacts photosynthetic efficiency and CO2-to-bioproduct conversion" is vague. It is unclear what "significantly impacts" means in this context.
  - **Required correction** Rephrase to be more specific, e.g., "circadian regulation of metabolism is known to affect photosynthetic efficiency and CO2-to-bioproduct conversion rates."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods section 2.2
  - **Evidence pointer** Methods, "Multi-method approach for gene regulatory network inference"
  - **Issue** The description of the three TF prediction methods is brief. It is unclear how the outputs of the three methods were combined into a single set of 123 TFs (e.g., union, intersection, weighted vote).
  - **Required correction** Specify the combination rule and provide the number of TFs identified by each method individually and by each pairwise overlap.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section 3.2
  - **Evidence pointer** Results, "Network centrality metrics differentiate..." (Table 1 referenced)
  - **Issue** The Mann-Whitney U test is mentioned, but the effect sizes or the actual distributions are not described. Reporting only p-values is insufficient.
  - **Required correction** Report median and interquartile ranges for centrality metrics for global vs. local TFs, and consider reporting a standardized effect size (e.g., rank-biserial correlation).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Throughout
  - **Evidence pointer** Results sections 3.4, 3.5
  - **Issue** The terms "day-phase regulators" and "night-phase regulators" are used, but the operational definition is not explicit. Is this based on the peak expression time of the TF itself, or the peak expression of its target genes?
  - **Required correction** Define these terms explicitly in the Methods or at first use in the Results.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction
  - **Evidence pointer** Introduction, paragraph 2
  - **Issue** The statement that "developing similar understanding for photosynthetic organisms remains challenging" is generic. The authors could strengthen the introduction by briefly mentioning specific prior GRN efforts in cyanobacteria and why they were limited.
  - **Required correction** Add one or two sentences citing prior GRN studies in cyanobacteria and explicitly stating the gap this work addresses.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing evidence for central claims), R1-M2 (lack of topology validation), R1-M3 (insufficient methodological detail for reproducibility)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of centrality analysis to circadian GRNs in cyanobacteria is not entirely novel, but the explicit framing of using network topology despite poor edge-level prediction is a useful perspective. The specific candidate regulators identified are new.  
  *Scientific importance*: Moderate. The work addresses a real gap in understanding secondary regulatory layers in a model cyanobacterium. However, the importance is contingent on the reliability of the network-level predictions, which is not fully established. The potential implications for metabolic engineering are stated but not developed.  
  *Interdisciplinary readership*: Limited. The manuscript is likely to appeal primarily to cyanobacterial biologists and computational biologists working on GRN inference. The broader systems biology audience may find the methodological framing interesting, but the presentation is not sufficiently general to attract a wide readership.  
  *Technical soundness*: The core computational pipeline is reasonable, but the lack of robustness analyses and the absence of key figures/tables prevent a full assessment. The statistical approach (Mann-Whitney U) is appropriate but underreported.  
  *Readability for nonspecialists*: The manuscript is generally well-written and accessible. The abstract and introduction are clear. However, the Results sections assume familiarity with network analysis terminology and cyanobacterial metabolism, which may limit accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant problem and the authors have a sensible analytical strategy. However, the central claims cannot be evaluated from the submitted material, and the lack of topology validation is a significant gap. The authors should be encouraged to resubmit after providing all supporting data, adding robustness analyses, and tempering the functional interpretations.

## Risk / unsupported claims
- The claim that HimA, TetR, and SrrB are "key regulators" of day-night metabolic transitions is unsupported without the centrality data and community assignments (Figures 3–5, Tables S8–S11).
- The claim that the network "successfully revealed the organizational principles of circadian regulation" is overstated given the low F1 score and the lack of topology validation.
- The specific mechanistic hypothesis that HimA acts via DNA topology modification is speculative and not supported by any direct evidence presented.
- The statement that the identified regulators "may inform metabolic engineering strategies" is a reasonable speculation but is not developed or supported with specific examples.
- The claim that the GRN "modeled the distribution of known regulatory interactions" (Figures 1E, 1F) cannot be assessed as the figures are not provided.