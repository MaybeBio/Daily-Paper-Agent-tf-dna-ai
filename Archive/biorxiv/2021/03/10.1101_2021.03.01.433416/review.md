## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose a method combining machine learning and polymer physics to infer, from Hi-C data alone, the 1D genomic arrangement of a minimal set of binding sites that can recapitulate 3D chromatin contact patterns genome-wide in human and mouse cells. They validate these inferred sites by predicting chromatin refolding in Sox9 locus duplications against independent cHi-C data, and they show that the inferred binding domains have an overlapping, combinatorial organization that matches epigenetic chromatin states. They further claim that epigenetic profiles alone can be used to derive binding sites and hence 3D architecture, validated by predictions of Hi-C matrices on independent chromosomes.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full manuscript, methods description, all figures and tables, statistical details, validation datasets, and code or algorithm specifications

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially impactful framework that integrates polymer physics and machine learning to link 1D epigenetics to 3D chromatin architecture. The core idea, that a minimal set of binding sites inferred from Hi-C can be mapped to epigenetic states and used to predict 3D structure, is conceptually interesting and could appeal to a broad readership. However, the abstract alone provides insufficient detail to assess the technical soundness, statistical rigor, or generalizability of the claims. Several statements are broad and lack quantitative support, and the validation strategy, while described, cannot be evaluated without access to the underlying data and methods. The claim of a "combinatorial code" is intriguing but not fully substantiated from the abstract alone.
- **Who would be interested in the results, and why** Researchers in chromatin biology, 3D genome organization, epigenetics, and computational biology would be interested. The work bridges biophysical modeling and machine learning, which may also attract physicists and computer scientists working on genomic data. The potential to predict 3D architecture from epigenetic marks alone has practical implications for understanding gene regulation and disease-associated structural variants.
- **Major strengths** The conceptual integration of polymer physics and machine learning is novel and timely. The use of independent validation datasets (cHi-C at Sox9, Hi-C on other chromosomes) is a positive feature. The idea that binding domains have an overlapping, combinatorial organization, distinct from conventional epigenetic segmentations, offers a new perspective on how 1D information encodes 3D structure.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: High. The combination of polymer physics and machine learning to infer binding sites from Hi-C and link them to epigenetics is a fresh approach.  
  - Scientific importance: Potentially high, as it addresses a fundamental question about how 3D genome organization is encoded in 1D sequence features.  
  - Interdisciplinary readership: Broad, spanning molecular biology, biophysics, and computational genomics.  
  - Technical soundness: Cannot be assessed from the abstract alone. The lack of methodological detail and quantitative results prevents evaluation of the robustness of the inference and validation.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terms (e.g., "cHi-C", "epigenetic segmentation") that may require prior knowledge. The logic is understandable at a high level.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a compelling narrative, but the technical claims cannot be verified without the full manuscript. I would be supportive if the technical concerns are resolved with detailed methods, statistical validation, and clear demonstration of predictive performance.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The method infers from only Hi-C data the minimal set of binding sites sufficient to recapitulate 3D contact patterns genome-wide.  
- **Evidence pointer** Abstract, no methods or figures provided  
- **Concern** The abstract claims that a "minimal set" of binding sites can recapitulate genome-wide 3D contact patterns, but no details are given on how "minimal" is defined, how the inference is performed, or what the accuracy of the recapitulation is. Without quantitative metrics (e.g., correlation coefficients, error rates) or a description of the polymer model and machine learning algorithm, the claim is unverifiable.  
- **Why it matters** The central premise of the paper rests on the ability of the inferred binding sites to faithfully reproduce Hi-C data. If the inference is not rigorously validated or the definition of "minimal" is arbitrary, the entire framework is undermined.  
- **Resolution test** Provide a detailed methods section describing the inference algorithm, the polymer model, and the criteria for "minimal." Include quantitative comparisons between predicted and experimental Hi-C maps (e.g., Pearson correlation, stratum-adjusted correlation coefficient) for multiple chromosomes and cell types.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation strength  
- **Claim pointer** The inferred binding sites are validated by predictions on chromatin refolding in Sox9 locus duplications against independent cHi-C data, showing distinct phenotypes originate from distinct enhancer hijackings.  
- **Evidence pointer** Abstract, no figures or data provided  
- **Concern** The validation at the Sox9 locus is described qualitatively. The abstract states that "different phenotypes originate from distinct enhancer hijackings," but no quantitative comparison between predicted and observed cHi-C data is provided. It is unclear how many duplications were tested, what the predictive accuracy was, or how the "enhancer hijacking" interpretation was derived.  
- **Why it matters** This is the only direct experimental validation presented. If the predictions are not quantitatively robust or the interpretation is not well-supported, the claim that the binding sites are biologically meaningful is weakened.  
- **Resolution test** Show predicted versus observed cHi-C contact maps for the Sox9 duplications, with statistical measures of agreement. Provide a clear description of how "enhancer hijacking" is inferred from the 3D structures and how this relates to the observed phenotypes.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability  
- **Claim pointer** The inferred binding domains have an overlapping, combinatorial organization along chromosomes, missing in epigenetic segmentations, which is required to explain Hi-C contact specificity with high accuracy.  
- **Evidence pointer** Abstract, no figures or tables provided  
- **Concern** The claim that the combinatorial organization is "required" to explain Hi-C contact specificity is strong, but no comparative analysis is shown. It is not clear how the proposed model performs against existing methods (e.g., standard epigenetic segmentation-based approaches) or what "high accuracy" means quantitatively.  
- **Why it matters** The novelty of the work partly relies on the claim that existing epigenetic segmentations are insufficient. Without a direct comparison, this claim is unsupported.  
- **Resolution test** Provide a benchmark comparing the predictive performance of the proposed binding-domain model against standard epigenetic segmentation models on the same Hi-C datasets, with appropriate statistical tests.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reverse approach validity  
- **Claim pointer** In a reverse approach, the epigenetic profile of binding domains provides a code to derive from only epigenetic marks the DNA binding sites and, hence, the 3D architecture, as validated by successful predictions of Hi-C matrices in an independent set of chromosomes.  
- **Evidence pointer** Abstract, no figures or data provided  
- **Concern** The reverse approach is a key claim, but the abstract does not specify which epigenetic marks are used, how the code is learned, or what the predictive accuracy is on the independent chromosomes. "Successful predictions" is vague and could range from weak to strong correlation.  
- **Why it matters** This claim extends the utility of the framework beyond Hi-C, suggesting that 3D structure can be predicted from widely available epigenetic data. If the accuracy is not clearly demonstrated, the practical relevance is questionable.  
- **Resolution test** Specify the epigenetic marks and the machine learning model used. Provide quantitative prediction accuracy (e.g., correlation coefficients, error metrics) for the independent chromosomes, and compare against a null model or existing predictors.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, "minimal set of binding sites"  
- **Issue** The term "minimal set" is ambiguous. It could mean the smallest number of sites needed to achieve a certain accuracy, or a set that is minimal in some biological sense.  
- **Required correction** Define "minimal" explicitly in the abstract or refer to a definition in the main text.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Method description  
- **Evidence pointer** Abstract, no methods  
- **Issue** The abstract does not mention whether the code or data are publicly available, which is important for reproducibility.  
- **Required correction** State data and code availability in the abstract or refer to the main text.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** Generalization statement  
- **Evidence pointer** Abstract, "genome-wide in human and mouse cells"  
- **Issue** The abstract claims genome-wide applicability in human and mouse, but it is unclear how many cell types or conditions were tested.  
- **Required correction** Specify the number and types of cell lines or conditions used, or qualify the claim accordingly.

## Risk / unsupported claims
- The claim that the inferred binding sites are "minimal" is unsupported without a formal definition or optimization criterion.
- The claim that the combinatorial organization is "required" for high accuracy is unsupported without comparative benchmarks.
- The claim of "successful predictions" of Hi-C matrices from epigenetic marks is unquantified and cannot be evaluated.
- The biological interpretation of "enhancer hijacking" in Sox9 duplications is not substantiated with data.
- The generalizability to "genome-wide" in human and mouse is asserted without specifying the number of cell types or the extent of validation.