## Review setup
- **Input scope** Full manuscript text including abstract, background, results, discussion, conclusions, materials and methods, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and structural validity of claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that somatic missense mutations in CTCF zinc fingers are enriched in cancer, and that five specific mutations found in ALL exhibit a spectrum of loss-, change-, and gain-of-function phenotypes in cell growth and transcriptional regulation, which are explained by structure-function relationships derived from molecular dynamics simulations
- **Visible evidence base** Results sections describing mutation distribution analysis, cell growth assays, clonogenicity assays, transcriptional reporter assays, ChIP experiments, and MD simulations; figures referenced but not provided; supplementary tables referenced but not provided
- **Missing materials affecting confidence** Figures 1-6, Supplementary Figures 1-4, Supplementary Tables 1-4, raw data files, PDB accession files, and detailed statistical analysis outputs are not included in the provided material

## Reviewer
- **Overall assessment** This manuscript addresses an important and under-explored question regarding the functional consequences of somatic CTCF zinc finger mutations in cancer. The authors combine cancer genomics data mining with experimental functional assays and computational structural analysis to propose a structure-function framework for interpreting mutation impact. The conceptual approach is timely and potentially valuable. However, the current manuscript has several significant limitations that prevent full assessment of the claims. The absence of all figures and supplementary materials makes it impossible to evaluate the quality of the experimental data, the statistical rigor, and the validity of the structural interpretations. The experimental design, particularly regarding the use of overexpression systems and the choice of cell lines, raises questions about physiological relevance. The link between the observed cellular phenotypes and the proposed structural mechanisms, while plausible, is not definitively established. The manuscript would benefit from additional experiments to directly test the proposed mechanisms and to address alternative explanations for the observed phenotypes.

- **Who would be interested in the results, and why** Cancer biologists studying transcription factor mutations and their role in tumorigenesis would be the primary audience. Researchers working on chromatin architecture and CTCF function would find the structure-function analysis of interest. Computational biologists and structural biologists working on zinc finger proteins and DNA binding specificity would also be interested in the MD simulation approach. Clinically oriented researchers interested in biomarker development or targeted therapy for CTCF-mutant cancers might find the phenotypic characterization useful. The work bridges cancer genomics, transcription factor biology, and structural biology, which could attract a broad readership across these fields.

- **Major strengths** The manuscript addresses a clinically relevant and mechanistically important question that has been largely unexplored. The combination of cancer genomics data mining with experimental validation and computational structural analysis is a comprehensive approach. The inclusion of multiple functional assays (cell growth, clonogenicity, transcriptional reporter, ChIP) provides a multi-dimensional assessment of mutation impact. The use of MD simulations to provide structural explanations for phenotypic differences is innovative and adds mechanistic depth. The observation of gain-of-function phenotypes for G420D is particularly interesting and challenges the simple loss-of-function paradigm for CTCF mutations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that CTCF ZF mutations exhibit differential effects on cell growth, clonogenicity, and transcriptional regulation, with specific patterns of loss-, change-, and gain-of-function
- **Evidence pointer** Results sections "CTCF ZF mutations exhibit loss- and gain-of-function in cell growth phenotypes in vitro" and "CTCF ZF mutations disrupt transcriptional activity"; Figures 2, 3, and 4 referenced but not provided
- **Concern** The manuscript references Figures 2, 3, and 4 for the cell growth, clonogenicity, transcriptional reporter, and ChIP data, but none of these figures are included in the provided material. Without the actual data, it is impossible to assess the magnitude of the observed effects, the statistical significance, the variability between replicates, or the quality of the experimental results. The claim that G420D exhibits gain-of-function by further reducing clonogenic capacity compared to WT is a key finding, but the effect size and reproducibility cannot be evaluated.
- **Why it matters** The central claims of the manuscript rest entirely on these experimental results. If the effects are small, variable, or not statistically robust, the conclusions would be substantially weakened. The distinction between loss-, change-, and gain-of-function phenotypes is the foundation of the structure-function interpretation, and this distinction must be clearly supported by the data.
- **Resolution test** Provide all figures with complete data, including individual data points, error bars, statistical test results, and sample sizes. For the clonogenicity assay, provide representative images and quantification from at least three independent experiments. For the ChIP experiments, provide enrichment values relative to input and appropriate negative controls for each target site.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and physiological relevance
- **Claim pointer** The authors claim that the observed phenotypes of CTCF ZF mutations reflect their impact on CTCF tumour suppressor function
- **Evidence pointer** Results sections on cell growth and clonogenicity; Methods section on cell lines and transduction
- **Concern** All functional assays were performed using overexpression of WT or mutant CTCF in K562 and HEK293T cells. The manuscript does not address whether the observed phenotypes are dependent on the expression level of the mutant protein relative to endogenous CTCF, nor whether the effects are specific to the mutant allele or could be due to overexpression artifacts. The use of a single cell line for the growth and clonogenicity assays limits the generalizability of the findings. Additionally, the manuscript does not discuss whether the mutations exert their effects in a dominant-negative manner, which would be relevant given that CTCF is haploinsufficient and cancer cells typically retain one WT allele.
- **Why it matters** Overexpression systems can produce non-physiological effects that do not reflect the behavior of the mutant protein at endogenous expression levels. The interpretation of the phenotypes as reflecting tumour suppressor function requires evidence that the effects are specific to the mutant and relevant in a more physiological context. The haploinsufficient nature of CTCF means that the interaction between mutant and WT alleles is critical for understanding the net functional outcome.
- **Resolution test** Include experiments with endogenous levels of mutant CTCF expression, such as CRISPR-mediated knock-in of the mutations into a cell line. Alternatively, perform knockdown of endogenous CTCF and rescue with WT or mutant constructs to assess allele-specific effects. Include a dose-response experiment to show that the observed phenotypes are not simply due to overexpression. Consider using additional cell lines to demonstrate generalizability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation validity
- **Claim pointer** The authors claim that MD simulations explain the loss- and gain-of-function phenotypes of CTCF ZF mutations through changes in protein stability, DNA binding, and conformational dynamics
- **Evidence pointer** Results section "Molecular dynamics (MD) simulations explain CTCF loss- and gain-of-function ZF mutant phenotypes"; Figures 5 and 6 referenced but not provided; Supplementary Figure 3 and 4 referenced but not provided
- **Concern** The MD simulation results are presented as providing mechanistic explanations for the observed phenotypes, but the connection between the computational predictions and the experimental observations is not rigorously established. The manuscript reports ΔΔG values for each mutation, but the relationship between these values and the functional outcomes is not quantitatively assessed. The claim that G420D forms a new hydrogen bond with DNA and shifts toward DNA, explaining its gain-of-function phenotype, is based on a single simulation trajectory and lacks experimental validation. The manuscript does not address the limitations of the MD approach, such as the short simulation time (10 ns), the use of implicit solvent, and the potential for force field inaccuracies.
- **Why it matters** The structure-function framework is a major contribution of the manuscript, but it must be supported by robust computational evidence and, ideally, experimental validation. If the MD predictions are not reliable or are not directly linked to the functional data, the central thesis of the manuscript is weakened. The gain-of-function mechanism proposed for G420D is particularly important and requires stronger support.
- **Resolution test** Provide convergence analysis for the MD simulations, including RMSD plots over time for all systems. Perform replicate simulations with different initial velocities to ensure reproducibility. Validate the predicted structural changes experimentally, for example, by electrophoretic mobility shift assays with purified mutant proteins or by hydrogen-deuterium exchange mass spectrometry. Provide a quantitative correlation between the computed ΔΔG values and the experimentally measured functional outcomes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that the CTCF ZF domain is significantly enriched for somatic missense mutations in cancer, and that specific mutations have differential functional impacts
- **Evidence pointer** Results section "CTCF ZF domain is enriched for somatic missense mutations in cancer"; Figure 1 referenced but not provided; Supplementary Tables 1 and 2 referenced but not provided
- **Concern** The statistical analysis supporting the enrichment of missense mutations in the ZF domain is not described in sufficient detail. The manuscript does not specify the statistical test used, how the expected number of mutations was calculated, or how potential confounders such as mutation rate variation across the genome were addressed. The comparison between somatic mutations and SNPs is interesting, but the analysis may be affected by differences in ascertainment between the two datasets. The manuscript also does not report confidence intervals or effect sizes for the enrichment.
- **Why it matters** The claim of ZF domain enrichment is a key observation that motivates the entire study. If the statistical analysis is flawed or the enrichment is not robust, the rationale for focusing on ZF mutations is weakened. The comparison with SNPs is used to argue for cancer-specific selection, and this requires careful statistical handling.
- **Resolution test** Provide a detailed description of the statistical methods, including the exact test used, the null model, and how multiple testing was handled. Report effect sizes and confidence intervals for the enrichment. Perform sensitivity analyses to show that the result is robust to different methods of calculating expected mutation rates. Provide the full data in Supplementary Tables for independent verification.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic depth
- **Claim pointer** The authors claim that the observed phenotypes are explained by structure-function relationships, specifically that mutations affect DNA binding and transcriptional regulation
- **Evidence pointer** Results sections on transcriptional activity and ChIP; Discussion section
- **Concern** The manuscript demonstrates that CTCF ZF mutations affect cell growth and transcriptional reporter activity, and that DNA binding is altered at some target sites. However, the link between these observations is not fully explored. The manuscript does not identify which target genes are misregulated by the mutant CTCF proteins, nor does it establish a causal relationship between altered DNA binding at specific sites and the observed growth phenotypes. The ChIP experiments show selective loss of binding at some sites, but the functional consequences of these changes are not investigated.
- **Why it matters** The claim that structure-function relationships explain the phenotypes requires a mechanistic chain from structural change to altered DNA binding to changes in gene expression to phenotypic outcome. The current manuscript provides evidence for each step in isolation but does not connect them. Without this connection, the interpretation remains correlative rather than causal.
- **Resolution test** Perform RNA-seq or qRT-PCR to identify genes whose expression is altered by mutant CTCF expression. Correlate these expression changes with the ChIP data to identify direct target genes. Use CRISPR-mediated deletion or mutation of specific CTCF binding sites to test whether the growth phenotype depends on altered binding at these sites.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** MD simulation methods
- **Evidence pointer** Methods section "Structural Modelling and MD simulations"
- **Issue** The description of the MD simulation protocol is incomplete. The manuscript states that simulations were performed using GROMACS version 4.5.3 with implicit solvent, but does not specify the force field used, the water model (if any), the temperature coupling method, or the pressure coupling method. The simulation time is stated as 10 ns, but the number of replicates is not mentioned.
- **Required correction** Provide a complete description of the MD simulation parameters, including the force field, the treatment of electrostatics, the thermostat and barostat algorithms, and the number of replicate simulations performed. Justify the choice of implicit solvent and the simulation time.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Results section "CTCF ZF domain is enriched for somatic missense mutations in cancer"; Figure 1 referenced but not provided
- **Issue** The manuscript describes Figure 1 as showing the distribution and frequency of all known somatic mutations in CTCF, but the figure is not provided. The description of the figure in the text is brief and does not explain how the data are presented or what the key findings are.
- **Required correction** Provide a detailed figure legend for Figure 1 that explains the data presentation, including the type of plot, the axes, and the color coding. In the text, describe the key features of the figure that support the claim of ZF enrichment.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Control experiments
- **Affected element** Cell growth and clonogenicity assays
- **Evidence pointer** Results section "CTCF ZF mutations exhibit loss- and gain-of-function in cell growth phenotypes in vitro"
- **Issue** The manuscript does not describe the use of a WT CTCF overexpression control in the cell growth and clonogenicity assays. It is unclear whether the effects observed for the mutants are compared to WT CTCF overexpression or to empty vector control. The text mentions that WT CTCF suppressed proliferation compared to empty vector, but the statistical comparison between WT and each mutant is not clearly described.
- **Required correction** Clarify the experimental design, including the specific comparisons made and the statistical tests used. State whether WT CTCF overexpression was used as a control in all experiments and whether the mutant phenotypes were statistically different from WT.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of ChIP data
- **Affected element** ChIP experiments
- **Evidence pointer** Results section "CTCF ZF mutations disrupt transcriptional activity"; Figure 4 referenced but not provided
- **Issue** The manuscript reports that ChIP experiments showed selective loss of DNA binding for the mutants at some target sites, but the criteria for "selective" are not defined. It is unclear whether the loss of binding was complete or partial, and whether the differences between WT and mutant were statistically significant at each site.
- **Required correction** Provide quantitative ChIP data with statistical analysis for each target site. Define the threshold for "loss of binding" and report the number of independent experiments performed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Issue** The Discussion section does not adequately address the limitations of the study, particularly the use of overexpression systems, the limited number of mutations examined, and the reliance on computational predictions without experimental validation of the structural changes.
- **Required correction** Add a paragraph discussing the limitations of the study and the potential impact of these limitations on the interpretation of the results. Suggest future experiments that could address these limitations.

## Risk / unsupported claims
- The claim that CTCF ZF mutations exhibit a spectrum of loss-, change-, and gain-of-function phenotypes is not fully supported because the figures containing the primary data are not provided.
- The claim that MD simulations explain the observed phenotypes is not fully supported because the simulation details are incomplete and the connection between computational predictions and experimental results is not rigorously established.
- The claim that the CTCF ZF domain is significantly enriched for somatic missense mutations in cancer is not fully assessable because the statistical methods are not described in sufficient detail and the supporting data are not provided.
- The claim that G420D exhibits a gain-of-function phenotype through the formation of a new hydrogen bond with DNA is not supported by experimental validation and is based on a single simulation trajectory.
- The claim that the observed phenotypes reflect the impact of mutations on CTCF tumour suppressor function is not fully supported because the experiments were performed using overexpression systems and the relevance to endogenous CTCF function is not established.
- The claim that the manuscript is the first to examine the effect of somatic mutation on CTCF ZF structure-function relationships is not verifiable from the provided material, as a comprehensive literature search was not possible.
- The PDB accession files listed in the Data Availability section (L309P, 1A2B; R339Q, 3C4D; R339W, 5E6F; R377H, 7G8H; G420D, 9I0J) appear to be placeholder or incorrect, as these accession codes do not correspond to the described CTCF structures. This requires verification.

## Assessment against Nature-style criteria
- **Originality** The manuscript addresses a question that has not been systematically examined, namely the structure-function relationships of somatic CTCF zinc finger mutations. The combination of cancer genomics, functional assays, and MD simulations is a novel approach. However, the individual components are not entirely new, and the manuscript does not fully distinguish itself from prior work on CTCF mutations.
- **Scientific importance** The topic is of significant importance given the high frequency of CTCF mutations in multiple cancer types and the fundamental role of CTCF in genome organization. Understanding the functional consequences of these mutations could have implications for cancer biology and potentially for therapeutic strategies. However, the importance is somewhat diminished by the limited number of mutations examined and the lack of mechanistic depth.
- **Interdisciplinary readership** The manuscript has the potential to appeal to cancer biologists, chromatin biologists, structural biologists, and computational biologists. The integration of experimental and computational approaches is a strength. However, the manuscript may be too specialized for a general audience, and the lack of clear figures and detailed methods may limit accessibility.
- **Technical soundness** The experimental approaches are generally sound, but the manuscript has several technical limitations, including the use of overexpression systems, the limited number of cell lines, and the lack of experimental validation of the computational predictions. The MD simulation methods are not described in sufficient detail to assess their rigor. The statistical analysis of the mutation enrichment is not fully described.
- **Readability for nonspecialists** The manuscript is written in a clear and logical manner, but the heavy reliance on specialized terminology and the lack of accessible figures may make it difficult for nonspecialists to fully appreciate the findings. The abstract provides a good summary, but the main text could benefit from more context and explanation of key concepts.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important question and has a potentially valuable approach, but the absence of all figures and supplementary materials prevents a full assessment of the data quality and the validity of the claims. The experimental design has limitations that need to be addressed, and the link between the computational predictions and the experimental observations needs to be strengthened. The manuscript would be suitable for reconsideration after major revisions that address these concerns.