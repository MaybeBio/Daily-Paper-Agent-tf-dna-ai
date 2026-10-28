## Review setup
- **Input scope** Full manuscript text (summary, introduction, results, discussion, methods) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose that HU protein in *E. coli* has two distinct DNA binding modes, non-specific and structure-specific, mediated by different amino acid residues (lysines K3, K18, K83 for both; proline P63 for structure-specific only), and that these modes serve separate physiological roles: structure-specific binding regulates gene expression and DNA supercoiling, while non-specific binding governs chromosome organization and dynamics
- **Visible evidence base** Text descriptions of in vitro binding assays (fluorescence polarization, EMSA), supercoiling assays, in vitro transcription assays, in vivo beta-galactosidase assays, RNA-seq differential expression analysis, and fluorescence microscopy; references to Figures 1-7, Tables 1-2, and supplementary items
- **Missing materials affecting confidence** All figures, tables, supplementary data, statistical details, RNA-seq quality metrics, microscopy quantification methods, and strain validation data are not provided; this substantially limits verification of quantitative claims

## Reviewer
- **Overall assessment** The manuscript addresses an important question in bacterial chromosome biology, namely the physiological separation of two DNA binding modes of the histone-like protein HU. The authors present a plausible hypothesis supported by a combination of biochemical and genetic approaches. However, the provided text alone does not allow full verification of the central claims due to missing quantitative data, figure content, and statistical analyses. The logic is generally coherent, but several claims appear under-supported or over-extrapolated from the described experiments. The work is potentially of interest to the bacterial physiology and gene regulation communities, but the case for distinct physiological roles would be strengthened by clearer evidence linking specific mutations to specific phenotypes without confounding effects.

- **Who would be interested in the results, and why** Researchers studying bacterial nucleoid organization, histone-like proteins, DNA supercoiling, and transcription regulation would find these results relevant. The separation of binding modes into distinct physiological functions could inform models of how architectural proteins contribute to genome function. The use of point mutations to dissect binding modes may also interest structural biologists and those studying protein-DNA interactions.

- **Major strengths** The manuscript tackles a clearly defined question with a combination of in vitro and in vivo approaches. The use of specific point mutations to separate binding modes is a logical strategy. The inclusion of multiple physiological assays (supercoiling, transcription, chromosome partitioning) provides breadth. The discussion attempts to integrate findings into a broader model of HU function.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "two DNA binding modes of HU play separate physiological roles" with structure-specific binding regulating gene expression and non-specific binding dictating chromosome structure
- **Evidence pointer** Results sections on supercoiling, gal operon, RNA-seq, and microscopy; Figures 1-6
- **Concern** The central claim of separate physiological roles relies on differential effects of P63A versus lysine mutations across assays. However, the text does not provide quantitative data (e.g., effect sizes, statistical tests, replicates) for the in vitro binding, supercoiling, transcription, or microscopy experiments. Without these, it is impossible to assess whether the observed differences between mutant classes are robust or within experimental noise. For example, the P63A mutation reduced supercoiling "significantly" but the magnitude and consistency are not reported.
- **Why it matters** The entire thesis of the paper depends on demonstrating that P63A selectively impairs structure-specific but not non-specific binding, and that this translates into distinct physiological outcomes. If the quantitative differences are small or variable, the conclusion of separate roles would not be established.
- **Resolution test** Provide full datasets with replicates, error bars, and statistical comparisons for all assays. Show that P63A does not affect non-specific binding parameters (Kd, Hill coefficient) within a defined confidence interval, and that lysine mutations do not selectively impair structure-specific binding beyond their effect on non-specific binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors state that "the DNA structure-specific binding of HU induces negative supercoils in DNA" based on the supercoiling assay
- **Evidence pointer** Supercoiling assay section; Figure 2
- **Concern** The supercoiling assay measures the ability of HU to restrain supercoils in a nicked plasmid after ligation. The text claims that P63A reduces this ability, implicating structure-specific binding. However, the assay does not directly demonstrate that structure-specific binding at distorted sites is the mechanism. Reduced supercoil restraint could also result from altered protein stability, oligomerization, or non-specific DNA affinity changes not captured by the binding assays. The authors do not rule out these alternative explanations.
- **Why it matters** The conclusion that structure-specific binding is responsible for supercoil restraint is a key pillar of the paper. If the effect is due to a general loss of DNA binding affinity or protein folding, the interpretation would be incorrect.
- **Resolution test** Include control experiments such as circular dichroism or size-exclusion chromatography to confirm mutant protein integrity, and test whether P63A affects non-specific DNA binding under the supercoiling assay conditions. Alternatively, use a DNA substrate with a defined distortion to show direct structure-specific binding in the supercoiling context.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that "structure-specific binding also regulate many other genes" based on RNA-seq comparison between HUα2 and HUα2-P63A strains
- **Evidence pointer** RNA-seq section; Figures 4-5; Tables S2-S4
- **Concern** The RNA-seq analysis identifies 261 differentially expressed genes between HUα2 and HUα2-P63A strains, with 201 overlapping with the HU-deletion strain. However, the text does not provide details on how the P63A mutation affects HU protein levels, whether the mutation causes polar effects, or whether the observed gene expression changes are direct or indirect. The authors acknowledge that P63A does not completely disrupt structure-specific binding, which complicates interpretation. Additionally, the criteria for differential expression (FDR 0.05, log2 fold change 1.5) are stated but the number of biological replicates and validation by qPCR are not mentioned.
- **Why it matters** The claim that structure-specific binding regulates many genes is central to the physiological relevance of this binding mode. Without evidence that the P63A mutation specifically affects structure-specific binding in vivo without altering protein abundance or other functions, the gene expression changes could be due to non-specific effects.
- **Resolution test** Confirm HU protein levels in all strains by Western blot. Validate a subset of differentially expressed genes by qPCR. Perform chromatin immunoprecipitation or binding assays to show that P63A reduces occupancy at known structure-specific sites but not at non-specific sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive consistency
- **Claim pointer** The authors state that "the non-specific binding also keeps HU mostly as a component of the chromosome" and that non-specific binding is responsible for chromosome organization
- **Evidence pointer** Microscopy section; Figures 6A-6B; discussion
- **Concern** The microscopy data show that lysine triple mutations reduce HU-chromosome co-localization, while P63A does not. This is interpreted as evidence for non-specific binding in chromosome association. However, the text does not provide quantitative co-localization metrics, cell counts, or statistical analysis. The claim that non-specific binding "dictates chromosome structure and organization" is broader than what the co-localization data can support, as the assay only measures spatial overlap, not organizational function.
- **Why it matters** Overstating the role of non-specific binding in chromosome organization could mislead the field. The data may only show that HU requires non-specific binding to remain associated with DNA, not that this association actively organizes the chromosome.
- **Resolution test** Provide quantitative co-localization coefficients with statistical comparisons. Include assays of chromosome morphology (e.g., size, shape, segregation) in the mutant strains to directly test organizational roles.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic specificity
- **Claim pointer** The authors propose that in structure-specific binding, "the P63 residues in the tip of each beta-arm intercalate into bases in the corresponding minor groove" and that lysine residues provide stability
- **Evidence pointer** Discussion; Figure 7
- **Concern** The proposed mechanism is based on prior crystal structures, but the current study does not provide new structural or biophysical data to support the combined role of P63 and lysines in structure-specific binding. The in vitro binding assays show that lysine mutations reduce binding to both linear and cruciform DNA, but this does not distinguish between a direct role in structure-specific recognition versus a general electrostatic contribution.
- **Why it matters** The mechanistic model is presented as a conclusion, but the evidence is indirect. If the lysine residues are simply required for any DNA binding, the model of cooperative action with P63 is speculative.
- **Resolution test** Perform binding assays with a range of DNA substrates (e.g., undamaged, kinked, cruciform) and use mutants with single lysine substitutions to map contributions. Consider surface plasmon resonance or isothermal titration calorimetry to measure binding kinetics and thermodynamics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section on RNA-seq
- **Evidence pointer** RNA-seq section; Figure 4
- **Issue** The text states "ΔhupB strain producing HUα2 homodimer showed differential expression of only two genes" but then discusses 203 up-regulated and 235 down-regulated genes for the HU-deletion strain. The transition between these comparisons is abrupt and could confuse readers.
- **Required correction** Clearly separate the comparisons: (1) HUα2 vs wild-type, (2) HU-deletion vs wild-type, (3) HUα2-P63A vs HUα2. Use subheadings or explicit sentences to guide the reader.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section on fluorescence microscopy
- **Evidence pointer** Fluorescence microscopy section
- **Issue** The methods describe image acquisition and processing but do not specify how many cells were analyzed per strain, whether the analysis was blinded, or how co-localization was quantified.
- **Required correction** Add details on sample size, blinding, and the specific co-localization metric used (e.g., Pearson coefficient, Manders overlap).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Discussion on supercoiling
- **Evidence pointer** Discussion section
- **Issue** The authors state that "in restraining DNA supercoils, HU uses structure-specific binding, presumably by binding at any constituent cruciform structures." However, the supercoiling assay uses a nicked plasmid, and the text does not explain how cruciform structures would form in this context or whether the plasmid contains such sequences.
- **Required correction** Clarify the substrate and the rationale for expecting cruciform structures, or soften the claim to acknowledge uncertainty.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Beta-galactosidase assay
- **Evidence pointer** Beta-galactosidase assay section; Figure 3B
- **Issue** The text reports "nearly 3-fold increase" and "complete or near complete de-repression" but does not provide error bars, number of replicates, or statistical tests.
- **Required correction** Include mean values with standard deviation or standard error, number of independent experiments, and p-values or confidence intervals.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Summary and Introduction
- **Evidence pointer** Summary; Introduction
- **Issue** The term "non-specific binding" is used to describe low-affinity binding to any B-DNA, but this could be confused with non-specific binding in the context of protein-DNA interactions that are purely electrostatic and non-functional. The authors should clarify that "non-specific" here means sequence-independent but still structured.
- **Required correction** Define the term explicitly at first use and consider using "sequence-independent" as an alternative.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** RNA-seq data
- **Evidence pointer** RNA-seq section
- **Issue** The authors state that RNA-seq data are deposited in GEO, but the accession number is only mentioned in the methods. This is appropriate, but the manuscript should also state whether the analysis scripts or processed data are available.
- **Required correction** Add a data availability statement in the main text or methods.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of quantitative data and statistical analysis for in vitro and in vivo assays
- R1-M2: Alternative explanations for supercoiling results not ruled out
- R1-M3: No verification of mutant protein stability or in vivo abundance
- R1-M4: Over-interpretation of microscopy co-localization data without functional assays
- R1-M5: Mechanistic model not directly tested

## Assessment against Nature-style criteria
- **Originality** The concept of separating HU binding modes into distinct physiological roles is a useful contribution, though prior work has hinted at such separation. The use of point mutations to dissect these roles is a reasonable approach, but the novelty is incremental rather than transformative.
- **Scientific importance** The question of how architectural proteins like HU contribute to genome function is important for understanding bacterial chromosome biology. If the claims are fully supported, the work would provide a clearer framework for interpreting HU function. However, the current evidence does not fully establish the case.
- **Interdisciplinary readership** The topic is primarily of interest to microbiologists and molecular biologists. The methods are standard for these fields, and the findings are unlikely to attract broad interdisciplinary attention beyond these communities.
- **Technical soundness** The experimental design is generally logical, but the lack of quantitative reporting and statistical rigor undermines confidence. The reliance on prior structural data for the mechanistic model is acceptable but should be clearly distinguished from new findings.
- **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with bacterial genetics and protein-DNA interactions. The summary is accessible, but the results and discussion sections would be challenging for nonspecialists. The flow is generally clear, though some transitions between experiments are abrupt.

## Risk / unsupported claims
- The claim that "two DNA binding modes of HU play separate physiological roles" is not fully supported without quantitative evidence that P63A and lysine mutations have distinct, non-overlapping effects across all assays.
- The statement that "the DNA structure-specific binding of HU induces negative supercoils in DNA" is an over-interpretation of the supercoiling assay, which does not directly demonstrate the mechanism.
- The claim that "non-specific binding dictates chromosome structure and organization" is broader than what the co-localization data can support.
- The mechanistic model involving P63 intercalation and lysine-mediated phosphate locks is plausible but not directly tested in this study.
- The RNA-seq results are described without validation or details on biological variability, making the list of differentially expressed genes difficult to evaluate.
- The statement that "HUα2 was as capable in controlling gene expression as the HUαβ heterodimer" is based on only two differentially expressed genes in the HUα2-only strain, which is a weak basis for this conclusion.