## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence. No assessment of code availability or peer review history.
- **Shared manuscript claim summary** The authors introduce GRouNdGAN, a causal implicit generative model that simulates single-cell RNA-seq data under the guidance of a user-defined gene regulatory network (GRN). The model is claimed to generate realistic scRNA-seq data preserving gene identities, cell trajectories, pseudo-time ordering, and technical/biological noise, while imposing causal TF-gene relationships. The authors further claim that GRouNdGAN enables in silico perturbation experiments and provides a benchmark for GRN inference methods that aligns with experimental results from prior studies.
- **Visible evidence base** Results sections on data realism (Tables 1–3, Figures 2, 6), GRN imposition (Figure 2F, Supplementary Figure 6), GRN reconstruction (Figure 3, Supplementary Figures 7–9), trajectory and pseudo-time preservation (Figures 4–5, Supplementary Figures 10–17), and methods sections describing architecture, training, and evaluation metrics.
- **Missing materials affecting confidence** Code repository not provided in the manuscript text. Full hyperparameter details for all datasets are only in supplementary tables (not fully visible). Detailed statistical comparisons (e.g., confidence intervals, variability across seeds) are not fully reported. The manuscript references supplementary notes and figures extensively, but these are not fully available in the provided material.

## Reviewer
- **Overall assessment** The manuscript presents a novel and timely contribution to the field of single-cell RNA-seq simulation by integrating causal GRN structure into a GAN framework. The methodological design is thoughtful, and the evaluation across multiple datasets and metrics is commendable. However, several technical concerns regarding causal validity, evaluation rigor, and reproducibility need to be addressed before the claims are fully established.
- **Who would be interested in the results, and why** Researchers developing and benchmarking GRN inference algorithms, computational biologists studying gene regulatory dynamics, and method developers in single-cell genomics. The ability to generate realistic scRNA-seq data with known ground-truth causal relationships is of broad interest for benchmarking and for in silico perturbation studies.
- **Major strengths**
  1. Novel integration of causal GRN structure into a GAN framework for scRNA-seq simulation, addressing a key limitation of existing simulators.
  2. Comprehensive evaluation across multiple datasets, including heterogeneous and continuous differentiation contexts.
  3. Demonstration of GRN imposition via knockout experiments and reconstruction by multiple inference methods.
  4. Preservation of trajectories and pseudo-time ordering, which is critical for downstream benchmarking.
  5. The model requires no manual parameter tuning for data realism, a practical advantage over existing methods.
- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Causal validity)
    - **Claim pointer** The authors claim that GRouNdGAN imposes a causal GRN in the simulated data, such that TF-gene edges represent causal relationships.
    - **Evidence pointer** Results section "GRouNdGAN imposes a causal GRN in the simulated data", Figure 2F, Supplementary Figure 6.
    - **Concern** The causal interpretation of the imposed GRN is not fully justified. The input GRN is inferred from the reference data using GRNBoost2, which identifies statistical associations, not necessarily causal relationships. While the authors acknowledge this, the claim that the model imposes "causal" relationships is stronger than what is demonstrated. The knockout experiments show that perturbing a TF changes target gene expression, but this only demonstrates that the model encodes the input graph structure, not that the input graph itself is causal. The authors should clarify the distinction between "causal" as encoded in the model architecture versus "causal" as a property of the underlying biology.
    - **Why it matters** The term "causal" is central to the manuscript's framing and to its claimed contribution. Overstating causal validity could mislead users who may interpret simulated data as reflecting true causal biology.
    - **Resolution test** The authors should either (a) temper the causal language throughout, referring to "graph-imposed" or "structure-guided" relationships, or (b) provide additional evidence that the imposed edges correspond to known causal interactions (e.g., using curated databases or perturbation data) for at least a subset of edges.
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Evaluation rigor)
    - **Claim pointer** The authors claim that GRouNdGAN outperforms existing simulators in generating realistic scRNA-seq data (Tables 1–3).
    - **Evidence pointer** Results section "GRouNdGAN generates realistic scRNA-seq data", Tables 1–3.
    - **Concern** The comparison with baseline simulators is limited. For PBMC-CTL, SERGIO results are excluded due to user-dependent quality, which is reasonable, but the comparison set is small. More importantly, the metrics used (cosine distance, Euclidean distance, MMD, RF AUROC, miLISI) are computed on a single train/test split, and no variability or statistical significance is reported. It is unclear whether the observed differences are robust across seeds or subsamples.
    - **Why it matters** Without measures of variability or statistical testing, the claim of "state-of-the-art" performance is not rigorously supported.
    - **Resolution test** The authors should report performance across multiple random seeds or bootstrap resamples, and provide confidence intervals or statistical tests for the differences between methods.
  - **R1-M3** (Severity: Major, Blocking: Yes, Axis: Technical soundness)
    - **Claim pointer** The authors claim that the labeler and anti-labeler ensure that the GRN is causally imposed and that the model does not ignore TF inputs.
    - **Evidence pointer** Methods section "Labeler and anti-labeler", Supplementary Notes, Supplementary Table 3.
    - **Concern** The ablation study is referenced but not fully described in the provided material. It is unclear how the labeler and anti-labeler losses are weighted relative to the adversarial loss, and whether the model is sensitive to these weights. Additionally, the claim that the anti-labeler prevents the generator from ignoring TF inputs is not directly tested; the knockout experiments show that TF perturbations affect targets, but this could also be achieved by the architectural constraint alone.
    - **Why it matters** The contribution of the labeler/anti-labeler is a key novelty of the method. Without a clear ablation demonstrating their necessity, the added complexity may not be justified.
    - **Resolution test** The authors should provide a detailed ablation study showing model performance and GRN imposition with and without the labeler/anti-labeler, and report sensitivity to loss weights.
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Reproducibility)
    - **Claim pointer** The authors claim that GRouNdGAN can be trained on a single GPU and that hyperparameters are consistent across datasets.
    - **Evidence pointer** Methods section "Training procedure and hyperparameter tuning", Supplementary Tables 1 and 2.
    - **Concern** The manuscript does not provide a clear statement on code availability, and the full hyperparameter details are only in supplementary tables. For a method intended for broad use, the lack of a public code repository or detailed implementation notes (e.g., framework, hardware, training time) limits reproducibility.
    - **Why it matters** Reproducibility is a core expectation for computational methods in Nature Communications.
    - **Resolution test** The authors should provide a public code repository with training scripts, configuration files, and a clear statement on hardware requirements and training time.
- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Clarity)
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Introduction.
    - **Issue** The term "causal" is used repeatedly without a clear definition of what causality means in this context. The authors should define "causal" early in the manuscript, distinguishing between structural causality (as encoded in the model) and biological causality.
    - **Required correction** Add a brief definition or clarification of "causal" in the Introduction.
  - **R1-m2** (Severity: Minor, Axis: Statistical reporting)
    - **Affected element** Results, Tables 1–3
    - **Evidence pointer** Tables 1–3.
    - **Issue** The tables report point estimates without any measure of uncertainty. For a fair comparison, variability across runs or subsamples should be reported.
    - **Required correction** Add standard deviations or confidence intervals to the tables, or state that results are from a single run and acknowledge this limitation.
  - **R1-m3** (Severity: Minor, Axis: Completeness)
    - **Affected element** Results, GRN reconstruction section
    - **Evidence pointer** Figure 3, Supplementary Figures 7–9.
    - **Issue** The GRN reconstruction analysis uses only a subset of inference methods and does not include a comparison with data simulated by other GRN-based simulators (e.g., SERGIO) under the same conditions.
    - **Required correction** Consider adding a comparison with SERGIO-simulated data for GRN reconstruction, or justify why this is not feasible.
  - **R1-m4** (Severity: Minor, Axis: Interpretation)
    - **Affected element** Discussion
    - **Evidence pointer** Discussion section.
    - **Issue** The discussion of limitations is brief. The authors mention the bipartite GRN assumption and the need for retraining on new datasets, but do not discuss potential failure modes, such as the impact of GRN density or the choice of TF set on model performance.
    - **Required correction** Expand the limitations paragraph to address these points.
  - **R1-m5** (Severity: Minor, Axis: Readability)
    - **Affected element** Methods, "Causal GRN preparation"
    - **Evidence pointer** Methods section.
    - **Issue** The description of how the input GRN is constructed from GRNBoost2 is clear, but the rationale for using 15 TFs per gene is not explained.
    - **Required correction** Add a sentence justifying the choice of 15 TFs.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (causal validity)
  - R1-M2 (evaluation rigor)
  - R1-M3 (technical soundness of labeler/anti-labeler)
- **Assessment against Nature-style criteria**
  - **Originality** High. The integration of causal GRN structure into a GAN for scRNA-seq simulation is a novel contribution that addresses a clear gap in existing simulators.
  - **Scientific importance** High. The ability to generate realistic scRNA-seq data with known ground-truth causal relationships has broad implications for benchmarking GRN inference and for in silico perturbation studies.
  - **Interdisciplinary readership** Moderate to high. The work bridges machine learning, causal inference, and single-cell biology, and should appeal to researchers in all three areas.
  - **Technical soundness** Moderate. The methodological design is sound, but the evaluation lacks statistical rigor, and the causal claims are stronger than what is demonstrated.
  - **Readability for nonspecialists** Moderate. The manuscript is generally well-written, but the causal terminology and some technical details may be challenging for readers without a background in causal inference or GANs.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are encouraging, but the causal claims need to be tempered or better supported, and the evaluation needs to be more rigorous.