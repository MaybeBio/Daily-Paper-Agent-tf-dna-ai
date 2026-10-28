## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, key points, availability, funding, footnotes) as provided in the submission.
- **Assessment boundary** Scientific and technical soundness of the methods, validity of the results and claims as presented, and clarity of the reporting. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors present GLMSite, a method that predicts nucleic-acid-binding sites (DNA and RNA) from protein sequences alone. The method uses ESMFold-predicted structures to construct protein graphs, ProtTrans language model embeddings as node features, and a geometric vector perceptron (GVP) based graph neural network. The authors claim GLMSite outperforms state-of-the-art sequence-based methods and is comparable to structure-based methods on independent test sets, and that residue-level predictions can be used to infer protein-level nucleic-acid-binding function.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (Sections 2.1, 2.2, 2.3), Results (Sections 3.1, 3.2, 3.3, 3.4, 3.5), Discussion, Key points, Availability, Funding, Conflict of Interest, Footnotes. Tables 1, 2, 3, 4, 5 and Figures 1, 2, 3, 4, 5, 6, 7 are referenced. Supplementary materials are referenced but not provided.
- **Missing materials affecting confidence** Supplementary Tables S1, S2, S3, S4, S5 and Supplementary Figures S1, S2, S3, S4, S5, S6, S7, S8 are referenced but not provided. Full equations for the GVP operations (Equations 1, 2, 3, 4, 5) are not fully written out. Detailed hyperparameter settings, training time, and computational resource requirements are not provided. The exact definition of the "percentage of binding residues" used in the protein-level scoring function is not fully specified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the prediction of nucleic-acid-binding sites from protein sequence. The use of ESMFold predicted structures combined with ProtTrans embeddings and a GVP-based graph neural network is a reasonable and timely approach. The reported performance on independent test sets is promising. However, several technical details are missing or unclear, and the evidence for some claims is incomplete. The comparison with existing methods, while favorable, lacks sufficient statistical rigor and detail. The claim that residue-level predictions are useful for protein-level function inference is interesting but requires more thorough validation. Overall, the work has potential, but the current manuscript does not fully establish the case for its central claims.
- **Who would be interested in the results, and why** Researchers in the fields of protein function prediction, structural bioinformatics, and machine learning applied to biology. The method's ability to predict binding sites from sequence alone, using predicted structures, is of practical interest for high-throughput annotation of proteins without experimental structures. The use of language model embeddings and geometric deep learning is also of methodological interest to the machine learning for biology community.
- **Major strengths**
    1.  The problem is important and the proposed solution is practical, addressing the limitation of structure-based methods by using fast, predicted structures.
    2.  The combination of ESMFold, ProtTrans, and GVP is a sensible and modern architecture choice, leveraging recent advances in protein language models and geometric deep learning.
    3.  The authors evaluate on independent test sets and compare with several existing methods, which is a strength.
    4.  The observation that residue-level predictions can be used for protein-level function inference is a valuable and potentially impactful finding.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness
        - **Claim pointer** The authors claim that GLMSite "surpasses the latest sequence-based methods and be comparable with structure-based methods" based on results in Table 5.
        - **Evidence pointer** Section 3.3, Table 5, Figure 5
        - **Concern** The comparison with other methods is not sufficiently rigorous. The manuscript does not describe the training and test protocols for the baseline methods. Were they retrained on the same training set? Were their hyperparameters optimized? The reported performance of baseline methods may not be their best achievable performance, leading to an unfair comparison. Additionally, no statistical significance tests (e.g., bootstrapping or DeLong's test for AUC) are reported to support the claim of superiority.
        - **Why it matters** Without a fair and statistically sound comparison, the central claim of the manuscript is not robustly supported. The reader cannot determine if the improvement is due to the method itself or to differences in training protocols.
        - **Resolution test** The authors should provide a detailed description of how each baseline method was trained and evaluated, including any hyperparameter tuning. They should also perform and report statistical significance tests for the differences in performance metrics (e.g., AUC ROC, AUC PR, MCC) between GLMSite and the best-performing baseline on both test sets.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness
        - **Claim pointer** The authors state that "the geometric graph learning is proven to be powerful" and that the GVP module is crucial for performance.
        - **Evidence pointer** Section 3.1, Table 3
        - **Concern** The ablation study is incomplete. The authors compare GLMSite to a BiLSTM baseline, which is a sequence-based method. This comparison does not isolate the contribution of the geometric graph learning component. To demonstrate the importance of the GVP and the graph structure, the authors should compare GLMSite against a variant that uses the same graph structure but a different, non-geometric neural network (e.g., a standard GCN or GAT), and a variant that uses the same GVP but without the graph structure (e.g., operating on a sequence or a set of residues).
        - **Why it matters** The claim that geometric graph learning is powerful is a key methodological contribution. Without a proper ablation study, the specific contribution of this component is not established.
        - **Resolution test** The authors should perform and report an ablation study that isolates the contributions of (a) the graph structure, (b) the GVP module, and (c) the ProtTrans features. This would involve testing variants of the model with one component removed or replaced.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Scientific importance
        - **Claim pointer** The authors claim that "the prediction results can help identify nucleic-acid-binding proteins, demonstrating its potential for protein function discovery."
        - **Evidence pointer** Section 3.4, Figure 6, Supplementary Tables S3, S7, S8
        - **Concern** The validation of the protein-level function inference is weak. The authors use a single dataset (PDB2770) and a single scoring function. The comparison of score distributions in Figure 6 is qualitative. The performance of this protein-level prediction is not compared against existing protein-level function prediction methods. The choice of the scoring function (Equation 6) is not well-justified.
        - **Why it matters** The claim that residue-level predictions are useful for protein-level function is a significant secondary claim. The current evidence is insufficient to support it, as it lacks quantitative performance metrics and comparison to existing approaches.
        - **Resolution test** The authors should provide quantitative metrics (e.g., AUC ROC, precision-recall) for the protein-level classification on PDB2770. They should also compare their protein-level prediction approach against a simple baseline, such as using the maximum residue score or the fraction of residues above a threshold, and ideally against existing protein-level DNA/RNA-binding prediction tools.
    - **R1-M4**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Technical soundness
        - **Claim pointer** The authors state that "the quality of ESMFold predicted structures is high" and that this contributes to the performance.
        - **Evidence pointer** Section 3.2, Figure 4, Supplementary Figures S3, S4
        - **Concern** The analysis of the relationship between structure quality and performance is superficial. The authors report a "low positive correlation" between GDT and AUC PR, but the analysis is not detailed. It is unclear if this correlation is statistically significant. More importantly, the authors do not compare the performance of GLMSite when using ESMFold structures versus using native structures or AlphaFold2 structures. This comparison is crucial to understand the impact of the predicted structure quality on the method's performance.
        - **Why it matters** The choice of ESMFold is a central aspect of the method. The claim that its predicted structures are of sufficient quality needs to be directly tested by comparing the model's performance with different structure sources.
        - **Resolution test** The authors should compare the performance of GLMSite when using (a) ESMFold predicted structures, (b) AlphaFold2 predicted structures, and (c) native experimental structures (where available) on the same test sets. This would directly quantify the impact of structure prediction quality.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Methods, Section 2.3
        - **Evidence pointer** Section 2.3, Equations 1-5
        - **Issue** The equations for the GVP operations are not fully written out. The text says "the calculation process is as follows" but the equations are not fully displayed in the provided text.
        - **Required correction** The authors should ensure that all equations are fully and clearly written out in the final manuscript.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Methods, Section 2.1
        - **Evidence pointer** Section 2.1, Table 1
        - **Issue** The description of the dataset construction is incomplete. The exact criteria for defining a binding residue are given, but the process of transferring annotations from homologous chains is not fully detailed. The number of proteins in the final training and test sets is mentioned, but the number of binding and non-binding residues in each set is not clearly stated.
        - **Required correction** The authors should provide a more detailed description of the dataset construction, including the number of positive and negative residues in each set, and clarify the annotation transfer process.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Methods, Section 2.2
        - **Evidence pointer** Section 2.2
        - **Issue** The description of the node and edge features is incomplete. The text mentions "Node vector features" and "Edge vector features" but does not fully specify all the features used. For example, the exact nature of the "structural properties" from DSSP and the "positional embedding" is not fully described.
        - **Required correction** The authors should provide a complete list of all node and edge features used in the model.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Results, Section 3.1
        - **Evidence pointer** Section 3.1, Table 2
        - **Issue** The standard deviations for the 5-fold CV results are mentioned but not shown in the main text. The text says "the low standard deviations of AUC ROC and AUC PR indicate the stability of the model" but the values are not reported.
        - **Required correction** The authors should report the standard deviations for all metrics in Table 2.
    - **R1-m5**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Results, Section 3.2
        - **Evidence pointer** Section 3.2, Table 4
        - **Issue** The feature analysis is incomplete. The authors test the model with different feature combinations, but they do not report the performance of the model with all features combined (which should be the full GLMSite model) in Table 4. This makes it difficult to assess the marginal contribution of each feature group.
        - **Required correction** The authors should include the performance of the full model (with all features) in Table 4 for comparison.
    - **R1-m6**
        - **Severity** Minor
        - **Axis** Clarity and reproducibility
        - **Affected element** Results, Section 3.5
        - **Evidence pointer** Section 3.5, Figure 7
        - **Issue** The case study is descriptive and lacks quantitative comparison. The authors show a visualization but do not provide a detailed analysis of why GLMSite succeeds or fails in this specific case.
        - **Required correction** The authors should provide a more detailed analysis of the case study, including a comparison of the predictions with the known binding sites and a discussion of the features that contributed to the prediction.
- **Technical failings that need to be addressed before the case is established**
    1.  Lack of a rigorous and fair comparison with baseline methods, including details on their training protocols and statistical significance testing (R1-M1).
    2.  Incomplete ablation study that does not isolate the contribution of the geometric graph learning component (R1-M2).
    3.  Weak validation of the protein-level function inference claim, lacking quantitative metrics and comparison to existing methods (R1-M3).
    4.  Lack of a direct comparison of model performance using ESMFold structures versus native or AlphaFold2 structures to support the claim about structure quality (R1-M4).
- **Assessment against Nature-style criteria**
    - **Originality** The combination of ESMFold, ProtTrans, and GVP for nucleic-acid-binding site prediction is a novel integration of recent techniques. However, the individual components are well-established, and the overall approach is an incremental advance over existing structure-based and sequence-based methods. The originality is moderate.
    - **Scientific importance** The problem of nucleic-acid-binding site prediction is important for understanding protein function. The potential for high-throughput, sequence-only prediction is practically valuable. However, the demonstrated improvement over existing methods is modest, and the impact is not yet fully established. The importance is moderate.
    - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The methods and results are unlikely to attract a broad readership beyond these fields. The interdisciplinary appeal is limited.
    - **Technical soundness** The technical approach is sound in principle, but the current manuscript has significant gaps in the evaluation and validation, as detailed in the Major Concerns. The technical soundness is not fully established.
    - **Readability for nonspecialists** The manuscript is written in a technical style that is accessible to specialists in the field. However, the incomplete descriptions of methods and the lack of clear explanations for some results may hinder readability for a broader audience. The readability is adequate for specialists but not for nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising approach, but the central claims are not sufficiently supported due to the lack of rigorous comparison, incomplete ablation, and weak validation of the secondary claim. The authors should address the Major Concerns before the case for the method is established.

## Risk / unsupported claims
- The claim that GLMSite "surpasses the latest sequence-based methods and be comparable with structure-based methods" is not fully supported due to the lack of a rigorous and fair comparison protocol.
- The claim that "the geometric graph learning is proven to be powerful" is not supported by the current ablation study, which only compares against a sequence-based BiLSTM.
- The claim that "the prediction results can help identify nucleic-acid-binding proteins" is not quantitatively validated and is not compared against existing protein-level prediction methods.
- The claim that "the quality of ESMFold predicted structures is high" is not directly tested by comparing model performance with different structure sources.
- The performance of the model on the 5-fold CV is reported, but the standard deviations are not shown in the main text, making the stability claim unverifiable from the provided material.