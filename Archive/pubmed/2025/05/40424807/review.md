## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results and discussion, conclusion, acknowledgements) as provided by the user. No supplementary files, figures, or tables were accessible beyond in-text descriptions.
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and alignment with the stated claims. Editorial or formatting issues are noted only where they affect comprehension or reproducibility.
- **Shared manuscript claim summary** The authors identify five AHR and two ARNT paralogs in tiger puffer (Takifugu rubripes), characterize their phylogenetic relationships, tissue expression patterns, functional cooperation in reporter assays, TCDD sensitivity (EC50 values), ligand binding, and molecular docking. They report that truAHR1a is the most TCDD-sensitive paralog, that truAHR1 subfamily members are more sensitive than truAHR2 members (contrasting with zebrafish and medaka), and that these data improve ecological risk assessment for dioxin-like compounds.
- **Visible evidence base** In-text descriptions of results, including EC50 values, relative sensitivity calculations, fold inductions, sequence identities, and docking scores. Figure and table references are present but the actual figures/tables were not provided.
- **Missing materials affecting confidence** All figures (Figs. 1–7), tables (Tables 1–2, S1–S3), supplementary material, and raw data. Statistical details (e.g., n numbers, replicates, error bar definitions) are not fully described. The RNA-seq analysis pipeline (Kallisto) is mentioned but no quality metrics, biological replicate numbers, or differential expression statistics are given.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question in aquatic toxicology: how AHR diversity and paralog-specific sensitivity influence dioxin risk assessment. The experimental design is logical, and the inclusion of multiple complementary approaches (phylogenetics, expression analysis, reporter assays, ligand binding, docking) is commendable. However, the central claim that truAHR1a is the most sensitive paralog and that this contrasts with zebrafish and medaka rests on reporter assay data whose statistical robustness, replication, and normalization are not fully documented in the provided text. The ecological risk assessment implications are stated but not quantitatively integrated into an AOP or risk framework. The manuscript is potentially valuable but requires additional methodological detail and a more rigorous connection between in vitro sensitivity and in vivo toxicity before the conclusions are fully supported.
- **Who would be interested in the results, and why** Researchers in environmental toxicology, ecological risk assessment, and comparative genomics of fish species. Those working on AHR signaling pathways, dioxin-like compound toxicity, and species-specific sensitivity differences would find the data useful. Regulatory scientists involved in deriving species sensitivity distributions for aquatic risk assessments may also be interested, though the current manuscript does not yet provide the quantitative framework needed for direct application.
- **Major strengths** 1) Comprehensive characterization of all AHR and ARNT paralogs in a non-model, economically important fish species. 2) Integration of phylogenetic, expression, functional, and structural approaches. 3) Direct comparison with zebrafish and medaka, providing evolutionary context. 4) Identification of truAHR1a as a highly sensitive paralog, which challenges assumptions based on model species. 5) Clear articulation of the relevance to ecological risk assessment.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical documentation), R1-M2 (RNA-seq methodology), R1-M3 (risk assessment integration), R1-M4 (docking validation).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate to high. The study provides novel data on a non-model fish species and identifies a sensitivity pattern that contrasts with established model species. However, the conceptual framework (AHR diversity drives species sensitivity) is not new.  
  *Scientific importance*: Moderate. The data are useful for refining risk assessments, but the manuscript does not yet demonstrate how these findings change risk predictions or outcomes. The importance is more incremental than transformative.  
  *Interdisciplinary readership*: Moderate. The topic bridges toxicology, ecology, and genomics, but the presentation is largely specialized. The risk assessment implications are stated but not developed in a way that would engage a broader readership.  
  *Technical soundness*: The experimental approaches are appropriate, but the lack of statistical detail and incomplete methodological reporting (especially for RNA-seq and docking) prevents full assessment.  
  *Readability for nonspecialists*: The introduction and conclusion are accessible, but the results and discussion sections assume substantial background knowledge. Some sentences are overly long and could be clarified.
- **Recommendation posture** Supportive if technical concerns are resolved. The core data are potentially valuable, but the manuscript requires additional methodological detail, statistical transparency, and a more explicit link to risk assessment outcomes before the conclusions are fully established.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor and reproducibility  
- **Claim pointer** The authors report EC50 values with standard deviations (e.g., truAHR1a 0.30±0.10 nM) and state that truAHR1a shows the highest sensitivity, with relative sensitivity values calculated against a reference.  
- **Evidence pointer** Results and Discussion section, Table 2 (not provided), Figure 6 (not provided)  
- **Concern** The number of independent experiments, number of replicates per concentration, and the statistical model used for curve fitting are not described. The EC50 values are presented with standard deviations, but it is unclear whether these represent inter-experiment variability or intra-experiment technical replicates. No statistical comparison between paralogs (e.g., ANOVA with post-hoc tests) is reported, so the claim that truAHR1a is significantly more sensitive than other paralogs is not supported by inferential statistics.  
- **Why it matters** The central conclusion of the manuscript, that truAHR1a is the most sensitive paralog and that this contrasts with other species, depends entirely on the reliability and statistical significance of the EC50 differences. Without proper replication and statistical testing, the observed differences could be within experimental noise.  
- **Resolution test** Provide the number of independent biological replicates (e.g., n=3 or n=4), the number of technical replicates per concentration, and the statistical tests used to compare EC50 values between paralogs. Report confidence intervals for EC50 estimates. If differences are not statistically significant, revise the claims accordingly.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** The authors state that RNA-seq data from the NCBI SRA database were used to quantify AHR and ARNT expression across six tissues, with truAHR2a showing the highest expression.  
- **Evidence pointer** Materials and Methods, Expression of tiger puffer AHR and ARNT; Figure 4 (not provided); Table S1 (not provided)  
- **Concern** The specific SRA accessions, tissue types, number of biological replicates, sequencing depth, and data processing parameters (e.g., alignment, quantification method) are not described. The Kallisto tool is mentioned, but no details on transcriptome assembly or reference sequence sources are given. Without this information, the expression results cannot be evaluated or reproduced.  
- **Why it matters** The expression data are used to support the claim that truAHR2a is the predominant form, which is relevant to understanding which paralog may drive toxicity. If the RNA-seq analysis is not reproducible or the data are from a single pooled sample, the conclusions are weakened.  
- **Resolution test** Provide SRA accession numbers, tissue types, replicate numbers, and a detailed description of the bioinformatics pipeline. Include quality metrics (e.g., mapping rates, number of reads per sample). If the data are from public sources, specify the exact samples used and justify their selection.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Relevance to stated aim  
- **Claim pointer** The authors conclude that the data "contribute to ecological toxicity assessment of dioxin-like compounds" and suggest that the findings can be incorporated into AOP frameworks.  
- **Evidence pointer** Abstract, Introduction, Conclusion  
- **Concern** The manuscript does not provide a quantitative link between the in vitro sensitivity data and ecological risk assessment outcomes. No species sensitivity distribution, toxicity equivalence factor, or risk calculation is presented. The statement that the data can improve risk assessment is qualitative and not demonstrated.  
- **Why it matters** The stated aim of the manuscript is to enhance ecological risk assessment. Without a concrete example of how the EC50 values or relative sensitivities would alter a risk assessment (e.g., a revised species sensitivity distribution or a case study), the practical significance of the findings remains unclear.  
- **Resolution test** Add a section or example showing how the truAHR sensitivity data could be integrated into an AOP or risk assessment framework, such as calculating a relative potency factor for TCDD or comparing the truAHR EC50 values to those of other species in a quantitative manner.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Structural modeling validation  
- **Claim pointer** The authors state that molecular docking predicted similar binding affinities for TCDD across all truAHRs, with conserved residues, and that differences in sensitivity are likely due to other factors.  
- **Evidence pointer** Results and Discussion, Molecular modeling; Figure 7 (not provided); Tables S2–S3 (not provided)  
- **Concern** The docking methodology is described only briefly. No details on the template structure quality, model validation (e.g., Ramachandran plots, RMSD), docking scoring function, or conformational sampling are provided. The claim that binding affinities are "similar" is based on a narrow range of predicted values (−9.666 to −9.714 kcal/mol), but the uncertainty in these predictions is not discussed.  
- **Why it matters** The docking results are used to argue that binding affinity alone does not explain sensitivity differences, which is an important negative result. However, if the models are not validated or the docking protocol is not robust, this conclusion is not reliable.  
- **Resolution test** Provide details on template selection, model quality metrics, and docking validation (e.g., redocking of a known ligand). Discuss the limitations of the predicted affinity values and whether the differences are within the error of the method.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity and precision  
- **Affected element** Abstract, Results and Discussion  
- **Evidence pointer** Abstract, "with truAHR1a showing the highest sensitivity"  
- **Issue** The abstract states that truAHR1a shows the highest sensitivity, but the Results section also reports truAHR1b with a similar EC50 (0.32 vs 0.30 nM). The difference is minimal and may not be biologically meaningful.  
- **Required correction** Clarify whether the difference between truAHR1a and truAHR1b is statistically significant. If not, state that both paralogs are highly sensitive rather than singling out truAHR1a.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology consistency  
- **Affected element** Introduction, Results and Discussion  
- **Evidence pointer** Introduction, "aryl hydrocarbon receptor (AHR)"; Results and Discussion, "AHR repressor (AHRR)"  
- **Issue** The abbreviation AHR is used for the receptor, but the repressor is abbreviated AHRR. This is standard, but the text sometimes uses "AhR" (e.g., "AhR signaling" in the Introduction) inconsistently.  
- **Required correction** Standardize the abbreviation to AHR throughout, including in phrases like "AHR signaling."

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Results and Discussion, Tiger puffer AHR subfamily sensitivities  
- **Evidence pointer** Table 2 (not provided)  
- **Issue** The relative sensitivity values are presented as ratios, but the reference paralog used for normalization is not explicitly stated in the text.  
- **Required correction** State the reference paralog (e.g., dreAHR2-dreARNT1) and the rationale for its use in the text.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Language and readability  
- **Affected element** Throughout  
- **Evidence pointer** Multiple sections  
- **Issue** Some sentences are overly long and contain redundant phrasing, which reduces readability. For example, "The scope and diversity of this battery, which encompass functions ranging from xenobiotic metabolism to oxidative stress modulation and apoptosis regulation17, collectively underscoring the mechanistic complexity and broad biological impact of AhR signaling" is grammatically awkward.  
- **Required correction** Revise for conciseness and grammatical clarity. Break long sentences into shorter, more direct statements.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Materials and Methods, Tiger puffer RNA extraction  
- **Evidence pointer** "Tiger puffer was purchased from a fishing farm"  
- **Issue** The source of the fish is vague. No details on the number of individuals, sex, size, or developmental stage are provided.  
- **Required correction** Specify the number of fish, their size or age, and any relevant biological characteristics. If tissues were pooled, state this explicitly.

## Risk / unsupported claims
- The claim that truAHR1a is the most sensitive paralog is not statistically supported without inferential tests comparing EC50 values.
- The claim that the data "contribute to ecological toxicity assessment" is not demonstrated quantitatively; no risk assessment application is shown.
- The statement that "truARNT1 cooperates more efficiently with truAHRs than truARNT2" is based on reporter assay fold inductions, but the statistical significance of these differences is not reported.
- The expression analysis relies on public RNA-seq data, but the specific samples and processing steps are not described, making the results unverifiable.
- The docking predictions of "similar binding affinities" are presented without validation or uncertainty analysis, so the conclusion that binding affinity does not explain sensitivity differences is not fully supported.