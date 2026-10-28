## Position: Genomic Model Research Must Move Beyond Anecdotal Evaluation of Interpretability Methods

Advances in machine learning and computational power have unlocked the predictive potential of the human genome, yet biologists now demand that these models also elucidate the underlying biological mechanisms. While interpretable machine learning (IML) techniques have been increasingly applied to bridge this gap, there has been a pervasive reliance on anecdotal validation: the vast majority of research relies on a single IML method and reports only isolated successful instances. Through a benchmarking study on transcription factor binding, we demonstrate the risks of current practices. We show that different IML methods can often (1) yield contradictory explanations for the same predictions, (2) fail to localize known regulatory motifs, and (3) fail to faithfully reflect the model’s internal decision process. In light of this, we argue for a validation framework analogous to clinical trials: just as trials require rigorous design and adverse-event reporting, genomic interpretability must move beyond cherry-picked plausibility toward systematic assessment of consistency, faithfulness, and biological validity. To facilitate this, we propose a tiered framework to guide rigorous evaluation and reporting of genomic IML methods.


## 1 Introduction

Understanding the language of the genome, i.e., how sequence variations shape molecular phenotypes, is a long-standing goal in functional genomics, underpinning applications from prioritizing non-coding variants in human genetics ( 4 ; 53 ) , to rational design in synthetic biology ( 48 ) , and uncovering disease mechanisms for therapeutic target discovery ( 18 ) . To this end, numerous deep learning approaches have proliferated ( 56 ; 15 ; 6 ; 12 ; 51 ; 25 ) . With the integration of high-throughput functional assays ( 36 ; 17 ) and burgeoning computational power, these deep neural networks (DNNs) have enabled potent predictive power across various genomic task, such as gene expression ( 4 ; 53 ) , transcription factor (TF) binding ( 5 ; 3 ; 54 ) , enhancer-promoter activity ( 14 ) among many others.

However, the predictive success of these models has not been matched by a commensurate understanding of their inner workings. Because of their intrinsic complexity (e.g., by featuring millions to billions of parameters), such DNNs are often perceived as a “black box”, with no explanation about how a given prediction was made or what biological mechanisms were learned. To address this challenge, a variety of post hoc interpretability methods have been employed for elucidating the predictions of genomic DNNs ( 38 ; 11 ) .

The most prevalent are feature attribution methods such as Saliency Maps ( 46 ) , DeepLIFT ( 45 ) , ISM ( 54 ) , and Integrated Gradients ( 47 ; 35 ) , which quantify the position-specific effect of sequence variations on model predictions. Beyond such main effects, interaction-based methods like integrated Hessians ( 28 ) , SQUID ( 44 ) , and DFIM ( 22 ) probe the epistatic interactions between mutations, while attention-based interpretation ( 49 ) and sparse autoencoders (SAEs) ( 9 ; 13 ; 10 ) instead examine the internal computations of transformer-based genomic models. Collectively, these techniques have enabled applications ranging from motif discovery and mechanistic understanding to de novo design and variant prioritization ( 5 ; 3 ; 14 ; 4 ) .

Despite this success, the lack of consensus on how to rigorously evaluate and report interpretability results in genomics is a significant concern. To quantify this gap, we conducted a large-scale mapping study of 3,575 3,575 papers employing Interpretable Machine Learning (IML) in genomics between 2010 and 2025. We found that the vast majority of studies: (1) relied on a single IML method without justification; (2) validated interpretations through heterogeneous and often subjective means; and (3) reported only “successful” cases while omitting failures (Section 2 ).

Furthermore, through a systematic benchmarking study on transcription factor binding prediction, we demonstrate that these practices have tangible consequences. We show that: (a) different IML methods produce drastically inconsistent explanations; (b) these explanations often fail to reflect the model’s actual decision-making process; and (c) results frequently misalign with known biological mechanisms—yielding near-zero recovery of true binding sites on challenging tasks, even when cherry-picking “successful” examples remains easy (Section 3 ).

Because rigorous evaluation is the cornerstone of scientific progress, we argue that genomics researchers must move beyond anecdotal evidence and systematically evaluate IML methods before relying on their outputs.


## 2 Mapping of Existing Practices

To establish a broad understanding of the existing practices in the evaluation and reporting of IML in genomics, we conducted a comprehensive, data-driven mapping study.


## 2.1 Methods

We first searched on the Web of Science (WoS) database 1 1 1 We use the WoS database because it offers the most comprehensive coverage of literature with highly curated metadata. for papers that explicitly mentioned the use of IML methods in genomics by applying the following search query. We applied this query to paper abstracts to optimize the trade-off between coverage and relevance.

This search led to 3,575 3,575 papers published between 2010 and 2025. Full-text articles were accessed through a combination of institutional subscriptions, open-access repositories, and preprint servers where available. As this amount of papers is too large for manual review, inspired by 26 , we prompted a gemini-3-flash-preview model (to balance costs and accuracy) to extract structured information from each full-text article. Specifically, for each paper, we extracted:

Types and number of IML methods employed.

Any justifications associated with this choice?

Types of validation for IML performed (e.g., visual inspection, querying domain-specific databases, or via wet-lab experiments?)

Number of “ successful ” instances, defined as cases the authors claim an IML output aligns with established domain knowledge (e.g., an attribution highlighting a known TF binding motif, or identified marker genes matching known cell types).

Any report on failed instances and their analysis?

To maximize extraction quality, we employed few-shot in-context learning (ICL) anchored by 10 10 manually curated demonstrations with self-reflection prompts to avoid hallucinations (see Appendix A for details). We also randomly sampled 100 100 papers, and one of the authors manually verified the model outputs, which yielded an overall agreement rate of 98 % 98\% (see Table 2 in Appendix B for the per-category breakdown).

Our analysis reveals several concerning patterns in how IML methods are evaluated and reported in genomics research. First, the vast majority of studies ( 86 % 86\% ) employed only a single IML method (Fig. 1 a), with no comparison against alternative interpretation techniques, nor justifications on why the chosen approach is more appropriate in this case. This lack of cross-method validation makes it difficult to assess the robustness or reliability of the reported interpretations.

Second, and perhaps most concerning, we observed substantial heterogeneity in validation practices (Fig. 1 b). Strikingly, nearly half of the studies relied on subjective visual inspection (e.g., whether highlighted regions correspond to known structural contacts). The remaining studies largely relied on indirect proxies like ChIP-seq peaks or simplified synthetic datasets, while only 2.81 % 2.81\% conducted wet-lab experiments to validate insights.

Third, the majority of papers reported only 1 1 – 3 3 “ successful ” instances where IML outputs aligned with known biology (Fig. 1 c), which raises concerns about cherry-picking. Furthermore, these papers typically did not disclose whether additional instances were examined, nor whether any interpretations failed to align with expectations (Fig. 1 d).

Such anecdotal evidence presents a problematic foundation for assessing IML capabilities. The selective reporting of favorable cases risks overstating the reliability of these methods, potentially fostering unwarranted confidence among practitioners. In high-stakes genomics applications—where experimental validation can be prohibitively expensive—over-reliance on inadequately evaluated IML methods could lead to substantial misallocation of resources and, more critically, erroneous biological conclusions.


## 3 Consequences of Current Practices: An Empirical Audit

The mapping study above reveals that evaluation in genomic IML relies heavily on anecdotal evidence. To move beyond abstract critique and concretely demonstrate the risks of these practices, we conduct a targeted empirical audit. We design a controlled case study to illustrate three specific failure modes that arise when rigorous validation is neglected: (1) Inconsistency , where methods yield contradictory explanations; (2) Unfaithfulness , where explanations decouple from model logic; and (3) Biological Misalignment , where “plausible” explanations fail to match causal ground truth.

Experimental Design. We anchor our audit on Transcription Factor (TF) binding prediction ( 16 ; 5 ; 50 ) , a canonical task in regulatory genomics. Rather than aggregating broad metrics, we specifically curated five TFs from ENCODE 2 2 2 https://www.encodeproject.org/ database to serve as distinct stress tests that probe the boundaries of IML validity:

Positive Controls (CTCF, MAX): We include these factors because they bind long, high-signal motifs. They represent the “easy” cases where any valid explanation method must succeed.

Compositional Bias Tests (SP1, TBP): To test whether methods detect specific regulatory grammar or merely “shortcut learn” background frequencies, we selected SP1 (which targets GC-rich islands) and TBP (which targets AT-rich promoters).

Resolution Tests (GATA1): We selected GATA1 to test the spatial precision of token-based architectures, as it binds a short ( ∼ \sim 6 bp) and often degenerate motif.

For each transcription factor, we collect high-confidence narrowPeak files from ENCODE. Each peak is represented as a fixed-length DNA sequence centered on the peak summit. Positive samples correspond to experimentally validated binding regions. Negative ones are generated from matched genomic regions that do not overlap called peaks, controlling for chromosome distribution and sequence length.

To ensure these stress tests are statistically robust, we constructed a large-scale benchmark comprising approximately 289,000 289,000 training and 11,500 11,500 test sequences (summarized in Table 1 ). We strictly split the data by chromosome, holding out Chromosome 9 entirely for testing to prevent information leakage. Crucially, this scale allows us to move beyond the qualitative inspection of cherry-picked examples; we utilize over 88,000 88,000 sequences with annotated motif positions to systematically quantify interpretability performance.

We replicate this audit across three divergent genomic foundation models— DNABERT-2 ( 55 ) (Transformer), HyenaDNA ( 37 ) (convolution/SSM), and Nucleotide Transformer v3 (NTv3) ( 8 ) (hybrid)—and evaluate five common interpretability methods: DeepLIFT ( 45 ) , IG ( 47 ) , ISM ( 54 ) , Local Interpretable Model-agnostic Explanations (LIME) ( 40 ) , and the Categorical Jacobian (CJ) ( 52 ) . The CJ quantifies pairwise dependencies by measuring how the model’s predicted distribution at one position changes under perturbations at every other position; to make it comparable to the four per-position attribution methods, we reduce its position-by-position coupling matrix to a per-position importance score by averaging absolute couplings over partner positions. All three models attain non-trivial predictive performance across the five TFs (see Table 3 in Appendix C for accuracy and F1 scores), ensuring that the explanations we audit are derived from models that have learned meaningful patterns from the data. To establish an objective ground truth, we rely on UniBind 3 3 3 https://unibind.uio.no/ database. By retrieving experimentally validated motif coordinates for our held-out test set, we can quantitatively measure whether explanations align with known causal mechanisms, independent of the model’s labels.


## 3.1 IML Methods Disagree with Each Other

If IML methods reliably recovered the true explanation for a model’s prediction, we would expect different methods to produce consistent results. We test this assumption by computing explanations from all IML methods on the same trained model and comparing their outputs.

Methodology. For each test sequence, we obtain per-nucleotide importance scores (absolute values) from each IML method. We quantify agreement between method pairs using: (1) Spearman rank correlation to measure global consistency across all positions, and (2) Jaccard similarity of the top- 20 20 most important positions to assess agreement on critical features—a particularly relevant metric since regulatory motifs are typically shorter than 20 20 bp.

Results. Fig. 2 reveals disagreement among IML methods. Fig. 2 a visualizes attribution maps from all five IML methods on the same CTCF sequence on NTv3, showing qualitatively different patterns: DeepLIFT and CJ show a dominant peak with broader background activity across the sequence, IG concentrates almost entirely on a single sharp peak, ISM generates a few sparse and isolated peaks, and LIME produces a diffuse, noisy signal throughout.

Quantitatively, Fig. 2 b shows that the average Spearman rank correlation between method pairs is consistently below 0.4 0.4 across all models and datasets. The highest correlation (ISM–LIME: ρ = 0.373 \rho=0.373 ) still indicates weak agreement, while several pairs show near-zero or even negative correlations (IG–CJ: ρ = − 0.021 \rho=-0.021 ). Fig. 2 c demonstrates that even when focusing on the most critical positions, the maximum Jaccard similarity remains below 0.5 0.5 (DeepLIFT–IG: 0.494 0.494 ), meaning methods agree on fewer than half of the positions deemed most important. Per-model and per-TF breakdowns of these correlation and Jaccard analyses are provided in Fig. 5 and Fig. 6 in Appendix D .

These results raise a fundamental concern regarding reliability: since different IML methods produce inconsistent explanations, it is unclear which, if any, accurately captures the model’s reasoning. If practitioners follow the common practice of using only one IML method, they risk relying on an arbitrary or biased viewpoint that may not reflect the model’s true decision process.


## 3.2 IML Explanations Are Not Faithful to Model Decisions

Beyond inter-method consistency, we ask whether explanations faithfully reflect what the model considers important—regardless of biological validity. We test this through systematic perturbation experiments ( 42 ) .

Methodology. If an IML method correctly identifies positions most important to a model’s prediction, then perturbing those positions should maximally affect model output. We implement two complementary tests:

Sequential deletion (MoRF) ( 42 ) : Starting from original sequence, we progressively mask positions in descending order of attributed importance by replacing them with neutral tokens(‘N’). A faithful explanation should produce rapid probability decay.

Sequential insertion ( 39 ) : Starting from a fully masked baseline, we progressively restore positions in descending order of importance. A faithful explanation should produce rapid probability recovery.

We quantify faithfulness via the area under the probability curve (AUC): lower deletion-AUC and higher insertion-AUC indicate better faithfulness.

Results. Fig. 3 a and b shows representative curves for CTCF on the NTv3 model. In the deletion experiment, ISM causes the steepest probability drop, followed by LIME and IG, while DeepLIFT and CJ produce the slowest decay. The insets reveal that meaningful separation between methods emerges within the first 20–50 positions—precisely where motif-level features reside. The insertion curves show the inverse pattern: ISM and LIME rapidly recover prediction confidence, while other methods require substantially more positions to achieve comparable recovery.

Fig. 3 c and d present the distribution of AUC scores across all sequences and TFs on NTv3 (DNABERT-2 and HyenaDNA is shown in Appendix E ). For deletion (Fig. 3 c), lower AUC indicates better faithfulness; IG consistently achieves the lowest scores across most TFs, though with substantial variance. Notably, for SP1 and TBP—the compositional bias stress tests—all methods show high AUC values clustered near 1.0, suggesting that none reliably identifies the features driving model predictions. The insertion results (Fig. 3 d) mirror this pattern: IG generally achieves the highest AUC (indicating faster recovery), but performance degrades markedly on SP1 compared to other TFs.

These results demonstrate that faithfulness varies considerably across both methods and tasks. While IG and ISM show relatively better faithfulness, no method consistently excels, and performance deteriorates on tasks where compositional biases may confound the explanations.


## 3.3 IML Explanations Do Not Align with Biological Ground Truth

Ultimately, the value of IML in genomics lies in recovering biologically meaningful signals. We evaluate whether explanations align with experimentally validated TF motifs.

Methodology. For each positive test sequence with an annotated UniBind motif, we extract the contiguous region of length L L (matching the motif length) with the highest summed attribution. We then compute the overlap ratio between this predicted region and the ground-truth motif annotation, yielding a Perception score between 0 (no overlap) and 1 (perfect alignment).

Results. Fig. 4 a reveals stark task-dependent variation in biological alignment on NTv3. For CTCF, which is our high-SNR positive control, all methods achieve reasonable alignment, with median Perception scores exceeding 0.5 and many sequences approaching perfect overlap. This confirms that when the biological signal is strong and unambiguous, IML methods can successfully recover it.

However, performance deteriorates dramatically on other TFs. For GATA1 (resolution challenge) and MAX, median scores drop to 0.2–0.4, with substantial probability mass near zero; on GATA1, CJ in particular collapses to a near-zero median, the lowest of all five methods. Most strikingly, for the compositional bias stress tests (SP1 and TBP), all methods show near-complete failure: the vast majority of sequences yield Perception scores close to zero, which indicates that IML-identified important regions rarely coincide with true binding sites. This suggests that explanations are confounded by background nucleotide composition rather than capturing specific regulatory motifs. Per-model Perception distributions are reported in Fig. 10 in Appendix F .

Fig. 4 b and c illustrate why anecdotal evidence can be misleading. Fig. 4 b shows a good example where LIME attributions (blue) align precisely with the annotated motif region (white background), which is the type of cherry-picked case often showcased in papers. Fig. 4 c shows a bad example where high attributions appear entirely outside the true motif location, yet such failures are rarely reported. Our systematic evaluation reveals that failure cases like Fig. 4 c are far more common than successes like Fig. 4 b for most TF tasks.


## 4 Practical Guidelines for IML Evaluation

With the identified critical limitations in current IML evaluation practices, we now propose a tiered framework of practical guidelines. In particular, considering that practitioners often operate under varying resource constraints, we organize our recommendations by the level of effort required to accommodate different practical scenarios.


## 4.1 Low-Effort Guidelines: Minimum Standards

The following practices require minimal additional effort and should be considered mandatory for any study reporting IML results in computational genomics.

G1: Use Multiple IML Methods. As demonstrated in the previous section, different IML methods can produce drastically different explanations for the same prediction. Relying on a single method provides no indication of explanation robustness. We recommend:

Apply at least three IML methods spanning different categories (e.g., gradient-based, perturbation-based, and attention-based) for generating interpretations.

Report the agreement between methods using quantitative metrics such as rank correlation or top- k k overlap, and treat high disagreement as a warning signal that explanations may be unreliable.

G2: Include Negative Controls. Explanations should be compared against appropriate baselines to assess whether they provide information beyond chance:

Compare IML importance scores against random baselines (uniform random importance assignment).

For sequence data, consider shuffled-sequence controls where the same IML method is applied to sequences with shuffled nucleotide order.

G3: Report Quantitative Metrics Over Visual Inspection. Qualitative assessments ( “the highlighted region appears to overlap with the known binding site” ) are subjective and irreproducible. Instead, we recommend:

Define precise quantitative criteria (e.g., precision, recall, correlation, overlap, etc., when ground-truth annotations are available) before examining explanations.

G4: Report Holistic Statistics Instead of Cherry-Picked Examples. The common practice of showing 1 to 5 “successful” examples provides no information about typical explanation quality. Instead, we recommend:

Compute quantitative evaluation metrics across all test samples.

Report distributions (mean, standard deviation, percentiles) rather than single exemplars.

If illustrative examples are shown, explicitly state how they were selected and how representative they are of the overall distribution.


## 4.2 Moderate-Effort Guidelines: Computational Validation

The following practices require additional computational experiments but no wet-lab resources. They provide stronger evidence of explanation quality.

G5: Perform Faithfulness Tests. As shown in Section 3 , explanations often fail to reflect the model’s actual decision process. Faithfulness can be assessed computationally:

Perturbation-based evaluation : Mask or perturb positions identified as important and measure the prediction drop. Compare against random masking.

Sufficiency test : Retain only the top- k k important positions (masking everything else) and verify that the prediction is preserved.

Comprehensiveness test : Mask the top- k k important positions and verify that the prediction degrades substantially.

Report faithfulness metrics relative to a random baseline. Instead of reporting raw prediction drops, quantify the margin between IML-guided perturbation and random perturbation (e.g., AUC scores).

G6: Test Across Diverse Conditions. Explanation quality may vary across different data characteristics. We recommend systematically evaluating across:

Different prediction confidence levels (e.g., do explanations degrade for uncertain predictions?).

Different sequence contexts (e.g., GC-rich vs. AT-rich regions, as in our experiments).

Different functional categories (e.g., promoters vs. enhancers, coding vs. non-coding regions).


## 4.3 High-Effort Guidelines: Experimental Validation

The following practices require wet-lab experiments or substantial additional resources. They provide the strongest evidence but should be guided by computational pre-screening.

G7: Design Experiments with Proper Controls. When wet-lab validation is pursued, ensure rigorous experimental design:

Select validation targets through stratified random sampling across the whole distribution of IML scores, not by cherry-picking high-confidence cases.

Include both negative controls (e.g., instances where the IML method predicts low importance for known functional elements) and positive controls (instances where both the model and prior knowledge agree on important regions).

Pre-register the validation targets before conducting experiments to prevent post-hoc selection bias.

Report all results, including failures and inconclusive cases, not just successful validations.


## 4.4 A Recommended Workflow

We synthesize the above guidelines into a practical workflow for IML evaluation:

Baseline Assessment (Low Effort) : Apply multiple IML methods, compute agreement metrics, and establish random baselines. If methods strongly disagree or perform near random, stop —explanations are likely unreliable.

Computational Validation (Moderate Effort) : Conduct faithfulness tests and sanity checks. Evaluate against available biological databases. Identify conditions where explanations succeed or fail.

Targeted Experimental Validation (High Effort) : Based on computational screening, design rigorous wet-lab experiments with proper controls. Validate a representative sample and report all results.

Iterative Refinement : Use validation results to refine model architecture, training procedure, or IML method selection. Re-evaluate after modifications.

By adopting these tiered guidelines, practitioners can move beyond anecdotal evidence toward rigorous, reproducible evaluation of IML methods. Even implementing only the low-effort guidelines would represent a substantial improvement over current practices and help prevent the resource misallocation documented in Section 2 .


## 5 Alternative Views

The concerns we raise about IML evaluation practices may seem overly stringent to some practitioners. Indeed, several alternative viewpoints exist that could justify current practices. We examine each of these perspectives and explain why they are insufficient to ensure reliable interpretability in genomics applications.

Theoretical Guarantees. Several popular IML methods come with theoretical foundations. For example, IG satisfies axioms like sensitivity and implementation invariance ( 47 ) ; SHAP values are grounded in cooperative game theory with uniqueness guarantees ( 35 ) ; DeepLIFT provides a principled decomposition of the prediction difference ( 45 ) . However, theoretical guarantees do not translate to practical reliability. The axioms satisfied by these methods concern mathematical properties of the attribution (e.g., that attributions sum to the prediction difference), not whether attributions identify biologically meaningful features ( 7 ) . A method can satisfy all theoretical axioms while still highlighting spurious correlations learned by the model. Moreover, different axiom-satisfying methods can produce drastically different explanations for the same prediction ( 32 ; 30 ; 21 ) , as we demonstrate empirically in Section 3.1 .

Visual Inspection. A common practice in the community is to have biologists visually inspect IML outputs on selected examples and assess whether the highlighted regions “make sense” given prior knowledge ( 3 ; 54 ; 5 ) . This approach suffers from several critical flaws. First, confirmation bias is inevitable: practitioners are more likely to notice and report cases where explanations match expectations, while dismissing or ignoring contradictory cases as noise or edge cases ( 29 ; 33 ; 1 ) . Such selective reporting provides no information about the method’s reliability in the broader scenarios. Second, visual inspection cannot detect subtle failures—an explanation might highlight a region near but not exactly at the true binding site, which appears correct visually but would fail quantitative evaluation. Finally, this approach cannot assess faithfulness: an explanation might align with biology by coincidence while not reflecting what the model actually learned ( 34 ) .

Accuracy Metrics. If a model achieves high accuracy on test data, one might assume that its explanations must capture true biological signals—otherwise, how could it predict well? This reasoning suggests that evaluation efforts should focus on model accuracy rather than explanation quality. Yet, models can achieve high accuracy through spurious correlations that happen to be predictive in the training distribution but do not reflect causal mechanisms. In genomics, this is particularly concerning: GC content, dinucleotide frequencies, or positional biases can be highly predictive of certain regulatory outcomes without corresponding to specific functional elements ( 20 ; 5 ; 50 ) . A model exploiting such shortcuts would produce explanations highlighting these confounders rather than true biological signals ( 19 ; 38 ) . Furthermore, even when a model does learn true signals, IML methods may fail to surface them faithfully, as we demonstrate in Section 3.2 . Predictive accuracy and explanation quality are orthogonal properties that must be evaluated independently ( 1 ; 41 ; 43 ) .

IML benchmarks. The machine learning community has developed various benchmarks for evaluating IML methods in general domains, including synthetic datasets with known ground truth ( 24 ) and comprehensive evaluation toolkits ( 23 ; 2 ) . While general-purpose benchmarks are valuable, they do not capture the unique challenges of genomics applications ( 27 ) . Biological sequences have distinct properties—combinatorial motif grammars, long-range dependencies, strand symmetries, and compositional biases—that are absent in natural images or tabular data ( 31 ; 22 ; 5 ) . IML methods may succeed on standard benchmarks while failing on genomics-specific challenges. For instance, a method might correctly identify important pixels in an image but fail to localize a short motif embedded in a longer regulatory sequence. Domain-specific evaluation using biologically meaningful ground truth is essential to validate IML methods for genomics ( 43 ; 16 ) .

Wet-lab validation. While wet-lab validation often provides the strongest evidence, it alone cannot serve as the primary evaluation strategy for several reasons. First, experimental validation is expensive and low-throughput—it is infeasible to validate more than a handful of predictions per study. Second, selective validation of high-confidence predictions creates survivorship bias: we only learn about cases where explanations were correct, not the (potentially larger) set of failures. Third, without computational pre-screening, wet-lab resources may be wasted on unreliable explanations. Computational tests serve as essential gatekeepers that identify when explanations are likely unreliable before committing experimental resources. The ideal workflow uses computational validation to filter and prioritize candidates for subsequent experimental confirmation.

Our position. None of the above alternatives provides adequate assurance that IML explanations are reliable for guiding biological interpretation or experimental design. We therefore argue that practitioners should adopt a multi-layered evaluation strategy as described in Section 4.4 . Only through such rigorous evaluation can we move beyond anecdotal evidence and establish genuine confidence in IML-derived biological insights.


## 6 Conclusion

Our results highlight a growing mismatch between how interpretability methods are used in genomic modeling and how rigorously their outputs are evaluated. Although post hoc IML techniques are often assumed to reveal meaningful model reasoning, our analysis shows that explanations frequently disagree across methods, only weakly reflect model behavior, and often fail to recover known biological mechanisms. These issues are largely obscured by current norms that emphasize qualitative plausibility and selectively reported successes.

This gap matters in practice. Interpretability results increasingly inform experimental prioritization, mechanistic claims, and downstream biological hypotheses. When explanations are unreliable, they risk misdirecting experimental effort and overstating model understanding. We therefore argue that interpretability should be evaluated as an empirical object in its own right. Systematic and rigorous quantitative validation is necessary for interpretability methods to support reliable scientific inference in genomics rather than anecdotal justification.

Code and Data Availability. The code and data used in this paper are available at https://github.com/COLA-Laboratory/EvalXAI .


## Acknowledgments

We sincerely thank all the reviewers for their encouraging and constructive feedback. This work was supported by the UKRI Future Leaders Fellowship under Grant MR/S017062/1 and MR/X011135/1; in part by NSFC under Grant 62376056 and 62076056; in part by the Royal Society Faraday Discovery Fellowship (FDF/S2/251014), BBSRC TransformativeResearch Technologies (UKRI1875), Royal Society International Exchanges Award (IES/R3/243136), Kan Tong Po Fellowship (KTP/R1/231017); and the Amazon Research Award and Alan Turing Fellowship. We also acknowledge the compute support provided by Modal.


## References


## Appendix A LLM-based Structure Extraction Prompt for the Mapping Study

We use gemini-3-flash-preview to extract structured information about interpretable machine learning (IML) evaluation and reporting practices from full-text genomics papers. The whole pipeline can be divided into two stages. At the first stage, we use a few-shot in-context learning approach to extract the structured information from the paper. At the second stage, we use a self-reflection pass to verify the extraction against the actual paper text and correct any errors.


## A.1 Stage 1: Few-shot In-context Learning for Structured Extraction

Ten manually curated demonstrations are provided below. Each consists of an abbreviated paper description and the corresponding gold-standard extraction (annotated by an author).

The full text of the paper is provided below the prompt, enclosed in delimiters:


## A.2 Stage 2: Self-Reflection Prompt

After Stage 1 returns a JSON extraction for a paper, we will input the paper text and the JSON output back to the LLM to perform the self-reflection. The LLM will re-read the paper and verify each field in the extraction against the actual paper text. It will then correct any hallucinations, miscounts, and misclassifications that slip through Stage 1.


## Appendix B Per-Category Agreement Rates of LLM-based Extraction

To assess the reliability of the LLM-based extraction pipeline described in Appendix A , one of the authors manually annotated a random sample of 100 100 papers and compared the manual labels against the LLM outputs across the four extraction categories used in our mapping study. The per-category agreement rates are reported in Table 2 . The overall agreement rate, averaged across all categories, is 98 % 98\% .


## Appendix C Predictive Performance of Foundation Models on TF Binding Prediction

Table 3 reports the test-set predictive performance (accuracy and F1 score) of the three genomic foundation models—DNABERT-2, HyenaDNA, and NTv3—fine-tuned on the TF binding prediction task across the five transcription factors (CTCF, MAX, SP1, TBP, and GATA1) introduced in Section 3 . These results establish that all three models attain non-trivial predictive performance, which is a prerequisite for the subsequent interpretability audit: the explanations evaluated in our study are derived from models that have learned meaningful patterns from the data.


## Appendix D Per-Model and Per-TF Breakdown of IML Disagreement

Fig. 5 and Fig. 6 report the inter-method Spearman rank correlation and top- 20 20 Jaccard similarity, broken down by foundation model (DNABERT-2, HyenaDNA, NTv3) and by transcription factor (CTCF, MAX, SP1, TBP, GATA1). These breakdowns complement the model- and TF-aggregated heatmaps in Fig. 2 b and c, and show that the low pairwise agreement reported in 3.1 is not driven by a particular model or TF.


## Appendix E Per-Model Faithfulness Evaluation

Fig. 7 , Fig. 8 , and Fig. 9 report the deletion-AUC and insertion-AUC distributions on DNABERT-2, HyenaDNA, and NTv3, respectively.


## Appendix F Per-Model Biological Alignment

Fig. 10 reports the per-TF and per-IML method Perception scores on DNABERT-2, HyenaDNA, and NTv3.