## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and evidence quality within the provided text. No external literature or code verification performed.
- **Shared manuscript claim summary** The authors propose a hybrid Markovian-promoter/ODE framework as a mechanistic alternative to Hill-function-based models for gene regulatory networks. They claim it is stochastic, CME-compatible, mechanistically grounded, scalable, and parameterizable from accessible data, validated on seven systems with 10-100x speedup over SSA.
- **Visible evidence base** Descriptions of methods, simulation results summaries, tables referenced (Tables 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16), figures referenced (Figures 1-10), and qualitative comparisons to experimental data.
- **Missing materials affecting confidence** Actual figures and tables are not provided. Numerical data, parameter values, and detailed simulation results are not visible. Code repository is referenced but not reviewed. Experimental data comparisons are described but not shown quantitatively.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing framework that addresses a real gap in stochastic gene regulation modeling. The core idea of coarse-graining promoter binding into discrete Markovian states while retaining mass-action kinetics is sound and potentially useful. However, the evidence as presented is largely qualitative and descriptive. The absence of actual figures, tables, and quantitative results prevents verification of the central claims regarding accuracy, speedup, and biological fidelity. The manuscript reads more like a proposal or extended abstract than a fully validated methods paper. The claims of generalizability and superiority over alternatives are not adequately supported by the visible evidence.
- **Who would be interested in the results, and why** Researchers in systems biology, computational biology, and biophysics, particularly those working on whole-cell modeling, stochastic gene expression, and synthetic biology. The framework offers a potential solution to integrating stochastic promoter dynamics into large-scale models without prohibitive computational cost. Those interested in mechanistic alternatives to phenomenological Hill functions would also find the conceptual framework relevant.
- **Major strengths**
  - The conceptual framework is well-motivated and addresses a genuine limitation of Hill-function models.
  - The emphasis on maintaining mass-action kinetics and CME compatibility is technically important and correct.
  - The selection of seven diverse test systems is appropriate for demonstrating generalizability.
  - The discussion of parameterization from accessible data is practical and addresses a real bottleneck.
  - The writing is clear and the logical structure is coherent.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes): The central quantitative claims are not verifiable from the provided text. The manuscript references numerous figures and tables, but none are included in the provided material. Claims of "excellent agreement," "CV ratios of 0.95-0.96," "20-fold speedup," and "correlation > 0.98" cannot be assessed without the actual data. This is a fundamental issue that prevents evaluation of the manuscript's core contribution.
  - **R1-M2** (Blocking: Yes): The validation methodology is described but not demonstrated. The manuscript states that comparisons were made against SSA and ODE models, but no details on simulation protocols, parameter estimation, or statistical analysis are provided. The claim that the Markovian model "achieves similar accuracy to full stochastic simulations" requires quantitative evidence that is not visible.
  - **R1-M3** (Blocking: No): The treatment of the timescale separation assumption is insufficient. The manuscript acknowledges this assumption but does not provide a rigorous analysis of when it holds or fails. The choice of communication time step is discussed empirically, but no theoretical guidance is given for new systems. This limits the practical utility of the framework.
  - **R1-M4** (Blocking: No): The comparison with existing hybrid methods in Section 4.3 is superficial. The manuscript lists alternative approaches but does not provide a quantitative or even qualitative comparison of their relative merits and limitations in the context of the seven test systems. This weakens the claim of novelty and advantage.
- **Minor Comments**
  - **R1-m1** (Axis: Clarity): The distinction between the "Full Markovian" model and the "CME+Markovian" model is unclear. The text mentions both but does not clearly define their differences in implementation or purpose.
  - **R1-m2** (Axis: Reproducibility): The manuscript states that code is available, but no version, license, or usage instructions are provided. The reproducibility of the results would be enhanced by more detailed documentation.
  - **R1-m3** (Axis: Presentation): The use of "10-100x" and "20-fold" speedup claims is inconsistent. The abstract states 10-100x, while the GAL system section states 20x. Clarification of the range and conditions for these speedups is needed.
  - **R1-m4** (Axis: Completeness): The experimental comparisons (e.g., Ramsey et al., Lahav et al.) are described qualitatively. Quantitative comparisons with error bars or confidence intervals would strengthen the validation.
  - **R1-m5** (Axis: Technical detail): The method for handling multi-input promoters in Section 2.2 is described only briefly. The logic function L(k) is mentioned but not formally defined or exemplified.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Missing figures and tables with quantitative results.
  - R1-M2: Lack of detailed simulation and validation protocols.
  - R1-M3: Insufficient analysis of the timescale separation assumption.
  - R1-M4: Superficial comparison with alternative hybrid methods.
- **Assessment against Nature-style criteria**
  - **Originality**: The concept of using Markovian promoter states as a mechanistic alternative to Hill functions is not entirely new, but the specific hybrid framework and its systematic validation across multiple systems may offer a novel contribution. However, the novelty cannot be fully assessed without seeing the detailed results.
  - **Scientific importance**: If validated, the framework could be important for whole-cell modeling and stochastic gene regulation. The potential to bridge phenomenological and mechanistic approaches is significant. However, the importance is contingent on the evidence supporting the claims.
  - **Interdisciplinary readership**: The topic is relevant to systems biology, biophysics, and computational biology. The writing is accessible to these audiences, though the lack of quantitative detail may limit broader appeal.
  - **Technical soundness**: The theoretical framework is sound in principle, but the technical execution cannot be evaluated without the missing data. The reliance on empirical time step selection and the lack of rigorous error analysis are concerns.
  - **Readability for nonspecialists**: The manuscript is generally well-written and the concepts are explained clearly. However, the heavy reliance on referenced figures and tables that are not provided makes it difficult for any reader to follow the results.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has a promising conceptual foundation, but the absence of quantitative results and detailed methodology prevents verification of the central claims. The authors should be encouraged to resubmit with the full set of figures, tables, and detailed methods. If the evidence supports the claims, the framework could be a valuable contribution.

## Risk / unsupported claims
- The claim of "10-100x speedup over SSA" is unsupported without actual timing data.
- The claim of "excellent agreement" with experimental data is unsupported without quantitative comparisons.
- The claim that the framework is "the only one that satisfies all criteria" (Table 1) is an overstatement that cannot be verified and is likely dependent on the specific criteria chosen.
- The claim that the framework "provides a mechanistic basis" for ultrasensitivity is plausible but not rigorously demonstrated.
- The generalizability claim across "the full spectrum of gene regulatory behaviors" is too broad given the limited number of systems tested and the lack of detailed results.
- The assertion that parameterization can be done from "accessible transcriptomic and proteomic data" is plausible but not demonstrated with a concrete example or protocol.