## Review setup
- **Input scope** Full manuscript text including abstract, background, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, analytical validity, and interpretation of results as presented in the manuscript
- **Shared manuscript claim summary** The authors construct mammalian evolutionary profiles of human endogenous G-quadruplexes (eG4s), identify highly conserved eG4s under mammalian constraint, develop a large language model-based prediction tool (eG4finder), and demonstrate that highly conserved eG4s exhibit enhanced regulatory potential, stronger transcriptional activation, and closer associations with complex human traits
- **Visible evidence base** Main text figures 1-8, supplementary figures S1-S25, supplementary tables S1-S4, methods section, and references cited within the text
- **Missing materials affecting confidence** Raw sequencing data files, complete bioinformatics pipeline scripts, model training hyperparameters, full GWAS SNP enrichment statistics, and detailed cell line metadata were not available for independent verification

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in understanding the evolutionary conservation and functional significance of endogenous G-quadruplexes in mammalian genomes. The integration of a comprehensive eG4 reference set with mammalian comparative genomics is a valuable contribution. The development of eG4finder as a sequence-based prediction tool is methodologically interesting, though the biological conclusions regarding trait associations require careful scrutiny given the analytical approach. The manuscript is generally well-written and the figures are informative, but several technical concerns need to be addressed to fully establish the claims.
- **Who would be interested in the results, and why** Researchers studying non-B DNA structures, regulatory genomics, comparative genomics, and the functional interpretation of GWAS variants would find this work relevant. The eG4finder tool and the evolutionary classification of eG4s will be of practical use to the G-quadruplex community. The connection between conserved eG4s and complex traits may interest human geneticists seeking mechanistic explanations for trait-associated variants.
- **Major strengths** The study leverages a comprehensive eG4 annotation integrating multiple cell lines and experimental approaches. The use of the Zoonomia 241-mammal alignment for evolutionary analysis is appropriate and powerful. The development of eG4finder addresses a real need for sequence-based eG4 prediction. The multi-layered functional characterization (chromatin state, histone modifications, TF binding, expression, and trait associations) provides a thorough phenotypic portrait of conserved eG4s.
- **Major Concerns** Several concerns are detailed below, primarily relating to the definition and interpretation of conservation categories, the validation of eG4finder, the statistical rigor of enrichment analyses, and the causal interpretation of trait associations.
- **Minor Comments** Several minor issues regarding presentation, statistical reporting, and methodological clarity are listed below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (conservation category definitions), R1-M2 (eG4finder validation), R1-M4 (GWAS enrichment analysis), R1-M5 (causal interpretation)
- **Assessment against Nature-style criteria** Originality: The work is original in its comprehensive evolutionary analysis of eG4s and the development of a new prediction tool. Scientific importance: The findings have broad implications for understanding regulatory element evolution and the functional interpretation of non-coding variants. Interdisciplinary readership: The work bridges structural biology, genomics, and human genetics, making it of interest across these fields. Technical soundness: The computational analyses are largely appropriate, but several methodological concerns (detailed below) need to be resolved. Readability for nonspecialists: The manuscript is generally accessible, though some sections assume familiarity with G-quadruplex biology and comparative genomics methods.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the current evidence does not fully establish the central claims regarding the functional primacy of highly conserved eG4s and their causal role in complex traits.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Statistical rigor
- **Claim pointer** The manuscript claims that three categories of eG4s with distinct evolutionary conservation patterns (highly conserved, actively evolving, primate-specific) reliably summarize the evolutionary landscape of human eG4s.
- **Evidence pointer** Figure 1B-H, Methods section "Measurement of evolutionary conservation of human eG4s"
- **Concern** The definition of the three conservation categories relies on arbitrary thresholds of N1 (number of species with base alignment rate ≥ 90%) and N2 (number of species with base alignment rate ≤ 10%). The specific cutoffs used to assign eG4s to C1, C2, and C3 are not clearly stated in the main text or methods. Without explicit threshold definitions, the classification is not reproducible, and the biological interpretation of these categories as "highly conserved," "actively evolving," and "primate-specific" may be an oversimplification of a continuous spectrum of conservation.
- **Why it matters** The entire downstream analysis, including functional enrichment, regulatory potential, and trait associations, depends on the validity of these categories. If the thresholds are arbitrary or the categories do not reflect meaningful biological distinctions, all subsequent conclusions are compromised.
- **Resolution test** The authors should explicitly state the N1 and N2 thresholds used for each category, provide a sensitivity analysis demonstrating that the main conclusions are robust to reasonable variations in these thresholds, and justify the biological rationale for the chosen cutoffs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Validation
- **Claim pointer** The manuscript claims that eG4finder is an effective and general tool for predicting eG4 formation from DNA sequence alone, with superior performance compared to existing tools.
- **Evidence pointer** Figure 3B-H, Methods section "Model architecture and performance analyses of eG4finder"
- **Concern** The evaluation of eG4finder relies heavily on the assumption that the training data from human cell lines are representative and that the binary classification threshold (recurrence < 1 vs. ≥ 1) is appropriate. The comparison with other tools (Quadron, G4detector, PENGUINN, DeepG4) is presented as percentage improvements in AUROC, AUPRC, and accuracy, but the absolute performance metrics and the statistical significance of these differences are not reported. Furthermore, the cross-species validation in mouse, pig, and chicken is complicated by the limited number of cell lines and the acknowledged issue of incomplete eG4 saturation, which the authors attempt to address but do not fully resolve.
- **Why it matters** eG4finder is a central tool used to verify structural conservation across species. If its performance is not rigorously validated, the structural conservation claims are weakened. Additionally, the tool is presented as a general resource, so its reliability must be established.
- **Resolution test** The authors should report absolute performance metrics with confidence intervals for all tools compared, perform statistical tests for differences in performance, and provide a more robust cross-species validation strategy that accounts for the saturation issue, possibly by using a gold-standard set of experimentally validated eG4s in non-human species.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation / Confounding
- **Claim pointer** The manuscript claims that highly conserved eG4s exhibit higher regulatory potential, regulatory activity, and affinity for transcription factors compared to other eG4 categories.
- **Evidence pointer** Figures 5-6, Methods section "Epigenome and transcription factor analyses"
- **Concern** The comparison of regulatory features across eG4 categories may be confounded by genomic location. Highly conserved eG4s are enriched in promoters, while primate-specific eG4s are more common in intergenic and intronic regions. Promoters inherently have higher accessibility, active histone marks, and TF binding. The authors attempt to address this by showing similar patterns in non-promoter regions, but the analysis may still be confounded by other genomic features such as CpG content, sequence composition, or proximity to other regulatory elements.
- **Why it matters** The claim that conservation status directly determines regulatory potential is central to the paper's thesis. If the observed differences are primarily driven by genomic context rather than conservation per se, the interpretation changes substantially.
- **Resolution test** The authors should perform a matched analysis that controls for genomic location, GC content, and other relevant covariates, or use a regression framework that includes these variables to isolate the independent effect of conservation category on regulatory features.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor / Methodology
- **Claim pointer** The manuscript claims that trait-associated variants and variants affecting the expression of high phenotypic severity genes are most enriched in highly conserved eG4s.
- **Evidence pointer** Figure 8A-E, Methods section "Trait-associated variant analyses"
- **Concern** The enrichment analysis for GWAS variants uses a randomization approach with GC-content matching, which is appropriate. However, the analysis does not appear to account for linkage disequilibrium (LD) structure, which can lead to inflated enrichment signals. Additionally, the comparison between eG4 categories and non-eG4s may be confounded by the fact that highly conserved eG4s are in more constrained genomic regions, which are generally depleted of common variants. The use of fine-mapped eQTLs is a strength, but the analysis of phenotypic severity genes relies on a categorical classification that may not capture the full spectrum of gene importance.
- **Why it matters** The association with complex traits is a key claim of the paper and likely to attract broad attention. If the enrichment is not robust to LD structure or other confounders, the conclusion may be overstated.
- **Resolution test** The authors should perform LD-based enrichment analyses (e.g., using stratified LD score regression or a permutation approach that preserves LD structure) and demonstrate that the enrichment of GWAS variants in highly conserved eG4s is independent of background selection and other genomic features.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation / Causality
- **Claim pointer** The manuscript claims that highly conserved eG4s are associated with complex human traits, implying a functional role in trait variation.
- **Evidence pointer** Figure 8, Discussion section
- **Concern** The analysis demonstrates statistical enrichment of trait-associated variants in highly conserved eG4s, but this does not establish a causal or functional role. The example of rs402072 in PRKD2 is suggestive but anecdotal. The manuscript does not provide functional validation (e.g., reporter assays, CRISPR perturbation) to demonstrate that disruption of eG4 structures in these regions affects gene expression or phenotype.
- **Why it matters** The claim of association with complex traits is used to argue for the biological importance of conserved eG4s. Without functional evidence, the clinical or biological significance remains correlational.
- **Resolution test** The authors should either temper the causal language in the discussion or provide additional functional evidence, such as demonstrating that variants in highly conserved eG4s affect eG4 stability or gene expression in relevant cellular contexts.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Presentation
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B
- **Issue** The heat-scatter plot in Figure 1B is visually complex and the three categories are not clearly delineated in the figure itself. The reader must rely on the text to understand the boundaries between categories.
- **Required correction** Consider adding explicit boundary lines or shading to the figure to visually separate the three categories, or provide a simpler schematic representation of the classification scheme.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3C-E
- **Evidence pointer** Figure 3C-E
- **Issue** The comparison of eG4finder with other tools reports percentage improvements but does not provide absolute values or confidence intervals for the metrics shown.
- **Required correction** Include a supplementary table with absolute values and confidence intervals for all performance metrics for all tools compared.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology / Reproducibility
- **Affected element** eG4finder model
- **Evidence pointer** Methods section "Model architecture and performance analyses of eG4finder"
- **Issue** The hyperparameters used for training eG4finder (learning rate, batch size, number of epochs, etc.) are not reported.
- **Required correction** Provide full training details in the methods or supplementary materials to ensure reproducibility.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation / Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of eG4 conservation could benefit from more explicit comparison with previous studies on G4 conservation, particularly those that have examined evolutionary patterns in more limited phylogenetic contexts.
- **Required correction** Add a brief paragraph situating the current findings within the broader literature on G4 evolution and conservation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Background section
- **Issue** The term "mammalian conservation" is used in the title and throughout, but the analysis is based on alignment to 240 non-human mammalian genomes. The term could be interpreted as implying direct experimental validation of eG4 structures in multiple mammals, which is not the case.
- **Required correction** Consider clarifying in the abstract or introduction that "conservation" refers to sequence-level conservation of eG4-forming regions, not direct structural validation across species.

## Risk / unsupported claims
- The claim that highly conserved eG4s are "the most powerful transcriptional activation elements in the total eG4 collection" is based on indirect epigenomic and expression correlations, not direct functional assays, and may be overstated.
- The assertion that eG4finder verifies "high structural conservation" of conserved eG4s across species is based on predicted structures, not experimentally validated structures in non-human species.
- The causal implication that variants in highly conserved eG4s "drive" complex human diseases is not supported by the correlational enrichment analysis presented.
- The claim that the human eG4 reference set is "saturated" is based on the observation that new cell lines add few novel eG4s, but this does not rule out the possibility that other cell types or conditions could reveal additional eG4s.