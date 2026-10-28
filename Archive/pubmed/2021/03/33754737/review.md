## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusions
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity as presented in the provided manuscript
- **Shared manuscript claim summary** The authors use coarse-grained and atomistic molecular dynamics simulations to investigate the molecular requirements for protein sliding along DNA, defined as rotation-translation coupled diffusion. They report that sliding is common among diverse DNA-binding proteins at low salt concentrations, transitions to hopping at higher salt concentrations, requires a minimum of five positively charged residues on the recognition helix for a homeodomain protein, and that wild-type PCNA predominantly follows hopping rather than sliding dynamics.
- **Visible evidence base** Figures 2-8, simulation methods described in the Methods section, and qualitative comparisons to published experimental and computational studies
- **Missing materials affecting confidence** Simulation parameter files, force field validation data, convergence criteria, error bars on reported slopes and diffusion coefficients, PDB validation for the PCNA model, and raw trajectory data

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in the field of protein-DNA interactions, namely the molecular determinants of sliding versus hopping diffusion mechanisms. The combination of coarse-grained and atomistic simulations is appropriate and potentially powerful. However, the evidence presented does not fully establish several key claims, particularly regarding the universality of sliding among DNA-binding proteins, the quantitative threshold of five positive charges, and the interpretation of the atomistic PCNA trajectories. The manuscript would benefit from additional quantitative analysis, clearer presentation of simulation reproducibility, and more careful distinction between supported and speculative conclusions.
- **Who would be interested in the results, and why** Researchers studying protein-DNA recognition, transcription factor target search mechanisms, DNA repair processes, and sliding clamp dynamics would find these results relevant. The work also speaks to the broader biophysics community interested in diffusion mechanisms on charged biopolymers and the role of electrostatics in molecular recognition.
- **Major strengths** The study addresses a fundamental mechanistic question with broad implications. The use of both coarse-grained and atomistic simulations is complementary and appropriate. The systematic variation of salt concentration and charge mutations provides a useful framework. The inclusion of non-DNA-binding proteins as controls is a thoughtful design element. The discussion of PCNA is well contextualized within the existing literature and highlights an important controversy.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality is moderate to high; the question is important and the approach is reasonably novel, though similar simulation studies exist. Scientific importance is significant for the specialized field of protein-DNA interactions, but the broader impact beyond this community may be limited. Interdisciplinary readership is possible given the biophysical focus, but the manuscript is written primarily for a specialist audience. Technical soundness is currently insufficient to fully support the claims, as detailed in the major concerns. Readability for nonspecialists is adequate but could be improved with clearer explanations of the simulation methodology and the significance of the rotation-translation coupling metric.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the quantitative support for the charge threshold claim, the interpretation of the atomistic PCNA trajectories, and the generalizability of the findings.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "a minimum of five positively charged residues at the recognition helix is necessary, albeit insufficient, for HD to slide along DNA via rotation-coupled translation."
- **Evidence pointer** Figure 4, Results section "Sliding of DNA-Binding Proteins along DNA"
- **Concern** The claim of a specific threshold of five positive charges is based on a limited set of mutants: one with six charges, six with five charges, and fifteen with four charges. The authors state that neutralizing two or more positive charges at any position led to loss of coupled diffusion, but the data presentation in Figure 4 is not sufficiently detailed to assess the statistical significance or reproducibility of this threshold. It is unclear how many independent simulations were performed per mutant, what the variability was across simulations, and whether the loss of coupling was abrupt or gradual.
- **Why it matters** The specific numerical threshold is a central quantitative claim of the paper. If the threshold is not robustly established, the conclusion that five charges are "necessary" is not supported. This claim could be an artifact of the specific protein system, the coarse-grained model, or the limited mutant sampling.
- **Resolution test** Provide a quantitative analysis of the slope of theta/Z for each mutant, including error bars and statistical tests comparing mutants with different charge numbers. Show that the loss of coupling is consistent across multiple independent simulations and is not dependent on the specific positions of the charges. Ideally, test additional mutants with intermediate charge numbers or different charge arrangements to confirm the threshold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretive validity
- **Claim pointer** The authors claim that "the toroidal PCNA protein is shown to follow the hopping rather than the sliding mechanism" based on both coarse-grained and atomistic simulations.
- **Evidence pointer** Figures 5 and 6, Results sections "Coarse-Grained Molecular Dynamics Simulations of PCNA Diffusion along DNA" and "Atomistic Simulations of PCNA Diffusion along DNA"
- **Concern** The atomistic simulations show heterogeneous behavior: three trajectories support hopping, two support sliding, and one is ambiguous. The authors emphasize the hopping interpretation but acknowledge that some trajectories support sliding. The coarse-grained simulations show no coupling for wild-type PCNA, but the authors also show that a variant with a single positively charged subunit does exhibit sliding. This suggests that the diffusion mechanism may be sensitive to the specific charge distribution and simulation conditions. The conclusion that PCNA "follows the hopping rather than the sliding mechanism" is therefore an oversimplification of the presented data.
- **Why it matters** The PCNA case is a central example in the paper and is used to argue against a recent structural study. If the simulation evidence is mixed, the conclusion should be more nuanced. Overstating the hopping mechanism could mislead readers and incorrectly dismiss the alternative interpretation.
- **Resolution test** Present a more balanced interpretation of the atomistic trajectories, clearly distinguishing between trajectories that support hopping, sliding, and ambiguous behavior. Discuss the possible reasons for the variability, such as differences in initial conditions, sampling time, or force field accuracy. If the authors wish to claim that hopping is the dominant mechanism, provide a quantitative metric that supports this conclusion across the ensemble of simulations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that the coarse-grained model can distinguish between sliding and hopping mechanisms based on the slope of theta/Z plots, and that a slope of -0.18 rad/angstrom indicates sliding.
- **Evidence pointer** Methods section "Coarse-Grained Molecular Dynamics Simulations", Results section "Sliding of DNA-Binding Proteins along DNA"
- **Concern** The coarse-grained model uses a native-contact based force field with a single bead per residue and three beads per nucleotide. The authors note that the effective salt concentration in the coarse-grained model may be higher by a factor of about 3 than in atomistic representations. This calibration issue is not addressed in the interpretation of the salt-dependent transitions. Additionally, the criterion of a slope of -0.18 rad/angstrom for sliding is based on the helical pitch of ideal B-DNA, but the authors do not demonstrate that this slope is robust to the choice of coarse-grained parameters or that it is uniquely associated with sliding rather than other diffusion modes.
- **Why it matters** The validity of the coarse-grained model is central to the conclusions about the universality of sliding and the salt-dependent transitions. If the model is not properly calibrated or if the sliding criterion is not well-defined, the conclusions drawn from the coarse-grained simulations are unreliable.
- **Resolution test** Provide a validation of the coarse-grained model against atomistic simulations or experimental data for at least one system. Show that the slope of theta/Z is stable across different simulation lengths, system sizes, and model parameters. Demonstrate that the sliding criterion is not an artifact of the specific coarse-grained representation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "sliding appears to be a mechanism common to diverse DNA-binding proteins that possess different structural features and perform various functions."
- **Evidence pointer** Figures 2 and 3, Results section "Sliding of DNA-Binding Proteins along DNA"
- **Concern** The claim of universality is based on only three DNA-binding proteins (SAP1, HD, and Skn1) and one minor-groove binder (HMG box). While these proteins are diverse in structure and function, three examples are insufficient to establish that sliding is "common" or "universal" among DNA-binding proteins. The authors also note that some DNA-binding proteins, such as TALE and UL42, have been experimentally characterized to diffuse via hopping, which contradicts the claim of universality.
- **Why it matters** The claim of universality is a key conceptual contribution of the paper. If the evidence is limited to a small number of systems, the claim should be appropriately qualified. Overgeneralization could lead to incorrect assumptions about the diffusion mechanisms of other DNA-binding proteins.
- **Resolution test** Either expand the set of DNA-binding proteins studied to include a wider range of structures and functions, or qualify the claim to state that sliding is common among the specific proteins studied. Discuss the features that distinguish proteins that slide from those that hop, based on the available data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretive validity
- **Claim pointer** The authors claim that "the DNA does not interact with a particular PCNA subunit for any extended period" based on hydrogen bond analysis of two atomistic trajectories.
- **Evidence pointer** Figures 7 and 8, Results section "Atomistic Simulations of PCNA Diffusion along DNA"
- **Concern** The hydrogen bond analysis is based on only two trajectories, and the authors themselves note that the number of hydrogen bonds is highly variable and that the system is dynamic. The conclusion that the DNA does not interact with a particular subunit for an extended period is based on a qualitative assessment of hydrogen bond patterns. No quantitative analysis of residence times or interaction persistence is provided.
- **Why it matters** This claim is used to argue against the interpretation of a recent structural study that proposed specific interactions between PCNA residues and DNA. If the claim is not quantitatively supported, the argument against the structural study is weakened.
- **Resolution test** Provide a quantitative analysis of hydrogen bond residence times and interaction persistence for each PCNA subunit. Show that the interactions are indeed transient and that no single subunit dominates the interaction over the simulation time. If possible, extend the analysis to additional trajectories to increase statistical power.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "coupling, while widespread, is not universal" but does not define what "widespread" means in quantitative terms. The abstract also does not mention the specific finding regarding the minimum number of positive charges required for sliding.
- **Required correction** Consider adding a quantitative statement about the proportion of proteins that exhibit sliding and explicitly mention the charge threshold finding in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Methods section
- **Evidence pointer** Methods section "Coarse-Grained Molecular Dynamics Simulations"
- **Issue** The force field equation is not fully defined in the text. The parameters Kbonds, Kangles, etc. are listed, but the functional forms of the potential terms are not explicitly given. This makes it difficult for readers to reproduce the simulations.
- **Required correction** Provide the full functional form of the force field or a reference to a publication where it is described in detail.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Figure 3
- **Issue** The slopes of theta/Z plots are reported as mean values, but no error bars or confidence intervals are shown. It is unclear how much variability exists across the 10 simulations per condition.
- **Required correction** Add error bars or confidence intervals to the data points in Figure 3 and report the number of independent simulations used for each condition.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Conclusions section
- **Issue** The authors mention that a recent cryo-EM structure supports their finding, but they do not provide a citation for this structure. They also do not discuss the limitations of their simulations in comparison to the experimental structures.
- **Required correction** Add the citation for the cryo-EM structure and briefly discuss how the simulation results compare to the experimental structural data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Introduction, Results
- **Issue** The terms "sliding" and "hopping" are used throughout, but the definitions are only given in the Introduction. The authors also use the term "rotation-translation coupling" without clearly explaining how it relates to the physical mechanism of diffusion.
- **Required correction** Provide a clear operational definition of sliding and hopping in the Methods section and explain how the rotation-translation coupling metric is calculated and interpreted.

## Risk / unsupported claims
- The claim that "a minimum of five positively charged residues at the recognition helix is necessary" for sliding is not fully supported by the data presented, as the mutant sampling is limited and no statistical analysis is provided.
- The claim that "PCNA follows the hopping rather than the sliding mechanism" is an oversimplification of the atomistic simulation results, which show heterogeneous behavior across trajectories.
- The claim that "sliding appears to be a mechanism common to diverse DNA-binding proteins" is based on a small number of examples and is contradicted by the authors' own discussion of proteins that hop.
- The claim that "the DNA does not interact with a particular PCNA subunit for any extended period" is based on qualitative analysis of only two trajectories and lacks quantitative support.
- The assertion that the coarse-grained model's effective salt concentration is higher by a factor of about 3 is not validated or corrected for in the interpretation of salt-dependent transitions.