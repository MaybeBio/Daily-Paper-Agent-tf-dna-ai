## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, experimental results, conclusion) for a preprint posted on bioRxiv.
- **Assessment boundary** Scientific and technical soundness of the proposed method (SLGNN), validity of claims relative to the provided evidence, and clarity of presentation. No assessment of formatting or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors propose SLGNN, a graph neural network that operates on chemical-substructure-based graphs and uses generalized fused lasso to identify connected, chemically valid subgraphs critical for drug-protein binding prediction. They claim that (1) all key structures identified by SLGNN are chemically valid, (2) these structures retain predictive power when used alone, and (3) the identified structures contain most known binding sites in case studies.
- **Visible evidence base** Abstract; Introduction; Methods (Sections 2.1–2.6); Experimental Results (Sections 3.1–3.7) including Figures 1–4 and Tables 1–4; Conclusion. No supplementary materials, code, or datasets were provided for inspection.
- **Missing materials affecting confidence** Code repository (referenced but not reviewed); full hyperparameter details for competing methods; statistical significance tests for Table 2 and Table 3 comparisons; details on the junction tree vocabulary construction and its coverage; details on how binding sites were mapped to substructures; details on the PALM algorithm implementation and convergence criteria; details on the baseline models' training procedures.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in explainable AI for drug discovery, namely the generation of chemically valid and connected substructures as explanations for drug-protein binding predictions. The core idea of using chemical-substructure-based graphs combined with generalized fused lasso is novel and potentially useful. However, the evidence provided is insufficient to fully support the central claims. The experimental evaluation lacks statistical rigor, the comparison with competing methods is not fully controlled, and several methodological details are missing. The case study results are promising but not conclusive. The manuscript would benefit from additional experiments, more rigorous evaluation, and clearer exposition of the method and its limitations.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, cheminformatics, and explainable AI for molecular data. The method addresses a practical limitation of existing explainable GNNs (chemically invalid explanations) and could be of interest to those developing interpretable models for drug-target interaction prediction. The use of sparse learning to enforce connectivity is a methodological contribution that may interest the graph neural network community.
- **Major strengths** 1. The problem is well-motivated and practically relevant. 2. The use of chemical-substructure-based graphs is a sensible design choice that guarantees chemical validity of identified subgraphs. 3. The incorporation of generalized fused lasso to enforce connectivity is a novel and technically sound idea. 4. The evaluation includes multiple complementary perspectives: chemical validity, predictive power, and binding site coverage.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of statistical significance testing), R1-M2 (uncontrolled comparison with competing methods), R1-M3 (insufficient methodological detail for reproducibility), R1-M4 (incomplete case study evaluation).
- **Assessment against Nature-style criteria** **Originality**: The idea of using chemical-substructure-based graphs with generalized fused lasso for explainable drug-protein binding prediction is original and not a trivial extension of existing work. **Scientific importance**: The problem is important for drug discovery, and the method addresses a real limitation of existing explainable GNNs. However, the significance of the contribution is not fully demonstrated due to the limited experimental evidence. **Interdisciplinary readership**: The work bridges machine learning and chemistry, and the writing is generally accessible to both communities, though some parts (e.g., the PALM algorithm) may be challenging for non-specialists. **Technical soundness**: The core idea is sound, but the evaluation is not rigorous enough to fully support the claims. Missing statistical tests and uncontrolled comparisons weaken the technical case. **Readability for nonspecialists**: The manuscript is generally readable, but the methods section could be clearer, particularly the description of the generalized fused lasso and its effect on connectivity.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the problem is relevant, but the current evidence does not fully establish the claimed advantages over existing methods. Additional experiments with statistical rigor and clearer methodological details are needed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that SLGNN outperforms competing methods in terms of predictive power (Table 2) and binding site coverage (Table 3).
- **Evidence pointer** Tables 2 and 3, Section 3.6 and 3.7
- **Concern** The performance comparisons in Tables 2 and 3 are presented without any statistical significance testing. It is unclear whether the observed differences between SLGNN and competing methods are meaningful or within the range of random variation. For example, in Table 3, the differences in AUPR and F1 scores between SLGNN and the best competing method are often small (e.g., 0.01–0.05), and without confidence intervals or p-values, these differences cannot be interpreted as evidence of superiority.
- **Why it matters** The central claim of the paper is that SLGNN provides better explanations than existing methods. Without statistical testing, the reader cannot assess whether the reported improvements are robust or due to chance. This is particularly important given the small number of test cases (10 drug-protein pairs in Table 3).
- **Resolution test** Provide confidence intervals or p-values for the comparisons in Tables 2 and 3. If the number of test cases is too small for standard tests, consider using bootstrap or permutation tests, or clearly state the limitations of the comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors claim that SLGNN's key structures have more predictive power than those identified by competing methods (Section 3.6).
- **Evidence pointer** Section 3.6, Table 2, Figure 4
- **Concern** The comparison with competing methods is not fully controlled. For SLGNN, the "identified" structures are used as input to a basic message-passing algorithm (SLGNN(Base)). For competing methods, the same procedure is applied to their identified structures. However, it is unclear whether the competing methods' identified structures are directly comparable. For example, GNNExplainer and PGExplainer generate node/edge importance scores, and the authors select a subset of atoms based on the number of atoms in SLGNN's output. This selection procedure may not be optimal for these methods and could disadvantage them. Additionally, the authors do not report how the number of atoms in SLGNN's output varies across drugs, which could affect the comparison.
- **Why it matters** The claim that SLGNN's explanations are more predictive than those of competing methods depends on a fair comparison. If the competing methods are not given the same opportunity to select their best substructures, the comparison is biased and the conclusion is not supported.
- **Resolution test** Describe the exact procedure for selecting substructures for each competing method. Consider using a consistent criterion (e.g., top-k atoms based on importance scores) for all methods. Alternatively, report results for multiple thresholds and show that SLGNN's advantage is robust.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that SLGNN uses generalized fused lasso with message passing and is optimized via the PALM algorithm (Sections 2.3 and 2.5).
- **Evidence pointer** Sections 2.3, 2.5, and 2.6
- **Concern** The methodological description is not sufficiently detailed for reproduction. Specifically, the following are missing: (1) the exact form of the generalized fused lasso penalty and how it is applied to the graph structure; (2) the initialization and update rules for the PALM algorithm, including the choice of step sizes; (3) the architecture of the message-passing network (e.g., number of layers, hidden dimensions, activation functions); (4) the training procedure, including the number of epochs, learning rate, and early stopping criteria; (5) the hyperparameter values for λ1, λ2, and λ3, and how they were selected. The code repository is referenced but was not provided for review.
- **Why it matters** Reproducibility is a core requirement for scientific contributions. Without these details, other researchers cannot implement or validate the method, which limits the impact of the work.
- **Resolution test** Provide a complete description of the model architecture, the optimization algorithm, and the hyperparameter selection process. Ensure that the code repository is publicly accessible and well-documented.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evaluation completeness
- **Claim pointer** The authors claim that the key structures identified by SLGNN contain most of the binding sites (Section 3.7).
- **Evidence pointer** Section 3.7, Table 3
- **Concern** The case study evaluation is limited to 10 drug-protein pairs. While this is a reasonable starting point, the authors do not discuss the generalizability of their findings. For example, it is unclear how the method performs on proteins with different binding site characteristics (e.g., shallow vs. deep pockets, flexible vs. rigid binding sites). Additionally, the authors do not report the size of the identified substructures relative to the full molecule, which could affect the interpretation of the results. A larger and more diverse set of test cases would strengthen the claim.
- **Why it matters** The claim that SLGNN identifies binding sites is central to the paper's contribution. A limited evaluation on 10 cases is not sufficient to establish generalizability, especially given the variability in drug-protein interactions.
- **Resolution test** Expand the case study to include more drug-protein pairs, ideally covering a range of protein families and binding site types. Report the size of the identified substructures and discuss any patterns or limitations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Equation (1)
- **Evidence pointer** Section 2.2
- **Issue** The message-passing equation is not fully defined. The notation for the hidden neighborhood vector is introduced but the exact computation is not clear. Specifically, the equation for the hidden vector is not shown, and the role of the learnable parameter β is described but not formalized.
- **Required correction** Provide the full equations for the message-passing function, including the computation of the hidden neighborhood vector and the exact role of β in the aggregation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.5, Table 1
- **Evidence pointer** Section 3.5, Table 1
- **Issue** The table reports the average number of connected components and the number of chemically valid structures, but the criteria for "chemically valid" are not defined. It is unclear whether this refers to valid substructures according to chemical valence rules, or something else.
- **Required correction** Define what constitutes a "chemically valid" structure in this context and describe how this was assessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.6, Figure 4
- **Evidence pointer** Section 3.6, Figure 4
- **Issue** The workflow in Figure 4 is described in the text but the figure itself is not referenced in the text. It would be helpful to refer to the figure explicitly when describing the procedure.
- **Required correction** Add a reference to Figure 4 in the text where the workflow is described.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The authors state that they use Ki values to label drugs as binding or non-binding, but they do not report the distribution of the data (e.g., number of positive and negative samples per protein). This information is important for understanding the difficulty of the classification task.
- **Required correction** Report the class distribution for each dataset.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The motivation for the additional term Γ(β) is described, but the exact form of the term is not given. It is unclear how the frequency m_ij is computed and how it is incorporated into the loss function.
- **Required correction** Provide the explicit form of Γ(β) and describe how m_ij is calculated.

## Risk / unsupported claims
- The claim that "all key structures identified by our SLGNN are chemically valid" is supported by the design of the method (chemical-substructure-based graphs), but the empirical evidence in Table 1 is limited to the datasets used and does not establish generalizability.
- The claim that "the key structures identified by our SLGNN have more predictive power than the key structures identified by the competing methods" is not fully supported due to the lack of statistical significance testing and potential biases in the comparison procedure (R1-M2).
- The claim that "the key structures identified by our SLGNN contain most of the binding sites" is based on a small number of case studies (10 drug-protein pairs) and may not be generalizable (R1-M4).
- The claim that "SLGNN is the most robust method among the competing methods" is based on the average performance across 10 cases, but the variability is not quantified with confidence intervals or statistical tests.
- The statement that "using chemical-substructure-based graphs can significantly improve learning accuracy over using atom-based graphs" is based on the results in Table 2, but the significance of this improvement is not tested statistically.