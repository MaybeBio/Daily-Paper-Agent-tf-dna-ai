## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors use 10–15 μs all-atom MD simulations of Thermus aquaticus MutS bound to homoduplex and T-bulge DNA to propose a multistep indirect readout mechanism for mismatch search, involving DNA shape checking, global bendability probing, and local basepair deformability assessment, culminating in mismatch recognition via the Phe-X-Glu motif.
- **Visible evidence base** MD simulation trajectories (10 μs MutS-T-bulge, 10 μs MutS-homoduplex, plus two replicate 10 μs MutS-homoduplex runs; 15 μs free DNA runs), RMSD/RMSF analyses, DCCM calculations, PCA, K-means clustering, Curves+ bending analysis, contact frequency analysis, and structural overlays
- **Missing materials affecting confidence** The manuscript text references supplementary figures (S1–S9), tables (S1–S3), and videos (S1–S4) that were not provided for review. Specific numerical data for contact frequencies, hydrogen bond occupancies, and energy calculations are not fully detailed in the main text. Force field validation and convergence assessment details are limited.

## Reviewer
- **Overall assessment** This manuscript presents a substantial computational investigation into the MutS mismatch search mechanism, addressing a significant gap in the field. The use of microsecond-timescale all-atom MD simulations is ambitious and appropriate for the questions posed. The proposed three-tiered indirect readout model (shape, bendability, deformability) is conceptually appealing and provides a plausible framework for how MutS discriminates mismatches from canonical DNA. However, several technical concerns regarding simulation setup, analysis rigor, and the strength of the evidence for the proposed mechanism require careful consideration before the conclusions can be fully accepted.

- **Who would be interested in the results, and why** Researchers in DNA repair, particularly those studying mismatch repair mechanisms, will find this work directly relevant. The computational biophysics community, especially those using MD simulations to study protein-DNA interactions, will be interested in the methodological approach and the long-timescale simulations. Structural biologists studying MutS family proteins and those interested in indirect readout mechanisms in protein-DNA recognition will also find value. The findings may also be of interest to researchers studying the molecular basis of Lynch syndrome, given the connection to MutS mutations.

- **Major strengths** The study addresses a fundamental and long-standing question in the mismatch repair field with an appropriate and state-of-the-art computational approach. The use of microsecond-timescale simulations is a significant advance over previous shorter simulations. The identification of distinct conformational substates along a pathway and the correlation of MutS conformational changes with DNA bending/unbending provides a dynamic view of the search process. The authors are appropriately cautious in some interpretations and acknowledge limitations, such as the use of a single starting structure. The proposed model integrates existing structural, biochemical, and single-molecule data into a coherent framework.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the observed conformational transitions in the MutS-homoduplex complex represent a "kinetic pathway" of substates that constitute a mismatch search mechanism.
- **Evidence pointer** Figure 5, Figure 6, Videos S3 and S4, Table S1
- **Concern** The interpretation of the nine clusters as a sequential kinetic pathway is based on a single 10 μs trajectory. While the authors performed two additional replicate simulations, the manuscript text states these replicates also show "similar results" but does not provide sufficient detail on whether the same nine substates were observed in the same sequential order, or whether the lifetimes and transitions were comparable. The claim of a defined pathway requires demonstration of reproducibility across independent trajectories. Furthermore, the assignment of substates as "on-pathway" intermediates in a search mechanism implies that these states are functionally relevant, but the manuscript does not provide a clear energetic or kinetic analysis (e.g., free energy profiles, transition rates) to support this interpretation. The clustering analysis identifies distinct conformations, but the sequential appearance of clusters in a single trajectory does not necessarily establish a preferred or biologically relevant pathway.
- **Why it matters** The central claim of the paper is that the simulations reveal a search mechanism. If the pathway is not reproducible or the substates are not energetically distinguishable, the mechanistic interpretation is weakened. The field requires robust evidence that the observed dynamics are not simply stochastic fluctuations of a flexible complex but represent a directed or biased search process.
- **Resolution test** The authors should provide a detailed comparison of the substates identified in all three independent MutS-homoduplex trajectories, including the order of appearance, lifetimes, and transition probabilities. Ideally, they would perform a Markov state model analysis to estimate transition rates and free energies between substates, which would provide a more rigorous basis for claiming a kinetic pathway. If the pathway is not reproducible, the claims should be moderated to describe the observed conformational flexibility rather than a defined search pathway.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors propose that specific MutS residues (Ser-63, Lys-64, Arg-110, Arg-76, Arg-473, Arg-475, Asn-443, Lys-471, Asp-38) constitute a "mismatch detection interface" that checks DNA shape, bendability, and deformability.
- **Evidence pointer** Figure 7, Table S2, Figure S9, Table S3
- **Concern** The selection of residues for the interaction analysis is based on a contact frequency threshold of >20% of frames having at least one hydrogen bond. This is a relatively low threshold and may include transient, non-specific interactions. The manuscript does not provide a clear definition of what constitutes a "functional" contact versus a transient encounter. More critically, the assignment of specific residues to specific functional roles (shape checking vs. bendability vs. deformability) appears somewhat arbitrary. For example, why do Arg-473 and Arg-475 in subunit A constitute "stable" contacts while the same residues in subunit B are described as "dynamic"? The manuscript does not provide a quantitative comparison of contact stability or interaction energies between the two subunits. The claim that Asp-38 and Lys-471 act as a "pincer" to check local deformability is intriguing but is not supported by direct evidence of basepair destabilization (e.g., increased basepair opening rates or decreased hydrogen bond occupancy at the probed site).
- **Why it matters** The proposed mechanism rests on the specific roles assigned to these residues. If the residue classification is not robust or the functional assignments are not well-supported, the proposed three-tiered mechanism becomes speculative. The field needs clear evidence linking specific interactions to specific functional outcomes.
- **Resolution test** The authors should provide a more rigorous analysis of the interactions, including: (1) a comparison of contact frequencies and hydrogen bond occupancies between the MutS-homoduplex and MutS-T-bulge complexes for each residue; (2) an analysis of the persistence and stability of individual contacts over time; (3) a more detailed structural rationale for why specific residues are assigned to specific functional roles; and (4) ideally, additional simulations or analyses (e.g., targeted mutations in silico) to test the proposed functional roles.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the MutS signature Phe-X-Glu motif can then lock in the mismatch-recognition complex to initiate repair" and that Phe-39 is "twice as flexible in the MutS-homoduplex versus the MutS-T-bulge trajectory."
- **Evidence pointer** Figure 2, Results section "MutS-DNA interactions"
- **Concern** The claim about Phe-39 flexibility is presented as a single observation without statistical analysis. The manuscript does not report the actual RMSF values or the uncertainty in these measurements. More importantly, the functional significance of this increased flexibility is not clearly established. The authors suggest it is "consistent with previous AFM studies," but the connection between increased flexibility in a homoduplex complex and the role of Phe-39 in mismatch recognition is not directly demonstrated. The statement that the Phe-X-Glu motif "can then lock in" the recognition complex is presented as a conclusion, but the simulations do not appear to capture the transition from the search state to the recognition state, as the T-bulge complex was simulated separately and started from the recognition conformation.
- **Why it matters** The role of the Phe-X-Glu motif is central to the proposed mechanism. If the evidence for the transition from search to recognition is not directly observed, the claim that the simulations illuminate this transition is overstated. The field requires direct evidence of the conformational transition or a clear statement that this transition is inferred rather than observed.
- **Resolution test** The authors should provide quantitative RMSF data for Phe-39 in both complexes, including error estimates. They should also clarify whether the simulations capture the transition from the search state to the recognition state or whether this is inferred from separate simulations. If the latter, the claims should be moderated accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors propose that the observed mechanism explains how MutS "can localize a potential target by indirect readout due to lower energetic costs of bending mismatched DNA."
- **Evidence pointer** Figure 4, Results section "Changes in DNA structural dynamics"
- **Concern** The manuscript does not provide a quantitative energetic analysis to support the claim that mismatched DNA has a lower bending cost. The bending analysis (Figure 4) shows that the T-bulge DNA remains bent in the MutS complex while the homoduplex straightens, but this does not directly demonstrate a difference in bending energetics. The authors reference previous studies (29, 67) for this concept, but the current simulations do not appear to provide new energetic data. The claim that the lower energetic cost "could help localize the protein" is presented as a hypothesis, but the manuscript does not test this hypothesis directly.
- **Why it matters** The energetic argument is a key component of the proposed mechanism. Without quantitative support from the simulations, this aspect of the mechanism remains speculative. The field would benefit from a direct calculation of bending free energies for matched vs. mismatched DNA in the context of MutS binding.
- **Resolution test** The authors should either provide a quantitative energetic analysis (e.g., free energy perturbation or umbrella sampling calculations of DNA bending in the MutS complex) or clearly state that this aspect of the mechanism is inferred from previous studies and not directly tested in the current work.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 1 legend
- **Evidence pointer** Figure 1
- **Issue** The figure legend describes the domain coloring but does not clearly indicate which structural elements correspond to the "mismatch detection interface" highlighted in the inset. The inset is described but the reader must infer which domains are shown.
- **Required correction** Please add a sentence to the legend explicitly identifying the domains and residues shown in the inset and their relationship to the full complex.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "MD simulations"
- **Evidence pointer** Methods section
- **Issue** The methods state that "Random seeds were utilized to initiate the simulations" but do not specify how many seeds were used or whether the replicates used different seeds. The description of the two additional replicate simulations is brief and does not specify whether they were started from the same or different initial structures.
- **Required correction** Please provide more detail on the replicate simulations, including the number of replicates, the initial conditions, and the specific random seeds used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "Changes in MutS structural dynamics"
- **Evidence pointer** Figure 2
- **Issue** The RMSF analysis is described qualitatively ("sharp spikes are due to loop regions"), but no numerical threshold is provided for what constitutes a "sharp spike" or a "significant" deviation. The comparison between the T-bulge and homoduplex complexes is descriptive rather than quantitative.
- **Required correction** Please provide quantitative RMSF values for key regions (e.g., clamp domain, mismatch binding domain) in both complexes, with appropriate statistical measures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section "Implications of asymmetry"
- **Evidence pointer** Discussion section
- **Issue** The discussion of asymmetry in eukaryotic MSH2-MSH6 versus bacterial MutS is interesting but somewhat speculative. The statement that "the division of labor in the mismatch search mechanism employed by bacterial homodimers may have allowed Msh2 to retain the common function" is presented without direct evidence from the simulations.
- **Required correction** Please clearly distinguish between conclusions drawn from the current simulations and evolutionary hypotheses that are speculative. Consider adding a sentence acknowledging the speculative nature of this discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "MutS-DNA interactions"
- **Evidence pointer** Table S2
- **Issue** The contact frequency analysis is described as being based on ">20% of all frames in the substate trajectory have at least one hydrogen bond." This threshold is not justified, and the manuscript does not report the sensitivity of the results to this threshold.
- **Required correction** Please justify the choice of threshold or provide a sensitivity analysis showing that the identified contacts are robust to reasonable variations in the threshold.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that MutS checks DNA for "1) shape, through contacts with the sugar-phosphate backbone, 2) conformational flexibility, through bending/unbending engineered by large-scale motions of the clamp domain, and 3) local deformability, through basepair destabilizing contacts." This three-part list is clear, but the abstract could benefit from a brief statement about the timescales of these processes to give readers a sense of the dynamics involved.
- **Required correction** Consider adding a phrase such as "on microsecond timescales" to the abstract to emphasize the temporal resolution of the simulations.

## Risk / unsupported claims
- The claim that the observed substates constitute a "kinetic pathway" for mismatch search is not fully supported by the evidence presented, as it is based primarily on a single trajectory with limited detail on replicate reproducibility.
- The assignment of specific functional roles (shape, bendability, deformability) to specific residues is not rigorously justified and may be an oversimplification of the complex interaction network.
- The claim that the simulations reveal how MutS "can localize a potential target by indirect readout due to lower energetic costs of bending mismatched DNA" is not directly tested in the simulations; no energetic calculations are presented.
- The statement that the Phe-X-Glu motif "can then lock in the mismatch-recognition complex" implies a transition that is not directly observed in the simulations.
- The evolutionary speculation about the division of labor in bacterial versus eukaryotic MutS homologs is not supported by data presented in this manuscript.
- The significance of the increased flexibility of Phe-39 in the homoduplex complex is not quantitatively established or functionally validated.