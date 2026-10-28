## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, appendices, and search strategies.
- **Assessment boundary** The review assesses the manuscript's methodological rigor, completeness of reporting, internal consistency, and the validity of its claims relative to the provided evidence. It does not assess the quality of the primary studies included in the scoping review beyond what is reported.
- **Shared manuscript claim summary** The manuscript claims to present a scoping review of 26 studies (2021–April 2024) that apply NLP techniques, particularly LLMs and transformer architectures, to genomic data analysis. It claims to focus on three areas: tokenization, transformer models, and regulatory annotation prediction. It further claims that these techniques enhance processing and understanding of genomic data, with applications in predicting regulatory annotations, and that the field holds promise for personalized medicine, while acknowledging limitations in model transparency and applicability.
- **Visible evidence base** The provided manuscript text, including the abstract, introduction, methods (eligibility criteria, information sources, search strategy), results (narrative summary, Table 1 and Table 2 descriptions), discussion, and appendices (PRISMA checklist, search strategies for six databases).
- **Missing materials affecting confidence** The full text of the 26 included studies is not provided. The content of Table 1 and Table 2 is not fully visible; only partial descriptions and some data points are given. The PRISMA flow diagram (number of records identified, screened, excluded, etc.) is not provided. The full search strategies for Google Scholar and Semantic Scholar are not provided. The supplementary materials (A and B) are referenced but not included in the provided text.

## Reviewer

- **Overall assessment** This manuscript addresses a timely and relevant topic: the application of advanced NLP, particularly LLMs and transformers, to genomic data. The authors have identified a clear gap in the literature and have chosen a scoping review methodology, which is appropriate for mapping an emerging field. The search strategy is described in reasonable detail, and the inclusion criteria are stated. However, the manuscript has significant weaknesses in reporting. The results section is largely narrative and lacks a structured synthesis of the included studies. The descriptions of Table 1 and Table 2 are incomplete, making it impossible to assess the evidence base. The methods section lacks critical details on the screening process, data extraction, and synthesis methods. The discussion, while touching on relevant challenges, is somewhat generic and does not deeply engage with the findings of the included studies. The manuscript's claims about the "promise" of the field are not fully supported by the evidence presented, which is largely a list of model performances without critical appraisal. The manuscript is not currently suitable for publication in a high-impact journal without substantial revisions.
- **Who would be interested in the results, and why** Researchers and practitioners in bioinformatics, computational genomics, and machine learning would be interested in this review as a map of the current state of NLP applications in genomics. Clinicians and researchers in personalized medicine might also be interested in the potential applications highlighted. The review could serve as a useful starting point for those entering the field. However, the interest would be tempered by the lack of critical synthesis and detailed reporting.
- **Major strengths**
    1.  The topic is timely and of high interest, given the rapid adoption of LLMs in various domains.
    2.  The authors have chosen a scoping review methodology, which is appropriate for a broad and emerging topic.
    3.  The search strategy is described for multiple databases, which is a strength for reproducibility.
    4.  The review focuses on a specific set of technical aspects (tokenization, transformers, regulatory annotation), providing a clear scope.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodological completeness
    - **Claim pointer** The manuscript claims to follow PRISMA guidelines and to have conducted a systematic scoping review.
    - **Evidence pointer** Methods section (Section 2), Appendix A
    - **Concern** The methods section is critically under-reported. It lacks a description of the study selection process (e.g., number of reviewers, conflict resolution), the data extraction process (e.g., what data was extracted, how), and the data synthesis method (e.g., narrative synthesis, thematic analysis). The PRISMA flow diagram, which is a core component of a PRISMA-compliant review, is not provided. The claim of following PRISMA guidelines is therefore not verifiable from the provided text.
    - **Why it matters** A scoping review's value is contingent on its methodological transparency and reproducibility. Without a clear description of the process, readers cannot assess the reliability of the review's findings or replicate the study. This is a fundamental flaw that undermines the manuscript's core claim.
    - **Resolution test** The authors must provide a detailed description of the screening process (including a PRISMA flow diagram), data extraction procedures, and synthesis methods. The methods section must be expanded to a level of detail that allows replication.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence synthesis and reporting
    - **Claim pointer** The results section claims to highlight that tokenization and transformer models enhance processing and understanding of genomic data, with applications in predicting regulatory annotations.
    - **Evidence pointer** Results section (Section 3), Table 1, Table 2
    - **Concern** The results are presented as a narrative summary of individual studies, but the synthesis is superficial. The descriptions of Table 1 and Table 2 are incomplete and do not provide a clear overview of the studies' characteristics, methods, or findings. For example, the text mentions "61,051 sequences containing 142,325 CpG islands" and "3,382 promoters" but does not clearly link these to specific studies or explain their significance in the context of the review. The tables themselves are not fully visible, making it impossible to assess the evidence base. The narrative does not critically appraise the included studies or identify patterns, gaps, or methodological strengths/weaknesses across the body of literature.
    - **Why it matters** A scoping review should provide a structured map of the evidence. The current narrative is descriptive but not analytical. The incomplete presentation of the tables prevents the reader from understanding the scope and nature of the included studies. The claim that these techniques "enhance" processing is a value judgment that is not supported by a critical synthesis of the evidence.
    - **Resolution test** The authors must provide complete, well-structured tables that summarize the key characteristics of all 26 studies (e.g., author, year, data type, NLP method, task, performance metrics). The narrative results should be organized around the key themes (tokenization, transformers, regulatory annotation) and should synthesize findings across studies, highlighting commonalities, differences, and gaps.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Validity of claims
    - **Claim pointer** The discussion claims that the application of NLP and LLMs to genomic data "can potentially drive advancements in personalized medicine."
    - **Evidence pointer** Discussion section (Section 4)
    - **Concern** This claim is speculative and not directly supported by the findings of the review. While the potential is plausible, the review does not present evidence that any of the included studies have been applied in a clinical or personalized medicine setting. The claim overstates the current state of the field based on the evidence presented.
    - **Why it matters** Overstating the implications of a review can mislead readers and potentially influence research directions or funding decisions. The discussion should clearly distinguish between the current state of the art (as evidenced by the included studies) and future potential.
    - **Resolution test** The authors should temper this claim and explicitly state that the potential for personalized medicine is a future possibility that requires further research and validation, rather than a current outcome of the reviewed literature.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness
    - **Affected element** Search strategy
    - **Evidence pointer** Section 2.2, Appendix B
    - **Issue** The information sources section lists databases, but the search strategies for Google Scholar and Semantic Scholar are not provided in Appendix B. The search dates for these databases are also not specified.
    - **Required correction** Provide the full search strategies for all databases listed in Section 2.2, including Google Scholar and Semantic Scholar, and specify the search dates for each.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity and completeness
    - **Affected element** Results section
    - **Evidence pointer** Section 3.1, Table 1
    - **Issue** The text in Section 3.1 mentions specific data points (e.g., "61,051 sequences containing 142,325 CpG islands") but does not clearly attribute them to specific studies or explain their relevance in the context of the review's synthesis.
    - **Required correction** Clarify the source and significance of these data points. Either link them to specific studies in the text or remove them if they are not essential to the narrative.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Readability
    - **Affected element** Discussion section
    - **Evidence pointer** Section 4
    - **Issue** The discussion is somewhat generic and does not deeply engage with the specific findings of the included studies. For example, the challenges of model interpretability and lack of standardized pipelines are mentioned, but not discussed in the context of the specific models or tasks reviewed.
    - **Required correction** Strengthen the discussion by linking the challenges and opportunities to specific examples from the included studies. This will make the discussion more informative and grounded in the review's findings.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Incomplete reporting of the review methodology, including the absence of a PRISMA flow diagram and details on screening, data extraction, and synthesis.
    - R1-M2: Incomplete presentation of the results, with the tables not fully visible and the narrative lacking a structured synthesis.
- **Assessment against Nature-style criteria**
    - **Originality** The topic is timely, but the review's originality is limited. It maps a known and rapidly growing field. The specific focus on tokenization, transformers, and regulatory annotation is a reasonable scoping choice, but the review does not offer a novel conceptual framework or a unique critical perspective.
    - **Scientific importance** The topic is of high scientific importance, as NLP methods are increasingly used in genomics. A well-conducted scoping review could be a valuable resource. However, the current manuscript's importance is diminished by its methodological and reporting flaws, which limit its utility as a reliable map of the field.
    - **Interdisciplinary readership** The topic has the potential to appeal to a broad readership, including computer scientists, bioinformaticians, and genomic biologists. However, the manuscript's readability for nonspecialists is a concern. The introduction and discussion assume a familiarity with both NLP and genomics concepts. The results section is a list of model names and metrics without sufficient context for a nonspecialist to understand the significance.
    - **Technical soundness** The technical soundness of the review process is not fully assessable due to incomplete reporting. The search strategy is described, but the lack of detail on screening and synthesis prevents a full assessment. The narrative synthesis is not rigorous enough to be considered technically sound.
    - **Readability for nonspecialists** The manuscript is not easily accessible to nonspecialists. Terms like "k-mers," "BERT," "transformer," and "CpG islands" are used without adequate explanation. The results section is particularly dense and assumes a high level of prior knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant topic, but the significant methodological and reporting gaps prevent a positive recommendation. The authors must substantially revise the manuscript to address the major concerns, particularly the incomplete methods and results reporting, before the case for publication can be considered.

## Risk / unsupported claims
- The claim that the review "highlights that tokenization and transformer models enhance the processing and understanding of genomic data" is an unsupported value judgment, as the results are presented descriptively without critical synthesis or comparison to non-NLP methods.
- The claim that the field "can potentially drive advancements in personalized medicine" is speculative and not supported by the evidence presented in the review.
- The claim that the review follows PRISMA guidelines is not verifiable from the provided text, as key PRISMA elements (e.g., flow diagram, detailed methods) are missing.
- The completeness and accuracy of the search results cannot be assessed, as the full search strategies for all databases and the PRISMA flow diagram are not provided.