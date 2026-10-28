## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Methodological soundness, biological applicability, and claims as presented in the text; no assessment of code, data availability, or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors propose an extrinsic-noise-driven neural stochastic differential equation (END-nSDE) framework using Wasserstein distance to reconstruct SDEs from noisy time-series data across heterogeneous cell populations. They demonstrate its effectiveness on three biological systems: circadian rhythms, RPA-DNA binding, and NFκB signaling, claiming superior performance over RNNs, LSTMs, Gaussian processes, and neural ODEs.
- **Visible evidence base** Text descriptions of methods, results, and comparisons; numerical error values reported in Section 3.1; qualitative statements of performance in Sections 3.2 and 3.3
- **Missing materials affecting confidence** Figures 1-9, Tables 1, S1 Text appendices A-H, experimental dataset details, code availability, hyperparameter settings, and full numerical results for Sections 3.2 and 3.3

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable extension of neural SDE reconstruction methods to account for extrinsic noise through parameter conditioning. The core idea of conditioning the drift and diffusion networks on biological parameters is sensible and addresses a real limitation of prior work. However, the evidence presented in the text alone is insufficient to fully evaluate the method's performance, particularly for the RPA-DNA and NFκB applications where quantitative results are largely absent from the visible text. The claims of superiority over benchmark methods require more rigorous statistical comparison. The biological insights derived from the NFκB application are preliminary and limited by strong simplifying assumptions.

- **Who would be interested in the results, and why** Computational biologists and biophysicists working on stochastic gene regulation, single-cell dynamics, and inference of dynamical systems from noisy data. Researchers developing neural differential equation methods for scientific applications would also find the methodological extension relevant. The potential to infer parameter-dependent dynamics from heterogeneous population data addresses a common challenge in quantitative biology.

- **Major strengths**
  1. The extension of W2-distance-based neural SDE reconstruction to incorporate parameter conditioning is a natural and useful methodological advance over prior work
  2. The three biological applications span distinct dynamical regimes (oscillatory, binding kinetics, signaling), demonstrating versatility
  3. The explicit treatment of both intrinsic and extrinsic noise is conceptually well-motivated and clearly explained
  4. The discussion of limitations, particularly regarding drift heterogeneity and computational cost, is honest and constructive

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims the END-nSDE method "outperforms existing time-series analysis methods such as recurrent neural networks (RNNs) and long short-term memory networks (LSTMs)" and also outperforms Gaussian processes and neural ODEs
- **Evidence pointer** Section 3.2, Table 1 (not visible); Section 3.3 (text only)
- **Concern** The claim of superior performance over benchmark methods is stated in the abstract and introduction, and referenced in Section 3.2, but the visible text provides no quantitative comparison results. Table 1 is referenced but not available for inspection. For the NFκB application, no benchmark comparisons are described at all. Without access to the actual comparison metrics, statistical significance tests, or error bars, this central claim cannot be evaluated.
- **Why it matters** The performance comparison against existing methods is a primary contribution claim of the paper. If the comparison is not rigorously established, the added value of END-nSDE over existing approaches remains unclear.
- **Resolution test** Provide the full comparison table with error metrics, confidence intervals, and statistical tests for all benchmark methods across all three applications. Ideally, include learning curves and computational cost comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The method "can accurately reconstruct the drift function" and "approximate the diffusion function well" for the circadian model, with reported mean errors of 0.15 (drift) and 0.16 (diffusion) for constant noise, and larger errors for more complex noise forms
- **Evidence pointer** Section 3.1, Figure 4 (not visible)
- **Concern** The reported reconstruction errors for the drift function (0.15 mean relative error) and diffusion function (0.16-0.41 mean relative error) are substantial. A 15% error in drift reconstruction could significantly affect downstream predictions, especially for oscillatory systems where small parameter errors can lead to phase drift. The manuscript does not discuss whether these error levels are acceptable for the intended applications, nor does it provide error analysis as a function of trajectory length, number of trajectories, or noise magnitude. The claim of "accurate" reconstruction requires context regarding what accuracy is needed for biological predictions.
- **Why it matters** The practical utility of the method depends on whether reconstruction errors are small enough for reliable biological inference. Without error characterization or comparison to required accuracy thresholds, the significance of the reported performance is unclear.
- **Resolution test** Provide systematic error analysis showing reconstruction accuracy as a function of data quantity, noise levels, and system complexity. Discuss what accuracy is required for meaningful biological predictions in each application.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological validity of assumptions
- **Claim pointer** For the NFκB application, the authors assume "(1) all cells share the same drift function, and (2) cells with trajectories deviating similarly from their ODE predictions have the same noise intensities"
- **Evidence pointer** Section 3.3.2, Figure 8 (not visible)
- **Concern** The assumption that all cells share the same drift function is a strong simplification that contradicts the stated motivation of modeling cellular heterogeneity. If drift functions vary across cells, the reconstructed SDE represents an average dynamics that may not capture the true heterogeneity. The manuscript acknowledges this limitation but does not quantify its impact on the reconstruction quality or biological conclusions. The grouping of cells by cosine similarity to a representative trajectory is also a heuristic that may not correspond to meaningful biological subpopulations.
- **Why it matters** The biological interpretability of the reconstructed NFκB dynamics depends on whether the modeling assumptions are valid. If the assumptions are violated, the inferred noise intensities and predicted trajectories may be misleading.
- **Resolution test** Validate the assumptions on synthetic data where the true drift heterogeneity is known. Quantify the bias introduced by assuming a shared drift function. Alternatively, demonstrate that the method is robust to moderate violations of these assumptions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and scalability
- **Claim pointer** The method is presented as "a useful surrogate modeling approach for complex biophysical processes, where high-fidelity mechanistic models may be impractical"
- **Evidence pointer** Section 4, Discussion
- **Concern** The three applications are relatively low-dimensional (2D circadian, 2D RPA, and a 52D NFκB system where only 2 variables are directly used in the loss). The manuscript does not discuss how the method scales to higher-dimensional systems or systems with more complex noise structures. The NFκB example uses only 2 of 52 variables in the loss function, which raises questions about whether the method can effectively handle systems where many variables are experimentally observable. The computational cost of training is mentioned as a limitation but not quantified.
- **Why it matters** The claimed general utility of the method depends on its applicability to realistic biological systems, which are often high-dimensional with partial observations. Without scalability analysis, the practical scope of the method is unclear.
- **Resolution test** Provide scaling analysis with respect to system dimensionality, number of parameters, and dataset size. Demonstrate the method on a higher-dimensional system with more observable variables.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Equation (8)
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The distinction between the proposed extrinsic-noise-driven loss function in Equation (8) and the original W2 loss in Equation (3) is not fully explained. Specifically, it is unclear how the integration over the parameter set Λ is performed in practice and whether this introduces additional computational overhead or approximation errors.
- **Required correction** Clarify the practical implementation of the parameter integration in Equation (8), including any discretization or sampling strategies used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1, Algorithm 1
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The algorithm description lacks details on hyperparameter selection, learning rate schedules, initialization strategies, and convergence criteria. The reference to Table A in S1 Text is noted, but the main text should provide sufficient information for a reader to understand the key training choices.
- **Required correction** Include key hyperparameters in the main text or provide a more detailed summary of the training setup.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 3.1, error metrics
- **Evidence pointer** Section 3.1, location not provided
- **Issue** The error metrics in Equations (14) and (15) are defined, but the number of independent simulations or experimental replicates used to compute these errors is not stated. Without this information, the reliability of the reported mean errors cannot be assessed.
- **Required correction** Report the number of independent runs and, if possible, confidence intervals for the error metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Section 3.3.2, NFκB results
- **Evidence pointer** Section 3.3.2, location not provided
- **Issue** The biological significance of the inferred noise intensities for NFκB dynamics is not discussed. What do the specific values of noise intensity imply for NFκB signaling biology? How do these compare to known sources of variability in immune signaling?
- **Required correction** Add a brief discussion of the biological implications of the inferred noise parameters.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison fairness
- **Affected element** Section 3.2, benchmark comparisons
- **Evidence pointer** Section 3.2, location not provided
- **Issue** The comparison with RNN, LSTM, Gaussian process, and neural ODE methods is described, but the training procedures, hyperparameter tuning, and architectural choices for these benchmark methods are not described in the main text. Without this information, it is difficult to assess whether the comparison is fair.
- **Required correction** Provide details on benchmark implementations or reference a supplementary section where these are described.

- **Technical failings that need to be addressed before the case is established**
  1. Quantitative comparison results against benchmark methods are not visible in the provided text (R1-M1)
  2. Error analysis is incomplete, lacking confidence intervals and systematic characterization (R1-M2)
  3. The impact of strong modeling assumptions on biological conclusions is not quantified (R1-M3)
  4. Scalability to higher-dimensional systems is not demonstrated (R1-M4)

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The extension of neural SDE reconstruction to parameter-conditioned models is incremental but useful. The core methodology builds directly on prior work by the same group, and the novelty lies primarily in the parameter conditioning rather than a fundamentally new approach.
  - **Scientific importance** Moderate. The ability to infer parameter-dependent stochastic dynamics from heterogeneous population data is relevant to quantitative biology, but the demonstrated applications are relatively simple and the biological insights are preliminary.
  - **Interdisciplinary readership** Limited. The manuscript is primarily accessible to computational biologists and machine learning researchers. The biological applications are described at a level that may not engage experimental biologists, and the methodological details may be too technical for a broad readership.
  - **Technical soundness** Not fully assessable from the provided text. The methodological framework is reasonable, but the missing quantitative results and incomplete error analysis prevent a full evaluation of technical soundness.
  - **Readability for nonspecialists** Adequate but improvable. The introduction and discussion are clearly written, but the methods section assumes familiarity with neural SDEs and Wasserstein distance. The biological motivation could be strengthened with more concrete examples of how extrinsic noise affects specific biological outcomes.

- **Recommendation posture** Supportive if technical concerns are resolved. The methodological extension is sensible and the applications are relevant, but the current evidence base is insufficient to fully establish the claims of superior performance and broad applicability. The authors should provide complete quantitative results, rigorous statistical comparisons, and a more thorough error analysis before the case is fully established.