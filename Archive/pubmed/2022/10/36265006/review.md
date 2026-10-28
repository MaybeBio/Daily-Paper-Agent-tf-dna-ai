## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence; no assessment of code functionality or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors propose Deep Mendelian Randomization (DeepMR), a method combining in silico mutagenesis with Mendelian randomization to estimate causal relationships between genomic marks learned by multi-task deep learning models. They report accurate global causal effect estimates in simulations, with degraded coverage under sequence-dependent confounding, and apply the method to BPNet to validate and generate hypotheses about transcription factor relationships in reprogramming.
- **Visible evidence base** Methods description, simulation design, results narrative, and discussion; figures, tables, and supplementary materials referenced but not provided
- **Missing materials affecting confidence** Figures 1-3, Tables 1, S1 Fig, S1 Text, S2 Text, and the BPNet repository details; these are essential for evaluating the quantitative claims, simulation outcomes, and the validity of the application results

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially useful approach for interrogating causal knowledge in genomic deep learning models. The combination of Mendelian randomization with in silico mutagenesis is novel and well-motivated. However, the evidence provided in the text alone is insufficient to fully assess the method's validity, particularly regarding simulation performance, statistical properties, and the biological application. The claims are plausible but require the missing figures and tables to be verified. The discussion of assumptions is thoughtful, but the manuscript would benefit from clearer articulation of limitations and more rigorous validation of the causal interpretation.
- **Who would be interested in the results, and why** Researchers in computational genomics, deep learning interpretability, and regulatory genomics would find this work relevant. Those developing or using multi-task genomic models would be interested in methods to extract causal or mechanistic insights from such models. The approach could also appeal to statisticians working on causal inference with complex, high-dimensional data.
- **Major strengths** The conceptual framing is clear and addresses an important gap in genomic deep learning. The methodological combination is creative and builds sensibly on existing tools. The simulation design is thoughtful, covering multiple confounding scenarios. The application to a real biological system (reprogramming TFs) demonstrates practical utility. The discussion of assumptions and limitations is honest and informative.
- **Major Concerns** The following concerns are identified.
- **Minor Comments** The following comments are identified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The approach is novel in combining MR with in silico mutagenesis for genomic DL models. Scientific importance: Potentially high for understanding model-learned biology, but the impact depends on the robustness and generalizability of the method, which is not fully established here. Interdisciplinary readership: The work bridges machine learning, statistics, and genomics, and would appeal to a broad audience if the claims are well-supported. Technical soundness: The methodological description is reasonable, but the statistical properties and assumptions require more rigorous validation and discussion. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some statistical concepts may be challenging for a general audience.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "DeepMR gives accurate and unbiased estimates of the 'true' global causal effect" in simulations.
- **Evidence pointer** Results section, Simulation subsection; Figure 2 and Table 1 (not provided)
- **Concern** The claim of accurate and unbiased estimation is central to the manuscript's contribution. However, the quantitative evidence for this claim is entirely contained in Figure 2 and Table 1, which are not provided in the submitted material. The text describes "near-perfect agreement" in some scenarios and "underestimation" in others, but without the actual data, the accuracy, precision, and bias of the estimates cannot be independently assessed. The correlation metric and the frequency of coverage are mentioned but not quantified.
- **Why it matters** The validity of the entire method rests on its demonstrated performance in simulation. Without access to the quantitative results, the reader cannot verify the strength of the evidence or the magnitude of the reported effects. This is a blocking issue for establishing the method's credibility.
- **Resolution test** Provide Figure 2 and Table 1, or a detailed numerical summary of the simulation results, including correlation coefficients, bias, coverage probabilities, and confidence intervals for all scenarios.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** "DeepMR obtains local (locus specific) and global estimates of (an assumed) linear causal relationship between marks."
- **Evidence pointer** Methods section, Algorithm overview; Figure 1 (not provided)
- **Concern** The manuscript assumes a linear causal relationship between marks, but the validity of this assumption is not thoroughly examined. The simulation model is constructed with a specific functional form (multiplicative in raw counts, transformed to Anscombe space), and it is unclear how violations of linearity, such as strong cooperativity or saturation effects, would affect the estimates. The discussion mentions "local linearity" as a weaker condition, but the practical implications and the range of validity are not explored.
- **Why it matters** If the linearity assumption is violated in real biological systems, the causal effect estimates could be biased or misleading. The manuscript needs to more rigorously justify or test this assumption, or at least clearly delineate the conditions under which the method is expected to work.
- **Resolution test** Add a simulation scenario with a non-linear relationship between exposure and outcome, or provide a theoretical analysis of the bias introduced by non-linearity. Discuss the practical implications of the linearity assumption for real-world applications.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "DeepMR's causal effect estimates validate previously hypothesized relationships between TFs and suggest new relationships for future investigation."
- **Evidence pointer** Results section, Application to reprogramming TFs; Figure 3 (not provided)
- **Concern** The application to BPNet is a key demonstration of the method's utility. However, the results are presented qualitatively in the text, with the actual estimates and their uncertainties contained in Figure 3, which is not provided. The claim of "validating" previous hypotheses is strong, but without seeing the effect sizes, confidence intervals, and the comparison to the original hypotheses, this claim cannot be evaluated. The text notes that the 2τ range includes 0 for some relationships, which tempers the claim, but the overall picture is unclear.
- **Why it matters** The biological application is what makes the method relevant to a broader audience. If the results are not clearly presented and statistically robust, the practical value of the method is diminished.
- **Resolution test** Provide Figure 3 and a detailed description of the results, including effect sizes, confidence intervals, and a clear comparison to the hypotheses from the original BPNet paper.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepMR can work with any MR method that takes multiple instruments' effect sizes and standard errors as inputs."
- **Evidence pointer** Methods section, Algorithm overview; Results section, Simulation
- **Concern** The manuscript only tests two MR methods: a simple baseline and MR-Egger. The claim of general compatibility with any MR method is not empirically demonstrated. Different MR methods have different assumptions and requirements, and it is unclear if the output of the in silico mutagenesis step (effect sizes and standard errors) is suitable for all of them. For example, methods that require individual-level data or specific instrument properties may not be directly applicable.
- **Why it matters** The claim of broad compatibility is a selling point of the method, but it is not supported by evidence. If the method only works with a limited set of MR techniques, this should be stated clearly.
- **Resolution test** Either test the method with additional MR methods (e.g., inverse-variance weighting, weighted median) or temper the claim to reflect the methods that have been validated.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, Algorithm overview
- **Evidence pointer** "Step 4 requires variant effect estimates for each mutation for both the exposure X and outcome Y."
- **Issue** The algorithm overview is described in a numbered list, but the steps are not fully detailed. For example, the filtering step (step 5) is mentioned but not explained.
- **Required correction** Provide a more detailed description of each step in the algorithm, particularly the filtering criteria and how the local estimates are combined into a global estimate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, Simulation
- **Evidence pointer** "We train ensembles of convolutional neural network (CNN) models on the data produced in each scenario..."
- **Issue** The simulation parameters are described, but the training details (e.g., number of epochs, learning rate schedule, batch size) are not fully specified. The code is available, but the manuscript should provide enough detail for replication without relying on the code.
- **Required correction** Add a table or paragraph with the key hyperparameters and training details for the CNN models.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** "DeepMR predicts that Sox2 acts on Klf4 more strongly than the reverse."
- **Issue** This is presented as a new hypothesis, but the biological interpretation is not discussed. What does this mean for reprogramming? Is there any existing evidence that supports or contradicts this?
- **Required correction** Add a brief discussion of the biological implications of this prediction and how it could be tested experimentally.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction section
- **Evidence pointer** "Here we ask: do such multi-task models, through learning to predict multiple marks jointly, gain an implicit understanding of mechanistic, causal relationships between marks?"
- **Issue** The introduction is well-written, but the distinction between "causal knowledge" and "predictive association" could be made more explicit. The term "causal knowledge" is used throughout, but it is not formally defined.
- **Required correction** Define what is meant by "causal knowledge" in the context of deep learning models, and clarify how DeepMR's estimates relate to this definition.

## Risk / unsupported claims
- The claim of "accurate and unbiased estimates" in simulations is unsupported without Figure 2 and Table 1.
- The claim of "validating" previous hypotheses in the BPNet application is unsupported without Figure 3.
- The claim of general compatibility with any MR method is unsupported, as only two methods were tested.
- The assumption of linearity is not rigorously tested or discussed in sufficient depth.
- The biological significance of the new predictions (e.g., Sox2 on Klf4) is not discussed.