## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report molecular dynamics simulations of the MntR protein from *Halalkalibacterium halodurans* (HhMntR) in complex with its DNA operator sequence (mntA), comparing the holoprotein (with Mn2+) and apoprotein (without Mn2+). They claim that Mn2+ binding increases DNA affinity through stable noncovalent interactions in the holoprotein, whereas the apoprotein exhibits dynamic attach/detach behavior on a nanosecond timescale. They further claim identification of key amino acids and propose a molecular framework for HhMntR function as a transcription factor, including a mechanism of lateral movement along DNA during target search.
- **Visible evidence base** Abstract text only; no methodological details, simulation parameters, force fields, convergence criteria, or quantitative results are provided
- **Missing materials affecting confidence** Full manuscript, simulation setup and validation, force field parameters, trajectory analysis details, statistical measures (e.g., RMSD, binding free energies, contact maps), figures, tables, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study addressing a relevant question in bacterial metal homeostasis, namely how Mn2+ binding modulates MntR DNA affinity. The central claims are mechanistically interesting and potentially significant for understanding transcription factor regulation. However, the abstract alone provides insufficient evidence to evaluate the technical soundness of the simulations, the robustness of the conclusions, or the novelty relative to existing MntR studies. The claims regarding stable versus dynamic binding and the proposed lateral movement mechanism require quantitative support that is not visible in the supplied material.
- **Who would be interested in the results, and why** Researchers in bacterial metal homeostasis, transcription factor regulation, and protein-DNA recognition would find these results relevant. The study also speaks to the broader community interested in molecular dynamics simulations of metalloproteins and DNA-binding proteins, particularly those studying how metal ions allosterically modulate DNA affinity. The proposed mechanism of lateral movement during target search could interest biophysicists studying facilitated diffusion.
- **Major strengths** The study addresses a biologically important question with clear relevance to manganese homeostasis. The comparison between holo and apo states is a well-designed approach to isolate the effect of Mn2+ binding. The abstract suggests a mechanistically detailed picture, including the identification of key residues and a proposed search mechanism, which goes beyond a simple affinity difference statement.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that holoprotein binds DNA through stable and consistent noncovalent interactions while apoprotein shows highly dynamic attach/detach behavior on a nanosecond timescale.
  - **Evidence pointer** Abstract only; no figures, tables, or quantitative metrics provided
  - **Concern** The abstract provides no quantitative measures to support the qualitative distinction between "stable and consistent" versus "highly dynamic" behavior. No RMSD, contact occupancy, hydrogen bond persistence, or binding free energy values are reported. The timescale of nanoseconds is mentioned, but without convergence analysis or replicate simulations, it is unclear whether the observed dynamics are statistically meaningful or artifacts of insufficient sampling.
  - **Why it matters** The central mechanistic conclusion rests on this qualitative difference between holo and apo states. Without quantitative evidence and proper statistical validation, the claim cannot be assessed for robustness. Molecular dynamics results are highly sensitive to force field parameters, simulation length, and initial conditions, and the abstract provides no indication that these factors were adequately controlled.
  - **Resolution test** Provide quantitative metrics such as RMSD trajectories, contact maps, hydrogen bond occupancy, and binding free energy estimates for both holo and apo states, with error bars from replicate simulations. Demonstrate convergence of these metrics over the simulation timescale.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the same observations are seen even during simulations that started with protein and DNA separated from the complex.
  - **Evidence pointer** Abstract only; no methodological details provided
  - **Concern** The abstract states that simulations starting from separated protein and DNA reproduce the same behavior, but no details are given on how these simulations were set up, how long they were run, or how association events were defined and counted. Without this information, it is impossible to assess whether the observed association is specific or merely a consequence of high local concentrations in a periodic box.
  - **Why it matters** This claim is used to support the biological relevance of the proposed mechanism, suggesting that the protein can find and bind DNA spontaneously. If the association is not demonstrated to be specific and reproducible, the claim of lateral movement along DNA is weakened.
  - **Resolution test** Describe the setup of the separated simulations, including initial distances, box size, and ionic conditions. Report the number of independent association events, the time to first contact, and the specificity of the final bound conformation relative to the known operator sequence.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality
  - **Claim pointer** The claim that key amino acids involved in the formation of the HhMntR-DNA complex were identified, leading to a molecular framework for transcription factor function.
  - **Evidence pointer** Abstract only; no residue-level data provided
  - **Concern** The abstract claims identification of key amino acids but does not name them or provide any supporting data such as mutation analysis, sequence conservation, or comparison with homologous MntR proteins. Without this information, the novelty of the proposed framework cannot be evaluated relative to existing structural and functional studies of MntR family proteins.
  - **Why it matters** The proposed molecular framework is a key deliverable of the study. If the identified residues are already known from prior experimental or computational work, the novelty claim is diminished. If they are new, the lack of detail prevents assessment of their plausibility.
  - **Resolution test** List the specific residues identified, provide evidence for their role (e.g., contact persistence, energy contribution, conservation), and compare with known MntR-DNA interaction data from the literature.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The opening sentence states that transition metals are essential for bacterial survival, which is a general statement that does not directly connect to the specific study. The transition to the MntR protein and its role is abrupt.
  - **Required correction** Provide a more specific context linking manganese homeostasis to the biological question addressed, such as the consequences of manganese dysregulation in bacteria.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Simulation methodology description
  - **Evidence pointer** Abstract, no methodological details
  - **Issue** The abstract does not specify the force field, water model, or simulation length used. These are standard details expected in computational studies and are essential for reproducibility.
  - **Required correction** Include force field, water model, simulation length, and temperature/pressure coupling details in the abstract or refer to the methods section with specific parameters.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Proposed mechanism
  - **Evidence pointer** Abstract, final sentence
  - **Issue** The claim that observed behaviors promote lateral movement along DNA is presented as a conclusion, but the abstract does not explain how the simulation data directly support this specific mode of search. Lateral movement could be inferred from the dynamic behavior, but the connection is not explicit.
  - **Required correction** Clarify the logical link between the observed dynamics and the proposed lateral movement mechanism, or present this as a hypothesis rather than a direct conclusion.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking because the central mechanistic claims lack quantitative support and methodological transparency. Without these, the case for a Mn2+-dependent affinity switch and the proposed search mechanism is not established from the supplied material.
- **Assessment against Nature-style criteria**  
  *Originality*: The study addresses a known protein family but the specific focus on *H. halodurans* MntR and the proposed lateral movement mechanism may offer new insights. However, without comparison to prior MntR studies, originality cannot be fully assessed.  
  *Scientific importance*: The question of how metal ions modulate transcription factor DNA affinity is of broad relevance. The potential to link molecular dynamics to a biological search mechanism adds importance, but the abstract does not yet demonstrate this convincingly.  
  *Interdisciplinary readership*: The topic bridges microbiology, structural biology, and computational biophysics, which could attract a broad audience. However, the abstract is written in a way that assumes familiarity with molecular dynamics terminology.  
  *Technical soundness*: Not assessable from the abstract. The lack of methodological detail and quantitative results is a major limitation.  
  *Readability for nonspecialists*: The abstract is generally clear but could benefit from more context and less jargon. The mechanism description is accessible but the evidence base is not.
- **Recommendation posture** Currently not established from the provided evidence. The study has potential merit, and the research question is relevant, but the abstract alone does not provide sufficient quantitative or methodological detail to support the central claims. A revised version with full methodological transparency and quantitative results would be needed to assess whether the case can be made.

## Risk / unsupported claims
- The claim of stable versus dynamic binding behavior is unsupported without quantitative metrics.
- The claim that simulations starting from separated protein and DNA reproduce the same behavior is unsupported without methodological details.
- The identification of key amino acids is unverifiable from the abstract.
- The proposed lateral movement mechanism is presented as a conclusion but is not directly evidenced in the abstract.
- The overall claim that Mn2+ binding increases DNA affinity is plausible but not quantitatively demonstrated.