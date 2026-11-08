## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific content, technical validity, logical coherence, and support of claims by presented evidence; not editorial or formatting issues
- **Shared manuscript claim summary** The authors reconstruct single-cell resolution developmental trajectories of the Arabidopsis root ground tissue using scRNA-seq and scATAC-seq, identify a transcriptional switch in the late meristematic zone, and propose that SF1 GATA transcription factors (GATA2 and GATA4) act as central coordinators of the proliferation-to-differentiation transition by integrating auxin and cytokinin signaling within a bistable gene regulatory network.
- **Visible evidence base** scRNA-seq reanalysis of ~11,000 cells; newly generated scATAC-seq atlas of 14,466 nuclei; reporter lines for GATA2 and GATA4; gata2 gata4 mutant analysis; inducible GATA4 overexpression; transient luciferase assays; RT-qPCR; CellOracle network inference; GO enrichment; motif enrichment analyses
- **Missing materials affecting confidence** Supplementary figures and data files referenced but not provided; source data not available; details of statistical tests for some comparisons not fully specified; raw sequencing quality metrics not shown

## Reviewer
- **Overall assessment** This manuscript presents a substantial and largely well-executed integration of single-cell transcriptomic and chromatin accessibility data to address a fundamental question in plant developmental biology: how proliferation and differentiation are coordinated in the root. The identification of a late meristematic zone transcriptional switch and the positioning of SF1 GATA TFs within an auxin-cytokinin regulatory network is conceptually interesting and experimentally supported by multiple complementary approaches. However, several technical concerns and gaps in evidence weaken the strength of the central claims, particularly regarding the directness of GATA regulation of target genes, the generality of the proposed bistable switch model, and the quantitative rigor of some phenotypic analyses. The manuscript would benefit from additional experiments or analyses to solidify the mechanistic model.

- **Who would be interested in the results, and why** Plant developmental biologists studying root patterning, meristem function, and cell differentiation; researchers interested in gene regulatory networks and single-cell genomics approaches; those studying hormonal crosstalk in development. The work provides a valuable resource (scATAC-seq atlas, data browser) and a testable model for how transcription factors coordinate developmental transitions.

- **Major strengths**
  1. Integration of two complementary single-cell modalities (RNA and chromatin) to reconstruct developmental trajectories is methodologically rigorous and timely.
  2. The identification of a discrete transcriptional switch in the late MZ, rather than a gradual transition, is a clear and interesting finding.
  3. The combination of computational prediction (CellOracle) with experimental validation (mutants, overexpression, reporters) is commendable.
  4. The proposed model connecting GATA TFs to auxin-cytokinin antagonism is conceptually appealing and generates testable predictions.
  5. The generation of a user-friendly data browser is a valuable community resource.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of GRN inference
- **Claim pointer** "Machine learning-based network inference of integrated GT trajectories identifies GATA TFs as core regulators of this transition" and "GATA TFs sit at the tipping point of a feedback-driven bistable system"
- **Evidence pointer** Results section "GATA TFs characterize the regulatory hub in the late meristem zone"; Methods "GRN inference and in silico TF perturbation analyses"
- **Concern** The CellOracle analysis is described briefly, and key parameters and validations are not fully detailed. The manuscript states that "only the top 3,000 links per cluster were retained" but does not justify this threshold or show how sensitive the results are to this choice. More critically, the perturbation scores are presented as predictions, but the experimental validation (gata2 gata4 phenotype) is consistent with a role in differentiation timing without directly confirming that the predicted downstream targets mediate this effect. The claim that GATA TFs are "core regulators" of the switch requires stronger evidence that they are necessary and/or sufficient for the transcriptional changes observed at the late MZ transition.
- **Why it matters** The central mechanistic claim of the paper rests on the GRN inference. If the network inference is not robust or if the predicted regulatory relationships are not validated, the model of GATA TFs as "central coordinators" is not established. The distinction between correlation (GATA expression correlates with the switch) and causation (GATA drives the switch) is critical.
- **Resolution test** Provide a more detailed description of CellOracle parameters, sensitivity analyses, and validation of predicted regulatory edges (e.g., ChIP-seq or DAP-seq confirmation for a subset of targets). Demonstrate that GATA2/GATA4 perturbation (loss- or gain-of-function) leads to changes in the expression of predicted downstream targets in the expected direction. Ideally, show that the bistable switch behavior is recapitulated in a mathematical model parameterized with experimental data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for bistable switch model
- **Claim pointer** "GATA TFs sit at the tipping point of a feedback-driven bistable system that integrates inputs from auxin and cytokinin to balance proliferation and differentiation"
- **Evidence pointer** Results section "GATA TFs promote developmental progressions in a network integrating auxin and cytokinin signaling"; Figure 5
- **Concern** The evidence for a bistable switch is indirect. The authors show that GATA2/GATA4 are repressed by PLT and induced by ARR1/ARR12, and that GATA TFs activate ARR genes and repress PLT genes. This is consistent with a bistable system, but no direct evidence of bistability (e.g., hysteresis, two stable steady states) is presented. The RT-qPCR data in Figure 5A show transient repression of PLT genes upon GATA4 induction, which is not obviously consistent with a simple bistable switch. The model in Figure 5E is presented as a summary, but the mathematical or conceptual basis for claiming bistability is not articulated.
- **Why it matters** Bistability is a strong claim with specific dynamical implications (e.g., irreversibility, hysteresis). If the system is not truly bistable, the model is misleading. The distinction between a negative feedback loop (which can produce oscillations or homeostasis) and a bistable switch (which requires specific network motifs such as mutual inhibition with positive feedback) is important.
- **Resolution test** Provide a formal analysis of the network motif (e.g., using a simple ODE model) to show that the proposed interactions can produce bistability. Alternatively, present experimental evidence for hysteresis (e.g., different thresholds for entering vs. exiting the differentiated state). At minimum, soften the language to "feedback-driven switch" rather than "bistable system" unless direct evidence is provided.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of phenotypic analyses
- **Claim pointer** "CRISPR-mediated knockout of GATA2 in a gata4 mutant background results in a significant increase in primary root length, root meristem length, and MZ cell number"
- **Evidence pointer** Results section "GATA TFs coordinate the transition from cell proliferation to differentiation"; Figure 4D-F
- **Concern** The phenotypic analyses appear to rely on box plots with asterisks indicating significance, but the number of biological replicates, the statistical test used, and the effect sizes are not stated in the main text. The methods section mentions "multiple (n≥3) independent events per construct/background" for confocal imaging, but it is unclear if this applies to the phenotypic measurements. For a phenotype as subtle as meristem size changes, careful quantification with adequate replication is essential.
- **Why it matters** The strength of the conclusion that GATA TFs regulate the proliferation-to-differentiation transition depends on the robustness of the mutant phenotype. If the effect is small or variable, the biological significance is less clear.
- **Resolution test** Provide exact n numbers, statistical tests, and effect sizes for all phenotypic measurements. Show that the phenotype is consistent across multiple independent mutant lines. Consider complementation experiments to confirm that the phenotype is due to the GATA mutations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Directness of GATA target regulation
- **Claim pointer** "Expression of the GATA genes is repressed by the auxin-responsive PLT TFs and induced by the CK-response regulators, ARR1 and ARR12" and "The SF1 GATA TFs, in turn, promote expression of ARR1 and ARR12, and repress PLT expression"
- **Evidence pointer** Results section "GATA TFs promote developmental progressions in a network integrating auxin and cytokinin signaling"; Figure 5A-D
- **Concern** The evidence for direct regulation is limited. The authors show that GATA4 induction leads to changes in PLT and ARR transcript levels, and that ARR1 can activate GATA promoters in luciferase assays. However, the PLT repression of GATA genes is inferred from ChIP-seq data (predicted targets) and RT-qPCR, but no direct binding or reporter assay is shown for PLT on GATA promoters. Similarly, the repression of PLT by GATA TFs is inferred from transcript changes, but direct binding is not demonstrated. The claim of a "network" with specific regulatory edges requires more direct evidence for each edge.
- **Why it matters** The proposed network model (Figure 5E) is a key conceptual contribution. If some edges are indirect or incorrectly assigned, the model may be wrong. The distinction between direct and indirect regulation is important for understanding the mechanism.
- **Resolution test** Perform ChIP-qPCR or ChIP-seq for GATA2/GATA4 and PLT on the promoters of proposed targets. Use reporter assays to test the effect of GATA and PLT on each other's promoters. Alternatively, use a more comprehensive approach such as DAP-seq for GATA2/GATA4 to identify direct binding sites.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** "GATA transcription factors coordinate developmental progression in the arabidopsis root" and "ensuring developmental precision and robustness in timing the cell proliferation-to-differentiation switch at the cell, tissue, and organ scales"
- **Evidence pointer** Throughout
- **Concern** The study focuses on the ground tissue (cortex and endodermis) of the root. The claim of coordination "at the cell, tissue, and organ scales" is supported by the observation that GATA2/GATA4 are expressed in multiple tissues and that the gata2 gata4 mutant affects root meristem size. However, the detailed mechanistic analysis is limited to the ground tissue. It is unclear whether the same regulatory logic applies to other tissues (e.g., epidermis, vasculature). The title and abstract imply a more general role for GATA TFs in root development than is directly demonstrated.
- **Why it matters** The broader significance of the work depends on whether the identified mechanism is general or specific to the ground tissue. Overstating the generality could mislead readers.
- **Resolution test** Examine GATA2/GATA4 expression and function in other root tissues. Test whether the gata2 gata4 mutant affects developmental transitions in the epidermis or vasculature. Alternatively, temper the claims in the title and abstract to be specific to the ground tissue.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C legend
- **Issue** The heatmap in Figure 1C is described as showing "five defined phases of expression which respect the trajectory's cell cluster arrangement," but the boundaries between phases are not clearly marked in the figure. The relationship between the heatmap and the anatomical regions (E-Q) is not immediately obvious.
- **Required correction** Add clear phase boundaries to the heatmap and label them consistently with the text. Consider adding a schematic of the root with the anatomical regions aligned to the heatmap.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 4E-F
- **Evidence pointer** Figure 4E-F legends
- **Issue** The figure legends state "*p<0.05, **p<0.01 two-sided Student's t-test" but do not specify the number of replicates or whether the tests were paired or unpaired. The methods section does not clearly describe the statistical analysis for these measurements.
- **Required correction** Provide exact n values, specify the type of t-test, and state whether data met assumptions of normality. Consider showing individual data points alongside box plots.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Methods section "Single cell ATAC-seq analysis"
- **Evidence pointer** Methods
- **Issue** The methods for scATAC-seq data processing are described, but key quality control metrics (e.g., number of fragments per cell, fraction of fragments in peaks, transcription start site enrichment) are not reported. The number of cells passing QC is not stated.
- **Required correction** Add a supplementary table with QC metrics and the number of cells/nuclei retained at each step.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of reporter expression
- **Affected element** Figure 3D-E
- **Evidence pointer** Figure 3D-E legends
- **Issue** The authors state that GATA2 and GATA4 protein fusions "dissipate rapidly from the late MZ into the elongating cells of the post MZ," but the images shown are qualitative. It is unclear if the apparent dissipation is due to protein degradation, dilution, or reporter instability.
- **Required correction** Quantify fluorescence intensity along the root axis for multiple roots. Consider using a more stable reporter (e.g., transcriptional reporter) to distinguish transcriptional from post-transcriptional regulation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the study, such as the reliance on computational predictions for some regulatory edges, the potential for off-target effects in the CRISPR mutants, or the possibility that the observed phenotypes are due to indirect effects.
- **Required correction** Add a paragraph acknowledging limitations and suggesting future experiments to address them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not explicitly stated in the provided text
- **Issue** The manuscript mentions a data browser and processed datasets, but a formal data availability statement is not included in the provided text. It is unclear where raw sequencing data will be deposited.
- **Required correction** Add a data availability statement specifying where raw and processed data will be deposited (e.g., GEO, SRA) and provide accession numbers.

## Risk / unsupported claims
1. The claim that GATA TFs are "central coordinators" of the proliferation-to-differentiation switch is not fully supported; the evidence shows correlation and some functional effects, but direct regulatory causality is not established for most predicted targets.
2. The claim of a "bistable system" is not supported by direct dynamical evidence; the network topology is consistent with bistability but does not demonstrate it.
3. The claim that the mechanism operates "at the cell, tissue, and organ scales" is only directly demonstrated for the ground tissue; generalizability to other tissues is inferred but not tested.
4. The statement that "chromatin accessibility marks the activation of key developmental regulators" is supported by correlation but the causal relationship (accessibility leading to expression) is not experimentally tested.
5. The claim that "nearly half of regulation stemming from these DARs manifests in expression in cells further up the root" is based on extrapolation from other datasets and is not directly demonstrated in this study.
6. The assertion that "the recovery of these known regulators at their expected trajectory positions supports the biological fidelity of the inferred network" is reasonable but does not validate the novel predictions of the network.