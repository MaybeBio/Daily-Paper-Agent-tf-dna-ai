## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors present an active machine learning framework to iteratively train models of cis-regulatory activity in mammalian photoreceptors. They claim that this approach trains accurate models with an order of magnitude less data than current methods, that model confidence estimates reliably guide sequence design, and that the model identifies causal sequence features, including a novel NR1-family motif, that distinguish active from inactive CREs.
- **Visible evidence base** Main text figures (Figures 1–4), Extended Data Figures 1–8, Supplementary Tables 1–8, Methods section, Data availability statement.
- **Missing materials affecting confidence** Figure panels and Extended Data figures were not viewable in the provided text. Supplementary Tables were not provided. Code and processed data were not accessed. This limits verification of quantitative results, model performance metrics, and detailed experimental outcomes.

## Reviewer
- **Overall assessment** This manuscript addresses a significant problem in regulatory genomics: the limited supply of natural genomic sequences for training deep learning models of cis-regulatory activity. The authors propose active learning as a solution and demonstrate its application to photoreceptor CREs, with a focus on the transcription factor CRX. The work is timely and the iterative experimental approach is ambitious. The central claims, however, rest on a series of comparisons and validations that are difficult to fully assess from the text alone. The demonstration that active learning outperforms random sampling is a key claim that requires careful statistical validation. The identification of a novel NR1-family motif is intriguing but its generalizability and mechanistic basis require further support. The manuscript is well-written and the methods are described in detail, but several technical aspects and the strength of the evidence for the main conclusions need clarification and additional analysis.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and gene therapy. The work is directly relevant to those studying cis-regulatory elements, transcription factor grammar, and the application of machine learning to functional genomics. The focus on photoreceptors and CRX will be of interest to the vision research community. The active learning framework itself has broader methodological appeal for anyone training models on limited biological data.
- **Major strengths**
    1.  The problem addressed is important and well-articulated: the genome is a finite source of training data for learning cis-regulatory grammar.
    2.  The application of active learning to this problem is novel and conceptually sound.
    3.  The experimental design, using iterative rounds of MPRA in live tissue, is ambitious and technically demanding.
    4.  The focus on silencers, a class of CREs often ignored, is a strength.
    5.  The use of model interpretation to generate and test hypotheses about regulatory grammar is a modern and powerful approach.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness / Statistical validation
        - **Claim pointer** The central claim that active learning trains accurate models with an order of magnitude less data than current approaches.
        - **Evidence pointer** Figure 1c, Figure 2a, Methods (Active learning)
        - **Concern** The primary evidence for the superiority of active learning is the performance comparison between models trained on actively selected data versus randomly selected data. The manuscript states that active learning outperforms random sampling, but the statistical significance of this difference is not reported. The comparison in Figure 2a appears to be a single trajectory or a small number of replicates. Without a proper statistical framework (e.g., multiple independent runs of the entire active learning loop, confidence intervals on the performance curves), it is impossible to determine if the observed improvement is robust or a stochastic artifact.
        - **Why it matters** This is the foundational claim of the paper. If the improvement from active learning is not statistically robust, the entire premise of the method is weakened. The claim of using "an order of magnitude less training data" is a quantitative statement that requires a quantitative demonstration of its reliability.
        - **Resolution test** The authors should provide a statistical analysis of the active learning performance. This could include running the entire active learning process multiple times (with different random seeds for model initialization and candidate generation) and reporting the mean and variance of the performance metric (e.g., wF1) at each round. A statistical test (e.g., a permutation test or a comparison of confidence intervals) should be used to demonstrate that the actively selected data leads to significantly better performance than randomly selected data of the same size.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness / Model validation
        - **Claim pointer** The claim that the model's internal confidence estimates are reliable guides for designing sequences with high activity.
        - **Evidence pointer** Figure 1f, Methods (Active learning)
        - **Concern** The manuscript reports that 72% of high-confidence predictions were correct. This is presented as a key result. However, the definition of "correct" is not fully clear. Is it correct classification into the exact same activity class? The manuscript mentions "off by one class" for 14.5% of predictions, implying that "correct" means the exact class. More importantly, the baseline for this performance is not established. What is the accuracy of the model on all predictions, or on low-confidence predictions? Without this comparison, it is unclear if 72% accuracy on high-confidence predictions is a meaningful improvement or simply a reflection of the model's overall accuracy. The utility of confidence estimates for *designing* sequences is also not directly demonstrated. The authors show that high-confidence predictions are more accurate, but do they show that selecting sequences predicted to be strong enhancers with high confidence actually yields strong enhancers at a higher rate than selecting sequences with lower confidence?
        - **Why it matters** This claim is central to the practical utility of the model. If confidence estimates are not calibrated or do not provide a better-than-random way to select functional sequences, then the model's value for genome editing or synthetic biology is diminished.
        - **Resolution test** The authors should report the accuracy of the model on all predictions and on low-confidence predictions. They should also perform a direct test of the design capability: e.g., take a set of sequences predicted to be strong enhancers with high confidence and a set predicted with low confidence, and compare their experimentally measured activities. This would directly demonstrate the value of the confidence scores for sequence design.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Scientific importance / Generalizability
        - **Claim pointer** The claim that the model identified a new sequence feature, the NR1-family motif, that is necessary and sufficient to distinguish active from inactive sequences.
        - **Evidence pointer** Figure 4, Extended Data Figures 6 and 7, Results (The model identifies causal differences between similar CREs)
        - **Concern** The analysis of the two example sequences is compelling, but it is a case study of a single pair of sequences. The claim that the NR1-family motif is a general feature of photoreceptor enhancers is not supported by a genome-wide or library-wide analysis. The authors state that the motif is "not sufficiently enriched among all strong enhancers to be detected by traditional motif-finding methods," which suggests it is not a globally important feature. The manuscript would be strengthened by a systematic analysis of how often the model's predictions of important NR1-family sites are validated across a larger set of sequences.
        - **Why it matters** The discovery of a new regulatory motif is a significant claim. A case study, while illustrative, is not sufficient to establish the general importance of this motif in photoreceptor gene regulation. The authors need to demonstrate that this motif plays a role in a significant fraction of photoreceptor enhancers.
        - **Resolution test** The authors could perform a larger-scale validation experiment where they mutate predicted NR1-family sites in a library of enhancers and measure the effect on activity. Alternatively, they could use their model to scan the genome for enhancers that depend on NR1-family sites and test a subset of these predictions experimentally.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity / Reproducibility
        - **Affected element** Methods (Active learning)
        - **Evidence pointer** Methods section
        - **Issue** The description of the active learning loop, particularly the candidate generation and selection process, is somewhat brief. The exact parameters for the "mutagenizing" step (e.g., mutation rate, number of candidates) and the criteria for "high confidence" are not fully specified.
        - **Required correction** Provide a more detailed pseudocode or a step-by-step description of the active learning algorithm, including all relevant hyperparameters. This is essential for reproducibility.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Technical soundness
        - **Affected element** Results (Iteratively learning the cis-regulatory grammar)
        - **Evidence pointer** Figure 1c, Extended Data Figure 3
        - **Issue** The manuscript mentions that the CNN did not generalize in Round 1 but does not provide a detailed analysis of why. Understanding the failure mode of the initial model is important for designing better active learning strategies.
        - **Required correction** Add a brief discussion of the potential reasons for the initial poor performance (e.g., insufficient data, model capacity, optimization issues) and how the active learning process overcame this.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Readability for nonspecialists
        - **Affected element** Introduction
        - **Evidence pointer** Introduction section
        - **Issue** The introduction is dense and assumes a high level of familiarity with both regulatory genomics and machine learning. The concept of "cis-regulatory grammar" could be explained more explicitly for a broader audience.
        - **Required correction** Consider adding a brief, accessible explanation of what is meant by "cis-regulatory grammar" and why learning it is a challenging problem.
- **Assessment against Nature-style criteria**
    - **Originality** The application of active learning to cis-regulatory grammar is novel. While active learning is an established field, its use in this context, particularly with iterative MPRA experiments in a complex tissue, is a new contribution.
    - **Scientific importance** The problem of learning regulatory grammar from limited data is of high importance. If the method is robust, it could be applied to other cell types and tissues, potentially accelerating our understanding of gene regulation. The focus on silencers is also important.
    - **Interdisciplinary readership** The work bridges machine learning, genomics, and vision research. It will be of interest to computational biologists and experimentalists in these fields. The potential for broader interest in the machine learning community is moderate, as the methodological novelty is in the application rather than in a new ML algorithm.
    - **Technical soundness** The experimental design is sound, but the statistical validation of the main claims is currently insufficient. The lack of statistical rigor in comparing active vs. random learning and in assessing the value of confidence scores is a significant weakness.
    - **Readability for nonspecialists** The manuscript is clearly written for a specialist audience. The abstract is accessible, but the introduction and results are dense. The main concepts and findings could be made more accessible to a broader scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the experimental effort is substantial. However, the central claims regarding the efficacy of active learning and the utility of confidence estimates are not yet fully established from the provided evidence. The authors must provide a more rigorous statistical analysis to support these claims. The case study of the NR1-family motif is interesting but requires broader validation to be a major finding.

## Risk / unsupported claims
- The claim that active learning requires "an order of magnitude less training data" is not quantitatively supported by a statistical comparison with random sampling.
- The claim that the model's confidence estimates are "reliable guides" for designing high-activity sequences is not supported by a direct test of the design process or a comparison to a baseline.
- The claim that the NR1-family motif is a "new sequence feature" that is "necessary and sufficient" for enhancer activity is based on a single case study and is not generalized.
- The performance of the SVM on the genomic test set is not reported, making it impossible to compare the two model architectures on this key benchmark.
- The claim that the model "recapitulates prior knowledge" is not explicitly demonstrated with a comparison to known regulatory features.