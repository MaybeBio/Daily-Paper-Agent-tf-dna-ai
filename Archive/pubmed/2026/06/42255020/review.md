## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose a statistical-mechanics framework to analyze high-throughput DNA cyclizability data, identify a minimal pairwise interaction model, extract sequence features controlling cyclizability, and validate predictions via all-atom molecular dynamics simulations
- **Visible evidence base** Text descriptions of results, equations, and references to figures/tables (Fig. 1-7, Table 1, Figs. S1-S5, Table S1) without actual data values or visual content
- **Missing materials affecting confidence** All figures, tables, supplementary material, and detailed numerical results; experimental protocol details for loop-seq are referenced but not reproduced

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing and physically interpretable approach to a timely problem in DNA mechanics. The statistical-mechanics framework is clearly described, and the progression from linear to pairwise models with symmetry constraints is logical. However, the absence of all figures, tables, and numerical data in the provided material severely limits the ability to verify the central claims. The predictive performance (r=0.68) is modest compared to existing deep learning approaches, and the authors acknowledge this gap. The molecular dynamics validation is described qualitatively, and without quantitative metrics, its evidentiary weight cannot be assessed. The manuscript is likely to interest researchers in DNA biophysics, chromatin biology, and DNA nanotechnology, but the current evidence base is insufficient to fully establish the claims.

- **Who would be interested in the results, and why** Researchers studying sequence-dependent DNA mechanics, chromatin organization, and nucleosome positioning would find the interpretable sequence features valuable. The DNA nanotechnology community would benefit from design rules for cyclizable sequences. Computational biologists developing predictive models for DNA biophysics would be interested in the comparison between physics-based and deep learning approaches. The general framework for extracting low-order collective features from high-dimensional sequence data may also appeal to researchers in statistical genetics and biophysics.

- **Major strengths** The statistical-mechanics framework provides a principled, interpretable alternative to black-box machine learning models. The systematic hierarchy from linear to pairwise terms with symmetry constraints is elegant and physically motivated. The use of two independent datasets (random and genomic) strengthens the generality of the findings. The explicit comparison with deep learning approaches and the discussion of shared coarse-grained features demonstrates intellectual honesty. The molecular dynamics validation, while qualitative, provides an independent test of predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that a minimal pairwise model captures the sequence dependence of DNA cyclizability, with predictive correlation r=0.68±0.02
- **Evidence pointer** Results section "A pairwise model", Figure 4
- **Concern** The predictive performance of r=0.68 is presented as evidence that the pairwise model captures the essential sequence features. However, this correlation is substantially lower than the r=0.8-0.9 reported for deep learning models and r=0.96 for the most recent approach. The authors acknowledge this gap but do not provide a statistical test demonstrating that the pairwise model captures a significant fraction of the explainable variance. Without knowing the noise ceiling of the loop-seq measurements, it is impossible to determine whether r=0.68 represents a near-optimal physics-based model or a substantially incomplete one.
- **Why it matters** The central claim of the manuscript is that a minimal pairwise model is sufficient to describe sequence-dependent cyclizability. If the pairwise model leaves substantial unexplained variance that higher-order terms could capture, the claim of minimality is weakened. The authors mention an unpublished study with three-body terms achieving r=0.92, which suggests that higher-order terms are indeed important, contradicting the "minimal" characterization.
- **Resolution test** Provide the noise ceiling of the loop-seq measurements (e.g., measurement reproducibility), a statistical comparison between the pairwise model and higher-order models on held-out data, and a variance decomposition showing what fraction of explainable variance the pairwise model captures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The claim that molecular dynamics simulations validate the predicted most and least cyclizable sequences
- **Evidence pointer** Results section "Molecular dynamics simulations of most and least cyclizable sequences", Figure 7
- **Concern** The molecular dynamics validation is described only qualitatively: the most cyclizable sequence "curves into a semicircle" while the least cyclizable sequences "remain straight." No quantitative metrics are provided, such as end-to-end distance distributions, bending angle distributions, or persistence length estimates. The observation that end-to-end distance decreases after 20 ns for the most cyclizable sequence is suggestive but lacks statistical rigor. With only one sequence per category and no replicate simulations, it is unclear whether the observed differences are significant or specific to the chosen sequences.
- **Why it matters** The molecular dynamics simulations are presented as independent validation of the model's predictions. Without quantitative analysis, this validation is anecdotal. The claim that simulations "strongly support" the predictions is not justified by the evidence described.
- **Resolution test** Provide quantitative metrics (e.g., mean and standard error of end-to-end distance, bending angle distributions) for multiple replicate simulations per sequence, and a statistical test comparing most versus least cyclizable sequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and robustness
- **Claim pointer** The claim that sequence features extracted from the pairwise model are robust and provide physical insight
- **Evidence pointer** Results section "Sequence features that control DNA cyclizability", Figure 5, Table 1
- **Concern** The eigenvalue decomposition identifies dominant modes, but the physical interpretation of these modes is not fully developed. The first two eigenvectors form a quadrature pair with ten-base periodicity, which is attributed to DNA helical pitch. However, the relationship between these modes and specific dinucleotide or trinucleotide properties is not quantified. The comparison between Random and Tiling libraries shows consistency for most cyclizable modes but differences for least cyclizable modes, yet the implications of this discrepancy are not discussed in depth. The predicted most and least cyclizable sequences are presented without uncertainty estimates or sensitivity analysis.
- **Why it matters** The manuscript claims to advance understanding of sequence-dependent DNA mechanics. This requires not just predictive models but interpretable features. The current analysis identifies modes but does not fully explain what physical properties (e.g., bendability, roll, tilt) these modes correspond to. The robustness of the extracted features to dataset composition and model assumptions is not established.
- **Resolution test** Provide a mapping between the dominant eigenvectors and known structural properties of dinucleotides (e.g., from crystallographic or NMR data), and perform a sensitivity analysis by varying the training set composition and model regularization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological completeness
- **Claim pointer** The claim that the statistical-mechanics framework is general and applicable to other high-dimensional problems
- **Evidence pointer** Discussion section
- **Concern** The framework is presented as a general approach for problems where input is high-dimensional and output is a functional property. However, the manuscript does not discuss the assumptions and limitations of the cluster expansion approach in this context. The convergence of the expansion, the choice of truncation order, and the computational scaling with sequence length are not addressed. The applicability to other problems (e.g., RNA or protein sequences) is asserted but not demonstrated.
- **Why it matters** The generality claim is a significant part of the manuscript's broader impact. Without a discussion of the method's limitations and requirements, the claim is not substantiated.
- **Resolution test** Provide a discussion of the conditions under which the cluster expansion converges, the computational complexity of the method, and a proof-of-concept application to a different problem or a clear statement of the requirements for applying the method to other systems.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that a "minimal pairwise model" is identified, but the term "minimal" is not defined. Does it mean the simplest model that achieves a certain performance threshold, or the model with the fewest parameters that is statistically justified?
- **Required correction** Define "minimal" in the context of model selection, or rephrase to "a pairwise model that captures the dominant sequence features."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section "Details of molecular dynamics simulations"
- **Issue** The methods state that simulations were "adapted from a previously developed pipeline" but do not provide sufficient detail to reproduce the simulations. Key parameters such as simulation length, equilibration protocol, and analysis methods are not described.
- **Required correction** Provide a more detailed description of the simulation protocol, including system setup, force field parameters, equilibration and production run lengths, and analysis methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "A pairwise model"
- **Evidence pointer** Results section "A pairwise model", Figure 4b
- **Issue** The predictive performance is reported as r=0.68±0.02 from "multiple random 90/10 splits." The number of splits and the variability across splits are not reported. Additionally, the use of Pearson correlation as the sole metric may not fully capture predictive accuracy.
- **Required correction** Report the number of splits, the range of correlations across splits, and consider additional metrics such as mean squared error or rank correlation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The comparison with deep learning approaches is brief and does not include a systematic comparison of model architectures, training data, or evaluation protocols. The statement that "both approaches identify a common coarse-grained organization" is based on a single comparison in Table S1, which is not described in detail.
- **Required correction** Provide a more detailed comparison with existing models, including a table of model architectures, training data, and performance metrics, and describe the methodology for comparing sequence features.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability statement mentions code and simulation outputs but does not specify the exact contents of the GitHub repository or the Zenodo deposit. It is unclear whether the raw loop-seq data are included or only the processed cyclizability values.
- **Required correction** Clarify the contents of the data repositories, including whether raw and processed data are available, and provide a persistent identifier for the Zenodo deposit.

## Risk / unsupported claims
- The claim that the pairwise model is "minimal" is not supported by statistical model comparison or noise ceiling analysis
- The claim that molecular dynamics simulations "strongly support" the predictions is not supported by quantitative evidence
- The claim that the framework is general and applicable to other problems is asserted but not demonstrated
- The claim that the extracted sequence features are "robust" is not supported by sensitivity analysis
- The claim that the most cyclizable sequence "curves into a semicircle" is based on a single simulation snapshot and is not quantified
- The comparison with deep learning approaches is based on a single table (Table S1) that is not described in the provided text
- The physical interpretation of the dominant eigenvectors is not fully developed or validated against known structural data