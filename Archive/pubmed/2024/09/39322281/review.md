## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods, supplemental material references)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and significance of the reported findings
- **Shared manuscript claim summary** The authors present regLM, a framework combining autoregressive language models (HyenaDNA) with supervised sequence-to-function models to generate synthetic cis-regulatory elements (CREs) with desired activity levels. They demonstrate generation of yeast promoters with varying strengths and cell type–specific human enhancers, and provide evidence that generated sequences resemble native regulatory DNA in sequence content and regulatory syntax.
- **Visible evidence base** Main text figures (Fig. 1, 2, 3), supplemental figures (S1–S30), supplemental tables (S1–S10), methods section, and software availability statements
- **Missing materials affecting confidence** Full supplemental methods, complete figure legends, exact hyperparameter settings for all models, benchmark implementation details, and raw data files were not available for review

## Reviewer
- **Overall assessment** This manuscript presents a timely and potentially valuable contribution to the field of regulatory DNA design. The regLM framework is clearly described and the authors provide a comprehensive evaluation strategy that goes beyond simple predictive accuracy. The yeast promoter results are particularly well supported, with multiple complementary analyses demonstrating that generated sequences capture native regulatory syntax. The human enhancer results are promising but rely more heavily on in silico predictions from models that may share biases with the generative model. The manuscript is generally well written and accessible, though some methodological details require clarification. The work is likely to interest researchers in synthetic biology, gene therapy, and computational genomics, but the current evidence does not fully establish that the generated human enhancers will function as predicted in vivo.

- **Who would be interested in the results, and why** Researchers in synthetic biology and biomanufacturing will be interested in the ability to generate promoters with tunable activity levels. The gene therapy community may find value in the cell type–specific enhancer generation capability. Computational biologists working on regulatory genomics will be interested in the interpretability analyses demonstrating that the language model has learned meaningful cis-regulatory syntax. The framework's generalizability across species (yeast and human) suggests broad applicability.

- **Major strengths**
  1. The framework is conceptually elegant, combining the generative power of autoregressive language models with the filtering capability of supervised predictors.
  2. The evaluation strategy is thorough, using multiple independent metrics (k-mer content, motif abundance, motif syntax, ISM, independent regression models) to assess realism.
  3. The comparison against five alternative design methods provides useful context for the field.
  4. The interpretability analyses (log-likelihood ratios, motif association with activity classes) provide mechanistic insight into what the model has learned.
  5. The authors are appropriately cautious in their claims, particularly regarding the human enhancer results.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that regLM-generated human enhancers have cell type–specific activity based on predictions from independent models.
- **Evidence pointer** Figure 3B, 3F–I; Supplemental Figures S21, S26–S29
- **Concern** The validation of human enhancer specificity relies entirely on in silico predictions from models that may share architectural or training biases with the regLM framework. The independent regression models are described as "trained on separate data" but are based on the same Enformer architecture and may have learned similar representations. The claim that generated enhancers "would have cell type–specific activity" is not supported by any experimental validation. While the authors acknowledge this limitation in the discussion, the strength of the claims in the results section exceeds what the evidence supports.
- **Why it matters** The central value proposition of this work is the ability to generate functional regulatory DNA. Without experimental validation, particularly for the human enhancers, the field cannot assess whether the in silico predictions translate to actual biological function. This is especially important given that the authors note the test set contains very few enhancers with the level of specificity they aim to generate, making it difficult to assess whether the model has truly learned the relevant regulatory grammar or is exploiting artifacts.
- **Resolution test** Provide experimental validation of at least a subset of the generated human enhancers (e.g., reporter assays in the relevant cell lines). Alternatively, substantially temper the claims about human enhancer functionality and clearly frame these as predictions requiring experimental confirmation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that regLM-generated yeast promoters are more realistic than those generated by five alternative methods based on multiple sequence-level metrics.
- **Evidence pointer** Figure 2F–I; Supplemental Tables S4, S5
- **Concern** The comparison against alternative methods may be confounded by the choice of hyperparameters and implementation details for the baselines. The authors state that all five model-guided methods were performed "using the regression model trained on the same data set as regLM as an oracle," but the specific implementation details (e.g., number of optimization steps, population sizes, mutation rates for directed evolution) are not provided in the main text. If the baselines were not given sufficient optimization budget or appropriate hyperparameters, the comparison may be unfair.
- **Why it matters** The claim that regLM outperforms existing methods is a key contribution of the paper. If the baselines are not optimally configured, the comparison does not accurately reflect the state of the art, and the field cannot assess whether regLM represents a genuine advance or an artifact of the evaluation setup.
- **Resolution test** Provide full implementation details for all baseline methods, including hyperparameter settings and optimization budgets. Consider performing sensitivity analyses to show that results are robust to reasonable variations in baseline configurations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that regLM "facilitates the design of realistic regulatory DNA elements while providing insights into the cis-regulatory code."
- **Evidence pointer** Figure 2J; Supplemental Figures S17, S30
- **Concern** The claim about providing insights into the cis-regulatory code is only weakly supported. The log-likelihood ratio analysis (Figure 2J) demonstrates that the model has learned to associate known activating and repressing motifs with appropriate activity classes, but this is largely confirmatory of existing knowledge rather than providing new insights. The authors do not identify novel motifs, new regulatory syntax rules, or unexpected relationships that would constitute genuine insight into the cis-regulatory code.
- **Why it matters** The stated contribution of providing insights into the cis-regulatory code is a significant part of the paper's framing. If the framework only recapitulates known regulatory biology, the scientific contribution is primarily methodological rather than biological. This distinction matters for assessing the paper's significance to the broader genomics community.
- **Resolution test** Either provide concrete examples of novel regulatory insights derived from the model (e.g., previously unknown motif combinations, spacing constraints, or cell type–specific syntax) or revise the claims to accurately reflect that the framework confirms known regulatory principles rather than revealing new ones.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The schematic in Figure 1 is described in the text but the figure itself is not available for review. Based on the text description, the figure appears to be a multi-panel overview of the regLM framework, but the specific components and workflow are not fully clear from the text alone.
- **Required correction** Ensure that Figure 1 provides a clear, self-contained overview of the framework that can be understood without reference to the methods section. Consider adding a simplified schematic of the overall workflow in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "Training regLM models"
- **Evidence pointer** Methods section, "Training regLM models"
- **Issue** The methods state that the yeast model was trained for 100 epochs and the human model for 16 epochs, but do not provide details on training time, computational resources, or convergence criteria. The choice of 16 epochs for the human model seems arbitrary and may not be sufficient for convergence.
- **Required correction** Provide additional details on training duration, convergence monitoring, and rationale for the chosen number of epochs. If early stopping was used, describe the criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "Generating synthetic CREs using regLM"
- **Evidence pointer** Methods section, "Generating synthetic CREs using regLM"
- **Issue** The authors use nucleus sampling for yeast promoter generation and beam search for human enhancer generation, but do not justify this difference in decoding strategy. The choice of decoding method can significantly affect the diversity and quality of generated sequences.
- **Required correction** Explain the rationale for using different decoding strategies for the two species, or use a consistent approach. If the choice was based on empirical performance, describe the comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of potential applications in gene therapy and biomanufacturing is brief and does not address practical considerations such as delivery methods, safety concerns, or regulatory pathways for synthetic regulatory elements.
- **Required correction** Consider expanding the discussion of practical applications to address these considerations, or explicitly state that such considerations are beyond the scope of the current work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "In silico evaluation of synthetic CREs"
- **Evidence pointer** Methods section, "In silico evaluation of synthetic CREs"
- **Issue** The k-mer analysis uses 4-mers, which may not capture longer-range regulatory syntax. The choice of k-mer length is not justified.
- **Required correction** Justify the choice of k-mer length or include analyses with additional k-mer lengths to demonstrate robustness.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of experimental validation for human enhancer specificity claims
  - R1-M2: Insufficient detail on baseline method implementations for fair comparison
  - R1-M3: Overstated claims about insights into the cis-regulatory code

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its application of autoregressive language models to regulatory DNA design. While language models have been applied to genomic sequences before, the specific framing of using prompt tokens to condition generation on desired activity levels is novel. The combination with supervised models as filters is also a reasonable and somewhat novel approach.
  - **Scientific importance**: The ability to design functional regulatory elements with specified properties has clear importance for synthetic biology and therapeutic applications. However, the current evidence does not fully establish that the generated elements will function as predicted in vivo, which limits the immediate scientific impact. The yeast results are more convincing than the human results.
  - **Interdisciplinary readership**: The work bridges computational biology, synthetic biology, and genomics. The framework is likely to be of interest to researchers in all three fields. The writing is generally accessible, though some sections assume familiarity with language model architectures.
  - **Technical soundness**: The methodology is generally sound, with appropriate use of multiple evaluation metrics and independent validation models. However, the lack of experimental validation for human enhancers and insufficient detail on baseline implementations are significant gaps. The statistical analyses appear appropriate, though exact test details are not always provided.
  - **Readability for nonspecialists**: The manuscript is well organized and the main concepts are explained clearly. The figures appear to be well designed based on the text descriptions, though they were not available for review. Some methods sections may be challenging for readers without a computational background.

- **Recommendation posture** Supportive if technical concerns are resolved. The framework is promising and the yeast promoter results are well supported. However, the human enhancer claims require either experimental validation or substantial tempering. The comparison against baseline methods needs more detail to be fully convincing. If these concerns are addressed, this work would be a valuable contribution to the field of regulatory DNA design.