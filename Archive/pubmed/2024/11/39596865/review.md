## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the manuscript
- **Shared manuscript claim summary** The authors report the synthesis of a novel quinoline compound (Q3) and demonstrate its inhibitory effect on canonical NF-κB transcriptional activity in a HeLa/NF-κB-Luc reporter cell line and intestinal epithelial cell lines. The compound does not affect IκBα degradation or cell viability but appears to interfere with p65 nuclear translocation and DNA binding, as supported by in silico docking and molecular dynamics analyses.
- **Visible evidence base** Figures 1–8, Table 1, Supplementary Files S1–S3, experimental methods sections 2.1–2.9
- **Missing materials affecting confidence** Raw data files, uncropped western blot images, full NMR spectra, complete ImageJ analysis parameters, MD simulation trajectory details, statistical analysis outputs, and compound purity/characterization data beyond NMR/LCMS

## Reviewer

- **Overall assessment** The manuscript presents a straightforward pharmacological characterization of a novel quinoline derivative with moderate NF-κB inhibitory activity. The experimental design is logical and the work combines in vitro reporter assays, viability testing, gene expression analysis, and computational modeling. However, several technical concerns limit the strength of the conclusions, particularly regarding the mechanism of action, the quantitative rigor of the image analysis, and the interpretation of the in silico data. The study is of interest to a specialized audience working on NF-κB inhibitors, but the claims of a specific mechanism require additional experimental support.

- **Who would be interested in the results, and why** Researchers in the fields of inflammation biology, NF-κB signaling, and drug discovery would find this work relevant. The identification of a new small-molecule scaffold that inhibits NF-κB transcriptional activity without affecting upstream IκB degradation could inform future medicinal chemistry efforts. Those working on inflammatory bowel disease or other chronic inflammatory conditions may also take interest given the stated therapeutic motivation.

- **Major strengths** The study addresses a relevant gap in the field, namely the lack of small molecules that directly interfere with NF-κB DNA binding. The use of a stable transgenic reporter cell line is appropriate and the validation with known inhibitors strengthens confidence in the assay system. The inclusion of multiple intestinal cell lines extends the relevance of the findings beyond a single cell type. The computational analyses are a useful complement to the cellular data, and the synthesis and characterization of the compound are clearly described.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanism of action
- **Claim pointer** The manuscript claims that Q3 inhibits NF-κB transcriptional activity by interfering with p65 DNA binding, based on in silico docking and MD simulations.
- **Evidence pointer** Section 3.4, Figure 8, Table 1
- **Concern** The conclusion that Q3 directly interferes with NF-κB DNA binding is inferred solely from computational docking and MD simulations. No experimental validation, such as electrophoretic mobility shift assays (EMSA), DNA pulldown, or chromatin immunoprecipitation, is provided to demonstrate that Q3 actually prevents p65 binding to DNA in cells or in vitro. The docking results show binding energies that are modest, and the difference between Q1 and Q3 in the NF-κB-DNA complex is not clearly quantified in the text. The MD simulation shows stable binding of Q3, but this does not establish functional interference with DNA binding.
- **Why it matters** The central mechanistic claim of the paper rests on this point. Without direct biochemical evidence, the mechanism remains speculative, and the distinction between Q3 acting at the level of DNA binding versus other nuclear events (e.g., transcriptional coactivator recruitment, chromatin remodeling) cannot be made.
- **Resolution test** Provide experimental evidence that Q3 reduces p65 binding to its cognate DNA response element, using EMSA with nuclear extracts from TNF-stimulated cells treated with Q3, or a DNA pulldown assay. Alternatively, a reporter assay with a minimal NF-κB promoter (devoid of other transcription factor binding sites) would strengthen the claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative image analysis
- **Claim pointer** The manuscript claims that Q3 interferes with TNF-induced p65 nuclear translocation based on quantitative immunocytochemistry image analysis.
- **Evidence pointer** Section 3.3, Figure 6, Supplementary File S1
- **Concern** The two image analysis methods described yield different results: the nuclear-positive cell counting method shows little impact of Q3 on p65 nuclear localization, while the IHC profiler digital analysis shows significant interference. The authors do not reconcile these discrepancies or explain which method is more reliable. The IHC profiler plugin is designed for immunohistochemistry scoring, not necessarily for subcellular localization quantification, and its application to nuclear versus cytoplasmic signal partitioning requires validation. The analysis was performed by two researchers, but inter-observer variability and the criteria for defining nuclear positivity are not reported.
- **Why it matters** The claim that Q3 affects p65 nuclear translocation is a key part of the proposed mechanism. If the effect is modest or inconsistent across analysis methods, the conclusion is weakened. The discrepancy between methods raises concerns about the robustness of the finding.
- **Resolution test** Provide a clear description of the image analysis pipeline, including thresholds, segmentation parameters, and validation of the IHC profiler method for nuclear-cytoplasmic partitioning. Report inter-observer agreement statistics. Ideally, confirm the finding with an independent biochemical approach, such as nuclear and cytoplasmic fractionation followed by western blot for p65.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Dose-response and potency
- **Claim pointer** The manuscript states that Q3 inhibits NF-κB luciferase activity by approximately 40% at 3 μM and is used at 5 μM in subsequent experiments.
- **Evidence pointer** Section 3.3, Figure 4
- **Concern** Only a single concentration of Q3 (3 μM) is shown to inhibit luciferase activity, and the dose-response curve is not presented. The selection of 5 μM for subsequent experiments is not justified by a full dose-response analysis. The degree of inhibition (40%) is moderate, and it is unclear whether higher concentrations would achieve greater inhibition or whether the effect plateaus. Additionally, the specificity of Q3 for NF-κB over other transcription factors is not addressed.
- **Why it matters** For a compound proposed as a potential therapeutic lead, understanding its potency and efficacy range is essential. A single concentration does not establish a dose-response relationship, and the moderate effect size raises questions about the practical utility of the compound.
- **Resolution test** Provide a full dose-response curve for Q3 (e.g., 0.1–50 μM) on TNF-induced luciferase activity, with IC50 calculation. Include a control transcription factor reporter (e.g., AP-1) to assess specificity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational analysis rigor
- **Claim pointer** The manuscript claims that MD simulations and MM/GBSA calculations support stable and favorable binding of Q3 to NF-κB.
- **Evidence pointer** Section 3.4, Section 3.5, Figure 8, Table 1
- **Concern** The docking methodology is described briefly, and key parameters are not reported (e.g., grid box dimensions beyond the number of points, exhaustiveness, number of runs). The MD simulation is described as 100 ns, but no details on the equilibration protocol, temperature/pressure coupling, or convergence criteria are provided. The MM/GBSA calculations are performed on "the three most statistically significant protein-ligand complexes" but the clustering method and selection criteria are not described. The RMSD plots in Figure 8 are not quantified, and the claim that Q1 "diffused away" is based on visual inspection of the plot.
- **Why it matters** Computational results are only meaningful if the methodology is reproducible and the analysis is rigorous. The lack of detail prevents assessment of the validity of the in silico findings, which are central to the proposed mechanism.
- **Resolution test** Provide full computational details, including software versions, force field parameters, simulation protocols, and convergence analysis. Report quantitative RMSD values and interaction energies with standard deviations. Make input files and trajectories available or provide sufficient detail for reproduction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Section 3.3, Figure 5
- **Issue** The western blot data for IκBα are presented as representative images with densitometry, but the number of independent biological replicates is not stated in the figure legend or text. The loading control (β-tubulin) is shown, but the quantification method and normalization are not described.
- **Required correction** State the number of independent experiments and describe the densitometry normalization procedure in the figure legend or methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.9, Figures 4, 6, 7
- **Evidence pointer** Section 2.9
- **Issue** The statistical methods are described generically, but the specific tests used for each figure are not indicated. For example, it is unclear whether the comparisons in Figures 4, 6, and 7 used one-way ANOVA with post-hoc tests or non-parametric equivalents, and whether corrections for multiple comparisons were applied.
- **Required correction** Indicate the specific statistical test used for each figure panel in the figure legends, including post-hoc tests and correction methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Compound characterization
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The compound characterization includes melting point, LCMS, 1H NMR, 13C NMR, and elemental analysis. However, the purity of the compound is not explicitly stated, and HPLC data are not provided. The NMR spectra are referenced to Supplementary File S2, but the full spectra are not shown in the main text.
- **Required correction** State the purity of Q3 (e.g., by HPLC) and include representative full NMR spectra in the supplementary material.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Solubility and formulation
- **Affected element** Section 2.1, Section 2.2
- **Evidence pointer** Section 2.1
- **Issue** The compound is described as soluble only in DMSO, and the authors note that DMSO can interfere with assays. However, the final DMSO concentration in the cell culture experiments is not stated for the Q3 treatments. This is relevant because the authors show that 1% DMSO inhibits luciferase activity.
- **Required correction** State the final DMSO concentration in all cell-based assays and confirm that it is below the threshold that affects the assay.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Title, Abstract, Section 1
- **Evidence pointer** Title
- **Issue** The title describes Q3 as an inhibitor of the "canonical NF-κB transcription factor pathway," but the data show inhibition of transcriptional activity and partial interference with nuclear translocation, not direct inhibition of the pathway per se. The term "inhibitor" may overstate the findings given the moderate effect size and lack of mechanistic detail.
- **Required correction** Consider revising the title to reflect the observed effects more precisely, such as "A Novel Quinoline Compound That Modulates NF-κB-Dependent Transcription."

## Risk / unsupported claims
- The claim that Q3 "potentially interferes with the DNA-binding activity" of NF-κB is unsupported by direct experimental evidence; it is inferred solely from computational docking and MD simulations.
- The claim that Q3 "interferes with but does not block" p65 nuclear translocation is based on a single image analysis method with unresolved discrepancies between two quantification approaches.
- The statement in the Conclusions that Q3 "could be potentially developed for further in vivo studies" is speculative given the lack of pharmacokinetic, toxicity, or in vivo efficacy data.
- The assertion that the difference in binding energies between Q1 and Q3 to the NF-κB-DNA complex is functionally meaningful is not statistically validated.
- The claim that Q3's inhibitory effect is due to its structural rigidity (double bond) is speculative and not experimentally tested.