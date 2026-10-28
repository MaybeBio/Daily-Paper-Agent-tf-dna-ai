## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided.
- **Assessment boundary** Scientific and technical soundness of the proposed method, validity of the claims against the presented evidence, and clarity of the presentation. This review does not assess the novelty of the work relative to unpublished literature.
- **Shared manuscript claim summary** The authors propose RevGraphVAMP, an unsupervised model combining graph convolutional neural networks (GCNs) and physical constraints (reversibility and detailed balance) for analyzing protein molecular dynamics (MD) simulation trajectories. They claim it achieves higher VAMP scores and better state transition prediction accuracy than existing VAMPnets-based models on two public datasets (alanine dipeptide and Aβ42 polypeptide), provides better dimensionality reduction for distinguishing substates, and offers interpretable results via an attention mechanism.
- **Visible evidence base** Abstract, Introduction, Methods (Sections 2.1, 2.2), Results (Sections 3.1, 3.2), Conclusions, Data availability, Author contributions, Competing interests, Acknowledgements. Figures and tables are referenced but not provided in the supplied text.
- **Missing materials affecting confidence** Figures 1-8, Tables 1-2, Supplementary Figures S1-S3, Supplementary Tables S1-S2, and the full mathematical derivations (equations are referenced but not fully displayed in the provided text). Code and data are not yet publicly available.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biophysics, namely the analysis of high-dimensional MD trajectory data with deep learning. The combination of GCNs, physical constraints, and attention mechanisms is a reasonable and potentially valuable direction. However, the current manuscript has significant technical gaps and presentation issues that prevent a full evaluation of the claims. The methods section is incomplete, with key equations and model details missing. The results section relies heavily on figures that were not provided, making it impossible to verify the reported performance. The claims of interpretability and biological relevance are interesting but not rigorously supported by the evidence presented in the text. The manuscript is not yet suitable for publication in its current form.
- **Who would be interested in the results, and why** Researchers in computational chemistry, biophysics, and machine learning applied to molecular dynamics. Specifically, those working on Markov state models, dimensionality reduction for biomolecular simulations, and interpretable deep learning for protein science would find the approach relevant. The potential application to drug discovery and analysis of disordered proteins broadens the appeal.
- **Major strengths**
    1.  The problem is well-motivated and important. The need for automated, interpretable, and physically meaningful analysis of large MD datasets is clear.
    2.  The proposed architecture is a sensible and novel combination of existing components (GCN, VAMP, physical constraints, attention). The integration of physical constraints to handle non-equilibrium data is a particularly good idea.
    3.  The use of two public datasets of different scales (small alanine dipeptide and larger Aβ42) is a good approach for demonstrating the method's versatility.
    4.  The focus on interpretability through attention weights is a valuable contribution, as it moves beyond black-box predictions.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The model combines graph convolutional neural networks and physical constraints to improve learning performance and handle non-equilibrium data.
    - **Evidence pointer** Section 2.2, "The architecture of RevGraphVAMP"
    - **Concern** The methods section is critically incomplete. The core mathematical formulations are missing. Equations for the graph convolution, the VAMP score, the physical constraints (S and u), and the loss functions are referenced but not displayed in the provided text. The description of the GASchNet component is high-level and lacks the specific details necessary for reproduction. The exact nature of the "physical constraints" and how they are enforced is not fully clear from the text alone.
    - **Why it matters** Without the full mathematical details, the technical soundness of the proposed method cannot be assessed. The core contribution is the specific architecture and its training procedure. If these are not fully specified, the work is not reproducible and the claims of improved performance cannot be verified.
    - **Resolution test** The authors must provide the complete mathematical formulation of the model, including all equations, in the main text or a clearly referenced supplement. This should include the exact form of the GCN layers, the attention mechanism, the constraint modules, and the loss functions.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence Quality
    - **Claim pointer** The model achieves the highest VAMP scores and better state transition prediction accuracy compared to other VAMPnets models on two public datasets.
    - **Evidence pointer** Section 3.1, "Analysis results of Alanine dipeptide data set"; Section 3.2, "Analysis result of Aβ 42 data set"; Table 2
    - **Concern** The central performance claims are based on figures and tables that were not provided in the manuscript text. The review cannot verify the VAMP scores, the CK test results, the state distributions, or the attention visualizations. The text describes the results but provides no numerical data or visual evidence to support them.
    - **Why it matters** The primary contribution of the paper is a new model that is claimed to be better than existing ones. This claim is entirely dependent on the experimental results. Without access to the figures and tables, the validity of the results cannot be confirmed, and the strength of the claims cannot be evaluated.
    - **Resolution test** The authors must provide all figures and tables in a reviewable format. The figures should be of high quality and clearly show the data. The tables should contain the numerical values for the VAMP scores and other metrics, including error bars or standard deviations where appropriate.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific Importance / Interpretability
    - **Claim pointer** The attention mechanism provides interpretable results for protein structural characterization, identifying key residues and interactions.
    - **Evidence pointer** Section 3.1, "Analysis result of Alanine dipeptide data set"; Section 3.2, "Analysis result of Aβ 42 data set"; Figures 5 and 8
    - **Concern** The claim of interpretability is a key selling point, but the analysis is superficial. The text states that certain atoms or residues have "strong interactions" or "important roles" based on attention weights, but it does not provide a rigorous analysis of what these weights mean. For example, in the Aβ42 case, the text mentions that LYS16 is important and links it to Alzheimer's disease, but this is a single, post-hoc observation. There is no systematic comparison of the attention-based findings with known structural or functional data, nor is there a discussion of the potential limitations or biases of using attention weights as a proxy for physical interaction strength.
    - **Why it matters** The claim of interpretability is a major differentiator for this model. If the interpretation is not rigorously validated, the claim is weakened. The paper needs to demonstrate that the attention weights provide reliable and novel biological insights, not just confirm known facts or produce plausible-sounding but unvalidated correlations.
    - **Resolution test** The authors should provide a more detailed and critical analysis of the attention weights. This could include a comparison of the identified key residues with known functional or structural annotations, a statistical analysis of the significance of the attention weights, or a discussion of the limitations of the interpretability method.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical Soundness
    - **Claim pointer** The model has higher dimensionality reduction discrimination ability for different substates.
    - **Evidence pointer** Section 3.1, "Analysis results of Alanine dipeptide data set"; Figure 4
    - **Concern** The claim of "higher dimensionality reduction discrimination ability" is based on a visual comparison of free energy surfaces (Figure 4). The text states that the model's results are "clearer" and "exhibit enhanced performance," but this is a subjective assessment. There is no quantitative metric used to compare the quality of the dimensionality reduction between the different models.
    - **Why it matters** A quantitative comparison is necessary to support the claim of superiority. Visual inspection can be misleading, and a more rigorous metric (e.g., VAMP score, clustering accuracy, or a measure of state separation) would provide stronger evidence.
    - **Resolution test** The authors should provide a quantitative comparison of the dimensionality reduction quality, such as the VAMP-2 score of the projected data, the silhouette score of the identified clusters, or a similar metric.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Section 1
    - **Issue** The abstract and introduction contain some grammatical errors and awkward phrasing (e.g., "puts challenges on how to extract", "the model in applied to the analysis"). The writing could be significantly improved for clarity and flow.
    - **Required correction** A thorough language edit by a native English speaker is recommended.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Section 2.1, "Datasets and data preparation"
    - **Evidence pointer** Section 2.1
    - **Issue** The description of the graph construction is incomplete. The text mentions that "the nearest m atoms or amino acids are selected for each node" but does not specify the value of `m` used in the experiments. The hyperparameters are listed in Table 1, which is not provided.
    - **Required correction** Specify the value of `m` and all other relevant hyperparameters in the main text.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Section 2.2, "The architecture of RevGraphVAMP"
    - **Evidence pointer** Section 2.2
    - **Issue** The text states that the model is "based on the Markov variation method (VAMP)" and uses "physical constraints." The specific type of VAMP score used (VAMP-2, VAMP-E) is mentioned, but the relationship between the VAMP loss and the physical constraints is not clearly explained. How do the constraints interact with the VAMP objective?
    - **Required correction** Clarify the role of the physical constraints in the loss function. Are they a separate term, a regularization, or a structural constraint on the transition matrix?

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Evidence Quality
    - **Affected element** Section 3.2, "Analysis result of Aβ 42 data set"
    - **Evidence pointer** Section 3.2
    - **Issue** The text mentions that a subset of 1024 trajectories was used for verification, but it is not clear if this subset was used for training or only for testing. The description of the training/validation split is ambiguous.
    - **Required correction** Clarify the data split used for training and testing.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Section 3.2, "Analysis result of Aβ 42 data set"
    - **Evidence pointer** Section 3.2
    - **Issue** There is a typo: "he model was then trained" should be "The model was then trained."
    - **Required correction** Correct the typo.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Incomplete methods section, missing core equations and model details.
    - R1-M2: Performance claims are not verifiable without the figures and tables.

- **Assessment against Nature-style criteria**
    - **Originality** The combination of GCNs, VAMP, and physical constraints is a novel integration of existing ideas. The application of attention mechanisms for interpretability in this context is also a valuable addition. However, the individual components are well-established, and the novelty lies in their specific combination.
    - **Scientific importance** The problem of analyzing MD trajectories is of high importance. The potential to handle non-equilibrium data and provide interpretable results could be a significant advance. However, the importance is not fully established due to the lack of verifiable results and the limited depth of the interpretability analysis.
    - **Interdisciplinary readership** The work is relevant to researchers in biophysics, computational chemistry, and machine learning. The potential applications in drug discovery could broaden its appeal. However, the presentation is currently too technical and incomplete for a broad interdisciplinary audience.
    - **Technical soundness** The technical soundness cannot be fully assessed due to the missing methods and results. The conceptual framework is sound, but the implementation and validation details are not provided.
    - **Readability for nonspecialists** The manuscript is not accessible to nonspecialists in its current form. The introduction provides some context, but the methods and results sections are dense and rely heavily on jargon and missing figures. The abstract is also somewhat unclear.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and proposes a plausible solution, but the technical details and experimental evidence are insufficient to support the claims. A major revision is required to provide the full methods, all figures and tables, and a more rigorous analysis of the results and interpretability claims.