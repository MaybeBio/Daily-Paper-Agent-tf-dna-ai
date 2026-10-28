## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, conclusion, and supporting information references.
- **Assessment boundary** Technical soundness, methodological novelty, validation rigor, reproducibility, and clarity of the presented claims. No assessment of formatting or editorial policy.
- **Shared manuscript claim summary** The authors present Motif-Cluster, an open-source computational framework that extends density-based clustering to prioritize transcription factor binding clusters from sequence data alone, integrating binding affinity and gap distributions. They claim improved cluster detection and ranking over existing tools, validated through simulations and case studies on ZNF410, PHB1, TWIST1, and EGR1.
- **Visible evidence base** Abstract, full methods, results sections, figures referenced (Fig 1–6, S1–S6), tables (Table 1–3, S1–S5), and discussion. No raw data, code repository, or supplementary files were provided for direct inspection.
- **Missing materials affecting confidence** Code repository, full simulation configuration files, detailed parameter settings for external tools, raw output tables, and the actual figures and supplementary tables. These are essential for verifying reproducibility and the quantitative claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in regulatory genomics by shifting focus from individual high-affinity TF binding sites to spatially clustered motif arrays, which are increasingly recognized as functionally important. The proposed method, Motif-Cluster, is conceptually sound and integrates affinity and gap information in a flexible manner. However, the evidence provided is insufficient to fully establish the claimed advantages over existing tools. The validation relies heavily on a small number of case studies and simulations with limited quantitative rigor. The lack of accessible code and detailed benchmarking protocols prevents independent verification. The manuscript is promising but requires substantial strengthening of the validation and reproducibility aspects before the claims can be considered established.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying motif analysis tools, as well as experimental researchers studying transcriptional regulation, particularly those working with TFs lacking high-quality ChIP-seq data. The method's sequence-only approach and focus on weak motif clusters could be valuable for prioritizing candidate regulatory regions in non-model organisms or under-explored cell types.
- **Major strengths**
  1. The conceptual motivation is clear and timely, addressing a recognized limitation in motif-centric analyses.
  2. The methodological design, extending DBSCAN with affinity weighting and adaptive gap parameters, is a reasonable and flexible approach.
  3. The inclusion of simulation modules for both BED-file and genome-level benchmarking is a valuable feature for the community.
  4. The case studies cover diverse TFs with different motif properties, demonstrating potential generalizability.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation rigor
  - **Claim pointer** The manuscript claims that Motif-Cluster "successfully recovers the previously characterized binding clusters in the CHD4 promoter" and that it outperforms alternative methods in prioritizing biologically meaningful clusters.
  - **Evidence pointer** Results section, Figures 2 and 5, Table 2.
  - **Concern** The validation is based on a single well-characterized locus (CHD4) and a few additional case studies. The claim of "successful recovery" is qualitative, and the ranking of the CHD4 cluster as second among 58,606 clusters, while notable, is not statistically benchmarked against a null expectation. The comparison with alternative methods (Fig 5) is visual and lacks quantitative metrics such as precision-recall curves or enrichment against known regulatory elements. The case studies for PHB1, TWIST1, and EGR1 are descriptive and do not provide a systematic evaluation of how many true positive clusters were identified versus false positives.
  - **Why it matters** Without a rigorous, quantitative validation against a set of known regulatory regions or a clear demonstration of improved performance over existing tools, the core claim of the method's utility remains unsubstantiated. The current evidence is largely anecdotal.
  - **Resolution test** Provide a genome-wide evaluation using a set of experimentally validated TF binding clusters (e.g., from ChIP-seq or STARR-seq) for multiple TFs. Report precision-recall curves, enrichment of predicted clusters at annotated regulatory elements, and a statistical comparison of ranking performance against MCAST, Cluster-Buster, and a simple window-based approach. For the case studies, provide quantitative metrics such as the number of true positive clusters recovered, false discovery rates, and a comparison of the top-ranked clusters against known functional regions.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript claims Motif-Cluster is an "open-source framework" with "reproducible workflows."
  - **Evidence pointer** Materials and methods, Discussion.
  - **Concern** The manuscript does not provide a link to a code repository, a version number, or a detailed description of the software dependencies and installation process. The methods section describes the algorithm conceptually but lacks specific parameter values for the Gaussian mixture model, DBSCAN, and the merging step. The simulation configuration files are mentioned but not shown. This makes it impossible for a reader to reproduce the results or apply the method to their own data.
  - **Why it matters** Reproducibility is a cornerstone of computational biology. The lack of accessible code and detailed parameters undermines the manuscript's contribution and prevents the community from using or building upon the method.
  - **Resolution test** Provide a public repository (e.g., GitHub) with the full source code, a detailed README, installation instructions, and example data. Include all parameter settings used in the manuscript's analyses, and provide the simulation configuration files as supplementary data. Ideally, provide a containerized version (e.g., Docker) for easy execution.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness of benchmarking
  - **Claim pointer** The manuscript claims that in simulation case A, Motif-Cluster achieved an average precision of 92.53% and recall of 84.95%, and that in simulation case B, it maintained the best balance between precision and recall compared to MCAST and Cluster-Buster.
  - **Evidence pointer** Results section, "Comparison with existing Motif Cluster tools", Tables S4 and S5.
  - **Concern** The benchmarking protocol is not fully described. The method for generating synthetic genomes, the number of simulation replicates, and the criteria for defining a "true" cluster match are not specified. The statement that "we attempted to optimize parameters across all methods to minimize differences introduced during motif calling" is vague and raises concerns about potential bias. The comparison is not entirely fair because each tool uses different internal motif scanning, which is acknowledged but not addressed quantitatively.
  - **Why it matters** The reported performance metrics are central to the claim of superiority. If the benchmarking is not rigorous and unbiased, the quantitative results are not trustworthy.
  - **Resolution test** Provide a detailed benchmarking protocol, including the exact simulation parameters, the number of replicates, and the matching criteria. Use a standardized set of motif scanning results (e.g., pre-computed FIMO output) as input to all tools to isolate the clustering performance. Report performance metrics with confidence intervals across multiple simulation runs. Consider using a third-party benchmark dataset for a more objective comparison.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The manuscript claims that the "top 20 significant regions in the high-affinity result (p < 0.001) are well-preserved overall" under increased noise levels.
  - **Evidence pointer** Results section, "Noise level tolerance testing", Figure 4.
  - **Concern** The analysis of noise tolerance is descriptive. The overlap of 7/20 and 9/20 between different thresholds is presented without any statistical significance testing. It is unclear whether this overlap is better than what would be expected by chance. The choice of thresholds (p < 0.001, 0.005, 0.01) is arbitrary, and the impact on the final cluster rankings is not systematically quantified.
  - **Why it matters** The robustness of the method to noise is a key selling point, but the current analysis does not provide a statistical basis for this claim.
  - **Resolution test** Perform a permutation test to assess whether the overlap between top-ranked clusters under different thresholds is significantly higher than expected by chance. Report the distribution of overlap scores under a null model. Additionally, quantify the stability of cluster boundaries and scores as a function of the p-value threshold.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Score and rank" section
  - **Evidence pointer** Formula (1) and (2)
  - **Issue** The formulas are presented without a clear definition of all variables. For example, the notation for the mean affinity and the empirical distribution is not fully explained. The text mentions "formula (1)" and "formula (2)" but the equations themselves are not shown in the provided text.
  - **Required correction** Provide the full equations with a clear definition of each symbol. Explain how the empirical distribution f(I|Gi) is constructed and how the final score is normalized or compared across clusters.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results, "More cases" section
  - **Evidence pointer** Figure 6
  - **Issue** The case studies for PHB1, EGR1, and TWIST1 are presented as evidence of general applicability, but the criteria for selecting these specific loci and the significance of the identified clusters are not discussed. For example, the PHB1 analysis identifies clusters near the AXIN1 TSS, but it is unclear how many other clusters were found genome-wide and what the false positive rate might be.
  - **Required correction** Provide a more systematic description of the case study results, including the total number of clusters identified, the ranking of the highlighted loci, and a discussion of how the results compare to what would be expected by chance.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of future work mentions "combinatorial multi-transcription-factor clustering analysis" but does not elaborate on how this might be achieved or what challenges exist.
  - **Required correction** Expand this point briefly to give readers a sense of the potential extensions and limitations of the current framework.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, "Cluster and merge" section
  - **Evidence pointer** Table 1
  - **Issue** The choice of ten Gaussian components is justified by AIC/BIC, but the sensitivity of the final results to this number is not explored. It is unclear if the clustering results are robust to this choice.
  - **Required correction** Add a sensitivity analysis showing how the number of clusters and their rankings change when the number of Gaussian components is varied (e.g., 5, 10, 15).
- **Technical failings that need to be addressed before the case is established**
  1. Lack of accessible code and detailed parameter settings (R1-M2).
  2. Insufficient quantitative validation against known regulatory regions (R1-M1).
  3. Incomplete description of the benchmarking protocol, leading to potential bias (R1-M3).
  4. Absence of statistical testing for robustness claims (R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** The idea of prioritizing clustered, weak TF binding sites is not entirely new, but the specific integration of affinity-weighted DBSCAN with Gaussian mixture gap modeling is a novel combination. The simulation modules are a useful addition. However, the conceptual advance over existing tools is incremental rather than transformative.
  - **Scientific importance** The problem addressed is important, as many TFs lack high-quality experimental binding data, and sequence-based prioritization of regulatory regions could have broad utility. However, the importance is not fully demonstrated by the current validation, which is limited in scope.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The potential appeal to experimental biologists is mentioned but not strongly supported by the case studies, which are not presented in a way that would guide experimental design.
  - **Technical soundness** The algorithmic approach is reasonable, but the technical soundness is undermined by the lack of rigorous benchmarking and statistical analysis. The reproducibility issues are a major concern.
  - **Readability for nonspecialists** The manuscript is generally well-written and the concepts are explained clearly. However, the methods section assumes familiarity with DBSCAN and Gaussian mixture models, which may be a barrier for some readers. The figures are referenced but not visible in the provided text, making it difficult to assess their clarity.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising method, but the core claims of improved performance and general applicability are not sufficiently supported by the available data. The lack of code and detailed benchmarking protocols is a critical barrier. I would be supportive if the authors address the major concerns, particularly by providing a rigorous, quantitative validation and making the code and parameters fully accessible.

## Risk / unsupported claims
- The claim that Motif-Cluster "successfully recovers" the CHD4 promoter cluster is based on a single example and is not statistically benchmarked.
- The claim of "general applicability" based on the PHB1, TWIST1, and EGR1 case studies is not supported by a systematic evaluation of false positive rates or comparison to a null model.
- The quantitative performance metrics from the simulations (precision, recall) are presented without a detailed protocol, making them unverifiable.
- The statement that Motif-Cluster "offers a robust and flexible approach" is a general assertion not backed by a comprehensive sensitivity analysis or comparison to a wider range of existing tools.