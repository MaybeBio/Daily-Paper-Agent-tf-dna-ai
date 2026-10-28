## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusions, methods, data availability, author contributions, and acknowledgements
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and alignment with claims; not editorial or formatting issues
- **Shared manuscript claim summary** The authors analyze binding motifs of 686 Arabidopsis thaliana transcription factors and 92 from other plants, identify 74 conserved motifs across 50 families, classify families as conserved, semi-conserved, or diverse, and experimentally validate conservation of selected motifs in Marchantia polymorpha using ampDAP-Seq, concluding that TF binding motifs are largely conserved for at least 450 million years and that evolution occurs more in cis- than trans-regulatory elements
- **Visible evidence base** Abstract, full results text, methods descriptions, figure references (Figures 1-5, Supplemental Figures S1-S6), table references (Tables 1, Supplemental Tables S1-S6), data availability statement
- **Missing materials affecting confidence** Figures and tables themselves are not provided; only references to them in text. Supplemental data sets and detailed phylogenetic trees are referenced but not included. Raw sequencing data availability is stated but not verifiable from this material.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in plant transcriptional regulation: the evolutionary conservation of transcription factor binding motifs. The authors leverage a large existing dataset of DAP-Seq and ampDAP-Seq data, apply a consistent analytical pipeline, and provide new experimental validation in a bryophyte. The central finding, that many TF families show conserved motifs over 450 million years, is potentially important for understanding regulatory evolution. However, the manuscript has several significant weaknesses. The classification of families into conserved, semi-conserved, and diverse categories relies on thresholds that are not clearly justified. The claim that evolution occurs more in cis than trans is an inference that goes beyond the direct evidence presented. The experimental validation in M. polymorpha is limited to a small number of TFs and lacks quantitative comparison with angiosperm motifs. The analysis of binding site overlap and expression correlation is descriptive and does not include statistical testing. The manuscript would benefit from clearer presentation of methods for motif comparison and family classification, and from a more cautious interpretation of the evolutionary implications.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcriptional regulation, particularly those working on transcription factor families and cis-regulatory element evolution. Evolutionary biologists interested in the conservation of gene regulatory networks across deep evolutionary timescales. Researchers using DAP-Seq or similar in vitro binding assays who would benefit from the methodological framework for comparing motifs across species. The finding that most TF families have conserved motifs while a few show diversity has implications for understanding how regulatory networks evolve and for predicting TF binding sites in non-model plants.
- **Major strengths** 1) The study uses a large, consistent dataset of experimentally determined TF binding motifs, reducing cross-lab variability. 2) The combination of bioinformatic analysis with new experimental validation in a bryophyte is a strong approach to test evolutionary conservation. 3) The classification of families into conserved, semi-conserved, and diverse provides a useful framework for thinking about TF family evolution. 4) The analysis of binding site overlap and expression correlation addresses the functional implications of motif conservation. 5) The manuscript is generally well-written and accessible to a broad biological audience.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The question of TF motif conservation across plant evolution is not entirely new, but the scale of analysis and the combination of bioinformatic and experimental approaches provide a fresh perspective. The finding that most families are conserved while a few show diversity is a useful contribution. Scientific importance: The results have implications for understanding regulatory evolution and for predicting TF binding in non-model species, which is relevant to both basic and applied plant science. Interdisciplinary readership: The topic is of interest to plant molecular biologists, evolutionary biologists, and computational biologists. The manuscript is written in a way that is accessible to these groups. Technical soundness: The analytical pipeline is generally sound, but several methodological details are unclear or not fully justified, and the statistical framework is weak. Readability for nonspecialists: The manuscript is clearly written, but the methods section assumes familiarity with DAP-Seq and motif analysis. Overall, the manuscript has potential but requires substantial revision to meet the standards of a high-impact journal.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state that "we found a constrained vocabulary of 74 conserved motifs spanning 50 families in plants" and classify families as conserved, semi-conserved, or diverse based on the number of distinct motifs within each family.
- **Evidence pointer** Results section, Figure 2B, Supplemental Table S2, Methods section "Family allocation" and "Phylogenetic analyses"
- **Concern** The classification of families into conserved, semi-conserved, or diverse is based on thresholds (e.g., "up to four different consensus TFBMs and no more than 15% outliers") that are presented without statistical justification. The authors do not provide a null model or a statistical test to determine whether the observed number of motifs within a family is significantly different from what would be expected by chance. The cutoffs appear arbitrary, and it is unclear how sensitive the classification is to these choices. Additionally, the comparison of motifs across families relies on a similarity threshold (cut-off of h=0.2) that is not justified.
- **Why it matters** The central conclusion of the manuscript, that most TF families have conserved motifs while a few are diverse, depends entirely on this classification. If the thresholds are arbitrary or not robust, the main message of the paper is not supported. A reader cannot assess whether the classification is meaningful without a statistical framework.
- **Resolution test** Provide a statistical justification for the classification thresholds, such as a permutation test or a null model based on random motif generation. Show that the classification is robust to reasonable variations in the thresholds. Alternatively, present the distribution of motif similarities within each family and use a formal clustering approach with a defined criterion for the number of clusters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that "we detected nearly identical binding motifs as predicted from the angiosperm data" for 17 M. polymorpha TFs from 11 families.
- **Evidence pointer** Results section "Many TFBMs have been conserved for at least 450 million years", Figure 5, Supplemental Figures S4-S6
- **Concern** The experimental validation in M. polymorpha is limited to 17 TFs, and the comparison with angiosperm motifs is described qualitatively as "nearly identical" without a quantitative measure of similarity. The authors do not provide a statistical comparison between the M. polymorpha motifs and the predicted angiosperm motifs. It is unclear how many of the 17 TFs showed exact matches, how many showed minor variations, and whether any showed significant differences. The number of biological replicates for the ampDAP-Seq experiments is not stated.
- **Why it matters** The claim of conservation for 450 million years is a key finding of the paper. Without a quantitative comparison and information on replication, the reader cannot assess the strength of the evidence. A qualitative statement of "nearly identical" is not sufficient to support such a strong evolutionary claim.
- **Resolution test** Provide a quantitative similarity score (e.g., Pearson correlation or Kullback-Leibler divergence) between each M. polymorpha motif and the corresponding angiosperm consensus motif, with a statistical test for significance. State the number of biological replicates for each ampDAP-Seq experiment. If some TFs show divergent motifs, discuss these cases explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that "we mapped (amp)DAP-Seq peaks from O'Malley et al., (2016) and López-Vidriero et al., (2021) onto individual promoters of genes" and that "peak sequences were extracted from the TAIR10 reference genome... and TFBMs were determined using MEME-ChIP."
- **Evidence pointer** Methods section "TFBM determination"
- **Concern** The methods for peak calling, motif discovery, and motif comparison are described at a high level, but several critical details are missing. The authors do not specify the parameters used for MEME-ChIP, the criteria for selecting the "best" motif (beyond lowest e-value and length), or how motifs were compared across TFs and families. The statement that "we considered sufficiently similar parts of a gapped TFBM as the same cluster" is vague and does not provide a reproducible criterion. The methods for calculating binding site overlap and expression correlation are also not described in sufficient detail.
- **Why it matters** Reproducibility is a core requirement for scientific publication. Without detailed methods, other researchers cannot replicate the analysis or assess its validity. The lack of specificity in motif comparison is particularly problematic because the classification of families depends on it.
- **Resolution test** Provide a detailed description of all parameters and criteria used in the analysis, including MEME-ChIP parameters, motif comparison thresholds, and the algorithm for defining "sufficiently similar" parts of gapped motifs. Make the analysis code publicly available and ensure it is well-documented.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors conclude that "the results indicate more potential for evolution in cis- rather than trans-regulatory elements."
- **Evidence pointer** Abstract, Discussion section "There is limited potential for TFBM evolution in some families", Conclusions
- **Concern** This conclusion is presented as a major implication of the study, but it is an inference that goes beyond the direct evidence. The authors show that TF motifs are conserved, but they do not directly measure cis-regulatory element evolution. The statement that "most evolution must occur in cis rather than trans" is a hypothesis that requires additional evidence, such as comparative analysis of promoter sequences or functional assays of promoter activity across species. The authors themselves acknowledge that "binding site spacing and protein-protein interactions were not explored in this work," which further limits the strength of this conclusion.
- **Why it matters** The conclusion about cis versus trans evolution is likely to be a headline finding of the paper. If it is not directly supported by the data, it could be misleading to readers and overstate the significance of the work.
- **Resolution test** Either soften the conclusion to state that the data are consistent with, but do not prove, a greater role for cis-regulatory evolution, or provide additional analysis that directly addresses cis-regulatory element evolution, such as comparing promoter sequences between species or measuring allele-specific expression.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Data completeness
- **Claim pointer** The authors state that "Database queries yielded a total of 2,190 redundant entries from the Plant Cistrome, JASPAR, PlantTFDB databases" and that after filtering, 686 A. thaliana TFs and 92 from other plants were analyzed.
- **Evidence pointer** Results section, Table 1, Methods section "TFBM determination"
- **Concern** The authors do not provide a breakdown of how many TFs came from each database, how many were excluded at each filtering step, and what proportion of the total annotated TFs in A. thaliana (1,725) are represented. The statement that "we know on average 40.5% of TFBMs of all annotated TFs in A. thaliana" suggests that a large fraction of TFs lack motif data, but the implications of this incomplete coverage are not discussed. It is unclear whether the missing data could bias the classification of families.
- **Why it matters** The completeness of the dataset affects the generalizability of the conclusions. If certain families are underrepresented, the classification of those families as conserved or diverse may not be reliable. The reader needs to know the extent of missing data to assess the robustness of the findings.
- **Resolution test** Provide a detailed flowchart of data filtering steps, including the number of TFs from each source and the reasons for exclusion. Discuss the potential impact of missing data on the classification of families, particularly for families with few characterized members.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Results section, Figure 1B
- **Issue** The text states that "there is experimental evidence for 0 to 357 (one outlier with 1,076) binding events per promoter" but does not explain what the outlier is or why it is excluded from the range.
- **Required correction** Clarify the nature of the outlier and whether it is included in any subsequent analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of C2H2 family
- **Evidence pointer** Results section "Semi-conservation of TFBMs follows phylogenetic relationships", Supplemental Figure S2
- **Issue** The authors state that the C2H2 family shows "high diversity among motifs" but do not discuss potential technical reasons for this diversity, such as the possibility that some C2H2 TFs bind DNA in a more flexible manner or that the motif discovery methods may be less sensitive for this family.
- **Required correction** Add a brief discussion of potential technical or biological explanations for the observed diversity in the C2H2 family.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Expression correlation analysis
- **Evidence pointer** Results section, Supplemental Table S5
- **Issue** The authors report correlation coefficients for expression similarity but do not state the number of samples used for each correlation or provide confidence intervals.
- **Required correction** Report the sample size for each correlation and consider providing confidence intervals or a measure of uncertainty.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "core motif"
- **Evidence pointer** Throughout the manuscript
- **Issue** The term "core motif" is used without a clear definition. It is unclear whether this refers to the most conserved positions within a motif or to a specific length of the motif.
- **Required correction** Define "core motif" explicitly when first used and ensure consistent usage throughout.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of limitations
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address the limitation that in vitro binding assays may not fully recapitulate in vivo binding, where chromatin context and cofactors play important roles.
- **Required correction** Add a sentence acknowledging this limitation and its potential impact on the interpretation of the results.

## Risk / unsupported claims
- The claim that "most evolution must occur in cis- rather than trans-regulatory elements" is not directly supported by the data presented and should be framed as a hypothesis.
- The classification of families as conserved, semi-conserved, or diverse is based on thresholds that are not statistically justified.
- The statement that M. polymorpha motifs are "nearly identical" to angiosperm motifs is qualitative and lacks quantitative support.
- The claim that "the results show a large repertoire of overlapping binding sites within a TF family" is based on descriptive analysis without statistical testing.
- The generalizability of the conclusions to all plant TF families is limited by incomplete coverage of the A. thaliana TF repertoire (only 40.5% of annotated TFs have motif data).