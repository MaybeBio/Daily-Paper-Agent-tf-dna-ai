## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, or supplementary data were provided
- **Shared manuscript claim summary** The authors report the design of synthetic coactivator-recruiting proteins guided by AlphaFold3 predictions, validated through a high-throughput mammalian cell screening platform. They identify over 300 nanomolar-affinity binders to Mediator, BRD4, NCOA, and p300, demonstrate tunable affinities via interface mutations, establish an ultrasensitive relationship between p300-binding affinity and transcriptional output with a threshold near 500 nM, show that p300 binder-based CRISPRa effectors outperform VPR across multiple loci with minimal cytotoxicity, and observe functional synergy between p300 and Mediator binders.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or statistical details
- **Missing materials affecting confidence** Full manuscript, experimental protocols, screening data, binding affinity measurements, transcriptional activity assays, cytotoxicity data, statistical analyses, and comparisons to existing effectors

## Reviewer
- **Overall assessment** The abstract presents a compelling and potentially high-impact approach to programmable gene activation through designed coactivator binders. The conceptual advance of linking quantitative binding affinity to transcriptional output is notable, and the reported synergy between coactivator pathways is intriguing. However, the abstract alone provides insufficient detail to evaluate the robustness of the screening platform, the quality of the binding affinity measurements, the statistical basis for the ultrasensitive threshold, or the rigor of the CRISPRa comparisons. Several claims, particularly regarding the generality of the design approach and the superiority over VPR, require careful scrutiny of the full data.
- **Who would be interested in the results, and why** Synthetic biologists and gene therapy researchers would be interested in the compact effectors for programmable activation. Protein designers and biophysicists would value the quantitative framework linking affinity to function. Researchers studying transcriptional regulation and coactivator biology would find the synergy data relevant. The work may also appeal to those developing CRISPRa tools for therapeutic applications.
- **Major strengths** The abstract describes a systematic, high-throughput approach to a longstanding challenge in transcriptional engineering. The use of AlphaFold3 to guide design is timely and potentially generalizable. The reported ultrasensitive threshold provides a quantitative design principle. The synergy between p300 and Mediator binders offers a new mechanistic insight. The compact size and low cytotoxicity of the effectors are practically advantageous.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide evidence for the specificity of the designed binders, the reproducibility of the screening platform, the statistical power of the affinity-transcription relationship, or the controls used in the CRISPRa comparisons. Without these, the core claims cannot be fully assessed.
- **Assessment against Nature-style criteria** Originality is high, as the quantitative affinity-to-output framework and the synergy finding are novel. Scientific importance is potentially high for both fundamental transcription biology and applied gene regulation. Interdisciplinary readership is plausible, spanning protein design, synthetic biology, and transcriptional regulation. Technical soundness cannot be evaluated from the abstract alone, and the lack of methodological detail is a concern. Readability for nonspecialists is adequate, though the abstract assumes familiarity with coactivator biology and CRISPRa systems.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim identification of over 300 well folded nanomolar affinity binders to multiple coactivator subunits.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe how binding affinity was measured, how folding was assessed, or how specificity against off-target coactivator subunits or other proteins was determined. The number of binders is stated without any distribution of affinities, subunit coverage, or validation criteria.
- **Why it matters** Without evidence of rigorous biophysical characterization and specificity controls, the claim of "well folded nanomolar affinity binders" cannot be distinguished from promiscuous or poorly characterized interactions, which would undermine the foundation of the entire study.
- **Resolution test** Provide binding affinity data (e.g., surface plasmon resonance or isothermal titration calorimetry) for a representative set of binders, structural or biophysical evidence of folding, and specificity assays against related coactivator domains and unrelated proteins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim an ultrasensitive relationship between p300-binding affinity and transcriptional output with a sharp threshold at approximately 500 nM.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not report the number of p300 binders tested, the range of affinities sampled, the number of replicates, or the statistical model used to define ultrasensitivity. The threshold value of 500 nM is presented without confidence intervals or a description of how it was derived.
- **Why it matters** The ultrasensitive relationship is a central quantitative claim that could guide future design. If the threshold is based on a small number of data points or a poorly constrained fit, the conclusion may not be robust, and the design principle would be unreliable.
- **Resolution test** Show a plot of transcriptional output versus binding affinity with all data points, fit parameters, and confidence intervals. Describe the statistical test used to establish the threshold and demonstrate that the relationship holds across independent replicates and multiple genomic loci.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that p300 binder-based CRISPRa effectors drove stronger activation than VPR across multiple genomic loci with minimal detectable cytotoxicity.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not specify the number of loci tested, the magnitude of activation differences, the normalization method, or the cytotoxicity assay used. It is unclear whether the comparison to VPR was performed under matched conditions (e.g., same delivery, same promoter, same expression level).
- **Why it matters** The claim of superiority over VPR is practically important for the utility of the effectors. Without controlled comparisons and quantitative data, the claim may be overstated or confounded by differences in expression or delivery.
- **Resolution test** Provide activation data for all tested loci with statistical comparisons to VPR, describe the cytotoxicity assay and its sensitivity, and confirm that effector and VPR were expressed at comparable levels.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality and scientific importance
- **Claim pointer** The authors claim that combining p300- and Mediator-specific binders enhanced transcription, revealing functional synergy.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe the magnitude of the synergistic effect, the number of combinations tested, or whether the effect was observed across multiple loci and cell types. The mechanistic basis for synergy is not discussed.
- **Why it matters** The synergy claim is mechanistically interesting and could have implications for understanding coactivator function. However, without quantitative data and mechanistic context, the claim remains preliminary and its significance is unclear.
- **Resolution test** Show dose-response and combination data for p300 and Mediator binders, including statistical interaction terms, and provide a mechanistic hypothesis supported by additional experiments (e.g., recruitment assays or mutant studies).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract text
- **Issue** The abstract uses terms such as "ultrasensitive relationship" and "compact synthetic effectors" without defining them for a broader audience.
- **Required correction** Briefly define ultrasensitivity in this context and specify what "compact" means relative to existing effectors.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Screening platform
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract states a high-throughput screening platform was developed but does not describe the assay readout, the number of variants screened, or the false-positive rate.
- **Required correction** Provide a brief description of the screening method and its validation in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Generalizability
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract does not indicate whether the design approach is generalizable to other coactivators or transcriptional contexts beyond those tested.
- **Required correction** Add a statement on the expected generality or limitations of the approach.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Cytotoxicity
- **Evidence pointer** Abstract only; location not provided
- **Issue** The claim of "minimal detectable cytotoxicity" is vague without a description of the assay or the threshold for detection.
- **Required correction** Specify the cytotoxicity assay used and the level of effect relative to controls.

## Risk / unsupported claims
- The claim of over 300 well folded nanomolar affinity binders is unsupported without biophysical data and specificity controls.
- The ultrasensitive threshold at approximately 500 nM is unsupported without the underlying data and statistical analysis.
- The claim of stronger activation than VPR is unsupported without controlled comparisons and quantitative results.
- The synergy between p300 and Mediator binders is unsupported without quantitative combination data and mechanistic evidence.
- The generalizability of the design approach to other coactivators is not assessable from the abstract.