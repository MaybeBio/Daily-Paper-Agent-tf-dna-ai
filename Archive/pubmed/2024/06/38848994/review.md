## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, conclusion, and appendix
- **Assessment boundary** Scientific validity, technical soundness, novelty, and clarity of the proposed gene regulatory neural network (GRNN) framework for nonlinear classification
- **Shared manuscript claim summary** The authors propose a mathematical framework that maps gene regulatory networks to artificial neural networks, termed gene regulatory neural networks (GRNNs), by modeling transcription and translation as weighted operations with sigmoidal activation. They claim that stability analysis via eigenvalues and Lyapunov's theorem ensures reliable computing, and demonstrate nonlinear classifiers using two generic multilayer sub-GRNNs and an E. coli-derived sub-GRNN.
- **Visible evidence base** Mathematical derivations (Eqs. 1-27), algorithmic pseudocode (Algorithms 1-2), simulation results for temporal stability (Figs. 5, 8, 10, 12), classification area plots (Figs. 9, 11, 13), and parameter tables (Tables 1-3)
- **Missing materials affecting confidence** No experimental validation data, no comparison with existing classification methods, no quantitative performance metrics (e.g., accuracy, precision), no code or data availability statement, no sensitivity analysis of model parameters

## Reviewer
- **Overall assessment** The manuscript presents an interesting conceptual bridge between gene regulatory networks and neuromorphic computing, with a plausible mathematical formulation. However, the work remains largely theoretical with limited validation. The stability analysis is standard and adds little beyond confirming well-known properties of the proposed ODE model. The classification demonstrations are qualitative, lacking quantitative benchmarks against established classifiers. The novelty is incremental, building on prior work by the same group (ref. 19), and the practical feasibility of implementing such wet-neuromorphic systems is not critically examined. The manuscript would benefit from clearer articulation of what is genuinely new, quantitative evaluation of classification performance, and discussion of biological realism and implementation challenges.

- **Who would be interested in the results, and why** Researchers in synthetic biology, unconventional computing, and bio-inspired AI may find the conceptual framework interesting. Those working on molecular computing or DNA-based information processing could see potential applications. However, the lack of experimental demonstration limits appeal to experimental biologists. Computational neuroscientists might be tangentially interested in the analogy between GRNs and ANNs, but the simplified model may not capture sufficient biological detail to be compelling.

- **Major strengths** 
  1. The conceptual mapping from GRNs to ANNs is clearly articulated and mathematically formalized, providing a useful framework for thinking about biological computing.
  2. The inclusion of both eigenvalue-based and Lyapunov-based stability analyses is thorough, and the derivation of the Lyapunov derivative (Eq. 27) is a nontrivial contribution.
  3. The use of a real E. coli sub-GRNN adds biological grounding and demonstrates the framework's applicability to actual regulatory networks.
  4. The parameter sensitivity demonstrations (showing how K_A shifts decision boundaries) provide insight into how synthetic biology could tune classifier behavior.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Lyapunov-based analysis "determines the time at which the stability is achieved" and that this ensures "reliable computing with minimal concentration fluctuations."
- **Evidence pointer** Section "Gene expression stability analysis", Eqs. 25-27, Fig. 5
- **Concern** The Lyapunov analysis as presented does not establish what the authors claim. The function V is defined as a quadratic deviation from equilibrium, and its derivative is computed. However, the analysis only shows that dV/dt is negative (approaching zero), which is a standard result for a stable linear system. The threshold V̇_th is chosen arbitrarily (e.g., −1×10⁻¹¹) without biological or computational justification. More critically, the "time to stability" t̄ is not connected to any computational reliability metric. The authors do not demonstrate that computations performed before t̄ are unreliable or that after t̄ they are reliable. The claim that this analysis "facilitates reliable GRNN computing" is therefore unsupported.
- **Why it matters** The stability analysis is presented as a core contribution and a prerequisite for reliable computing. If the connection between stability time and computational reliability is not established, the practical value of this analysis for the proposed wet-neuromorphic computing paradigm is unclear. The manuscript's central thesis depends on this link.
- **Resolution test** The authors should either (a) provide a formal definition of computational reliability in terms of the Lyapunov function and demonstrate that the threshold V̇_th corresponds to a meaningful error bound, or (b) temper the claims to state that the analysis confirms asymptotic stability without asserting a direct link to computational reliability.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "the GRN exhibits NN properties as the gene-perceptron demonstrated sigmoidal-like behavior for multiple inputs and tunable decision boundaries," and that this "showcases aspects of biological AI."
- **Evidence pointer** Section "Results", Figs. 9, 11, 13
- **Concern** The classification demonstrations are purely qualitative. No quantitative performance metrics are provided (e.g., classification accuracy, F1 score, comparison with linear classifiers or standard nonlinear classifiers). The decision boundaries are shown for specific parameter sets, but there is no systematic evaluation of how well these classifiers would perform on actual classification tasks. The claim that these are "nonlinear classifiers" is trivially true given the sigmoidal activation, but the practical utility is not demonstrated. Moreover, the classification boundaries appear to be simple thresholded regions rather than learned decision boundaries, which raises the question of whether this framework offers any advantage over simpler threshold-based classifiers.
- **Why it matters** The manuscript's stated contribution is establishing "nonlinear classifiers for molecular machine learning." Without quantitative evaluation, the reader cannot assess whether this approach is competitive with or superior to existing classification methods, whether biological or conventional. The scientific importance hinges on demonstrating that GRNNs can perform useful classification tasks.
- **Resolution test** The authors should implement a concrete classification task (e.g., binary classification with known ground truth), report standard performance metrics, and compare against appropriate baselines (e.g., logistic regression, SVM, or simple threshold classifiers). This would establish whether the GRNN framework offers genuine advantages.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the eigenvalue-based stability analysis verifies the existence of upper bounds of transcription and translation guaranteeing minimal concentration fluctuations that can reduce potential computing errors."
- **Evidence pointer** Section "Stability of gene-perceptron based on eigenvalues", Eqs. 6-7, Algorithm 1
- **Concern** The eigenvalue analysis is trivial for the proposed model. The Jacobian is a 2x2 diagonal matrix with eigenvalues −d1i and −d2i, which are always negative for positive degradation rates. This confirms stability but provides no insight into "upper bounds" or "minimal concentration fluctuations." The authors do not derive any quantitative bounds on concentration fluctuations or connect these to error rates in computing. The analysis is mathematically correct but adds little beyond what is obvious from the model structure.
- **Why it matters** The manuscript presents this as a contribution, but it is a standard stability check that does not inform the design or operation of GRNN-based classifiers. The claimed connection to error reduction is not substantiated.
- **Resolution test** Either derive explicit bounds on concentration fluctuations as functions of model parameters and connect these to computational error, or remove the claim that this analysis guarantees minimal fluctuations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The authors claim to develop "nonlinear classifiers for molecular machine learning using the inherent sigmoidal nonlinear behavior of gene expression."
- **Evidence pointer** Entire manuscript, particularly Introduction and Conclusion
- **Concern** The conceptual analogy between gene regulatory networks and neural networks is well established in the literature, and the authors' prior work (ref. 19) already introduced the GRNN concept. The present manuscript extends this by adding stability analysis and classification examples, but the core idea of using sigmoidal gene expression for classification is not fundamentally new. The specific mathematical formulation (Hill function kinetics) is standard in systems biology. The novelty appears incremental rather than transformative.
- **Why it matters** For a journal like Biophysical Reports, the expectation is that the work provides a meaningful advance over prior art. If the GRNN concept was already introduced in ref. 19, the authors need to clearly articulate what is genuinely new in this manuscript beyond incremental technical details.
- **Resolution test** The authors should explicitly state what is new relative to ref. 19 and other prior work on gene regulatory network computing, and justify why this advance is significant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The authors state that "our model has the potential to transform GRNs into GRNNs when the suitable parameters are established for the dual-layered chemical reaction model."
- **Evidence pointer** Conclusion
- **Concern** The manuscript does not address the practical feasibility of implementing the proposed GRNN classifiers in living cells. Key questions remain unanswered: How would the required parameters (K_A, k1, k2, d1, d2) be set in a real biological system? What are the noise levels and cell-to-cell variability, and how would these affect classification reliability? How would the input concentrations [TF] be controlled experimentally? The authors mention synthetic biology but provide no concrete implementation strategy or discussion of challenges.
- **Why it matters** The stated vision is "wet-neuromorphic computing," which implies eventual physical implementation. Without addressing feasibility, the work remains a purely theoretical exercise, limiting its relevance to experimental researchers and reducing its impact across disciplines.
- **Resolution test** Add a discussion section addressing implementation challenges, including parameter tuning strategies, noise robustness, and potential experimental approaches. Alternatively, clearly scope the manuscript as purely theoretical and avoid claims about practical potential.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Eq. 5
- **Evidence pointer** Section "Modeling translation of a RNA"
- **Issue** The solution for protein concentration in Eq. 5 appears to have a formatting issue with the term "e−d2it×[R]i(0)k2i1(d2i−d1i)" which is difficult to parse. The equation is presented in a way that may confuse readers.
- **Required correction** Reformat Eq. 5 to clearly show the structure of the solution, possibly by breaking it into multiple lines or using clearer notation for the exponential terms.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "GRNN application for nonlinear classifiers"
- **Evidence pointer** Introduction, bullet point 3
- **Issue** The third contribution bullet states "By varying parameters of the chemical reactions, we demonstrate how the classification area can be shifted, which can serve as a tool for engineering the GRN." This is vague; it is unclear what "engineering the GRN" means in practice and how this would be achieved.
- **Required correction** Provide a more specific explanation of how parameter variation corresponds to genetic engineering strategies, or rephrase to be more precise about the claimed contribution.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Table 3
- **Evidence pointer** Section "E. coli sub-GRNN classification analysis"
- **Issue** The parameter values in Table 3 are presented with references, but the units for K_A are listed as "×10⁻⁷" without specifying the base units. The values for d2i are given as percentages (3.5%), which is unusual for a rate constant and may confuse readers.
- **Required correction** Clarify the units for all parameters, and either convert d2i to standard rate units or explain why percentage is used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 13
- **Evidence pointer** Section "E. coli sub-GRNN classification analysis"
- **Issue** The caption for Fig. 13 does not explain what the axes represent or what the color/shading indicates. The reader cannot interpret the classification regions without this information.
- **Required correction** Expand the figure caption to describe axes, color coding, and the meaning of the decision boundary.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Algorithm 2
- **Evidence pointer** Appendix
- **Issue** The pseudocode in Algorithm 2 is somewhat convoluted, particularly the FindMinT function which uses argmin over |V̇−V̇_th|. The logic of when the function returns a time versus an error message is not immediately clear.
- **Required correction** Simplify the pseudocode or add explanatory comments to clarify the control flow and the meaning of the output.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Eq. 14
- **Evidence pointer** Section "GRNN analysis"
- **Issue** The generalization of the Lyapunov derivative to multiple TFs in Eq. 14 is stated without derivation. It is not clear how the product over j TFs arises from the single-TF case, and whether this generalization is mathematically justified.
- **Required correction** Provide a derivation or at least a brief justification for the multi-TF form of Eq. 14.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Stability of a gene-perceptron using the Lyapunov function"
- **Evidence pointer** Fig. 5
- **Issue** The description of Fig. 5 states that the gene-perceptron "accelerates toward equilibrium within the time window t≤5" and "subsequently slows this tendency after t≈5." This is a qualitative observation, but the figure itself is not described in terms of what is plotted (e.g., V̇ vs. t, or V vs. t).
- **Required correction** Clarify what is plotted in Fig. 5 and how the reader should interpret the time windows mentioned in the text.

## Risk / unsupported claims
- The claim that stability analysis "guarantees minimal concentration fluctuations and reduced computing errors" is not quantitatively supported.
- The claim that the GRNN framework "showcases aspects of biological AI" is an overstatement given the lack of experimental validation or comparison with biological neural systems.
- The classification performance of the proposed GRNN classifiers is not evaluated against any benchmark or alternative method, making the claim of "nonlinear classifiers" unsubstantiated in terms of practical utility.
- The assertion that "modifying the half-maximal RNA concentration K_A can significantly expand the classification area" is based on only two parameter sets and lacks systematic analysis.
- The practical feasibility of implementing the proposed framework in living cells is asserted but not discussed, making the "wet-neuromorphic computing" claims speculative.