## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific soundness, methodological rigor, interpretability claims, and clinical relevance assertions based solely on the provided text
- **Shared manuscript claim summary** The authors present TSProm, a fine-tuned DNA foundation model (DNABERT-2) framework for classifying tissue-specific promoters at isoform level across brain, liver, and testis, with an explainable AI module combining attention-based motif discovery and SHAP analysis to identify clinically relevant transcription factors and regulatory grammar
- **Visible evidence base** Text descriptions of methods, results summaries, and references to figures (Fig. 1A-B, 2A-B, 3A-E, 4A-D) and supplementary tables (S1-S8) that are not directly viewable
- **Missing materials affecting confidence** All figures, supplementary tables, appendices, exact performance metrics, hyperparameter details, dataset statistics, and code availability information

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable application of DNA foundation models to tissue-specific promoter classification and interpretation. The conceptual framing of separating general promoter biology (Model A) from tissue-specific regulation (Model B) is thoughtful. However, the current text lacks sufficient quantitative detail to evaluate the core claims rigorously. Key performance metrics are described qualitatively ("F1 = 0.85–0.95") without standard deviations or cross-validation details. The interpretability claims, while plausible, require stronger validation against known regulatory biology and appropriate baselines. The clinical relevance assertions are intriguing but rely on literature associations rather than direct functional validation. The manuscript would benefit from clearer articulation of the novelty relative to existing promoter prediction tools and more rigorous statistical reporting.

- **Who would be interested in the results, and why** Computational biologists studying gene regulation, researchers developing interpretable deep learning methods for genomics, and investigators interested in tissue-specific transcriptional control in development and disease. The framework's focus on distal promoter regions and isoform-level resolution addresses a gap in current approaches, making it relevant to those studying alternative promoter usage and its dysregulation in cancer.

- **Major strengths**
  1. The dual-model design (Model A vs. Model B) provides a principled approach to isolate tissue-specific regulatory signals from general promoter features
  2. The integration of attention-based motif discovery with SHAP analysis offers complementary interpretability perspectives
  3. The focus on distal promoter regions (up to 3 kb upstream) extends beyond typical core promoter analyses
  4. The cross-species approach (human and mouse) strengthens generalizability claims
  5. The validation strategy using multiple external databases (JASPAR, TF-Marker, KnockTF, ENCODE) is commendable

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We observed similar performances on fine-tuning tasks across 2k, 3k, and 4k lengths around the TSS between DNABERT2 and GENA-LM. NT (500m–1000G) performs the least accurate in this task (Fig. 2A). In fact, DNABERT2 models show slightly higher accuracy and F1 scores."
- **Evidence pointer** Figure 2A; location not provided
- **Concern** The performance comparison across models is described only qualitatively. No numerical values, confidence intervals, or statistical significance tests are reported. The claim that DNABERT2 shows "slightly higher" performance is not quantified, making it impossible to assess whether differences are meaningful. Additionally, the hyperparameter tuning description ("learning rate of (2e-5, 1e-5, 3e-4, 5e-6, and others)") is vague and does not specify which values were used for which models, preventing reproducibility.
- **Why it matters** The central claim of the manuscript is that TSProm provides high predictive performance. Without quantitative performance metrics with appropriate uncertainty estimates, the technical foundation of the framework cannot be evaluated. Reproducibility requires precise hyperparameter reporting.
- **Resolution test** Provide a table with mean and standard deviation for accuracy, F1, MCC, precision, and recall across at least 5 independent runs for each model and sequence length. Report the specific hyperparameters used for each model. Include statistical tests (e.g., paired t-test or Wilcoxon) comparing DNABERT2 to GENA-LM and NT.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "TSProm demonstrates that transformer-based encoder DNA Foundation Models can be effectively specialized to capture long-range TSp promoter logic, providing high predictive performance."
- **Evidence pointer** Results section; location not provided
- **Concern** The manuscript does not compare TSProm against existing promoter prediction tools or simpler baselines beyond the three DFMs and two traditional deep learning methods mentioned. It is unclear whether the attention-based interpretability provides advantages over established motif discovery tools (e.g., HOMER, MEME-ChIP) in identifying tissue-specific regulators. The claim of "high predictive performance" needs benchmarking against state-of-the-art promoter classifiers.
- **Why it matters** Without appropriate baselines, the incremental contribution of TSProm over existing methods cannot be established. The field has many promoter prediction tools, and the novelty claim requires demonstrating clear advantages.
- **Resolution test** Include comparisons against at least 2-3 existing promoter prediction methods (e.g., CNN-based approaches, other transformer models) using the same datasets and evaluation metrics. Report whether TSProm's interpretability module identifies motifs that standard tools miss, with quantitative enrichment comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We applied SHAP KernelExplainer to interpret finetuned DNABERT2 predictions at the token level. Each promoter sequence was tokenized, and a background baseline was constructed by replacing all tokens with the model's mask token."
- **Evidence pointer** Methods section, "Validation of motifs: SHAP analysis"; location not provided
- **Concern** The SHAP methodology description is methodologically problematic. KernelExplainer with a baseline of all mask tokens is computationally expensive for sequences of 4-5 kb length with BPE tokenization, potentially making the analysis intractable. The choice of background distribution fundamentally affects SHAP values, and using a single baseline (all masks) may not reflect the true data distribution. Additionally, the manuscript does not specify how many background samples were used, which is critical for KernelExplainer convergence.
- **Why it matters** SHAP values are central to the interpretability claims. If the methodology is flawed or computationally impractical, the identified motifs may not be reliable. The choice of baseline distribution is known to significantly impact attribution results.
- **Resolution test** Provide details on the number of background samples, computational runtime, and convergence diagnostics. Justify the choice of all-mask baseline versus alternative approaches (e.g., random sampling from training data). Consider using a more efficient explainer (e.g., GradientExplainer or Integrated Gradients) appropriate for transformer models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** "mRNA transcripts are molecules thay carrry genetic information frrom DNA to ribosomes for protein synthesis."
- **Evidence pointer** Introduction; location not provided
- **Concern** This sentence contains multiple typographical errors ("thay", "carrry", "frrom") and is written at a level inconsistent with the target audience of a genomics journal. More importantly, the sentence is unnecessary for readers of this journal and suggests unclear editorial standards.
- **Why it matters** While not affecting scientific content, such errors undermine the manuscript's professionalism and suggest insufficient proofreading. The sentence's inclusion at a basic level may indicate uncertainty about the target audience.
- **Resolution test** Remove the sentence or rewrite it at an appropriate technical level. Conduct thorough proofreading throughout the manuscript.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We find significant peaks based on proportions of the background peaks found and rank them as suggested in other motif and peak scoring methods"
- **Evidence pointer** Methods section, "Clinical and biological relevance of motifs"; location not provided
- **Concern** The ENCODE validation methodology is described vaguely. The manuscript does not specify which ENCODE cell lines or tissues were used, how peak overlaps were computed, what constitutes "significant," or how background was defined. The ranking method is referenced but not described.
- **Why it matters** The ENCODE validation is a key component of the external validation strategy. Without clear methodology, the results cannot be reproduced or evaluated for potential biases (e.g., cell line selection bias).
- **Resolution test** Provide detailed methodology for ENCODE analysis: specific datasets used, peak calling parameters, overlap criteria, background model, and statistical thresholds. Include a supplementary table listing all ENCODE experiments used.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses "regulatory grammar" and "regulatory logic" without clear definitions, which may confuse readers unfamiliar with the concept.
- **Required correction** Briefly define what is meant by regulatory grammar/logic in the context of DNA sequences, or provide a concrete example.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Dataset description
- **Evidence pointer** Datasets section; location not provided
- **Issue** The manuscript states "We chose these three tissues as they had the highest number of TSp transcripts across human and mouse common organs" but does not provide the actual counts or the threshold used to determine "highest."
- **Required correction** Include a supplementary table with TSp transcript counts for all tissues considered and justify the selection threshold.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** MMseqs2 clustering
- **Evidence pointer** Datasets section, "Tackling data redundancy"; location not provided
- **Issue** The clustering threshold of 80% sequence identity and coverage is stated, but the resulting number of sequences before and after clustering is not reported.
- **Required correction** Report the number of sequences before and after clustering for each tissue and model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section
- **Evidence pointer** Results, "Deciphering brain regulatory language"; location not provided
- **Issue** The notation "B ∩ Ac" is used without prior definition, which may confuse readers.
- **Required correction** Define this notation explicitly when first used, e.g., "motifs found in Model B but not in Model A."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Statistical analysis
- **Evidence pointer** Results, "Language of the global tissue specificity"; location not provided
- **Issue** The Mann-Whitney U test result (U = 42.0, P = 0.012) is reported without context on sample sizes or what exactly was compared.
- **Required correction** Provide sample sizes and clarify what distributions were compared (e.g., overlap scores for long vs. short motifs).

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Model architecture
- **Evidence pointer** Methods, "Fine tuning of DFMs"; location not provided
- **Issue** The LoRA configuration (rank, alpha, target modules) is not specified, which is essential for reproducibility.
- **Required correction** Provide complete LoRA hyperparameters in the methods or supplementary.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The clinical relevance discussion for ZNF460 and SP5 in cancers is interesting but lacks specific citations for the cancer associations mentioned.
- **Required correction** Add appropriate references for the cancer associations of ZNF460 and SP5.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (quantitative performance reporting), R1-M2 (baseline comparisons), R1-M3 (SHAP methodology details)

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The application of DNA foundation models to tissue-specific promoter classification is not entirely novel, but the dual-model design (A vs. B) and the integration of attention-based motif discovery with SHAP analysis offer some methodological novelty. The focus on distal promoter regions at isoform resolution is a useful contribution.
  - **Scientific importance**: Moderate. Understanding tissue-specific regulation is important, and the framework could be useful for prioritizing regulatory elements in disease studies. However, the clinical relevance claims are largely associative and require functional validation to establish significance.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to computational biologists and genomics researchers. The clinical implications are mentioned but not developed sufficiently to attract a broader biomedical audience.
  - **Technical soundness**: Currently insufficient. The lack of quantitative performance metrics, vague hyperparameter reporting, and incomplete SHAM methodology details prevent rigorous evaluation. The ENCODE validation approach is described at a level that precludes reproduction.
  - **Readability for nonspecialists**: Acceptable but uneven. The introduction and discussion are generally accessible, but the methods section assumes significant expertise. The typographical errors and unnecessary basic explanations (e.g., mRNA definition) suggest inconsistent editing.

- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising, and the interpretability approach has potential, but the manuscript requires substantial revision to provide quantitative performance data, rigorous baseline comparisons, and complete methodological details. The authors should also strengthen the validation of clinical relevance claims. I would be supportive if these technical concerns are resolved in a revised manuscript with full figures and supplementary data available for evaluation.