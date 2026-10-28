## Review setup
- **Input scope** Full manuscript text (summary, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Technical soundness, methodological novelty, evidence quality, and claims as presented in the provided text; no independent replication or access to raw data
- **Shared manuscript claim summary** The authors present D&D-seq, a single-cell method that uses a nanobody-tethered cytosine deaminase (D&D) to record transcription factor (TF) binding events as C-to-T mutations in accessible chromatin. They demonstrate its application in cell lines (K562, CA46) and primary human PBMCs, benchmark against ChIP-seq and uliCUT&RUN, integrate with C.Origami for 3D genome prediction, and combine with GoT-ChA genotyping to study IDH2-mutant clonal hematopoiesis.
- **Visible evidence base** Results sections describe experiments and analyses; figures are referenced (Fig. 1a-k, Fig. 2a-p, Fig. 3a-f, Fig. 4a-n, Supplementary Figs. 1-4) but figure panels are not viewable; methods sections provide protocol details; no quantitative results, statistics, or data tables are included in the provided text
- **Missing materials affecting confidence** Figure panels and legends; quantitative results (effect sizes, p-values, confidence intervals); detailed bioinformatics parameters for D&D signal extraction; validation statistics for C.Origami predictions; raw data access details; details on antibody validation; negative control results for D&D specificity

## Reviewer

### Overall assessment
The manuscript describes a conceptually interesting approach to a recognized problem: direct, single-cell profiling of non-histone DNA-binding proteins. The use of a split deaminase tethered to antibodies via nanobodies is a creative adaptation of existing base-editing tools, and the integration with established single-cell ATAC workflows is pragmatic. However, the evidence presented in the text is largely qualitative and descriptive. Key claims regarding sensitivity, specificity, and biological discovery are not supported by quantitative data in the provided material. The benchmarking against uliCUT&RUN is presented as favorable but lacks statistical rigor. The IDH2 application is intriguing but the analysis is underpowered and the conclusions are speculative. The manuscript has potential but the case is not established from the provided evidence.

### Who would be interested in the results, and why
Researchers in single-cell genomics, chromatin biology, and epigenomics would be interested. The method addresses a gap in the single-cell toolkit, and the potential to combine TF binding with chromatin accessibility and genotype in the same cell is attractive. Those studying clonal hematopoiesis, cancer epigenetics, and 3D genome organization may also find the applications relevant. The approach could be of interest to method developers seeking alternatives to CUT&Tag-based single-cell approaches.

### Major strengths
1. The core concept is novel and addresses a real limitation in the field.
2. The split-deaminase design with inducible activation is a thoughtful control for non-specific activity.
3. Integration with existing 10x Genomics workflows lowers the barrier for adoption.
4. The combination with GoT-ChA for genotype-phenotype linkage is a valuable extension.
5. The application to primary human samples is a strength, demonstrating practical utility.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "obtaining high specificity and efficiency, with clear identification of TF footprint and signal retention in the targeted cell subpopulations"
- **Evidence pointer** Results section "D&D-seq allows for single-cell DNA:Protein binding profiling"; Fig. 2f-i, 2n-o; location not provided
- **Concern** The claim of high specificity and efficiency is not supported by quantitative data in the text. No numbers are given for sensitivity (e.g., fraction of known binding sites detected), specificity (e.g., enrichment over background), or reproducibility across replicates. The comparison to ChIP-seq is described as "high concordance" but no correlation coefficients or overlap statistics are provided. The statement that signal is "retained exclusively in the subpopulation stained with the respective specific antibody" is presented without quantitative support.
- **Why it matters** The central claim of the method is that it can accurately record TF binding. Without quantitative metrics, the reader cannot assess whether the method is reliable, how it compares to existing approaches, or whether the signal is biologically meaningful versus noise.
- **Resolution test** Provide quantitative metrics: precision-recall curves or ROC-style analyses for known binding sites, enrichment scores for target vs. background regions, correlation coefficients with ChIP-seq, and replicate concordance. Show these for both cell lines and PBMCs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "the deamination reaction showed minimal off-target activity"
- **Evidence pointer** Results section "Docking & Deamination (D&D-seq) allows for mapping DNA:Protein binding via molecular foot-printing"; Supplementary Fig. 1i-m; location not provided
- **Concern** The claim of minimal off-target activity is not quantified. The text mentions that D&D edits are found in TpC, CpC, and GpC contexts, which suggests sequence-context-dependent activity, but the distribution of edits across the genome (e.g., in non-accessible regions, in repeat elements, at random sites) is not described. The split-enzyme design is presented as a control, but no data are shown demonstrating that the split enzyme alone (without the C-terminal peptide) produces no edits.
- **Why it matters** Off-target deamination would generate false-positive binding sites and compromise the interpretation of all downstream analyses. The method's utility depends on the edits being specifically localized to the target protein's binding sites.
- **Resolution test** Provide genome-wide edit frequency in on-target vs. off-target regions, edit rates in cells treated with the split enzyme without activation, and a comparison of edit rates in accessible vs. inaccessible chromatin. Show that edits are not enriched in known repeat elements or other non-specific regions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "D&D-seq successfully identified cell-specific TF binding patterns for CTCF, GATA1, recapitulating profiles generated using gold-standard protocols, such as ENCODE's ChIP-seq"
- **Evidence pointer** Results section "D&D-seq allows for single-cell DNA:Protein binding profiling"; Fig. 2n-o; location not provided
- **Concern** The benchmarking against ChIP-seq is described qualitatively. No statistical measures of agreement are provided (e.g., Jaccard index, correlation of signal intensity, fraction of ChIP-seq peaks recovered). The comparison to uliCUT&RUN is presented as a single FRiP metric, which is a global measure and does not assess site-level accuracy. The statement that D&D-seq "outperforms" uliCUT&RUN is based on FRiP alone, which may not reflect biological accuracy.
- **Why it matters** The method's validity rests on its ability to reproduce known binding patterns. Without rigorous benchmarking, the reader cannot determine whether D&D-seq provides accurate, quantitative measurements of TF binding or merely a noisy approximation.
- **Resolution test** Provide site-level comparisons: fraction of ChIP-seq peaks with a D&D edit, correlation of D&D edit counts with ChIP-seq signal strength, and a direct comparison of D&D-seq and uliCUT&RUN on the same cell type using multiple metrics (e.g., precision, recall, F1 score).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "we observed a significant alteration of 3D genome contacts in mutant-enriched T cells compared to wild-type-enriched T cells at the GIT1 locus"
- **Evidence pointer** Results section "Linking genotype to DNA:Protein interaction profiles and chromatin landscapes in single cells"; Fig. 4j; location not provided
- **Concern** The claim of significant alteration of 3D genome contacts is based on predictions from the C.Origami algorithm, not on experimental Hi-C data. The text states that the predicted structures "closely recapitulate" experimental Hi-C data, but no quantitative comparison is shown. The differential analysis between mutant and wild-type cells is based on a small number of cells (329 mutant vs 534 wild-type in one replicate) and the statistical method is not described in detail. The FDR threshold of 0.25 is permissive and may yield many false positives.
- **Why it matters** The biological conclusion regarding IDH2 mutations and CTCF-mediated genome organization is a key translational claim. If the 3D structure predictions are not validated or the statistical analysis is underpowered, the conclusion is not supported.
- **Resolution test** Validate C.Origami predictions against experimental Hi-C data in the same cell types. Provide a more stringent statistical analysis with appropriate multiple-testing correction. Consider validating the GIT1 locus findings with an orthogonal method (e.g., 3C, 4C, or DNA FISH).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "D&D-seq represents an important technological advance enabling the direct mapping of TF or chromatin remodeler binding to the DNA in primary human samples"
- **Evidence pointer** Methods sections; location not provided
- **Concern** The methods as described lack sufficient detail for replication. Key parameters for the D&D signal extraction pipeline are not fully specified (e.g., thresholds for variant calling, filtering criteria, how germline variants are distinguished from D&D edits). The antibody concentrations, incubation times, and validation of antibody specificity in the D&D context are not described. The efficiency of the deamination reaction (edits per cell per binding site) is not reported.
- **Why it matters** Reproducibility is a core requirement for a method paper. Without detailed protocols, other laboratories cannot adopt the method or verify the results.
- **Resolution test** Provide a complete step-by-step protocol, including all buffer compositions, incubation times, temperatures, and bioinformatics parameters. Report the distribution of edits per cell and the relationship between antibody concentration and edit frequency.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1a
- **Evidence pointer** Results section "Docking & Deamination (D&D-seq) allows for mapping DNA:Protein binding via molecular foot-printing"; location not provided
- **Issue** The schematic in Fig. 1a is described as showing the integration of D&D-seq with ATAC-seq, but the text does not clarify whether the deamination occurs before or after tagmentation, and how the two signals are separated computationally.
- **Required correction** Clarify the order of operations in the figure and text, and describe how D&D edits are distinguished from ATAC-seq insertion sites.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Differential CTCF binding analysis
- **Evidence pointer** Results section "Linking genotype to DNA:Protein interaction profiles and chromatin landscapes in single cells"; Fig. 4i; location not provided
- **Issue** The text states that a linear mixed model was used but does not specify the covariates, the random effects structure, or how the FDR was calculated. The permissive threshold of 0.25 is unusual and should be justified.
- **Required correction** Provide full model specification, justify the FDR threshold, and report the number of significant sites at more stringent thresholds (e.g., 0.05, 0.01).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Data Availability section; location not provided
- **Issue** The data availability statement indicates that raw data will be deposited, but no accession numbers are provided. The code repository is mentioned but not linked in the text.
- **Required correction** Provide accession numbers for all datasets and a working URL for the code repository.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** GIT1 and CNIH2 loci
- **Evidence pointer** Results section "Linking genotype to DNA:Protein interaction profiles and chromatin landscapes in single cells"; Fig. 4k-n; location not provided
- **Issue** The text suggests that loss of CTCF binding at GIT1 and CNIH2 leads to "disorganized" chromatin interactions, but the functional consequences are speculative. The connection to immune dysregulation in CHIP is not directly tested.
- **Required correction** Clearly distinguish between observed changes in co-accessibility and inferred functional consequences. Consider discussing alternative explanations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion section
- **Evidence pointer** Discussion; location not provided
- **Issue** The discussion is largely forward-looking and speculative. It does not critically evaluate the limitations of the method, such as the low number of edits per cell, the potential for antibody cross-reactivity, or the bias toward open chromatin regions.
- **Required correction** Add a dedicated limitations paragraph that addresses these issues and discusses potential solutions.

### Technical failings that need to be addressed before the case is established
- R1-M1: Lack of quantitative metrics for sensitivity and specificity
- R1-M2: No quantification of off-target activity
- R1-M3: Inadequate benchmarking against ChIP-seq and uliCUT&RUN
- R1-M4: Unsupported claim of significant 3D genome alterations based on predictions
- R1-M5: Insufficient methodological detail for replication

### Assessment against Nature-style criteria
- **Originality** High. The concept of using a tethered deaminase to record TF binding in single cells is novel and distinct from existing approaches such as CUT&Tag or DamID.
- **Scientific importance** Moderate to high. If validated, the method could fill a gap in the single-cell toolkit and enable new questions about TF dynamics in heterogeneous tissues. The application to CHIP is clinically relevant.
- **Interdisciplinary readership** Moderate. The method will appeal to single-cell method developers, epigenomics researchers, and those studying gene regulation. The clinical application may attract a broader audience.
- **Technical soundness** Currently insufficient. The evidence presented is largely qualitative, and key claims are not supported by quantitative data. The benchmarking is incomplete, and the statistical analysis is underpowered.
- **Readability for nonspecialists** The text is generally clear but assumes familiarity with single-cell ATAC-seq, base editing, and chromatin conformation analysis. The methods section is dense and would benefit from a schematic overview of the computational pipeline.

### Recommendation posture
Currently not established from the provided evidence. The concept is promising and the authors have demonstrated feasibility, but the quantitative evidence required to support the claims of specificity, efficiency, and biological discovery is missing. The manuscript would benefit from a revised version that includes rigorous benchmarking, quantitative metrics, and a more detailed methods section. I would be supportive if these technical concerns are resolved.

## Risk / unsupported claims
- "High specificity and efficiency" of D&D-seq in single cells (no quantitative support)
- "Minimal off-target activity" (no genome-wide quantification)
- "High concordance to bulk ChIP-seq reference data" (no correlation or overlap statistics)
- "Significant alteration of 3D genome contacts" in IDH2-mutant cells (based on predictions, not experimental data; underpowered analysis)
- "D&D-seq outperforms uliCUT&RUN" (based on a single FRiP metric, not a comprehensive comparison)
- "Unprecedented accuracy" and "transformative" potential (subjective, not supported by data)
- The claim that D&D-seq can profile "even weak or transient factor binding" is not directly demonstrated; the experiments target CTCF and GATA1, which are relatively strong binders.