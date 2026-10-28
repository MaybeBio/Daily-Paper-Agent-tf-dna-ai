## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary notes) as provided
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence presented; no editorial or formatting review
- **Shared manuscript claim summary** The authors present Qimai, a multi-agent framework combining a transformer-based DNA-protein interaction (DPI) model with LLM-based reasoning over direct and indirect motif evidence, to improve prediction generalization to unseen proteins. They report consistent performance gains over standalone deep learning models on internal and external benchmarks, with ablation studies attributing gains to LLM reasoning and indirect evidence.
- **Visible evidence base** Abstract; Introduction; Results sections (Qimai Framework, DPI model performance, Qimai internal cross-validation, external validation, LLM vs LightGBM comparison, case studies); Online Methods (Data, DPI Model, Implementation, Benchmarking, Evaluation and Ablation Setup); Supplementary Notes A–E; Supplementary Tables referenced (Tables 1–13); Supplementary Figures referenced (S1–S7)
- **Missing materials affecting confidence** Full figure panels (main text Figures 1 and 2) not visible; Supplementary Tables 1–13 and Supplementary Figures S1–S7 not provided; exact hyperparameter values for DPI model training not fully specified; details of LLM prompt engineering not fully disclosed; statistical significance testing for performance differences not reported; code repository not inspected

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting framework that combines deep learning predictions with LLM-based reasoning over biological motif evidence, targeting a real and important problem: generalization to unseen proteins in DNA-protein interaction prediction. The reported performance gains on unseen proteins are substantial and the ablation analyses are thoughtfully designed. However, the evidence as presented is incomplete in several critical respects. The main figures and supplementary materials are not available for inspection, which limits verification of the claims. The comparison against LightGBM, while useful, does not fully isolate the contribution of the LLM reasoning mechanism. The lack of statistical significance testing and the absence of detailed error analysis are notable gaps. The claim that Qimai establishes a "generalizable and interpretable paradigm" is plausible but not fully supported by the evidence provided in this version of the manuscript.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, transcription factor binding prediction, and protein-DNA interaction modeling would be the primary audience. Researchers developing AI agents or LLM-based frameworks for scientific discovery would also find the methodological approach of interest. The framework's emphasis on interpretability and generalization to novel proteins addresses a known limitation in the field, making the results potentially impactful for those developing predictive models for understudied or newly discovered transcription factors.
- **Major strengths**
  1. The problem addressed is important and timely: generalization to unseen proteins is a recognized limitation of current deep learning models in regulatory genomics.
  2. The framework design is modular and conceptually clear, separating evidence gathering from evidence synthesis, which is a sensible architectural choice.
  3. The inclusion of indirect motif evidence via protein-protein interaction partners is biologically motivated and addresses a real gap in existing models.
  4. The ablation studies are well-structured and attempt to isolate the contribution of each component.
  5. The use of multiple LLMs and the demonstration that open-source models perform comparably strengthens the generalizability of the framework.
  6. The case studies provide concrete examples of the framework's reasoning process, which is valuable for assessing interpretability claims.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that Qimai "consistently outperforms standalone deep learning models across all metrics" on the external benchmark of 78 unseen proteins, with specific improvements in AUC-PR, AUC-ROC, and MCC.
- **Evidence pointer** Results section "Qimai Achieves Superior Generalization on Novel Proteins in external dataset"; Figure 2A; Supplementary Table 7
- **Concern** The main figures (Figure 1 and Figure 2) and all supplementary tables and figures are referenced but not provided in the submitted material. Without access to these data, the central performance claims cannot be independently verified. The reported numbers in the text are not accompanied by confidence intervals, standard errors, or statistical significance tests. It is unclear whether the observed improvements are statistically robust or could arise from a single favorable data split.
- **Why it matters** The central claim of the manuscript is that Qimai outperforms existing methods on unseen proteins. If the supporting data are not available for scrutiny, the claim cannot be evaluated. Statistical rigor is essential for claims of performance improvement, particularly when the improvements are reported as percentages that could be sensitive to small sample sizes.
- **Resolution test** Provide the main figures and all supplementary tables with full numerical results. Include confidence intervals or standard deviations for all reported metrics. Perform and report statistical significance testing (e.g., paired bootstrap or McNemar's test) for the key comparisons between Qimai and standalone models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The manuscript claims that the LLM's "context-aware reasoning" is superior to a fixed-weight classifier (LightGBM) for integrating evidence, with a 221% relative improvement in MCC.
- **Evidence pointer** Results section "LLM Agent Outperforms a state-of-the-art Classifier through Context-aware Reasoning"; Figure 2C; Supplementary Table 10
- **Concern** The comparison between the LLM agent and LightGBM is described, but the experimental setup is not fully specified. The LightGBM was trained on 10,000 protein-DNA pairs with 16 features, but the feature set includes "Deep Learning Model Predictions" which are derived from the same DPI model used in the Qimai framework. It is unclear whether the LightGBM was given access to the same evidence in the same format, and whether the LLM had access to additional information (e.g., free-text biological knowledge) that LightGBM could not use. The claim that the LLM's advantage stems from "context-aware reasoning" requires a more controlled comparison where the only difference is the reasoning mechanism, not the information available.
- **Why it matters** The claim that LLM reasoning is superior to classical machine learning for evidence integration is a strong claim with implications for the field. If the comparison is not fair or the experimental setup is confounded, the conclusion may not be valid.
- **Resolution test** Provide a detailed description of the exact features and information provided to both the LLM and LightGBM. Ensure that both models receive identical evidence inputs. Consider additional baselines, such as a logistic regression or a simple rule-based system, to better isolate the contribution of the LLM's reasoning. Report the performance of LightGBM with different hyperparameter settings to ensure the comparison is not biased by suboptimal baseline tuning.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The manuscript claims that the DPI model's attention weights highlight regions overlapping with annotated DNA-binding domains, with 32 out of 34 proteins showing at least 50% overlap.
- **Evidence pointer** Results section "The new transformer DPI model achieves superior performance"; Supplementary Figure 1C
- **Concern** The interpretation of attention weights as evidence of biological relevance is methodologically fragile. Attention weights are known to be sensitive to training dynamics and do not necessarily correspond to functional importance. The comparison with annotated DBDs is a useful sanity check, but the threshold of 50% overlap is arbitrary, and no statistical significance is reported. It is unclear whether this overlap is significantly higher than what would be expected by chance, particularly given that DBDs can be large and attention weights are diffuse.
- **Why it matters** The claim that the model has learned biologically meaningful representations is used to support the interpretability of the framework. If the attention analysis is not statistically rigorous, the interpretability claim is weakened.
- **Resolution test** Perform a permutation test or a comparison against randomly selected regions of the protein to establish that the overlap with DBDs is significantly higher than chance. Report the distribution of overlap percentages across all proteins, not just the 34 with annotated DBDs. Consider using more rigorous interpretability methods, such as attribution techniques or probing tasks, to complement the attention analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The manuscript claims that Qimai's performance gains are "driven by the LLM's ability to dynamically weigh diverse evidence," with indirect evidence particularly critical for unseen proteins.
- **Evidence pointer** Results section "Qimai Achieves Robust Performance on Internal Cross-Validation"; Ablation studies; Supplementary Figure S4B
- **Concern** The ablation studies are described, but the specific results are not fully reported in the text. The claim that indirect evidence is "particularly critical" for unseen proteins is supported by the comparison between "Qimai (w/o indirect)" and the full system, but the magnitude of the effect and its consistency across the five internal splits are not reported. Additionally, the definition of "novel" proteins (sequence identity < 30%) is reasonable but may not capture all forms of novelty relevant to the problem.
- **Why it matters** The claim about the importance of indirect evidence is central to the biological contribution of the work. If the effect is small or inconsistent, the conclusion may not be robust.
- **Resolution test** Report the full ablation results for each of the five internal splits, including the performance of all ablated configurations on all metrics. Provide a more detailed analysis of the types of proteins for which indirect evidence is most helpful. Consider additional definitions of novelty (e.g., based on protein family or domain composition) to test the robustness of the findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "zero-shot DNA-protein interaction prediction" in the title and abstract is not clearly defined in the text. The term "zero-shot" typically implies the model has never seen the protein during training, but the manuscript also uses "unseen" and "novel" to describe proteins. The relationship between these terms should be clarified.
- **Required correction** Define "zero-shot" explicitly in the introduction and explain how it relates to the "unseen" and "novel" protein definitions used in the evaluation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, DPI Model
- **Evidence pointer** Online Methods, "DPI Model" section
- **Issue** The description of the DPI model architecture is incomplete. The manuscript states that it is "adapted from the original Transformer architecture" but does not specify the number of layers, heads, hidden dimensions, or other key hyperparameters. The training details (learning rate, batch size, number of epochs) are also not fully specified.
- **Required correction** Provide a complete description of the model architecture and training hyperparameters, either in the main text or in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Evaluation and Ablation Setup
- **Evidence pointer** Online Methods, "Evaluation and Ablation Setup" section
- **Issue** The manuscript states that the external validation was "repeated 10 times using 10 different random seeds," but the internal cross-validation is described as "five random train/test splits." It is unclear whether the internal splits were also repeated with different seeds, and how the results were aggregated across splits.
- **Required correction** Clarify the exact evaluation protocol for both internal and external validation, including how results were averaged and whether standard deviations were computed across splits or seeds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code availability
- **Evidence pointer** Code availability section
- **Issue** The code repository is mentioned, but it is not clear whether the data used in the study (e.g., the Encode3and4 and ChIP_690 datasets) are publicly available or how to access them.
- **Required correction** Provide a data availability statement specifying where the datasets can be accessed, or state clearly if they are available upon request.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, all sections
- **Evidence pointer** Results sections; Figure 1C, 1D, 2A–2D
- **Issue** The manuscript reports performance metrics without any measure of uncertainty. Given the relatively small number of held-out proteins (44 per split internally, 78 externally), confidence intervals or standard errors are essential for interpreting the results.
- **Required correction** Report standard deviations or confidence intervals for all key metrics, and consider adding statistical tests for the main comparisons.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Related work
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraphs 1–2
- **Issue** The introduction cites several deep learning models for TF binding prediction but does not discuss recent work on zero-shot or few-shot learning for protein-DNA interactions, nor does it discuss the growing literature on LLM-based agents for biological prediction tasks.
- **Required correction** Add a brief discussion of related work on zero-shot prediction and LLM-based approaches in genomics to better contextualize the contribution.

## Risk / unsupported claims
- The claim that Qimai "establishes a generalizable and interpretable paradigm" is not fully supported by the evidence provided, as the generalizability is demonstrated on only two datasets and the interpretability is assessed only through case studies and attention analysis.
- The claim that the DPI model's attention weights "have encoded protein binding information" is not statistically validated and may overstate the biological interpretability of the model.
- The claim that the LLM's "context-aware reasoning" is the cause of performance gains over LightGBM is not fully established, as the comparison may be confounded by differences in information access or baseline tuning.
- The performance improvements reported in the abstract (17.6%, 15.6%, 244%) are presented without confidence intervals or significance testing, making it impossible to assess their robustness.
- The manuscript claims that Qimai "consistently outperforms" standalone models, but the consistency across the five internal splits is not reported in detail, and the external validation is based on a single dataset.