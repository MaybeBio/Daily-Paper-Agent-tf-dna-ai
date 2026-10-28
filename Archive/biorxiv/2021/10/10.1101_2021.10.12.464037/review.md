## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) from bioRxiv preprint
- **Assessment boundary** Scientific claims, experimental design, modeling approach, and interpretation as presented in the provided text; no evaluation of figures or supplementary materials beyond what is described
- **Shared manuscript claim summary** The authors claim that mammalian promoters can decode transcription factor (TF) dynamics, that this decoding requires inefficient coupling between TF binding and pre-initiation complex (PIC) formation, that inefficient translation initiation amplifies this decoding, and that a phase separation-based mechanism could theoretically allow promoters to respond better to pulsatile than sustained TF signals
- **Visible evidence base** Descriptions of experimental results (Figures 1-6, S1-S5), mathematical model description, methods for imaging and image analysis
- **Missing materials affecting confidence** Actual figures and supplementary tables (Table S1, S3, S4), full model equations (referenced as Supplementary Text), raw data, statistical details, and code for the model and image analysis pipeline

## Reviewer
- **Overall assessment** This manuscript addresses an important question in gene regulation: how promoters decode TF dynamics. The combination of optogenetics, synthetic promoters, deep learning-based image analysis, and mathematical modeling is innovative and well-suited to the problem. The central claim that weak coupling between TF binding and PIC assembly enables dynamic decoding is mechanistically plausible and supported by the described experiments. However, the manuscript has several significant weaknesses that must be addressed. The evidence for the key claims is presented largely through figure descriptions without access to the actual data, making it difficult to fully assess statistical robustness. The theoretical mechanism based on phase separation is speculative and not experimentally tested. The translation initiation claim rests on a single construct comparison. The authors should also clarify the relationship between their synthetic system and natural promoter behavior, and address the population-level versus single-cell interpretations of their data.

- **Who would be interested in the results, and why** Researchers in gene regulation, systems biology, synthetic biology, and optogenetics would find these results of interest. The work provides a mechanistic framework for understanding how promoter architecture influences responsiveness to TF dynamics, which has implications for understanding natural signaling pathways (e.g., p53, NF-κB) and for designing synthetic gene circuits with specific dynamic response properties. The combination of experimental and modeling approaches offers a template for similar studies in other systems.

- **Major strengths** 
  1. The use of a synthetic biology approach with well-characterized parts allows for systematic dissection of promoter features that enable dynamic decoding, avoiding confounding factors in natural promoters.
  2. The combination of optogenetics with automated image analysis enables precise control and measurement of TF dynamics at single-cell resolution.
  3. The mathematical model provides a mechanistic framework that can generate testable predictions and is validated against multiple experimental conditions.
  4. The finding that weak coupling between TF binding and PIC assembly is key for dynamic decoding is a conceptually important insight that could apply broadly.
  5. The theoretical exploration of phase separation as a mechanism for filtering sustained signals is thought-provoking and could stimulate future work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we find that decoding of TF dynamics occurs only when the coupling between TF binding and transcription pre-initiation complex formation is inefficient"
- **Evidence pointer** Figures 2, 3, 4; Table S1
- **Concern** The central claim that decoding requires inefficient coupling is based on a limited set of promoter variants (p1-p4, p5-p7). The authors vary promoter strength by changing the TATA box and RE strength, but it is unclear how many independent promoter configurations were tested and whether the observed pattern holds across a broader parameter space. The claim that decoding "occurs only when" coupling is inefficient is strong and would require demonstration that efficient coupling always abolishes decoding, not just in the few tested cases.
- **Why it matters** This is the central mechanistic claim of the paper. If the conclusion is based on a narrow set of promoter variants, it may not generalize. The authors should either test a wider range of promoter configurations or temper the strength of their claim.
- **Resolution test** Provide additional promoter variants with intermediate coupling efficiencies, or clearly state the limitations of the tested parameter space. Alternatively, use the model to predict and experimentally verify the behavior of additional promoter designs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "the ability of a promoter to decode TF dynamics gets amplified by inefficient translation initiation"
- **Evidence pointer** Figure 5; Figures S4, S5
- **Concern** The claim that translation initiation efficiency amplifies decoding is based on a comparison between constructs with different 5'UTRs (5UTR1, 5UTR2, 5UTR3). However, the authors only show that the construct with the lowest translation efficiency (5UTR3, lacking Kozak sequence) shows dynamic sensitivity at the protein level. It is unclear whether this effect is specific to translation initiation efficiency or could be due to other differences between the constructs (e.g., mRNA stability, secondary structure). Additionally, the model prediction for this effect is described but the model parameters for translation are not clearly specified.
- **Why it matters** This is a secondary but important claim that connects promoter-level decoding to downstream translation. If the effect is not specifically due to translation initiation efficiency, the interpretation is weakened.
- **Resolution test** Include additional controls, such as constructs with mutations in the Kozak sequence that do not affect mRNA stability, or measure mRNA levels directly to rule out stability effects. Provide more detail on how translation parameters were estimated in the model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** "we propose a theoretical mechanism based on phase separation that would allow a promoter to be activated better by pulsatile than sustained TF signals"
- **Evidence pointer** Figure 6
- **Concern** The phase separation mechanism is purely theoretical and is not experimentally tested. While the authors acknowledge this, the inclusion of this speculative mechanism in the abstract and as a major conclusion may overstate its significance. The model modification to include a fourth "inactive" state is ad hoc, and the biological plausibility of this state is not well-justified.
- **Why it matters** Readers may interpret this as a demonstrated mechanism rather than a hypothesis. The authors should clearly distinguish between experimentally supported conclusions and theoretical predictions.
- **Resolution test** Either provide experimental evidence for the phase separation mechanism (e.g., using known phase-separating TFs) or clearly frame this as a purely theoretical prediction that requires future testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Combining optogenetics, deep learning-based image analysis and mathematical modeling"
- **Evidence pointer** Methods: Quantification and statistical analysis
- **Concern** The image analysis pipeline is described in detail but relies on a previously published neural network (Çiçek et al., 2020). The authors describe modifications to this pipeline, but it is unclear how the accuracy of the modified pipeline was validated for the specific experimental conditions used here. The segmentation of nuclei and cytosol in the absence of dedicated markers is challenging, and errors could affect the quantitative measurements of TF dynamics and reporter expression.
- **Why it matters** The quantitative measurements are the foundation of all experimental claims. If the image analysis introduces systematic errors, the conclusions could be affected.
- **Resolution test** Provide validation of the image analysis pipeline for the specific experimental conditions, such as comparison with manual segmentation or use of known ground truth data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "All experimental findings were reproduced in at least three independent experiments"
- **Evidence pointer** Methods: Statistics and reproducibility
- **Concern** The statement that experiments were reproduced in at least three independent experiments is vague. It is unclear whether this refers to three independent biological replicates, three independent transfections, or three independent experiments with multiple replicates each. The statistical analysis is not described in detail, and it is unclear what statistical tests were used and how significance was determined.
- **Why it matters** Reproducibility and statistical rigor are essential for the claims made. Without clear description of replicates and statistical methods, the reader cannot assess the robustness of the findings.
- **Resolution test** Provide detailed description of the number of replicates, the statistical tests used, and the criteria for significance. Include error bars and statistical significance indicators in all figures.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "decoding of TF dynamics occurs only when the coupling between TF binding and transcription pre-initiation complex formation is inefficient" but does not define what is meant by "inefficient" in quantitative terms.
- **Required correction** Provide a quantitative definition of "inefficient coupling" in the abstract or refer to the specific parameters used in the model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results: "Mammalian promoters can decode TF dynamics"
- **Issue** The authors state that promoter p1 "does not respond significantly to synTF amplitude" but do not provide the statistical analysis or the range of amplitudes tested.
- **Required correction** Provide the statistical test used and the range of amplitudes tested, or refer to the relevant figure and supplementary information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results: "Weak coupling between TF binding and PIC assembly..."
- **Issue** The description of the model's "refractory state" is somewhat confusing. It is defined as a state where PIC cannot be assembled despite TF being bound, but the biological basis for this state is not clearly explained.
- **Required correction** Provide a clearer biological explanation for the refractory state and how it relates to known mechanisms of transcriptional regulation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The authors discuss the implications of their findings for natural signaling pathways but do not provide specific examples of promoters that might exhibit the described behavior.
- **Required correction** Provide specific examples of natural promoters or signaling pathways where the proposed mechanism might be relevant.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Methods
- **Evidence pointer** Methods: Modeling
- **Issue** The model description is brief and refers to supplementary text for equations. It is unclear how the model parameters were estimated and what the sensitivity of the results is to parameter values.
- **Required correction** Provide a more detailed description of the model in the main text or ensure the supplementary text includes full equations, parameter values, and sensitivity analysis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods: Molecular cloning
- **Issue** The methods describe the construction of plasmids but do not provide details on how the promoter variants were designed and validated.
- **Required correction** Provide details on the design of promoter variants, including the sequences of the RE and TATA box variants, and how they were validated.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results: "Promoters activated by pulsatile but not sustained dynamics can theoretically exist"
- **Issue** The title of this section is somewhat misleading, as the authors do not demonstrate the existence of such promoters but rather show that they can theoretically exist in the model.
- **Required correction** Consider rephrasing the section title to more accurately reflect the content, e.g., "A theoretical mechanism for pulsatile-specific promoter activation."

## Risk / unsupported claims
- The claim that "decoding of TF dynamics occurs only when the coupling between TF binding and transcription pre-initiation complex formation is inefficient" is not fully supported by the limited set of promoter variants tested.
- The claim that "inefficient translation initiation amplifies the decoding process" is based on a limited set of constructs and may be confounded by other factors.
- The theoretical mechanism based on phase separation is not experimentally tested and should be clearly framed as a hypothesis.
- The statement that "all experimental findings were reproduced in at least three independent experiments" is vague and does not provide sufficient detail on replicates and statistical analysis.
- The model's ability to predict the behavior of promoters p2-p4 is described but the quality of the fit and the uncertainty in parameter estimates are not reported.
- The claim that "promoters that are activated by pulsatile dynamics are also activated by sustained signals" is based on the limited set of promoters tested and may not be generalizable.