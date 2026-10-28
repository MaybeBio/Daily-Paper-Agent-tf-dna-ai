## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present TSProm, a framework that adapts the DNA foundation model DNABERT2 to identify tissue-specific promoter regulatory logic at isoform resolution. They propose a comparative training design (two models, one for general promoter biology and one for tissue-specific regulation) and an explainable AI module combining attention-based analysis with SHAP. Application to brain, liver, and testis promoters yields clinically relevant transcription factors in brain (SP1, MYC, HES6) and a global dominance of C2H2 Zinc Finger proteins in tissue-specific regulation.
- **Visible evidence base** Abstract text only; no quantitative results, validation metrics, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, model architecture details, training and evaluation protocols, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract describes a potentially useful framework for tissue-specific promoter analysis, combining a foundation model with a comparative design and explainable AI. The conceptual approach is timely and the reported biological findings are plausible. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, the validity of the comparative design, or the robustness of the biological claims. The central assertion that the two-model design "precisely isolates" tissue-defining motifs is not supported by any quantitative evidence in the supplied material. The clinical relevance claims for SP1, MYC, and HES6 are presented without supporting data. The manuscript may merit consideration after full review, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Computational biologists working on gene regulation, researchers developing or applying DNA foundation models, and experimental biologists studying tissue-specific transcription factor networks. The framework could be of interest to those seeking interpretable deep learning approaches for regulatory genomics, and the specific findings on brain transcription factors may interest neuro-oncology researchers.
- **Major strengths** The comparative training design is conceptually novel and addresses a real limitation of standard promoter models. The integration of attention-based and SHAP-based interpretability is a sensible approach to cross-validate learned features. The focus on isoform-level resolution is a meaningful advance over gene-level analyses. The reported biological findings, if validated, would be of interest to the regulatory genomics community.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (comparative design validity), R1-M2 (interpretability robustness), R1-M3 (biological validation), R1-M4 (generalizability)
- **Assessment against Nature-style criteria** Originality is moderate to high, as the comparative two-model design is not standard practice. Scientific importance is potentially high if the framework delivers on its claims, but this cannot be assessed from the abstract. Interdisciplinary readership is plausible, spanning computational and experimental biology. Technical soundness is not assessable from the supplied material. Readability for nonspecialists is adequate, though some terms (e.g., "regulatory grammar," "isoform level") may require clearer definition in the full text.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a promising framework, but the absence of any quantitative results, validation metrics, or methodological detail precludes a supportive recommendation. A full manuscript review would be required to assess whether the technical concerns can be resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the comparative design "enables the precise isolation of sequence motifs around the transcription start site that uniquely define tissue identity."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract provides no information on how the two models are trained, how their outputs are compared, or what metrics are used to establish that isolated motifs are indeed "precise" and "unique" to tissue identity. No performance benchmarks, ablation studies, or comparisons to existing methods are reported.
- **Why it matters** The central methodological contribution of the paper rests on this comparative design. Without evidence that the design outperforms simpler alternatives (e.g., a single model with tissue labels) or that the motif isolation is quantitatively validated, the core claim is unsupported.
- **Resolution test** Provide training details, a formal definition of the comparison procedure, and quantitative metrics (e.g., motif enrichment scores, precision-recall against known TF motifs, comparison to baseline models) demonstrating that the two-model design isolates tissue-defining motifs with measurable accuracy.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the xAI module "integrates attention-based discovery with model-agnostic SHAP analysis to provide robust, cross-validated interpretations of learned features."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No details are given on how attention and SHAP outputs are integrated, how cross-validation is performed, or what criteria define "robust" interpretations. Attention-based explanations are known to be unreliable in some contexts, and SHAP on transformer models can be computationally intensive and sensitive to background distributions. The abstract does not address these known limitations.
- **Why it matters** The interpretability module is the second major contribution. If the integration is not carefully designed and validated, the biological conclusions drawn from the model could be artifacts of the explanation method rather than genuine regulatory signals.
- **Resolution test** Describe the integration procedure, report agreement metrics between attention and SHAP outputs, and include validation against known regulatory elements or experimental perturbation data to demonstrate that the interpretations are biologically meaningful.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim to have "identified and validated clinically relevant transcription factors (TFs) in the brain, including SP1, MYC, and HES6, and confirmed their known roles in diseases such as gliomas and neuroblastomas."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The term "validated" is used without specifying the validation method. No experimental data, literature-based confirmation, or statistical significance is reported. The connection to gliomas and neuroblastomas is asserted without supporting evidence.
- **Why it matters** Clinical relevance is a strong claim that requires rigorous support. If the validation is only literature-based, this should be stated clearly. If experimental validation was performed, the methods and results must be described.
- **Resolution test** Specify the validation approach (e.g., ChIP-seq, knockdown experiments, curated database cross-referencing), report the relevant statistics or experimental outcomes, and clarify the strength of the disease association claims.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "C2H2 Zinc Finger proteins are a dominant feature of the global landscape of TSp gene regulation."
- **Evidence pointer** Abstract only; location not provided
- **Concern** This claim is based on analysis of only three tissues (brain, liver, testis). The term "global landscape" implies broader coverage than three tissues can support. No statistical measure of dominance is provided.
- **Why it matters** Overgeneralization from a limited tissue set could mislead the field about the universality of this finding. The claim should be scoped to the tissues analyzed or supported by additional data.
- **Resolution test** Either restrict the claim to the three tissues studied, or provide evidence from additional tissues or a meta-analysis supporting the global statement. Report the quantitative measure of dominance (e.g., enrichment score, proportion of TSp promoters).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "regulatory grammar" is evocative but undefined. Nonspecialist readers may not understand what specific sequence features are being referred to.
- **Required correction** Define the term operationally in the full text, e.g., as specific combinations of TF binding motifs, sequence conservation patterns, or structural features in promoter regions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model comparison
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not mention how TSProm compares to existing tissue-specific promoter prediction tools or to other DNA foundation model adaptations.
- **Required correction** Include a brief statement of comparative performance in the abstract or clearly reference a results section where such comparisons are presented.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Abstract; location not provided
- **Issue** No mention of data availability, code release, or model weights. For a computational framework, this is important for community adoption.
- **Required correction** State in the abstract or full text where the code, trained models, and processed data will be made available.

## Risk / unsupported claims
- The claim of "precise isolation" of tissue-defining motifs is unsupported by any quantitative evidence in the abstract.
- The claim of "robust, cross-validated interpretations" is unsupported without details on the integration and validation procedure.
- The claim of "validated clinically relevant TFs" is unsupported without specification of the validation method.
- The claim of a "global landscape" of C2H2 Zinc Finger dominance is unsupported given the analysis covers only three tissues.
- The overall performance of TSProm relative to existing methods is not assessable from the abstract.
- The isoform-level resolution claim is not substantiated with any example or metric.