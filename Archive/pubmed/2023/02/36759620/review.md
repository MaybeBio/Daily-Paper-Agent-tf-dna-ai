## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific soundness, technical rigor, validity of claims relative to presented evidence, and suitability for a high-impact generalist journal
- **Shared manuscript claim summary** The authors characterize the gene regulatory activities of the PML::RARA fusion protein in acute promyelocytic leukemia using integrated multi-omics data (RNA-seq, Cut&Run, ATAC-seq, promoter capture Hi-C) in an inducible cell line model and patient samples. They report that PML::RARA binding does not uniformly repress target genes, and they develop a machine learning approach (REBEL) to identify transcription factor binding site combinations that distinguish regulatory outcomes.
- **Visible evidence base** Results sections with figures 1-7, supplementary figure descriptions, methods section, and figure legends
- **Missing materials affecting confidence** Raw data files, supplementary tables, detailed model hyperparameters, code availability, and complete figure panels were not provided for independent verification

## Reviewer

### Overall assessment
This manuscript addresses an important question in APL biology: how the PML::RARA fusion protein exerts context-specific transcriptional effects. The multi-omics approach is comprehensive and the finding that PML::RARA binding does not uniformly repress gene expression is a valuable contribution that challenges simplified models. The machine learning framework is innovative and potentially useful to the field. However, several technical concerns limit the strength of the conclusions as currently presented. The lack of replicates for key validation experiments, the absence of direct functional validation of predicted regulatory mechanisms, and the limited patient sample size (n=2) weaken the generalizability claims. The manuscript would benefit from clearer presentation of the machine learning methodology and more rigorous statistical treatment of the integrative analyses.

### Who would be interested in the results, and why
Researchers studying transcriptional regulation in leukemia, particularly those focused on fusion oncoproteins and their chromatin-level effects. The multi-omics integration strategy and machine learning approach will also interest computational biologists working on gene regulatory networks. Clinically oriented investigators studying APL pathogenesis and potential therapeutic targets would find the patient sample comparisons relevant.

### Major strengths
1. Comprehensive multi-omics dataset generation in a well-established inducible model system
2. Novel finding that PML::RARA binding leads to both activation and repression, challenging the prevailing repression-centric model
3. Integration of chromatin conformation data (capture Hi-C) with gene expression and transcription factor binding, which is relatively uncommon in this field
4. The machine learning framework (REBEL) provides a systematic approach to dissect complex regulatory codes
5. Validation of key findings in primary patient samples, albeit limited in number

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "genes whose regulatory elements recruit PML::RARA are not uniformly transcriptionally repressed... but also may be upregulated or remain unchanged" and that this is a robust finding from their integrated analysis.
- **Evidence pointer** Figure 2c, 2d; Supplementary Figure 2o-2v
- **Concern** The classification of PML::RARA-bound genes into up/down/no-change categories relies on a 5-hour zinc induction time point. The authors do not provide evidence that this time point captures the full repertoire of PML::RARA-mediated transcriptional changes. Early direct targets may show different kinetics than secondary effects. Additionally, the comparison with NB4 cells (constitutive PML::RARA) shows only 67% overlap in binding sites, raising questions about whether the inducible system fully recapitulates the steady-state binding landscape.
- **Why it matters** The central claim of context-specific regulatory outcomes depends on the assumption that the 5-hour time point and the inducible system adequately represent PML::RARA function. If the time point is too early or too late for certain gene classes, the distribution of up/down/no-change categories could be misrepresented.
- **Resolution test** Provide a time course analysis (e.g., 2h, 5h, 12h, 24h) for a subset of genes to demonstrate that the 5-hour time point captures both early and sustained transcriptional responses. Alternatively, perform RNA-seq at multiple time points and show that the proportion of up/down/no-change categories remains stable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "REBEL uncovered clear discrimination of TFBS patterns within promoters and distal interacting regions into multiple sub-clusters for each functional outcome" and that these clusters show meaningful biological enrichment.
- **Evidence pointer** Figure 5c-5h; Supplementary Figure 5a-5g
- **Concern** The machine learning approach is described at a high level, but critical methodological details are missing. The authors do not specify the exact feature set used (beyond "motif binding site repertoire"), the number of features, the handling of correlated motifs, or the cross-validation strategy in sufficient detail. More importantly, the AUC scores for the one-vs-all models range from 0.55 to 0.70, which indicates modest predictive power. The biological interpretation of the clusters relies on enrichment analyses that may be confounded by the small number of genes in each cluster.
- **Why it matters** The REBEL framework is presented as a major methodological contribution. Without sufficient detail and with only modest predictive performance, the robustness and utility of the approach cannot be adequately assessed. The biological conclusions drawn from the clustering may be overinterpreted given the modest AUC values.
- **Resolution test** Provide complete methodological details including feature selection, hyperparameter tuning results, and cross-validation performance. Report precision-recall curves in addition to AUC. Validate the identified TFBS combinations using an independent approach, such as motif perturbation assays or comparison with publicly available ChIP-seq data for the implicated transcription factors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "our results indicate that many but not all expression and long-range interaction profiles are matched between the cell line model and primary patient samples" and that this validates the cell line model.
- **Evidence pointer** Figure 6a-6d; Supplementary Figure 6a-6l
- **Concern** The patient sample analysis is based on only two APL patients. While the authors acknowledge this limitation, the conclusions drawn from this comparison are used to support the generalizability of the cell line findings. The correlation coefficients between patients and cell line (r=0.74, 0.67 for PML::RARA-bound genes) are moderate, and the authors do not adequately address the possibility that the discrepancies reflect genuine biological differences between the model and the disease rather than technical variation.
- **Why it matters** The translational relevance of the findings depends on the fidelity of the cell line model to primary disease. With only two patients, it is impossible to distinguish between patient-specific variation and systematic differences between the model and the disease.
- **Resolution test** Increase the number of patient samples analyzed, or at minimum, provide a more nuanced discussion of the limitations. If additional samples are not available, temper the claims about model fidelity and explicitly state that the two-patient comparison is preliminary.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "74% of PML::RARA-occupied sites were positioned in fragments that engage in interactions in uninduced and/or induced cells" and that this supports a role for chromatin looping in PML::RARA function.
- **Evidence pointer** Supplementary Figure 3g-3i; Figure 3h
- **Concern** The integration of capture Hi-C data with Cut&Run binding sites is presented as evidence for long-range regulatory effects. However, the capture Hi-C data are not deeply described. The authors do not report the resolution of the Hi-C data, the number of significant interactions per replicate, or the reproducibility of the differential interaction calls. The GOTHiC method for differential interaction calling has known limitations with low sequencing depth.
- **Why it matters** The chromatin conformation data are central to the claim that PML::RARA affects long-range regulatory interactions. If the Hi-C data quality is insufficient, the conclusions about gained and lost interactions may not be reliable.
- **Resolution test** Provide detailed quality metrics for the capture Hi-C data, including the number of valid interaction pairs, the reproducibility between replicates, and the fraction of interactions that pass the significance threshold. Consider validating a subset of differential interactions by an orthogonal method such as 3C-qPCR.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure 1a
- **Evidence pointer** Figure 1a
- **Issue** The schematic in Figure 1a is dense and may be difficult for readers unfamiliar with the experimental system to follow. The relationship between the different omics datasets and the integration pipeline is not immediately clear.
- **Required correction** Consider simplifying the schematic or adding a step-by-step workflow diagram that clearly shows how each dataset feeds into the integrative analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, RNA-seq analysis
- **Evidence pointer** Methods section, RNA-seq analysis
- **Issue** The authors state that differential expression was determined using limma but do not specify the exact model used, the inclusion of surrogate variables, or the handling of batch effects. Given that the zinc induction may have broad cellular effects beyond PML::RARA activation, the specificity of the transcriptional response should be more carefully addressed.
- **Required correction** Provide the full limma model formula, including any adjustment for surrogate variables or batch effects. Consider including a control experiment with zinc treatment in cells lacking the PML::RARA transgene to rule out zinc-specific effects.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Cut&Run analysis
- **Evidence pointer** Methods, Cut&Run analysis
- **Issue** The authors used both an anti-RARA antibody and an anti-PML::RARA antibody. The relationship between the binding sites identified by these two antibodies is not fully described. The anti-RARA antibody would also detect wild-type RARA, which may confound the interpretation of PML::RARA-specific binding.
- **Required correction** Clarify how the authors distinguished PML::RARA-specific binding from wild-type RARA binding. If the anti-PML::RARA antibody is truly fusion-specific, this should be validated more explicitly.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of clinical implications is somewhat speculative. The authors mention coagulation-associated genes as potential therapeutic targets but do not provide a clear framework for how these findings might translate to clinical practice.
- **Required correction** Either provide a more concrete discussion of how the identified regulatory mechanisms could be targeted therapeutically, or temper the clinical implications section to match the level of evidence presented.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract introduces the machine learning method (REBEL) without sufficient context for readers unfamiliar with such approaches. The acronym is not defined in the abstract.
- **Required correction** Define REBEL in the abstract and provide a one-sentence explanation of what the method does and why it is needed.

### Technical failings that need to be addressed before the case is established
1. R1-M1: Time course analysis needed to support the claim of context-specific regulatory outcomes
2. R1-M2: Insufficient methodological detail for the machine learning approach and modest predictive performance
3. R1-M3: Limited patient sample size (n=2) undermines generalizability claims
4. R1-M4: Inadequate quality metrics for capture Hi-C data

### Assessment against Nature-style criteria
- **Originality**: The work is original in its integration of multiple omics approaches to study PML::RARA function and in the application of machine learning to dissect regulatory codes. The finding that PML::RARA can activate as well as repress transcription is a novel contribution.
- **Scientific importance**: The question of how fusion oncoproteins exert context-specific effects is important for understanding leukemia biology and potentially for therapeutic development. However, the limited patient validation and lack of functional follow-up reduce the immediate impact.
- **Interdisciplinary readership**: The work bridges leukemia biology, chromatin biology, and computational biology, which could appeal to a broad readership. However, the technical complexity of the machine learning approach may limit accessibility.
- **Technical soundness**: The experimental design is generally sound, but several technical concerns (time course, Hi-C quality, machine learning details) need to be addressed. The statistical rigor of the integrative analyses could be improved.
- **Readability for nonspecialists**: The manuscript is reasonably well-written but the methods and results sections are dense. The figures are informative but some are complex and may be difficult for nonspecialists to interpret.

### Recommendation posture
Supportive if technical concerns are resolved. The core finding that PML::RARA has context-specific regulatory activities is potentially important, and the multi-omics approach is commendable. However, the current evidence does not fully establish the claims as presented. The time course issue (R1-M1) and the machine learning methodology (R1-M2) are the most critical concerns. The limited patient validation (R1-M3) is a significant limitation that should be acknowledged more explicitly. If the authors can address these concerns with additional data or more careful analysis, the manuscript could be suitable for publication.