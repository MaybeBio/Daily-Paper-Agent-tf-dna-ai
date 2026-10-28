## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript text. No external data, supplementary files, or peer review history were assessed.
- **Shared manuscript claim summary** The authors report that a patient-specific heterozygous HNF1A H126D mutation, modeled in hiPSC-derived beta-like cells, leads to reduced GLUT2 expression, decreased glucose uptake, and lower ATP:ADP ratio, which they propose contributes to the insulin secretion defects observed in MODY3 patients.
- **Visible evidence base** Main text figures (Figs. 1-8) and their legends, methods section, and in-text references to supplementary figures and tables.
- **Missing materials affecting confidence** Supplementary figures (S1-S11), supplementary tables, supplementary data files, and source data files were not provided. These are critical for evaluating the robustness of the ChIP-seq, RNA-seq, and other quantitative analyses.

## Reviewer
- **Overall assessment** This manuscript addresses an important question in MODY3 pathophysiology using a valuable patient-specific hiPSC model. The combination of computational, genomic, and functional assays is commendable. However, the central claim that decreased GLUT2 and glucose uptake are primary contributors to the insulin secretion defect is not fully established from the provided evidence. Key concerns include the lack of direct functional rescue experiments, the reliance on a single patient mutation without isogenic controls, and the incomplete presentation of genomic data analysis. The manuscript is technically sound in its execution but requires substantial additional evidence to support its mechanistic conclusions.
- **Who would be interested in the results, and why** Researchers in the fields of monogenic diabetes, beta-cell biology, and stem cell disease modeling would be interested. The work provides a human-relevant model for MODY3 and implicates GLUT2, a controversial player in human beta-cell glucose sensing, as a potential therapeutic target. The findings could also inform studies on the broader role of HNF1A in pancreatic development and function.
- **Major strengths**
    1.  Use of patient-derived hiPSCs from two individuals with a unique, clinically relevant HNF1A mutation, providing a human-specific disease model.
    2.  The multi-pronged approach integrating molecular dynamics simulations, transcriptomics (RNA-seq, ChIP-seq), and functional assays (glucose uptake, ATP/ADP, insulin secretion) to dissect the pathway.
    3.  The systematic evaluation of the stimulus-secretion coupling pathway, ruling out defects in KATP channel and calcium signaling, which helps narrow down the site of dysfunction.
    4.  The identification of GLUT2 as a direct HNF1A target in human cells, which contrasts with some previous literature and has significant implications for understanding human beta-cell physiology.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental Design / Genetic Evidence
    - **Claim pointer** The manuscript claims that the HNF1A H126D mutation causes the observed defects in GLUT2 expression, glucose uptake, and insulin secretion.
    - **Evidence pointer** Results sections "MODY3-hiPSCs as a human model to study pancreatic β cells" and "Decreased GLUT2, glucose uptake and ATP production"; Figures 2, 6, 7.
    - **Concern** The study uses patient-derived hiPSC lines but does not include isogenic control lines where the H126D mutation is corrected. Without this, it is impossible to definitively attribute the observed phenotypic differences to the HNF1A mutation itself, as opposed to other genetic or epigenetic variations between the patient and control lines. The comparison is between two independent control lines (H9, iAGb) and six patient lines, which does not control for genetic background.
    - **Why it matters** This is a fundamental requirement for genetic disease modeling. The lack of isogenic controls leaves open the possibility that the observed differences are due to off-target effects or background genetic variation, not the specific HNF1A mutation. This weakens the causal link that is central to the paper's thesis.
    - **Resolution test** The authors should generate isogenic control lines by correcting the H126D mutation in the patient hiPSCs (e.g., using CRISPR/Cas9) and demonstrate that the corrected lines rescue the wild-type phenotype in terms of GLUT2 expression, glucose uptake, ATP production, and insulin secretion. Alternatively, they could introduce the H126D mutation into a wild-type hiPSC line and show it recapitulates the disease phenotype.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Functional Validation / Mechanistic Proof
    - **Claim pointer** The manuscript claims that decreased GLUT2 and glucose uptake "contribute to" the insulin secretion defects, implying a causal relationship.
    - **Evidence evidence** Results section "Decreased GLUT2, glucose uptake and ATP production"; Figure 7.
    - **Concern** The manuscript demonstrates a correlation between reduced GLUT2 expression, reduced glucose uptake, and reduced insulin secretion. However, it does not provide direct functional evidence that restoring GLUT2 expression or function can rescue insulin secretion. The use of the GLUT2 inhibitor fisetin shows that inhibiting GLUT2 in wild-type cells reduces glucose uptake, but it does not show that this is sufficient to impair insulin secretion, nor does it show that the defect in mutant cells is specifically due to GLUT2 loss.
    - **Why it matters** To establish a causal role, the authors must show that the pathway is not just associated with, but is required for, the observed phenotype. A rescue experiment is the gold standard. Without it, the conclusion that GLUT2 deficiency is a primary driver of the insulin secretion defect remains speculative.
    - **Resolution test** The authors should overexpress GLUT2 in the mutant beta-like cells and test whether this restores glucose uptake, ATP production, and glucose-stimulated insulin secretion. Conversely, they could knock down GLUT2 in wild-type cells to see if it phenocopies the mutant defect. The fisetin experiment should also be extended to measure insulin secretion.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Data Presentation / Statistical Rigor
    - **Claim pointer** The manuscript claims that RNA-seq and ChIP-seq analyses reveal numerous HNF1A target genes affected by the mutation, and that GLUT2 is a direct target.
    - **Evidence pointer** Results sections "Downregulation of genes in β cell function" and "Putative HNF1A targets affected by HNF1A+/H126D mutation"; Figures 3, 4.
    - **Concern** The details of the RNA-seq and ChIP-seq analyses are not presented in the main text. The number of replicates, the method for determining differential expression (e.g., specific R package, thresholds), and the statistical significance of the ChIP-seq peak differences (e.g., Fig. 4b, S11b) are not fully described. The statement that a ChIP-seq peak reduction is "not statistically significant" (Fig. S11b) is concerning, as it undermines the claim of direct binding loss at the GLUT2 promoter.
    - **Why it matters** The genomic analyses are a cornerstone of the paper, providing the link between the mutation and downstream gene expression changes. Without clear and rigorous statistical presentation, the reliability of these findings cannot be assessed. The lack of significance in the ChIP-seq data at the GLUT2 promoter is a critical weakness.
    - **Resolution test** The authors should provide a detailed description of the bioinformatics pipeline, including quality control metrics, alignment statistics, and the exact statistical tests used. They should also clarify the significance of the ChIP-seq binding difference at the GLUT2 promoter and, if necessary, provide additional evidence (e.g., independent ChIP-qPCR with more biological replicates) to support the claim of reduced binding.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Model Relevance / Physiological Context
    - **Claim pointer** The manuscript claims that the findings in hiPSC-derived beta-like cells can account for the clinical insulin secretion defect in MODY3 patients.
    - **Evidence pointer** Results sections "No defects in calcium signaling nor potassium channels" and "Decreased GLUT2, glucose uptake and ATP production"; Figure 6.
    - **Concern** The hiPSC-derived beta-like cells are immature and may not fully recapitulate the physiology of adult human beta cells. The manuscript shows that these cells are not functional in vitro and require in vivo maturation for 23 weeks to respond to glucose. The relevance of the findings, particularly regarding GLUT2, to mature human beta cells is not directly demonstrated. The authors do not show GLUT2 expression in adult human beta cells or in the context of the intact pancreas.
    - **Why it matters** The physiological relevance of the model is key to the translational impact of the study. If the findings are an artifact of the in vitro differentiation system, they may not be applicable to the human disease. The controversy over GLUT2's role in human beta cells makes this point particularly important.
    - **Resolution test** The authors should validate their key findings in a more physiologically relevant system. This could include showing GLUT2 expression in adult human islets, using a more mature stem cell-derived beta cell protocol, or performing experiments in a human beta cell line or primary islets where HNF1A is knocked down.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity / Presentation
    - **Affected element** Figure 1e
    - **Evidence pointer** Results section "HNF1A H126D mutation altered amino acid interactions"; Figure 1e.
    - **Issue** The computed binding free energies (∆H) in Figure 1e show no significant difference between WT and mutant, which seems to contradict the later claim of reduced binding. The text explains this by stating the simulations were initiated from the bound state, but this is a point of confusion.
    - **Required correction** The authors should more clearly explain the discrepancy between the binding free energy calculation and the functional outcome, perhaps by moving the discussion of the unbound simulations to the main text and more explicitly stating that the bound-state simulations are not predictive of binding affinity differences.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data Presentation
    - **Affected element** Figure 7c
    - **Evidence pointer** Results section "Decreased GLUT2, glucose uptake and ATP production"; Figure 7c.
    - **Issue** The figure legend for Figure 7c mentions a p-value for GLUT1 but the text says "GLUT1 = 0.0125 (P1), 0.0373 (P2); GLUT1 = 0.0068 (P1), 0.0021 (P2)". This appears to be a typo, with the second set of p-values likely intended for GLUT2.
    - **Required correction** The authors should correct the typo in the figure legend to accurately report the p-values for GLUT1 and GLUT2.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Statistical Reporting
    - **Affected element** Statistical analysis methods
    - **Evidence pointer** Methods section "Statistical analysis".
    - **Issue** The statistical methods section is very brief. It mentions unpaired one-tailed Student's t-test and one-way ANOVA, but does not specify how normality was tested, whether corrections for multiple comparisons were applied (other than Tukey's post-hoc), or how the data in figures with multiple comparisons were analyzed.
    - **Required correction** The authors should provide a more detailed description of their statistical analysis, including the software used, the tests for normality, and the specific multiple comparison correction methods applied for each figure.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity / Presentation
    - **Affected element** Discussion section
    - **Evidence pointer** Discussion section, paragraph 4.
    - **Issue** The statement "A similar lack of GLUT2 expression observed in the HNF1A P291fsinsC mutant suggests that impaired glucose uptake capacity may be common amongst diabetes patients whose β cells harbor various HNF1A gene mutations" is an overgeneralization based on data from a single overexpression experiment in a non-beta cell line (AD-293).
    - **Required correction** The authors should temper this statement and acknowledge that this is a preliminary finding in a heterologous system that requires validation in a more relevant model.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of isogenic controls.
    - R1-M2: Lack of functional rescue experiments.
    - R1-M3: Incomplete presentation of genomic data analysis and statistics.

## Risk / unsupported claims
- The claim that the HNF1A H126D mutation is the direct cause of the observed phenotypes is not fully supported without isogenic controls.
- The claim that decreased GLUT2 and glucose uptake "contribute to" the insulin secretion defect is correlative, not causal, based on the provided evidence.
- The claim that the findings can be generalized to other HNF1A mutations (e.g., P291fsinsC) is based on limited heterologous overexpression data and is not fully supported.
- The physiological relevance of the findings to adult human beta cells is not established, given the immature nature of the hiPSC-derived beta-like cells.
- The significance of the ChIP-seq binding difference at the GLUT2 promoter is unclear, as the text notes it is not statistically significant.

## Assessment against Nature-style criteria
- **Originality** The work is original in its use of patient-specific hiPSCs with a unique HNF1A mutation to dissect the molecular mechanisms of MODY3. The focus on GLUT2 as a key downstream target in human cells provides a new perspective, as previous work has often emphasized other pathways. The combination of computational and experimental approaches is also a strength.
- **Scientific importance** The findings have the potential to be important for understanding the pathophysiology of MODY3 and for developing targeted therapies. If the causal role of GLUT2 is firmly established, it could be a novel therapeutic target. The work also contributes to the ongoing debate about the role of GLUT2 in human beta-cell glucose sensing.
- **Interdisciplinary readership** The topic is of interest to a specialized audience in diabetes research, stem cell biology, and genomics. The use of hiPSC technology and multi-omics approaches may also appeal to a broader readership interested in disease modeling. However, the current presentation is quite specialized and may not be immediately accessible to a general scientific audience.
- **Technical soundness** The individual experimental techniques appear to be executed properly, and the use of multiple orthogonal methods is commendable. However, the overall technical soundness of the central claim is compromised by the lack of isogenic controls and functional rescue experiments. The statistical rigor of the genomic analyses is also not fully demonstrated.
- **Readability for nonspecialists** The manuscript is clearly written but is dense with technical details and assumes a high level of background knowledge in beta-cell biology and genomics. The main narrative could be made more accessible with a clearer summary of the proposed mechanism and its implications. The figures are complex and may be difficult for nonspecialists to interpret.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a significant question with a valuable model system, and the initial observations are interesting. However, the central mechanistic claim is not sufficiently supported due to the lack of isogenic controls and functional rescue experiments. The authors should be encouraged to address these major concerns, as the work has the potential to be a significant contribution to the field.