## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided.
- **Assessment boundary** The scientific content, methodological soundness, and claims as presented in the provided text. No external data, figures, or supplementary materials were available for inspection.
- **Shared manuscript claim summary** The authors present a computational framework using sequence-specific thermodynamic models to simulate massively parallel reporter assays (MPRAs) for bacterial promoters. They generate synthetic expression data, compute summary statistics (information footprints and expression shift matrices), and systematically perturb biological and experimental parameters to assess their impact on the interpretability of MPRA data. The goal is to provide a "theory of the experiment" to guide experimental design and improve the inference of regulatory architectures.
- **Visible evidence base** The manuscript text includes equations (Eqs 1–17), references to figures (Figs 1, 3–15), and descriptions of computational methods. No actual data, code outputs, or supplementary figures were provided in the input.
- **Missing materials affecting confidence** All figures, tables, supplementary appendices (S1–S11), and the associated code repository are referenced but not included. This significantly limits the ability to verify the quantitative results, the accuracy of the simulations, and the validity of the conclusions drawn from the presented analyses.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely problem: the need for a quantitative, theory-driven framework to interpret high-throughput reporter assays. The authors leverage their expertise in thermodynamic modeling of gene regulation to build a simulation platform that generates synthetic MPRA data, allowing them to systematically explore how various parameters affect the recovery of regulatory architectures. The conceptual framing is strong, and the potential utility of such a platform for experimental design is clear. However, the manuscript as presented is largely a description of a computational pipeline and its qualitative outputs. The core claims about the utility of the framework, the optimal mutation rate, and the robustness of information footprints are not quantitatively substantiated in the provided text. The lack of access to the figures and supplementary materials makes it impossible to assess the rigor of the simulations, the statistical significance of the findings, or the validity of the conclusions. The manuscript is well-written and the logic is clear, but the scientific case is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in the fields of gene regulation, systems biology, and synthetic biology would be the primary audience. Specifically, experimentalists who use MPRAs (e.g., Sort-Seq, Reg-Seq) to map regulatory elements would find the practical guidance on experimental design (e.g., mutation rate, library size, plasmid copy number) valuable. The theoretical framework and the discussion of non-equilibrium effects would also be of interest to computational biologists and biophysicists working on models of transcriptional regulation. The paper's emphasis on a "theory of the experiment" is a broader conceptual contribution that could influence how high-throughput assays are designed and interpreted across different biological systems.
- **Major strengths**
    1.  The manuscript addresses a significant gap in the field by providing a theoretical framework for a widely used experimental technique.
    2.  The use of sequence-specific thermodynamic models, with energies derived from experimentally determined matrices, is a clear advance over more generic models.
    3.  The systematic exploration of multiple parameters (mutation rate, bias, library size, copy number, inducer concentration) is comprehensive and provides practical insights.
    4.  The inclusion of non-equilibrium models (via the graph-theoretic approach) demonstrates a forward-looking perspective and extends the framework's applicability.
    5.  The writing is clear, well-structured, and accessible to a broad scientific audience.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Evidence
        - **Claim pointer** The authors claim that their simulations "reveal important effects of the parameters on MPRA data" and that they can "optimize MPRA experimental designs."
        - **Evidence pointer** Figures 5–10, Sections 2.1.2–2.2.4, location not provided.
        - **Concern** The central claims of the paper are based on the results of simulations, which are presented only as figures. Without access to these figures, the quantitative nature of the effects (e.g., how much signal-to-noise ratio changes with library size, how the optimal mutation rate is determined) cannot be assessed. The text provides qualitative descriptions but no numerical data, error bars, or statistical analyses. The claim of "optimization" requires a quantitative demonstration that the framework can identify a clear optimum and that this optimum is robust.
        - **Why it matters** The scientific value of this work hinges on the validity and quantitative rigor of the simulation results. If the effects are not clearly demonstrated and quantified, the practical recommendations for experimental design are not well-supported. The reader cannot evaluate the strength of the evidence without seeing the data.
        - **Resolution test** The authors must provide the actual figures and, ideally, the underlying numerical data. The figures should clearly show the trends described, with appropriate measures of variability (e.g., error bars from multiple simulation runs). The claim of an "optimal" mutation rate should be supported by a clear demonstration of a peak in signal-to-noise ratio, with a defined range of acceptable values.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Reproducibility
        - **Claim pointer** The authors state that "All code for generating synthetic datasets, information footprints, and expression shift matrices is written in Python" and is available on GitHub.
        - **Evidence pointer** Section 4, Materials and methods, location not provided.
        - **Concern** While the code is made available, the manuscript does not provide sufficient detail on the simulation parameters, the specific algorithms used, or the validation of the code. For a computational paper, reproducibility is paramount. The reader needs to know the exact values of all parameters (e.g., NNS, P, R, energy matrix values) used to generate the figures. The description of the "graph-theoretic approach" in Section 2.4 is too brief to be reproducible without consulting the supplementary materials.
        - **Why it matters** Without a complete description of the methods, other researchers cannot reproduce the results or apply the framework to their own systems. This undermines the utility of the platform as a community resource. The paper's contribution is not just the conceptual framework but also the practical tool, and the tool must be usable.
        - **Resolution test** The authors should provide a detailed description of the simulation parameters in the main text or a table. The methods section should be expanded to include a step-by-step description of the algorithm, including how the energy matrices are used, how mutations are generated, and how the summary statistics are calculated. The code repository should be well-documented and versioned.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Scientific Importance
        - **Claim pointer** The authors claim that their framework can be used to "explore regulatory evolution" and that it will help "streamline strategies needed to decipher the roles of other types of transcription factors."
        - **Evidence pointer** Section 3, Discussion, location not provided.
        - **Concern** These claims are speculative and not directly supported by the results presented. The paper focuses on the inference of binding sites from simulated data. The link to "regulatory evolution" is not developed, and the extension to elongation/termination factors is mentioned as a future direction. While such forward-looking statements are acceptable in a discussion, they are presented as a key motivation without any preliminary evidence or a clear conceptual pathway.
        - **Why it matters** The significance of the work is partly based on its potential to address broader biological questions. If these connections are not made more concrete, the impact of the paper may be seen as limited to a methodological contribution. The authors should either temper these claims or provide a more detailed argument for how their framework can be applied to these questions.
        - **Resolution test** The authors should either remove or significantly qualify these speculative claims. Alternatively, they could add a short section or paragraph in the discussion that outlines a specific, testable hypothesis for how their framework could be used to study regulatory evolution, perhaps by simulating the effects of mutations on fitness landscapes.
    - **R1-M4**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Technical Soundness
        - **Claim pointer** The authors state that "the lack of signal may not necessarily indicate the absence of a binding site, but it may instead be a result of weak binding or low transcription factor copy number."
        - **Evidence pointer** Section 2.2.1, Figure 7, location not provided.
        - **Concern** This is an important interpretive point, but the analysis appears to be based on a single parameter (FR) being tuned. The interplay between different parameters (e.g., weak binding AND low copy number) is not explored. The conclusion that a lack of signal is ambiguous is likely correct, but the manuscript does not provide a systematic analysis of the parameter space to demonstrate the conditions under which this ambiguity arises.
        - **Why it matters** This point is crucial for the correct interpretation of experimental MPRA data. If the framework is to be used as a guide, it should provide a more nuanced understanding of when signals are expected to be present or absent. A more thorough parameter sweep would strengthen this conclusion.
        - **Resolution test** The authors should perform a more comprehensive analysis, perhaps a two-dimensional parameter sweep (e.g., binding energy vs. copy number), to map out the regions where signals are detectable. This would provide a more robust and useful guide for experimentalists.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity
        - **Affected element** Section 2.1.1, Equation 1
        - **Evidence pointer** Section 2.1.1, location not provided.
        - **Issue** The derivation of Eq 1 is referenced to S2 Appendix, but the main text does not provide a brief physical explanation of the terms. For a non-specialist reader, the meaning of the parameters (e.g., NNS, P, R) and the logic of the equation could be clearer.
        - **Required correction** Add a sentence or two in the main text explaining the physical meaning of each term in Eq 1 and the logic of the simple repression model.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Readability
        - **Affected element** Section 2.2.2, Figure 8
        - **Evidence pointer** Section 2.2.2, location not provided.
        - **Issue** The description of the AND and OR logic results is clear, but the figure is not available. The text would benefit from a more explicit description of what the expected differences in the information footprints are for the two logics.
        - **Required correction** In the text, explicitly state the key qualitative difference between the AND and OR logic footprints (e.g., "In the AND logic case, the footprint shows no signal at either binding site when one repressor is absent, whereas in the OR logic case, a signal is still present at the other binding site").
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Completeness
        - **Affected element** Section 2.4, Non-equilibrium models
        - **Evidence pointer** Section 2.4, location not provided.
        - **Issue** The section on non-equilibrium models is very brief. The graph-theoretic approach is mentioned, but the specific model, the parameters, and the conditions for breaking detailed balance are not described in the main text.
        - **Required correction** Provide a more detailed description of the non-equilibrium model in the main text, or at least a clear summary of the model and the specific perturbation applied (e.g., the "AP → A edge").
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Presentation
        - **Affected element** Section 3, Discussion
        - **Evidence pointer** Section 3, location not provided.
        - **Issue** The discussion of the limitations is brief. The combinatorial explosion issue is mentioned, but the potential impact of this limitation on the scalability of the approach is not fully discussed.
        - **Required correction** Expand the discussion of limitations to include a more detailed assessment of the computational cost and the potential strategies to overcome the combinatorial explosion (e.g., using coarse-grained models or machine learning approaches).
- **Technical failings that need to be addressed before the case is established**
    - The lack of access to the figures and supplementary materials is a critical failing in the context of this review. The core evidence for the claims is not visible.
    - The manuscript does not provide a quantitative validation of the simulation framework against experimental data. While the authors compare to Reg-Seq data qualitatively (as stated in S3 Appendix), a direct quantitative comparison would significantly strengthen the case.
    - The description of the "graph-theoretic approach" is insufficient for reproducibility.
- **Assessment against Nature-style criteria**
    - **Originality:** The concept of a "theory of the experiment" for MPRA is a valuable and original contribution. While thermodynamic models are not new, their systematic application to simulate and dissect the output of a high-throughput assay is a novel and important step.
    - **Scientific importance:** The work has the potential to be highly important for the field of gene regulation. It provides a framework to guide experimental design and interpret complex data, which could accelerate the annotation of regulatory elements in bacterial genomes. The practical recommendations (e.g., on mutation rate and copy number) are directly actionable.
    - **Interdisciplinary readership:** The topic is of interest to a broad audience, including molecular biologists, biophysicists, and computational biologists. The writing is accessible, but the lack of quantitative detail in the main text may limit its appeal to non-specialists who want to understand the robustness of the findings.
    - **Technical soundness:** The theoretical framework is sound, and the use of energy matrices is appropriate. However, the technical soundness of the *results* cannot be fully assessed without the figures and data. The lack of a quantitative comparison to experimental data is a concern.
    - **Readability for nonspecialists:** The manuscript is well-written and logically structured. The introduction and discussion are clear. However, the methods and results sections are dense and rely heavily on the figures, which are not available. A non-specialist would struggle to follow the quantitative arguments.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is valuable and the potential impact is high. However, the current manuscript does not fully establish its case from the provided evidence. The authors must provide the missing figures and data, and they should strengthen the quantitative validation of their approach. Once these issues are addressed, the paper would be a strong candidate for publication.

## Risk / unsupported claims
- The claim that the framework can be used to "optimize MPRA experimental designs" is not quantitatively supported in the provided text.
- The claim that the framework can be used to "explore regulatory evolution" is speculative and not developed.
- The claim that the framework will help "streamline strategies needed to decipher the roles of other types of transcription factors" is a future direction, not a current result.
- The specific numerical results (e.g., optimal mutation rate of 0.10) are presented without error bars or sensitivity analysis, making their robustness unclear.
- The comparison to experimental Reg-Seq data is mentioned but not shown, making the claim of similarity unverifiable.