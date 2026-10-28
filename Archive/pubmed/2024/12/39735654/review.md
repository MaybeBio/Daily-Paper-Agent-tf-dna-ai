## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, technical accuracy, completeness of coverage, clarity of presentation, and suitability for the stated audience
- **Shared manuscript claim summary** The manuscript reviews machine learning approaches for predicting gene expression and chromatin features from DNA sequence, with emphasis on methods for extracting biological hypotheses and assessing confidence in those hypotheses
- **Visible evidence base** Full text including abstract, introduction, sections on ML methods, variant prioritization, hypothesis testing, model interpretation, and conclusions
- **Missing materials affecting confidence** Figures and Box 1 referenced in the text were not provided; no supplementary materials were available

## Reviewer
- **Overall assessment** This is a well-structured and clearly written review article covering a timely and important topic in regulatory genomics. The author provides a useful synthesis of ML methods ranging from classical approaches to deep learning, with particular attention to the critical issue of model interpretability and confidence assessment. The manuscript is accessible to its intended audience of biologists and computational biologists. However, several technical inaccuracies and omissions weaken the review, and the treatment of some topics is uneven. The Rashomon effect discussion is a valuable addition but could be more deeply integrated. The review would benefit from more critical evaluation of the methods described and from addressing recent developments in the field.

- **Who would be interested in the results, and why** Biologists and computational biologists working in regulatory genomics, gene expression prediction, and functional interpretation of non-coding variants. The review provides a practical overview of available methods and their interpretability, which is directly relevant to researchers designing or interpreting ML-based studies of gene regulation. The discussion of confidence measures and hypothesis extraction is particularly useful for experimentalists seeking to validate computational predictions.

- **Major strengths** 
  1. Clear and accessible explanation of diverse ML methods, from linear models to deep learning, without assuming advanced ML expertise
  2. Thoughtful organization around the theme of hypothesis extraction and confidence assessment, which is a genuinely important and often underappreciated aspect of ML applications in genomics
  3. Good use of concrete examples from the literature to illustrate methodological points
  4. The discussion of the Rashomon effect and model stability is a valuable and relatively novel contribution to the review literature
  5. Balanced treatment of the limitations of current approaches, particularly regarding extrapolation and the gap between model accuracy and biological validity

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that gkm-SVM was applied to 467 human ChIP-seq experiments from ENCODE, with sequences of around 300 bp and random genomic sequences as negatives.
- **Evidence pointer** Section "Support vector machines", location not provided
- **Concern** The description of the gkm-SVM application is incomplete and potentially misleading. The original gkm-SVM study by Ghandi et al. (2014) used a specific approach for negative sequence selection that involved matching genomic features, not simply random genomic sequences. The manuscript's simplified description does not accurately represent the methodology and could mislead readers about the importance of negative selection strategies.
- **Why it matters** Negative sequence selection is a critical methodological choice in regulatory genomics ML, and the manuscript elsewhere emphasizes the importance of this choice. An inaccurate description of a key reference undermines the review's reliability and its pedagogical value.
- **Resolution test** Revise the description of gkm-SVM to accurately reflect the negative sequence selection strategy used in the original study, or clarify that the description is a simplification and direct readers to the original publication for methodological details.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that DeepSEA reports median AUROC between 85% and 95% depending on the type of profiles.
- **Evidence pointer** Section "Convolutional neural networks", location not provided
- **Concern** The reported AUROC ranges for DeepSEA are not consistent with the original publication. Zhou and Troyanskaya (2015) reported performance metrics separately for TF binding, DHS, and histone marks, with median AUROC values that vary by data type and are not uniformly in the 85-95% range. The manuscript's single range for all profile types is imprecise and potentially misleading.
- **Why it matters** Accurate reporting of performance metrics is essential for readers to assess the relative merits of different methods. Imprecise reporting undermines the review's utility as a reference.
- **Resolution test** Verify the AUROC values against the original DeepSEA publication and report performance separately for each data type, or provide a more accurate summary range with appropriate qualification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of coverage
- **Claim pointer** The manuscript claims to review "a selection of these methods, ranging from linear models to random forests, kernel methods, and more advanced deep learning models" and to cover "the different techniques and strategies that can be used to extract new gene-regulation hypotheses from these models."
- **Evidence pointer** Sections "ML for Regulatory Genomics" through "Breaking the Regulatory Code", location not provided
- **Concern** The review omits several important recent developments in the field, including: (1) transformer-based models beyond Enformer, such as Borzoi and Nucleotide Transformer; (2) the use of large language model architectures for regulatory genomics; (3) recent work on uncertainty quantification in genomic ML; and (4) methods for causal inference from sequence-to-expression models. Given the rapid pace of development in this area, the review already appears somewhat dated despite its 2024 publication date.
- **Why it matters** A review article should provide readers with a current and comprehensive overview of the field. Omissions of major recent developments limit the review's value as a resource for researchers entering the field or seeking to understand the current state of the art.
- **Resolution test** Add discussion of transformer-based approaches and other recent developments, or explicitly state the cutoff date for literature coverage and justify the selection criteria.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual clarity
- **Claim pointer** The manuscript distinguishes between "objective" importance measures (based on model error) and "subjective" measures (based solely on model predictions), and uses this distinction throughout the review.
- **Evidence pointer** Sections "Introduction" and "Breaking the Regulatory Code", location not provided
- **Concern** The objective/subjective dichotomy is not clearly defined and may be conceptually problematic. All importance measures are ultimately model-dependent and therefore subjective in a philosophical sense. The distinction the author seems to be drawing is between measures that are validated against held-out data (error-based) and those that are not, but this is not stated clearly. The terminology could confuse readers and oversimplifies a nuanced issue.
- **Why it matters** The objective/subjective distinction is a central organizing theme of the review. If the conceptual foundation is unclear, the entire framework of the review is weakened.
- **Resolution test** Clarify the definition of objective versus subjective importance measures, perhaps by using more precise terminology such as "error-based" versus "prediction-based" measures, and discuss the limitations of this dichotomy.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "the main limitation of CNN models lies in the difficulty to globally and objectively assess the importance of the extracted features" and that "we do not know with precision whether all important features have been extracted."
- **Evidence pointer** Section "Conclusions", location not provided
- **Concern** This claim is presented as a general limitation of CNN models, but the manuscript does not discuss recent work addressing this issue, such as: (1) methods for comprehensive feature attribution (e.g., DeepSHAP, Integrated Gradients applied systematically); (2) approaches for validating extracted features through saturation mutagenesis experiments; and (3) techniques for assessing feature completeness. The claim may be overly pessimistic given recent methodological advances.
- **Why it matters** The conclusion that CNN interpretability is fundamentally limited may discourage readers from using these methods. A more nuanced discussion of current capabilities and limitations would be more balanced and useful.
- **Resolution test** Qualify the claim by discussing recent advances in feature attribution and validation, and distinguish between practical limitations and fundamental ones.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the review covers "linear models to random forests, kernel methods, and more advanced deep learning models" but does not mention the important theme of confidence assessment and hypothesis validation, which is a major focus of the review.
- **Required correction** Add a sentence to the abstract mentioning the review's focus on methods for extracting and validating biological hypotheses from ML models.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Support vector machines"
- **Evidence pointer** Section "Support vector machines", location not provided
- **Concern** The manuscript states that "SVMs are among the most successful methods of ML" without qualification. While SVMs have been successful in many applications, their dominance has been largely superseded by deep learning in genomics and other fields.
- **Required correction** Qualify the statement, for example by noting that SVMs were among the most successful methods prior to the deep learning era, or by specifying the contexts in which SVMs remain competitive.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Convolutional neural networks"
- **Evidence pointer** Section "Convolutional neural networks", location not provided
- **Concern** The description of Enformer mentions self-attention but does not explain the key architectural innovation of using transformer layers to capture long-range interactions. Readers unfamiliar with transformers may not understand why this is significant.
- **Required correction** Add a brief explanation of how self-attention enables modeling of long-range dependencies, and why this is important for regulatory genomics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Identifying and Prioritizing Genomic Variants"
- **Evidence pointer** Section "Identifying and Prioritizing Genomic Variants", location not provided
- **Concern** The discussion of variant prioritization is brief and does not mention important practical considerations such as the choice of reference genome, handling of multiple variants in linkage disequilibrium, or the use of allele-specific expression data.
- **Required correction** Expand the discussion to address these practical considerations, or add a note directing readers to more detailed resources.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Exploring model behavior on synthetic sequences"
- **Evidence pointer** Section "Exploring model behavior on synthetic sequences", location not provided
- **Concern** The manuscript states that the global importance analysis approach "does not comply with a fundamental assumption in ML, which states that the training and test sets must be representative of the samples to classify." This is a somewhat imprecise statement of the i.i.d. assumption, and the connection to synthetic sequences could be made more clearly.
- **Required correction** Clarify the statistical assumption being referenced and explain more precisely why synthetic sequences may violate it.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Breaking the Regulatory Code"
- **Evidence pointer** Section "Breaking the Regulatory Code", location not provided
- **Concern** The section on model interpretation is dense and could benefit from a summary table comparing the different interpretation methods and their outputs.
- **Required correction** Consider adding a table summarizing the interpretation methods, their inputs, outputs, and limitations.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Conclusions"
- **Evidence pointer** Section "Conclusions", location not provided
- **Concern** The conclusions section does not discuss future directions or open challenges in the field, which would be valuable for readers seeking to identify research opportunities.
- **Required correction** Add a brief discussion of open challenges and promising future directions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "ML for Regulatory Genomics"
- **Evidence pointer** Section "ML for Regulatory Genomics", location not provided
- **Concern** The description of one-hot encoding states that each nucleotide is replaced with a boolean vector of size 4. This is correct, but the manuscript does not mention that some implementations use additional channels for other features (e.g., conservation scores, mappability).
- **Required correction** Add a note that one-hot encoding can be extended with additional feature channels.

## Risk / unsupported claims
- The claim that gkm-SVM used "random genomic sequences" as negatives is not supported by the original methodology and appears inaccurate
- The reported DeepSEA AUROC range of 85-95% is not verifiable from the provided text and appears inconsistent with the original publication
- The statement that "the main limitation of CNN models lies in the difficulty to globally and objectively assess the importance of the extracted features" is presented as a general conclusion but is not supported by a systematic comparison of available methods
- The claim that "several recent studies highlighted the limitations of state-of-the-art approaches for predicting the effect of personal variants" is made without specific citations or discussion of the nature of these limitations
- The assertion that "the approach does not comply with a fundamental assumption in ML" regarding synthetic sequences is stated without precise reference to the statistical assumption being invoked
- The manuscript's claim to cover "a wide variety of models" is not fully supported given the omission of several important recent approaches
- The statement that "most of the promoter information for the control of mRNA expression likely lies in -1.5/+1.5 kb" is presented as a finding from the cited study but the manuscript does not discuss potential limitations or alternative interpretations of this result