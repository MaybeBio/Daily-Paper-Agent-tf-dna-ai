## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report atomistic molecular dynamics simulations of a plant WRKY transcription factor domain protein diffusing along DNA, capturing a complete 1-bp stepping cycle on poly-A DNA, and propose a strand-biased association mechanism that balances target search and sequence recognition.
- **Visible evidence base** Main text, figures referenced (Figs. 1-5), SI Appendix references (Figs. S1-S17, Tables S1-S2), ITC binding data, single-molecule fluorescence measurements
- **Missing materials affecting confidence** SI Appendix content not provided, figure images not available, simulation parameter details not fully specified, experimental methods for single-molecule measurements not described in main text

## Reviewer
- **Overall assessment** This manuscript presents a substantial computational effort to characterize the diffusive behavior of a WRKY domain protein on DNA at atomic resolution. The work addresses a fundamental question in transcription factor target search and provides a plausible mechanistic framework. However, the evidence for the central claim of a complete 1-bp stepping cycle rests on a single event in one trajectory, and the statistical robustness of several key analyses is not established from the provided material. The strand-bias hypothesis is interesting but its functional significance remains speculative.
- **Who would be interested in the results, and why** Researchers studying protein-DNA interactions, transcription factor target search mechanisms, and molecular dynamics of biomolecular complexes. The work may also interest those developing coarse-grained models for protein diffusion and experimentalists using single-molecule approaches to study DNA-binding proteins.
- **Major strengths** The use of unbiased equilibrium atomistic simulations to capture protein diffusion events is commendable and represents a technical advance. The combination of atomistic and coarse-grained simulations with experimental validation (ITC, single-molecule fluorescence) provides a multi-scale approach. The identification of strand-biased association as a potential general principle for small DNA-binding domains is conceptually interesting.
- **Major Concerns** The central claim of a complete 1-bp stepping cycle is based on limited sampling. The statistical significance of the energetic analyses comparing static versus diffusive states is not fully established. The relationship between the computational findings and the experimental single-molecule measurements is not quantitatively connected. The functional implications of the strand-bias mechanism are not directly tested.
- **Minor Comments** Several methodological details are deferred to SI Appendix without sufficient summary in the main text. The presentation of the energetic analyses could be clearer. The discussion of related work could be more comprehensive.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The work offers a novel atomic-level view of protein stepping on DNA, which is a significant contribution. Scientific importance: The findings have implications for understanding transcription factor target search, a fundamental biological process. Interdisciplinary readership: The work bridges computational biophysics, structural biology, and molecular biology, and should appeal to a broad audience. Technical soundness: The simulation methodology is generally appropriate, but the statistical robustness of key claims requires strengthening. Readability for nonspecialists: The manuscript is generally well-written but assumes familiarity with molecular dynamics terminology and concepts.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness of central claim
- **Claim pointer** The authors claim to have captured "a complete stepping cycle of the protein for one base pair on DNA within microseconds" from atomistic simulations.
- **Evidence pointer** Figure 3, Results section "Atomistic Simulation of WRKY Diffusion along Homogeneous Poly-A DNA"
- **Concern** The central claim of a complete 1-bp stepping cycle appears to be based on a single event observed in one 10-μs trajectory. While the authors mention additional shorter simulations, it is unclear whether these provide independent observations of complete stepping cycles or merely sample intermediate states. The statistical basis for this claim is not established.
- **Why it matters** The observation of a single stepping event, however detailed, does not provide sufficient evidence for a general mechanism. Without multiple independent observations or a clear statistical framework, the claim that this represents a "complete stepping cycle" cannot be robustly evaluated.
- **Resolution test** Provide multiple independent observations of complete stepping cycles, or a statistical analysis demonstrating that the observed event is representative. Alternatively, clearly state the limitations of single-event observation and frame the claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative connection between simulation and experiment
- **Claim pointer** The authors state that the diffusion coefficient estimated from single-molecule fluorescence experiments (about 0.05 bp2/μs) is "consistent with our computational samplings of the protein stepping on the DNA."
- **Evidence pointer** Results section "The WRKY Electrostatic Association Bias toward the Preferred DNA Strand Is Less Distinct during Protein Diffusion than in the Static DNA Binding"
- **Concern** The claimed consistency between the experimental diffusion coefficient and computational sampling is not quantitatively demonstrated. No diffusion coefficient is reported from the atomistic simulations, and the relationship between the observed stepping events and a macroscopic diffusion coefficient is not established.
- **Why it matters** The comparison between experiment and simulation is a key validation of the computational findings. Without a quantitative connection, the claim of consistency is unsupported and potentially misleading.
- **Resolution test** Provide a quantitative estimate of the diffusion coefficient from the atomistic simulations, with appropriate error analysis, and demonstrate statistical consistency with the experimental value.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of strand-bias mechanism
- **Claim pointer** The authors propose that "the biased protein association with one strand of the dsDNA can be marginally sustained during the stochastic search process to facilitate fast protein movements, while the bias can be maximally employed into the quasi-static binding and DNA-sequence recognition."
- **Evidence pointer** Discussion section "The Protein Electrostatic Association Bias with One Strand of DNA Can Be Marginally Maintained to Assist the Domain Protein Diffusion and Maximally Employed to Support Protein DNA Sequence Recognition"
- **Concern** The functional significance of the strand-bias mechanism is asserted but not directly tested. The authors do not provide evidence that the observed bias is necessary or important for target search efficiency or specificity. The connection between the energetic analyses and the proposed functional role is speculative.
- **Why it matters** The strand-bias mechanism is presented as a general principle for small DNA-binding domains. Without direct testing of its functional importance, this claim remains a hypothesis rather than an established finding.
- **Resolution test** Provide direct evidence that the strand bias affects search efficiency or recognition specificity, for example through mutation studies or comparative simulations with proteins lacking the bias.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Simulation setup details
- **Evidence pointer** Materials and Methods section
- **Issue** The main text defers many methodological details to the SI Appendix without providing sufficient summary. Key parameters such as the exact simulation protocol, equilibration procedure, and analysis methods are not described in the main text.
- **Required correction** Provide a more complete summary of the simulation methodology in the main text, including key parameters and analysis procedures.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation of energetic analyses
- **Affected element** Figure 5 and related text
- **Evidence pointer** Results section "The WRKY Electrostatic Association Bias toward the Preferred DNA Strand Is Less Distinct during Protein Diffusion than in the Static DNA Binding"
- **Issue** The presentation of the energetic analyses, particularly the t-values and correlation coefficients, is dense and could be clearer. The relationship between these statistical measures and the biological conclusions is not immediately apparent.
- **Required correction** Clarify the presentation of the statistical analyses and explicitly state how they support the biological conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of related work on protein diffusion on DNA and transcription factor target search could be more comprehensive, particularly regarding recent experimental and computational studies.
- **Required correction** Expand the discussion to include more recent relevant literature and explicitly place the current findings in this context.

## Risk / unsupported claims
- The claim of a "complete stepping cycle" based on a single observed event is not statistically robust.
- The claimed consistency between experimental and computational diffusion coefficients is not quantitatively demonstrated.
- The functional significance of the strand-bias mechanism is asserted without direct testing.
- The generalizability of the strand-bias mechanism to other small DNA-binding domains is speculative.
- The relationship between the observed stepping dynamics and the estimated free energy barrier (~2 kBT) is not fully established.