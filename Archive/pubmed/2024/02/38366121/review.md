## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, logical coherence, and support for claims presented in this review article
- **Shared manuscript claim summary** This review synthesizes recent systems biology studies on nitrogen sensing and signaling in plants, emphasizing temporal dynamics (e.g., Michaelis-Menten kinetics of transcriptional responses, NLP7 as a nitrate sensor, "hit-and-run" transcription) and spatial dynamics (cell type-specific responses, root-to-shoot communication). It also discusses emerging technologies (single-cell sequencing, machine learning, AI) and translational potential for improving nitrogen use efficiency in crops.
- **Visible evidence base** Full text of the review, including abstract, introduction, sections on temporal and spatial nitrogen responses, single-cell analysis, model-to-crop translation, AI applications, conclusions, author contributions, and funding
- **Missing materials affecting confidence** Figures and tables referenced in the text (Figures 1-5, Tables 1-3) were not provided. Specific data values, experimental details, and statistical analyses from primary studies cited are not available for verification.

## Reviewer
- **Overall assessment** This is a well-written and comprehensive review that effectively integrates temporal and spatial perspectives on nitrogen sensing and signaling in plants. The authors are clearly experts in the field, and the review provides a valuable synthesis of recent systems biology approaches. The organization is logical, progressing from foundational concepts to emerging technologies and translational applications. The review is likely to be of significant interest to plant biologists, particularly those studying nutrient signaling, systems biology, and crop improvement. However, the review would be strengthened by more critical evaluation of the methods discussed, clearer articulation of outstanding questions and challenges, and more explicit connections between the temporal and spatial themes. The absence of figures and tables limits full assessment of the illustrative content.
- **Who would be interested in the results, and why** Plant molecular biologists, systems biologists, and crop scientists interested in nitrogen metabolism, nutrient signaling, gene regulatory networks, and translational approaches to improve nitrogen use efficiency. The review's coverage of single-cell technologies and AI applications will also appeal to researchers interested in emerging computational and experimental methods in plant biology.
- **Major strengths** 1) Comprehensive and up-to-date synthesis of recent systems biology studies on nitrogen signaling, with a clear focus on temporal and spatial dimensions. 2) Effective integration of diverse methodologies, from classic kinetic modeling to cutting-edge single-cell and AI approaches. 3) Clear articulation of translational potential for improving nitrogen use efficiency, with societal and environmental relevance. 4) Well-structured narrative that guides the reader through complex topics. 5) Appropriate acknowledgment of limitations and future directions in several sections.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific rigor and critical evaluation
  - **Claim pointer** The review presents single-cell RNA-seq and related approaches as promising tools for understanding nitrogen responses, but does not critically evaluate their limitations or challenges in this context.
  - **Evidence pointer** Section "New aspects of N-response in time and space: single-cell analysis"
  - **Concern** The section on single-cell analysis is largely aspirational and descriptive, highlighting potential applications without adequately addressing technical challenges such as data sparsity, cell type annotation difficulties, batch effects, and the challenge of capturing transient nitrogen responses in single-cell snapshots. The authors mention that scRNA-seq data are "highly sparse due to cell dropouts" but do not discuss how this affects the reliability of trajectory inference or pseudotime analysis for nitrogen-responsive genes. Additionally, the review does not address whether current single-cell protocols are sensitive enough to detect rapid (minutes-scale) transcriptional changes induced by nitrate, which is a central theme of the temporal aspects discussed earlier.
  - **Why it matters** For a review aimed at guiding future research, a balanced assessment of methodological strengths and limitations is essential. Overly optimistic presentation of emerging technologies without critical evaluation may mislead readers, particularly early-career researchers, about the current state of the field and the practical challenges of implementing these approaches.
  - **Resolution test** The authors should add a critical discussion of the challenges and limitations of single-cell approaches for studying nitrogen responses, including technical considerations (e.g., sensitivity, throughput, cost) and analytical challenges (e.g., trajectory inference assumptions, validation of predicted regulatory relationships). They should also suggest potential solutions or alternative approaches where appropriate.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Coherence and integration of themes
  - **Claim pointer** The review's central thesis is that nitrogen sensing and signaling operate across "time and space," but the integration of these two dimensions is not consistently maintained throughout.
  - **Evidence pointer** Overall manuscript structure
  - **Concern** While the title and introduction emphasize the importance of both temporal and spatial dimensions, the sections on temporal aspects (Michaelis-Menten kinetics, NLP7 dynamics, hit-and-run) and spatial aspects (cell type-specific responses, root-to-shoot communication) are largely presented as separate topics. The review would benefit from more explicit discussion of how temporal and spatial dynamics interact. For example, how do cell type-specific differences in nitrate sensing kinetics contribute to organ-level coordination? How does the timing of root-to-shoot signaling relate to local cellular responses? The conclusion touches on this integration but does not develop it in depth.
  - **Why it matters** The stated novelty of this review is its focus on both time and space as integrated dimensions of nitrogen signaling. If these themes are not explicitly integrated, the review risks reading as two separate reviews combined into one, which weakens its conceptual contribution to the field.
  - **Resolution test** The authors should add explicit discussion of how temporal and spatial dynamics are interconnected, perhaps through specific examples or a dedicated section. For instance, they could discuss how the timing of nitrate responses in different cell types contributes to coordinated root development, or how systemic signals integrate temporal information across organs.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Completeness and balance of coverage
  - **Claim pointer** The review focuses heavily on Arabidopsis and briefly discusses crops, but the coverage of crop nitrogen signaling is uneven and somewhat superficial.
  - **Evidence pointer** Section "Model-to-crop: nitrogen sensing and signaling and its impact on agricultural outcomes"
  - **Concern** The model-to-crop section provides useful examples of cross-species comparisons and translational approaches, but it is relatively brief compared to the Arabidopsis-focused sections. The discussion of crop studies is somewhat cursory, with limited depth on the specific challenges and opportunities in crop systems. For example, the review mentions maize and rice studies but does not discuss the complexity of polyploid genomes, the challenges of field-based phenotyping, or the regulatory and economic barriers to translating fundamental knowledge into improved crop varieties. The section on microbial interactions and nitrogen fixation is also brief and could benefit from more detailed discussion of recent advances and remaining challenges.
  - **Why it matters** Given the review's stated goal of addressing agricultural outcomes and nitrogen use efficiency, a more thorough and critical treatment of the crop translation aspect would strengthen the review's practical relevance and impact. The current treatment may leave readers with an incomplete understanding of the gap between fundamental research and agricultural application.
  - **Resolution test** The authors should expand the model-to-crop section with more detailed discussion of specific crop studies, the challenges of translating Arabidopsis findings to crops, and the current state of efforts to improve nitrogen use efficiency in major crop species. They should also address the limitations of current approaches and propose concrete strategies for overcoming these barriers.
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific rigor and critical evaluation
  - **Claim pointer** The review discusses the role of NLP7 as a nitrate sensor and master regulator, but does not critically evaluate the evidence for this claim or discuss alternative interpretations.
  - **Evidence pointer** Section "Time- and space-dependent modes of action for NLP7 as a master regulator of nitrate signaling"
  - **Concern** The review presents NLP7 as a nitrate sensor based on the sCiNiS biosensor study, but does not discuss potential caveats or alternative interpretations. For example, the physiological relevance of NLP7's nitrate-binding affinity relative to ambient nitrate concentrations in plant tissues is not addressed. The review also does not discuss whether other NLP family members or proteins might have redundant or complementary sensing functions. Additionally, the relationship between NLP7's role as a sensor and its established role as a transcription factor is not fully explored, particularly regarding how nitrate binding relates to transcriptional activation.
  - **Why it matters** The claim that NLP7 acts as a nitrate sensor is a significant recent finding with implications for understanding plant nitrogen sensing. A critical review should evaluate the strength of the evidence and discuss alternative interpretations or unresolved questions, particularly given the importance of this claim for the field.
  - **Resolution test** The authors should add a more critical discussion of the evidence for NLP7 as a nitrate sensor, including consideration of binding affinity, physiological relevance, potential redundancy with other sensors, and the relationship between sensing and transcriptional regulation. They should also acknowledge any controversies or unresolved questions in this area.
  
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific rigor and critical evaluation
  - **Claim pointer** The review discusses the application of machine learning and AI to nitrogen research, but the treatment is largely descriptive and lacks critical evaluation of these approaches.
  - **Evidence pointer** Section "Nitrogen research in the age of artificial intelligence (AI)"
  - **Concern** The AI section provides a general overview of AI applications in biology and agriculture but does not critically evaluate the specific challenges and limitations of applying these methods to nitrogen signaling research. For example, the review does not discuss issues of data quality and standardization, the interpretability of deep learning models, the risk of overfitting in small biological datasets, or the need for experimental validation of AI-generated predictions. The section also does not provide concrete examples of how AI has been successfully applied to nitrogen research specifically, beyond general statements about image analysis for nitrogen content assessment.
  - **Why it matters** As AI becomes increasingly prominent in biological research, it is important for reviews to provide balanced guidance on when and how these methods can be effectively applied. A purely descriptive treatment may lead readers to overestimate the current capabilities of AI in this domain or underestimate the challenges involved.
  - **Resolution test** The authors should add a more critical discussion of the challenges and limitations of AI approaches in nitrogen research, including specific examples of successful applications and lessons learned. They should also discuss the importance of experimental validation and the need for high-quality training data.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Introduction
  - **Evidence pointer** Introduction section
  - **Issue** The introduction references the Michaelis-Menten paper from 1913 and its relevance to nitrogen research, but the connection between enzyme kinetics and transcriptional responses could be explained more clearly for readers unfamiliar with this analogy.
  - **Required correction** Consider adding a brief explanation of how Michaelis-Menten kinetics can be applied to transcriptional responses, perhaps with a simple analogy or example, to make this conceptual link more accessible to a broad readership.
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section on temporal nitrogen responses
  - **Evidence pointer** Section "Nitrogen dose sensing as a function of time"
  - **Issue** The section discusses the finding that 30% of nitrogen-responsive genes follow Michaelis-Menten kinetics, but does not discuss what distinguishes these genes from the remaining 70% or whether there are common features among the Michaelis-Menten responsive genes.
  - **Required correction** Consider adding a brief discussion of the characteristics of Michaelis-Menten responsive genes versus non-Michaelis-Menten responsive genes, if such information is available from the cited studies.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Section on NLP7
  - **Evidence pointer** Section "Time- and space-dependent modes of action for NLP7"
  - **Issue** The description of the "hit-and-run" model could be clearer for readers not familiar with this concept. The current explanation assumes prior knowledge of transcription factor dynamics.
  - **Required correction** Consider providing a more explicit definition of the "hit-and-run" model early in the section, perhaps with a brief analogy or schematic description, to ensure all readers can follow the subsequent discussion.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section on cell type-specific responses
  - **Evidence pointer** Section "The dynamics of nitrogen responses in specific cell types"
  - **Issue** The section discusses cell type-specific responses in roots but does not mention any cell type-specific studies in shoots, despite the review's emphasis on spatial dynamics across organs.
  - **Required correction** Consider adding a brief discussion of cell type-specific nitrogen responses in shoots, or explicitly state if such studies have not yet been conducted, to provide a more complete picture of spatial dynamics.
  
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Section on single-cell analysis
  - **Evidence pointer** Section "New aspects of N-response in time and space: single-cell analysis"
  - **Issue** The section discusses trajectory inference and pseudotime analysis but does not explain these concepts for readers unfamiliar with single-cell bioinformatics approaches.
  - **Required correction** Consider adding brief definitions or explanations of trajectory inference and pseudotime analysis, perhaps in a box or glossary, to make this section accessible to readers without specialized bioinformatics training.
  
  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section on AI
  - **Evidence pointer** Section "Nitrogen research in the age of artificial intelligence (AI)"
  - **Issue** The section discusses AI applications broadly but does not mention specific AI tools or platforms that are currently available for plant biology research.
  - **Required correction** Consider adding a brief list or table of currently available AI tools and platforms relevant to nitrogen research, with examples of their applications, to make this section more practically useful.
  
  - **Concern ID** R1-m7
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Conclusions
  - **Evidence pointer** Conclusions section
  - **Issue** The conclusions section is relatively brief and does not fully synthesize the temporal and spatial themes emphasized throughout the review.
  - **Required correction** Consider expanding the conclusions to more explicitly integrate the temporal and spatial dimensions of nitrogen sensing and signaling, and to articulate a clear vision for future research directions.
  
  - **Concern ID** R1-m8
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** References
  - **Evidence pointer** Reference list
  - **Issue** The review cites many studies but does not include a table summarizing key studies, their approaches, and their main findings, which would be helpful for readers seeking a quick overview.
  - **Required correction** Consider adding a summary table of key studies discussed in the review, including the species studied, the approach used, and the main findings, to enhance the review's utility as a reference.
  
  - **Concern ID** R1-m9
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Terminology
  - **Evidence pointer** Throughout the manuscript
  - **Issue** The review uses several technical terms and abbreviations (e.g., sCiNiS, TARGET, DamID, scRNA-seq, snATAC-seq) without always providing clear definitions or explanations for non-specialist readers.
  - **Required correction** Consider adding a glossary of terms and abbreviations, or ensuring that all technical terms are defined at first use, to improve accessibility for readers from related fields.
  
  - **Concern ID** R1-m10
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section on root-to-shoot communication
  - **Evidence pointer** Section "Nitrogen responses across organs: root-to-shoot communication"
  - **Issue** The section discusses known long-distance signals (hormones, peptides, microRNAs) but does not discuss how these signals are integrated with local cell type-specific responses.
  - **Required correction** Consider adding a brief discussion of how systemic and local signals interact to coordinate nitrogen responses across organs, which would strengthen the integration of temporal and spatial themes.
  
  - **Concern ID** R1-m11
  - **Severity** Minor
  - **Axis** Clarity and accessibility
  - **Affected element** Section on model-to-crop translation
  - **Evidence pointer** Section "Model-to-crop: nitrogen sensing and signaling and its impact on agricultural outcomes"
  - **Issue** The section discusses the White House Executive Order and policy goals, which may be of limited relevance to the international readership of the journal.
  - **Required correction** Consider broadening the discussion of policy and societal relevance to include international perspectives, or briefly acknowledge that the policy context is specific to the United States.
  
  - **Concern ID** R1-m12
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section on AI
  - **Evidence pointer** Section "Nitrogen research in the age of artificial intelligence (AI)"
  - **Issue** The section discusses the potential of AI but does not address ethical considerations or potential risks associated with AI applications in agriculture.
  - **Required correction** Consider adding a brief discussion of ethical considerations and potential risks of AI in agricultural research, such as data privacy, algorithmic bias, and the digital divide, to provide a balanced perspective.
- **Technical failings that need to be addressed before the case is established** No fundamental technical failings identified. The review is well-supported by the cited literature, and the claims are generally consistent with the current state of the field. The main limitations are the lack of critical evaluation of some emerging technologies and the incomplete integration of temporal and spatial themes, as noted in the major concerns.
- **Assessment against Nature-style criteria** 
  - **Originality** The review offers a distinctive perspective by explicitly framing nitrogen sensing and signaling through the dual lenses of time and space. While individual topics have been reviewed elsewhere, the integrated temporal-spatial framework provides a novel organizing principle. However, the originality is somewhat limited by the fact that much of the content synthesizes previously published work rather than presenting new conceptual frameworks or hypotheses.
  - **Scientific importance** The topic is of significant importance given the global challenges of nitrogen pollution, food security, and sustainable agriculture. The review addresses fundamental questions in plant biology with clear translational relevance. The emphasis on systems biology approaches and emerging technologies positions the review at the forefront of the field.
  - **Interdisciplinary readership** The review bridges plant molecular biology, systems biology, computational biology, and agricultural science. The discussion of AI and machine learning applications extends the potential readership to computational biologists and data scientists. However, the heavy focus on Arabidopsis molecular details may limit accessibility for readers from other disciplines.
  - **Technical soundness** The review is technically sound, with claims generally well-supported by the cited literature. The authors are established experts in the field, and the review reflects a thorough understanding of the subject matter. The main technical limitation is the lack of critical evaluation of some emerging methods, as noted in the major concerns.
  - **Readability for nonspecialists** The review is generally well-written and accessible, with clear explanations of complex concepts. However, some sections assume significant background knowledge in plant molecular biology and bioinformatics. The use of technical terms and abbreviations without consistent definition may pose challenges for nonspecialist readers. The absence of figures and tables in the provided material limits assessment of their effectiveness in enhancing readability.
- **Recommendation posture** Supportive if technical concerns are resolved. The review makes a valuable contribution to the field by synthesizing recent advances in nitrogen sensing and signaling from a temporal-spatial perspective. The major concerns identified are addressable through revision, and addressing them would significantly strengthen the review's impact and utility. The review is likely to be well-cited and to serve as a useful reference for researchers in the field.

## Risk / unsupported claims
- The claim that NLP7 acts as an intracellular nitrate sensor is presented as established fact, but the evidence is based on a single biosensor study and the physiological relevance is not critically evaluated.
- The statement that "62% of TF-target interactions were predicted to occur in the endodermis" is presented without discussion of the limitations of the prediction methods used.
- The claim that "the endodermis might have a role as a regulatory hub for nitrate signaling" is speculative and presented without sufficient caveats.
- The discussion of AI applications in nitrogen research is largely aspirational and lacks concrete examples of successful applications specific to nitrogen signaling.
- The assertion that "unveiling the mechanisms underlying the spatial dynamics of nitrogen sensing/signaling networks across species from model to crop could pave the way for translational studies" is presented as a certainty rather than a possibility, without discussion of the significant challenges involved in such translation.
- The review's claim that systems biology approaches have "uncovered" mechanisms of nitrogen sensing and signaling may overstate the current state of knowledge, as many of the described findings are recent and not yet fully validated across different conditions and species.