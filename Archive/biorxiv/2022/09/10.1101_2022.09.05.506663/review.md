## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no external validation or replication attempted
- **Shared manuscript claim summary** The authors propose that an alpha-helical lid within the RuvC domain of CRISPR-Cas12a anchors the crRNA:target strand (TS) hybrid and guides the TS toward the RuvC catalytic core, with REC2 and Nuc domains facilitating this traversal, based on long-timescale molecular dynamics, free-energy simulations, and in vitro cleavage assays
- **Visible evidence base** Simulation descriptions (MD, US), structural models (PDB 6GTG, 5NFV), free-energy profiles (Figure 4a), experimental cleavage data (Figure 4b), supplementary figures referenced but not provided in full
- **Missing materials affecting confidence** Full figures and supplementary information (Supplementary Figs. 1-12, Tables 1-2) not included; convergence criteria for US simulations not fully detailed; experimental replicates and statistical analysis for cleavage assays not described; force field validation for this specific system not discussed

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely question in CRISPR biology, namely how the target DNA strand reaches the RuvC active site in Cas12a. The combination of long-timescale MD, free-energy calculations, and experimental validation is commendable and appropriate for the problem. However, several technical aspects require clarification and strengthening before the mechanistic claims can be fully accepted. The central role of the alpha-helical lid is plausible and supported by the presented data, but the quantitative robustness of the free-energy results and the generalizability of the proposed mechanism need further scrutiny.
- **Who would be interested in the results, and why** Researchers in CRISPR biology, genome editing, and RNA-guided nucleases would find these results valuable. The proposed mechanism has implications for engineering Cas12a variants with altered specificity or activity. Computational biophysicists studying protein-DNA interactions and conformational dynamics would also be interested in the methodological approach and the long-timescale simulations.
- **Major strengths** The study uses state-of-the-art long-timescale MD simulations on Anton2, which is appropriate for capturing slow conformational changes. The combination of computational predictions with experimental validation through mutagenesis and cleavage assays strengthens the conclusions. The proposed mechanism integrates multiple domains (lid, REC2, Nuc) into a coherent model, providing a testable framework for future studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (free-energy convergence and sampling), R1-M2 (experimental validation robustness), R1-M3 (generality of the model)
- **Assessment against Nature-style criteria**  
  *Originality*: High. The question of TS traversal in Cas12a is unresolved, and the proposed lid-mediated mechanism is novel.  
  *Scientific importance*: High. Understanding this mechanism could inform engineering of Cas12a for improved genome editing and diagnostic applications.  
  *Interdisciplinary readership*: Moderate to high. The topic bridges structural biology, computational biophysics, and biochemistry, but the technical depth may limit accessibility to a broad audience.  
  *Technical soundness*: Moderate. The simulation approach is appropriate, but concerns about free-energy convergence and experimental reproducibility need to be addressed.  
  *Readability for nonspecialists*: Moderate. The abstract and introduction are accessible, but the results section assumes familiarity with MD and free-energy methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding free-energy convergence, experimental validation, and generalizability.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The free-energy profiles (Figure 4a) show a barrierless traversal for the wild-type system and a ~5 kcal/mol barrier for the mutant, supporting the lid's role in guiding the TS.
- **Evidence pointer** Results section "Traversal of the DNA TS and accommodation in the RuvC catalytic pocket"; Methods "Umbrella Sampling simulations"; Figure 4a
- **Concern** The convergence of the 2D US simulations is not sufficiently demonstrated. The manuscript states that 3,332 windows were simulated for ~50 μs total, but details on how convergence was assessed (e.g., overlap of histograms, evolution of PMF with simulation time) are not provided. The bootstrap error analysis is mentioned but the magnitude of errors on the PMF is not reported. Without this information, the quantitative reliability of the free-energy barriers (or lack thereof) cannot be evaluated.
- **Why it matters** The central mechanistic claim relies on the difference in free-energy profiles between wild-type and mutant systems. If the profiles are not converged, the conclusion that the lid facilitates traversal could be an artifact of insufficient sampling.
- **Resolution test** Provide convergence metrics, such as PMF values as a function of simulation time, histogram overlap for adjacent windows, and error bars on the PMF. If possible, show that the barrier difference between wild-type and mutant is statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We observed substantial reduction in TS cleavage activities with combined alanine substitutions the positively charged residues (K1013A, R1014A, R1016A, K1018A) in the lid" and "single point mutation of F1002A alone reduces TS cleavage by ~40 %"
- **Evidence pointer** Results section "Mutations of the lid adversely affect target strand traversal"; Figure 4b
- **Concern** The experimental validation is described qualitatively. No information is provided on the number of replicates, error bars, statistical significance, or how the cleavage rates were quantified. The statement "~40 %" for F1012A lacks precision. Additionally, the manuscript does not clarify whether the reduced cleavage is due to impaired TS traversal specifically or to other effects, such as reduced binding or altered protein stability.
- **Why it matters** The experimental data are used to corroborate the computational predictions. Without proper statistical analysis and controls, the strength of this corroboration is unclear.
- **Resolution test** Provide quantitative data with replicates, error bars, and statistical tests. Include control experiments to rule out effects on protein stability or binding. Consider testing additional mutants to establish a structure-function correlation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The proposed mechanism is presented as a general model for Cas12a function, with implications for engineering.
- **Evidence pointer** Discussion section
- **Concern** The simulations and experiments are based on Francisella novicida Cas12a. The generalizability of the lid-mediated mechanism to other Cas12a orthologs or to Cas12b/Cas12c is not discussed. Sequence conservation of the lid residues across orthologs is not analyzed.
- **Why it matters** If the mechanism is not conserved, the broader implications for genome editing may be overstated.
- **Resolution test** Add a sequence alignment or conservation analysis of the lid region across Cas12a orthologs. Discuss whether the proposed mechanism is likely to be universal or specific to FnCas12a.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The abstract and introduction use technical terms (e.g., "crRNA:TS hybrid," "RuvC catalytic core") without defining them for a general audience. The significance of the "alpha-helical lid" is not introduced until the results section.
- **Required correction** Briefly define key terms and introduce the lid concept in the introduction to improve accessibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Structural Models
- **Evidence pointer** Methods "Structural Models"
- **Issue** The homology modeling of the disordered lid in the 5NFV structure is described, but the quality of the model (e.g., sequence identity, template structure) is not assessed. The choice of SWISS-MODEL is not justified.
- **Required correction** Provide details on the modeling quality, such as sequence identity to the template and model validation scores (e.g., QMEAN, MolProbity).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Umbrella Sampling simulations
- **Evidence pointer** Methods "Umbrella Sampling simulations"
- **Issue** The force constants for the US simulations are reported, but the rationale for choosing these values and the bin sizes is not explained. The equilibration time for each window is not specified.
- **Required correction** Justify the choice of force constants and bin sizes, and state the equilibration time for each window.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section "REC2 and Nuc facilitate the traversal of the TS"
- **Evidence pointer** Results section "REC2 and Nuc facilitate the traversal of the TS"
- **Issue** The description of bending angle analysis is brief and may be difficult to follow without the supplementary methods. The reference to "vector passing through the regions of interest" is vague.
- **Required correction** Provide a clearer description of the bending angle calculation in the main text or refer more explicitly to the supplementary methods.

## Risk / unsupported claims
- The claim that the lid "guides" the TS toward the RuvC core is supported by simulations and experiments, but the causal relationship is inferred rather than directly demonstrated. The possibility that the lid merely stabilizes a conformation that favors traversal is not excluded.
- The statement that the mechanism is "elegant" and "cardinal" is subjective and not directly supported by data.
- The claim that the findings "will enrich fundamental knowledge and facilitate further engineering strategies" is speculative and not substantiated by specific examples.
- The assertion that the lid's interactions are "critical" for TS traversal is based on mutant studies, but the degree of impairment and the specificity of the effect are not fully quantified.
- The generalizability of the mechanism to other Cas12a orthologs is not established and should not be assumed.