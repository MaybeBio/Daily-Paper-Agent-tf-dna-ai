## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, funding, author contributions, competing interests, data availability, acknowledgements)
- **Assessment boundary** Scientific content and technical claims as presented in the provided text; no supplementary figures or methods were available for inspection
- **Shared manuscript claim summary** The authors present NeMECiS, a high-throughput combinatorial screening approach, to dissect the design principles of signal-dependent cis-regulatory elements (CREs) in a mammalian stem cell differentiation model. They report that individual 200 bp CRE fragments show minimal activity, but combinatorial assembly yields thousands of functional synthetic CREs (synCREs) with activities exceeding natural sequences. Statistical modelling decomposes CRE function into modular contributions following a multiplicative rule modulated by pairwise interactions and spacing-dependent syntax. The authors apply these rules to re-engineer an Olig2 CRE, demonstrating predictable changes in motor neuron progenitor patterning in neural tissue.
- **Visible evidence base** Main text figures referenced (Fig. 1A-I, 2A-K, 3A-K, 4A-O); supplementary figures referenced (Fig. S1-S12); no figure panels, numerical data, or methodological details were provided in the submitted material
- **Missing materials affecting confidence** All figures and figure legends; Materials and Methods section; supplementary information; statistical model specifications; sequencing data; code repository contents; experimental protocols

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: whether quantitative, predictive rules govern the assembly of signal-dependent cis-regulatory elements. The authors introduce an innovative experimental platform, NeMECiS, that enables exhaustive combinatorial exploration of CRE design space, and they present a compelling conceptual framework decomposing CRE activity into modular, interactional, and syntactical components. The finding that weak individual fragments combine multiplicatively to generate strong signal-responsive activity is conceptually important and potentially transformative for synthetic biology. However, the provided text lacks the methodological detail and quantitative evidence necessary to evaluate the robustness of the claims. The statistical modelling framework, the validation of model assumptions, the reproducibility metrics, and the experimental controls are not described in sufficient detail. The central claims of predictive power and rule-based engineering rest on analyses that cannot be assessed from the current submission. The manuscript is intellectually ambitious and likely to be of broad interest, but the evidence base as presented is insufficient to establish the case.

- **Who would be interested in the results, and why** This work will appeal to several distinct communities. First, developmental biologists studying morphogen gradient interpretation and cell fate specification will find the re-engineering of Olig2 expression and the resulting changes in motor neuron progenitor patterning of direct relevance. Second, synthetic biologists and genetic engineers interested in designing programmable gene expression systems will value the proposed modular composability rules as a design framework. Third, computational biologists working on regulatory genomics and deep learning models of CRE function will be interested in the comparison between interpretable linear models and neural network approaches. Fourth, evolutionary biologists studying CRE structure and constraint may find the observation that natural CRE orderings are suboptimal for maximal activity provocative. The interdisciplinary reach is substantial, spanning molecular biology, quantitative biology, and engineering.

- **Major strengths**
  1. The experimental design is conceptually innovative. The NeMECiS platform addresses a critical gap in the field by enabling systematic, exhaustive exploration of CRE combinatorics at lengths beyond typical MPRA fragments.
  2. The finding that individual fragments show minimal activity but combine to generate thousands of functional synCREs is striking and challenges simplistic models of CRE architecture.
  3. The decomposition of CRE activity into modular, interactional, and syntactical components provides a clear and interpretable framework that bridges mechanistic understanding and predictive modelling.
  4. The demonstration that re-ordering fragments of an endogenous CRE can predictably tune signal-dependent activity, validated in a functional tissue context, is a powerful proof of concept.
  5. The comparison between interpretable statistical models and deep learning approaches addresses an important methodological question in the field.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "CRE function can be decomposed into specific quantitative contributions in which sequence fragments combine through a multiplicative rule, tuned by their relative positioning and spacing."
- **Evidence pointer** Results section, Fig. 2A-K, Fig. 3A-K; location not provided
- **Concern** The multiplicative model is central to the paper's conceptual contribution, but the statistical evidence supporting this claim cannot be evaluated. The text states that a "linear modelling framework" was established and that multiplicative models "captured the behaviour better" than additive models, but no details are provided on model specification, parameter estimation, model comparison criteria, uncertainty quantification, or goodness-of-fit metrics. The comparison between additive and multiplicative models is mentioned but the statistical tests used are not described. Furthermore, the claim that the model "decomposes" CRE function into modular contributions requires demonstration that the decomposition is identifiable and that alternative decompositions are rejected by the data.
- **Why it matters** The multiplicative rule is the foundational claim from which the predictive framework and engineering applications follow. If the statistical evidence is weak or the model comparison is not rigorous, the entire conceptual edifice is compromised. The distinction between additive and multiplicative models has profound implications for how CREs are understood mechanistically and how they should be engineered.
- **Resolution test** Provide complete model specification, including the mathematical form of the linear model, the prior distributions used in Bayesian inference, the likelihood function, and the posterior predictive checks. Report quantitative model comparison metrics (e.g., information criteria, cross-validated predictive accuracy) for additive versus multiplicative models across the full dataset. Demonstrate that the multiplicative model captures the data substantially better than alternatives, with uncertainty estimates that do not overlap. Show residual analyses and validation on held-out data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the learned rules extrapolate beyond the training design-space, enabling the re-design of CREs controlling stem cell diversification" and that engineered CREs "successfully directed alternative spatial patterning outcomes in neural tissue."
- **Evidence pointer** Results section, Fig. 4A-O; location not provided
- **Concern** The predictive power of the model is claimed to extend beyond the training set, but the evidence for extrapolation is not presented. The text describes selecting candidate FL-synCREs from the top and bottom 10% of the design space, but the criteria for selection, the number of candidates tested, the replication strategy, and the statistical significance of the observed differences are not reported. The validation in neural tissue relies on qualitative descriptions of "expanded" or "diminished" domains without quantitative morphometric analysis or statistical testing. The calibration of the ODE model is mentioned but the fitting procedure, parameter uncertainty, and model validation are not described.
- **Why it matters** The claim of predictive extrapolation is what distinguishes this work from a descriptive analysis. If the model cannot reliably predict the activity of unseen sequences, the engineering applications and the broader implications for synthetic biology are not supported. The tissue-level validation is the ultimate test of the framework's utility, and without quantitative evidence, the claim of "programmable control" is not established.
- **Resolution test** Report the number of predicted and tested FL-synCREs, the correlation between predicted and measured activities for held-out sequences, and the confidence intervals for predictions. Provide quantitative analysis of tissue patterning (e.g., domain widths, cell counts, positional boundaries) with appropriate statistical tests comparing engineered versus wild-type conditions. Describe the ODE model calibration procedure, including parameter identifiability analysis and posterior predictive checks against independent data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that NeMECiS is "a novel, high-throughput combinatorial screening strategy" and that the library comprised "25^3 = 15,625 synCREs, the exhaustive permutation-set of twenty-five 200bp fragments."
- **Evidence pointer** Results section, Fig. 1D, Fig. S1-S2; location not provided
- **Concern** The experimental methodology is described only at a high level. Critical details are missing: the cloning strategy for generating the combinatorial library, the error rate and fidelity of the assembly, the representation and coverage of the library in the sequencing, the number of biological replicates, the sequencing depth, the thresholds for filtering low-quality barcodes, and the normalization procedures for comparing across conditions. The lentiviral integration strategy raises concerns about copy number variation and position effects that are not addressed. The gating strategy for flow cytometry and the conversion from fluorescence intensity to activity scores are not described.
- **Why it matters** The entire dataset rests on the quality and reproducibility of the NeMECiS platform. Without detailed methods, the reliability of the measurements cannot be assessed, and the conclusions drawn from the data are not verifiable. The claim of exhaustiveness (15,625 synCREs) requires demonstration that the library was complete and that all members were adequately sampled.
- **Resolution test** Provide complete Materials and Methods for library construction, including oligonucleotide design, assembly conditions, and quality control metrics. Report library coverage statistics, sequencing depth per barcode, and the distribution of barcode counts. Describe the normalization and data processing pipeline in detail. Include information on the number of independent differentiations, the variability across replicates, and the criteria for including or excluding data points.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that "the field's historical focus on shorter fragments may have systematically underappreciated the modular composability rules of CREs" and that the findings "contrast with the rigid conformation-dependent model proposed by enhanceosome models."
- **Evidence pointer** Discussion section; location not provided
- **Concern** The broader implications of the findings are stated without sufficient contextualization. The claim that the field has "systematically underappreciated" composability rules requires a more thorough comparison with existing literature on MPRA studies, synthetic enhancer design, and models of enhancer architecture. The contrast with the enhanceosome model is presented as a dichotomy, but the relationship between the proposed modular framework and existing models of enhancer function (e.g., billboard, flexible billboard, enhanceosome) is not clearly delineated. The evolutionary implications are mentioned but not developed.
- **Why it matters** The significance of the work depends on how it advances understanding beyond existing models. Without a clear articulation of what is new and how it relates to prior work, the contribution may appear incremental or overstated. The claim of "systematic underappreciation" is strong and requires evidence that prior approaches were indeed limited in the way suggested.
- **Resolution test** Expand the discussion to include a systematic comparison with prior MPRA and synthetic enhancer studies, highlighting specific examples where the modular composability rules would make different predictions. Clarify the relationship between the proposed framework and existing models of enhancer architecture, including where the framework is consistent with and where it extends beyond current understanding. Provide a more nuanced discussion of the evolutionary implications, considering trade-offs between maximal activity and other constraints.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the interaction and syntax terms" in the synergistic model are "significant and reproducible" and that the model "matched those of the deep-learning models" in predictive performance.
- **Evidence pointer** Results section, Fig. 3A-K, Fig. S7-S8; location not provided
- **Concern** The comparison between the interpretable synergistic model and deep learning approaches is mentioned but not quantified. The text states that deep learning models "generally perform better" than the linear model (PCCs 0.61-0.66 versus 0.56), but the significance of this difference is not tested, and the comparison is not placed in the context of model complexity. The synergistic model is claimed to match deep learning performance, but the specific metrics and the conditions under which this match holds are not reported. The identification of interaction and syntax effects relies on statistical thresholds that are not described.
- **Why it matters** The claim that an interpretable model can match the performance of deep learning approaches is important for the field, as it suggests that fundamental rules can be extracted from complex data. However, if the comparison is not rigorous, the claim is not credible. The balance between model interpretability and predictive power is a key contribution, but it must be demonstrated with appropriate metrics.
- **Resolution test** Report the full comparison between the synergistic model and deep learning approaches, including cross-validated performance metrics, confidence intervals, and statistical tests for differences. Describe the criteria for identifying significant interaction and syntax effects, including multiple testing corrections. Provide a complexity-adjusted comparison (e.g., using information criteria or cross-validated likelihood) to demonstrate that the interpretable model achieves comparable performance without overfitting.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses specialized terminology (e.g., "NeMECiS", "synCREs") without defining these terms for a general scientific audience. The phrase "hierarchical design rules" is introduced without explanation of what "hierarchical" means in this context.
- **Required correction** Define NeMECiS and synCREs at first use. Briefly explain what is meant by "hierarchical" in the context of CRE design rules, or rephrase to be more accessible.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data and materials availability; location not provided
- **Issue** The data availability statement mentions a GitHub repository and a GEO accession, but the specific contents of these resources are not described. It is unclear whether the code is documented, whether the data are raw or processed, and whether analysis scripts are included.
- **Required correction** Provide a more detailed description of the contents of the GitHub repository and the GEO submission, including the types of files, the format of the data, and any documentation or README files.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, Fig. 1C
- **Evidence pointer** Results section, Fig. 1C; location not provided
- **Issue** The text states that "none of the fragments alone showed substantial SAG-dependent fold-changes in activity," but the threshold for "substantial" is not defined. It is unclear whether this is a statistical threshold, an effect size threshold, or a visual assessment.
- **Required correction** Define the criteria for "substantial" activity, including the statistical test used and the effect size threshold, or rephrase to describe the observed distribution of activities more precisely.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, Fig. 3F-H
- **Evidence pointer** Results section, Fig. 3F-H; location not provided
- **Issue** The description of the orthonormal basis decomposition and the projection into 2D space is difficult to follow without a more detailed explanation of the method. The connection between the mathematical decomposition and the biological interpretation is not immediately clear.
- **Required correction** Provide a more accessible explanation of the orthonormal basis decomposition, including a brief description of the mathematical approach and how the resulting components relate to biological phenomena such as distance-dependent and order-dependent effects.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Results section, Fig. 4J-K
- **Evidence pointer** Results section, Fig. 4J-K; location not provided
- **Issue** The text describes "intracellular staining" for flow cytometry but does not specify the antibody, the fixation/permeabilization protocol, or the gating strategy. This limits the reproducibility of the experiments.
- **Required correction** Provide details on the antibody used, the staining protocol, and the gating strategy in the Materials and Methods section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The discussion is somewhat repetitive, restating findings that were already presented in the results section without adding substantial new interpretation. The paragraph on neural network models could be more focused.
- **Required correction** Streamline the discussion to avoid repetition and focus on the most important implications and open questions.

## Risk / unsupported claims
- The claim that "CRE function can be decomposed into specific quantitative contributions" following a multiplicative rule is unsupported without the statistical model details and validation metrics.
- The claim that "the learned rules extrapolate beyond the training design-space" is unsupported without evidence of predictive performance on held-out sequences.
- The claim that engineered CREs "successfully directed alternative spatial patterning outcomes" is unsupported without quantitative analysis of tissue patterning.
- The claim that the synergistic model "matched those of the deep-learning models" in predictive performance is unsupported without a rigorous comparison.
- The claim that "the field's historical focus on shorter fragments may have systematically underappreciated the modular composability rules" is an overstatement without a comprehensive literature comparison.
- The claim that the findings "contrast with the rigid conformation-dependent model proposed by enhanceosome models" is not fully supported, as the relationship between the proposed framework and existing models is not clearly delineated.
- The claim that NeMECiS bridges "the gap between high-throughput reporter assays and more extensive genomic engineering approaches" is not evaluated with respect to existing technologies.
- The claim that the approach "will enable the construction of tailored synthetic regulatory sequences" is speculative and not directly supported by the presented data.
- The claim that the findings "provide a basis for understanding developmental gene regulation" is plausible but not directly demonstrated in the presented text.
- The claim that the model provides "clear mechanistic insights" is not supported without a detailed description of the model interpretation.