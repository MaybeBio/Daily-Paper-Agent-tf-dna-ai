## Review setup
- **Input scope** Full manuscript text including main text and supplementary materials
- **Assessment boundary** Statistical methodology, computational implementation, simulation study design, real data application, and biological interpretation
- **Shared manuscript claim summary** The authors propose a novel tree-based kernel for density estimation that incorporates a sparse covariance structure on splitting probabilities, enabling flexible within-cluster dependence. They embed this kernel in a Dirichlet process mixture model for clustering density-valued data and demonstrate its utility on simulated data and DNase-seq footprint profiles from ENCODE.
- **Visible evidence base** Main text Sections 1-6, Tables 1-2, Figures 1-5, Supplementary Sections S1-S4, Table S1-S2, Figures S1-S4
- **Missing materials affecting confidence** Code repository not reviewed; raw data not available; detailed algorithmic pseudocode for Gibbs sampler not fully specified in main text; convergence diagnostics beyond traceplots not provided

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in Bayesian nonparametrics: constructing density-valued kernels with flexible covariance structures for clustering applications. The proposed Cor-tree model is a meaningful extension of existing tree-based approaches, and the application to DNase-seq footprint clustering is timely and relevant. However, several technical aspects require clarification and strengthening before the methodological contribution is fully established. The simulation study is somewhat limited in scope, and the real data analysis would benefit from more rigorous validation and comparison.
- **Who would be interested in the results, and why** Researchers in Bayesian nonparametrics, particularly those working on density estimation and clustering; computational statisticians interested in scalable MCMC for structured models; bioinformaticians and genomicists studying transcription factor binding and chromatin accessibility. The methodological framework could also appeal to statisticians working on functional data analysis and random measures.
- **Major strengths** The problem is well-motivated and the proposed model is a natural extension of existing tree-based approaches. The use of a sparse covariance prior on splitting probabilities is a clever way to introduce flexibility while maintaining computational tractability. The application to DNase-seq data is practically relevant, and the authors demonstrate improved clustering accuracy relative to several benchmarks. The R package implementation is a valuable contribution to the community.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the proposed model "allows within-group covariance to deviate from the fixed structure imposed by a dyadic tree based on empirical evidence attained from the data" (Section 1, paragraph 5).
  - **Evidence pointer** Section 2.2, Definition 2, Equation (1)
  - **Concern** The manuscript does not provide a clear theoretical justification for why the sparse covariance prior on the logit-transformed splitting probabilities leads to meaningful and identifiable covariance structures. The relationship between the covariance of splitting probabilities and the resulting covariance of the density functions is not formally established. The authors state that the model "can accommodate a variety of covariances" but do not characterize the class of achievable covariance functions. This is a critical gap, as the identifiability of the covariance structure is essential for the interpretability of the clustering results.
  - **Why it matters** Without a formal characterization of the achievable covariance structures, it is unclear whether the model can truly capture the long-range dependencies claimed to be important for TF footprint profiles. The identifiability issue also raises concerns about whether the posterior distribution of the covariance is well-behaved and whether the MCMC algorithm can reliably explore the parameter space.
  - **Resolution test** The authors should provide a theoretical analysis of the mapping between the covariance of splitting probabilities and the covariance of the induced density functions. This could include a characterization of the class of covariance functions achievable under the proposed prior, or at minimum, a discussion of identifiability conditions. Alternatively, a simulation study specifically designed to assess the recovery of known covariance structures would provide empirical evidence.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "Bayesian inference for latent variable models using this kernel can proceed with Gibbs sampling using Pólya-Gamma augmentation" (Abstract).
  - **Evidence pointer** Section 3, Supplementary Section S2
  - **Concern** The computational section is underdeveloped. The manuscript does not provide a detailed description of the Gibbs sampling algorithm, including the full conditional distributions for all parameters, the handling of the sparse covariance prior, and the computational complexity of each update. The convergence assessment is limited to traceplots of the mixing weights, which is insufficient for a model of this complexity. The authors do not discuss potential issues with MCMC mixing, label switching, or the choice of the number of clusters in the Dirichlet process mixture.
  - **Why it matters** The practical utility of the proposed method depends critically on the reliability and efficiency of the computational algorithm. Without a thorough description of the algorithm and convergence diagnostics, it is difficult for readers to assess whether the reported results are trustworthy or to implement the method themselves.
  - **Resolution test** The authors should provide a complete algorithmic description, including all full conditional distributions and the computational complexity. They should also report additional convergence diagnostics, such as effective sample sizes, multiple chains with different initializations, and posterior predictive checks. A discussion of the sensitivity of the results to the number of MCMC iterations and the choice of hyperparameters would also be valuable.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors claim that the application to DNase-seq data "results in biologically meaningful clusters corresponding to binding events of two common TFs" (Abstract).
  - **Evidence pointer** Section 5, Figures 4-5, Table 2
  - **Concern** The real data analysis is presented as a key contribution, but the validation is limited. The authors compare clustering results to ChIP-seq data, which is a reasonable reference, but the analysis is somewhat superficial. The authors do not provide a detailed biological interpretation of the clusters beyond noting that one cluster shows a bimodal pattern. The comparison with competing methods is based on a single metric (ARI), and the authors do not discuss the sensitivity of the results to the choice of preprocessing steps or the number of clusters.
  - **Why it matters** The biological relevance of the clustering results is a central claim of the manuscript. A more thorough validation, including a detailed analysis of the biological characteristics of the identified clusters and a more comprehensive comparison with existing methods, would strengthen the case for the practical utility of the proposed approach.
  - **Resolution test** The authors should provide a more detailed biological analysis of the clusters, including motif enrichment analysis, comparison with known TF binding sites, and functional annotation. They should also report results for a range of cluster numbers and discuss the stability of the clustering solution. A comparison with additional state-of-the-art methods, such as CENTIPEDE with different parameter settings, would also be informative.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the cor-tree model uses the first 4 layers' splitting variables to be included in the covariance structure" (Section 4, paragraph 3).
  - **Evidence pointer** Section 4, Section 5.2
  - **Concern** The choice of the number of correlated layers (L) is not justified. The authors use L=4 in the simulation study and L=4 for REST and L=3 for NRF1 in the real data analysis, but no sensitivity analysis is provided for this key parameter. The choice of L determines the complexity of the covariance structure and could have a significant impact on the clustering results.
  - **Why it matters** The number of correlated layers is a critical tuning parameter that controls the flexibility of the model. Without a principled approach for selecting L, the method may be sensitive to this choice, and the reported results may not be representative of the method's performance in general.
  - **Resolution test** The authors should provide a sensitivity analysis for the choice of L, showing how the clustering results vary with different values. They could also propose a data-driven approach for selecting L, such as using a model selection criterion or a prior distribution on L.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 2.1, Figure 1
  - **Evidence pointer** Figure 1(a), Figure 2(a)
  - **Issue** The description of the dyadic tree construction is somewhat abstract and could benefit from a more concrete example. The notation is dense and may be difficult for non-specialists to follow.
  - **Required correction** Consider adding a simple worked example with a small number of layers to illustrate the tree construction and the meaning of the splitting probabilities. This would improve accessibility for readers unfamiliar with tree-based density estimation.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 3, Equation (3)
  - **Evidence pointer** Section 3, Equation (3)
  - **Issue** The definition of the CENTIPEDE model in Equation (3) is incomplete. The notation is not fully explained, and the relationship to the original CENTIPEDE paper is not clear.
  - **Required correction** Provide a more complete description of the CENTIPEDE model, including the definition of all variables and the likelihood function. A reference to the original paper should be included.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 5.2, Figure 4
  - **Evidence pointer** Figure 4
  - **Issue** The figure captions are not sufficiently detailed. It is unclear what the different panels represent and how the clustering results are visualized.
  - **Required correction** Expand the figure captions to clearly describe the content of each panel, the color scheme, and the interpretation of the results.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 4, Table 1
  - **Evidence pointer** Table 1
  - **Issue** The simulation study is limited to a single scenario with two clusters. The authors do not explore the performance of the method under different numbers of clusters, different levels of separation between clusters, or different covariance structures.
  - **Required correction** Consider adding additional simulation scenarios to assess the robustness of the method. This would provide a more comprehensive evaluation of the proposed approach.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 6, Discussion
  - **Evidence pointer** Section 6
  - **Issue** The discussion of limitations is brief and does not address some important practical considerations, such as the computational cost of the method for large datasets or the sensitivity to the choice of prior hyperparameters.
  - **Required correction** Expand the discussion to include a more thorough treatment of limitations and potential directions for future work.

- **Technical failings that need to be addressed before the case is established** R1-M1 (identifiability of covariance structure), R1-M2 (incomplete computational details and convergence assessment)
- **Assessment against Nature-style criteria**
  - **Originality** The proposed model is a novel combination of tree-based density estimation with sparse covariance priors. While the individual components are known, their integration into a clustering framework for density-valued data is original. However, the theoretical contribution is limited, and the manuscript does not fully explore the implications of the proposed covariance structure.
  - **Scientific importance** The problem of clustering density-valued data with flexible dependence structures is relevant across many scientific domains. The application to DNase-seq footprint analysis addresses a real biological question. However, the demonstrated advantages over existing methods are modest, and the biological insights are not deeply explored.
  - **Interdisciplinary readership** The manuscript is likely to appeal to statisticians and computational biologists. The writing is generally clear, but the technical sections may be challenging for non-specialists. The biological application is well-motivated but could be presented more accessibly.
  - **Technical soundness** The core methodological idea is sound, but the manuscript has significant gaps in the theoretical justification and computational details. The simulation study is limited, and the real data analysis would benefit from more rigorous validation.
  - **Readability for nonspecialists** The introduction and biological background are accessible, but the model description and computational sections are dense. The manuscript would benefit from additional examples and clearer explanations of the key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem and presents a promising approach, but the current version does not fully establish the methodological contribution. The authors should address the concerns regarding identifiability, computational details, and validation before the case is fully made.

## Risk / unsupported claims
- The claim that the model "can accommodate a variety of covariances" is not formally supported by theoretical analysis or comprehensive simulation studies.
- The claim that the clustering results are "biologically meaningful" is based on limited validation and would benefit from more detailed biological analysis.
- The claim that the method "substantially outperforms" existing approaches is based on a limited set of simulation scenarios and a single real data application.
- The sensitivity of the results to the choice of the number of correlated layers (L) is not assessed, making it difficult to evaluate the robustness of the method.
- The convergence of the MCMC algorithm is only assessed through traceplots of the mixing weights, which is insufficient for a model of this complexity.