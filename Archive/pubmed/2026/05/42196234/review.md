## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Scientific soundness, technical rigor, validity of claims relative to provided evidence, and suitability for a high-impact generalist journal
- **Shared manuscript claim summary** The authors propose an integrated pipeline combining differential expression, WGCNA, PPI networks, three machine-learning algorithms, reverse network pharmacology, molecular docking, molecular dynamics simulations, and in vivo rat experiments to identify JUN and C3 as candidate diagnostic biomarkers for CKD and to suggest resveratrol as a therapeutic candidate acting via suppression of MAPK/JNK signaling.
- **Visible evidence base** Human transcriptomic datasets (GSE175759, GSE37171, GSE66494); bioinformatics analyses (WGCNA, GO/KEGG, GSEA, CIBERSORT); machine-learning feature selection; reverse network pharmacology compound screening; molecular docking and 100 ns MD simulations; in vivo adenine-induced CKD rat model with biochemical, histological, immunofluorescence, RNA-seq, and Western blot data
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S5) referenced but not provided; detailed machine-learning parameter settings and MD simulation protocols stated to be in Supplementary Materials but not available; raw Western blot images not shown; no information on antibody validation or catalog numbers; no data on statistical power calculations for animal group sizes; no information on blinding or randomization in animal experiments

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive multi-omics and experimental study addressing an important clinical problem. The integration of computational prediction with in vivo validation is commendable in scope. However, several technical and conceptual issues undermine the strength of the conclusions. The discrepancy between human transcriptomic data (JUN downregulated) and rat protein data (c-Jun upregulated) is acknowledged but not fully resolved. The claim that JUN and C3 serve as diagnostic biomarkers is based on retrospective tissue-level transcriptomic data without prospective validation in accessible biofluids. The mechanistic link between resveratrol and MAPK/JNK suppression is supported by correlative rather than causal evidence. The manuscript would benefit from clearer presentation of key computational parameters and additional experimental controls.

- **Who would be interested in the results, and why** Researchers in nephrology, particularly those focused on CKD biomarkers and fibrosis mechanisms, would find the candidate gene identification relevant. Investigators studying natural compounds for renal protection, especially resveratrol, would be interested in the in vivo efficacy data. Methodologists developing integrated bioinformatics-machine learning pipelines for disease gene discovery may find the analytical framework useful. However, the clinical translational relevance is limited by the retrospective nature of the human data and the use of a single animal model.

- **Major strengths**  
  1. The study integrates multiple complementary approaches (transcriptomics, machine learning, network pharmacology, computational chemistry, and in vivo experiments) in a single coherent pipeline, which is methodologically ambitious.  
  2. The use of three independent machine-learning algorithms with intersection analysis reduces the risk of algorithm-specific bias in feature selection.  
  3. External validation of candidate gene expression in independent datasets strengthens the generalizability of the transcriptomic findings.  
  4. The in vivo experiments include multiple outcome measures (renal function, histology, fibrosis markers, transcriptomics, protein expression) providing a multifaceted assessment of resveratrol efficacy.  
  5. The authors acknowledge and discuss the discrepancy between human transcriptomic and rat protein data, showing scientific transparency.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and causal inference
- **Claim pointer** The manuscript claims that resveratrol exerts anti-fibrotic effects via suppression of MAPK/JNK signaling, specifically through downregulation of JNK-mediated c-Jun phosphorylation.
- **Evidence pointer** Section 2.9, Figure 9
- **Concern** The evidence presented is correlational. The authors show that resveratrol treatment is associated with reduced p-JNK/JNK and p-c-Jun/c-Jun ratios, but no causal experiments (e.g., JNK agonist, constitutively active JNK, or knockdown/overexpression of JUN) are performed to demonstrate that MAPK/JNK suppression is necessary or sufficient for the anti-fibrotic effect. Alternative mechanisms, such as direct antioxidant effects or modulation of other signaling pathways, are not excluded.
- **Why it matters** The title and conclusions assert a specific mechanism ("Anti-Fibrotic Mechanism of Resveratrol via MAPK/JNK Signaling"). Without causal evidence, the mechanistic claim is overstated. The observed association could be epiphenomenal to the general anti-inflammatory or anti-fibrotic effects of resveratrol.
- **Resolution test** Provide loss- or gain-of-function experiments for JNK or c-Jun in the rat model or in vitro, or temper the mechanistic claim to "associated with modulation of MAPK/JNK signaling" rather than "mechanism via."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biomarker validation and clinical relevance
- **Claim pointer** The manuscript claims JUN and C3 are "candidate diagnostic biomarkers" for CKD with "promising discriminatory performance."
- **Evidence pointer** Sections 2.3, 4.9, Figures 4H–J, Supplementary Table S1
- **Concern** The biomarker claim is based on retrospective tissue-level transcriptomic data from datasets with heterogeneous CKD etiologies (GSE175759 includes multiple glomerular diseases). The AUC values are reported for the training set and one external validation set, but the manuscript does not report whether these AUC values are adjusted for clinical covariates (age, sex, eGFR, proteinuria) that are routinely available and would be expected to confound or improve diagnostic performance. No comparison to established biomarkers (e.g., serum creatinine, cystatin C, NGAL, KIM-1) is provided. The clinical utility of tissue-based JUN/C3 expression as a diagnostic biomarker is questionable since kidney biopsy is invasive and not performed for diagnostic screening.
- **Why it matters** The term "diagnostic biomarker" implies clinical applicability. Without demonstration of added value over existing biomarkers, in accessible samples, and in prospective cohorts, the claim is premature and potentially misleading.
- **Resolution test** Provide multivariable analysis adjusting for clinical covariates, compare AUC against standard biomarkers, or reframe the claim as "tissue-based candidate biomarkers associated with CKD" rather than "diagnostic biomarkers."

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reproducibility
- **Claim pointer** The manuscript states that detailed machine-learning parameter settings, MD simulation protocols, and supplementary figures (S1–S5) are provided in Supplementary Materials.
- **Evidence pointer** Sections 4.8, 4.12, Supplementary Materials (referenced but not provided)
- **Concern** The supplementary materials are not available for review. This includes critical methodological details: LASSO regularization parameters, SVM-RFE kernel and feature ranking method, random forest hyperparameters and number of trees, MD simulation force field, water model, equilibration protocol, and convergence criteria. Supplementary Figures S1–S5 are referenced in the main text but cannot be evaluated. The RNA-seq analysis pipeline (Section 4.17) lacks detail on alignment, quantification, and differential expression tools.
- **Why it matters** Reproducibility is a core scientific standard. Without access to these details, the computational and simulation results cannot be independently verified or replicated. The MD simulation results in particular are presented only as a summary statement without quantitative data.
- **Resolution test** Provide all supplementary materials for review, including full parameter settings, simulation protocols, and all referenced figures and tables.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Species discrepancy and interpretation
- **Claim pointer** The manuscript states that JUN was downregulated in human CKD transcriptomic data but Jun was upregulated in the rat model, and this discrepancy is attributed to "species divergence" and the distinction between mRNA and protein levels.
- **Evidence pointer** Sections 2.3, 2.6, 2.7, 2.9, Figures 4E–G, 7C–E, 9A–D
- **Concern** The direction of JUN expression change is opposite between human datasets and the rat model. The authors suggest this may reflect species differences or post-transcriptional regulation, but no direct evidence is provided to support either explanation. The rat model shows increased c-Jun protein and p-c-Jun, while human data show decreased JUN mRNA. If JUN is proposed as a diagnostic biomarker, the direction of change should be consistent. If the rat model is used to validate the therapeutic mechanism, the opposite expression pattern raises questions about the model's relevance to human disease.
- **Why it matters** The core translational logic of the study depends on the consistency between human and animal data. An unexplained reversal in the key gene's expression undermines the validity of both the biomarker claim and the mechanistic model.
- **Resolution test** Provide additional analysis (e.g., protein-level data from human samples, if available) or a more rigorous discussion of why the opposite direction does not invalidate the translational conclusions. Alternatively, acknowledge this as a limitation that prevents direct extrapolation from the rat model to human disease.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor in animal experiments
- **Claim pointer** The manuscript reports significant differences between groups in biochemical markers, histology, and protein expression.
- **Evidence pointer** Sections 2.6, 2.7, 2.9, Figures 6, 7, 9
- **Concern** The manuscript does not report the number of independent biological replicates per group for each assay, whether the data met assumptions for parametric testing, or how multiple comparisons were handled. Group sizes of n=6 per group are stated, but it is unclear if all assays were performed on all animals. No effect sizes or confidence intervals are reported. The Western blot quantification methodology is described but the number of replicate blots is not stated.
- **Why it matters** Without clear reporting of sample sizes, statistical methods, and variance, the reliability of the reported differences cannot be assessed. This is particularly important given the small group sizes.
- **Resolution test** Provide complete statistical reporting: exact n per group per assay, normality testing, multiple comparison correction methods, and effect sizes with confidence intervals.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting clarity
- **Affected element** Section 4.5
- **Evidence pointer** Section 4.5
- **Issue** The text states "DEGs identified in Section 2.3 were intersected with genes from the module showing the strongest association in Section 2.4." This cross-referencing is confusing because Section 2.3 describes machine-learning screening, not DEG identification, and Section 2.4 describes functional enrichment, not module identification. The section numbering appears inconsistent with the results structure.
- **Required correction** Correct the section cross-references to accurately point to the relevant results subsections.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Section 2.5, Figure 5
- **Concern** The MD simulation results are described only in terms of RMSD, Rg, SASA, and hydrogen bond counts. No data on binding free energy calculations (e.g., MM-PBSA) are presented, which would strengthen the claim of stable binding. The RMSD values are reported in Angstroms but the equilibration period is not clearly distinguished from the production phase.
- **Required correction** Provide additional MD analysis metrics or clarify the limitations of the current analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion of resveratrol's mechanisms in CKD is extensive but does not critically evaluate conflicting evidence in the literature regarding resveratrol's bioavailability and its translation to human efficacy. The authors mention low oral bioavailability as a limitation but do not discuss strategies to overcome this.
- **Required correction** Add a brief discussion of bioavailability challenges and potential formulation approaches, or acknowledge this as a key translational barrier.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Throughout
- **Evidence pointer** Abstract, Sections 1, 3
- **Issue** The term "reverse network pharmacology" is used to describe the approach, but the distinction from conventional network pharmacology is not clearly defined. The authors state they used a "target-seeking-drug" strategy, but the methods described (compound-target network construction from databases) appear similar to standard network pharmacology approaches.
- **Required correction** Clarify what makes the approach "reverse" and how it differs methodologically from established network pharmacology workflows.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The study workflow figure is described but not visible in the provided text. If it is a schematic, it should clearly indicate the data flow and analysis steps with sufficient detail for readers to follow the methodology.
- **Required correction** Ensure Figure 1 is self-explanatory and includes all key analysis steps and dataset identifiers.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (causal mechanism not established), R1-M2 (biomarker claim overextended), R1-M3 (missing methodological details), R1-M4 (unresolved species discrepancy), R1-M5 (incomplete statistical reporting)

- **Assessment against Nature-style criteria**  
  **Originality:** Moderate. The integration of multiple computational methods with in vivo validation is not entirely novel, as similar pipelines have been published. The specific combination of reverse network pharmacology with machine learning applied to CKD is somewhat distinctive but represents an incremental methodological advance rather than a paradigm shift.  
  **Scientific importance:** Moderate. CKD biomarkers and therapies are important clinical needs. However, the candidate biomarkers are not validated in accessible biofluids or prospective cohorts, and the therapeutic mechanism is not causally established. The potential clinical impact is therefore uncertain.  
  **Interdisciplinary readership:** Limited. The study bridges bioinformatics, computational chemistry, and nephrology, which could appeal to multiple communities. However, the presentation is heavily weighted toward the computational aspects, and the experimental validation is relatively superficial. The mechanistic depth may not satisfy either computational or experimental specialists fully.  
  **Technical soundness:** The computational analyses appear reasonable but cannot be fully assessed due to missing methodological details. The animal experiments are described but lack statistical rigor in reporting. The discrepancy between human and rat JUN expression is a significant technical concern.  
  **Readability for nonspecialists:** The abstract and introduction are accessible, but the results section assumes familiarity with multiple specialized techniques (WGCNA, SVM-RFE, MD simulations). The manuscript would benefit from clearer explanations of key concepts for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an ambitious integrated pipeline with potentially interesting findings, but major concerns regarding causal mechanism, biomarker validation, species discrepancy, and missing methodological details prevent endorsement. The authors should be encouraged to address these concerns through additional experiments, revised claims, and complete reporting. If the mechanistic claim is tempered to an association and the biomarker claim is reframed as hypothesis-generating, the manuscript could be reconsidered after major revision.