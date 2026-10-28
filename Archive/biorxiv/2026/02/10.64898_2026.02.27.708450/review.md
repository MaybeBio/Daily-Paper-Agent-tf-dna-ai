## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results and discussion, final conclusions, and supplementary declarations)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and support of claims based solely on the provided manuscript text. No external data, figures, or supplementary tables were available for inspection.
- **Shared manuscript claim summary** The authors present EMSA-seq as a high-throughput method to quantify the effect of single nucleotide variants on NKX2.1 transcription factor binding. They train convolutional neural network models on this data, validate with MST, X-ray crystallography, and ChIP-seq, and propose the models as tools to prioritise potential disease-causing variants in regulatory elements of CAHTP patients.
- **Visible evidence base** Text descriptions of methods and results; references to figures (Figures 1–11), supplementary tables (S1–S4), supplementary figures (S1–S2), GEO accession GSE319141, and PDB IDs 9U18 and 9U19. No actual data, figures, or tables were provided.
- **Missing materials affecting confidence** All figures, supplementary tables, supplementary figures, raw sequencing data, model code, hyperparameter settings, crystallographic data, and ChIP-seq dataset details. Without these, quantitative claims and validation results cannot be independently assessed.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question: whether in vitro high-throughput binding assays combined with deep learning can predict the functional impact of variants in NKX2.1 binding sites. The methodological approach is ambitious and the combination of EMSA-seq, neural networks, biophysical validation, and structural biology is potentially powerful. However, the manuscript as presented has several critical gaps. The central claim that the models can be used to prioritise disease-causing variants in CAHTP patients is not supported by direct evidence in the text. The validation strategy is incomplete: MST correlations are essentially zero, the ChIP-seq classification task is indirect, and no patient-derived variant data are presented. The crystallographic work is described but its connection to the predictive models is qualitative. The manuscript would benefit from clearer presentation of quantitative results, a more rigorous statistical framework, and a direct test of the clinical utility claim.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational genomics, and clinical genetics would be interested. Specifically, those studying transcription factor binding specificity, developing deep learning models for regulatory genomics, or seeking to interpret non-coding variants in Mendelian disorders would find the approach relevant. Clinicians and geneticists working on NKX2.1-related disorders (CAHTP, choreoathetosis, congenital hypothyroidism) may also be interested if the predictive utility is convincingly demonstrated.
- **Major strengths** 1) The use of EMSA-seq to generate quantitative binding data for millions of variants is a technically sound and scalable approach. 2) The comparison of multiple validation methods (MST, X-ray crystallography, ChIP-seq) is commendable in principle. 3) The development of a neural network model that can handle variable-length sequences and capture non-linear dependencies is a methodological advance over PWM-based approaches. 4) The structural analysis, including the identification of a specific conformational change upon a CACG mutation, provides mechanistic insight. 5) The authors acknowledge limitations of their approach, such as the trade-off between sequence diversity and read depth.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim-evidence mismatch
  - **Claim pointer** The abstract and final conclusions state that the models "can be used to evaluate whole genome sequencing data of CAHTP-patients in order to prioritise potential disease-causing variants in regulatory elements."
  - **Evidence pointer** Results and Discussion, "EMSA-seq derived models are able to identify NKX2.1 binding sites in genomic data"; Final conclusions
  - **Concern** The manuscript provides no direct evidence that the models can prioritise disease-causing variants in CAHTP patients. The ChIP-seq classification task demonstrates that the models can distinguish NKX2.1 peaks from other TF peaks, but this is not equivalent to identifying pathogenic variants. No patient-derived variant data, no functional validation in patient cells, and no comparison with known pathogenic regulatory variants are presented. The leap from in vitro binding prediction to clinical prioritisation is unsupported.
  - **Why it matters** The stated clinical utility is a major motivation for the work. Without direct evidence, the claim is speculative and could mislead potential users. The manuscript should either provide such evidence or clearly reframe the claim as a potential future application.
  - **Resolution test** Provide a validation cohort of known or suspected pathogenic variants in NKX2.1 binding sites from CAHTP patients or related disorders, and show that the model scores correlate with pathogenicity or functional impact. Alternatively, perform a prospective analysis of WGS data from unsolved CAHTP cases and demonstrate that the prioritised variants are enriched for functional effects.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation adequacy
  - **Claim pointer** The authors state that MST was used to validate the EMSA-seq data and models, and that the lack of correlation is due to the competitive nature of EMSA-seq.
  - **Evidence pointer** Results and Discussion, "EMSA-seq captures binding affinities at higher resolution compared to microscale thermophoresis through competitive binding dynamics"
  - **Concern** The correlation between MST Kd values and model predictions is essentially zero (r = 0.04, 0.00, 0.14 for CORE, FLANK, ALL models respectively). The authors attribute this to the competitive nature of EMSA-seq, but this is a post-hoc explanation. The manuscript does not provide a direct comparison between EMSA-seq enrichment and MST Kd for the same sequences, nor does it demonstrate that EMSA-seq can detect affinity differences that MST cannot. The claim that EMSA-seq has "higher resolution" is not substantiated with quantitative evidence. The validation of the models against an independent biophysical method fails, and the authors do not adequately address this.
  - **Why it matters** MST is a gold-standard biophysical method for measuring binding affinity. The lack of correlation undermines the quantitative accuracy of the EMSA-seq-derived models. If the models do not correlate with true binding affinity, their utility for predicting variant effects is questionable. The authors need to either reconcile this discrepancy with direct evidence or acknowledge that the models predict a different quantity (e.g., relative enrichment under competitive conditions) and validate accordingly.
  - **Resolution test** Perform a direct comparison of EMSA-seq enrichment values and MST Kd for a set of sequences. If they do not correlate, provide a mechanistic explanation supported by data (e.g., show that EMSA-seq captures kinetic or competitive effects that MST does not). Alternatively, validate the models against a different biophysical method that measures binding under competitive conditions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and data availability
  - **Claim pointer** The methods section describes the training of neural network models and the use of ChIP-seq data for validation.
  - **Evidence pointer** Materials and Methods, "Neural network model training" and "ChIP-seq validation"
  - **Concern** The manuscript states that model hyperparameters are in Supplementary Table S3 and software packages in Supplementary Table S2, but these are not provided in the submitted text. The ChIP-seq datasets are referenced as "Supplementary Table 4" (inconsistent numbering with S1–S3), and the specific accession numbers or processing details are not given. The GEO accession GSE319141 is mentioned, but the data are not accessible for review. Without these materials, the training and validation procedures cannot be reproduced or independently evaluated.
  - **Why it matters** Reproducibility is a core requirement for scientific claims, especially for computational models. The lack of access to code, hyperparameters, and validation data prevents reviewers and readers from assessing the robustness of the models and the validity of the ChIP-seq results.
  - **Resolution test** Provide all supplementary tables, code, and data access details in the revision. Ensure that the GEO submission is complete and publicly accessible. Include a detailed description of the ChIP-seq data processing pipeline and the exact datasets used.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigour
  - **Claim pointer** The authors report Spearman correlation coefficients for model comparisons and ChIP-seq classification performance.
  - **Evidence pointer** Results and Discussion, "EMSA-seq captures binding affinities at higher resolution compared to microscale thermophoresis through competitive binding dynamics" and "EMSA-seq derived models are able to identify NKX2.1 binding sites in genomic data"
  - **Concern** The manuscript reports correlation coefficients and qualitative statements about model performance (e.g., "performed relatively well", "out-performed all other models") without providing confidence intervals, p-values, or effect sizes. The classification task is described but no metrics such as AUC, precision, recall, or F1-score are given. The comparison between models and PWM is not quantified beyond correlation coefficients.
  - **Why it matters** Without statistical measures, the reader cannot assess the significance or reliability of the reported performance. The claim that the FLANK model outperforms the PWM needs quantitative support.
  - **Resolution test** Provide full statistical reporting for all comparisons, including confidence intervals, p-values, and classification metrics (AUC, precision, recall). Include error bars or variance measures for repeated experiments.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states "We employed EMSA-seq to quantify the effects of genetic variation on NKX2.1 binding strength" but does not specify the number of variants or the scale of the dataset.
  - **Required correction** Add a brief quantitative summary of the dataset size (e.g., number of unique sequences tested) to give readers a sense of scale.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Results and Discussion, "EMSA-seq is able to quantify the effects of single nucleotide variants on transcription factor binding in a high-throughput manner"
  - **Evidence pointer** Results and Discussion, first subsection
  - **Issue** The term "epistasis" is used to describe non-independence of nucleotide positions in binding. This is a non-standard use of the term, which typically refers to genetic interactions between loci. The authors should clarify or use a different term.
  - **Required correction** Define the term as used in this context or replace with "positional interdependence" or "non-additive effects."
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Materials and Methods, "ChIP-seq validation"
  - **Evidence pointer** Materials and Methods, "ChIP-seq validation"
  - **Issue** The supplementary table is referred to as "Supplementary Table 4" while earlier tables are numbered S1–S3. This inconsistency could confuse readers.
  - **Required correction** Use consistent numbering (e.g., Supplementary Table S4) throughout.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results and Discussion, "X-ray crystallography reveals interactions between NKX2.1 and the DNA sequence that align with patterns learnt by neural network models"
  - **Evidence pointer** Results and Discussion, crystallography subsection
  - **Issue** The manuscript mentions "eight variant DNA sequences" for crystallography but does not list which variants were tested or how they were selected.
  - **Required correction** Provide a list of the variants tested and the rationale for their selection.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results and Discussion, "EMSA-seq captures binding affinities at higher resolution compared to microscale thermophoresis through competitive binding dynamics"
  - **Evidence pointer** Results and Discussion, MST subsection
  - **Issue** The authors suggest that the lack of correlation between MST and model predictions is due to the competitive nature of EMSA-seq, but they do not discuss alternative explanations, such as differences in buffer conditions, protein construct, or DNA length.
  - **Required correction** Acknowledge and discuss alternative explanations for the discrepancy.
- **Technical failings that need to be addressed before the case is established** 1) The clinical utility claim (R1-M1) is unsupported and must be either substantiated with patient data or removed. 2) The validation against MST (R1-M2) fails and requires direct reconciliation or reframing. 3) Reproducibility materials (R1-M3) are missing and must be provided. 4) Statistical reporting (R1-M4) is inadequate and must be improved.
- **Assessment against Nature-style criteria**  
  *Originality*: The combination of EMSA-seq with deep learning for NKX2.1 is novel, and the generation of a large-scale in vitro binding dataset for this TF is a valuable contribution. However, the approach is not fundamentally new, as similar strategies have been applied to other TFs.  
  *Scientific importance*: The question of how variants in TFBSs contribute to disease is important, and NKX2.1 is a clinically relevant TF. However, the manuscript does not yet demonstrate that the models can identify disease-causing variants, which limits the immediate importance.  
  *Interdisciplinary readership*: The work bridges molecular biology, computational biology, and clinical genetics. The methods are described in sufficient detail for specialists, but the lack of quantitative results and clear validation will limit broader interest.  
  *Technical soundness*: The experimental methods are generally sound, but the validation strategy is incomplete and the statistical analysis is weak. The crystallographic work is described but not fully integrated into the model validation.  
  *Readability for nonspecialists*: The manuscript is generally well-written and the logic is clear, but the lack of quantitative summaries and the reliance on supplementary materials for key details reduce accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the central claims are not supported by the data presented. Major revisions are required to address the validation gap, provide reproducibility materials, and strengthen the statistical analysis. If these issues are resolved, the work could be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that the models can prioritise disease-causing variants in CAHTP patients is unsupported by direct evidence.
- The claim that EMSA-seq captures binding affinities at higher resolution than MST is not substantiated with quantitative data.
- The claim that the FLANK model outperforms the PWM in ChIP-seq classification is not supported by reported metrics.
- The claim that the crystallographic structures "align with patterns learnt by neural network models" is qualitative and not quantitatively demonstrated.
- The claim that AlphaFold predictions were validated against crystal structures is mentioned but the specific results (RMSD values) are only stated for model optimisation, not for the validation of novel variants.