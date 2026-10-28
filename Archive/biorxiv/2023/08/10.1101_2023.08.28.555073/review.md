## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency as presented in the manuscript. No external validation or replication attempted.
- **Shared manuscript claim summary** The authors propose that the repertoire of transcription factor binding motifs (TFBMs) in plants is limited to 76 core motifs, that most TF families show high conservation of binding motifs, that some families show semi-conservation or diversity, and that co-expression of TFs binding the same motif implies competition and signal integration at single binding sites.
- **Visible evidence base** DAP-Seq data from O'Malley et al. (2016), ampDAP-Seq data generated for Marchantia polymorpha, public databases (JASPAR, PlantTFDB), RNA-Seq expression data from 6,033 experiments, phylogenetic analyses, and motif clustering analyses.
- **Missing materials affecting confidence** Supplementary figures and tables (Figures S1-S53, Tables S1-S3) are referenced but not provided. The deposited data at https://doi.org/10.4119/unibi/2982196 and GitHub repository are not accessible for verification. Detailed methods for expression data processing and correlation thresholds are incomplete.

## Reviewer
- **Overall assessment** The manuscript addresses an important question in plant transcriptional regulation: whether the diversity of transcription factors is matched by diversity in their binding motifs. The authors present a meta-analysis of existing and newly generated binding data, concluding that the TFBM vocabulary is small (76 core motifs) and that many TF families share conserved motifs. The concept of signal integration at single binding motifs via competition is interesting and potentially significant. However, the evidence presented is largely descriptive and correlative. The central claims about the "limited vocabulary" depend heavily on the completeness and quality of the underlying datasets, which are not fully assessed. The expression analysis is used to infer competition, but no direct competition assays are provided. The manuscript would benefit from clearer definitions of classification thresholds and a more rigorous treatment of potential biases in the data.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcriptional regulation, particularly those working on transcription factor function, promoter architecture, and gene regulatory networks. Computational biologists developing models for gene expression prediction from sequence. Evolutionary biologists interested in the evolution of gene regulatory elements. The claim of a limited binding vocabulary has practical implications for promoter engineering and for understanding how complex expression patterns arise from a relatively small set of regulatory elements.
- **Major strengths** 1. The study addresses a fundamental question in gene regulation with potential broad implications. 2. The integration of multiple public datasets and new ampDAP-Seq data is valuable. 3. The classification of TF families into conserved, semi-conserved, and diverse categories provides a useful framework. 4. The concept of signal integration at single binding motifs via competition is a novel and thought-provoking idea. 5. The use of a large RNA-Seq compendium to assess co-expression is a strength.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that "the currently known promoter vocabulary of TFBMs consists of 76 distinct TFBMs in plants" is presented as a definitive number.
  - **Evidence pointer** Results section, Table 1, Methods (TFBM acquisition)
  - **Concern** The number 76 is derived from a specific pipeline that includes data from multiple sources with different methodologies (DAP-Seq, ampDAP-Seq, ChIP-Seq, protein binding microarrays). The authors state they "prefer" ampDAP-Seq data but the criteria for choosing one representative TFBM per TF when multiple are available are not fully described. The completeness of the underlying data is questionable: only 680 of 1,725 A. thaliana TFs have a known TFBM. The authors do not assess whether the 76 motifs represent a saturation point or an artifact of incomplete sampling. The claim of a "limited vocabulary" is therefore not robustly established.
  - **Why it matters** The central thesis of the manuscript rests on this number. If the number is an underestimate due to incomplete data or methodological biases, the conclusion that the vocabulary is "limited" is weakened. The authors need to demonstrate that additional sampling would not substantially increase the number of core motifs.
  - **Resolution test** Provide a saturation analysis showing that the number of new motifs plateaus with increasing numbers of TFs sampled. Alternatively, provide a statistical estimate of the total number of motifs expected given the sampling effort. Justify the choice of representative TFBM more rigorously, including a sensitivity analysis showing that the classification of families into conserved/semi-conserved/diverse is robust to the choice of representative motif.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support
  - **Claim pointer** The claim that "expression analyses revealed high competition within TF families for the same binding motif" and that "single binding motifs act as signal integrators in plants where a combination of binding affinity and TF abundance likely determine the output."
  - **Evidence pointer** Results section (expression analyses), Figures 2C, 3C, Table S3
  - **Concern** The inference of competition is based solely on co-expression analysis (Pearson correlation of expression profiles). Co-expression is a necessary but not sufficient condition for competition. The authors do not provide any direct evidence of competition, such as competitive binding assays, ChIP-Seq data showing mutually exclusive binding, or genetic experiments. The correlation thresholds used (0.7 and 0.5) are arbitrary and not justified. The analysis is limited to A. thaliana wild-type RNA-Seq data, which may not capture the relevant conditions where competition occurs. The claim that "TF abundance determine the output" is speculative and not directly tested.
  - **Why it matters** The concept of signal integration at single motifs is a key novelty of the paper. If the evidence for competition is weak, this concept remains an interesting hypothesis but not a demonstrated finding. The authors need to provide more direct evidence or clearly frame this as a hypothesis.
  - **Resolution test** Provide direct experimental evidence of competition, such as in vitro binding assays with competing TFs, or ChIP-Seq data showing that binding of one TF excludes another at the same site. Alternatively, re-frame the claim as a hypothesis and provide a more rigorous statistical framework for inferring competition from expression data, including justification of correlation thresholds and consideration of confounding factors.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodology transparency
  - **Claim pointer** The classification of TF families into conserved, semi-conserved, and diverse categories.
  - **Evidence pointer** Methods (Family allocation, Phylogenetic analyses), Table S1
  - **Concern** The criteria for classification are described in the text but the specific thresholds are not fully defined. The text states "we established the classification of semi-conservation to cover families with up to four different consensus TFBMs and no more than 15% outliers." The definition of "outlier" is not clear. The manual curation step in the clustering process (mentioned in Methods) introduces subjectivity. The number of families in each category is not clearly stated in the main text.
  - **Why it matters** The classification is a central organizing framework of the results. If the criteria are not transparent and reproducible, the classification cannot be independently verified or applied by other researchers.
  - **Resolution test** Provide a detailed, step-by-step description of the classification algorithm, including all thresholds and the exact definition of "outlier." Provide the classification of all 50 families in a supplementary table. Consider making the clustering and classification code fully available and documented.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data completeness
  - **Claim pointer** The evolutionary analysis using Marchantia polymorpha to date the age of TFBM conservation.
  - **Evidence pointer** Results (phylogenetic analyses), Methods (ampDAP-Seq)
  - **Concern** The manuscript states that ampDAP-Seq data for M. polymorpha was generated, but only one TF from M. polymorpha is mentioned in the results (a MYB TF). The number of M. polymorpha TFs with TFBMs is not stated. The evolutionary conclusions about the age of TFBM conservation (e.g., "at least 500 million years") are based on the presence of orthologs in M. polymorpha, but the analysis is not described in detail. The authors mention 14 M. polymorpha TFs in the Methods but the results for these are not presented.
  - **Why it matters** The evolutionary claims are a significant part of the discussion. If the M. polymorpha data is limited or not fully analyzed, the strength of the evolutionary conclusions is reduced.
  - **Resolution test** Clearly state the number of M. polymorpha TFs with TFBMs and present the results of the evolutionary analysis in the main text or a supplementary figure. Provide a more detailed description of the orthology analysis and the dating methodology.

- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states "Analyzing 2,190 binding motifs, we identified only 76 core TF binding motifs in plants." The number 2,190 is described as "binding motifs" but in the results it is described as "redundant data points." This is confusing.
  - **Required correction** Clarify the terminology. Use "2,190 redundant TFBM entries" or similar in the abstract.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Expression analysis
  - **Evidence pointer** Results, Figures 2C, 3C
  - **Issue** The correlation thresholds (0.7 and 0.5) are used to define "shared expression" and "similar expression." The rationale for these specific thresholds is not provided.
  - **Required correction** Provide a justification for the chosen thresholds, or present the results as a continuous distribution of correlation coefficients rather than a binary classification.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1
  - **Issue** The description of Figure 1 in the text is brief. The figure appears to show a genome browser view, but the details of what is displayed (e.g., which TFs, which loci) are not clear.
  - **Required correction** Expand the figure legend to clearly describe all panels and the data displayed.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Discussion
  - **Evidence pointer** Discussion
  - **Issue** The term "vocabulary" is used metaphorically. While evocative, it may be imprecise. The authors should define what they mean by "vocabulary" in operational terms.
  - **Required correction** Define "vocabulary" as the set of distinct core TFBM sequences identified in this analysis.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods
  - **Evidence pointer** Methods (ampDAP-Seq)
  - **Issue** The Methods section for ampDAP-Seq is brief. Details on library preparation, sequencing depth, and data processing are missing.
  - **Required correction** Provide a more detailed protocol or cite a published protocol for ampDAP-Seq.

- **Technical failings that need to be addressed before the case is established** R1-M1 (saturation analysis and justification of representative TFBM selection) and R1-M2 (direct evidence or re-framing of competition claim) are the most critical. Without addressing these, the central claims of a limited vocabulary and signal integration via competition are not fully supported. R1-M3 (classification transparency) is also important for reproducibility.

- **Assessment against Nature-style criteria** 
  - **Originality** The concept of signal integration at single binding motifs via competition is a novel perspective. The systematic classification of TF families based on binding motif conservation is a useful contribution. However, the idea that TF binding motifs are conserved within families is not entirely new, and the originality lies more in the synthesis and the proposed functional implications.
  - **Scientific importance** The question of how a relatively small number of TFs generate diverse expression patterns is fundamental. If the claims are substantiated, the work could influence how researchers think about promoter architecture and gene regulation. The potential implications for understanding redundancy and evolution of gene regulation are significant.
  - **Interdisciplinary readership** The topic is of primary interest to plant molecular biologists and computational biologists. The findings may be of interest to a broader audience interested in gene regulation, but the presentation is quite specialized. The use of terms like "TFBM" and "ampDAP-Seq" without extensive explanation may limit accessibility.
  - **Technical soundness** The technical approach is generally sound, but there are concerns about data completeness, classification criteria, and the inference of competition from co-expression data. The lack of a saturation analysis and the subjective elements in the classification process are weaknesses.
  - **Readability for nonspecialists** The manuscript is written in a clear and direct style, but the subject matter is inherently technical. The abstract is accessible, but the results and methods sections would be challenging for a nonspecialist. The main concepts are explained, but the significance of the findings could be better contextualized for a broader audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a potentially significant concept. However, the central claims are not fully established from the provided evidence. The authors must address the concerns about data saturation, the inference of competition, and the transparency of the classification methodology. If these are resolved, the manuscript could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that the TFBM vocabulary is "limited" to 76 motifs is not supported without a saturation analysis.
- The claim that "high competition within TF families for the same binding motif" is inferred from co-expression data and is not directly supported.
- The claim that "single binding motifs act as signal integrators" is a hypothesis that is not directly tested.
- The evolutionary claims about the age of TFBM conservation (e.g., "at least 500 million years") are based on limited data (one M. polymorpha MYB TF) and are not fully supported.
- The statement that "the results show that singular binding motifs act as signal integrators in plants where a combination of binding affinity and TF abundance likely determine the output" is a conclusion that goes beyond the presented evidence.