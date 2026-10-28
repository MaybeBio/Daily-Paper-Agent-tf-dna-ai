## Review setup
- **Input scope** Full manuscript text including main text, methods, and appendices
- **Assessment boundary** Scientific validity, methodological soundness, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose Ctrl-DNA, a constrained reinforcement learning framework for designing cell-type-specific regulatory DNA sequences. The method applies Lagrangian-regularized policy gradients to autoregressive genomic language models, avoiding value network training. Claims include state-of-the-art performance on human promoter and enhancer design tasks across six cell types, with improved target-cell fitness and off-target constraint satisfaction compared to existing generative and RL-based methods.
- **Visible evidence base** Main text figures (Figure 2, Figure 3), Table 1, Table 2, and appendices A-E. Figure 2 plots are referenced but not visible in the provided text. Table values are referenced but not shown in the provided material.
- **Missing materials affecting confidence** Actual figure contents, table data values, hyperparameter settings (Table 3), percentile statistics (Tables 4-5), full diversity results (Figure 4), and pseudocode from Appendix A are referenced but not provided. This limits quantitative verification of all claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in regulatory DNA design. The methodological contribution of integrating constrained RL with autoregressive genomic language models is interesting and potentially useful. However, the evidence provided is insufficient to fully evaluate the strength of the claims. Key quantitative results are referenced but not shown, and several methodological details require clarification. The work is promising but the case is not fully established from the provided material.

- **Who would be interested in the results, and why** Researchers in synthetic biology, gene therapy, and precision medicine would find this work relevant. The ability to design cell-type-specific regulatory elements has direct applications in targeted gene expression control. Computational biologists working on DNA sequence design, reinforcement learning practitioners interested in biological applications, and researchers developing generative models for genomics would also be interested. The constrained RL framework for sequence generation could have broader applicability beyond regulatory DNA.

- **Major strengths**
  - The problem formulation as a constrained MDP is appropriate and addresses a real limitation in existing approaches
  - The method avoids value network training, which is a practical advantage given sparse reward signals in DNA design
  - The TFBS frequency correlation regularization is a sensible approach to maintain biological plausibility
  - Evaluation across multiple cell types and two regulatory element types (promoters and enhancers) is comprehensive in scope
  - The ablation studies on constraint formulations are valuable for understanding design choices

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that Ctrl-DNA consistently outperforms existing generative and RL-based approaches across all evaluated settings
- **Evidence pointer** Figure 2, Table 1, Table 2 (location not provided in text)
- **Concern** The central performance claims are made without the actual data being visible in the provided material. Figure 2 plots, Table 1 metrics, and Table 2 ablation results are referenced but their contents are not shown. Without seeing the actual numbers, statistical significance, or effect sizes, the strength of the claimed improvements cannot be assessed.
- **Why it matters** The primary contribution of the paper is empirical demonstration of superior performance. If the quantitative evidence is not available for scrutiny, the core claim cannot be verified.
- **Resolution test** Provide the actual figure and table contents with numerical values, error bars or confidence intervals, and statistical significance tests where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The claim that the method achieves stable and efficient optimization without value network training
- **Evidence pointer** Section 3.2, Appendix A (location not provided)
- **Concern** The description of the batch-wise relative policy optimization is incomplete. The pseudocode is referenced but not provided. The exact form of the Lagrangian advantage, the clipping mechanism for the main objective coefficient, and the interaction between the KL penalty and the Lagrangian terms require more precise specification. The stability properties claimed are not theoretically justified.
- **Why it matters** Reproducibility is a fundamental requirement. Without complete algorithmic details, other researchers cannot implement or build upon the method.
- **Resolution test** Provide the full pseudocode, explicit equations for all loss terms, and a clear description of the optimization procedure including hyperparameter sensitivity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Baseline fairness
- **Claim pointer** The claim that Ctrl-DNA outperforms existing RL-based approaches including TACO and PPO-Lagrangian
- **Evidence pointer** Section 4.1, Appendix C (location not provided)
- **Concern** The baseline implementations are described only briefly. It is unclear whether the baselines were given comparable computational budgets, hyperparameter tuning, or architectural flexibility. TACO uses a different reward structure (motif-based), and it is unclear if the comparison is apples-to-apples. The PPO baseline without Lagrangian is not included, which would help isolate the contribution of the constraint mechanism.
- **Why it matters** Unfair or incomparable baselines can lead to misleading conclusions about relative performance.
- **Resolution test** Provide details on baseline hyperparameter tuning, computational budgets, and include additional baselines such as unconstrained PPO to isolate the effect of the constraint mechanism.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The claim that generated sequences capture biologically meaningful, cell-type-specific regulatory motifs
- **Evidence pointer** Section 4.3, Figure 3 (location not provided)
- **Concern** The biological validation is limited to motif frequency analysis. While motif enrichment is suggestive, it does not demonstrate functional activity. The paper would be strengthened by experimental validation or at least comparison with known functional regulatory elements. The claim of biological plausibility is stronger than what the evidence supports.
- **Why it matters** For a paper targeting applications in gene therapy and precision medicine, biological relevance is critical. Computational metrics alone may not translate to functional performance.
- **Resolution test** Add experimental validation or clearly limit claims to computational plausibility. At minimum, compare generated sequences to known functional elements and discuss potential limitations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2, empirical modifications
- **Evidence pointer** Section 3.2 (location not provided)
- **Issue** The description of the replay buffer mixing and the clipping of the main objective coefficient is vague. The rationale for these choices and their impact on performance is not discussed.
- **Required correction** Provide a clearer explanation of these design choices and ideally an ablation showing their contribution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.2, promoter task
- **Evidence pointer** Section 4.2 (location not provided)
- **Issue** The discussion of the promoter task notes that no method succeeds at the strictest constraint for THP1, but the implications of this failure are not fully explored. Is this a fundamental limitation of the approach or a data issue?
- **Required correction** Expand the discussion on the limitations imposed by data distribution and potential strategies to address this.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 4.3, diversity metric
- **Evidence pointer** Section 4.3, Figure 3b (location not provided)
- **Issue** The diversity metric is reported as Shannon entropy, but the units and interpretation are not explained. It is unclear what level of diversity is desirable and how it trades off against fitness.
- **Required correction** Provide context for interpreting the diversity values and discuss the trade-off between diversity and fitness optimization.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Appendix A, hyperparameters
- **Evidence pointer** Table 3 (location not provided)
- **Issue** The hyperparameter table is referenced but not shown. Key parameters such as learning rates, batch sizes, and the number of generated sequences per iteration are not visible.
- **Required correction** Include the full hyperparameter table in the main text or ensure it is available in the appendix.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Missing quantitative results for central performance claims
  - R1-M2: Incomplete algorithmic description preventing reproduction
  - R1-M3: Insufficient baseline comparison details
  - R1-M4: Overstated biological plausibility claims

- **Assessment against Nature-style criteria**
  - **Originality** The combination of constrained RL with Lagrangian multipliers for regulatory DNA design is a novel contribution. The application of batch-normalized rewards without value networks in this context is also original. However, the individual components (RL for DNA design, Lagrangian methods for constrained RL) are established, and the novelty lies primarily in their integration.
  - **Scientific importance** The problem of cell-type-specific regulatory element design is important for multiple biomedical applications. A reliable computational method for this task would be valuable. However, the importance of the specific contribution over existing methods needs to be demonstrated more clearly with visible quantitative evidence.
  - **Interdisciplinary readership** The work bridges machine learning, genomics, and synthetic biology. The writing is generally accessible, though some RL terminology may be challenging for biology-focused readers. The biological motivation is clearly stated. The paper would benefit from a brief primer on constrained RL for non-specialists.
  - **Technical soundness** The methodological approach is reasonable, but the incomplete description of the algorithm and the missing quantitative results prevent full assessment. The ablation studies are a good start but need to be more comprehensive. The lack of statistical significance testing is a concern.
  - **Readability for nonspecialists** The introduction and problem formulation are clear. The methods section is dense but understandable for readers with RL background. The results section would benefit from more interpretation of the practical implications. The discussion is brief and could be expanded.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the problem is important, but the current evidence is insufficient to fully establish the claims. The authors should provide the missing quantitative data, complete the algorithmic description, strengthen the baseline comparisons, and temper the biological plausibility claims. With these revisions, the work could make a solid contribution to the field.