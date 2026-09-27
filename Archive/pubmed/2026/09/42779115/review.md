## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to figures, tables, methods, or supplementary materials
- **Shared manuscript claim summary** The authors present PURE, an interpretable computational framework that ranks candidate transcription factors (TFs) underlying differential gene expression in plants by integrating co-expression, sequence motifs, and experimental binding evidence, with cross-species projection of reference binding profiles and SHAP-based attribution, benchmarked across 11 species and applied to three biological case studies plus a discovery-oriented test on tomato SlDOF3.
- **Visible evidence base** Abstract text only; no methodological details, benchmark results, case study outputs, or validation statistics are provided
- **Missing materials affecting confidence** Full methods, benchmark tables, case study figures, SlDOF3 validation data, web resource functionality, and any statistical or performance metrics

## Reviewer
- **Overall assessment** The abstract describes a potentially useful and timely framework for TF prioritization in plants, with a clear motivation rooted in the limitations of transformation-based validation. The integration of multiple evidence types and the cross-species projection strategy are conceptually appealing. However, the abstract provides no quantitative results, no benchmark comparisons against existing methods, and no details on the SlDOF3 validation beyond a qualitative statement. The scientific case is therefore not established from the supplied material, and the claims of utility and interpretability cannot be assessed.
- **Who would be interested in the results, and why** Plant molecular biologists and crop researchers studying transcriptional regulation, particularly those working on non-model species or crops where genetic transformation is inefficient. Computational biologists developing gene regulatory network inference or TF prioritization tools would also be interested, as would researchers studying C4 photosynthesis, photosystem regulation, and fruit ripening, given the case studies.
- **Major strengths** The motivation is clear and practically relevant. The framework integrates multiple evidence types (co-expression, motifs, binding data) in a way that could improve over single-modality approaches. The cross-species projection of binding profiles is a sensible strategy for non-model species. The inclusion of a web resource increases accessibility. The discovery-oriented test on SlDOF3, with follow-up ChIP-seq and RNA-seq, is a commendable attempt to demonstrate biological utility.
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
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The combination of gradient boosting with SHAP attribution and cross-species binding projection is not entirely novel, but the specific integration for plant TF prioritization may offer a new angle. However, without comparison to existing tools, originality cannot be fully evaluated.  
  - Scientific importance: The problem is important, and the potential to aid non-model species research is significant. But the abstract does not demonstrate that PURE solves the problem better than existing approaches.  
  - Interdisciplinary readership: The work bridges computational biology and plant biology, which could attract a broad readership, but the abstract is too thin to engage either community deeply.  
  - Technical soundness: Not assessable from the abstract. No metrics, no validation details, no method specifics.  
  - Readability for nonspecialists: The abstract is generally readable, but terms like "gradient boosting" and "SHAP feature attribution" are used without explanation, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The framework is promising, but the abstract lacks the quantitative and methodological detail needed to support the claims. A revised submission with full results and comparisons would be needed for a supportive posture.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Benchmarking across 11 species spanning the green lineage showed that PURE feature matrices captured expression contrasts associated with abiotic stress, developmental trajectories, and cell-type specificity, and downstream evidence-filtered attribution scores prioritized TF candidates supported by the integrated regulatory evidence."  
- **Evidence pointer** Abstract only; no benchmark results, tables, or figures provided  
- **Concern** The abstract claims successful benchmarking across 11 species but provides no quantitative outcomes, no comparison to existing TF prioritization methods, and no definition of what "captured" or "prioritized" means in terms of performance metrics.  
- **Why it matters** Without benchmark statistics or comparisons, the reader cannot judge whether PURE outperforms or even matches existing approaches, which is essential for establishing its utility.  
- **Resolution test** Provide benchmark tables or figures with metrics such as precision, recall, or area under the curve, and compare against at least one or two existing methods on the same datasets.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation strength  
- **Claim pointer** "As a discovery-oriented test, PURE prioritized the less-characterized tomato light-dark TF SlDOF3, and integrated SlDOF3 ChIP-seq and RNA-seq analyses supported binding and associated expression changes at predicted pathway loci."  
- **Evidence pointer** Abstract only; no ChIP-seq or RNA-seq results shown  
- **Concern** The SlDOF3 validation is described qualitatively. No data are presented to show the strength of binding, the significance of expression changes, or the specificity of the predicted loci.  
- **Why it matters** The discovery test is a key claim of biological utility. Without quantitative evidence, the claim that PURE prioritizes functionally relevant TFs is unsupported.  
- **Resolution test** Show ChIP-seq peak enrichment statistics, RNA-seq differential expression values with significance thresholds, and ideally a functional assay or at least a clear link between binding and expression changes at the predicted loci.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** "PURE uses gradient boosting to handle sparse and imbalanced plant regulatory matrices and then applies SHAP feature attribution to convert model behavior into TF-level contribution scores."  
- **Evidence pointer** Abstract only; no method section or algorithmic details  
- **Concern** The abstract does not specify the input features, the training data, the handling of cross-species projection, or the criteria for filtering evidence. The gradient boosting and SHAP steps are mentioned but not described in sufficient detail to assess their appropriateness.  
- **Why it matters** Reproducibility and technical soundness cannot be evaluated without methodological detail. The reader cannot determine whether the approach is sound or whether the cross-species projection introduces biases.  
- **Resolution test** Provide a full methods section with algorithmic steps, hyperparameters, data sources, and a clear description of how cross-species relationships are used to constrain the search space.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** "PURE further supported analyses of the transcriptional plasticity of maize C(4) photosynthesis, the conserved photosystem response across lineages, and the hierarchical metabolic architecture of tomato fruit ripening."  
- **Evidence pointer** Abstract only; no case study results or figures  
- **Concern** The three case studies are mentioned as "supported" but no results are shown. It is unclear what PURE contributed beyond what standard co-expression or motif analysis would provide.  
- **Why it matters** These case studies are presented as evidence of broad applicability. Without results, the claim that PURE provides unique insights is unsubstantiated.  
- **Resolution test** Provide figures or tables for each case study showing the prioritized TFs, the supporting evidence, and a comparison to what would be obtained with simpler methods.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract terminology  
- **Evidence pointer** Abstract, first paragraph  
- **Issue** Terms like "gradient boosting" and "SHAP feature attribution" are used without brief explanation, which may confuse nonspecialist readers.  
- **Required correction** Add a short parenthetical explanation for these terms, or rephrase to describe the function in plain language.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Web resource description  
- **Evidence pointer** Abstract, last sentence  
- **Issue** The web resource is mentioned but no details on its usability, data coverage, or interface are given.  
- **Required correction** Provide a brief description of the web resource's features, such as input formats, output visualization, and supported species.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Benchmark claim  
- **Evidence pointer** Abstract, benchmarking sentence  
- **Issue** The phrase "captured expression contrasts" is vague and could mean different things.  
- **Required correction** Specify what was measured, such as classification accuracy or correlation with known regulatory events.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Comparison to existing tools  
- **Evidence pointer** Abstract, overall  
- **Issue** No mention of how PURE compares to existing TF prioritization tools, such as PlantTFDB or other co-expression-based methods.  
- **Required correction** Add a sentence in the abstract or introduction that situates PURE relative to existing approaches.

## Risk / unsupported claims
- The claim that PURE "prioritized candidate TFs supported by the integrated regulatory evidence" is unsupported without benchmark metrics.
- The claim that SlDOF3 validation "supported binding and associated expression changes" is unsupported without quantitative data.
- The claim that PURE "supported analyses" of the three case studies is unsupported without results.
- The overall utility and interpretability of PURE cannot be assessed from the abstract alone.