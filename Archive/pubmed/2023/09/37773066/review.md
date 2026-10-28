## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific content, experimental design, data analysis, interpretation, and claims as presented. Editorial quality and formatting are considered only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors generated a panel of ten MCF10A-derived cell lines, each stably expressing one of the ten most common TP53 missense mutants found in breast cancer, and characterized six cancer-related phenotypes. They report mutant-specific phenotypic heterogeneity, with R248W, R273C, R248Q, and Y220C being most aggressive and G245S and Y234C least aggressive, correlating with patient survival. RNA-Seq and ChIP-Seq identified distinct transcriptional and DNA-binding profiles, and integrative pathway analysis implicated the Hippo/YAP/TAZ pathway as a key driver of invasiveness. MD simulations provided structural rationales for differential DNA binding.
- **Visible evidence base** Main text figures (Figs. 1, 2, 3, 5, 6, 7), supplementary figures (Supplementary Figs. 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18), supplementary tables (Supplementary Tables 1, 2, 3), and methods sections.
- **Missing materials affecting confidence** Raw RNA-Seq and ChIP-Seq data files, processed data matrices, and complete lists of differentially expressed genes and peaks are not provided in the manuscript. Details on the number of biological replicates for RNA-Seq and ChIP-Seq experiments are not fully specified. The manuscript states that xenograft experiments were performed but results are described as unpublished, limiting the in vivo validation. Statistical details for some comparisons (e.g., survival analysis) are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a systematic and quantitative characterization of ten common TP53 missense mutants in an isogenic, non-transformed mammary epithelial cell model. The work is ambitious in scope, combining phenotypic assays, transcriptomics, chromatin profiling, and molecular dynamics simulations. The finding that different missense mutants produce distinct, sometimes opposing, phenotypic outcomes, exemplified by the R273C vs. R273H comparison, is potentially important. The association of the Hippo/YAP/TAZ pathway with invasiveness is a valuable observation. However, the manuscript has several significant technical and conceptual limitations that currently prevent the case from being fully established. These include the use of a single cell line, potential overexpression artifacts, incomplete validation of ChIP-Seq findings, and a correlative rather than causal link between the identified pathways and phenotypes. The clinical correlations are based on small patient subgroups and require more robust statistical support. The molecular dynamics simulations are preliminary and not fully integrated with the experimental data. Despite these concerns, the dataset is a useful resource for the field.
- **Who would be interested in the results, and why** Researchers studying TP53 biology, particularly the functional consequences of missense mutations; investigators focused on triple-negative breast cancer and its heterogeneity; those interested in the Hippo/YAP/TAZ pathway in cancer; and scientists developing mutant p53-targeted therapies. The systematic phenotyping approach may also be of interest to the broader functional genomics community.
- **Major strengths**
  1. Systematic and quantitative comparison of ten clinically relevant TP53 missense mutants in a controlled isogenic background, addressing a significant gap in the field.
  2. Multidimensional approach integrating phenotypic, transcriptomic, and epigenomic data, providing a rich resource.
  3. The identification of dramatic functional differences between mutants at the same residue (R273C vs. R273H) is a compelling and novel observation.
  4. The development and application of customized pathway analysis methods to link gene expression to continuous phenotypic traits is methodologically thoughtful.
  5. The correlation of in vitro phenotypic aggressiveness with patient survival data, while preliminary, suggests clinical relevance.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental model and physiological relevance
- **Claim pointer** The manuscript claims that the phenotypic differences observed in the MCF10A panel reflect the neomorphic behaviors of p53 missense mutants relevant to triple-negative breast cancer.
- **Evidence pointer** Results section "Characterization and quantification of multiple cancer phenotypes...", Fig. 1, Fig. 3
- **Concern** The entire study is based on a single, non-transformed, immortalized cell line (MCF10A) with ectopic overexpression of mutant p53. While this provides an isogenic background, it does not recapitulate the complex genetic and microenvironmental context of human breast tumors. The relevance of these findings to actual tumor biology, where p53 mutations occur alongside numerous other genetic alterations, is unclear. The authors acknowledge this limitation in the Discussion, but it fundamentally limits the strength of the claims about clinical relevance.
- **Why it matters** The central claim of the paper is that specific p53 missense mutations drive distinct neomorphic phenotypes that contribute to clinical heterogeneity. Without validation in more physiologically relevant models (e.g., patient-derived cells, organoids, or in vivo models with endogenous mutant p53 expression), the translational significance of these findings remains speculative.
- **Resolution test** The authors should either validate key findings in additional cell lines or more complex models, or substantially temper the claims about clinical relevance. Demonstrating that the phenotypic spectrum and pathway associations hold in a second, independent isogenic system or in a panel of TP53-mutant breast cancer cell lines would significantly strengthen the case.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal evidence for pathway involvement
- **Claim pointer** The manuscript claims that the Hippo/YAP/TAZ pathway plays a key role in driving the cellular phenotypes towards basal-like in the presence of more aggressive p53 mutants.
- **Evidence pointer** Results section "Transcriptomic profiling and integrative quantitative pathway analysis...", Fig. 4, Fig. 5, Fig. 7
- **Concern** The evidence linking the Hippo/YAP/TAZ pathway to the observed phenotypes is entirely correlative. The authors show that Hippo pathway gene expression correlates with invasiveness and that TEAD activity is higher in invasive cells. However, no functional perturbation experiments (e.g., knockdown or overexpression of YAP/TAZ, or treatment with Hippo pathway inhibitors) are performed to demonstrate that this pathway is causally required for the aggressive phenotypes. The claim that this pathway "plays a key role in driving" the phenotypes is therefore not supported by the data.
- **Why it matters** The identification of a causal driver pathway would be a major contribution and could have therapeutic implications. As presented, the data only show an association, which could be a downstream consequence of other changes or a bystander effect. The strong causal language in the abstract and discussion overstates the evidence.
- **Resolution test** The authors should perform loss- and/or gain-of-function experiments targeting key Hippo pathway components (e.g., YAP1, TAZ, TEAD) in the aggressive mutant cell lines and assess the impact on invasion, migration, and other phenotypes. If the phenotypes are reversed, the causal claim would be supported.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data completeness and accessibility
- **Claim pointer** The manuscript claims that RNA-Seq and ChIP-Seq analyses show distinct DNA binding properties and heterogeneous transcriptomic profiles for different p53 mutants.
- **Evidence pointer** Results sections "Transcriptomic profiling..." and "ChIP-Seq uncovered heterogeneity...", Methods sections "RNA-Seq" and "ChIP-Seq"
- **Concern** The raw and processed RNA-Seq and ChIP-Seq data are not provided or referenced with accession numbers. The manuscript mentions supplementary tables with results, but these are not available for review. Without access to the underlying data, the quality of the analysis, the validity of the differential expression and peak calling, and the robustness of the pathway enrichment results cannot be independently assessed. Furthermore, the number of biological replicates for these genomic experiments is not clearly stated.
- **Why it matters** The genomic analyses are central to the manuscript's conclusions about the molecular mechanisms. The lack of data availability and unclear experimental design details prevent a thorough evaluation of the technical soundness of these results and hinder reproducibility, which is a core expectation for high-impact publications.
- **Resolution test** The authors should deposit all raw and processed sequencing data in a public repository (e.g., GEO) and provide accession numbers. They should also clearly state the number of biological replicates used for each experiment and provide details on the statistical methods used for differential analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Clinical correlation and statistical power
- **Claim pointer** The manuscript claims that the phenotypic aggressiveness of the p53 mutants correlates with survival rates of basal-like breast cancer patients.
- **Evidence pointer** Results section "Association of cellular phenotypes with overall survival...", Fig. 3b, 3c, Supplementary Fig. 10
- **Concern** The survival analysis is based on a small number of patients per mutation group (as implied by the text, though exact numbers are not given). The authors state that only mutations with three or more samples were used, which likely results in very small groups for some mutations. The statistical significance is marginal (log-rank p = 0.072 for the overall comparison). The correlation analysis between phenotypic aggressiveness and survival (Fig. 3c) is based on only eight data points (one per mutation), which is a very small sample size for a correlation analysis.
- **Why it matters** The claim of clinical relevance is a key part of the paper's significance. If the correlation is not robust due to small sample sizes, the conclusion that the in vitro phenotypes reflect clinical behavior is not well supported. This could mislead the field about the prognostic value of specific p53 mutations.
- **Resolution test** The authors should provide the exact number of patients in each mutation group, report confidence intervals for the survival estimates, and perform a more robust statistical analysis. Ideally, they should validate the correlation in an independent patient cohort. If the sample size is too small for robust conclusions, the claim should be appropriately qualified.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic depth of molecular dynamics simulations
- **Claim pointer** The manuscript claims that MD simulations provided a structural basis for differential DNA binding of different p53 mutants.
- **Evidence pointer** Results section "ChIP-Seq uncovered heterogeneity...", Supplementary Fig. 18
- **Concern** The MD simulation results are presented very briefly and are not well integrated with the experimental data. The description of the simulations is superficial, and it is unclear how the simulations were set up, how long they were run, and what specific structural features were compared. The claim that the simulations provide a "structural basis" for the observed differences in DNA binding is not convincingly supported by the data presented. For example, the finding that R273H retains some electrostatic interaction while R273C does not is interesting, but it is not clear how this translates to the genome-wide binding differences observed in ChIP-Seq.
- **Why it matters** The MD simulations are presented as a key part of the multi-level analysis. If they are not rigorous or are not clearly linked to the experimental observations, they add little to the paper and may distract from the stronger experimental findings. The current level of detail is insufficient for a reader to evaluate the validity of the simulation results.
- **Resolution test** The authors should provide a more detailed description of the simulation methods, including system setup, force field parameters, simulation length, and analysis. They should also more explicitly connect the simulation results to the ChIP-Seq data, for example, by discussing how the predicted structural changes might affect binding to specific DNA sequences or chromatin contexts.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 3a and associated text
- **Evidence pointer** Results section "Characterization and quantification...", Fig. 3a
- **Issue** The heatmap in Fig. 3a is described as showing "phenotype measurements" normalized to WTOE, but the specific metric used to create the heatmap (e.g., z-score, fold-change) is not clearly defined in the figure legend or the text. The color scale is also not shown.
- **Required correction** Clarify the metric used for the heatmap and include a color scale. Define the "overall aggressiveness" score used in Fig. 3c.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Survival analysis
- **Evidence pointer** Results section "Association of cellular phenotypes...", Fig. 3b
- **Issue** The number of patients at risk in each group at different time points is not shown in the Kaplan-Meier plot. The exact p-values for pairwise comparisons between mutation groups are not reported.
- **Required correction** Add a risk table to the Kaplan-Meier plot and report pairwise p-values (with multiple testing correction) for the survival comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Western blot quantification
- **Evidence pointer** Results section "Characterization and quantification...", Supplementary Fig. 1b
- **Issue** The western blot in Supplementary Fig. 1b shows p53 protein levels, but it is not clear if this is a representative blot or if quantification from multiple experiments was performed. The text states that Y234C showed lower levels, but no quantification is provided.
- **Required correction** Provide quantification of western blots from at least three independent experiments, with loading controls, and report the statistical significance of any differences in protein levels.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Correlation between phenotypes
- **Evidence pointer** Results section "Characterization and quantification...", Fig. 3a
- **Issue** The authors note that some phenotypes do not correlate with each other (e.g., viability vs. apoptosis resistance). This is interesting but is not discussed in detail. It would be helpful to understand whether these are independent axes of mutant behavior.
- **Required correction** Add a brief discussion of the relationships (or lack thereof) between different phenotypic traits and what this implies about the multifunctional nature of p53 mutants.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Pathway analysis
- **Evidence pointer** Methods section "Enrichment and model-based pathway analysis"
- **Issue** The description of the PLSR-based pathway analysis is somewhat technical and may be difficult for a non-specialist to follow. The key steps and the rationale for using this approach over simpler methods could be explained more clearly.
- **Required correction** Provide a more accessible description of the PLSR method, perhaps with a schematic diagram, and clearly state what advantages it offers over standard GSEA for this type of data.

## Risk / unsupported claims
- The claim that the Hippo/YAP/TAZ pathway "plays a key role in driving" the aggressive phenotypes is unsupported by the correlative data presented; causal experiments are needed.
- The claim that the in vitro phenotypic spectrum "correlates with survival rates of basal-like breast cancer patients" is based on a small number of patients and marginal statistical significance; this should be considered preliminary.
- The claim that MD simulations provide a "structural basis" for differential DNA binding is not sufficiently detailed or integrated with the experimental data to be fully evaluated.
- The claim that the MCF10A model reflects the "early stage of breast cancer development in vivo" is an extrapolation that is not directly supported by the data.
- The statement that "p53 tetramers in the cell lines predominantly function as mutant p53" is an assumption based on protein levels and does not account for potential mixed tetramers with endogenous wild-type p53.