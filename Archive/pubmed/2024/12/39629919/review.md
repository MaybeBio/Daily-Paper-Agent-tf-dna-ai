## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, experimental section, and figure legends as provided.
- **Assessment boundary** Scientific validity, technical soundness, and support for the central claims based solely on the provided manuscript text. No external data, supplementary figures, or unpublished materials were assessed.
- **Shared manuscript claim summary** The authors propose that Smad1 promotes glioblastoma tumorigenicity and chemoresistance by sequestering the acetyltransferase p300 away from p53, thereby reducing p53 acetylation and activity. They further identify a small molecule, cpd.618, that disrupts the Smad1-p300 interaction and restores p53 acetylation, with therapeutic potential.
- **Visible evidence base** In vitro assays (cell growth, colony formation, EdU, invasion, apoptosis, IC50), in vivo xenograft models (subcutaneous and intracranial), immunoprecipitation, western blot, qRT-PCR, ChIP/qChIP, luciferase reporter assays, tissue microarray immunohistochemistry, and computational docking/virtual screening.
- **Missing materials affecting confidence** Supplementary figures (Figure S1-S14), tables (Table S1-S11), Supplemental Data files, ChIP-seq dataset details (GSE46641), and full statistical outputs were not provided. The manuscript text references these materials but they were not available for independent verification.

## Reviewer
- **Overall assessment** This manuscript addresses a clinically relevant question in glioblastoma biology, namely the regulation of p53 acetylation and its impact on chemoresistance. The proposed mechanism, involving Smad1-mediated sequestration of p300 from p53, is novel and potentially significant. However, the evidence presented in the text has several gaps that prevent full support of the conclusions. Key concerns include the lack of direct biochemical evidence for the ternary complex, incomplete genetic rescue experiments, and insufficient validation of the small molecule's specificity and in vivo efficacy. The manuscript is technically ambitious but requires substantial additional experimentation and clarification to establish the mechanistic model and therapeutic claims.
- **Who would be interested in the results, and why** Researchers in cancer biology, particularly those studying glioblastoma, p53 signaling, and epigenetic regulation. The work may also interest investigators focused on protein-protein interaction inhibitors as therapeutic strategies and those studying the role of acetyltransferases in cancer. The potential clinical implications for chemoresistance in GBM patients with p53 mutations would be of interest to translational oncology researchers.
- **Major strengths** The study addresses an important and understudied question regarding the regulation of p53 acetylation in GBM. The use of multiple complementary approaches, including patient-derived samples, in vitro assays, in vivo models, and computational docking, is commendable. The identification of a specific small molecule that disrupts the Smad1-p300 interaction is a potentially valuable contribution. The clinical correlation between Smad1 expression and patient prognosis adds translational relevance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6, R1-M7.
- **Assessment against Nature-style criteria**  
  **Originality** The proposed mechanism is novel, as the role of Smad1 in sequestering p300 from p53 has not been previously described. However, the concept of competitive binding for acetyltransferases is not entirely new, and the authors should more clearly delineate what is uniquely novel.  
  **Scientific importance** The findings have potential importance for understanding GBM biology and chemoresistance, particularly in the context of p53 mutations. However, the clinical relevance is not fully established, and the therapeutic claims require more rigorous validation.  
  **Interdisciplinary readership** The work bridges cancer biology, epigenetics, and drug discovery, which could appeal to a broad audience. However, the technical depth may limit accessibility to non-specialists.  
  **Technical soundness** The experimental design is generally sound, but several key experiments lack appropriate controls or are incomplete. The computational docking studies require experimental validation, and the in vivo efficacy data are preliminary.  
  **Readability for nonspecialists** The manuscript is clearly written but contains significant jargon and technical detail that may be challenging for a general scientific audience. The figures and figure legends, which were not fully provided, would be critical for comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and potentially important, but the current evidence does not fully establish the mechanistic model or the therapeutic potential of cpd.618. Substantial additional experimentation is required.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** The authors claim that Smad1 forms a ternary complex with p53 and p300, sequestering p300 from p53 and thereby inhibiting p53 acetylation.
- **Evidence pointer** Results section "Smad1 Binds and Inhibits p53 Acetylation via MH1 and MH2"; Figures 4I, 4J, 5D-5H
- **Concern** The text describes immunoprecipitation (IP) experiments showing Smad1-p53 and Smad1-p300 interactions, but the evidence for a ternary complex is indirect. The authors do not demonstrate that p53, Smad1, and p300 exist in a single complex simultaneously. Furthermore, the claim that Smad1 "sequesters" p300 from p53 implies a competitive mechanism that is not directly tested. The experiments showing that Smad1 overexpression reduces p53-p300 binding (Figure 5H) are suggestive but do not rule out other mechanisms, such as Smad1-induced conformational changes or post-translational modifications of p300 that reduce its affinity for p53.
- **Why it matters** The central mechanistic claim of the paper rests on the competitive sequestration model. Without direct evidence for a ternary complex and a demonstration that Smad1 binding to p300 is mutually exclusive with p53 binding, the proposed mechanism remains speculative.
- **Resolution test** Perform three-color immunoprecipitation or proximity ligation assays to demonstrate the simultaneous presence of p53, Smad1, and p300 in a complex. Use competition assays with purified proteins to show that increasing Smad1 concentration displaces p53 from p300 in a dose-dependent manner. Alternatively, use surface plasmon resonance or isothermal titration calorimetry to measure binding affinities and demonstrate competitive binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Genetic rescue and specificity
- **Claim pointer** The authors claim that Smad1's oncogenic function and inhibition of p53 acetylation are mediated through its interaction with p300, and that the K373 acetylation site is essential for this function.
- **Evidence pointer** Results section "p300-Mediated Acetylation is Vital for Smad1 Oncofunctions"; Figures 6A-6K, S5, S6
- **Concern** The manuscript does not provide a clear genetic rescue experiment. The authors show that Smad1 K373R loses its oncogenic function, but they do not demonstrate that this loss is due specifically to the inability to interact with p300 or to be acetylated. The K373R mutation could affect other aspects of Smad1 function, such as protein stability, subcellular localization, or interaction with other partners. Additionally, the authors do not test whether a Smad1 mutant that cannot bind p300 (e.g., the MH2 deletion mutant) but retains the K373 site can still promote tumorigenesis in a p53-independent manner. The specificity of the proposed mechanism is therefore not established.
- **Why it matters** The paper proposes a specific molecular mechanism, but without appropriate rescue experiments, alternative explanations for the observed phenotypes cannot be excluded. This weakens the causal link between the proposed mechanism and the functional outcomes.
- **Resolution test** Perform rescue experiments in Smad1-KO cells with wild-type Smad1, K373R, MH2-deletion, and a mutant that cannot bind p53 (MH1-deletion). Assess which mutants can restore tumorigenicity, chemoresistance, and inhibition of p53 acetylation. Additionally, test whether a p300 mutant that cannot bind Smad1 (but retains acetyltransferase activity) can rescue p53 acetylation in the presence of Smad1.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo efficacy of small molecule
- **Claim pointer** The authors claim that cpd.618 suppresses tumor growth in vivo and enhances chemosensitivity.
- **Evidence pointer** Results section "A Small Molecule Targeting Smad1-p300 Binding is an Effective GBM Suppressive Strategy"; Figures 9I-9L, S14
- **Concern** The in vivo experiments with cpd.618 are described only briefly. The text states that cpd.618 suppressed tumor growth in mice bearing tumors derived from p53-KO U87 cells re-expressing wild-type p53 or R175H. However, key details are missing, including the dosing regimen, route of administration, number of animals per group, and whether the compound was well-tolerated. The text does not report whether cpd.618 crosses the blood-brain barrier, which is critical for a brain tumor model. The mechanism of action in vivo is not confirmed, as the authors do not show that cpd.618 actually disrupts Smad1-p300 binding and increases p53 acetylation in the tumor tissue.
- **Why it matters** The therapeutic claim is a major selling point of the manuscript. Without rigorous in vivo pharmacokinetic, pharmacodynamic, and efficacy data, the translational potential of cpd.618 is not established.
- **Resolution test** Provide a detailed description of the in vivo experimental design, including animal numbers, dosing, and statistical analysis. Measure drug concentration in the brain and tumor tissue. Perform immunohistochemistry or western blot on tumor samples to demonstrate that cpd.618 treatment leads to increased p53 acetylation and decreased Smad1-p300 interaction. Include a toxicity assessment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Clinical correlation and patient data
- **Claim pointer** The authors claim that p53 acetylation is a favorable prognostic marker for GBM, regardless of p53 status, and that Smad1 is negatively associated with p53 acetylation.
- **Evidence pointer** Results section "Smad1 is Negatively Associated with p53 Acetylation in Primary GBM"; Figures 7A-7K
- **Concern** The clinical analysis is based on a tissue microarray with 60 GBM samples and 4 normal samples. The text reports correlations between Smad1 expression, p53 acetylation, and survival, but the statistical methods are not fully described. The authors do not report whether the analysis was adjusted for known prognostic factors such as age, sex, tumor grade, or MGMT promoter methylation status. The finding that p53 acetylation is a favorable prognostic marker "regardless of p53 status" is surprising and requires careful validation, as p53 mutations are common in GBM and may confound the analysis. The text does not specify how p53 status (wild-type vs. mutant) was determined in the patient samples.
- **Why it matters** The clinical correlation is used to support the translational relevance of the findings. If the statistical analysis is not robust or if confounding factors are not addressed, the clinical claims are not reliable.
- **Resolution test** Provide a detailed description of the statistical methods, including the specific tests used, adjustment for covariates, and handling of missing data. Report the method used to determine p53 mutational status. Perform a multivariate analysis including known prognostic factors. Validate the findings in an independent patient cohort.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of small molecule
- **Claim pointer** The authors claim that cpd.618 specifically disrupts the Smad1-p300 interaction without affecting p53-p300 binding.
- **Evidence pointer** Results section "A Small Molecule Targeting Smad1-p300 Binding is an Effective GBM Suppressive Strategy"; Figures 9F-9H, S12
- **Concern** The text states that cpd.618 was selected based on virtual screening for its ability to bind the Smad1-p300 interface. However, the specificity of this compound is not thoroughly demonstrated. The authors do not show that cpd.618 does not affect other protein-protein interactions involving p300 or Smad1. The text mentions that cpd.618 was chosen for its "weakest affinity for p300 at p300/p53 binding surface," but this is based on computational predictions, not experimental validation. The potential off-target effects of cpd.618 are not addressed.
- **Why it matters** A small molecule that non-specifically disrupts p300 interactions could have broad and unpredictable effects. The therapeutic claim requires evidence of specificity.
- **Resolution test** Perform pull-down or IP assays to show that cpd.618 does not disrupt p53-p300 binding at concentrations that disrupt Smad1-p300 binding. Test the effect of cpd.618 on other p300-interacting proteins. Assess the selectivity of cpd.618 against a panel of related acetyltransferases. Perform RNA-seq or proteomics to identify potential off-target effects.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic link to chemoresistance
- **Claim pointer** The authors claim that Smad1 promotes chemoresistance by inhibiting p53 acetylation and that this is dependent on p53.
- **Evidence pointer** Results section "Smad1 Upregulation Promotes GBM Tumorigenesis and Chemoresistance In Vitro and In Vivo"; Figures 2G, 3I, 3J, 8A-8E
- **Concern** The text shows that Smad1 depletion increases chemosensitivity and that this is associated with increased p53 acetylation. However, the causal link between p53 acetylation and chemoresistance is not fully established. The authors do not show that restoring p53 acetylation in Smad1-overexpressing cells (e.g., by expressing an acetylation-mimetic p53 mutant) is sufficient to reverse chemoresistance. The experiments in p53-KO cells show that Smad1's effect on chemoresistance is p53-dependent, but the specific role of acetylation is not directly tested.
- **Why it matters** The paper proposes that acetylation is the key modification linking Smad1 to chemoresistance. Without direct evidence that acetylation is the critical modification, other p53 modifications or functions could be responsible.
- **Resolution test** Express an acetylation-mimetic p53 mutant (e.g., K373Q) in Smad1-overexpressing cells and test whether this reverses chemoresistance. Conversely, express a non-acetylatable p53 mutant (K373R) in Smad1-KO cells and test whether this abolishes the chemosensitivity phenotype. Use p53 mutants that are specifically defective in acetylation but retain other functions.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** The authors make multiple quantitative claims regarding cell growth, apoptosis, tumor volume, and protein expression levels.
- **Evidence pointer** Throughout Results; Figures 2, 3, 6, 8, 9
- **Concern** The statistical methods are not described in the main text. The figure legends, which were not provided, would typically contain information on the number of independent experiments, error bars, and statistical tests used. The text mentions "p < 0.05" as a threshold but does not specify the tests used for each comparison. The authors do not report effect sizes or confidence intervals. The lack of detailed statistical reporting makes it difficult to assess the robustness of the findings.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without clear statistical reporting, the reliability of the quantitative conclusions cannot be evaluated.
- **Resolution test** Provide a detailed description of the statistical methods in the Experimental Section, including the specific tests used for each comparison, the number of biological and technical replicates, and how normality and variance were assessed. Report effect sizes and confidence intervals where appropriate. Ensure that all data points are shown in the figures or available as source data.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The abstract is dense and uses specialized terminology without sufficient context. The introduction could more clearly state the gap in knowledge that this study addresses.
- **Required correction** Revise the abstract to improve accessibility for a broader audience. In the introduction, explicitly state what is unknown about p53 acetylation regulation in GBM and how this study addresses that gap.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1, 7, 9
- **Evidence pointer** Results sections; Figures 1, 7, 9
- **Issue** The text references multiple panels in figures that were not provided. The quality and clarity of the figures cannot be assessed. Some figure panels are described only briefly in the text.
- **Required correction** Ensure that all figures are of high resolution and that all panels are clearly labeled and referenced in the text. Provide detailed figure legends that explain the experimental setup and the statistical analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Results section "Smad1 Binds and Inhibits p53 Acetylation via MH1 and MH2"
- **Evidence pointer** Figure 4K
- **Issue** The text refers to "dMH1" and "dMH2" deletion mutants, but the exact amino acid boundaries of these deletions are not specified in the text.
- **Required correction** Provide the exact amino acid residues deleted in each mutant in the Experimental Section or figure legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The data availability statement is generic and does not specify where the microarray data, ChIP-seq data, or other datasets can be accessed.
- **Required correction** Provide accession numbers for the microarray and ChIP-seq data in public repositories, and specify how other data can be obtained.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Experimental Section "Animal Experiments"
- **Evidence pointer** Experimental Section
- **Issue** The text states that mice were "randomly assigned" but does not describe the method of randomization or whether the investigators were blinded to group allocation during outcome assessment.
- **Required correction** Provide details on the randomization method and blinding procedures in the Experimental Section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion does not explicitly address the limitations of the study, such as the lack of direct evidence for the ternary complex, the potential off-target effects of cpd.618, and the limited clinical sample size.
- **Required correction** Add a paragraph discussing the limitations of the study and how they might be addressed in future work.

## Risk / unsupported claims
- The claim that Smad1 forms a ternary complex with p53 and p300 is not directly supported by the provided evidence. The IP experiments show pairwise interactions but not simultaneous binding of all three proteins.
- The claim that cpd.618 specifically disrupts the Smad1-p300 interaction without affecting p53-p300 binding is based on computational predictions and requires experimental validation.
- The claim that p53 acetylation is a favorable prognostic marker "regardless of p53 status" is not fully supported by the statistical analysis described in the text. The method for determining p53 status is not provided.
- The claim that Smad1's oncogenic function is dependent on its acetylation at K373 is not fully established, as the K373R mutation could affect other aspects of Smad1 function.
- The in vivo efficacy of cpd.618 is not fully established due to missing details on dosing, pharmacokinetics, and mechanism of action in the tumor tissue.
- The clinical correlation between Smad1 expression and patient survival is based on a small cohort (60 GBM samples) and requires validation in an independent, larger cohort.