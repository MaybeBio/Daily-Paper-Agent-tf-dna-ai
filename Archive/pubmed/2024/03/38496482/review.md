## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Methodological soundness, benchmark design, evidence quality, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark computational methods for identifying differentially-active transcription factors from ATAC-seq data, using curated perturbation datasets and semi-simulations, and identify three top-performing approaches. They also apply these methods to a novel TRAFTAC experiment targeting NFkB.
- **Visible evidence base** Text descriptions of benchmark results (Figs 1-6 referenced), method descriptions, simulation procedures, and one application experiment
- **Missing materials affecting confidence** All figures, tables (including Table 1 and 2), supplementary figures and tables, code repository contents, and detailed numerical results

## Reviewer
- **Overall assessment** This manuscript addresses a timely and practically important question in epigenomics: how to reliably infer differentially-active transcription factors from ATAC-seq data. The authors have assembled a substantial benchmark effort combining real perturbation datasets with semi-simulations, and their findings offer practical guidance for the field. The work is generally well-structured and the methodological variations are thoughtfully explored. However, the absence of all figures and tables in the provided material severely limits the ability to verify the quantitative claims, assess the statistical rigor of the benchmark, or evaluate the quality of the application example. Several methodological choices require clarification, particularly regarding the handling of motif redundancy, the interpretation of the network score, and the treatment of multiple testing across the large number of motifs tested.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those analyzing ATAC-seq or similar chromatin accessibility data. Practitioners seeking guidance on which TF activity inference tool to use for their specific datasets would find the benchmark comparisons and practical recommendations directly useful. The TRAFTAC application also targets researchers in chemical biology and epigenome engineering.
- **Major strengths** The benchmark design is thoughtful, combining real perturbation datasets with controlled semi-simulations to address the lack of ground truth. The inclusion of both specialized and repurposed methods provides a comprehensive comparison. The exploration of methodological variations (e.g., normalization strategies, motif matching thresholds) adds practical value. The authors are transparent about limitations, such as the ambiguity of ground truth in real datasets and the assumption that binding changes correspond to accessibility changes.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (network score validity), R1-M2 (multiple testing control), R1-M3 (TRAFTAC interpretation), R1-M4 (simulation realism)
- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The question of benchmarking TF activity inference methods is not entirely new, and a related study is acknowledged. However, the specific combination of real perturbation datasets, semi-simulations, and the systematic exploration of methodological variations provides a useful and somewhat distinctive contribution.
  - **Scientific importance**: High. ATAC-seq is widely used, and the choice of method for TF activity inference can substantially affect biological conclusions. A rigorous benchmark with clear recommendations has the potential to influence standard practice in the field.
  - **Interdisciplinary readership**: Moderate. The topic is primarily of interest to computational biologists and epigenomics researchers. The TRAFTAC application may broaden appeal to chemical biology, but the core content is specialized.
  - **Technical soundness**: Cannot be fully assessed from the provided text alone. The methodological descriptions are plausible, but the absence of figures and tables prevents verification of the quantitative results and the statistical rigor of the benchmark.
  - **Readability for nonspecialists**: The manuscript is clearly written and the concepts are explained well. However, the density of method names and variations may be challenging for readers outside the immediate field. The abstract and introduction are accessible, but the results and methods sections assume familiarity with the tools and concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is important, the benchmark design is thoughtful, and the findings are potentially valuable. However, the current evidence base (text only) is insufficient to fully establish the validity of the claims. The authors must provide the missing figures and tables, address the methodological concerns raised, and clarify the statistical handling of multiple comparisons.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that the "network score" is a valid metric for evaluating method performance, based on ranking known physical interactors of the perturbed TF.
- **Evidence pointer** Methods section "Benchmark metrics"; Figure 1 (middle panel)
- **Concern** The network score assumes that physical interactors of the perturbed TF should also show differential activity. This is a strong assumption that may not hold universally. For example, a TF could be perturbed without affecting the activity of its binding partners, or the interactors could be constitutively active. The authors do not provide a justification for this assumption, nor do they validate the network score against an independent ground truth. The score's validity is critical because it is used as a primary evaluation metric in Figure 1.
- **Why it matters** If the network score is not a reliable proxy for true differential activity, the ranking of methods based on this metric could be misleading, undermining the central conclusions of the benchmark.
- **Resolution test** The authors should provide a rationale for the network score, ideally with a sensitivity analysis showing that results are robust to the choice of interactor database or to the definition of "interactor." They could also compare the network score against the rank of the true motif in a subset of datasets where the ground truth is more certain.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report precision and recall values for each method, using an adjusted p-value threshold of 0.05.
- **Evidence pointer** Methods section "Benchmark metrics"; Figure 2A
- **Concern** The manuscript does not describe how multiple testing is controlled across the large number of motifs tested (likely thousands). The text mentions "adjusted p-value" but does not specify the correction method (e.g., Benjamini-Hochberg, Bonferroni). This is a critical detail, as the number of tests directly affects the false discovery rate and the comparability of precision across methods. Furthermore, the precision calculation considers "all motifs clustering with the true TF or its known interactors" as true positives, which is a broad definition that could inflate precision estimates.
- **Why it matters** Without proper multiple testing control, the reported precision and recall values may not be reliable, and the comparison between methods could be biased. The definition of true positives also affects the interpretation of the results.
- **Resolution test** The authors should specify the multiple testing correction method used and justify its choice. They should also provide a sensitivity analysis using different definitions of true positives (e.g., only the true motif, or motifs with a certain sequence similarity threshold).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that the TRAFTAC experiment shows "the strongest signal is in motifs related to the AP-1 complex, i.e. JUN/FOS family members... showing a decreased accessibility in the knockdown."
- **Evidence pointer** Results section "Application of the methods to characterize TRAFTAC-mediated TF degradation"; Figure 5
- **Concern** The interpretation of the TRAFTAC experiment is presented as a key application of the benchmarked methods, but the biological conclusion is not well-supported. The authors note that NFkB motif matches show only a "weak trend" of decreased accessibility, which is not significant. Instead, they highlight AP-1 motifs, which are not the direct target of the TRAFTAC. The proposed explanation of "cross-talk" is speculative and not backed by any additional experimental validation. The lack of a significant direct effect on the intended target (NFkB) raises questions about the efficacy of the perturbation or the sensitivity of the methods in this context.
- **Why it matters** The TRAFTAC experiment is presented as a demonstration of the practical utility of the methods. If the primary intended target is not detected, the example may not effectively illustrate the methods' value, and the biological interpretation could be overreaching.
- **Resolution test** The authors should provide a more detailed analysis of the TRAFTAC experiment, including the overall quality of the ATAC-seq data, the number of differentially accessible peaks, and a discussion of why the direct target was not significantly detected. They should also temper the claims about AP-1 cross-talk or provide additional evidence to support it.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the semi-simulations "confirm the main results of the benchmark on real datasets."
- **Evidence pointer** Results section "Semi-simulations confirm the results from real benchmark datasets"; Figure 4
- **Concern** The semi-simulation procedure is a valuable addition, but its realism is limited by the assumption that changes in binding are associated with corresponding changes in accessibility. The authors acknowledge this, but the impact of this assumption on the benchmark results is not fully explored. For example, if a TF binds but does not open chromatin, the simulation would not capture this. The simulation also relies on ChIP-seq peaks as the ground truth, which may not be available for all TFs of interest.
- **Why it matters** The semi-simulations are used to confirm the findings from real datasets. If the simulation procedure is biased, it could provide false confidence in the benchmark results.
- **Resolution test** The authors should discuss the limitations of the simulation procedure more thoroughly and ideally provide a sensitivity analysis, for example by varying the relationship between binding and accessibility changes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Benchmark metrics"
- **Evidence pointer** Text description of the ranking procedure
- **Issue** The description of how methods are ranked in Figure 1 is somewhat unclear. The text mentions "we transformed the ranks of the true motif using an inverse-logit-based transformation" but does not clearly explain the rationale for this transformation or how the final ranking is computed.
- **Required correction** Provide a clearer explanation of the ranking procedure, including the formula and the rationale for the transformation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Datasets preprocessing"
- **Evidence pointer** Text description of the TRAFTAC experiment
- **Issue** The description of the TRAFTAC experiment is brief, and some details are missing, such as the number of replicates, the concentration of the TRAFTAC, and the time point of the ATAC-seq assay.
- **Required correction** Provide more experimental details to allow others to reproduce the experiment.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Application of the methods to characterize TRAFTAC-mediated TF degradation"
- **Evidence pointer** Figure 5C
- **Issue** The text mentions "some example significant motifs across the top three methods" but does not clearly explain how these examples were selected or what the reader should take away from them.
- **Required correction** Clarify the selection criteria for the example motifs and explain the key observations from Figure 5C.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Text description of the comparison with a related study
- **Issue** The discussion of the related study by Santana et al. is brief and does not fully explore the similarities and differences in findings. A more detailed comparison would help readers understand the broader context.
- **Required correction** Expand the discussion of the related study, highlighting specific points of agreement and disagreement.

## Risk / unsupported claims
- The claim that the "network score" is a valid evaluation metric is not fully supported by the provided text.
- The claim that the TRAFTAC experiment reveals a role for AP-1 cross-talk is speculative and not directly supported by the data presented.
- The claim that the semi-simulations "confirm" the real dataset results is weakened by the acknowledged assumption that binding changes correspond to accessibility changes.
- The overall performance rankings of the methods cannot be independently verified without the figures and tables.
- The precision and recall values cannot be assessed for statistical rigor without details on multiple testing correction.