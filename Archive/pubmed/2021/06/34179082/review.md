## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, structure, clarity, and completeness of the review as presented; no external literature verification performed
- **Shared manuscript claim summary** The authors review recent machine learning approaches, particularly deep learning, for predicting gene expression phenotypes from nucleotide sequence and for interpreting the cis-regulatory grammar across prokaryotic and eukaryotic organisms. They argue that deep neural networks outperform shallow methods, that whole-gene regulatory structures carry more predictive information than individual regions, and that computational models are approaching the accuracy of experimental assays.
- **Visible evidence base** Abstract, Introduction, sections on protein-DNA interactions, coding and non-coding regions, transcript/protein level prediction, Discussion, Tables 1-4 (referenced but not fully visible), Figures 1-3 (referenced but not visible)
- **Missing materials affecting confidence** Tables 1-4 contents, Figures 1-3 contents, reference list, any supplementary materials

## Reviewer
- **Overall assessment** This is a well-structured and informative review that covers a broad range of machine learning applications in gene expression regulation. The authors successfully organize the material from first principles, progressing from individual regulatory elements to whole-gene models, and provide a useful synthesis of recent advances. The review is generally clear and accessible, though some sections are dense and would benefit from more explicit critical evaluation of the methods discussed. The main weakness is the lack of a systematic comparison framework across studies, which limits the strength of the conclusions about relative method performance.
- **Who would be interested in the results, and why** Researchers in computational biology, genomics, and regulatory genomics would find this review valuable as a comprehensive entry point to the field. Practitioners in synthetic biology and biotechnology interested in predictive sequence design would also benefit. The review is particularly useful for those seeking an overview of deep learning architectures applied to gene expression prediction and the interpretability of these models.
- **Major strengths** The review is logically organized, building from molecular mechanisms to computational methods. The authors provide a good balance of biological context and technical detail. The inclusion of both prokaryotic and eukaryotic examples is a strength, as is the discussion of model interpretability. The information-centric synthesis in the Discussion is a valuable conceptual contribution.
- **Major Concerns** The review lacks a critical comparative analysis of the methods discussed; performance metrics are reported inconsistently across studies, making direct comparisons difficult. The authors do not adequately address the limitations of deep learning approaches, such as data requirements, overfitting, and generalizability across species or cell types. The Discussion section makes claims about trends in explained variance across organisms that are based on a small number of heterogeneous studies, and the authors do not sufficiently caveat these conclusions.
- **Minor Comments** Some terminology is used without definition (e.g., "dilated convolution", "self-attention") which may hinder nonspecialist readers. The figures are referenced but not visible in the provided material, making it difficult to assess their quality and relevance. The review would benefit from a summary table of key studies with consistent reporting of data types, model architectures, and performance metrics.
- **Technical failings that need to be addressed before the case is established** The claim that deep learning outperforms shallow methods is supported by several examples, but the authors do not provide a systematic meta-analysis or discuss cases where shallow methods perform comparably or better. The claim about increasing explained variance with organism complexity (Figure 3C) is based on a very limited number of studies with different methodologies and should be presented as a hypothesis rather than a trend.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The review synthesizes existing work but does not present a novel framework or perspective that significantly advances the field.  
  - Scientific importance: High. The topic is of broad interest and the review addresses a rapidly evolving area.  
  - Interdisciplinary readership: Moderate. The content is accessible to computational biologists but may be challenging for experimental biologists without ML background.  
  - Technical soundness: Adequate. The descriptions of methods are generally accurate, but the lack of critical evaluation weakens the technical depth.  
  - Readability for nonspecialists: Moderate. The structure is clear, but some technical sections are dense and assume prior knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The review is a useful contribution, but the authors should strengthen the critical analysis, provide more consistent performance comparisons, and temper conclusions that are not robustly supported by the evidence presented.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that deep learning methods frequently outperform shallow methods and are the method of choice for quantifying gene expression.
- **Evidence pointer** Throughout the manuscript, particularly in sections on protein-DNA interactions and transcript level prediction; Tables 1-3 (not fully visible)
- **Concern** The claim of deep learning superiority is supported by selected examples, but the review does not provide a systematic comparison across studies. Performance metrics are reported inconsistently (e.g., AUC, R², Spearman's ρ), and the authors do not discuss cases where shallow methods perform comparably or better. Without a structured comparison, the claim is not robustly established.
- **Why it matters** The central thesis of the review is that deep learning is the preferred approach. If this claim is not rigorously supported, the review's conclusions are weakened and may mislead readers.
- **Resolution test** Provide a systematic comparison table of studies with consistent metrics, or explicitly discuss the conditions under which shallow methods are competitive. Alternatively, temper the claim to reflect the current evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation and generalizability
- **Claim pointer** The authors suggest that the region spanning <10 kb around the TSS has the largest measurable effect on gene expression and that enhancers are harder to model due to variable positioning.
- **Evidence pointer** Discussion section; references to Agarwal and Shendure (2020) and Zrimec et al. (2020)
- **Concern** The generalization about the <10 kb window is based on a limited number of studies, and the authors do not discuss exceptions or the dependence of this finding on organism, cell type, or gene class. The statement about enhancers is presented as a limitation without exploring recent advances in long-range modeling.
- **Why it matters** These claims have implications for model design and interpretation. If they are overstated, they could mislead researchers in choosing input sequence windows or in interpreting model limitations.
- **Resolution test** Add caveats about the generalizability of the <10 kb finding, and discuss recent approaches that successfully model distal enhancers. Provide a more nuanced discussion of the trade-offs between sequence window size and model performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of coverage
- **Claim pointer** The review claims to provide an overview of the latest developments in applying machine learning to gene expression regulation.
- **Evidence pointer** Introduction and section headings
- **Concern** The review focuses heavily on transcription initiation and mRNA level prediction, with relatively less coverage of post-transcriptional regulation, RNA modifications, and translation dynamics. Some recent advances in transformer-based models and single-cell approaches are mentioned only briefly.
- **Why it matters** The field is broad, and a review that claims comprehensive coverage should address the full scope of gene expression regulation, including emerging areas that are likely to shape future research.
- **Resolution test** Expand the discussion of post-transcriptional regulation and translation, and include a section on emerging architectures (e.g., transformers) and their applications in genomics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity for nonspecialists
- **Affected element** Technical terminology
- **Evidence pointer** Sections on deep learning architectures
- **Issue** Terms such as "dilated convolution", "self-attention", and "bidirectional LSTM" are used without definition or brief explanation.
- **Required correction** Add a short glossary or provide brief definitions when these terms are first introduced to improve accessibility for readers without a machine learning background.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility and transparency
- **Affected element** Performance metrics
- **Evidence pointer** Tables 1-3 (not fully visible)
- **Issue** The review reports performance metrics from different studies without standardizing them, making it difficult to compare results across methods.
- **Required correction** Include a table that normalizes performance metrics where possible, or clearly state the metric used for each study and discuss the implications for comparability.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Structure and flow
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The Discussion section introduces new concepts (e.g., information-centric view) that are not fully developed in the main text, and some conclusions are presented without sufficient caveats.
- **Required correction** Move the information-centric synthesis to a clearly labeled subsection and ensure that all conclusions are explicitly linked to the evidence presented in the main text.

## Risk / unsupported claims
- The claim that deep learning methods are "the method of choice" for gene expression prediction is not systematically supported by the evidence presented.
- The statement that "about ⅔ of the variation of mRNA and protein levels can be explained from DNA sequence" is based on a small number of studies with heterogeneous methodologies and should be presented as an estimate with caveats.
- The assertion that "current computational approaches are achieving a level of accuracy that might soon allow substituting wet-lab HTS experiments with fully computational pipelines" is speculative and not directly supported by the reviewed studies.
- The claim that "motif associations could explain a much larger portion of the dynamic range of mRNA levels (84 vs. 57%)" is presented without sufficient detail on how this comparison was made across different studies.