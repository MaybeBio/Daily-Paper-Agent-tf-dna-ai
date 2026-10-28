## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, conclusion, methods, declarations) as provided
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, and evidence quality as presented in the supplied text. Figures and tables are referenced but not directly inspected.
- **Shared manuscript claim summary** The authors propose ProMoNet, a sequence-based pre-training and fine-tuning framework for predicting protein-ligand binding characteristics. ProMoSite, the pre-training module, learns residue-level binding site predictions using ESM-2 and Uni-Mol encoders with geometric constraints from contact maps and distance maps. ProMoBind, the fine-tuning module, uses ProMoSite outputs to predict binding affinity and kinetics. The authors claim ProMoSite matches or surpasses structure-based methods for cryptic pocket detection, and ProMoBind outperforms baselines for affinity and kinetics prediction.
- **Visible evidence base** Results sections 2.2-2.5 with references to Figures 2-3, Tables 1-2, and Supplementary Figures/Tables. Methods section 4.1-4.5 describing architectures, datasets, and experimental settings.
- **Missing materials affecting confidence** Actual figures, tables, and supplementary materials are not provided. Numerical results are described but not shown. Baseline implementation details for several comparisons are incomplete. Statistical significance testing is not described.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to integrating protein and ligand foundation models via binding site pre-training. The idea of using binding site prediction as a bridge between protein-level and ligand-level representations is novel and potentially impactful. However, the evidence as presented is insufficient to fully evaluate the claims. Key results are described qualitatively without numerical data in the visible text, and several methodological details require clarification. The comparison to structure-based methods, particularly for cryptic pocket detection, needs careful scrutiny regarding dataset overlap and evaluation fairness. The efficiency claims are promising but require more rigorous benchmarking. Overall, the work has merit but the current presentation does not fully establish the stated advantages.

- **Who would be interested in the results, and why** Computational biologists and medicinal chemists working on structure-based drug discovery, particularly those interested in cryptic pocket identification, binding affinity prediction, and virtual screening. The sequence-based approach could appeal to researchers seeking to avoid expensive structure prediction or MD simulations. The integration of foundation models is timely and relevant to the broader machine learning for drug discovery community.

- **Major strengths**  
  1. Novel pre-training strategy using binding site prediction to bridge protein and ligand foundation models, which is conceptually distinct from prior work.  
  2. Sequence-based approach with demonstrated efficiency advantages over structure-based generative models.  
  3. Comprehensive evaluation across multiple tasks (binding site, affinity, kinetics) with multiple data splits.  
  4. Clear discussion of limitations and comparison to prior methods in Section 4.5.

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence quality  
  - **Claim pointer** "ProMoSite outperforms all 3D structure-based baselines, achieving an averaged Top-n success rate of 68.30% ± 0.99 on COACH420 and 73.46% ± 0.65 on HOLO4K"  
  - **Evidence pointer** Section 2.2, Figure 2a  
  - **Concern** The numerical results are stated in the text but the actual figure is not available for inspection. More critically, the comparison to structure-based methods requires careful examination of whether the evaluation protocol is fair. Structure-based methods typically require a single input structure, while ProMoSite may benefit from training on holo structures in scPDB. The manuscript does not clarify whether the structure-based baselines were given the same holo structures or only apo structures. If baselines were evaluated on apo structures while ProMoSite implicitly learns from holo-derived labels, the comparison may be biased.  
  - **Why it matters** The central claim of matching or surpassing structure-based methods depends entirely on the fairness of this comparison. Without clarity on input structures and evaluation protocols, the claim cannot be verified.  
  - **Resolution test** Provide explicit description of what structural inputs each baseline received (apo vs holo), and confirm that ProMoSite does not have access to holo structure information at inference time beyond what is encoded in sequence. Consider evaluating baselines on both apo and holo structures to demonstrate the comparison is not biased.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological clarity  
  - **Claim pointer** "ProMoSite matches or surpasses state-of-the-art methods that depend on 3D structures and achieves the best results on cryptic site prediction"  
  - **Evidence pointer** Section 2.3, Figure 3a-b  
  - **Concern** The cryptic pocket detection evaluation uses the PocketMiner dataset, which includes proteins with known cryptic pockets. The manuscript states ProMoSite is trained on scPDB, a general binding site database, and evaluated on PocketMiner test sets. However, the relationship between scPDB training data and PocketMiner test proteins is not fully described. If any PocketMiner test proteins or close homologs appear in scPDB, the evaluation could be compromised. Additionally, the comparison to generative models (NeuralPLexer, DynamicBind) that predict 3D complexes is methodologically different from residue-level scoring, and the mapping of ProMoSite residue scores to 3D pockets via clustering may introduce artifacts.  
  - **Why it matters** Cryptic pocket detection is a challenging task where data leakage or evaluation protocol differences can dramatically affect results. The claim of matching generative models is strong and requires rigorous validation.  
  - **Resolution test** Provide sequence identity analysis between scPDB training proteins and PocketMiner test proteins. Describe the clustering parameters and how they affect results. Consider evaluating ProMoSite on additional cryptic pocket benchmarks to demonstrate generalizability.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence quality  
  - **Claim pointer** "ProMoBind achieves the highest Pearson and Spearman correlation coefficients and the second-lowest RMSE" on binding affinity prediction, and "outperforms all baselines across all metrics" for kinetics prediction  
  - **Evidence pointer** Section 2.4, Table 1; Section 2.5, Table 2  
  - **Concern** The actual numerical values in Tables 1 and 2 are not visible in the provided text. The claims of superiority are made without presenting the magnitude of improvement or error bars. For affinity prediction, the comparison includes many baselines with different input types (3D structures, sequences, etc.), and it is unclear whether the differences are statistically significant. For kinetics prediction, the dataset is small (683 pairs) and the baselines are limited to RF and XGBoost, which may not represent the state of the art.  
  - **Why it matters** The practical value of ProMoBind depends on the magnitude of improvement over existing methods. Without numerical details and significance testing, the claims cannot be assessed.  
  - **Resolution test** Provide full numerical results with standard deviations or confidence intervals. Perform statistical significance testing (e.g., paired bootstrap or McNemar test) for the key comparisons. Include additional state-of-the-art baselines for kinetics prediction.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Technical soundness  
  - **Claim pointer** "By using contact maps, our model can implicitly leverage dynamic structural information associated with multistate protein conformations"  
  - **Evidence pointer** Section 2.1, Figure 1a  
  - **Concern** The claim that predicted contact maps capture dynamic conformational information is plausible but not directly validated. The manuscript does not provide evidence that the contact maps used are accurate for the test proteins, nor does it demonstrate that the model actually benefits from conformational diversity rather than simply learning static binding site features. The comparison to structure-based methods that use static structures may conflate the benefit of contact maps with other architectural differences.  
  - **Why it matters** The novelty of the approach partly rests on the claim that sequence-based contact maps can substitute for explicit conformational sampling. This needs direct validation.  
  - **Resolution test** Provide analysis of contact map prediction accuracy on test proteins. Conduct ablation studies where contact maps are replaced with alternative features (e.g., predicted secondary structure) to isolate the contribution of contact maps. Consider comparing to a variant that uses static predicted structures (e.g., from ESMFold) to demonstrate the specific advantage of contact maps.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Section 2.2, comparison to sequence-based methods  
  - **Evidence pointer** Figure 2b  
  - **Issue** The comparison to sequence-based methods (HoTS, DeepProSite, Pseq2Sites) is described but the specific advantages of ProMoSite over these methods are not clearly enumerated. The text mentions "consistently better performance" but does not explain why.  
  - **Required correction** Provide a brief analysis of why ProMoSite outperforms sequence-based baselines, focusing on architectural differences (e.g., contact map constraints, foundation model representations).

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Section 4.3, dataset preprocessing  
  - **Evidence pointer** Section 4.3  
  - **Issue** The description of dataset preprocessing for the koff dataset is incomplete. The criteria for removing "inconsistent entries" and "redundant pairs" are described but the exact thresholds and procedures are not fully specified.  
  - **Required correction** Provide detailed preprocessing steps, including specific criteria for inconsistency (e.g., ratio of koff/kon to Kd) and redundancy (e.g., Tanimoto coefficient threshold and how "same protein" is defined).

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Presentation  
  - **Affected element** Section 2.4, efficiency comparison  
  - **Evidence pointer** Supplementary Table 8  
  - **Issue** The efficiency comparison is mentioned but the actual training and inference times for baselines are not discussed in the main text. The claim of being "the fastest model" needs context.  
  - **Required correction** Summarize the key efficiency numbers in the main text and discuss the trade-offs between speed and performance.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Section 4.1, ProMoSite architecture  
  - **Evidence pointer** Equations 4-6  
  - **Concern** The equations for the interaction module are presented but the dimensions and initialization of the learnable parameters are not specified. The number of layers and hidden dimensions are not stated.  
  - **Required correction** Provide full architectural details, including number of layers, hidden dimensions, and parameter initialization schemes.

## Risk / unsupported claims
- The claim that ProMoSite "captures the dynamic nature of proteins" is not directly validated with experiments showing sensitivity to conformational states.
- The claim of "superior performance" in affinity and kinetics prediction cannot be fully assessed without the actual numerical results from Tables 1 and 2.
- The statement that ProMoNet "matches or surpasses state-of-the-art structure-based methods" for cryptic pocket detection requires verification of evaluation fairness, particularly regarding input structures and dataset overlap.
- The efficiency advantage of ProMoSite (0.05s per protein) is presented without comparison to the preprocessing time required for structure-based methods, which may include MD simulations that are not counted in the inference time.
- The generalizability of ProMoSite to protein families underrepresented in scPDB (e.g., GPCRs, ion channels) is acknowledged as a limitation but not quantitatively assessed.