## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary information descriptions
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present a single-cell chromatin accessibility atlas of the developing human brain during the first trimester (6–13 weeks post-conception), integrating scATAC-seq and multiome data from 526,094 nuclei across 76 biological samples. They identify 135 clusters, link candidate cis-regulatory elements to gene expression, apply convolutional neural networks to predict transcription factor binding, and use GWAS integration to associate specific cell types with neuropsychiatric disease risk, particularly midbrain GABAergic neurons with major depressive disorder.
- **Visible evidence base** Abstract, main text sections (Atlas overview, Chromatin accessibility, Cis-regulatory element specificity, Enhancer logic, Purkinje neuron dynamics, GWAS polymorphisms), methods descriptions, figure legends (Figs 1–5), extended data figure descriptions, supplementary table descriptions
- **Missing materials affecting confidence** Actual figures and extended data figures not viewable; supplementary tables not accessible; detailed numerical results and statistical outputs not provided; code availability not verified; raw data not assessable

## Reviewer

- **Overall assessment** This manuscript presents a substantial and potentially valuable resource for the field of human neurodevelopment. The scale of data collection, integration of multiomic measurements, and the analytical approaches applied are commendable. The authors address an important gap by extending chromatin accessibility profiling to the entire developing brain during the first trimester, a period critical for neural patterning and cell type specification. The application of deep learning to predict regulatory syntax and the integration with GWAS data to identify disease-relevant cell types are innovative and timely. However, several methodological details and validations are not fully described in the provided text, and some claims appear to extend beyond what is directly demonstrated. The manuscript would benefit from clearer presentation of validation strategies, more explicit discussion of limitations, and additional evidence for some of the causal interpretations offered.

- **Who would be interested in the results, and why** Developmental neuroscientists studying human brain patterning and cell type specification would find this atlas directly relevant. Researchers in neuropsychiatric genetics, particularly those investigating the regulatory architecture underlying disorders such as major depressive disorder, schizophrenia, and autism spectrum disorder, would value the cell-type-specific chromatin accessibility maps and their integration with GWAS data. Computational biologists developing methods for single-cell epigenomics, deep learning approaches to regulatory genomics, and gene regulatory network inference would also be interested. Additionally, the resource aspect of this work, providing a comprehensive reference for first-trimester human brain chromatin accessibility, would be of broad utility to the neuroscience community.

- **Major strengths**
  1. The study addresses a significant gap by profiling chromatin accessibility across the entire developing human brain during the first trimester, a period not comprehensively covered by previous atlases.
  2. The integration of scATAC-seq and multiome data from a large number of nuclei (526,094) across multiple brain regions and developmental stages provides a rich resource.
  3. The application of a convolutional neural network to identify functional transcription factor binding sites and predict regulatory syntax is methodologically advanced and adds analytical depth.
  4. The linking of disease-associated SNPs to cell-type-specific cis-regulatory elements, with validation in an independent cohort, provides a compelling demonstration of the atlas's utility.
  5. The identification of midbrain GABAergic neurons as potentially vulnerable to MDD-related mutations offers a novel and testable hypothesis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "using a convolutional neural network, we identified putative functional transcription factor-binding sites in enhancers characterizing neuronal subtypes" and that this model was applied to ESRRB regulatory elements to "elucidate its activation mechanism in the Purkinje cell lineage."
- **Evidence pointer** Main text section "Enhancer logic in neuronal specification", Figure 3, Methods section "Supervised inference and stochastic simulation of Purkinje gene regulatory network"
- **Concern** The CNN approach is described at a high level, but critical details for assessing its validity are missing. The training and validation strategy is not fully described, including how overfitting was prevented, how the model's performance was evaluated beyond the reported AUC, and whether the model was tested on held-out chromosomes or cell types. The interpretation of contribution scores and seqlets as "functional" binding sites requires experimental validation or at least comparison with orthogonal data (e.g., ChIP-seq, footprinting). The application to ESRRB and the proposed two-step activation mechanism (TFAP2B then LHX5) is presented as a finding, but the evidence appears to be primarily computational. Without experimental validation or strong orthogonal support, the claim of "elucidating" the activation mechanism is overstated.
- **Why it matters** The CNN analysis is a central analytical component of the paper, and the ESRRB case study is presented as a demonstration of the method's utility. If the computational predictions are not rigorously validated, the conclusions drawn from this analysis, including the proposed regulatory mechanism, may not be reliable. The field requires clear standards for computational predictions of regulatory function, and this manuscript does not provide sufficient evidence to meet those standards.
- **Resolution test** Provide a detailed description of the CNN training and validation protocol, including data splitting, hyperparameter selection, and performance metrics on held-out data. Include experimental validation of at least a subset of predicted TF binding sites (e.g., electrophoretic mobility shift assay, luciferase reporter assays, or CRISPR perturbation) or demonstrate strong concordance with independent ChIP-seq or ATAC-seq footprinting data. For the ESRRB mechanism, provide additional evidence such as perturbation experiments in relevant cell models or demonstrate that the predicted regulatory logic is conserved across species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "by linking disease-associated single nucleotide polymorphisms to cis-regulatory elements, we validated putative pathogenic mechanisms in several diseases and identified midbrain-derived GABAergic neurons as being the most vulnerable to major depressive disorder-related mutations."
- **Evidence pointer** Main text section "Cell type specificity of GWAS polymorphisms", Figure 5, Supplementary Table 5
- **Concern** The GWAS integration analysis is a key translational component of the paper, but the description of the methodology and results is insufficient to evaluate the robustness of the findings. The specific LD score regression implementation, the choice of annotations, the handling of overlapping annotations, and the statistical thresholds are not fully described. The validation in a second cohort (FinnGen) is mentioned, but the results are only presented in a supplementary table without detailed discussion. The claim that midbrain GABAergic neurons are "the most vulnerable" to MDD-related mutations requires a clear comparison with other cell types and a discussion of effect sizes, not just significance. Additionally, the interpretation that "some broadly expressed genes associated with MDD contribute to disease when perturbed specifically in midbrain GABAergic neurons during early neurodevelopment" is a strong causal claim that goes beyond what association-based analyses can establish.
- **Why it matters** The GWAS integration is likely to be a major focus of interest for the broad readership of Nature. If the methodology is not transparent and the results are not robustly validated, the conclusions could mislead the field. The causal interpretation, in particular, needs to be tempered with appropriate caveats about the limitations of LD score regression and the distinction between association and causation.
- **Resolution test** Provide a complete description of the LD score regression analysis, including all parameters, covariates, and quality control steps. Present the full results of the validation cohort analysis in the main text or with sufficient detail in the supplement. Include a comprehensive comparison of effect sizes across cell types, not just significance levels. Revise the causal language to reflect the associative nature of the findings, or provide additional evidence (e.g., Mendelian randomization, functional validation in relevant cellular models) to support causal claims.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors describe the identification of "106,991 predicted enhancer–gene interactions for 16,267 genes and 59,069 accessible regions (henceforth, cCREs)" using a modified version of Cicero.
- **Evidence pointer** Main text section "Chromatin accessibility in the first trimester", Methods section "Gene expression imputation and cCREs"
- **Concern** The description of the modified Cicero approach is brief, and the validation of these predicted enhancer-gene interactions is not described. The accuracy of enhancer-gene linking is a known challenge in the field, and the authors do not provide evidence that their modifications improve upon existing methods. The downstream analyses, including the GWAS integration and the ESRRB case study, rely heavily on these cCRE predictions. If the enhancer-gene linking is inaccurate, the conclusions drawn from these analyses could be affected.
- **Why it matters** The cCRE predictions are a foundational resource presented in this paper. If they are not rigorously validated, their utility to the community is diminished, and the downstream biological conclusions may be compromised. The field needs confidence in the quality of predicted regulatory interactions, especially when they are used to interpret disease associations.
- **Resolution test** Provide a detailed description of the modified Cicero algorithm and the rationale for the modifications. Include validation of predicted enhancer-gene interactions using orthogonal approaches, such as Hi-C, eQTL colocalization, or CRISPR perturbation of a subset of predicted enhancers. Demonstrate that the predictions are robust to parameter choices and that they outperform or are comparable to existing methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the number of accessible regions increased both with age and along neuronal differentiation" and that "we observed a significant 10% increase in the number of accessible regions along the neuronal differentiation trajectory, but no significant increase in the glioblast lineage."
- **Evidence pointer** Main text section "Chromatin accessibility in the first trimester", Figure 2a, Extended Data Figure 4g
- **Concern** The statistical analysis supporting these claims is not fully described. The authors mention a linear regression for the age effect (coefficient 3,206; s.e. 634; t = 5.06; 6 d.f.), but the model specification, covariates, and handling of potential confounders (e.g., batch effects, brain region) are not detailed. The comparison between neuronal and glioblast lineages is presented as a binary outcome, but the statistical test used and the effect sizes are not reported. The biological interpretation of these differences is also not discussed in depth.
- **Why it matters** These findings about the dynamics of chromatin accessibility are presented as key observations of the atlas. If the statistical analysis is not rigorous, the conclusions about developmental trends may not be reliable. The comparison between lineages has implications for understanding the regulation of neurogenesis versus gliogenesis.
- **Resolution test** Provide a complete description of the statistical models used, including all covariates and model diagnostics. Report effect sizes and confidence intervals for the comparisons between lineages. Discuss potential confounders and how they were addressed. Consider whether the observed trends are consistent across brain regions and developmental stages.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and introduction
- **Evidence pointer** Abstract, first paragraph of main text
- **Issue** The abstract and introduction assume significant familiarity with single-cell genomics terminology and techniques. Terms such as "multiomic measurements," "candidate cis-regulatory elements," and "convolutional neural network" are used without brief explanations. While the target audience for Nature includes specialists, the broad readership would benefit from more accessible framing of the key concepts and their significance.
- **Required correction** Consider adding brief, plain-language explanations of key technical terms in the abstract or introduction. For example, "chromatin accessibility" could be described as "the degree to which DNA is physically accessible to regulatory proteins," and "cis-regulatory elements" as "DNA sequences that control the expression of nearby genes."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Sample collection"
- **Evidence pointer** Methods section "Sample collection"
- **Issue** The description of sample collection mentions that samples were obtained from "routine termination of pregnancies" and that "the timing was variable and based on expert annotation rather than knowledge of the date of conception." The potential impact of this variability on the developmental staging and the interpretation of age-related trends is not discussed in the main text.
- **Required correction** Add a brief discussion of how the variability in developmental staging might affect the interpretation of age-related changes in chromatin accessibility, and whether any sensitivity analyses were conducted to address this.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion focuses primarily on the MDN findings and the ESRRB case study. The broader implications of the atlas for understanding fundamental principles of human brain development, such as the relationship between chromatin accessibility and cell fate decisions, are not fully explored. The authors could strengthen the discussion by placing their findings in a wider context.
- **Required correction** Expand the discussion to consider how the atlas contributes to our understanding of the regulatory logic of human brain development, and how it compares to other species or model systems. Discuss potential future applications of the resource beyond the specific analyses presented.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "GWAS enrichment"
- **Evidence pointer** Methods section "GWAS enrichment"
- **Issue** The description of the GWAS enrichment analysis mentions that "we added accessible regions identified throughout development and adulthood to the background dataset to correct for our fetal neural-focused selection of features." The rationale for this approach and the potential limitations of using a background dataset from different developmental stages are not fully explained.
- **Required correction** Provide a more detailed explanation of the background dataset construction and the rationale for this approach. Discuss potential biases introduced by using a background from different developmental stages and how these were addressed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure legends
- **Evidence pointer** Figure 1 legend, Figure 3 legend
- **Issue** The figure legends are dense and technical, making it difficult for nonspecialists to understand the key messages of each figure. For example, the Figure 1 legend includes many abbreviations and technical terms without explanation.
- **Required correction** Consider simplifying figure legends and providing brief explanations of key terms and abbreviations. Highlight the main takeaway of each figure in plain language.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors do not discuss the limitations of their study in the main text, beyond a brief mention in the Methods. A more explicit discussion of limitations, such as the relatively small number of biological replicates, the potential for batch effects, and the challenges of validating computational predictions, would strengthen the manuscript.
- **Required correction** Add a paragraph in the Discussion acknowledging the limitations of the study and how they might affect the interpretation of the findings. Suggest directions for future work to address these limitations.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (CNN validation and ESRRB mechanism), R1-M2 (GWAS methodology and causal interpretation), R1-M3 (cCRE validation)

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript presents a novel resource, the first comprehensive single-cell chromatin accessibility atlas of the entire developing human brain during the first trimester. This fills a clear gap in the field, as previous studies focused primarily on the forebrain or later developmental stages. The integration of multiomic data and the application of deep learning approaches add originality to the work.
  - **Scientific importance**: The atlas has the potential to be a valuable community resource, enabling studies of gene regulation in early human brain development. The identification of midbrain GABAergic neurons as potentially vulnerable to MDD-related mutations is a significant finding that could have implications for understanding the neurodevelopmental origins of psychiatric disorders. However, the importance of the findings is somewhat diminished by the lack of experimental validation for key computational predictions.
  - **Interdisciplinary readership**: The work is likely to appeal to a broad audience, including developmental biologists, neuroscientists, geneticists, and computational biologists. The GWAS integration provides a direct link to psychiatric genetics, which is of interest to a wide clinical and research community. However, the technical complexity of the methods may limit accessibility for nonspecialists.
  - **Technical soundness**: The data generation and processing appear to follow established protocols, and the scale of the dataset is impressive. However, the lack of detailed methodological descriptions and validation for the CNN and GWAS analyses raises concerns about the robustness of the conclusions. The cCRE predictions, which are central to the downstream analyses, are not validated against orthogonal data.
  - **Readability for nonspecialists**: The manuscript is written in a technical style that assumes significant expertise in genomics and computational biology. While this is common for Nature papers, the authors could improve accessibility by providing more context and explanation of key concepts for a broader readership.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially valuable resource and several interesting findings, but the lack of methodological detail and validation for key computational analyses prevents full assessment of the claims. The authors should address the major concerns outlined above, particularly the validation of the CNN predictions and the GWAS methodology, before the case is fully established.

## Risk / unsupported claims
- The claim that the CNN identified "putative functional transcription factor-binding sites" is not supported by experimental validation or strong orthogonal evidence.
- The claim that the ESRRB activation mechanism is "elucidated" is overstated given the computational nature of the analysis.
- The claim that midbrain GABAergic neurons are "the most vulnerable" to MDD-related mutations is not fully supported by the presented statistical comparisons.
- The causal interpretation that "some broadly expressed genes associated with MDD contribute to disease when perturbed specifically in midbrain GABAergic neurons during early neurodevelopment" goes beyond what association-based analyses can establish.
- The accuracy and biological relevance of the 106,991 predicted enhancer-gene interactions are not validated.
- The statistical analysis supporting the claim that "the number of accessible regions increased both with age and along neuronal differentiation" is not fully described, making the claim difficult to evaluate.