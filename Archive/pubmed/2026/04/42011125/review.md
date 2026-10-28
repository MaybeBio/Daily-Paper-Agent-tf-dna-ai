## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors use KANBind as a diagnostic probe to evaluate sequence-based DNA-binding protein (DBP) prediction under strict homology control and realistic prevalence. They report a calibrated precision of 0.0558 at a realistic bacterial prevalence, corresponding to a 94.42% false discovery rate, and approximately 95 false positives per 100 predicted DBPs in a proteome-scale scan. Interpretability analysis suggests predictions are driven by coarse physicochemical cues such as electrostatics. The authors conclude that apparent benchmark gains may be dominated by homology leakage and balanced evaluation sets rather than generalizable functional rules.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full methods, benchmark details (HBTD construction, homology control thresholds), prevalence estimation procedure, model architecture and training details, interpretability methodology, and all quantitative results beyond the single precision value

## Reviewer
- **Overall assessment** The abstract presents a potentially important cautionary result regarding the generalizability of DBP prediction models under realistic conditions. The core finding, that calibrated precision drops to 0.0558 at realistic prevalence, is striking and could have broad implications for the field. However, the abstract alone provides insufficient detail to verify the methodology, the validity of the prevalence estimate, the rigor of the homology control, or the interpretability claims. The manuscript may be of interest to the computational biology community, but the evidence base as presented is too thin to establish the case.
- **Who would be interested in the results, and why** Researchers developing and evaluating protein function prediction tools, particularly those working on DNA-binding protein prediction, would be interested in the prevalence-calibrated evaluation framework and the cautionary findings. The results may also interest bioinformaticians concerned with benchmark design and the pitfalls of balanced test sets, as well as biologists who use such prediction tools for proteome-wide annotation and need to understand their reliability.
- **Major strengths** The abstract addresses a real and underappreciated problem in the field, namely the gap between benchmark performance and real-world applicability under class imbalance. The use of a diagnostic probe rather than a claim of model superiority is a thoughtful framing. The explicit reporting of false discovery rate and false positives per 100 predictions is a clear and useful way to communicate practical impact.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (prevalence estimate), R1-M2 (homology control rigor), R1-M3 (interpretability claim)
- **Assessment against Nature-style criteria** Originality: the prevalence-calibrated evaluation approach is a useful contribution, though the general idea of class imbalance affecting performance is not new. Scientific importance: the finding, if verified, is important for the DBP prediction community and for users of such tools. Interdisciplinary readership: the abstract is accessible to computational biologists and may interest experimental biologists who use prediction tools, but the narrow focus on DBP prediction limits broader appeal. Technical soundness: cannot be assessed from the abstract alone; the key methodological details are missing. Readability for nonspecialists: the abstract is clearly written and the practical implications are well communicated, though the formula notation is not expanded.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims a calibrated precision of 0.0558 at a realistic bacterial prevalence, implying a 94.42% FDR.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The prevalence value is not stated numerically in the abstract, only referenced as "[Formula: see text]". The basis for this prevalence estimate is not described. It is unclear whether this prevalence is derived from a specific bacterial proteome, a curated database, or an assumption. The precision value depends critically on this prevalence, and without knowing its provenance, the headline result cannot be evaluated.
- **Why it matters** The central quantitative claim of the abstract rests entirely on the prevalence estimate. If the prevalence is unrepresentative or miscalculated, the reported precision and FDR would change substantially. The authors frame this as a "reality check", so the realism of the prevalence input is the foundation of the entire argument.
- **Resolution test** Provide the numerical prevalence value, its source, and the method used to estimate it. Show sensitivity of the calibrated precision to a plausible range of prevalence values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims evaluation on a "homology-controlled HBTD benchmark" with "strict homology control".
- **Evidence pointer** Abstract text; location not provided
- **Concern** No details are given about how homology control was implemented. Common issues include the sequence identity threshold used, whether the control was applied at the family or fold level, and whether the test set was truly independent of the training set. Without this information, the claim of "strict" homology control cannot be verified, and the conclusion that benchmark gains are due to "homology leakage" is not established.
- **Why it matters** The authors' central argument is that previous high performance was inflated by homology leakage. To make this claim, they must demonstrate that their own evaluation is free of such leakage. If the homology control is weak or inconsistently applied, the comparison to prior benchmarks is not fair, and the conclusion is undermined.
- **Resolution test** Describe the homology control procedure in detail, including the sequence identity threshold, the database used for redundancy removal, and the validation that no test sequences share significant similarity with training sequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that "interpretability analysis indicates that predictions are driven mainly by coarse physicochemical cues such as electrostatics".
- **Evidence pointer** Abstract text; location not provided
- **Concern** No information is provided about the interpretability method used, the nature of the analysis, or the quantitative support for this claim. The statement is vague and could be based on any number of approaches, from attention weights to saliency maps to feature ablation. Without specifics, this claim is not assessable.
- **Why it matters** This claim is used to support the conclusion that the model has not learned generalizable functional rules. If the interpretability analysis is methodologically weak or the conclusion is overstated, the broader message about the limits of sequence-based prediction is weakened.
- **Resolution test** Describe the interpretability method, show the specific evidence that electrostatics dominate, and provide a quantitative comparison to other feature types.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "prevalence-calibrated reporting" is used without definition. It is not clear whether this refers to a specific statistical correction method or simply to reporting metrics at a realistic prevalence.
- **Required correction** Define the term explicitly or replace it with a more standard phrase such as "metrics computed at realistic class prevalence".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not report the performance of KANBind on the original balanced benchmark. Without this comparison, the reader cannot assess the magnitude of the drop from balanced to realistic conditions.
- **Required correction** Include the balanced benchmark performance alongside the prevalence-calibrated result to contextualize the drop.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states "approximately 95 false positives per 100 predicted DBPs" but does not clarify whether this is a direct conversion of the 94.42% FDR or an independent calculation. The rounding also obscures the exact relationship.
- **Required correction** State explicitly that this is derived from the FDR and use consistent precision in the numbers.

## Risk / unsupported claims
- The calibrated precision of 0.0558 and the associated FDR of 94.42% are unsupported because the prevalence value and its estimation method are not provided.
- The claim of "strict homology control" is unsupported because no methodological details are given.
- The interpretability claim regarding electrostatics is unsupported because no method or quantitative evidence is described.
- The conclusion that "apparent benchmark gains can be dominated by homology leakage" is not established from the abstract alone, as no comparison to prior benchmarks is shown and the homology control procedure is not described.
- The claim that the findings "motivate stress-test benchmarks" is a reasonable suggestion but is not supported by data in the abstract.