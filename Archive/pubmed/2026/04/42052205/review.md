## Review setup
- **Input scope** Full manuscript text (Introduction, Methods, Results, Discussion sections) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no external data or supplementary materials were accessible for verification
- **Shared manuscript claim summary** The authors present an ensemble approach using two fine-tuned GPT-based foundation models (LLaMA-3 and GPT-4o mini) to predict transcriptional regulatory effects (activation, repression, regulation) between transcription factors and regulated elements from biomedical literature. They report F1-scores above 0.87 on test data, successful reconstruction of 80% of a curated Salmonella Typhimurium transcriptional regulatory network from 264 full-text articles, and application to a larger corpus of 2,278 publications to generate a novel network.
- **Visible evidence base** Tables 4-7 (performance metrics), Figures 1-5 (described in text), confusion matrices (Figure 2), network analyses (Figures 6-8), supplementary tables referenced but not provided
- **Missing materials affecting confidence** Supplementary Tables S1-S8, Supplementary Methods, actual figures, the curated Salmonella interaction dataset, the E. coli fine-tuning dataset, and the full predicted interaction list from the 2,278-article corpus were not available for independent verification

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely problem: automating the reconstruction of bacterial transcriptional regulatory networks from literature using modern large language models. The authors demonstrate that fine-tuned GPT-based models can classify regulatory effects with high accuracy on a held-out test set and that an ensemble approach improves precision over individual models. The application to a large corpus and the public release of the resulting network are valuable contributions. However, several methodological details are insufficiently described, the comparison with prior work is incomplete, and the gap between test-set performance and real-world reconstruction performance raises questions about generalizability that are only partially addressed. The statistical analysis is underpowered and the biological validation is largely anecdotal. The manuscript would benefit from clearer reporting of experimental design, more rigorous evaluation, and a more cautious interpretation of the network-level results.
- **Who would be interested in the results, and why** Researchers in systems biology, specifically those studying bacterial gene regulation, would find the reconstructed Salmonella network useful as a hypothesis-generating resource. Computational biologists working on biomedical text mining and relation extraction would be interested in the methodological comparison between GPT-based models and earlier BERT-based approaches. Curators of regulatory databases such as RegulonDB could benefit from the assisted-curation workflow described. The work may also appeal to the broader natural language processing community interested in domain-specific fine-tuning of foundation models.
- **Major strengths** The problem is well-motivated and practically important. The use of two different GPT-based architectures (open and closed) with a consistent fine-tuning protocol is a reasonable design. The ensemble approach is simple and effective, improving precision over individual models. The evaluation on a real curated dataset, rather than only on artificial benchmarks, is commendable. The public release of the reconstructed network and code is a significant contribution to the community. The error analysis of false positives is thoughtful and provides actionable insights for future improvements.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (insufficient dataset description), R1-M2 (incomplete baseline comparison), R1-M3 (inadequate statistical rigor), R1-M4 (limited biological validation)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of GPT-based foundation models to bacterial TRN reconstruction is novel, but the underlying task (relation extraction from biomedical literature) is well-established, and the methodological novelty over prior BERT-based work is incremental. **Scientific importance**: Moderate to high. The problem of incomplete TRNs is significant, and an automated pipeline that can accelerate curation has clear value. However, the demonstrated impact is limited to a single organism and the biological insights derived are not deeply explored. **Interdisciplinary readership**: The work bridges computational linguistics and microbiology, which could attract readers from both communities, but the presentation is somewhat technical and assumes familiarity with both NLP terminology and bacterial regulatory biology. **Technical soundness**: The core classification results appear sound, but several methodological details are under-specified (dataset construction, hyperparameter selection, statistical testing), and the network-level evaluation lacks rigorous validation. **Readability for nonspecialists**: The manuscript is generally readable but contains jargon from both fields without sufficient explanation. The flow from methods to results to discussion is logical, but the motivation for specific technical choices (e.g., why LLaMA-3 8B vs. 4B) is not always clear.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are encouraging, but the manuscript requires substantial revisions to clarify methodology, strengthen statistical analysis, and provide more rigorous biological validation before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim that fine-tuning with 1,562 sentences from E. coli literature enables accurate prediction of regulatory effects, and that the resulting models generalize to Salmonella literature.
- **Evidence pointer** Section "Data set for fine-tuning", Table 2
- **Concern** The description of the fine-tuning dataset is insufficient. The authors state that the dataset comprises 1,562 sentences from 119 articles and that categories follow RegulonDB conventions, but critical details are missing: (1) How were sentences selected? Was there a sampling strategy or were all sentences from the articles included? (2) What is the distribution of categories in the dataset? Table 2 is referenced but not shown in the provided text. (3) How were entity pairs constructed within each sentence? The authors mention that sentences were duplicated for each TF-regulated element pair, but the total number of training instances (after duplication) is not stated. (4) What was the inter-annotator agreement, if any, for the curation process? (5) The authors mention that the dataset was obtained from a "real curation workflow" but do not specify whether the curation was performed specifically for this study or repurposed from existing database curation efforts. Without this information, it is difficult to assess potential biases in the training data and the generalizability of the fine-tuned models.
- **Why it matters** The quality and composition of the training data directly determine the models' performance and generalizability. If the dataset is small, imbalanced, or contains systematic biases (e.g., overrepresentation of certain regulatory mechanisms or gene families), the reported F1-scores may not reflect real-world performance on diverse literature.
- **Resolution test** Provide a detailed description of the dataset construction process, including sentence selection criteria, category distribution, number of training instances after entity pairing, and any quality control measures. If possible, report inter-annotator agreement statistics. Additionally, discuss potential biases in the dataset and how they might affect generalization to other bacterial species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim that their approach "overtook the performance of prior works predicting the effect of the interaction" and that the ensemble approach outperforms individual models.
- **Evidence pointer** Section "Performance of TRN reconstruction", Table 7
- **Concern** The comparison with prior work is incomplete and potentially misleading. The authors compare their results with Varela-Vega et al. (2024) and Gill et al. (2024), but the comparison is not apples-to-apples. Specifically: (1) The authors use a different dataset (Salmonella full-text articles) than the prior work (which may have used different corpora or evaluation protocols). (2) The authors report F1-scores for TRN reconstruction, but the prior work may have used different evaluation metrics or granularity (e.g., sentence-level vs. document-level). (3) The authors do not report confidence intervals or statistical significance for the performance differences, making it unclear whether the improvements are meaningful. (4) The comparison with Gill et al. (2024) is acknowledged as not directly comparable, but the authors still use it to argue for the superiority of their approach. A more rigorous comparison would involve running the prior methods on the same evaluation dataset or using a standardized benchmark.
- **Why it matters** The claim of outperforming prior work is central to the manuscript's contribution. If the comparison is not fair or statistically grounded, the claim is weakened and the practical value of the approach is less clear.
- **Resolution test** Provide a more rigorous comparison with prior work, ideally by re-implementing or obtaining the prior methods and evaluating them on the same Salmonella dataset. Report confidence intervals for all performance metrics and perform statistical significance testing (e.g., bootstrap or McNemar's test, which is already used but should be applied to all comparisons). If re-implementation is not feasible, clearly state the limitations of the comparison and avoid strong claims of superiority.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report F1-scores, precision, and recall for the fine-tuned models and the ensemble approach, and use McNemar's test to compare models.
- **Evidence pointer** Section "Performance of TRN reconstruction", Table 7, Supplementary Table S2
- **Concern** The statistical analysis is underpowered and incomplete. (1) The McNemar's test is applied to compare models on the set of curated interactions, but the authors do not report the full 2x2 contingency tables for all pairwise comparisons, only summarizing discordant counts in Supplementary Table S2 (not provided). (2) The test is applied at the level of unique interactions, but the authors do not account for the fact that interactions are derived from sentences, and multiple sentences may refer to the same interaction. This could introduce dependencies that violate the assumptions of McNemar's test. (3) The authors report that the ensemble approach is significantly different from BERT, but the direction of the difference (c > b) indicates that BERT recovers more true interactions. The authors interpret this as the ensemble being conservative, but this interpretation is post hoc and not supported by a pre-specified hypothesis. (4) No correction for multiple testing is applied despite multiple pairwise comparisons being performed. (5) The authors do not report confidence intervals for the F1-scores, precision, or recall, making it difficult to assess the precision of the estimates.
- **Why it matters** The statistical analysis is crucial for determining whether the observed performance differences are meaningful or due to chance. Inadequate statistical rigor undermines the confidence in the reported results and the conclusions drawn from them.
- **Resolution test** Provide full contingency tables for all pairwise comparisons, apply appropriate corrections for multiple testing, and account for potential dependencies in the data (e.g., by clustering at the article or sentence level). Report confidence intervals for all performance metrics. If the sample size is limited, consider using bootstrap or permutation-based methods to assess the stability of the results.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim that the reconstructed Salmonella TRN from 2,278 articles "aligns with biological knowledge" and demonstrate this through network analyses and over-representation analyses.
- **Evidence pointer** Section "Application of the approach", Figures 6-8, Supplementary Tables S4-S6
- **Concern** The biological validation of the reconstructed network is largely anecdotal and lacks quantitative rigor. (1) The authors highlight a few known regulatory relationships (e.g., PhoP, RpoS, H-NS) but do not provide a systematic comparison of the reconstructed network against known regulatory interactions from databases such as RegulonDB or SalmoNet2. (2) The over-representation analyses are described qualitatively, with only a few examples given. The full results are in supplementary tables that were not provided, making it impossible to assess the statistical significance and effect sizes. (3) The network metrics (degree, etc.) are reported for a few nodes, but no comparison is made to random networks or to networks reconstructed by alternative methods. (4) The authors acknowledge that some predicted interactions are false positives (e.g., marA and tolC in the PhoP subnetwork), but they do not quantify the overall error rate at the network level or discuss how these errors might affect downstream analyses. (5) The claim that the network "integrates existing biological knowledge" is not supported by a systematic enrichment analysis against known regulatory pathways or gene ontology terms.
- **Why it matters** The biological relevance of the reconstructed network is a key claim of the manuscript. Without rigorous validation, it is unclear whether the network is a reliable resource for hypothesis generation or whether it contains too many errors to be useful.
- **Resolution test** Perform a systematic comparison of the reconstructed network against known regulatory interactions from curated databases, reporting precision and recall at the network level. Conduct enrichment analyses against known biological pathways and gene ontology terms, with appropriate statistical corrections. Compare network properties (e.g., degree distribution, clustering coefficient) against random networks or networks from prior methods. Quantify the impact of false positives on downstream analyses and discuss strategies to mitigate them.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Data set for fine-tuning"
- **Evidence pointer** Table 1
- **Issue** The authors reference Table 1 with examples of annotated sentences, but the table is not shown in the provided text. The examples described in the text (e.g., "melR gene is repressed by the MelR TF") are helpful but insufficient to understand the full annotation scheme.
- **Required correction** Include Table 1 in the main text or provide a more detailed description of the annotation format, including how entity boundaries are marked and how the "regulator" category is distinguished from "activator" and "repressor."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "GPT-based foundation models"
- **Evidence pointer** Section "LLaMA-3 8B and 4B (4-bit LoRA)"
- **Issue** The authors state that LLaMA-3 8B outperforms its 3B version, but the 3B version is not mentioned elsewhere in the text. It is unclear whether the 3B model was evaluated in this study or if this is a reference to external results.
- **Required correction** Clarify whether the 3B model was part of this study and, if so, report its performance. If not, remove the comparison or clearly state that it refers to external findings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Performance of TRN reconstruction"
- **Evidence pointer** Table 7
- **Issue** The authors report that the ensemble approach achieved an F1-score of 0.645, but they do not report the precision and recall for the ensemble approach separately. Given that the ensemble is a consensus of two models, it would be informative to know how the precision-recall trade-off changes compared to individual models.
- **Required correction** Report precision and recall for the ensemble approach alongside the F1-score, and discuss the trade-off in the context of the application.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section "Application of the approach"
- **Evidence pointer** Figure 5
- **Issue** The authors state that the model agreement was "very high" for the 2,278-article corpus, but the exact agreement rate is not reported. Without this number, it is difficult to assess the reliability of the consensus approach on a larger and potentially more diverse corpus.
- **Required correction** Report the exact agreement rate between the two models on the 2,278-article corpus, and discuss any differences in agreement across article types (e.g., full-text vs. abstract-only).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Discussion"
- **Evidence pointer** Section "Novelty of the study"
- **Issue** The discussion of prior work is somewhat disjointed, moving from rule-based approaches to classical machine learning to foundation models without a clear synthesis of how the current work fits into the broader landscape. The comparison with Gill et al. (2024) is acknowledged as not directly comparable, but the discussion could be more structured.
- **Required correction** Reorganize the discussion to clearly delineate the contributions of this work relative to prior approaches, highlighting both the similarities and the key differences (e.g., the use of GPT-based models, the prediction of regulatory effect, the ensemble strategy).

## Risk / unsupported claims
- The claim that the approach "overtook the performance of prior works" is not fully supported due to incomplete and non-standardized comparisons with prior methods.
- The claim that the reconstructed network "aligns with biological knowledge" is based on anecdotal examples and lacks systematic quantitative validation.
- The claim that the models generalize to other bacterial species is speculative, as only E. coli and Salmonella were tested, and the authors acknowledge that dictionaries are required for new species.
- The reported F1-scores on the test set (0.87) may not reflect real-world performance on full-text articles, as the gap between test-set performance and TRN reconstruction performance (F1 = 0.645) is substantial and only partially explained.
- The use of McNemar's test for comparing models on the curated interaction set is appropriate, but the interpretation of the results is limited by the lack of full contingency tables and the potential for dependencies in the data.
- The statement that "the gap is due to the fine-tuned models dealing with sentences from full-text articles with expression ways that were not present in training data" is a hypothesis that is not directly tested; alternative explanations (e.g., domain shift, annotation inconsistencies) are not ruled out.