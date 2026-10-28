## Review setup
- **Input scope** Full manuscript text (abstract, introduction, main sections, discussion, author contributions, conflict of interest, publisher's note, acknowledgements)
- **Assessment boundary** Scientific content, technical soundness, completeness of the review as a scholarly contribution, and alignment with stated aims. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The manuscript is a review article that surveys computational models for predicting functional effects of noncoding genetic variants from DNA sequences, covering traditional annotation-based methods, deep learning approaches, and foundation models. It argues that de novo prediction from sequence alone, enabled by context-specific molecular data, represents a key advance over population-based association studies, and it identifies remaining challenges including single-cell resolution and reference-genome bias.
- **Visible evidence base** Full text of the review, including one figure (Figure 1, referenced but not shown), one table (Table 1, referenced but not shown), and citations to primary literature. No supplementary materials were provided.
- **Missing materials affecting confidence** Figure 1 and Table 1 are referenced in the text but were not included in the supplied material. Their absence limits assessment of how effectively the visual summary and comparative table support the narrative. No reference list was provided, so citation accuracy and completeness cannot be verified.

## Reviewer
- **Overall assessment** This is a competent and readable narrative review of a fast-moving field. The authors organize the material into a logical progression from annotation-based methods to deep learning to foundation models, and they make a reasonable case for the importance of de novo sequence-based prediction. The discussion of cross-species training and long-range regulatory effects is a useful addition. However, the review is largely descriptive rather than critical. It does not offer a comparative evaluation of model performance, does not discuss limitations of the cited methods in sufficient depth, and does not articulate a clear forward-looking research agenda beyond general statements. The absence of Figure 1 and Table 1 from the supplied material makes it impossible to assess whether these elements add substantive value. The manuscript would benefit from a more analytical stance, including explicit criteria for comparing methods and a more concrete discussion of validation standards in this field.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and human genetics who seek a concise entry point into sequence-based variant effect prediction. The review may also be useful for graduate students or newcomers to the field who need an overview of the model landscape. Practitioners already familiar with the primary literature are unlikely to find new insights, as the review does not provide a critical synthesis or quantitative comparison.
- **Major strengths** The manuscript is clearly written and well organized. The progression from traditional methods to deep learning to foundation models is logical and easy to follow. The authors correctly identify key limitations of GWAS and QTL approaches, and they make a sound argument for why sequence-based de novo prediction is an important complement. The discussion of cross-species training and the limitations of CNN receptive fields is a valuable contribution. The treatment of foundation models, including DNABERT, Nucleotide Transformer, and HyenaDNA, is current and appropriately highlights the shift toward self-supervised learning.
- **Major Concerns** The review lacks critical depth. It describes what models do but does not systematically compare their performance, discuss their failure modes, or evaluate the evidence for their claims. The section on foundation models is particularly descriptive, with little discussion of what these models actually learn, how their representations are validated, or whether their performance gains over supervised models are consistent across tasks. The discussion section identifies two challenges but does not propose concrete solutions or a research agenda. The absence of Figure 1 and Table 1 from the supplied material is a significant gap, as these are likely intended to provide the comparative and structural overview that the text lacks.
- **Minor Comments** The abstract is somewhat dense and could be more accessible to nonspecialists. The introduction could benefit from a clearer statement of the review's scope and criteria for including or excluding specific models. The section on cross-species training is interesting but underdeveloped; the authors could have discussed specific examples of cross-species transfer in more detail. The discussion of CRISPR as a validation tool is brief and could be expanded to address how such data might be integrated into model training or evaluation.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide a quantitative or systematic comparison of the methods it reviews. Claims about the superiority of deep learning or foundation models are made without supporting benchmarks or references to comparative studies. The review also does not address the issue of model interpretability in sufficient depth, which is a major concern for clinical or biological applications. The absence of Figure 1 and Table 1 means that the structural and comparative elements of the review cannot be evaluated.
- **Assessment against Nature-style criteria** Originality: The review covers recent developments but does not offer a novel framework or perspective. Its organization is standard for the field. Scientific importance: The topic is important, and the review may serve as a useful introduction, but it does not advance the field's understanding or provide a critical synthesis. Interdisciplinary readership: The manuscript is likely accessible to computational biologists and geneticists, but may be less so to experimental biologists or clinicians due to the density of technical terms. Technical soundness: The descriptions of model architectures are generally accurate, but the lack of comparative analysis and validation discussion weakens the technical contribution. Readability for nonspecialists: The writing is clear but assumes familiarity with genomics and machine learning concepts. Overall, the manuscript is a reasonable review for a specialized audience but does not meet the bar for a high-impact general journal.
- **Recommendation posture** Supportive if technical concerns are resolved. The review has merit as a survey, but it needs to be more critical and comparative. The authors should add a systematic comparison of model performance, discuss limitations and failure modes, and provide a more concrete research agenda. The missing Figure 1 and Table 1 must be provided for assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The review claims to provide a "systematic overview" of models for variant effect prediction, implying a comprehensive and critical treatment.
- **Evidence pointer** Abstract; Introduction; Sections "De novo prediction of genetic variants' effects based on deep learning" and "General sequence grammar of variants learned by foundation models"
- **Concern** The review is descriptive rather than systematic. It does not compare models on common benchmarks, does not report quantitative performance metrics, and does not discuss the conditions under which one model might be preferred over another. For example, the transition from DeepSEA and Basset to Basenji and Enformer is presented as a natural progression, but the authors do not discuss whether the increased complexity of Enformer is justified by improved performance, nor do they address the computational costs or practical usability of these models. The section on foundation models is similarly uncritical, presenting DNABERT, Nucleotide Transformer, and HyenaDNA as advances without discussing their relative strengths or the evidence for their superiority.
- **Why it matters** A review that does not critically evaluate the methods it describes cannot help readers make informed choices about which model to use for a given task. The field is moving quickly, and a purely descriptive survey risks becoming outdated quickly without providing analytical value.
- **Resolution test** The authors should add a comparative table or section that evaluates models on common tasks, reports performance metrics where available, and discusses the trade-offs between model complexity, interpretability, and accuracy. They should also cite and discuss any existing benchmark studies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The review states that de novo prediction of functional effects is "pivotal for enhancing our comprehension of transcriptional regulation and its disruptions caused by the plethora of noncoding genetic variants linked to human diseases and traits."
- **Evidence pointer** Abstract; Discussion
- **Concern** The review does not provide evidence for this claim. It does not discuss specific examples where de novo prediction has led to biological insights or clinical applications that would not have been possible with other approaches. The discussion of challenges is general and does not address the question of whether these models have actually delivered on their promise. For example, the authors mention that models are trained on reference genomes and may not capture diversity, but they do not discuss the extent to which this has been shown to affect predictions in practice.
- **Why it matters** The central claim of the review is that de novo prediction is important, but the review does not substantiate this with concrete examples or evidence. Without this, the review risks being a summary of methods without a clear argument for why they matter.
- **Resolution test** The authors should include specific case studies or examples where de novo prediction has been validated experimentally or has provided insights into disease mechanisms. They should also discuss the limitations of current validation approaches and what would be needed to establish clinical utility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The review claims to cover "the state-of-the-art models and algorithms for genetic variant effect predictions, including traditional sequence-based models, Deep Learning models, and the cutting-edge Foundation Models."
- **Evidence pointer** Abstract; Table 1 (referenced but not provided)
- **Concern** The review does not discuss several important classes of methods, including those that integrate evolutionary conservation across species (e.g., phyloP, GERP), those that use regulatory annotations from ENCODE/Roadmap in a more integrated fashion (e.g., Eigen, CADD), and those that use Bayesian or probabilistic approaches. The focus is heavily on deep learning and foundation models, which is understandable given the title, but the claim of a "systematic overview" is not fully supported. The absence of Table 1 from the supplied material makes it impossible to assess whether the table fills this gap.
- **Why it matters** Readers may come away with an incomplete picture of the field. A review that claims to be systematic should either cover the full range of methods or clearly state its scope and criteria for inclusion.
- **Resolution test** The authors should either expand the coverage to include other classes of methods or revise the claim to be more specific about the scope. The table, if provided, should clearly indicate the criteria for inclusion and the relationships between methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The review states that "the model's attention weights offer greater interpretability, shedding light on the underlying mechanisms of chromatin and gene regulation" in the context of Enformer.
- **Evidence pointer** Section "Cross-species regulatory information and long-range variant effects"
- **Concern** This claim is not supported by evidence. While attention weights can be inspected, their interpretability is a subject of ongoing debate in the machine learning community. The authors do not provide examples of how attention weights from Enformer have been used to gain biological insights, nor do they discuss the limitations of attention-based interpretability. The claim as stated is overly strong and not substantiated.
- **Why it matters** Overstating the interpretability of deep learning models can mislead readers about the current state of the field and the reliability of model-based insights.
- **Resolution test** The authors should either provide specific examples of interpretability analyses using Enformer or similar models, or soften the claim to reflect the current understanding of attention-based interpretability.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses technical terms without definition, which may limit accessibility for nonspecialist readers.
- **Required correction** Consider revising the abstract to include brief definitions or context for terms such as "context-specific molecular information" and "foundation models."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction does not clearly state the criteria for selecting the models discussed in the review, nor does it explain why certain models are excluded.
- **Required correction** Add a sentence or two in the introduction that describes the scope and selection criteria for the models covered.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section "De novo prediction of genetic variants' effects based on deep learning"
- **Evidence pointer** Section "De novo prediction of genetic variants' effects based on deep learning"
- **Issue** The description of the one-hot encoding and the input representation S∈R4×L is correct but could be clearer for readers unfamiliar with the notation.
- **Required correction** Consider adding a brief explanation of the notation or a simple example to aid comprehension.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of single-cell data is brief and does not address the specific challenges of applying sequence-based models to single-cell data, such as data sparsity and batch effects.
- **Required correction** Expand this section to discuss these challenges in more detail and suggest potential approaches.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Cross-species regulatory information and long-range variant effects"
- **Evidence pointer** Section "Cross-species regulatory information and long-range variant effects"
- **Issue** The transition from the discussion of cross-species training to the limitations of CNNs is abrupt and could be smoother.
- **Required correction** Add a connecting sentence or two to improve the flow of the narrative.

## Risk / unsupported claims
- The claim that "the model's attention weights offer greater interpretability" (R1-M4) is not supported by evidence in the text.
- The claim that de novo prediction is "pivotal" for understanding transcriptional regulation and disease is asserted but not substantiated with specific examples (R1-M2).
- The review's claim to be a "systematic overview" is not fully supported by the content, as several important classes of methods are not discussed (R1-M3).
- The absence of Figure 1 and Table 1 from the supplied material means that any claims relying on these elements cannot be assessed.