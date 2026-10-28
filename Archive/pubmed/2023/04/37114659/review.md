## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the manuscript
- **Shared manuscript claim summary** The authors present CRPBSFinder, a quantitative model combining hidden Markov models, knowledge-based position-weighted matrices, and structure-based binding affinity matrices, for genome-wide prediction of cyclic AMP receptor protein binding sites. The model is claimed to outperform classic methods, provide quantitative binding affinity scores, identify 1089 novel CRP-regulated genes in E. coli, and be applicable to 35 other species with homologous CRP proteins.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Conclusions, Methods sections; Tables 1 and 2 referenced; Figures 1-5 and S1-S9 referenced; Supplementary Files 1-6 referenced
- **Missing materials affecting confidence** Actual figures, tables, and supplementary files not provided; detailed algorithm parameters and code not fully specified; raw datasets and test set composition not fully described; statistical test details for enrichment analyses not provided

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful computational tool for CRP binding site prediction with a novel combination of methods. The quantitative scoring approach and experimental validation are commendable. However, several technical details are insufficiently described, and some claims appear to exceed what the presented evidence can support. The cross-species application in particular requires more careful justification.
- **Who would be interested in the results, and why** Researchers studying transcription factor binding site prediction, bacterial gene regulation, CRP biology, and computational genomics. The quantitative scoring feature may interest those studying binding affinity prediction. The cross-species predictions could be useful for comparative genomics studies of CRP regulation.
- **Major strengths** 1) Novel combination of HMM, PWM, and structure-based energy matrices for binding site prediction. 2) Quantitative scoring that correlates with experimental binding affinity, validated by EMSA. 3) Comprehensive functional analysis of predicted regulons. 4) Experimental validation of three novel target genes. 5) Publicly available web tool and database.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** **Originality**: Moderate. The combination of methods is novel, but each component is established. **Scientific importance**: Moderate. Provides a useful tool and comprehensive predictions for E. coli CRP, but the conceptual advance is incremental. **Interdisciplinary readership**: Limited. Primarily relevant to computational biologists and bacterial gene regulation specialists. **Technical soundness**: Partially established. The model architecture is described, but key validation details and statistical rigor are insufficient. **Readability for nonspecialists**: Acceptable. The manuscript is generally clear, though some methods sections assume familiarity with bioinformatics tools.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model achieves higher prediction performance than classic methods and the combined model reaches the best ACCg performance.
- **Evidence pointer** Table 2, Supplementary File 1, Results section "Evaluation of the quantitative model"
- **Concern** The performance comparison with FIMO, MAST, HOCNN, and deepRAM is described only in text. The actual metrics, test set composition, and statistical significance of differences are not presented in the visible text. The test set contains 379 sequences, but the balance of positive and negative samples, the source of negative sequences, and whether the test set was used for any model tuning are not specified. Without these details, the claimed performance advantage cannot be independently assessed.
- **Why it matters** The central claim of the paper is that CRPBSFinder outperforms existing methods. If the comparison is not rigorously described and statistically validated, the primary contribution of the work is not established.
- **Resolution test** Provide the full performance table with all metrics (Sn, PPV, ACCg, and others), specify the exact composition of the test set, describe how negative samples were generated, and report confidence intervals or statistical tests for performance differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The prediction score quantitatively indicates the binding affinity of transcription factor binding sites.
- **Evidence pointer** Figure 2, Results section "Evaluation of the quantitative model"
- **Concern** The EMSA experiments with 10 selected binding sites are described as showing correlation between predicted scores and binding affinity. However, the visible text does not provide quantitative details of this correlation, such as correlation coefficients, the range of scores tested, or how binding affinity was quantified from EMSA band intensities. The claim that scores quantitatively indicate binding affinity requires more rigorous demonstration than visual inspection of gel shifts.
- **Why it matters** The quantitative nature of the score is a key differentiator of this tool from existing methods. If the correlation between score and affinity is not rigorously quantified, this claim is not supported.
- **Resolution test** Provide quantitative analysis of EMSA results, including correlation statistics between predicted scores and measured binding affinities, and describe how affinity was quantified from the experimental data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model predicted 1089 novel CRP-regulated genes in E. coli.
- **Evidence pointer** Results section "Functional classification of CRP regulons in E. coli", Supplementary Files 3 and 4
- **Concern** The definition of "novel" genes is not clearly stated. The text indicates these are genes not included in RegulonDB, but the criteria for considering a gene as CRP-regulated (e.g., distance from binding site to promoter, score threshold) are not fully described. Additionally, the false positive rate for novel predictions is not estimated. Given that the model predicts nearly 2000 CRP-regulated genes and only about 500 are experimentally confirmed, the false discovery rate among novel predictions could be substantial.
- **Why it matters** The identification of novel CRP-regulated genes is a major biological contribution of this work. If the criteria are not transparent and the error rate is not estimated, the reliability of these novel predictions is unclear.
- **Resolution test** Clearly define the criteria for novel gene classification, provide an estimate of the false discovery rate (e.g., through motif conservation analysis or comparison with independent datasets), and discuss the confidence level of novel predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model was applied to 35 other species with highly conserved CRP functional domains.
- **Evidence pointer** Results section "Prediction of CRP-binding sites on 35 species and construction of online tools and databases", Supplementary File 6
- **Concern** The text states that all 35 species have orthologous CRPs with E. coli, but the criteria for orthology and the conservation of the binding motif across these species are not described. The model was trained on E. coli data, and its application to other species assumes that the binding motif and energy landscape are conserved. This assumption is not tested or discussed. The percentage of predicted regulated genes ranges from 16% to 65% across species, which is a very wide range that is not explained.
- **Why it matters** The cross-species application is a significant extension of the work. If the conservation assumptions are not validated, the predictions for other species may be unreliable.
- **Resolution test** Provide evidence of motif conservation across the 35 species, describe the orthology criteria, and discuss the wide range in predicted regulated gene percentages. Consider validating predictions in at least one additional species experimentally or against published data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Construction of the CRP-binding site prediction model"
- **Evidence pointer** Methods section, Equations 1-6
- **Issue** The equations for the energy matrix, normalization, and scoring function are presented without sufficient explanation of the variables and parameters. For example, the meaning of K in Equation (2) and the specific values in the knowledge-based position importance matrix are not described in detail.
- **Required correction** Provide a clear definition of all variables in each equation and describe how the knowledge-based position importance matrix was derived from previous work.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Evaluation of the model"
- **Evidence pointer** Methods section, Results section "Evaluation of the quantitative model"
- **Concern** The training and testing data split is described, but the exact number of positive and negative samples in each set is not provided. The description of the negative sample generation as "randomly generated" is insufficient for reproducibility.
- **Required correction** Specify the exact composition of training and testing sets, describe the negative sample generation procedure in detail, and provide the data or a link to the data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Functional classification of CRP regulons in E. coli"
- **Evidence pointer** Results section, Methods section "Analysis of biological pathways regulated by CRPs"
- **Issue** The enrichment analysis uses a threshold of 0.1 for EASE score or P-value, which is unusually lenient. The text does not report the number of enriched terms, the effect sizes, or how multiple testing was handled beyond the Benjamini procedure.
- **Required correction** Report the number of enriched GO terms and KEGG pathways, provide effect sizes, and justify the choice of threshold.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Prediction of CRP-binding sites on 35 species and construction of online tools and databases"
- **Evidence pointer** Results section, Supplementary File 6
- **Issue** The text mentions that 19 of the 35 species are common pathogens, but the significance of this observation is not discussed. The functional implications of CRP regulation in these pathogens are not addressed.
- **Required correction** Discuss the potential implications of CRP regulation in pathogenic species and how the predictions could inform future studies.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph on lacZ
- **Issue** The discussion of the lacZ dual regulation mode is interesting but speculative. The text states that this dual regulation "might be widely present" in E. coli, but no systematic analysis is presented to support this claim.
- **Required correction** Either provide a systematic analysis of dual regulation patterns in the predicted data or temper the claim to reflect its speculative nature.

## Risk / unsupported claims
- The claim that the model "quantitatively indicates the binding affinity" is not rigorously supported by the visible evidence; the EMSA correlation is described qualitatively.
- The claim of "1089 novel CRP-regulated genes" is not supported with clear criteria for novelty or an estimate of the false discovery rate.
- The cross-species predictions for 35 species are presented without validation of the conservation assumptions underlying model transfer.
- The performance comparison with other methods is described but not fully presented with metrics and statistical tests.
- The statement that "the model not only can provide higher prediction performance than a classic method" is not fully supported without the complete comparison data.
- The claim that "CRPs may play an important role in fission yeast" based on predicted binding site abundance is speculative and not supported by functional evidence.