## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, perspective, methods, and supplemental material descriptions
- **Assessment boundary** Scientific content, methodological rigor, claims versus evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors survey histone-like sequences across all available archaeal genomes, group them into five clusters based on physical properties, identify seven genomic strategies for histone usage, and use AlphaFold3 predictions and molecular dynamics simulations to infer DNA-binding and oligomerization behavior
- **Visible evidence base** Main text figures 1-5 (referenced), supplemental figures 1-9, supplemental tables 1-2, methods descriptions, and data availability statements
- **Missing materials affecting confidence** Actual figure images and supplemental files were not provided; only figure legends and text descriptions were available for assessment

## Reviewer

- **Overall assessment** This manuscript presents a broad bioinformatic survey of archaeal histone diversity, which addresses a genuine gap in the field. The identification of five clusters and seven strategies provides a useful organizational framework. However, the central claims regarding structural predictions and DNA-binding behavior rest on computational methods that the authors themselves acknowledge have limitations. The correlation analyses with environmental pressures are presented with appropriate caution, but the mechanistic interpretations remain speculative. The work is primarily descriptive and taxonomic in nature, and the path from these predictions to experimentally validated insights is not yet established. The manuscript would benefit from clearer articulation of what is genuinely novel versus what consolidates existing knowledge, and from a more rigorous treatment of the limitations of the computational pipeline.

- **Who would be interested in the results, and why** Researchers studying archaeal chromatin organization, histone evolution, and the origins of eukaryotic chromatin would find this survey useful as a reference resource. The classification scheme and the identification of understudied histone variants could guide future experimental work. The paper may also interest computational biologists developing pipelines for protein family classification and structure prediction in diverse sequence space. However, the audience is likely to be specialized rather than broad, given the descriptive nature of the findings and the absence of experimental validation.

- **Major Strengths**
  - The survey covers a large and comprehensive dataset of 5,869 archaeal genomes, providing a broad taxonomic sampling
  - The clustering approach based on physical properties rather than sequence identity alone is a thoughtful methodological choice that captures functional diversity
  - The identification of acidic histones as a major category is an important observation that challenges the assumption that histones are predominantly basic
  - The authors are appropriately cautious about the limitations of AlphaFold3 predictions, acknowledging that computational models require experimental verification
  - The framework of seven strategies provides a useful heuristic for organizing the diversity of histone usage across archaea

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that five distinct clusters of archaeal histones exist based on physical properties (length, pI, hydrophobicity, instability index) and that these clusters represent biologically meaningful categories
- **Evidence pointer** Figure 1, Supplemental Figure 1, Supplemental Table 1, Methods (DBSCAN clustering)
- **Concern** The clustering methodology relies on DBSCAN with parameters optimized for a silhouette score of 0.25, which is generally considered a weak clustering structure. The authors do not provide sufficient validation that these clusters are robust to parameter choices, dataset composition, or the inclusion of additional physical properties. The choice of four parameters (length, pI, GRAVY, helical propensity) is justified by variance, but the biological relevance of these particular parameters for defining functional histone categories is not established. Furthermore, the use of a single silhouette score threshold without reporting the distribution of silhouette scores across clusters leaves uncertainty about whether some clusters are much better defined than others.
- **Why it matters** The entire classification framework, and all subsequent analyses of strategies and correlations, depends on the validity of these clusters. If the clustering is not robust, the derived strategies and their inferred biological significance may be artifacts of the specific computational choices made.
- **Resolution test** Provide robustness analyses showing cluster stability across different parameter values, subsampling of the dataset, and alternative clustering algorithms. Report silhouette scores for individual clusters. Validate that cluster assignments correlate with independent sequence-based phylogenetic groupings or structural features.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that specific environmental pressures correlate with specific histone strategies, particularly the association of combination 3&4 with halophilic environments
- **Evidence pointer** Figure 4, Supplemental Table 2, Supplemental Figure 4, Methods (Metadata correlation)
- **Concern** The correlation analysis between environmental pressures and histone strategies is based on manually coded keywords from sampling location annotations. This approach is inherently subjective and prone to misclassification. The statistical testing uses the Shapiro test, which is a test for normality, not a test for association between categorical strategy assignments and environmental variables. The appropriate statistical framework for testing associations between categorical groupings and environmental metadata is not described. Additionally, the authors acknowledge that these parameters are difficult to verify, but the analysis is still presented as supporting a correlation claim.
- **Why it matters** The claim that environmental pressures shape histone strategy selection is one of the more biologically interesting findings, but if the statistical basis is flawed, the conclusion is not supported. This weakens the evolutionary narrative the authors wish to advance.
- **Resolution test** Use appropriate statistical tests for categorical associations (e.g., chi-square, Fisher exact test, or logistic regression) with correction for phylogenetic non-independence. Provide a clear description of how environmental categories were assigned and validated. Report effect sizes and confidence intervals, not just p-values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that AlphaFold3 predictions and molecular dynamics simulations demonstrate that most histone classes form stable complexes with DNA, and that specific strategies produce nucleosome-like structures
- **Evidence pointer** Figure 5, Supplemental Figures 7-9, Methods (Structural prediction, Molecular dynamics simulations)
- **Concern** The authors acknowledge that AlphaFold3 predictions have limitations, but the presentation of the simulation results as evidence of "stable" DNA binding is problematic. The molecular dynamics simulations were run for 100 ns, which is relatively short for assessing the stability of large nucleosome-like assemblies. The authors do not report convergence metrics, replicate variability, or whether the simulations reached equilibrium. The "tug" step used to relax the models before simulation is a non-standard approach that could introduce artifacts. The claim that acidic histones maintain a "basic putative DNA binding ridge" is inferred from structural models without experimental validation. The authors also note that simulations at high ionic strength (2 M KCl) produced different results, but these are not shown in the main text.
- **Why it matters** The structural predictions and simulations are the primary evidence for the functional claims of the paper. If the computational methods are not rigorously validated, the conclusions about which histone classes can bind DNA and form nucleosome-like structures are not reliable.
- **Resolution test** Provide detailed simulation validation including root-mean-square deviation and fluctuation analyses, convergence assessment, and replicate reproducibility. Show the high ionic strength simulations in the main text. Compare predictions against known experimental structures where available. Clearly distinguish between predictions that are consistent with experimental data and those that are novel and untested.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The claim that this work provides a comprehensive guide to survey diverse strategies for histone-based DNA organization in archaea
- **Evidence pointer** Discussion, Perspective
- **Concern** While the survey is broad, the conceptual framework of classifying histones by physical properties and genomic strategies is not entirely novel. Previous studies have noted the diversity of archaeal histones, the presence of acidic variants, and the existence of multiple histone genes in single genomes. The authors do not clearly articulate what is genuinely new about their classification scheme compared to existing phylogenetic or sequence-based classifications. The claim of providing a "guide" is somewhat overstated given that the experimental validation of the predicted structures and functions is not provided.
- **Why it matters** For a Nature-style publication, the work needs to demonstrate a clear advance over existing knowledge. If the classification is largely confirmatory of known diversity patterns, the novelty claim is weakened.
- **Resolution test** Clearly state what is new about the five-cluster classification compared to existing schemes. Provide a quantitative comparison with previous classification approaches. Demonstrate that the new classification captures features that previous approaches missed.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, Results
- **Evidence pointer** Location not provided
- **Issue** The manuscript assumes significant familiarity with histone biology and archaeal taxonomy. Terms such as "hypernucleosome," "four-helix bundle," and "salt-in strategy" are used without adequate definition for a general scientific audience.
- **Required correction** Provide brief definitions or explanatory context for specialized terms when first introduced. Consider adding a schematic figure illustrating the different histone strategies.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Molecular dynamics simulations
- **Evidence pointer** Location not provided
- **Issue** The methods describe simulations in 2 M KCl as producing different results, but these are not shown. The choice of ionic conditions for the standard simulations is not justified relative to the physiological conditions of the organisms being modeled.
- **Required correction** Show the high ionic strength simulation results or explain why they are not included. Justify the choice of ionic conditions for the standard simulations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Results, Selective pressures
- **Evidence pointer** Figure 4
- **Issue** The correlation between genome size, GC content, and coding density with histone strategies is presented, but the biological interpretation of these correlations is limited. The authors note that increased GC content is associated with halophiles, but do not explore whether this is a direct consequence of the histone strategy or a general feature of halophilic genomes.
- **Required correction** Provide a more nuanced discussion of whether the observed correlations are specific to histone strategies or reflect broader genomic adaptations to environmental conditions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion of the "basic ridge" as a DNA binding surface is presented as a general feature, but the evidence for this is based on structural predictions of a limited number of representatives. The generalization to all clusters may be premature.
- **Required correction** Clarify the extent to which the "basic ridge" observation is based on the specific representatives analyzed versus a general feature of all histones in each cluster.

- **Technical failings that need to be addressed before the case is established**
  - The statistical analysis for environmental correlations uses an inappropriate test (Shapiro test) for the claimed associations
  - The clustering validation is insufficient to establish the robustness of the five-cluster classification
  - The molecular dynamics simulations lack standard validation metrics and the high ionic strength results are not shown
  - The manuscript does not provide a clear comparison with existing classification schemes for archaeal histones

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The survey is broad and the classification scheme is useful, but the conceptual framework is not entirely novel. The authors do not clearly demonstrate what is new compared to existing classifications of archaeal histone diversity.
  - **Scientific importance** Moderate. The work provides a useful reference resource for the field, but the lack of experimental validation limits the significance of the functional claims. The correlations with environmental pressures are suggestive but not rigorously established.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to researchers in archaeal biology, chromatin structure, and evolutionary genomics. The computational methods are standard and the findings are unlikely to attract broad interdisciplinary attention.
  - **Technical soundness** The computational pipeline is generally reasonable, but the clustering validation, statistical analysis, and simulation methodology have weaknesses that need to be addressed. The authors are appropriately cautious about AlphaFold3 limitations, but the presentation of simulation results as evidence of stability is not fully justified.
  - **Readability for nonspecialists** The manuscript is written for a specialized audience and would benefit from clearer definitions of key terms and concepts. The structure is logical, but the density of specialized terminology may limit accessibility.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a useful survey and classification framework, but the central claims regarding environmental correlations and structural predictions require stronger methodological support. The work would be more suitable for a specialized journal in microbiology or chromatin biology rather than a broad-impact journal, unless the authors can substantially strengthen the validation of their computational pipeline and clearly articulate the novel conceptual advances.

## Risk / unsupported claims
- The claim that specific environmental pressures correlate with specific histone strategies is not supported by the statistical analysis described
- The claim that most histone classes form stable complexes with DNA is based on short simulations of computationally predicted structures without experimental validation
- The claim that cluster 5 histones "might not function in genome organization" is speculative and not directly tested
- The generalization that acidic histones maintain a "basic putative DNA binding ridge" is based on a limited number of structural predictions
- The claim that the work provides a "guide" for future studies is reasonable, but the practical utility of the classification scheme is not demonstrated with concrete examples
- The percentage of archaeal genomes encoding histones (67%) is presented as a key finding, but the sensitivity of this estimate to the search strategy and thresholds used is not fully explored