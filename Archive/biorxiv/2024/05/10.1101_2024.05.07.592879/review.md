## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Materials and Methods, and supplementary figure/table references)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the provided evidence, and clarity of presentation
- **Shared manuscript claim summary** The authors present a two-step machine learning approach to predict both the functional states (active/inactive) and types (enhancer/silencer) of cis-regulatory modules (CRMs) across human cell/tissue types, and report that a substantial fraction of CRMs are dual-functional (acting as both enhancers and silencers), with distinct properties in length and TFBS density.
- **Visible evidence base** Abstract, full Introduction, full Results section, full Materials and Methods, references to Figures 1-6, Supplementary Figures S1, and Supplementary Tables S1-S11
- **Missing materials affecting confidence** The actual figures and supplementary tables are not provided. This limits verification of quantitative results, statistical analyses, and detailed method performance metrics.

## Reviewer
- **Overall assessment** The manuscript addresses an important gap in CRM prediction by extending a two-step strategy to simultaneously classify functional type and state. The core idea is a logical extension of prior work and the results, if reproducible, would be of interest to the gene regulation community. However, the current manuscript has several technical and conceptual issues that need to be addressed. The reliance on a single data source (Cistrome) for training and the lack of independent validation for the dual-functional predictions are significant concerns. The claim of prevalence of dual-functional CRMs is interesting but requires stronger evidence to rule out technical artifacts. The manuscript is generally well-written and the methods are described in sufficient detail to be replicated, but the presentation of results is incomplete without the figures.
- **Who would be interested in the results, and why** Researchers in gene regulation, epigenomics, and computational biology would be interested. The work provides a new tool for predicting silencers and dual-functional CRMs, which are understudied compared to enhancers. The finding that dual-functional CRMs are prevalent could have implications for understanding the complexity of gene regulation and interpreting non-coding variants.
- **Major strengths**
    1.  The two-step approach is a logical and potentially powerful strategy that separates CRM location prediction from functional state prediction, which may reduce false positives compared to one-step methods.
    2.  The study addresses a significant gap by explicitly modeling silencers and dual-functional CRMs, which are often ignored.
    3.  The use of only three epigenetic marks for prediction, if validated, would make the method widely applicable to datasets with limited epigenomic profiling.
    4.  The analysis of CRM properties (length, TFBS density) across functional types provides a useful characterization.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness / Methodological Rigor
    - **Claim pointer** The claim that the method can "accurately predict the functional types and states of CRMs" is central to the paper.
    - **Evidence pointer** Results section "Functional states of CRMs as silencers and enhancers can be accurately predicted using three epigenetic marks", Figure 1, Supplementary Figure S1
    - **Concern** The performance of the models is evaluated using 10-fold cross-validation on a pooled dataset. This is a weak form of validation. The models are trained and tested on data from the same cell/tissue types. It is unclear if the models generalize to new cell/tissue types not represented in the training data. A more rigorous evaluation would involve held-out cell/tissue types (e.g., leave-one-cell-type-out cross-validation) to assess the model's ability to predict in unseen biological contexts. The high AUROC values reported (0.96-0.98) might be optimistic due to this potential data leakage.
    - **Why it matters** The primary utility of the method is to predict CRM states in new cell/tissue types where experimental data is limited. If the model does not generalize across cell types, its practical value is significantly diminished. The current validation strategy does not demonstrate this key capability.
    - **Resolution test** The authors should perform a leave-one-cell-type-out cross-validation or an external validation on a completely independent set of cell/tissue types not used in training. The AUROC and other metrics from this evaluation should be reported and compared to the in-sample cross-validation results.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Scientific Importance / Validity of Conclusions
    - **Claim pointer** The claim that "dual functional CRMs and silencers might be more prevalent than previously assumed" is a key finding.
    - **Evidence pointer** Results section "At least 10% of the CRMs are dual functional", Figure 2A, Figure 4
    - **Concern** The classification of a CRM as "dual-functional" relies on the independent predictions of the enhancer and silencer models. The authors acknowledge that a CRM with a very strong CA signal could be predicted as both active enhancer and active silencer, potentially inflating the number of dual-functional CRMs. While they apply a filtering step for type I dual-functional CRMs requiring at least one enhancer and one silencer mark, this filter is only applied to the 44,153 type I CRMs. The 39,832 type II CRMs, which are dual-functional across different cell types, are not subject to this filter. The possibility that these type II CRMs are artifacts of the high weight of CA signal in both models needs to be more thoroughly investigated.
    - **Why it matters** The prevalence of dual-functional CRMs is a central conclusion of the paper. If this is an artifact of the model's reliance on a single dominant feature (CA), the conclusion is not valid. The authors need to provide stronger evidence that these predictions reflect true biology and not a technical limitation.
    - **Resolution test** The authors should analyze the feature contributions for the predicted dual-functional CRMs. For example, they could show that the distribution of enhancer and silencer mark signals (H3K4me1/H3K27ac vs. H3K9me3/H3K27me3) is distinct for dual-functional CRMs compared to those predicted as only enhancers or only silencers. They could also perform a sensitivity analysis by retraining the models without the CA feature to see if the proportion of dual-functional CRMs changes dramatically.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical Soundness / Evidence
    - **Claim pointer** The claim that "Most dual functional CRMs function either as enhancers or silencers in different cell/tissue types (Type I), while some have dual functions regulating different genes in the same cell/tissue types (Type II)" and the subsequent analysis of target genes.
    - **Evidence pointer** Results section "Type I dual functional CRMs might execute dual functions by regulating different genes in the same cell type", Figure 5
    - **Concern** The analysis of target genes for dual-functional CRMs is based on Hi-C data from a single cell line (K562). The authors use this to infer potential target genes for CRMs in other cell types. This is a significant assumption, as chromatin interactions are highly cell-type-specific. The conclusion that a CRM regulates different genes in the same cell type (Type II) is based on this cross-cell-type Hi-C data, which may not be valid. The analysis should be performed using Hi-C data from the relevant cell types, or the limitations of this approach should be clearly acknowledged.
    - **Why it matters** The functional interpretation of dual-functional CRMs depends on correctly identifying their target genes. Using Hi-C data from an unrelated cell line could lead to incorrect assignments of target genes and thus incorrect conclusions about their function.
    - **Resolution test** The authors should either use cell-type-specific Hi-C data where available, or clearly state this as a limitation and temper their conclusions. They could also use other methods to predict target genes, such as eQTL analysis or correlation of enhancer activity with gene expression across the cell types.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Figure 1B
    - **Evidence pointer** Results section "Functional states of CRMs as silencers and enhancers can be accurately predicted using three epigenetic marks"
    - **Issue** The UpSet plot in Figure 1B is described as showing the overlap of peaks from the three marks. It is unclear if this is showing the overlap of peaks in the positive set or in the entire genome. The description should be clarified.
    - **Required correction** Clarify in the figure legend and text what exactly is being plotted in the UpSet plot.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Materials and Methods, "Epigenetic mark feature scores"
    - **Evidence pointer** Materials and Methods section
    - **Issue** The formula for the raw feature score is not fully defined in the text provided. The variables are described, but the exact equation is missing.
    - **Required correction** Ensure the complete formula is included in the final version of the manuscript.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Results section "Varying portions of the 1.2M CRMs are active as enhancers or silencers in various cell/tissue types"
    - **Evidence pointer** Figure 2A, Supplementary Tables S4, S5
    - **Issue** The text states that the number of active enhancers and silencers varies highly across cell types. It would be useful to know if these numbers correlate with any known biological properties of the cell types, such as their developmental origin or function.
    - **Required correction** A brief discussion of the variation in the number of active CRMs across cell types would strengthen the manuscript.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Results section "The substantial or complete overlaps between enhancer and silencer epigenetic marks peaks along type I dual functional CRMs"
    - **Evidence pointer** Figure 4C
    - **Issue** The text states that 55% of type I dual-functional CRMs have completely overlapping enhancer and silencer mark peaks. It is unclear how this overlap is calculated and what the threshold for "complete" overlap is.
    - **Required correction** Provide a clear definition of the "overlapping ratio" and how "complete" overlap is defined in the text or figure legend.

## Risk / unsupported claims
- The claim that the method can predict functional states and types using only three epigenetic marks is supported by the in-sample cross-validation, but the generalizability to new cell types is not established.
- The claim that dual-functional CRMs are prevalent is supported by the model predictions, but the biological validity of these predictions is not independently verified.
- The claim that type I dual-functional CRMs regulate different genes in the same cell type is based on Hi-C data from a single, potentially irrelevant, cell line (K562) and is therefore not well-supported.
- The claim that "validated" silencers from silencerDB that do not overlap the authors' CRMs are false positives is based on their neutral evolutionary signature. This is an indirect inference and could be an overstatement.