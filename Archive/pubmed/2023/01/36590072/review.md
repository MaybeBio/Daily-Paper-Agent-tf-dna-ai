## Review setup
- **Input scope** Full manuscript text (review article, no supplementary materials provided)
- **Assessment boundary** Scientific content, logical coherence, evidence quality, and clarity of the arguments presented in the manuscript; no assessment of formatting or editorial style
- **Shared manuscript claim summary** The authors argue that eukaryotic gene regulation is likely non-equilibrium (NEQ) in nature, that the space of possible NEQ models is vast but mostly uninteresting, and that a normative theoretical approach—prescribing which regulatory phenotypes evolution may have optimized—can help navigate this space to identify biologically relevant models. They support this with toy models and a review of indirect evidence.
- **Visible evidence base** Main text, figures referenced (Figures 1–3), abstract, simulation code repository link, and references cited within the text
- **Missing materials affecting confidence** Supplementary information, figure files, simulation code contents, and detailed model derivations were not provided; these would be needed to fully evaluate the toy models and the normative approach

## Reviewer
- **Overall assessment** This is a thought-provoking and timely review that addresses a fundamental question in gene regulation: whether eukaryotic transcriptional regulation operates at equilibrium or out of it. The authors make a compelling case that NEQ mechanisms deserve serious consideration, and they propose a novel normative framework to focus theoretical and experimental efforts. The manuscript is well-structured, clearly written, and accessible to a broad audience. However, the review is largely conceptual and relies on toy models that are not fully described in the provided text. The evidence for NEQ regulation in eukaryotes is presented as suggestive rather than definitive, and the normative approach, while promising, is not developed to the point of yielding concrete, testable predictions. The manuscript would benefit from a more detailed exposition of the toy models and a clearer articulation of how the normative approach can be operationalized in practice.
- **Who would be interested in the results, and why** Researchers in gene regulation, systems biology, biophysics, and theoretical biology would find this review valuable. It bridges molecular biology and non-equilibrium physics, offering a framework that could inspire new experimental designs and theoretical analyses. The discussion of energy costs and evolutionary selection is relevant to those studying cellular resource allocation and evolutionary dynamics. The review is also accessible to computational biologists interested in model selection and inference in biological systems.
- **Major strengths** The manuscript addresses a significant and under-explored question with clarity and intellectual honesty. The authors carefully distinguish between equilibrium and non-equilibrium definitions, acknowledge the limitations of current evidence, and avoid overclaiming. The toy models, while simple, effectively illustrate key concepts such as proofreading and higher-order cooperativity. The normative approach is a novel and potentially influential contribution, offering a principled way to narrow the space of NEQ models. The writing is engaging and the use of figures (as described) appears to support the narrative well.
- **Major Concerns** The toy models are described only in general terms; without the code or detailed derivations, it is impossible to verify the claims about model behavior or the comparisons between EQ and NEQ models. The evidence for NEQ regulation in eukaryotes is largely circumstantial, and the authors do not provide a systematic review of experimental studies that directly test EQ vs. NEQ hypotheses. The normative approach, while conceptually appealing, is not developed into a concrete methodology; the authors do not specify how to choose the phenotypes to optimize, how to handle trade-offs between phenotypes, or how to validate the resulting model ensembles against data. The claim that "most of the NEQ model space is uninteresting" is asserted but not quantitatively supported. The discussion of energetic costs is speculative and does not engage with quantitative estimates of the ATP costs of specific regulatory mechanisms.
- **Minor Comments** The manuscript would benefit from a glossary of terms for non-specialist readers (e.g., detailed balance, entropy production, proofreading). The references to figures are frequent but the figures themselves are not provided; this limits the reader's ability to follow the arguments. The section on "Tantalizing cues for NEQ regulation" is somewhat anecdotal; a more structured summary of experimental evidence would strengthen the case. The authors mention "recent work" in several places without providing specific citations in the text (though references are listed); this could be clarified. The code repository link is a positive feature, but the manuscript should state the software version and dependencies.
- **Technical failings that need to be addressed before the case is established** The toy models are not fully specified, making it impossible to reproduce or verify the results. The normative approach lacks a formal definition and a worked example with real data. The evidence review is not systematic and does not include a critical assessment of alternative EQ explanations for the cited observations.
- **Assessment against Nature-style criteria** Originality: High. The question of EQ vs. NEQ in eukaryotic regulation is important, and the normative approach is a fresh perspective. Scientific importance: High. The outcome could reshape how researchers model and interpret gene regulation. Interdisciplinary readership: Good. The manuscript is accessible to biologists and physicists, though some sections may be challenging for non-theorists. Technical soundness: Moderate. The conceptual arguments are sound, but the toy models are not verifiable from the provided materials, and the normative approach is not fully developed. Readability for nonspecialists: Good. The writing is clear, but the abstract and some sections assume familiarity with non-equilibrium physics.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript makes a valuable conceptual contribution, but the toy models and normative framework need to be more rigorously presented and validated before the case for NEQ regulation is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their toy models demonstrate that NEQ mechanisms can outperform EQ models in achieving specific regulatory phenotypes (e.g., high specificity via proofreading, high sensitivity via higher-order cooperativity).
- **Evidence pointer** Section "Regulatory phenotypes bearing indirect signatures of non-equilibrium regulation", Figure 2, and code repository link
- **Concern** The toy models are described only qualitatively. The manuscript does not provide the model equations, parameter values, or simulation details needed to reproduce the results. Without this information, the claims about NEQ advantages cannot be verified, and the comparison to EQ alternatives is not transparent.
- **Why it matters** The central argument of the manuscript rests on the behavior of these toy models. If the models are not fully specified, the reader cannot assess whether the conclusions are robust or whether they depend on specific parameter choices.
- **Resolution test** Provide a complete description of the models (e.g., in a supplement), including the master equations, parameter ranges, and the code used to generate the figures. Alternatively, include a detailed worked example in the main text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors propose a "normative approach" that prescribes which regulatory phenotypes evolution may have optimized, and claim this can guide model selection and experimental design.
- **Evidence pointer** Section "Normative approach: navigating the space of non-equilibrium regulatory schemes", Figure 3
- **Concern** The normative approach is described in general terms but not formalized. The authors do not specify how to define the optimization problem (e.g., choice of phenotypes, constraints, objective function), how to handle multiple or conflicting phenotypes, or how to validate the resulting model ensemble against experimental data. The example in Figure 3 is mentioned but not explained in sufficient detail.
- **Why it matters** The normative approach is a key contribution of the manuscript. Without a clear methodology, it remains an appealing idea rather than a usable tool, and its practical value is unclear.
- **Resolution test** Provide a step-by-step description of the normative approach, including a worked example with real or realistic data. Specify how to choose phenotypes, set constraints, and evaluate model predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** The authors state that "certain reported features of eukaryotic regulation are hard to reconcile with equilibrium mechanisms" and list several examples (e.g., short TF residence times, sequential assembly of the pre-initiation complex, peaked waiting-time distributions).
- **Evidence pointer** Section "Tantalizing cues for NEQ regulation"
- **Concern** The evidence for NEQ regulation is presented as a list of observations, but the authors do not critically evaluate whether EQ models could also explain these observations, nor do they discuss potential confounding factors or alternative interpretations. The review would be stronger if it included a systematic comparison of EQ and NEQ explanations for each observation.
- **Why it matters** The manuscript aims to persuade readers that NEQ regulation is plausible and important. A one-sided presentation of evidence weakens the argument and may leave readers skeptical.
- **Resolution test** Add a critical discussion of each piece of evidence, including potential EQ explanations and the assumptions required for the NEQ interpretation. Consider including a table summarizing the evidence and its interpretation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "most of the NEQ model space is uninteresting" and that the normative approach can "rule out most of the parameter space as deleterious."
- **Evidence pointer** Section "Normative approach: navigating the space of non-equilibrium regulatory schemes", Figure 3d–e
- **Concern** This claim is asserted but not quantitatively supported. The authors do not provide a measure of "interestingness" or "deleteriousness," nor do they show how the normative approach would rule out parameter regions in a concrete example.
- **Why it matters** This claim is central to the motivation for the normative approach. Without quantitative support, it is unclear whether the approach would indeed narrow the model space in practice.
- **Resolution test** Provide a quantitative example showing the distribution of model performance across parameter space and how the normative approach identifies a small, functionally relevant subset.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract uses the phrase "at equilibrium, or non?" which is informal and may be unclear to some readers.
- **Required correction** Consider rephrasing to "at equilibrium or out of equilibrium?" for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Fundamentals of non-equilibrium regulatory processes"
- **Evidence pointer** Section "Fundamentals of non-equilibrium regulatory processes"
- **Issue** The term "linear framework" is introduced without a brief explanation of what it entails, which may confuse non-specialist readers.
- **Required correction** Add a sentence explaining the linear framework in plain terms, e.g., "a mathematical description of chemical reactions as a network of states with transitions between them."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evidence quality
- **Affected element** Section "Tantalizing cues for NEQ regulation"
- **Evidence pointer** Section "Tantalizing cues for NEQ regulation"
- **Issue** The section lists several observations but does not provide specific citations in the text (though references are listed at the end).
- **Required correction** Add in-text citations for each observation to help readers locate the original studies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section "Simulation code for toy-models"
- **Evidence pointer** Section "Simulation code for toy-models"
- **Issue** The code repository is mentioned, but the manuscript does not state the software version or dependencies (e.g., MATLAB version, toolboxes).
- **Required correction** Add a note specifying the software environment required to run the code.

## Risk / unsupported claims
- The claim that "most of the NEQ model space is uninteresting" is not quantitatively supported.
- The claim that the normative approach can "rule out most of the parameter space as deleterious" is not demonstrated with a concrete example.
- The toy model results (Figure 2) are not verifiable from the provided materials, as the models are not fully described.
- The evidence for NEQ regulation in eukaryotes is presented without a critical evaluation of alternative EQ explanations.
- The normative approach is described conceptually but not formalized, so its practical utility cannot be assessed.