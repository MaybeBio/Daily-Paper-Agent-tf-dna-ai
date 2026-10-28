## Review setup
- **Input scope** Full manuscript text including abstract, highlights, introduction, materials and methods, results, discussion, conclusion, and declarations. Figure legends are present but figure images are not available for inspection.
- **Assessment boundary** This review evaluates the scientific claims, methodological rigor, and evidentiary support presented in the manuscript. It does not assess editorial fit or journal-specific policy compliance beyond general Nature-style criteria.
- **Shared manuscript claim summary** The authors report that a machine learning framework integrating 117 algorithm combinations identified SP5 as a core sunitinib resistance gene in renal cell carcinoma (RCC). They claim that SP5 directly binds to the VEGFA promoter to upregulate VEGFA transcription, activating AKT phosphorylation via autocrine and paracrine loops, thereby driving angiogenesis and sunitinib resistance. They further report that suramin, identified by virtual screening, disrupts the SP5-VEGFA interaction and synergizes with sunitinib to overcome acquired resistance.
- **Visible evidence base** Bulk RNA-seq datasets (GSE172165, GSE173572, GSE216494), scRNA-seq dataset (GSE156632), four prognostic cohorts (TCGA-KIRC, EMTAB, CTPAC, GSE167573), in vitro assays (qRT-PCR, Western blot, CUT&RUN, dual-luciferase, CCK-8, colony formation, wound healing, transwell, tube formation), in vivo xenograft model, and virtual docking (AutoDock, Selleck L1300 database).
- **Missing materials affecting confidence** Figure images are not provided, preventing visual verification of Western blot quality, microscopy data, and tumor images. Supplementary tables (S1-S3) containing shRNA sequences, primer sequences, and antibody information are referenced but not included. Statistical details such as exact P values, sample sizes for each experiment, and replication numbers are not fully reported in the text. The docking methodology and scoring function details are not described.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive bioinformatics-driven discovery pipeline with substantial experimental validation. The identification of SP5 as a regulator of VEGFA transcription and its role in sunitinib resistance is potentially interesting. However, several technical concerns regarding the specificity of the SP5-VEGFA interaction, the robustness of the machine learning approach, and the translational relevance of the suramin findings require clarification. The manuscript is well-structured and the narrative is coherent, but the evidentiary depth for some mechanistic claims is currently insufficient to fully establish the case.
- **Who would be interested in the results, and why** Researchers in renal cell carcinoma biology, drug resistance mechanisms, angiogenesis research, and transcriptional regulation would find these results relevant. The machine learning framework for biomarker discovery may also interest computational oncologists. The potential therapeutic application of suramin in combination with sunitinib could attract translational researchers and clinicians in urologic oncology.
- **Major strengths** The study integrates multiple public datasets with orthogonal experimental validation, which is commendable. The use of a large algorithm ensemble (117 combinations) for model selection is methodologically thorough. The mechanistic work linking SP5 to VEGFA transcription via CUT&RUN and luciferase assays provides direct evidence for the proposed regulatory axis. The identification of suramin as a potential SP5 inhibitor with functional validation in vitro and in vivo adds translational value.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the machine learning model
- **Claim pointer** The authors claim that a 117-algorithm machine learning framework identified SP5 as a core sunitinib resistance gene and established a robust prognostic risk model.
- **Evidence pointer** Materials and methods, "Construction of the machine learning model"; Results, "Screening of Sunitinib Resistance Genes and Single-Cell Omics Characterization in RCC" and "Model Performance Validation and Establishment of a Prognostic Nomogram"
- **Concern** The description of the machine learning framework is insufficiently detailed. The authors state that 117 algorithm combinations were evaluated and that SuperPC was selected as the optimal model, but they do not specify the exact algorithms included, the hyperparameter tuning strategy, the feature selection procedure, or the criteria for defining "optimal." The risk score composition is not described, and the number of genes included in the final model is not stated. Furthermore, the validation approach relies on C-index and AUC values, but the potential for overfitting in a high-dimensional setting with 118 candidate genes is not addressed. The claim of robustness is not fully supported without details on internal cross-validation schemes, calibration, or comparison to simpler models.
- **Why it matters** The machine learning model is the foundation for identifying SP5 as the key gene. Without adequate methodological detail, the reproducibility and generalizability of the model cannot be assessed, and the claim that SP5 is the "core" resistance gene may be an artifact of the specific algorithm ensemble rather than a biologically robust finding.
- **Resolution test** Provide a complete description of the algorithm ensemble, feature selection, hyperparameter optimization, and model selection criteria. Report the final gene list in the risk score, the coefficients or weights, and the performance metrics with confidence intervals. Include a nested cross-validation or bootstrap validation to demonstrate model stability. Show that the model outperforms simpler baseline models (e.g., LASSO alone or a single-gene SP5 model).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of SP5 binding to the VEGFA promoter
- **Claim pointer** The authors claim that SP5 directly binds to binding site 1 within the VEGFA promoter to transcriptionally upregulate VEGFA.
- **Evidence pointer** Results, "SP5 potentiates renal cancer angiogenesis and sunitinib resistance via VEGFA-mediated pAKT activation through autocrine and paracrine loops"; Figure 7G-J
- **Concern** The CUT&RUN assay identified binding at site 1 but not sites 2 and 3. However, the functional significance of this single binding site is not fully established. The luciferase reporter assay shows that mutation of site 1 abolishes SP5-enhanced transcription, but the magnitude of the effect and the baseline activity are not reported. It is unclear whether SP5 binding to site 1 is sufficient for transcriptional activation or whether other co-factors are required. Additionally, the authors do not address whether SP5 binding to the VEGFA promoter is direct or mediated through other DNA-binding proteins, given that CUT&RUN can detect indirect chromatin interactions. The specificity of the SP5 antibody used in CUT&RUN is not validated.
- **Why it matters** The direct binding of SP5 to the VEGFA promoter is the central mechanistic claim of the paper. If this interaction is not specific or is indirect, the proposed model of SP5-driven VEGFA transcription is weakened, and the suramin-based therapeutic strategy targeting this interaction loses its rationale.
- **Resolution test** Perform an electrophoretic mobility shift assay (EMSA) with recombinant SP5 protein and the VEGFA promoter fragment containing site 1 to demonstrate direct protein-DNA interaction. Include a competition assay with unlabeled probe. Validate the SP5 antibody by Western blot using SP5-knockdown lysates. Report the fold-change in luciferase activity with standard deviations and show that SP5 overexpression alone is sufficient to drive transcription from the wild-type but not the mutant promoter.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Suramin mechanism of action
- **Claim pointer** The authors claim that suramin binds to the C2H2 zinc-finger domain of SP5, disrupting the SP5-VEGFA interaction and resensitizing tumors to sunitinib.
- **Evidence pointer** Results, "Suramin enhances sunitinib sensitivity via disruption of SP5-VEGFA promoter interaction"; Figure 8
- **Concern** The virtual docking prediction is presented without experimental validation of the physical binding between suramin and SP5. The docking score of -12.3 kcal/mol is reported, but the scoring function, the protein structure used, and the docking protocol are not described. The functional assays show that suramin reduces VEGFA mRNA and secretion and enhances sunitinib sensitivity, but these effects could be due to off-target mechanisms unrelated to SP5 binding. Suramin is known to inhibit multiple enzymes and growth factors, and its effects on VEGFA expression could be indirect. No experiment directly demonstrates that suramin disrupts SP5 binding to the VEGFA promoter in cells.
- **Why it matters** The suramin finding is presented as a potential therapeutic strategy. If the mechanism of action is not established, the translational claim is premature. Suramin is an old drug with known toxicity, and its repurposing for RCC requires a clear mechanistic basis to justify further development.
- **Resolution test** Perform a cellular thermal shift assay (CETSA) or surface plasmon resonance (SPR) to demonstrate direct binding between suramin and SP5. Use a chromatin immunoprecipitation (ChIP) assay to show that suramin treatment reduces SP5 occupancy at the VEGFA promoter. Include a negative control compound with similar physicochemical properties that does not bind SP5. Show that suramin does not affect VEGFA expression in SP5-knockdown cells, demonstrating on-target specificity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance of the risk model
- **Claim pointer** The authors claim that the risk model can stratify patients into high- and low-risk groups with significantly different prognosis, and that this has clinical utility.
- **Evidence pointer** Results, "Model Performance Validation and Establishment of a Prognostic Nomogram"; Figure 3
- **Concern** The risk model is built and validated on retrospective cohorts. The clinical utility of the model is not demonstrated beyond statistical significance. The authors do not report whether the model adds predictive value beyond established clinical variables (e.g., TNM stage, Fuhrman grade) in a multivariable analysis. The nomogram is presented, but decision curve analysis is only shown for the model itself, not compared to a "treat-all" or "treat-none" strategy. The external validation cohorts are relatively small, and the model's performance in non-clear cell RCC subtypes is not assessed.
- **Why it matters** For a prognostic model to be clinically useful, it must demonstrate added value over standard of care and be validated in appropriate external cohorts. Without this, the model remains a research tool with unclear translational impact.
- **Resolution test** Perform a multivariable Cox regression including the risk score and established clinical variables to show independent prognostic value. Report the net reclassification improvement (NRI) or integrated discrimination improvement (IDI) compared to a clinical-only model. Validate the model in an independent cohort with clear cell RCC only, and report performance separately for early- and late-stage disease.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** In vivo experimental design
- **Claim pointer** The authors claim that SP5 knockdown reduces tumor growth in xenograft models, supporting the tumor-promoting role of SP5.
- **Evidence pointer** Results, "SP5 modulates malignant progression and sunitinib resistance in RCC"; Figure 6E-F
- **Concern** The xenograft experiment is described only briefly. The number of mice per group, the duration of the experiment, and whether the tumors were measured blinded are not reported. The authors do not state whether the xenograft model included sunitinib treatment to assess resistance in vivo. The tumor growth curves are mentioned but not shown in the text. The statistical analysis for the in vivo data is not described.
- **Why it matters** In vivo data are critical for validating the functional role of SP5 and for supporting the therapeutic claims. Incomplete reporting of the experimental design limits the ability to assess the reliability of the conclusions.
- **Resolution test** Report the number of animals per group, the randomization and blinding procedures, and the statistical tests used. Include tumor growth curves with error bars and individual data points. If sunitinib resistance is claimed, include a group treated with sunitinib to demonstrate that SP5 knockdown resensitizes tumors to the drug.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Figure legends
- **Evidence pointer** Figures 1-9
- **Issue** The figure legends are present but do not include information on the number of biological replicates, the statistical tests used, or the meaning of error bars. Some legends are abbreviated (e.g., "Fig 1 dummy alt text").
- **Required correction** Expand all figure legends to include the number of independent experiments, the statistical test used, the definition of error bars (SD vs. SEM), and the significance thresholds. Remove placeholder text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting of statistical details
- **Affected element** Results and figure legends
- **Evidence pointer** Throughout the Results section
- **Issue** The text reports significance levels as asterisks (e.g., *P < 0.05) but does not consistently report exact P values or effect sizes. The number of replicates for each experiment is not stated in the text.
- **Required correction** Report exact P values for all comparisons, or at minimum provide the number of replicates and the test statistic. State the number of independent biological replicates for each experiment in the figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Availability of data and materials section
- **Evidence pointer** "Availability of data and materials"
- **Issue** The statement says "The TCGA and GEO databases are publicly available" and "The datasets and custom scripts are available upon request." This is vague and does not specify which scripts or how to access them.
- **Required correction** Provide a clear data availability statement that includes accession numbers for all datasets used, a link to a repository (e.g., GitHub) for custom scripts, and a contact for data requests.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Docking methodology details
- **Affected element** Materials and methods, "Drug screening" (implied)
- **Evidence pointer** Results, "Suramin enhances sunitinib sensitivity via disruption of SP5-VEGFA promoter interaction"
- **Issue** The virtual screening methodology is not described in the Materials and methods section. The protein structure of SP5 used for docking, the preparation of the ligand library, and the scoring function are not specified.
- **Required correction** Add a subsection in Materials and methods describing the virtual screening protocol, including the source of the SP5 structure (e.g., AlphaFold, homology model), the software used, the docking parameters, and the criteria for selecting the top hit.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency of terminology
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The terms "sunitinib resistance genes," "sunitinib resistance-related DEGs," and "core sunitinib resistance gene" are used interchangeably. The definition of "core" is not explicitly stated.
- **Required correction** Define the term "core sunitinib resistance gene" in the Results or Methods, and use consistent terminology throughout the manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, final paragraph
- **Issue** The limitations section is brief and does not address the potential for confounding in the bioinformatics analysis, the lack of a positive control in the suramin experiments, or the generalizability of the findings beyond clear cell RCC.
- **Required correction** Expand the limitations paragraph to address these points and suggest specific future experiments to overcome them.

## Risk / unsupported claims
- The claim that SP5 is the "core" sunitinib resistance gene is not fully supported, as the model selection criteria and the relative contribution of SP5 compared to other genes in the risk score are not reported.
- The claim that suramin "disrupts the SP5-VEGFA interaction" is not directly demonstrated experimentally; only indirect functional evidence is provided.
- The claim that the risk model has clinical utility is not supported by evidence of added value over standard clinical variables.
- The claim that SP5 regulates angiogenesis via VEGFA/AKT in both autocrine and paracrine loops is partially supported by in vitro data, but the in vivo evidence for the paracrine loop is not presented.
- The generalizability of the findings to non-clear cell RCC subtypes is not assessed and should not be implied.

## Assessment against Nature-style criteria
- **Originality** The application of a 117-algorithm ensemble to identify resistance genes is methodologically novel, and the specific focus on SP5 as a regulator of VEGFA in sunitinib resistance is a new contribution. However, the general concept of transcription factor-driven VEGFA regulation in RCC is well established, and the novelty lies primarily in the specific gene and the integrative approach.
- **Scientific importance** The topic of sunitinib resistance in RCC is clinically important, and identifying new therapeutic targets is valuable. The potential repurposing of suramin is interesting, but the evidence is preliminary. The mechanistic link between SP5 and VEGFA/AKT is plausible and could have broader implications for angiogenesis research.
- **Interdisciplinary readership** The manuscript bridges computational biology, cancer biology, and pharmacology. The machine learning framework may appeal to bioinformaticians, while the mechanistic studies will interest cancer biologists. The clinical implications could attract oncologists. However, the technical detail in the methods is currently insufficient for computational readers to fully evaluate the approach.
- **Technical soundness** The experimental design is generally sound, but several technical concerns need to be addressed, including the specificity of the SP5-VEGFA interaction, the robustness of the machine learning model, and the in vivo validation of the suramin effect. The lack of detailed statistical reporting and figure images limits the ability to fully assess technical quality.
- **Readability for nonspecialists** The manuscript is clearly written and the narrative is logical. The abstract and highlights effectively summarize the key findings. However, the methods section assumes familiarity with machine learning and bioinformatics tools, which may be challenging for a general readership. The discussion provides useful context for understanding the significance of the findings.

## Recommendation posture
Supportive if technical concerns are resolved. The core hypothesis is interesting and the experimental work is substantial, but the current evidence does not fully establish the specificity of the SP5-VEGFA interaction, the robustness of the machine learning model, or the translational potential of suramin. Addressing the major concerns with additional experiments and more detailed reporting would significantly strengthen the manuscript.