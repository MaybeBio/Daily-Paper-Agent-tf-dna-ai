## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and clinical relevance as presented in the text; no assessment of figures, tables, or supplementary data that were not provided
- **Shared manuscript claim summary** The manuscript reports that TP53 R181H and R181C variants, commonly identified in germline genetic testing, confer an attenuated cancer risk phenotype compared to dominant negative/loss of function variants. Despite markedly reduced DNA binding cooperativity and transcriptional activity, these mutants retain mitochondrial-associated apoptosis, which the authors propose explains the reduced penetrance phenotype.
- **Visible evidence base** Text descriptions of patient cohort analyses, fluorescence polarization assays, differential scanning fluorimetry, crosslinking experiments, RNA-seq, ChIP-seq, flow cytometry, proximity ligation assays, and mouse xenograft experiments
- **Missing materials affecting confidence** All figures, tables, supplementary materials, statistical outputs, and raw data; specific numerical values for binding affinities, Hill slopes, p-values, and effect sizes; details on ChIP-seq peak calling and quality metrics; details on RNA-seq differential expression thresholds and gene lists

## Reviewer
- **Overall assessment** This manuscript addresses an important clinical and mechanistic question regarding TP53 R181 variants, which are frequently encountered in germline genetic testing yet remain classified as variants of uncertain significance or with conflicting interpretations. The authors present a compelling hypothesis that retention of transcription-independent apoptosis explains the attenuated phenotype. However, the evidence as described in the text is incomplete in several critical areas. The clinical cohort analysis lacks key statistical details and comparator information. The biochemical assays, while appropriate in design, are described without quantitative results, making it impossible to assess the magnitude of the reported defects. The claim of "essentially abolished" DNA binding in ChIP-seq is not supported by any presented data. The mechanistic link between retained mitochondrial apoptosis and the clinical phenotype is inferred rather than directly demonstrated. The manuscript has potential but requires substantial additional data and analysis to establish the central claims.
- **Who would be interested in the results, and why** Cancer geneticists and genetic counselors would be interested in the clinical classification of TP53 R181 variants and the implications for patient management. p53 biologists would be interested in the separation of transcriptional and non-transcriptional tumor suppressor functions. Clinicians managing Li-Fraumeni syndrome families would benefit from refined risk stratification. The work also has relevance for variant classification efforts in clinical genomics.
- **Major strengths** The study addresses a clinically important and unresolved question about a common TP53 variant. The combination of clinical cohort data with mechanistic cell biology is commendable. The use of endogenous gene editing rather than overexpression systems is a methodological strength. The focus on transcription-independent p53 functions is timely and underappreciated in the field.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6
- **Assessment against Nature-style criteria** Originality: The concept of transcription-independent p53 function explaining reduced penetrance is not entirely novel, but the specific focus on R181 variants and the combination of clinical and mechanistic data provides a fresh perspective. Scientific importance: The work has clear clinical relevance for variant classification and patient counseling, which is significant. However, the mechanistic depth is currently insufficient to fully establish the proposed model. Interdisciplinary readership: The topic bridges clinical genetics and basic p53 biology, which could attract a broad audience if the evidence is strengthened. Technical soundness: The experimental approaches are generally appropriate, but the lack of quantitative data and statistical rigor in the presented text undermines confidence. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with p53 biology and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and clinically relevant, but the current evidence base is insufficient to establish the claims as presented.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Clinical data interpretation
- **Claim pointer** The authors claim that R181 variants confer an attenuated cancer risk phenotype compared to dominant negative/loss of function variants, based on analysis of 415 LFS families.
- **Evidence pointer** Results section, Figure 1, Tables S1-S3, location not provided
- **Concern** The clinical cohort analysis is described only in qualitative terms. No hazard ratios, cumulative incidence curves, or formal statistical comparisons between R181 variant carriers and DN/LOF carriers are presented in the text. The comparison of cancer types and age of onset lacks effect sizes and confidence intervals. The authors state that R181 carriers have "significantly older" age of onset but do not provide the statistical test results or the magnitude of the difference. Additionally, the classification of variants into "hypomorphic" versus "DN/LOF" categories relies on prior functional data, but the criteria for this classification are not described in the methods.
- **Why it matters** The clinical phenotype is the foundation of the manuscript's central claim. Without rigorous statistical analysis and transparent methodology, the conclusion that R181 variants cause attenuated cancer risk is not established. This is particularly important because the authors are proposing changes to how these variants are classified and managed clinically.
- **Resolution test** Provide quantitative comparisons with appropriate statistical tests, including hazard ratios or cumulative incidence curves for cancer risk, age of onset distributions with confidence intervals, and a clear description of how variants were categorized. Include the number of carriers at risk and follow-up time for each group.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biochemical data quantification
- **Claim pointer** The authors claim that R181H and R181C have "significantly reduced" cooperative DNA binding compared to wild-type p53, based on fluorescence polarization assays.
- **Evidence pointer** Results section, Figure 2D-H, location not provided
- **Concern** The fluorescence polarization data are described only in terms of qualitative observations ("mildly reduced" for R181H, "more significantly reduced" for R181C). No apparent Kd values, Hill coefficients, or statistical comparisons are provided in the text. The claim of reduced cooperativity is central to the mechanistic model, yet the quantitative extent of the defect is not reported. Furthermore, the authors do not describe how many independent experiments were performed or how the data were fit.
- **Why it matters** The biochemical characterization is the direct evidence for the proposed mechanism of reduced DNA binding cooperativity. Without quantitative data, the reader cannot assess whether the reduction is biologically meaningful or within the range of experimental noise. The distinction between "mildly" and "more significantly" reduced is subjective without numerical support.
- **Resolution test** Provide apparent Kd values, Hill slopes, and their standard errors for each construct, with the number of independent replicates. Include a statistical comparison (e.g., one-way ANOVA with post-hoc tests) between wild-type and mutant constructs. If cooperativity is specifically claimed, provide a quantitative measure of cooperativity (e.g., Hill coefficient) and its confidence interval.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Transcriptional activity assessment
- **Claim pointer** The authors claim that R181H and R181C have "markedly impaired" transactivation of p53 target genes, based on RNA-seq and qPCR data.
- **Evidence pointer** Results section, Figures 3A-F, S4, Tables S4-S11, location not provided
- **Concern** The RNA-seq analysis is described without key details. The authors state that "a number of p53 target genes were significantly down-regulated" but do not provide the total number of differentially expressed genes, the overlap between R181H and R181C, or the magnitude of the expression changes. The claim that the "vast majority" of p53 target genes are impaired is not quantified. The qPCR validation is mentioned but no data are shown in the text. The IPA analysis is described but the specific pathways and z-scores are not presented. The comparison between R181 mutants and null cells is not clearly described.
- **Why it matters** The transcriptional defect is a key part of the proposed mechanism. Without quantitative data on the extent of the defect, the reader cannot determine whether R181 mutants are truly "similar to null" as claimed, or whether they retain partial activity. This distinction is critical for understanding the phenotype.
- **Resolution test** Provide the number of p53 target genes significantly induced in wild-type cells, the proportion of these that are impaired in R181 mutants, and the average fold-change reduction. Include volcano plots or heatmaps as supplementary data. Provide the specific IPA pathway z-scores and the list of significant upstream regulators. Clarify the statistical thresholds used for differential expression analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** ChIP-seq interpretation
- **Claim pointer** The authors claim that p53 binding to chromatin is "essentially abolished" in R181H and R181C cells.
- **Evidence pointer** Results section, Figure 5A-C, S5, location not provided
- **Concern** The ChIP-seq data are described without any quantitative metrics. The claim of "essentially abolished" binding is a strong statement that requires supporting data, such as the number of peaks called in each genotype, the overlap between genotypes, and the read density at known p53 target loci. The authors do not describe how peak calling was performed, what thresholds were used, or how the data were normalized. The comparison between wild-type and mutant cells is not quantified.
- **Why it matters** This is the most direct evidence for the loss of DNA binding in a cellular context. The claim of "essentially abolished" is central to the argument that R181 mutants are transcriptionally dead. Without quantitative ChIP-seq data, this claim is unsupported.
- **Resolution test** Provide the number of significant peaks in wild-type, R181H, and R181C cells, with the statistical threshold used. Show read density profiles at representative p53 target loci. Provide a quantitative comparison of peak intensity between genotypes. If binding is truly abolished, show that the number of peaks in mutant cells is not significantly different from input or IgG controls.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic link to apoptosis
- **Claim pointer** The authors claim that R181 mutants retain transcription-independent apoptosis through mitochondrial BAK interaction, and that this explains the attenuated phenotype.
- **Evidence pointer** Results section, Figure 6B-F, S7, location not provided
- **Concern** The apoptosis data are described qualitatively. The Annexin V assay shows "comparable apoptosis levels" but no quantitative data or statistical analysis are provided. The proximity ligation assay demonstrates BAK interaction but the quantification is not described. The cytochrome c release data are mentioned but not quantified. Most importantly, the causal link between retained mitochondrial apoptosis and the clinical phenotype is not directly tested. The authors do not show that blocking mitochondrial apoptosis in R181 mutant cells abolishes the attenuated phenotype, nor do they compare the apoptotic response to other hypomorphic variants.
- **Why it matters** The central claim of the manuscript is that retained transcription-independent apoptosis explains the reduced penetrance. This requires direct evidence that the apoptotic function is both present and functionally significant in the context of the mutant cells. Correlation between retained apoptosis and attenuated phenotype is suggestive but not conclusive.
- **Resolution test** Provide quantitative apoptosis data with statistical comparisons. Show that the mitochondrial apoptosis pathway is specifically required for the observed cell death (e.g., using BAK inhibitors or BAK knockout). If possible, compare the apoptotic response of R181 mutants to other hypomorphic variants with known phenotypes to establish a correlation.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** Yes
- **Axis** Mouse xenograft data
- **Claim pointer** The authors claim that R181H and R181C HCT116 cells show "similar tumor growth rates and final tumor weights" compared to wild-type cells in mouse xenografts.
- **Evidence pointer** Results section, Figure S6A-B, location not provided
- **Concern** The xenograft experiment is described in a single sentence with no quantitative data. No tumor growth curves, final tumor weights, or statistical analysis are presented. The number of mice per group is stated as six, but no variability measures are provided. The relevance of this experiment to the clinical phenotype is unclear, as HCT116 cells are a cancer cell line and the xenograft model does not recapitulate the germline predisposition context.
- **Why it matters** The xenograft data are presented as supporting evidence for retained tumor suppressor function, but without quantitative data, the claim is unverifiable. Moreover, the experimental design may not be appropriate for testing the specific hypothesis about germline predisposition.
- **Resolution test** Provide tumor growth curves with error bars, final tumor weights with statistical comparison, and the number of independent experiments. Clarify the rationale for using this model and discuss its limitations in the context of germline predisposition.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Clinical cohort analysis
- **Evidence pointer** Results section, Figure 1, location not provided
- **Issue** The authors state that R181 carriers have "significantly older" age of onset but do not report the statistical test used or the p-value in the text.
- **Required correction** Report the specific statistical test, the p-value, and the median ages with interquartile ranges for each group.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** RNA-seq and ChIP-seq data
- **Evidence pointer** Data Availability Statement
- **Issue** The authors state that sequencing data are deposited in GEO under GSE303326, but the specific accession for ChIP-seq data is not mentioned separately.
- **Required correction** Clarify whether the GEO accession includes both RNA-seq and ChIP-seq data, or provide a separate accession for ChIP-seq.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** CRISPR cell line generation
- **Evidence pointer** Methods section, Antibodies, cell lines, drugs, software
- **Issue** The methods state that CRISPR cell lines were generated but do not describe the guide RNA sequences, the targeting strategy, or how homozygous mutant clones were verified.
- **Required correction** Provide details on the CRISPR guide sequences, the donor templates if used, and the verification method (e.g., Sanger sequencing, Western blot) for each cell line.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of patient data
- **Affected element** Discussion of R181C founder mutation
- **Evidence pointer** Discussion section
- **Issue** The authors mention that R181C appears to be a Palestinian founder mutation but do not provide a reference or discuss the implications of this for the observed phenotype.
- **Required correction** Add a reference for the founder mutation claim and discuss how this might affect the interpretation of cancer risk in R181C carriers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Results section
- **Evidence pointer** Results section, Figures 1-6, S1-S7
- **Issue** The text refers to many supplementary figures and tables, but the main text does not summarize the key findings from these supplementary items.
- **Required correction** Add brief summaries of the key supplementary findings in the main text to help readers understand their relevance.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "hypomorphic" is used to describe the clinical phenotype, but this term is typically used for alleles with reduced but not absent function. The authors should clarify whether they are using this term to describe the clinical phenotype or the molecular function.
- **Required correction** Define the term "hypomorphic" as used in this context and clarify whether it refers to the clinical phenotype, the molecular function, or both.

## Risk / unsupported claims
- The claim that R181 variants are the "most common" germline TP53 variants identified in the cohort is not supported by the text, as no comparison to other variant frequencies is provided.
- The claim that R181 variants "lack dominant negative activity" based on patient-derived LCL data is not supported, as the data are only described qualitatively and the experimental design is not fully described.
- The claim that "retention of transcription-independent p53 tumor suppressor function results in a reduced penetrance cancer risk syndrome" is an inference from correlative data and is not directly tested.
- The claim that ChIP-seq shows "essentially abolished" binding is unsupported without quantitative peak calling data.
- The claim that R181 mutants retain "wild-type p53 structure" is based on AlphaFold models and thermal stability measurements, but the text does not provide the AlphaFold confidence scores or the Tm values with statistical comparison.
- The clinical relevance of the xenograft experiment is unclear, and the claim of "similar tumor growth rates" is unsupported without quantitative data.