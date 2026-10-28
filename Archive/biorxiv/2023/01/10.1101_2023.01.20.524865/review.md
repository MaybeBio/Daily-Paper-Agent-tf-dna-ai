## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, funding, highlights)
- **Assessment boundary** Scientific and technical evaluation of the force field comparison and parameterization study for NPL4 MD simulations, as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors compare non-bonded force field parameters (CHARMM36m, ff99SB-ILDN, ff99SB*-ILDN) for MD simulations of zinc-bound NPL4 constructs, benchmark them against QM reference calculations, and develop a bonded model for Cu²⁺ in NPL4 based on QM-derived parameters
- **Visible evidence base** Abstract, Introduction, Methods (Sections 2.1-2.6), Results (Sections 3.1-3.4), Discussion, Data availability, Funding, Highlights
- **Missing materials affecting confidence** Figures 1-5 and Tables 1-2 are referenced but not provided; Supplementary Figures S1-S5 and Table S1 are referenced but not provided; no simulation convergence metrics, error estimates, or statistical analyses are shown in the text

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely methodological question in biomolecular simulation, namely the suitability of different force field parameter sets for studying zinc finger proteins and their potential metal exchange with copper ions. The work is motivated by a compelling biomedical context (Antabuse repurposing in cancer therapy) and the authors have made a reasonable effort to benchmark MD results against QM reference calculations. However, the manuscript as presented has several important limitations. The central conclusion that non-bonded models are inadequate for this system is not surprising and has been reported in the literature for similar zinc finger systems. The development of a bonded model for Cu²⁺ is a useful contribution, but the validation is limited to a single 500-ns simulation with no assessment of parameter transferability or robustness. The choice of QM level (B3LYP/TZVP) is reasonable but not state-of-the-art, and the lack of dispersion corrections or benchmarking against higher-level methods weakens the reference standard. The manuscript would benefit from a more systematic comparison across force fields, explicit statistical treatment of replicate variability, and a clearer articulation of what new knowledge this study provides beyond existing force field assessments.

- **Who would be interested in the results, and why** Computational biophysicists and molecular modelers working on metalloproteins, particularly those studying zinc finger proteins or metal substitution mechanisms. Researchers interested in the molecular mechanism of Antabuse's anticancer activity may also find the contextual motivation relevant. The bonded parameter set for Cu²⁺ in a zinc finger environment could be of practical use to the simulation community, though its limited validation currently restricts its broader applicability.

- **Major strengths** The study addresses a practically important problem in MD simulation of metalloproteins. The comparison across multiple force fields and constructs is a sensible approach. The use of QM calculations as a reference for coordination geometry is appropriate. The development of a bonded model for Cu²⁺ based on QM frequency calculations is a constructive step. The biomedical context provides clear motivation for the work.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "the force fields could not provide microsecond stable coordination trajectories of the Zn²⁺ ion in Npl4(Zn²⁺)129-151" and that this construct "cannot be used as a minimal model for our study."
  - **Evidence pointer** Section 3.2, Figure 2, Figure S1-S3, Table S1
  - **Concern** The conclusion that the minimal ZF1 construct is unsuitable is based on observations from a limited number of replicates (three per force field). The detachment event of C148 in one CHARMM36m replicate is presented as evidence of force field inadequacy, but the authors do not provide a statistical framework to distinguish force field artifacts from legitimate conformational sampling. The manuscript does not report whether the detachment event is reproducible across independent simulations with different initial velocities, nor does it assess whether the detachment might be influenced by the choice of starting structure, protonation states, or truncation effects at the construct boundaries. The comparison between constructs is also confounded by the different simulation lengths (1 μs for the minimal construct vs 500 ns for the larger construct).
  - **Why it matters** The central methodological conclusion of the paper rests on the reliability of the observed instability in the minimal construct. If the detachment event is a rare fluctuation rather than a systematic force field failure, the conclusion would be substantially weakened. The lack of statistical rigor in assessing replicate variability undermines confidence in the primary claim.
  - **Resolution test** The authors should provide additional replicates (at least 5-10 per condition) with explicit statistical analysis of detachment frequencies and coordination geometry distributions. They should also perform simulations starting from different initial structures (e.g., alternative PDB entries or conformations from the QM-optimized geometries) to assess whether the observed instability is robust. Reporting the fraction of simulation time in which the native coordination is maintained, with confidence intervals, would strengthen the claim.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the parameters for Zn²⁺ and coordinated cysteines and histidines used for ff99SB*-ILDN, which have been recently parametrized based on QM calculations, gave an improved performance, better preserving the tetrahedral coordination of the Zn²⁺ binding site."
  - **Evidence pointer** Section 3.3, Figure 3, Table S1
  - **Concern** The claim of improved performance for ff99SB*-ILDN is based on a single 500-ns simulation for the larger construct. The manuscript does not report replicate simulations for this condition, making it impossible to assess whether the observed preference for tetrahedral coordination is statistically significant or within the range of expected fluctuation. Additionally, the comparison between force fields is not balanced: CHARMM36m was run in triplicate for the larger construct, while ff99SB*-ILDN was run only once. The authors also do not report quantitative metrics such as root-mean-square deviations of the coordination geometry from the QM reference, or the distribution of coordination numbers over time.
  - **Why it matters** The recommendation that ff99SB*-ILDN is preferable for this system is a key practical outcome of the study. Without replicate simulations and quantitative comparison metrics, this recommendation is not adequately supported. The imbalance in sampling between force fields introduces a potential bias in the comparison.
  - **Resolution test** The authors should run at least three replicates for each force field and construct combination, and report quantitative metrics such as time-averaged coordination numbers, distributions of bond lengths and angles, and CShM scores with standard deviations across replicates. Statistical tests (e.g., bootstrapping or permutation tests) should be used to assess whether differences between force fields are significant.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the bonded model for Cu²⁺ (ff99SB*-ILDN-bonded) "preserved the coordination geometries of ZF1 and ZF2 through all the simulation" and that it "performed better than the tested non-bonded models in obtaining the correct metal-ligand bond lengths."
  - **Evidence pointer** Section 3.4, Figure 5, Table S1
  - **Concern** The bonded model is validated on the basis of a single 500-ns simulation. The manuscript does not report whether the bonded parameters were tested for stability across multiple simulations, whether the parameters are transferable to other zinc finger contexts, or whether the bonded model artificially constrains the metal site in a way that prevents realistic sampling of metal dissociation or exchange. The authors acknowledge that the bonded model "does not allow for the study of dissociation events and changes in coordination geometry after metal replacement," which substantially limits its utility for the stated biomedical motivation of understanding Cu²⁺-induced zinc displacement. The comparison with non-bonded models is also limited to a single metric (bond lengths) without assessing other important properties such as the energetics of metal binding or the dynamics of the surrounding protein environment.
  - **Why it matters** The bonded parameter set is presented as a practical tool for future studies of NPL4 with Cu²⁺. However, the limited validation and the acknowledged inability to model dissociation events mean that the parameters cannot be used for the very process (metal exchange) that motivates the study. This substantially weakens the practical contribution of the work.
  - **Resolution test** The authors should provide additional validation of the bonded model, including multiple replicate simulations, tests of parameter transferability on related zinc finger systems, and a discussion of the limitations of the bonded approach for studying metal exchange. If the bonded model cannot capture dissociation, the authors should clarify what specific scientific questions it can address and how it advances the stated goal of understanding NPL4 misfolding induced by Cu²⁺.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "the molecular details of the mechanisms of interactions of Antabuse metabolites with NPL4 and the consequent structural effects are still elusive" and imply that their force field assessment is a necessary step toward addressing this gap.
  - **Evidence pointer** Abstract, Introduction, Discussion
  - **Concern** The manuscript does not clearly articulate how the force field comparison advances the understanding of the molecular mechanism of Antabuse action. The study is framed as a preparatory step, but the connection between the force field assessment and the biomedical question is not developed. The authors do not discuss what specific mechanistic hypotheses could be tested with the recommended force field, nor do they provide a roadmap for how the simulation approach would be applied to study Cu²⁺-induced NPL4 misfolding. The choice of the yeast NPL4 system and the specific constructs is not justified in terms of relevance to the human protein targeted by Antabuse.
  - **Why it matters** For a Nature-style audience, the significance of the work must be clearly articulated. If the force field comparison is purely methodological, the novelty and impact are limited. The authors need to make a stronger case for how this work enables new biological insights into the mechanism of Antabuse action.
  - **Resolution test** The authors should add a section in the Discussion that explicitly connects the force field assessment to the biomedical context, outlining specific simulation studies that are now enabled and the mechanistic questions they would address. They should also justify the choice of yeast NPL4 and discuss the relevance to the human protein.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction, Section 1
  - **Evidence pointer** Section 1
  - **Issue** The introduction assumes significant prior knowledge of force field terminology and metal coordination chemistry. Terms such as "non-bonded parameters," "bonded model," and "CShM" are introduced without sufficient explanation for a general scientific audience.
  - **Required correction** Provide brief definitions or intuitive explanations of key technical terms when first introduced, and consider adding a short paragraph explaining why force field choice matters for metal-containing proteins in accessible language.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, Section 2.1
  - **Evidence pointer** Section 2.1
  - **Issue** The QM calculations are described as using B3LYP/TZVP, but no justification is provided for this choice of functional and basis set. The authors do not discuss whether dispersion corrections were applied or whether the results were benchmarked against higher-level methods.
  - **Required correction** Add a brief justification for the choice of QM level and discuss its limitations. If dispersion corrections were not applied, state this explicitly and discuss the potential impact on the reference geometries.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, Section 2.5
  - **Evidence pointer** Section 2.5
  - **Issue** The equilibration protocol is described in detail, but the manuscript does not report how convergence of the simulations was assessed, nor does it provide measures of statistical uncertainty for the reported observables.
  - **Required correction** Add a paragraph describing convergence assessment (e.g., block averaging, autocorrelation analysis) and report uncertainties for key quantities such as coordination distances and CShM scores.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Discussion, Section 4
  - **Evidence pointer** Section 4
  - **Issue** The discussion of the biomedical relevance of NPL4 and Antabuse is brief and does not engage with the broader cancer biology literature. The authors do not discuss how their findings might inform experimental studies or therapeutic development.
  - **Required correction** Expand the discussion to include a more detailed consideration of the biological context, including what is known about NPL4 function in cancer and how the simulation findings could guide future experimental work.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results, Section 3.1
  - **Evidence pointer** Section 3.1
  - **Issue** The description of CShM scores and their interpretation is terse. A reader unfamiliar with continuous shape measures may not understand what a CShM score of 1.2 versus 3.8 means in practical terms.
  - **Required correction** Add a brief explanation of CShM scores and their interpretation, including what values indicate good or poor agreement with a reference geometry.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Insufficient replicate sampling and lack of statistical analysis for the minimal construct simulations
  - R1-M2: Unbalanced comparison between force fields (single simulation for ff99SB*-ILDN in the larger construct)
  - R1-M3: Inadequate validation of the bonded Cu²⁺ model, including no assessment of parameter transferability or robustness
  - R1-M4: Lack of convergence assessment and uncertainty quantification for MD observables

## Risk / unsupported claims
- The claim that "the force fields could not provide any stable and reliable microsecond simulations of the Zn²⁺ ion in Npl4(Zn²⁺)129-151" is based on a limited number of replicates and lacks statistical support
- The claim of improved performance for ff99SB*-ILDN over other force fields is based on a single simulation and is not statistically substantiated
- The claim that the bonded Cu²⁺ model "performed better than the tested non-bonded models" is based on a single simulation and limited metrics
- The assertion that the minimal ZF1 construct "cannot be used as a minimal model" is not fully supported given the limited sampling and lack of investigation into alternative explanations for the observed instability
- The relevance of the yeast NPL4 system to the human protein targeted by Antabuse is asserted but not discussed in detail
- The statement that "the performance of these parameters in our model systems reflected how they had been developed using as reference the complexes of Zn²⁺-water molecules" is speculative and not directly tested in this study
- The claim that the bonded model could provide "insights into possible structural changes associated with the presence of Cu²⁺" is not demonstrated, as the model explicitly prevents dissociation events that are central to the proposed mechanism

## Assessment against Nature-style criteria
- **Originality**: Moderate. The study applies existing force field assessment methodologies to a specific system (NPL4) with biomedical relevance. The development of a bonded Cu²⁺ model is a useful contribution, but the general approach of comparing force fields for metal-binding proteins is well established. The manuscript does not introduce fundamentally new methodology or concepts.
- **Scientific importance**: Moderate. The biomedical context (Antabuse in cancer therapy) provides motivation, but the study is primarily methodological and does not directly advance understanding of the mechanism of drug action. The findings are of interest to a specialized community of computational biophysicists but may not have broad impact across disciplines.
- **Interdisciplinary readership**: Limited. The manuscript is written for a specialized audience of molecular modelers. The connection to cancer biology is mentioned but not developed in a way that would engage researchers outside the simulation community. The technical content would be challenging for nonspecialists.
- **Technical soundness**: Currently insufficient. The lack of replicate simulations, statistical analysis, and convergence assessment undermines confidence in the central claims. The validation of the bonded model is too limited to support the conclusions drawn. The QM reference level is reasonable but not benchmarked against higher-level methods.
- **Readability for nonspecialists**: Below the standard expected for a general journal. The manuscript assumes significant prior knowledge of force field terminology and metal coordination chemistry. Key concepts are introduced without adequate explanation for a broader scientific audience.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant problem and the authors have made a reasonable start, but the technical limitations described above prevent the central claims from being adequately supported. The study would need substantially more rigorous sampling, statistical analysis, and validation of the bonded model before the conclusions could be considered reliable. The authors should also strengthen the articulation of the biomedical significance and improve accessibility for a broader readership.