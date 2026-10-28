## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplemental figure/table legends
- **Assessment boundary** Scientific claims, methodological rigor, reproducibility, and interpretation of results as presented in the manuscript
- **Shared manuscript claim summary** The authors infer a 17-node transcription factor regulatory network from public melanoma datasets and use RACIPE simulations to show that its dynamics produce multiple attractor states corresponding to known melanoma phenotypes, recapitulate proliferative-invasive heterogeneity, and predict a dedifferentiation trajectory upon BRAF inhibition.
- **Visible evidence base** Main text Figures 1–7, Supplemental Figures S1–S8, Supplemental Tables S1–S4, Methods section, Data availability statement
- **Missing materials affecting confidence** Raw simulation outputs, parameter sampling ranges for RACIPE beyond what is stated, code implementation details, full ARACNE output networks, and complete literature curation table for network edges

## Reviewer
- **Overall assessment** This manuscript presents a network modeling approach to understand phenotypic plasticity in melanoma. The authors combine correlation analysis, WGCNA, ARACNE, and RACIPE simulations to propose a 17-node transcription factor network that can generate multiple attractor states. The work addresses an important question and the systems-level approach is timely. However, several technical aspects require clarification and additional validation before the conclusions can be fully supported. The link between the inferred network and the simulated dynamics needs stronger justification, and the biological validation of the model predictions is limited.
- **Who would be interested in the results, and why** Researchers in cancer systems biology, computational biology, and melanoma biology would find this work relevant. Those studying phenotypic heterogeneity, drug resistance, and cell state transitions would benefit from the modeling framework. The work may also interest researchers working on network-based approaches to understand cancer plasticity and therapeutic resistance.
- **Major strengths** The study addresses a clinically relevant problem using a quantitative framework. The integration of multiple public datasets and the use of an unbiased approach to identify master regulators is commendable. The RACIPE method is appropriate for exploring multistability in gene regulatory networks. The authors make their code available and use publicly accessible data, supporting reproducibility.
- **Major Concerns** The network inference relies heavily on correlation and literature curation, which may introduce bias. The validation of the four predicted phenotypes against experimental data is indirect. The claim that the network is the "master regulator" of phenotypic plasticity is not fully supported by the evidence presented. The robustness of the RACIPE results to parameter choices and network topology is not thoroughly explored.
- **Minor Comments** Several figure labels and statistical details could be clarified. The discussion of the relationship between the model and epithelial-mesenchymal transition could be more nuanced. The limitations section is brief and could acknowledge additional caveats.
- **Technical failings that need to be addressed before the case is established** The network inference pipeline needs clearer justification for the choice of datasets and thresholds. The RACIPE simulation setup, including parameter ranges and sampling strategy, should be described in more detail. The comparison between simulated and experimental data relies on qualitative visual inspection rather than quantitative metrics.
- **Assessment against Nature-style criteria** Originality: The application of RACIPE to melanoma phenotypic plasticity is novel, though the general concept of attractor states in cancer is established. Scientific importance: The question of phenotypic heterogeneity in melanoma is clinically significant, and a predictive network model could have translational value. Interdisciplinary readership: The work bridges computational biology and oncology, potentially appealing to both communities. Technical soundness: The methods are generally appropriate, but several technical details need strengthening. Readability for nonspecialists: The manuscript is largely accessible, though some systems biology concepts may require background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the inferred 17-node network is the master regulator network driving phenotypic plasticity in melanoma.
- **Evidence pointer** Figure 4A, Table S3, Methods section "Identification of master regulator network"
- **Concern** The network inference combines ARACNE results with literature curation, but the criteria for including or excluding edges are not fully transparent. The authors state that edges were curated from public databases and literature, but the specific evidence for each edge is not provided in a systematic way. The choice of the final 17 nodes from the initial candidate list is not clearly justified. This raises concerns about whether the network is truly representative of the underlying biology or whether it reflects the biases of the curation process.
- **Why it matters** The entire modeling framework depends on the accuracy and completeness of the inferred network. If the network is incomplete or contains spurious edges, the simulated attractor states may not reflect real biological states. A biased network could lead to incorrect predictions about phenotypic transitions and drug responses.
- **Resolution test** Provide a detailed table listing each edge with the specific evidence supporting it (e.g., ChIP-seq data, perturbation experiments, literature references). Justify the selection of the 17 nodes based on objective criteria, such as statistical significance in the ARACNE analysis or enrichment in the WGCNA modules. Perform a sensitivity analysis by removing or adding edges to test whether the attractor landscape is robust to network perturbations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that RACIPE simulations recapitulate the four phenotypes observed in melanoma and predict the dedifferentiation trajectory upon BRAF inhibition.
- **Evidence pointer** Figures 6A, 6B, 6C, 7A, 7B, S7, Methods section "RACIPE"
- **Concern** The comparison between simulated attractor states and experimental phenotypes is largely qualitative. The authors show that simulated clusters separate along principal components and that marker genes are differentially expressed, but they do not provide a quantitative measure of how well the simulated states match the experimental data. The claim that the model recapitulates the dedifferentiation trajectory is based on visual inspection of cluster proximity and pseudotime analysis of one experimental dataset, but the correspondence between the simulated trajectory and the experimental trajectory is not rigorously established.
- **Why it matters** Without quantitative validation, it is difficult to assess whether the model predictions are meaningful or whether they arise from the specific parameter choices in the simulations. The clinical relevance of the model depends on its ability to accurately predict phenotypic transitions, which requires a more rigorous comparison with experimental data.
- **Resolution test** Develop a quantitative metric to compare the simulated attractor states with experimental phenotypes, such as a correlation score between simulated and experimental gene expression profiles for each phenotype. Perform a statistical test to determine whether the simulated trajectory matches the experimental pseudotime trajectory better than chance. Validate the model predictions by comparing with additional experimental datasets, such as time-course data of melanoma cells treated with BRAF inhibitors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that all code is available at a GitHub repository and that the analysis uses publicly available data.
- **Evidence pointer** Data and code availability section
- **Concern** While the code repository is mentioned, the manuscript does not provide a detailed description of the computational environment, dependencies, or instructions for running the simulations. The RACIPE method requires specific parameter settings, and the manuscript does not specify the ranges for all kinetic parameters or the number of models and initial conditions used beyond stating 10,000 models and 100 initial conditions. This limits the reproducibility of the results.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without clear documentation of the simulation setup and code dependencies, other researchers cannot easily replicate or build upon this work.
- **Resolution test** Provide a detailed README file in the GitHub repository with instructions for setting up the environment, running the simulations, and reproducing the figures. Include a table of all RACIPE parameters and their ranges. Consider using a container or virtual environment to ensure consistent execution.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their modeling framework offers a platform to identify novel therapeutic strategies targeting melanoma plasticity.
- **Evidence pointer** Discussion section, Figure 7
- **Concern** The therapeutic implications are discussed in general terms, but the manuscript does not provide concrete examples of how the model could be used to identify new drug targets or combination therapies. The only perturbation explored is MITF knockdown, which is already known to be important in melanoma. The model's utility for discovering novel therapeutic strategies is not demonstrated.
- **Why it matters** The translational relevance of the work is a key selling point. Without a concrete demonstration of how the model can generate testable therapeutic hypotheses, the practical impact of the study remains unclear.
- **Resolution test** Use the model to simulate the effects of perturbing other network nodes and identify those that could shift the population toward a more drug-sensitive phenotype. Validate one or more of these predictions experimentally, or at least provide a clear computational prediction that could be tested.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B
- **Issue** The correlation matrices in Figure 1B are presented for multiple datasets, but the sample sizes and the specific melanoma subtypes are not clearly indicated in the figure legend.
- **Required correction** Add sample sizes and a brief description of the sample types for each dataset in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 6B
- **Evidence pointer** Figure 6B
- **Issue** The significance levels in Figure 6B are indicated with asterisks, but the statistical test used and the number of biological replicates are not stated in the figure legend.
- **Required correction** Specify the statistical test used and the number of replicates in the figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "RACIPE"
- **Evidence pointer** Methods section "RACIPE"
- **Issue** The description of the RACIPE method is brief and does not explain how the parameter ranges were chosen or how the number of models was determined.
- **Required correction** Expand the methods to include a justification for the parameter ranges and the number of models used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the relationship between the model and the epithelial-mesenchymal transition (EMT) is somewhat superficial and does not fully engage with the existing literature on EMT in melanoma.
- **Required correction** Expand the discussion to more thoroughly compare and contrast the model with existing EMT frameworks in melanoma.

## Risk / unsupported claims
- The claim that the inferred network is the "master regulator" of phenotypic plasticity is not fully supported, as the network inference relies on correlation and literature curation without direct experimental validation of the regulatory relationships.
- The claim that the model recapitulates the dedifferentiation trajectory upon BRAF inhibition is based on qualitative comparisons and would benefit from quantitative validation.
- The claim that the modeling framework can identify novel therapeutic strategies is not demonstrated with concrete examples.
- The robustness of the attractor landscape to network perturbations and parameter variations is not assessed, so the generality of the conclusions is uncertain.