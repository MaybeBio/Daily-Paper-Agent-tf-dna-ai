## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2024)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No supplementary figures or tables were available for direct inspection.
- **Shared manuscript claim summary** The authors report that two human transcription factors, ERα and Sox2, exhibit multiphasic association and dissociation kinetics for both DNA and RNA binding, as measured by fluorescence polarization and surface plasmon resonance. They propose distinct kinetic models for each protein: a sequential monomer-binding model for Sox2, and a novel "feedback" model involving complex isomerization for ERα.
- **Visible evidence base** Main text figures (Figures 1–5), Table 1, Supplemental Figures 1–7 (referenced but not provided), equations (Eq. 1.1–5), and methods descriptions.
- **Missing materials affecting confidence** All supplementary figures and tables (including Supplemental Figure 1 binding curves, Supplemental Figures 3–7 kinetic fits and simulations, Supplemental Table 1 oligonucleotide sequences) were not available. Raw kinetic traces, replicate data, and statistical details beyond stated ranges were not accessible. This limits independent verification of fit quality and model discrimination.

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question: how transcription factors interact kinetically with both DNA and RNA. The observation of multiphasic binding kinetics for both ERα and Sox2 is novel and potentially significant. The authors are appropriately cautious in presenting a "framework" model rather than a fully validated mechanism. However, the manuscript has several weaknesses that need to be addressed: (1) the distinction between the proposed models and simpler alternatives is not rigorously established; (2) the "lag" phase in ERα association is a striking claim that requires more robust evidence; (3) the physiological relevance of the observed kinetics is not discussed in sufficient depth; and (4) some technical details and controls are missing. The work is of interest to the biophysics and transcription factor communities, but the current evidence does not fully establish the proposed novel mechanism.

- **Who would be interested in the results, and why** Researchers studying transcription factor dynamics, DNA-protein interactions, RNA-mediated regulation of gene expression, and biophysicists interested in kinetic modeling of macromolecular interactions. The findings could also be relevant to those investigating ERα biology in breast cancer and Sox2 in stem cell biology, as the kinetic parameters may inform understanding of target site selection and regulation by RNA.

- **Major strengths** (1) The study addresses a gap in the field by providing detailed kinetic analyses of TF-RNA interactions, which are less studied than TF-DNA interactions. (2) The use of two orthogonal biophysical methods (FP and SPR) strengthens the conclusions. (3) The authors systematically test and reject several conventional models before proposing their framework. (4) The work is clearly written and the figures are well-designed based on the descriptions. (5) The authors are appropriately cautious in their claims, acknowledging the limitations of their model.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model discrimination and alternative explanations
- **Claim pointer** The authors claim that "none of the conventional models adequately explained all the ERα nucleic acid binding data" and propose a novel "feedback" model (Figure 6c).
- **Evidence pointer** Results section "ERαDBD-Ext, but not Sox2HMG, exhibits multiphasic association to target DNA"; Discussion section "A model for ERαDBD-Ext DNA and RNA binding"; Figure 6c; Supplemental Figures 6–7 (not provided)
- **Concern** The manuscript does not provide a systematic comparison of the proposed "feedback" model against all plausible alternative models. The authors state that conventional models were considered and rejected, but the specific models tested, the criteria for rejection, and the quantitative comparison (e.g., AIC, BIC, or F-tests) are not presented in the main text. The "lag" phase is a critical observation, but its robustness across replicates and protein preparations is not documented. Furthermore, the proposed model has many free parameters (k1, k−1, k2, k−2, k3, k−3, k3b, kα, kβ), and it is unclear whether the model is identifiable from the data or whether overfitting is a concern. The simulations shown in Supplemental Figures 6–7 are described as "recapitulating general trends," which is not a rigorous standard for model validation.
- **Why it matters** The central claim of the paper is that ERα binds nucleic acids via a novel mechanism. If the model discrimination is not rigorous, the claim is not established. Overparameterized models can fit many datasets, and the "general trends" criterion is insufficient to distinguish between competing mechanisms.
- **Resolution test** Provide a systematic model comparison: (1) list all models considered (including the sequential binding model, ligand isomerization model, conformational selection model, and the proposed feedback model); (2) fit each model to the same datasets using global fitting; (3) report information criteria (AIC or BIC) or likelihood ratio tests for model comparison; (4) show residual plots for each model; (5) perform parameter identifiability analysis (e.g., profile likelihood) for the proposed model; (6) demonstrate that the "lag" phase is reproducible across at least three independent protein preparations and multiple ligand concentrations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor and data reporting
- **Claim pointer** The authors report kon, koff, and Kd values for multiple protein-nucleic acid interactions in Table 1, and state that "both proteins exhibited multiphasic nucleic acid binding kinetics."
- **Evidence pointer** Table 1; Results sections "ERαDBD-Ext and Sox2HMG equilibrium ligand binding" and "ERαDBD-Ext and Sox2HMG ligand dissociation are multiphasic"; Methods sections "FP-based Kdapp and Association Rate Determination" and "FP-based Competitive Dissociation (FPCD)"
- **Concern** The manuscript reports rate constants and equilibrium constants, but the statistical treatment is unclear. The authors state "Mean and error (50% range) are reported in Table 1," which is an unusual choice. The number of replicates (n) for each measurement is not consistently reported. For the biphasic fits, the criteria for choosing a bi-exponential over a mono-exponential fit (e.g., F-test, AIC) are not described. The "lag" phase in ERα association is described qualitatively, but no quantitative measure (e.g., lag duration, its dependence on protein concentration) is provided. Additionally, the authors note that "the ERαDBD-Ext dsDNA Kdapp is mostly influenced by the slow bi-exponential dissociation phase" and "the RNA Kdapp is mostly influenced by the fast bi-exponential dissociation phase," but the propagation of errors in these calculations is not discussed.
- **Why it matters** The quantitative values are the primary data of the paper. Without proper statistical reporting, the reader cannot assess the reliability of the conclusions. The unusual error metric (50% range) and inconsistent replicate reporting undermine confidence in the results.
- **Resolution test** Report: (1) the number of independent experiments and technical replicates for each measurement; (2) standard errors or confidence intervals using conventional metrics; (3) the statistical test used to select between mono- and bi-exponential fits; (4) a quantitative characterization of the "lag" phase (e.g., lag time as a function of protein concentration); (5) error propagation for derived quantities like Kd calculated from kon/koff.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance and interpretation
- **Claim pointer** The authors state that "our findings reveal that Sox2 and ERα bind RNA and DNA with previously unappreciated multiphasic binding kinetics, and that their reaction mechanisms differ with ERα binding nucleic acids via a novel reaction mechanism."
- **Evidence pointer** Discussion section; Concluding remarks
- **Concern** The manuscript does not adequately discuss the biological implications of the observed multiphasic kinetics. The authors note that the "lag" phase in ERα association could be relevant to "situations like ERα nucleic acid condensates," but this is only a brief speculation. The physiological relevance of the kinetic parameters (e.g., kon values that are 10^3–10^4 times slower than diffusion-limited) is not addressed. How do these kinetic features relate to ERα's function as a transcription factor in cells? Could the multiphasic behavior be an artifact of the truncated protein constructs used (ERαDBD-Ext, residues 180–280; Sox2HMG, residues 40–123)? The authors do not discuss whether full-length proteins would exhibit similar behavior.
- **Why it matters** The paper's significance depends on the claim that these kinetic features are biologically meaningful. If the observed behavior is a property of isolated domains rather than full-length proteins, or if it has no clear functional consequence, the impact of the work is substantially reduced.
- **Resolution test** Add a discussion section that: (1) addresses the potential limitations of using truncated constructs; (2) discusses how the kinetic parameters might influence target site selection, transcriptional output, or regulation by RNA in cells; (3) provides testable predictions from the model that could be evaluated in vivo or in more complex in vitro systems; (4) compares the observed kinetics with those of other transcription factors where available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation and controls
- **Claim pointer** The authors use FP and SPR to measure binding kinetics and state that "the SPR-based findings independently confirm the kinetic observations for our FP experiments."
- **Evidence pointer** Results section "ERαDBD-Ext multiphasic DNA dissociation is conserved across methodology and temperature"; Figure 5; Supplemental Figure 5 (not provided)
- **Concern** Several technical concerns are not fully addressed. (1) The authors note that "mass transfer effects could be deflating the apparent association rates to some unknown degree" in SPR experiments, but they do not quantify this effect or demonstrate that it does not affect the conclusions. (2) For FP experiments, the authors do not report whether the fluorescent label affects binding kinetics. (3) The protein concentrations used in FP experiments (up to 10 μM) are high, and the authors do not discuss potential aggregation or non-specific binding at these concentrations. (4) The authors do not report control experiments with mutant proteins or non-specific competitors to demonstrate binding specificity under the kinetic assay conditions. (5) The temperature difference between FP (4°C) and SPR (25°C) experiments is noted, but the potential impact on the kinetic parameters is not discussed.
- **Why it matters** The validity of the kinetic measurements depends on the absence of artifacts. Mass transfer, labeling effects, aggregation, and non-specific binding could all produce multiphasic kinetics that are not intrinsic to the protein-nucleic acid interaction.
- **Resolution test** (1) Quantify mass transfer effects in SPR by varying flow rate and immobilization density; (2) compare binding kinetics with labeled and unlabeled nucleic acids (e.g., using competition experiments); (3) include controls for protein aggregation (e.g., size-exclusion chromatography before and after experiments, dynamic light scattering); (4) perform competition experiments with excess unlabeled specific and non-specific competitors; (5) discuss the potential temperature dependence of the observed kinetics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Figure 1a (schematic of FPCD methodology)
- **Evidence pointer** Results section "ERαDBD-Ext and Sox2HMG ligand dissociation are multiphasic"; Figure 1a
- **Issue** The schematic in Figure 1a is described as providing "helpful clarification of the methodology," but the text does not clearly explain the two internal controls (control-1 and control-2) in the figure legend or main text. The distinction between these controls and their purpose is not immediately clear.
- **Required correction** Expand the figure legend to explicitly describe control-1 and control-2, including what each control measures and how the data are normalized.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Materials Availability section
- **Evidence pointer** "Data, Materials, and Software Availability" section
- **Issue** The authors state that the R script for simulations is available on GitHub, but the specific repository URL is not provided in the text (only mentioned as "github.com/whemphil/ER-Sox2_Manuscript" in the methods). Additionally, raw kinetic data are not deposited in a public repository.
- **Required correction** Provide the full URL in the Data Availability section and consider depositing raw kinetic traces in a public repository (e.g., Zenodo, Figshare) to facilitate independent analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction section; Discussion section
- **Issue** The manuscript cites prior work on ERα and Sox2 RNA binding, but does not discuss the broader literature on multiphasic binding kinetics in protein-nucleic acid interactions. For example, other DNA-binding proteins have been reported to exhibit complex binding kinetics, and the authors could strengthen their paper by placing their findings in this context.
- **Required correction** Add a brief paragraph in the Discussion comparing the observed multiphasic kinetics with those reported for other DNA/RNA-binding proteins, and discuss whether the proposed "feedback" mechanism could be a general phenomenon.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract; Discussion section
- **Issue** The term "multiphasic" is used throughout, but the authors do not define it explicitly. It is clear from context that it refers to multiple kinetic phases, but a formal definition would improve clarity.
- **Required correction** Define "multiphasic" at first use (e.g., "multiphasic, meaning the presence of more than one kinetically distinct phase in the association or dissociation time course").

- **Technical failings that need to be addressed before the case is established** R1-M1 (model discrimination), R1-M2 (quantitative rigor), and R1-M4 (technical validation) must be addressed. The proposed novel mechanism for ERα is not established without rigorous model comparison and demonstration that the "lag" phase is reproducible and not an artifact. The quantitative reporting needs to be brought to a standard that allows independent verification.

- **Assessment against Nature-style criteria** 
  - **Originality**: The observation of multiphasic binding kinetics for TF-RNA interactions is novel, and the proposed "feedback" model for ERα is original. However, the originality is tempered by the fact that multiphasic kinetics have been observed for other protein-nucleic acid interactions, and the authors do not fully distinguish their findings from these prior observations.
  - **Scientific importance**: The work addresses a fundamental question in gene regulation: how TFs interact with RNA and DNA. The kinetic parameters reported could be valuable for the community. However, the biological significance of the findings is not fully established, and the use of truncated protein domains limits the direct relevance to cellular function.
  - **Interdisciplinary readership**: The work is primarily of interest to biophysicists and biochemists studying protein-nucleic acid interactions. The broader cell biology and gene regulation communities may find the work interesting, but the technical nature of the manuscript may limit its accessibility.
  - **Technical soundness**: The experimental methods are appropriate and well-described, but the quantitative analysis and model discrimination are not sufficiently rigorous. The lack of statistical details and the qualitative nature of the model validation are significant weaknesses.
  - **Readability for nonspecialists**: The manuscript is clearly written, and the figures are well-designed based on the descriptions. However, the kinetic modeling sections are dense and may be challenging for nonspecialists. The authors could improve accessibility by providing a more intuitive explanation of the proposed models.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents novel observations, but the central claim of a novel ERα binding mechanism is not currently established from the provided evidence. The authors must provide rigorous model comparison, improved statistical reporting, and additional controls to support their conclusions. If these concerns are addressed, the work could be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that ERα binds nucleic acids via a "novel reaction mechanism" involving "feedback" is not established. The model is presented as a "framework" that "recapitulated the general trends," which is insufficient to support a novel mechanism claim.
- The claim that "Sox2 and ERα bind RNA and DNA with previously unappreciated multiphasic binding kinetics" is supported by the data, but the generality of this claim (i.e., whether it applies to other TFs) is not established.
- The statement that "the more stable complex state emerges first, followed by the less stable complex state" for ERα-DNA binding is based on indirect inference and requires direct evidence.
- The biological relevance of the observed kinetics is speculative and not supported by experimental evidence.
- The assertion that the "lag" phase is a genuine kinetic feature rather than an experimental artifact is not fully supported, given the acknowledged mass transfer concerns in SPR and the lack of controls for potential aggregation or labeling effects in FP.