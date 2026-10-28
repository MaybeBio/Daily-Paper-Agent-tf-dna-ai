## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods) without figures or supplementary materials
- **Assessment boundary** Technical soundness and scientific validity of the GAME framework as described; claims about benchmarking results and framework capabilities are assessed only to the extent supported by the provided text
- **Shared manuscript claim summary** The authors present GAME, a containerized, API-based framework for standardized, community-led benchmarking of sequence-to-activity genomics models. The framework separates models (Predictors) from benchmarks (Evaluators), uses an LLM-based Matcher for task alignment, and is demonstrated on gene expression, chromatin conformation, and consistency tasks across several models including Borzoi, Enformer, DREAM-RNN, Orca, and DeepBICCN2.
- **Visible evidence base** Abstract, main text, methods sections on information passing, communication protocol, module responsibilities, containerization, maintenance, and Matcher implementation. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures (Fig. 1, 2, 3) and their captions; quantitative benchmarking results; API specification details; code repository contents; validation metrics; details on down-sampling procedures; Matcher accuracy assessments

## Reviewer

- **Overall assessment** The manuscript describes a timely and potentially valuable community infrastructure for standardized benchmarking of genomics models. The API-based design and containerization are sensible and address real problems of reproducibility and comparability. However, the provided text lacks quantitative evidence of framework performance, validation of the Matcher module, or demonstration that the framework produces meaningful benchmarking results. The claims about the framework's utility and the specific benchmarking outcomes in Fig. 2 cannot be assessed from the supplied material. The manuscript is more of an infrastructure description than a scientific result, and the case for its adoption would be strengthened by concrete validation data.

- **Who would be interested in the results, and why** Computational genomics researchers developing or using sequence-to-activity models (e.g., Enformer, Borzoi, similar architectures) would be the primary audience. The framework addresses a genuine need for standardized comparison across models and benchmarks. Researchers in regulatory genomics, variant effect prediction, and those applying such models to disease genetics would also benefit from a community benchmarking standard. The infrastructure nature of the work may also interest bioinformatics tool developers and those working on reproducible ML pipelines.

- **Major strengths**
  1. The problem is well-motivated: heterogeneous benchmarking practices in genomics ML are a recognized issue, and the authors articulate the specific challenges clearly (assay-specific biases, task mismatch, implementation degrees of freedom).
  2. The API-based design is conceptually clean and borrows proven software engineering patterns. The separation of Predictors and Evaluators with a standardized protocol is a sensible architecture.
  3. The design principles are thoughtful, particularly the focus on biological phenomena rather than assays, and the restriction of information provided to models to prevent benchmark overfitting.
  4. The Matcher module addresses a real practical problem (task alignment) that would otherwise require manual curation.
  5. Containerization with Apptainer is appropriate for HPC environments and addresses reproducibility concerns.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that GAME was applied to several models and two benchmarking tasks (gene expression and chromatin conformation) with results shown in Fig. 2, and that consistency Evaluators confirm correlated predictions between forward and reverse complement sequences (Fig. 3b).
- **Evidence pointer** Fig. 2, Fig. 3b (figures not provided)
- **Concern** The central demonstration of the framework is entirely contained in figures that were not provided for review. Without the actual benchmarking results, correlation values, or comparative performance metrics, the claim that GAME works as intended cannot be evaluated. The text mentions down-sampling of certain Evaluator datasets for computational efficiency, but no details are given on the extent of down-sampling or its potential impact on the reported results.
- **Why it matters** The manuscript's scientific contribution rests on demonstrating that the framework produces meaningful, interpretable benchmarking results. Without access to these results, the reader cannot assess whether GAME achieves its stated purpose or whether the specific implementations are correct.
- **Resolution test** Provide the figures and their captions, along with the underlying data and analysis scripts. The benchmarking results should include quantitative metrics (e.g., correlation coefficients, AUROC, etc.) with appropriate uncertainty estimates, and the down-sampling procedures should be described in sufficient detail to assess their impact.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The Matcher module, powered by a local LLM (Gemma 3), is claimed to automate ambiguous task alignment between benchmarks and models, using lexical, syntactic, and semantic matching with a tournament-style chunking strategy.
- **Evidence pointer** Methods section "Automated and externalized cell type, molecule, and species matching"
- **Concern** No validation of the Matcher's accuracy or reliability is provided. The manuscript does not report how often the Matcher produces correct alignments, how it handles ambiguous or novel terms, or how its performance compares to manual curation. The tournament-style chunking strategy is described but not evaluated for accuracy or failure modes. The choice of Gemma 3 and the specific prompting strategy are not justified with comparative data.
- **Why it matters** The Matcher is a critical component that determines whether benchmarks are applied to appropriate model outputs. If the Matcher makes systematic errors, the resulting benchmarking results could be misleading. The authors themselves note that determining the best way to match tasks was "a substantial challenge," yet no evidence is presented that the challenge has been adequately addressed.
- **Resolution test** Provide a validation study of the Matcher, including accuracy on a held-out set of task-alignment problems, comparison to manual expert curation, and analysis of failure cases. Report the impact of Matcher errors on downstream benchmarking results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and completeness
- **Claim pointer** The manuscript states that "the existing models and benchmarks in GAME will mean that implementing the GAME API will become the most efficient way to complete evaluations" and that the framework is designed to be sustainable with minimal centralized maintenance.
- **Evidence pointer** Main text, sections on "Maintenance and Community Contributions" and "Data and Code availability"
- **Concern** The manuscript claims that five models and six benchmarks are already implemented, but the provided text does not describe the full list of these implementations, their provenance, or their validation status. The claim that the framework will become self-sustaining through community contributions is speculative and not supported by evidence of community adoption or contribution mechanisms beyond a GitHub repository.
- **Why it matters** The value of an infrastructure resource depends on its completeness and the quality of its initial content. If the existing implementations are incomplete, poorly documented, or contain errors, early adopters may be discouraged. The sustainability claim is important for users deciding whether to invest in learning and adopting the framework.
- **Resolution test** Provide a complete inventory of implemented Predictors and Evaluators, including their source, training data, and any validation performed. Describe the contribution and review process for new modules. Provide evidence of community interest or adoption, such as external contributions or usage statistics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scope and generalizability
- **Claim pointer** The manuscript claims that GAME is designed for "large-scale, community-led standardized model benchmarking on user-defined evaluation tasks" and that the framework will "accelerate genomics research by illuminating the best models for a given task."
- **Evidence pointer** Abstract and main text
- **Concern** The demonstrated applications are limited to gene expression (MPRA-based) and chromatin conformation (Orca-based), plus a consistency check for accessibility models. The framework's generalizability to other important genomics tasks (e.g., splicing, methylation, 3D genome organization beyond the single Orca example) is asserted but not demonstrated. The text does not discuss potential limitations of the API design for certain types of models or tasks.
- **Why it matters** The claimed broad utility of the framework is a key part of its appeal. If the API design has inherent limitations for certain model types or tasks, these should be disclosed so that potential users can make informed decisions.
- **Resolution test** Provide additional examples of diverse task types implemented in GAME, or explicitly discuss known limitations and planned extensions. If the framework is intended to be general, demonstrate this with at least one example from a substantially different task category.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, sentence on "technology-independent" tasks
- **Issue** The phrase "technology-independent" is ambiguous. It could mean independent of the assay technology used to generate data, or independent of the computing technology used to run models. The intended meaning becomes clearer in the main text but the abstract could be misinterpreted.
- **Required correction** Clarify the meaning, e.g., "independent of the specific assay technology used to measure the biological phenomenon."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Communication protocol" section
- **Evidence pointer** Methods section on communication protocol
- **Issue** The description of the JSON schema and the specific data structures used for requests and responses is at a high level. The manuscript states that "sample files and code can be found on GitHub" but does not describe the schema in the text.
- **Required correction** Provide a brief description of the core data structures (e.g., the fields in a request and response) in the methods, or include a supplementary table summarizing the schema.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Containerization" section
- **Evidence pointer** Methods section on containerization
- **Issue** The manuscript states that Apptainer is used but does not specify the version or provide a definition file or recipe for the containers. This limits reproducibility of the exact containerized environment.
- **Required correction** Provide container definition files or a link to them in the code repository, and specify the Apptainer version used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Main text, discussion of Fig. 2 results
- **Evidence pointer** Main text, paragraph describing Fig. 2
- **Issue** The text mentions that "we down-sampled certain Evaluator datasets" for computational efficiency but does not specify which datasets, the extent of down-sampling, or how this might affect the comparability of results across models.
- **Required correction** Specify the down-sampling procedure in the methods and discuss any potential impact on the reported benchmarking results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Main text, description of Matcher
- **Evidence pointer** Main text, paragraph on Matcher advantages
- **Issue** The description of the Matcher's matching strategies (lexical, syntactic, semantic) is clear at a high level, but the manuscript does not explain how the LLM is prompted or how the tournament-style elimination is implemented in practice.
- **Required correction** Provide a brief example of a typical Matcher query and response, or include pseudocode for the tournament algorithm.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Author contributions
- **Evidence pointer** Author contributions section
- **Issue** The contributions list several individuals who provided feedback but does not specify the contributions of all authors. For example, the contributions of D.D. and W.H. are mentioned in the acknowledgements for Matcher help but not in the author contributions.
- **Required correction** Ensure the author contributions section accurately reflects the contributions of all authors, including those who contributed to the Matcher implementation.

## Risk / unsupported claims
- The claim that GAME enables "large-scale, community-led standardized model benchmarking" is not supported by evidence of scale or community adoption beyond the authors' own implementations.
- The claim that the Matcher "ensures that performance measures are not influenced by the Predictor builder's understanding of cellular, molecular, or species relationships" is not validated; the Matcher's accuracy and potential biases are not assessed.
- The claim that "the existing models and benchmarks in GAME will mean that implementing the GAME API will become the most efficient way to complete evaluations" is speculative and not supported by comparative efficiency data.
- The specific benchmarking results shown in Fig. 2 (e.g., model rankings, performance differences) are not assessable from the provided text.
- The claim that GAME will "reveal model limitations and low-quality benchmarks" is a forward-looking statement without demonstrated examples.
- The statement that "having all models share a common language means that other software can use GAME to facilitate model reuse and swapping" is plausible but not demonstrated with examples.
- The claim that the framework is "sustainable in the long term" with "minimal centralized maintenance" is not supported by evidence of the maintenance burden or community contribution activity.

## Assessment against Nature-style criteria
- **Originality** The concept of an API-based, community-driven benchmarking framework for genomics models is a novel contribution. While prior work has addressed benchmarking (e.g., Kipoi, ENCODE-DREAM challenges), the specific design of separating Predictors and Evaluators with a standardized protocol and an LLM-based Matcher is original. However, the originality is primarily in the infrastructure design rather than in new biological or methodological insights.
- **Scientific importance** The problem of standardized benchmarking is important for the field, and a well-designed framework could have significant impact on how genomics models are compared and adopted. The potential importance is high, but the demonstrated impact is currently limited to the authors' own implementations.
- **Interdisciplinary readership** The work is primarily of interest to computational genomics researchers. The API design concepts may appeal to a broader computational audience, but the specific applications are niche. The manuscript is unlikely to attract substantial readership outside genomics and ML applied to genomics.
- **Technical soundness** The technical design is sound in principle, but the lack of validation data for the Matcher and the absence of quantitative benchmarking results prevent a full assessment of technical correctness. The description of the communication protocol and containerization is clear, but the implementation details are not fully specified.
- **Readability for nonspecialists** The manuscript is reasonably well-written and explains the motivation clearly. However, the methods sections assume familiarity with genomics assays, ML models, and software engineering concepts. A nonspecialist would struggle with terms like "sequence-to-activity models," "MPRA," and "Apptainer" without additional context.

## Recommendation posture
Currently not established from the provided evidence. The framework concept is promising and the design principles are thoughtful, but the manuscript lacks the quantitative validation and demonstration of the framework's utility that would be necessary to support its claims. The authors should provide the missing figures and data, validate the Matcher's performance, and demonstrate that the framework produces meaningful benchmarking results before the case for its adoption is established. If the missing evidence is provided and the technical concerns are addressed, the work could be a valuable contribution to the field.