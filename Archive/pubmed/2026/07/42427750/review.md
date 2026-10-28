## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary figure/table references)
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and reproducibility based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors characterize genomic features that predict estrogen receptor alpha (ER) binding to estrogen response elements (EREs) and the effects of that binding on gene expression in endometrial cancer (Ishikawa) versus breast cancer (T-47D) cells, using machine learning (Boruta feature selection, logistic regression) and functional validation via CRISPR knockout screens and follow-up experiments, identifying SOX17 as a key cell type-specific regulator of ER activity in endometrial cancer.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Methods, references to Supplementary Figures 1-9, Supplementary Tables S1-S4, and data accession numbers (GSE312322, GSE312323, GSE333956, GSE334097, GSE334100)
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S9, S1-S4) are referenced but not provided; raw sequencing data not independently accessible; no detailed statistical outputs (e.g., confidence intervals, effect sizes) for key comparisons; no code or analysis scripts provided; no details on the number of replicates for ChIP-seq, ATAC-seq, or RNA-seq experiments beyond general descriptions

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in understanding ER biology in endometrial cancer, where therapeutic options lag behind breast cancer. The use of EREs as a consistent genomic anchor across cell types is a thoughtful approach, and the integration of machine learning with functional CRISPR screening is commendable. The identification of SOX17 as a regulator of ER activity in endometrial cancer is potentially significant. However, the manuscript has several technical and conceptual issues that need to be addressed. The predictive models for regulatory EREs show limited sensitivity, and the causal link between SOX17 and ER activity, while supported by some experiments, requires stronger mechanistic evidence. The reliance on previously published datasets from different sources introduces potential batch effects that are not fully addressed. The manuscript is well-written and accessible, but the current evidence does not fully establish the claim that the identified features "uniquely" impact ER binding in endometrial cancer versus breast cancer, as the comparative analysis is limited by dataset availability and potential confounders.
- **Who would be interested in the results, and why** Researchers in cancer biology, particularly those studying hormone-dependent cancers (breast and endometrial), transcriptional regulation, and epigenomics. The findings on SOX17 could be of interest to those investigating endometrial cancer pathogenesis and potential therapeutic targets. The methodological approach (machine learning on genomic features) may appeal to computational biologists and bioinformaticians working on transcription factor binding prediction.
- **Major strengths** 1) The study addresses a clinically relevant and understudied area (ER biology in endometrial cancer) with a clear rationale. 2) The use of EREs as a common framework for comparing ER behavior across cell types is methodologically sound. 3) The integration of multiple data types (ChIP-seq, ATAC-seq, PRO-seq, HiChIP) and machine learning is comprehensive. 4) The CRISPR knockout screen provides functional validation that strengthens the computational findings. 5) The identification of SOX17 as a potential regulator of ER in endometrial cancer is novel and warrants further investigation. 6) The manuscript is clearly written and accessible to a broad audience.
- **Major Concerns** 
  - R1-M1: The claim of "uniquely" impacting ER binding in endometrial cancer is not fully supported by the comparative analysis, as the datasets for the two cell lines are not fully matched and the analysis does not directly test for statistical significance of differences in feature importance between cell lines.
  - R1-M2: The definition of "regulatory EREs" based on proximity to differentially expressed genes within 100 kb is simplistic and may misclassify many EREs; the authors acknowledge this but do not provide alternative analyses to strengthen the definition.
  - R1-M3: The predictive models for regulatory EREs have low sensitivity (e.g., 34.8-44.4%), which limits their practical utility and the strength of conclusions drawn from them.
  - R1-M4: The causal role of SOX17 in regulating ER activity is not fully established; the authors show correlations and some loss-of-function effects, but the mechanism (direct vs. indirect) remains unclear.
  - R1-M5: The potential for batch effects and technical artifacts due to combining datasets from different sources is acknowledged but not systematically addressed (e.g., through batch correction or sensitivity analyses).
- **Minor Comments** 
  - R1-m1: The abstract states "less than 3%" of EREs contribute to binding or regulation, but the exact numbers (2.6% bound, 43.4% of bound regulatory) are only in the results; consider including these in the abstract for clarity.
  - R1-m2: The Methods section for the CRISPR screen lacks details on the number of biological replicates, sequencing depth, and quality control metrics.
  - R1-m3: The authors mention "HCI-EC-23 has lower ER activity than Ishikawa cells" but do not provide quantitative evidence for this claim.
  - R1-m4: The discussion of SOX17's role in endometrial biology is thorough but could be more concise; some speculative statements (e.g., about PRC2) could be tempered.
  - R1-m5: The manuscript would benefit from a figure summarizing the key findings and the proposed model of ER regulation in endometrial cancer.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: The study is original in its focus on endometrial cancer ER biology and the use of EREs as a comparative framework. The identification of SOX17 is novel. However, the overall approach (machine learning on genomic features) is not entirely new, and the findings, while interesting, do not represent a paradigm shift.
  - Scientific importance: The topic is important, given the rising incidence of endometrial cancer and the lack of effective ER-targeted therapies. The findings could inform future therapeutic strategies. However, the clinical relevance is not directly demonstrated.
  - Interdisciplinary readership: The work bridges cancer biology, genomics, and computational biology, and would appeal to readers across these fields. The writing is accessible.
  - Technical soundness: The methods are generally sound, but there are concerns about dataset comparability, the definition of regulatory EREs, and the low sensitivity of predictive models. The functional validation is a strength, but the mechanistic depth is limited.
  - Readability for nonspecialists: The manuscript is well-written and the concepts are explained clearly. The use of figures (not provided) would aid comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The study has merit and the findings are potentially important, but the current evidence does not fully support the strong claims made, particularly regarding "uniqueness" and the predictive power of the models. The authors should address the concerns raised, particularly around dataset comparability, the definition of regulatory EREs, and the causal role of SOX17.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The authors claim that certain genomic features "uniquely" impact ER binding in endometrial cancer, implying cell type-specific mechanisms.
- **Evidence pointer** Results section, Figures 2G-H, Supplementary Figure 2D
- **Concern** The comparative analysis between Ishikawa and T-47D cells is based on datasets that are not fully matched (e.g., different sources, potential batch effects). The authors do not perform a formal statistical test to compare feature importance between cell lines; they only report which features are important in each cell line. The claim of "uniqueness" requires a direct comparison showing that the importance of a feature in one cell line is significantly different from its importance in the other.
- **Why it matters** The central thesis of the manuscript is that ER regulation differs between endometrial and breast cancer. Without a rigorous statistical comparison, the claim of cell type-specific features is not established, weakening the overall contribution.
- **Resolution test** Perform a formal statistical comparison of feature importance scores between cell lines (e.g., using a permutation test or bootstrap) and report which features are significantly different. Alternatively, use a multi-task learning approach that explicitly models cell type interactions. If the analysis is not feasible due to dataset limitations, temper the language to "features that are predictive in endometrial cancer" rather than "uniquely."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors define "regulatory EREs" as bound EREs within 100 kb of a gene that changes expression in response to estrogen.
- **Evidence pointer** Methods section, "Estrogen response element identification and classification"
- **Concern** The 100 kb distance cutoff is arbitrary and may include many EREs that are not functionally linked to the nearby gene. The authors acknowledge this limitation but do not provide alternative analyses, such as using HiChIP data to define direct enhancer-promoter interactions or using a more stringent cutoff. This could lead to misclassification of regulatory EREs and affect all downstream analyses.
- **Why it matters** The definition of the outcome variable (regulatory vs. non-regulatory) is critical to the validity of the machine learning models. If the outcome is noisy, the identified features may not be reliable.
- **Resolution test** Perform sensitivity analyses using different distance cutoffs (e.g., 50 kb, 25 kb) or using HiChIP-defined interactions to define regulatory EREs. Show that the main conclusions are robust to these changes. If the results are sensitive, discuss the implications and consider using a more conservative definition.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that their models can predict regulatory EREs with reasonable accuracy, but the reported sensitivities are low (34.8-44.4%).
- **Evidence pointer** Results section, "Predictive multi-variable model of regulatory EREs", Supplementary Figure 7
- **Concern** The low sensitivity of the models for regulatory EREs means that the majority of regulatory EREs are not identified. This limits the practical utility of the models and the strength of the conclusions that can be drawn about the features that predict regulatory activity. The authors acknowledge this but do not discuss the implications in detail.
- **Why it matters** If the models cannot accurately identify regulatory EREs, the claim that certain features are important for regulatory activity is weakened. The findings may not be generalizable.
- **Resolution test** Discuss the trade-off between sensitivity and specificity and the potential reasons for low sensitivity (e.g., missing features, noisy outcome). Consider using alternative modeling approaches (e.g., random forest, gradient boosting) or incorporating additional data types. If the low sensitivity is inherent, temper the conclusions and suggest that the models are useful for identifying a subset of regulatory EREs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The authors conclude that SOX17 controls ER activity in endometrial cancer cells based on CRISPR knockout experiments.
- **Evidence pointer** Results section, "SOX17 is important for ER activity in Ishikawa cells", Figures 5-6
- **Concern** The experiments show that SOX17 knockout reduces ER activity and ER binding, but the mechanism is not fully explored. The authors suggest two possibilities: SOX17 regulates ESR1 transcription and SOX17 co-binds with ER at target sites. However, they do not directly test whether SOX17's effect on ER activity is primarily through ESR1 expression or through direct co-regulation. The relative contribution of these two mechanisms is unclear.
- **Why it matters** Understanding the mechanism is important for assessing the therapeutic potential of targeting SOX17. If the effect is indirect (through ESR1), the implications are different than if SOX17 is a direct cofactor.
- **Resolution test** Perform add-back experiments (e.g., overexpress ESR1 in SOX17 KO cells) to determine if restoring ESR1 expression rescues ER activity. Alternatively, perform chromatin accessibility or DNA methylation analyses to understand how SOX17 regulates ESR1 expression. If the mechanism is primarily through ESR1, discuss the implications for therapeutic targeting.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "less than 3%" of EREs are bound, but the specific percentages (2.6% in Ishikawa, 2.8% in T-47D) are only in the results. Including these numbers in the abstract would provide more concrete information.
- **Required correction** Add the specific percentages to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, CRISPR screen
- **Evidence pointer** Methods section, "Post-screen enrichment analysis using MAGeCK"
- **Issue** The Methods section for the CRISPR screen does not specify the number of biological replicates, sequencing depth, or quality control metrics (e.g., number of reads per sample, mapping rate).
- **Required correction** Add details on the number of replicates, sequencing depth, and QC metrics to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, HCI-EC-23 validation
- **Evidence pointer** Results section, "Predictive multi-variable model of ERE binding"
- **Issue** The statement that "HCI-EC-23 has lower ER activity than Ishikawa cells" is not supported by quantitative data. It is unclear how this was determined.
- **Required correction** Provide quantitative evidence (e.g., ER protein levels, ER ChIP-seq signal) or cite a reference for this claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, PRC2
- **Evidence pointer** Discussion section
- **Issue** The discussion of PRC2's role is speculative and could be more balanced. The authors suggest that EZH2 and SUZ12 are ER enabling, which is unexpected given their role in repression, but they do not provide a clear hypothesis for how this might work.
- **Required correction** Provide a more nuanced discussion, acknowledging the complexity of PRC2 function and suggesting potential mechanisms or experiments to test the hypothesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Results section, all figures
- **Issue** The manuscript would benefit from a summary figure that integrates the key findings, such as a model of ER regulation in endometrial cancer versus breast cancer.
- **Required correction** Add a schematic figure summarizing the proposed model and the role of SOX17.

## Risk / unsupported claims
- The claim that identified features "uniquely" impact ER binding in endometrial cancer is not statistically supported by the comparative analysis.
- The definition of "regulatory EREs" based on a 100 kb distance cutoff is arbitrary and may not accurately reflect functional regulation.
- The low sensitivity of the predictive models for regulatory EREs limits the strength of conclusions about the features that predict regulatory activity.
- The causal role of SOX17 in regulating ER activity is not fully established; the mechanism (direct vs. indirect) remains unclear.
- The statement that HCI-EC-23 has "lower ER activity" than Ishikawa cells is not quantitatively supported.
- The potential for batch effects due to combining datasets from different sources is acknowledged but not systematically addressed.