## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and clarity of the presented review; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors review computational approaches for gene regulatory network (GRN) inference in developmental systems, arguing that progress in multi-omics integration, single-cell sequencing, and neural network models will substantially improve the accuracy and causal interpretability of inferred GRNs compared to traditional co-expression-based methods.
- **Visible evidence base** Abstract, Introduction, sections on multi-omics, single-cell sequencing, neural networks, Discussion, Perspectives, Competing Interests, Funding, Author Contributions
- **Missing materials affecting confidence** No figures, tables, or supplementary materials were provided; no reference list was provided; the Perspectives section is empty

## Reviewer
- **Overall assessment** This is a well-structured and readable review that covers three important methodological directions in GRN inference. The authors provide a balanced perspective, acknowledging both the promise and the current limitations of each approach. The manuscript is likely to be informative for researchers entering the field or seeking an overview of recent trends. However, the review would benefit from more critical depth in several areas, particularly in the evaluation of neural network interpretability and in the discussion of benchmarking standards. The absence of figures and references in the provided material limits a full assessment of the supporting evidence.
- **Who would be interested in the results, and why** Researchers in developmental biology, computational biology, and bioinformatics who use or plan to use GRN inference methods. The review provides a useful entry point for understanding the current methodological landscape and the rationale for adopting multi-omics and single-cell approaches. It may also be of interest to method developers seeking to position their work within the broader field.
- **Major strengths** The manuscript is clearly written and logically organized. The authors successfully synthesize a large body of work into three coherent themes. The discussion of the limitations of current approaches, such as the curse of dimensionality and the correlative nature of co-expression networks, is well articulated. The emphasis on the need for standardized benchmarking is a valuable contribution.
- **Major Concerns** The review would be strengthened by a more critical and detailed examination of the interpretability of neural network models in the context of GRN inference. The claim that ANNs will become commonplace is plausible but not deeply argued. The discussion of benchmarking, while important, could be more specific about the challenges and potential solutions. The statement that single-cell GRN methods are "barely any better than purely random models" is strong and would benefit from more context regarding the specific benchmarks and methods referenced.
- **Minor Comments** The manuscript would benefit from a brief explanation of what is meant by "context-specific GRNs" in the abstract. The transition from the multi-omics section to the single-cell section could be smoother. The Perspectives section is empty, which is a missed opportunity to provide a forward-looking synthesis.
- **Technical failings that need to be addressed before the case is established** None identified from the supplied material. The manuscript is a review and does not present new experimental data or a novel computational method that would require technical validation.
- **Assessment against Nature-style criteria** 
  - Originality: The review does not present a novel conceptual framework, but it does offer a useful synthesis of recent developments. Its originality lies in the specific combination of topics chosen.
  - Scientific importance: The topic is of high importance to a broad community of developmental and computational biologists. The review addresses a recognized need for more accurate and causal GRN models.
  - Interdisciplinary readership: The manuscript is likely to appeal to both experimental biologists and computational scientists, though the level of detail may be more accessible to the latter.
  - Technical soundness: The technical descriptions are generally accurate, but the review would benefit from more critical evaluation of the methods discussed, particularly regarding the limitations of neural network interpretability and the practical challenges of multi-omics integration.
  - Readability for nonspecialists: The manuscript is well-written and largely accessible, but some sections assume familiarity with computational concepts. A brief glossary or more introductory explanations would improve accessibility.
- **Recommendation posture** Supportive if the authors address the major concerns regarding critical depth and provide the missing materials (figures, references) for a complete assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Depth of analysis
- **Claim pointer** The authors state that neural networks are "extremely powerful GRN tools" and that they expect their adoption to become commonplace.
- **Evidence pointer** Section "Neural networks as flexible gene regulatory models", location not provided
- **Concern** The discussion of neural networks focuses primarily on their capacity to learn complex relationships without explicit specification. However, the review does not critically address the significant challenges of interpreting these models in a biological context. The "black box" concern is mentioned but dismissed as a "persistent misconception" without a detailed explanation of how interpretability can be achieved. The authors do not discuss specific techniques for extracting regulatory rules or identifying important features from trained networks, nor do they address the risk of overfitting and the need for extensive validation.
- **Why it matters** For a review aimed at guiding the field, it is crucial to provide a balanced view of the trade-offs between model flexibility and interpretability. If the authors advocate for the adoption of ANNs, they should equip the reader with a realistic understanding of the challenges involved in deriving biological insights from these models. Without this, the recommendation may be seen as overly optimistic.
- **Resolution test** The authors should expand the discussion to include specific examples of interpretability methods (e.g., saliency maps, attention mechanisms, or model distillation) and critically evaluate their applicability to GRN inference. They should also discuss the potential for ANNs to generate testable hypotheses and how these can be validated experimentally.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Evidence support
- **Claim pointer** The authors state that many single-cell GRN inference methods "fail to show consistent improvement over methods that were developed for bulk data, and are seemingly barely any better than purely random models."
- **Evidence pointer** Section "Single cell sequencing for cell type specific regulation", location not provided
- **Concern** This is a strong and potentially controversial claim. The authors do not provide specific details about which methods were compared, on which datasets, or under what evaluation metrics. Without this context, the statement is difficult to evaluate and could be misleading. It is also unclear whether this conclusion is based on a specific benchmark study or on a general impression from the literature.
- **Why it matters** This claim has significant implications for the field, as it suggests that a large body of recent methodological work has not delivered on its promise. If this is the authors' conclusion, they should provide the evidence to support it, allowing the reader to assess the validity of the claim and its generalizability.
- **Resolution test** The authors should cite specific benchmark studies (e.g., BEELINE or DREAM challenges) and summarize their findings in more detail. They should also discuss the potential reasons for the poor performance of single-cell methods, such as data sparsity or the difficulty of capturing dynamic processes from static snapshots.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "context-specific GRNs" is used without definition. It is unclear whether this refers to cell-type-specific, tissue-specific, or condition-specific networks.
- **Required correction** Briefly define the term in the abstract or in the introduction to avoid ambiguity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Structure
- **Affected element** Section "Multi-omics to capture gene regulation"
- **Evidence pointer** Section "Multi-omics to capture gene regulation", location not provided
- **Issue** The transition from the discussion of TF binding prediction to enhancer-promoter interactions is abrupt. The logical connection between these topics could be made more explicit.
- **Required correction** Add a sentence or two to explain how enhancer-promoter interactions build upon the earlier discussion of TF binding and chromatin accessibility to improve GRN inference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Perspectives section
- **Evidence pointer** Section "Perspectives", location not provided
- **Issue** The Perspectives section is empty. This is a missed opportunity to provide a forward-looking synthesis of the field and to highlight the most promising avenues for future research.
- **Required correction** Add a brief section that summarizes the authors' vision for the future of GRN inference, including the most important challenges and opportunities.

## Risk / unsupported claims
- The claim that single-cell GRN methods are "barely any better than purely random models" is not supported by specific evidence in the provided text.
- The claim that ANNs will become "commonplace" in GRN inference is presented as an expectation without a detailed argument for why this will occur.
- The statement that multi-omics approaches "will become dominant in all modalities of GRN inference approaches" is a strong prediction that is not fully justified by the evidence presented.
- The assertion that "the goal of GRN inference is to gain mechanistic insights, as opposed to getting an optimal benchmark score" is presented as a general truth but may not be universally accepted.