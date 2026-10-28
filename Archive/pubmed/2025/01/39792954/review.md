## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results and discussion, Conclusions, Methods) as provided
- **Assessment boundary** Scientific claims, methodology, evidence quality, and presentation as they appear in the supplied text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors argue that large-scale chromatin state deep learning models, specifically Sei, serve as effective foundation models for predicting intron retention (IR) from DNA sequence alone. They demonstrate that fine-tuning Sei (FSei) outperforms a DNA language model (DNABERT-2) and models trained from scratch, and that a simple logistic regression on Sei's chromatin-state predictions yields interpretable associations between transcription factors and IR.
- **Visible evidence base** Reported AUPRC/ROC values, model architecture descriptions, dataset composition (20,925 positive, 55,067 negative examples), feature importance rankings, Integrated Gradients analysis, and literature citations.
- **Missing materials affecting confidence** No figures, tables, or supplementary data were provided. No code repository, hyperparameter details beyond those mentioned, or full results tables were accessible. The manuscript references figures (Fig 1-5) and tables (Table 1-3) that could not be inspected. No statistical significance tests or confidence intervals were reported in the text.

## Reviewer
- **Overall assessment** The manuscript presents a compelling and timely case for using chromatin-state foundation models over DNA language models for a specific regulatory genomics task. The core comparison between Sei and DNABERT-2 is informative, and the interpretability analysis via Sei-targets is a valuable contribution. However, the evidence as presented is incomplete: key figures and tables are missing, several claims about biological relevance rely on qualitative literature connections rather than quantitative validation, and the lack of statistical rigor in model comparisons weakens the central argument. The work is potentially publishable after substantial revision and addition of missing evidence.
- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on regulatory genomics, splicing regulation, and transfer learning. The paper directly addresses the practical utility of foundation models in genomics, a topic of broad current interest. Researchers studying intron retention and its connection to chromatin state would also find the TF associations valuable.
- **Major strengths** 1) Clear and well-motivated research question with a practical demonstration of transfer learning. 2) Direct comparison between a chromatin-state model and a DNA language model, addressing an important gap in the literature. 3) The Sei-targets approach provides an interpretable bridge between black-box predictions and biological hypotheses. 4) The finding that a simple logistic regression on Sei outputs nearly matches fine-tuning performance is practically useful and intellectually interesting.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing statistical comparison), R1-M2 (incomplete dataset description), R1-M3 (unvalidated TF associations), R1-M4 (unverifiable interpretability analysis).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of Sei to IR prediction is novel, but the general approach of fine-tuning pre-trained models is well established. **Scientific importance**: Moderate to high. The demonstration that chromatin-state models outperform DNA language models for a chromatin-related task has implications for model choice in regulatory genomics. **Interdisciplinary readership**: Moderate. The paper bridges machine learning and molecular biology, but the presentation assumes familiarity with both fields. **Technical soundness**: Currently insufficient. The lack of statistical tests, incomplete dataset description, and unverifiable interpretability analysis prevent a full assessment. **Readability for nonspecialists**: Good. The writing is clear and the logical flow is easy to follow, though some jargon (e.g., "dilated convolution", "Integrated Gradients") could be better explained.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is sound and the results are promising, but the current evidence base is insufficient to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "The fine-tuned Sei model (FSei) outperformed the LLM-based model that uses DNABERT-2 (AUPRC of 0.653 compared to 0.567)."
- **Evidence pointer** Results and discussion, "Transfer learning is all you need" section; Figure 2 (not provided)
- **Concern** The manuscript reports AUPRC values for multiple models but provides no statistical significance testing, confidence intervals, or variance estimates. It is impossible to determine whether the observed differences (e.g., 0.653 vs. 0.627) are meaningful or within noise. The authors also do not report the number of independent runs or how variability was assessed.
- **Why it matters** The central claim of the paper is that Sei-based models are superior to alternatives. Without statistical validation, this claim is not established. The differences between some models are small (0.653 vs. 0.656), and the reader cannot assess whether these are reproducible.
- **Resolution test** Provide confidence intervals or standard deviations for all reported metrics, ideally from multiple training runs with different random seeds. Perform a statistical test (e.g., bootstrap or McNemar's test) comparing the top models. Report the number of runs and the variance across runs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data description and reproducibility
- **Claim pointer** "The resulting dataset contains 20,925 IR DHSs (positive examples) and 55,067 DHSs that are not known to exhibit IR (negative examples)."
- **Evidence pointer** Results and discussion, first paragraph; Methods, "Data" section; Table 2 (not provided)
- **Concern** The dataset description is incomplete. The authors state that they extended their previous dataset with IR events from RNA-seq data, but do not provide details on how IR events were defined from RNA-seq, what thresholds were used, how many IR events were added, or how the final positive/negative balance was achieved. The final dataset size (151,984 sequences) does not match the numbers given in the text (20,925 + 55,067 = 75,992), suggesting additional data augmentation or filtering steps that are not described. The Methods section mentions "reverse complement for data augmentation" but does not explain how this affects the dataset size or whether the reported numbers include augmented sequences.
- **Why it matters** Reproducibility is a core requirement. Without a complete description of data generation, filtering, and augmentation, other researchers cannot replicate the experiments or assess potential biases in the dataset.
- **Resolution test** Provide a complete data processing pipeline, including: (1) exact criteria for defining IR from RNA-seq, (2) the number of IR events added from RNA-seq, (3) how DHSs were assigned to IR or non-IR classes, (4) how reverse complement augmentation was applied and whether it was applied to both classes, and (5) a clear breakdown of dataset sizes at each stage.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** "We are able to provide evidence for the involvement of several of the top ranking targets in alternative splicing."
- **Evidence pointer** Results and discussion, "TF involvement in IR" section; Figure 5 (not provided)
- **Concern** The authors list several TFs (Pol II, AFF4, MYC, CTCF, BRD4) that appear high in their rankings and connect them to known literature on splicing regulation. However, no quantitative validation is provided. The authors do not test whether the enrichment of these TFs in IR-associated DHSs is statistically significant compared to a null model, nor do they compare their findings to known IR-regulating factors in a systematic way. The claim that these associations constitute "evidence" is overstated.
- **Why it matters** The interpretability analysis is a key contribution of the paper. If the TF associations are not rigorously validated, the biological conclusions are speculative and the practical utility of the Sei-targets approach is diminished.
- **Resolution test** Perform a permutation test or use a background model to assess whether the top-ranked TFs are significantly enriched in IR DHSs. Compare the identified TFs against a curated list of known splicing regulators to assess recall. Provide effect sizes and confidence intervals for the enrichment scores.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability methodology
- **Claim pointer** "Using the methodology described in the Methods section, which uses positions identified using the Integrated Gradients method, we obtained a ranking of 949 human TFs based on their preference for occurrence in retained introns compared to non-retained introns."
- **Evidence pointer** Methods, "Attribution with Integrated Gradients" section
- **Concern** The Integrated Gradients analysis is described briefly, but several critical details are missing. The authors do not specify how the "hot spots" were defined beyond a 70% threshold, how motif scanning was performed (e.g., which Jaspar motif database version, what score threshold), or how the final TF ranking was computed. The reduction from 21,907 Sei targets to 949 TFs is not explained. The authors also do not discuss potential biases in the approach, such as the effect of sequence length or GC content on IG scores.
- **Why it matters** The interpretability results are a major selling point of the paper. Without a complete methodological description, the results cannot be reproduced or properly evaluated.
- **Resolution test** Provide a detailed step-by-step description of the IG analysis, including: (1) the exact definition of a "hot spot", (2) the Jaspar database version and score threshold used, (3) how multiple motifs per TF were handled, (4) how the final TF ranking was derived, and (5) any normalization or correction steps applied.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract opens with a general statement about deep learning in NLP and computer vision, which is not directly relevant to the specific contribution of the paper. This delays the reader's understanding of the actual work.
- **Required correction** Consider starting the abstract with the specific problem (intron retention prediction) and the gap the paper addresses, then introduce the foundation model concept.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction, "Related work on splicing prediction"
- **Evidence pointer** Introduction, "Related work on splicing prediction" section
- **Issue** The term "slicing code" appears to be a typo for "splicing code". This is a minor but noticeable error.
- **Required correction** Correct "slicing code" to "splicing code".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and discussion, "Transfer learning is all you need"
- **Evidence pointer** Results and discussion, "Transfer learning is all you need" section
- **Issue** The authors mention that "freezing the weights of the Sei model provided lower accuracy" but do not report the actual value. This is a relevant comparison point for understanding the importance of fine-tuning.
- **Required correction** Report the AUPRC for the frozen Sei model in the text or in Table 1.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Training, validation, and testing"
- **Evidence pointer** Methods, "Training, validation, and testing" section
- **Issue** The hyperparameter table (Table 3) is referenced but not provided. The authors mention "early stopping epochs" and other parameters but do not give specific values in the text.
- **Required correction** Ensure Table 3 is included in the final submission with all hyperparameter values clearly listed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results and discussion, "TF involvement in IR"
- **Evidence pointer** Results and discussion, "TF involvement in IR" section
- **Issue** The authors state that "the top 100 and bottom 100 ranked TFs had an intersection of 22 TFs" but do not discuss the implications of this overlap. This is an interesting observation that deserves more interpretation.
- **Required correction** Add a brief discussion of what the overlap between top and bottom ranked TFs might indicate (e.g., context-dependent roles of TFs).

## Risk / unsupported claims
- The claim that "chromatin state has a strong influence on splicing outcome" is supported by literature citations but not directly tested in this work. The paper demonstrates correlation, not causation.
- The statement that "the Sei model captures more of the complexities of chromatin state due to the much larger datasets used to train it" is speculative. The performance difference could be due to other factors such as architecture or training procedure.
- The claim that "our findings are in strong agreement with recent work" (reference [18]) is not substantiated with specific comparisons. The authors should detail what aspects of their findings agree and how.
- The biological interpretation of TF associations (Section "TF involvement in IR") is presented as evidence but lacks statistical validation, as noted in R1-M3.
- The assertion that "the fined-tuned Sei model" (typo in section heading) provides interpretable results via Integrated Gradients is not fully supported, as the methodology is incomplete (R1-M4).