## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full manuscript, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present pyDNA-EPBD, a parallel software implementation of the Extended Peyrard-Bishop-Dauxois (EPBD) nonlinear DNA model. The software is claimed to generate genomic scale profiles of average base-pair openings, base flipping probability, DNA bubble probability, and a characteristic dynamic length indicating the number of base pairs statistically significantly affected by a single point mutation, using the Markov Chain Monte Carlo algorithm.
- **Visible evidence base** Abstract text only; no performance benchmarks, validation data, algorithmic details, or usage examples are provided
- **Missing materials affecting confidence** Full manuscript, figures, tables, code repository contents, documentation, benchmark results, and any comparative validation against experimental or other computational data

## Reviewer
- **Overall assessment** The abstract describes a potentially useful software tool for simulating DNA breathing dynamics using a well-established nonlinear model. The motivation is clear and biologically relevant. However, the abstract provides insufficient technical detail to assess the novelty, correctness, or performance of the implementation. Key claims about genomic scale profiling and the characteristic dynamic length are not substantiated with any quantitative evidence or validation. The software availability statement is helpful, but the scientific case for the tool's utility and reliability is not established from the supplied material.
- **Who would be interested in the results, and why** Computational biophysicists and bioinformaticians studying DNA dynamics, transcription regulation, and DNA-protein interactions would be interested. Researchers using Peyrard-Bishop-type models or seeking efficient tools for predicting DNA bubble propensity and mutation effects at genomic scale would find the software potentially valuable. The tool could also appeal to those integrating DNA structural dynamics into larger genomic analyses.
- **Major strengths** The software addresses a relevant biological problem with a well-known physical model. The parallel implementation and genomic scale capability are potentially significant practical improvements. The availability of open source code and documentation is commendable and supports reproducibility.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The abstract does not clearly establish novelty beyond a new implementation of an existing model. Scientific importance: The biological motivation is important, but the abstract does not demonstrate that the tool provides new biological insights or substantially improves on existing methods. Interdisciplinary readership: The topic bridges physics, biology, and computation, but the abstract is too brief to engage a broad audience. Technical soundness: Cannot be assessed from the abstract alone; no validation or performance data are provided. Readability for nonspecialists: The abstract is generally clear but uses technical terms without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide enough information to support the claims. A full manuscript with validation, benchmarks, and algorithmic details would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The software generates genomic scale profiles of average base-pair openings, base flipping probability, and DNA bubble probability.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract claims genomic scale profiling but provides no information on the algorithm's computational complexity, memory usage, runtime, or scalability. No benchmarks or comparisons to existing implementations are shown.
- **Why it matters** Without performance data, it is impossible to verify that the software can actually handle genomic scale inputs in a practical manner. The claim of genomic scale capability is central to the tool's value proposition.
- **Resolution test** Provide runtime and memory benchmarks on standard genomic sequences, compare with existing tools, and describe the parallelization strategy and its efficiency.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and accuracy
- **Claim pointer** The software describes features of DNA dynamics in detail, including base flipping probability and the characteristic dynamic length affected by a single point mutation.
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** No validation of the model outputs against experimental data, known biological results, or other computational methods is presented. The characteristic dynamic length is a novel concept but is not defined or demonstrated with any example.
- **Why it matters** Without validation, the biological relevance and accuracy of the predictions are unknown. The characteristic dynamic length could be a useful metric, but its meaning and utility are not established.
- **Resolution test** Include validation studies comparing predicted bubble profiles and mutation effects with experimental data or established computational results. Provide a clear definition and illustrative example of the characteristic dynamic length.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and usability
- **Claim pointer** The software is freely available and supported across most operating systems.
- **Evidence pointer** Abstract, Availability and implementation section; location not provided
- **Concern** The abstract does not describe the input formats, output formats, user interface, or required dependencies. No example usage or tutorial is mentioned.
- **Why it matters** For a software tool, usability and clear documentation are essential for adoption. The abstract claims extensive documentation, but this is not verifiable from the supplied material.
- **Resolution test** Provide a brief description of the software architecture, input and output formats, and a minimal working example in the manuscript. Confirm that the documentation includes installation instructions and usage guides.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Motivation section
- **Evidence pointer** Location not provided
- **Issue** The phrase "characteristically dynamic length" is introduced without definition or context.
- **Required correction** Define this term explicitly in the abstract or provide a reference to a detailed explanation in the full manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, Results section
- **Evidence pointer** Location not provided
- **Issue** The abstract does not mention any limitations of the model or the software, such as parameter sensitivity or assumptions.
- **Required correction** Add a sentence acknowledging known limitations or parameter dependencies of the EPBD model and the implementation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Abstract, Availability and implementation section
- **Evidence pointer** Location not provided
- **Issue** The abstract does not specify the license under which the software is distributed.
- **Required correction** State the software license explicitly in the abstract or the availability section.

## Risk / unsupported claims
- The claim of genomic scale profiling is unsupported without performance benchmarks.
- The biological accuracy of the predicted profiles is unverified without validation data.
- The characteristic dynamic length is not defined or demonstrated, making its significance unassessable.
- The claim of broad operating system support is not verifiable from the abstract alone.
- The utility of the software for biological discovery is not established from the provided evidence.