## Review setup
- **Input scope** Full manuscript text, including summary, results, methods, and discussion sections
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical rigor as presented in the provided text
- **Shared manuscript claim summary** The authors propose that the long non-coding RNA SLNCR binds to the transcription factor E2F1 via RNA analogs of the E2F1 DNA binding site, forming a complex that promotes melanoma proliferation, invasion, and lung extravasation. They further claim that blocking this interaction without reducing SLNCR or E2F1 levels inhibits melanoma progression in a mouse model, and that molecular dynamics simulations and biochemical assays support a model where RNA binding to E2F1 is kinetically favorable while DNA binding is thermodynamically more stable.
- **Visible evidence base** RNA-seq differential expression analysis, TF binding site enrichment, Kaplan-Meier survival analysis, yeast three-hybrid screens, REMSA binding assays, DMS-MaP probing, molecular dynamics simulations, in vivo mouse extravasation experiments
- **Missing materials affecting confidence** Figures and supplementary tables referenced but not provided; raw RNA-seq data not accessible; detailed MD simulation parameters and convergence criteria not fully described; statistical details for several experiments incomplete; no information on replicate numbers for mouse experiments

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting mechanism whereby a lncRNA mimics a transcription factor DNA binding site to modulate E2F1 activity in melanoma. The central hypothesis is novel and the combination of computational and experimental approaches is ambitious. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. The claim that SLNCR phenocopies the E2F1 DNA binding site to promote melanoma progression is supported by correlative and in vitro data, but the in vivo relevance and the mechanistic details require stronger experimental validation. The manuscript would benefit from clearer presentation of key data and additional controls.
- **Who would be interested in the results, and why** Researchers studying long non-coding RNAs in cancer, transcription factor regulation, and melanoma biology would find this work relevant. The concept of a lncRNA mimicking a DNA binding site to sequester or redirect a transcription factor has broad implications for gene regulation. Clinicians interested in novel therapeutic targets for melanoma may also find the oligonucleotide-based approach of interest.
- **Major strengths** The study addresses an important and under-explored question regarding lncRNA-transcription factor interactions. The combination of transcriptomics, proteomics, biochemical binding assays, computational modeling, and in vivo experiments is comprehensive. The identification of specific RNA sequences within SLNCR that bind E2F1 and the demonstration that blocking this interaction reduces extravasation in mice are notable findings. The authors also acknowledge limitations appropriately.
- **Major Concerns** Several concerns are detailed below. The most significant relate to the strength of the in vivo evidence, the interpretation of the MD simulation data, and the lack of direct evidence that the SLNCR-E2F1 interaction occurs in patient samples or drives endogenous gene expression programs.
- **Minor Comments** Several minor issues regarding presentation, statistical reporting, and methodological clarity are listed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: High. The concept of a lncRNA phenocopying a transcription factor DNA binding site is novel and extends current understanding of lncRNA function. Scientific importance: Moderate to high. If fully validated, this work could establish a new paradigm for lncRNA-mediated regulation of transcription factors in cancer. Interdisciplinary readership: Moderate. The work bridges RNA biology, transcription factor biochemistry, and cancer biology, which could attract readers from multiple fields. Technical soundness: Moderate. The experimental approaches are generally appropriate, but several key claims lack sufficient supporting data or controls. Readability for nonspecialists: Moderate. The manuscript is generally well-written but contains sections that may be challenging for readers without expertise in MD simulations or RNA biochemistry.
- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and the work has potential, but the current evidence does not fully establish the mechanistic claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for in vivo claim
- **Claim pointer** The authors claim that "Blocking SLNCR-E2F1 complex formation without reducing the levels of either SLNCR or E2F1 prevents lung extravasation in mice."
- **Evidence pointer** Results section, mouse studies subsection; Figures 3C, 3D, S3D
- **Concern** The in vivo experiment uses a single cell line (A375-Luc2) and a single time point (7 days). The number of mice per group is not stated. Bioluminescence imaging is used as a proxy for extravasation, but no histological confirmation of lung metastases is provided. The specificity of the RNA mimic 2+3 for blocking SLNCR-E2F1 interaction in vivo is not demonstrated. Off-target effects of the oligonucleotide are not addressed.
- **Why it matters** The in vivo claim is central to the translational relevance of the work. Without adequate sample sizes, histological validation, and specificity controls, the conclusion that blocking SLNCR-E2F1 interaction prevents extravasation is not firmly established.
- **Resolution test** Provide mouse numbers per group, include histological analysis of lung tissue, demonstrate that the RNA mimic does not affect SLNCR or E2F1 levels in vivo, and include a control oligonucleotide with a scrambled sequence or a control targeting a different region of SLNCR.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of MD simulation results
- **Claim pointer** The authors state that "MD simulations predict higher affinity for DNA-E2F1 complex formation but faster kinetics and a greater number of RNA-amino acid contacts for the RNA-E2F1 complex, suggesting that RNA binding to E2F1 is more kinetically favorable."
- **Evidence pointer** Results section, molecular dynamics simulation subsection; Figures 4E, 4F, S4, S5
- **Concern** The MD simulations are based on a homology model of E2F1DBD rather than an experimentally determined structure. The force field parameters and simulation length are not described in sufficient detail. The claim that RNA binding is "more kinetically favorable" is not directly supported by kinetic measurements. The comparison between DNA and RNA binding is based on different simulation systems with potentially different sampling. The threshold of −9.8 kcal/mol for defining strong interactions is described as "empirically determined" but the basis for this threshold is unclear.
- **Why it matters** The MD simulations are used to support a mechanistic model of how RNA competes with DNA for E2F1 binding. If the simulations are not robust or the interpretation is overextended, the proposed mechanism is weakened.
- **Resolution test** Provide detailed simulation parameters, convergence analysis, and error estimates. Directly measure binding kinetics using surface plasmon resonance or similar techniques. Clarify the basis for the interaction energy threshold and show that the conclusions are robust to threshold choice.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance of SLNCR-E2F1 interaction
- **Claim pointer** The authors claim that "SLNCR binds to E2F1 to promote the proliferation, invasion, and migration of melanoma cells."
- **Evidence pointer** Results section, SLNCR and E2F1 co-regulate melanoma-relevant genes subsection; Figures 1D-1G, 3A, 3B
- **Concern** The functional experiments rely on overexpression of SLNCR and knockdown of E2F1. The authors do not show that endogenous SLNCR-E2F1 complexes exist in melanoma cells or patient samples. The specificity of the SLNCR-E2F1 interaction for the proposed mechanism is not tested. The authors do not demonstrate that the effects on proliferation and invasion are specifically due to the SLNCR-E2F1 interaction rather than independent effects of SLNCR or E2F1.
- **Why it matters** The central claim of the paper is that the SLNCR-E2F1 complex drives melanoma progression. Without evidence that this complex forms endogenously and that its formation is required for the observed phenotypes, the mechanistic link is incomplete.
- **Resolution test** Perform RNA immunoprecipitation in melanoma cell lines and patient samples to show endogenous SLNCR-E2F1 interaction. Rescue experiments where SLNCR mutants that cannot bind E2F1 are expressed in SLNCR-depleted cells would strengthen the specificity claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and data presentation
- **Claim pointer** The authors report differential expression, survival analysis, and functional assays, but statistical details are incomplete in several places.
- **Evidence pointer** Throughout Results; Figures 1A-1G, 3A-3D
- **Concern** The number of biological replicates for RNA-seq is not stated. The survival analysis uses a small cohort (n=76) and the stratification method is not fully described. For proliferation and invasion assays, the text states "error bars represent the mean ± SD of 3 independent replicates" but it is unclear if these are technical or biological replicates. The statistical tests used for each comparison are not always specified.
- **Why it matters** Reproducibility and statistical rigor are essential for the claims made. Incomplete reporting prevents assessment of the robustness of the findings.
- **Resolution test** Clearly state the number of biological replicates for each experiment, specify the statistical tests used, and provide effect sizes and confidence intervals where appropriate.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of the RNA mimic approach
- **Claim pointer** The authors use an "RNA mimic 2+3" oligonucleotide to block SLNCR-E2F1 interaction and claim this reduces invasion, proliferation, and extravasation.
- **Evidence pointer** Results section, SLNCR-E2F1 complex formation promotes melanoma invasion and proliferation subsection; Figures 3A-3D, S3A
- **Concern** The mechanism by which the RNA mimic blocks SLNCR-E2F1 interaction is not clearly explained. It is unclear whether the mimic acts as a decoy that sequesters E2F1 or if it binds to SLNCR directly. The specificity of the mimic for the intended target is not demonstrated. The authors do not show that the mimic does not affect other E2F family members or other transcription factors.
- **Why it matters** The therapeutic potential of the approach depends on the specificity of the mimic. If the mimic has off-target effects, the conclusions about the SLNCR-E2F1 interaction being required for melanoma progression are not valid.
- **Resolution test** Provide a detailed mechanism of action for the RNA mimic. Test the mimic against other E2F family members and unrelated RNA-binding proteins. Include a control mimic with a scrambled sequence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1A
- **Evidence pointer** Results section, SLNCR and E2F1 co-regulate melanoma-relevant genes subsection
- **Issue** The TF enrichment analysis identifies SMARCA4, E2F1, and FOSL2 as enriched, but the biological rationale for focusing on E2F1 over the other two factors is not clearly explained.
- **Required correction** Provide a brief justification for why E2F1 was prioritized for further study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Yeast three-hybrid screen
- **Evidence pointer** STAR Methods, Yeast three hybrid (Y3H) subsection
- **Issue** The description of the Y3H screen is incomplete. The number of clones screened, the criteria for positive hits, and the validation of hits are not described.
- **Required correction** Provide additional details on the Y3H screen methodology and hit validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Figure 4A, 4B
- **Evidence pointer** Results section, E2F1 binds RNA via its DNA binding domain subsection
- **Issue** The competition assays show that RNA competes with DNA for E2F1 binding, but the concentrations used are not directly comparable between experiments. The text states "as little as 50 nM RNA competed with 100 nM DNA" but the DNA concentration in the reverse experiment is not stated.
- **Required correction** Clarify the concentrations used in each competition experiment and ensure the comparison is fair.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section, Limitations of the study
- **Evidence pointer** Discussion section
- **Issue** The limitations section acknowledges that the full-length E2F1 context was not modeled, but does not discuss the potential impact of other E2F1 domains or post-translational modifications on RNA binding.
- **Required correction** Briefly discuss how the absence of full-length E2F1 in the MD simulations might affect the interpretation of the results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** RNA-seq data
- **Evidence pointer** STAR Methods, RNA-seq subsection
- **Issue** The GEO accession number for the RNA-seq data is not provided in the text.
- **Required correction** Include the GEO accession number in the Data and code availability section.

## Risk / unsupported claims
- The claim that "this is the first example of a TF with RNA-rather than DNA-dependent oncogenic activity" is a strong statement that is not fully supported by the data presented. The authors show that SLNCR-E2F1 complex formation is required for some phenotypes, but they do not demonstrate that E2F1's oncogenic activity is exclusively RNA-dependent.
- The statement that "RNA binding to E2F1 is more kinetically favorable" is not directly measured and is inferred from MD simulations. This claim requires experimental validation.
- The extrapolation of the in vitro and mouse model findings to human melanoma patients is not fully justified. The survival analysis is based on a small cohort and the correlation between SLNCR and E2F1 expression and patient outcomes is not mechanistically linked to the proposed interaction.
- The claim that the RNA mimic 2+3 "blocks the SLNCR-E2F1 interaction" is not directly demonstrated in vivo. The authors show reduced extravasation, but the mechanism of action of the mimic in vivo is not established.