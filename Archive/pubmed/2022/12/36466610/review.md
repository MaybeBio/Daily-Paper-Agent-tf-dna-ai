## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical accuracy, completeness of coverage, and alignment with stated aims of the review
- **Shared manuscript claim summary** The authors present a narrative review of deep learning methods for prioritizing noncoding genetic variants in neurodegenerative diseases, with emphasis on Alzheimer's disease. They organize methods by genomic target (transcription factor binding, chromatin accessibility, gene expression, 3D chromatin interactions), discuss model interpretability, and outline challenges and future directions.
- **Visible evidence base** Full text of the manuscript, including abstract, introduction, sections on deep learning architectures, genomic applications, machine learning in neurodegeneration, limitations, and discussion. No figures or tables were provided in the submitted material.
- **Missing materials affecting confidence** Figures (referenced as Figure 1 and Figure 2) and Table 1 were not included. This limits assessment of the pedagogical value of the visual aids and the completeness of the interpretability methods summary.

## Reviewer
- **Overall assessment** This is a well-written, clearly organized narrative review that serves as a useful entry point for researchers interested in applying deep learning to noncoding variant prioritization in neurodegeneration. The authors demonstrate familiarity with both the deep learning genomics literature and the specific challenges of neurodegenerative disease genetics. The review is accessible and logically structured. However, the scope is broad and the treatment of several topics is shallow, with some important recent methods and benchmarking efforts omitted. The review would benefit from a more critical comparative analysis of the methods discussed, rather than a largely descriptive catalog. The absence of figures and tables in the submitted material limits full evaluation, but the text alone supports a moderate assessment of value.
- **Who would be interested in the results, and why** Researchers in neurogenomics, computational genomics, and bioinformatics who are seeking an overview of deep learning tools applicable to noncoding variant prioritization. Clinicians or geneticists with an interest in the functional interpretation of GWAS loci in Alzheimer's and other neurodegenerative diseases may also find the review useful as a conceptual introduction. The review is likely most valuable to newcomers to the field rather than experts, who may already be familiar with most of the methods discussed.
- **Major strengths**  
  1. Clear organization by genomic target, which helps readers navigate a complex and rapidly evolving literature.  
  2. Accessible explanations of deep learning concepts (e.g., CNNs, RNNs, transfer learning, interpretability methods) for a non-specialist audience.  
  3. Good integration of disease-specific context, particularly the discussion of cell type specificity in the brain and the use of functional genomics data.  
  4. The discussion of validation strategies, including MPRA and base editing, is a valuable and practical addition.  
  5. The authors are appropriately cautious about the limitations of current methods and the need for experimental validation.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Completeness of coverage  
  - **Claim pointer** The review claims to present "the current state-of-the-art DL methods" for variant effect prediction and to "clearly represent the benefits and drawbacks of each given approach."  
  - **Evidence pointer** Sections "Transcription factor binding and chromatin accessibility", "Gene expression", "3D chromatin interactions"  
  - **Concern** The review omits several influential and widely used deep learning models for variant effect prediction, including Enformer is discussed, but other important tools such as SpliceAI is mentioned only briefly, and models like DeepVariant, PrimateAI is mentioned, but others such as CADD, Eigen, and FATHMM are not discussed. More critically, the review does not mention recent benchmarking studies (e.g., the CAGI variant effect prediction challenges) that systematically compare the performance of these methods. The claim of presenting the "state-of-the-art" is therefore overstated.  
  - **Why it matters** A review that claims to cover the state of the art but omits key methods and comparative benchmarks may mislead readers about the relative strengths and weaknesses of available tools, which is precisely the information a reader would seek from such a review.  
  - **Resolution test** The authors should either expand the scope to include a more comprehensive set of methods and benchmarking results, or temper the claim to "a selection of representative methods" and explicitly acknowledge the omission of others.
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Critical analysis  
  - **Claim pointer** The review states that "DL algorithms are particularly well-suited for this 'variant effect prediction' task because they are computational representations of the biological relationship between a DNA sequence and its genomic features."  
  - **Evidence pointer** Sections "Deep learning", "Genomic applications of deep learning"  
  - **Concern** The review is largely descriptive and does not critically evaluate the assumptions underlying deep learning approaches to variant effect prediction. For example, the issue of training data bias (e.g., the use of regulatory annotations as proxies for functional effect), the limited portability of models across cell types and tissues, and the challenge of interpreting model predictions in a biologically meaningful way are mentioned but not deeply examined. The review also does not discuss the risk of circularity when models are trained and evaluated on the same types of genomic annotations.  
  - **Why it matters** A review that does not critically interrogate the foundational assumptions of the methods it describes may give readers an overly optimistic view of their reliability and applicability, which is particularly problematic in a clinical or translational context.  
  - **Resolution test** The authors should add a section or expand existing discussion to critically evaluate the limitations and potential pitfalls of deep learning approaches, including training data biases, model transferability, and the interpretability of predictions.
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Depth of treatment  
  - **Claim pointer** The review claims to "organize and discuss the many unique model architectures, development philosophies, and interpretation methods that have emerged in the last few years."  
  - **Evidence pointer** Sections "Deep learning architectures", "Model interpretability"  
  - **Concern** The treatment of individual methods is often superficial. For example, the discussion of Enformer is limited to a few sentences, and the description of its architecture and training is insufficient for a reader to understand what distinguishes it from earlier models. Similarly, the discussion of interpretability methods (e.g., DeepLIFT, DeepSHAP, TF-MoDISco) is brief and does not explain the mathematical or conceptual differences between them. The review would benefit from a more detailed comparison of at least a few key methods, including their architectural innovations, training data, and performance characteristics.  
  - **Why it matters** A review that aims to help readers choose among methods must provide sufficient detail for them to understand the trade-offs. A superficial treatment may leave readers unable to make informed decisions.  
  - **Resolution test** The authors should expand the discussion of at least 3-4 key methods, providing more detail on architecture, training data, performance, and limitations, and include a comparative table if possible.
  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Reproducibility and practical guidance  
  - **Claim pointer** The review discusses "the future of the field" and suggests that deep learning methods "could serve as a supplementary analytical platform to traditional genomic techniques."  
  - **Evidence pointer** Sections "Current limitations and future directions", "Discussion"  
  - **Concern** The review does not provide practical guidance for researchers who wish to apply the methods discussed. There is no discussion of software availability, computational requirements, recommended workflows, or common pitfalls in applying these models to new datasets. The mention of the Kipoi repository is useful but brief.  
  - **Why it matters** For a review aimed at encouraging adoption of deep learning methods in neurodegeneration research, practical guidance is essential. Without it, readers may be discouraged by the perceived complexity or may apply methods incorrectly.  
  - **Resolution test** The authors should add a section on practical considerations, including software tools, computational resources, data requirements, and step-by-step guidance for applying deep learning models to variant prioritization.
- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract  
  - **Evidence pointer** Abstract  
  - **Issue** The abstract is dense and could benefit from a clearer statement of the review's scope and intended audience.  
  - **Required correction** Consider adding a sentence that explicitly states the review is intended for researchers in neurodegeneration who are new to deep learning, and that it focuses on methods applicable to noncoding variant prioritization.
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** Section "Deep learning architectures"  
  - **Evidence pointer** Section "Deep learning architectures"  
  - **Issue** The term "Residual Neural Networks (RNNs)" is used, but the standard abbreviation for Residual Networks is ResNet, and RNN typically refers to Recurrent Neural Networks. This could cause confusion.  
  - **Required correction** Use "Residual Networks (ResNets)" and "Recurrent Neural Networks (RNNs)" to avoid ambiguity.
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Section "Machine learning in neurodegenerative disease genomics research"  
  - **Evidence pointer** Section "Machine learning in neurodegenerative disease genomics research"  
  - **Issue** The discussion of existing applications in neurodegeneration is brief and focuses on a few examples. A more comprehensive survey of the current literature would strengthen the review.  
  - **Required correction** Consider adding a table summarizing key studies that have applied deep learning to variant prioritization in neurodegenerative diseases, including the model used, the data, and the main findings.
  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** References  
  - **Affected element** Reference list  
  - **Evidence pointer** Reference list  
  - **Issue** Some references are cited in the text but not listed in the reference list, and vice versa. This is likely an editorial issue but should be checked.  
  - **Required correction** Ensure all citations in the text appear in the reference list and that all listed references are cited in the text.
  - **Concern ID** R1-m5  
  - **Severity** Minor  
  - **Axis** Figures  
  - **Affected element** Figures 1 and 2, Table 1  
  - **Evidence pointer** Figures 1 and 2, Table 1  
  - **Issue** Figures and tables were not provided in the submitted material, so their content and quality cannot be assessed.  
  - **Required correction** Ensure figures and tables are included in the final submission and that they are clearly labeled and referenced in the text.
- **Technical failings that need to be addressed before the case is established**  
  No technical failings that invalidate the core content of the review were identified. The manuscript is a narrative review, not a primary research article, so the standards for technical validation differ. However, the omissions noted in R1-M1 and the lack of critical analysis noted in R1-M2 should be addressed to strengthen the review's utility.
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The review does not present new data or a novel framework, but it does organize existing literature in a way that may be useful to newcomers. The focus on neurodegenerative diseases, particularly Alzheimer's, is a distinguishing feature, but the underlying methods are well established in the broader genomics community.  
  - **Scientific importance** Moderate. The topic is important, as noncoding variant interpretation is a major bottleneck in neurogenomics. However, the review does not provide new insights or a critical synthesis that would elevate its importance beyond a general overview.  
  - **Interdisciplinary readership** Moderate. The review is accessible to researchers in neurodegeneration who are not computational specialists, which is a strength. However, the depth of coverage may be insufficient for computational readers seeking technical detail.  
  - **Technical soundness** The technical content is accurate as far as it goes, but the review is incomplete in its coverage of the field and does not critically evaluate the methods discussed. This limits its technical soundness as a comprehensive resource.  
  - **Readability for nonspecialists** Good. The writing is clear and the organization is logical. The explanations of deep learning concepts are accessible, though some sections could benefit from additional detail.
- **Recommendation posture** Supportive if technical concerns are resolved. The review has value as an accessible introduction to deep learning for noncoding variant prioritization in neurodegeneration, but it requires expansion and critical refinement to fully meet its stated aims. The authors should address the concerns regarding completeness, critical analysis, and practical guidance before the manuscript can be considered a definitive resource.

## Risk / unsupported claims
- The claim that the review presents "the current state-of-the-art DL methods" is not fully supported, as several important methods and benchmarking studies are omitted.
- The claim that deep learning models are "computational representations of the biological relationship between a DNA sequence and its genomic features" is an oversimplification that is not critically examined.
- The statement that "the eventual integration of DL methods will be crucial" for studying noncoding variant effects is an opinion that is not supported by evidence presented in the review.
- The assertion that "all of the lessons learned from the disease-independent DL genomics methods developed in the last few years can be applied to AD-specific data and use cases" is plausible but not critically evaluated, and the review does not discuss potential barriers to such transfer.