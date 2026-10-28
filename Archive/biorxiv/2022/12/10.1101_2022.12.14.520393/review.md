## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) from bioRxiv preprint
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors use all-atom steered MD simulations with Jarzynski's equality and umbrella sampling to compute binding free energy differences between a WRKY transcription factor domain protein bound to specific vs non-specific DNA. They report a difference of approximately 10 kBT, supporting the idea that search and recognition modes are distinguished by protein orientation rather than conformation. They further hypothesize that discrepancies with experimental estimates (~4-5 kBT) arise from flanking DNA sequences affecting dissociation kinetics, supported by a simplified spherical protein model with stochastic simulations.
- **Visible evidence base** Main text figures (Figures 1-6), supplementary figure references (Figures S1, S3-S8), methods descriptions, and discussion
- **Missing materials affecting confidence** Supplementary Information (SI) sections referenced but not provided in full; specific numerical values for some free energies are omitted in the text (indicated by blank spaces); simulation trajectory data not available; experimental details from prior work [19, 20] not fully described

## Reviewer
- **Overall assessment** The manuscript addresses an important question in transcription factor target search: whether binding free energy differences between specific and non-specific DNA can be attributed to protein orientation rather than conformational change. The computational approach is reasonable, and the combination of all-atom MD with a simplified model is potentially powerful. However, several technical concerns limit the strength of the conclusions as currently presented. The reported free energy values are partially missing from the text, the convergence of Jarzynski-based PMFs appears questionable given the non-Gaussian work distributions, and the simplified model's connection to the all-atom results requires clearer justification. The hypothesis regarding flanking sequence effects is interesting but the evidence presented is indirect.

- **Who would be interested in the results, and why** Researchers in computational biophysics, protein-DNA interactions, and gene regulation would find this work relevant. Those studying facilitated diffusion models of transcription factor target search would be particularly interested in the quantitative estimate of binding free energy differences between specific and non-specific DNA. The methodological comparison between Jarzynski's equality and umbrella sampling for protein-DNA dissociation would also interest practitioners of free energy calculations.

- **Major strengths** The study addresses a fundamental question in transcription factor biology with state-of-the-art computational methods. The use of two independent free energy calculation methods (Jarzynski's equality and umbrella sampling) provides cross-validation. The authors acknowledge limitations of their sampling and propose a testable hypothesis for the discrepancy with experimental measurements. The simplified spherical model provides a conceptual framework for understanding flanking sequence effects.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have obtained binding free energies of approximately 10 kBT difference between specific and non-specific DNA binding, with specific values reported as "and" without numerical values in the text.
- **Evidence pointer** Results section, "Binding free energy measurements using SMD & Jarzynski's equality" and "Binding free energy measurements using Umbrella Sampling"; Figure 3b,d
- **Concern** The actual numerical values of the binding free energies are missing from the manuscript text. The phrases "we obtain and , corresponding to the nonspecific and specific binding free energies, respectively" and "The binding free energy difference between the systems is then given by" contain blank spaces where values should be. This makes it impossible to evaluate the magnitude of the reported effect, the statistical significance, or the consistency between the two methods.
- **Why it matters** The central quantitative claim of the paper is the binding free energy difference of approximately 10 kBT. Without the actual values, the reader cannot assess whether this difference is robust, whether the two methods agree within error, or whether the comparison with experimental estimates is meaningful.
- **Resolution test** Provide the numerical values with associated errors for all reported binding free energies in both the main text and figure captions. State explicitly whether the two methods agree within statistical uncertainty.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that PMFs obtained using Jarzynski's equality with only the first two cumulants of the work distribution are "not well behaved" and that the exponential averaging form shows convergence within 4 kBT for specific and 2 kBT for non-specific binding.
- **Evidence pointer** Results section, "Binding free energy measurements using SMD & Jarzynski's equality"; Figure S8
- **Concern** The authors acknowledge that the work distributions deviate significantly from Gaussian, which is a requirement for the cumulant expansion to be valid. They then use the exponential averaging form, but the convergence criterion of 4 kBT for the specific system is large relative to the reported difference of ~10 kBT. It is unclear how many independent trajectories were used, whether the 10 trajectories per system are sufficient for the exponential average to converge, and whether the bias from insufficient sampling of rare low-work trajectories has been addressed.
- **Why it matters** Jarzynski's equality is notoriously sensitive to insufficient sampling, and the exponential average is dominated by rare trajectories with low work values. If these are not adequately sampled, the resulting PMF will be systematically biased. The stated convergence of 4 kBT could represent a substantial fraction of the reported binding free energy difference.
- **Resolution test** Provide a quantitative analysis of convergence, including the number of trajectories, the distribution of work values, and a comparison of PMFs obtained from different numbers of trajectories. Consider using bootstrap analysis to estimate the statistical error on the Jarzynski-based PMF.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors hypothesize that the discrepancy between their calculated binding free energy difference (~10 kBT) and the experimentally estimated value (~4-5 kBT) arises from flanking DNA sequences impacting dissociation kinetics measurements.
- **Evidence pointer** Results section, "PMF and protein dissociation kinetics from simplified spherical protein model"; Discussion section, "Toy model and analyses reveal potential impacts of flanking DNA sequence on measurements of protein-DNA affinity"
- **Concern** The simplified spherical protein model is used to support the flanking sequence hypothesis, but the connection between this highly simplified model and the all-atom system is not clearly established. The model parameters (charge distributions, interaction strengths, etc.) are not described in the main text, and the relationship between the model's free energy difference (7.9 kBT from steered simulations) and the all-atom result (~10 kBT) is not discussed. Furthermore, the model predicts a reduced free energy difference of ~3.2 kBT from dissociation kinetics, which is compared to the experimental value of ~4-5 kBT, but the discrepancy between 3.2 and 4-5 kBT is not addressed.
- **Why it matters** The flanking sequence hypothesis is presented as a resolution to the discrepancy between computation and experiment. If the simplified model does not quantitatively reproduce the experimental value, the hypothesis remains speculative. The model's assumptions and limitations need to be clearly stated to assess its validity.
- **Resolution test** Provide a more detailed description of the simplified model parameters and a sensitivity analysis. Discuss whether the model can be calibrated to reproduce the experimental value of 4-5 kBT, and whether the predicted flanking sequence effect is consistent with available experimental data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the protein in the nonspecific system has a more significant orientation change over time (16.6° ± 7.9° for nonspecific vs 10.1° ± 2.8° for specific)" and that the orientation angles with respect to the DNA are "quite different between the specific (57° ± 8°) and nonspecific (32° ± 3°) systems."
- **Evidence pointer** Results section, "Equilibrium reached for the specific and nonspecific complexes"; Figure 1c; Figure S1b
- **Concern** The orientation angle α is a critical parameter for the authors' conclusion that protein orientation distinguishes specific from non-specific binding. However, the definition of this angle is not provided in the main text, and the reported values have large uncertainties. The difference in orientation angles (57° vs 32°) is substantial, but it is unclear whether this reflects a stable orientational preference or a dynamically averaged quantity. The relationship between the orientation angle and the binding free energy difference is not quantitatively established.
- **Why it matters** The central claim that "search and recognition modes are distinguished only by protein orientations on the DNA" requires a clear demonstration that the orientation difference is the primary determinant of the binding free energy difference, rather than other factors such as specific hydrogen bonding patterns or electrostatic interactions.
- **Resolution test** Provide a clear definition of the orientation angle α and its calculation. Show the distribution of orientation angles over time for both systems, and demonstrate that the binding free energy difference can be attributed to the orientational preference rather than other structural or energetic factors.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract contains incomplete sentences with missing values: "with and " and "with and " appear without numerical values. This makes the abstract difficult to interpret.
- **Required correction** Complete the abstract with the actual numerical values of the binding free energies and their differences.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Steered MD (SMD) simulations setup"
- **Evidence pointer** Methods section, "Steered MD (SMD) simulations setup"; Figure 2
- **Issue** The choice of pulling direction (the −y direction for the specific DNA system and +z direction for the non-specific DNA system) is justified by stating that these directions have the protein dissociation "most ready or probable" based on RAMD simulations. However, the criteria for selecting these directions and the number of RAMD trials are not described.
- **Required correction** Provide details on the RAMD protocol, including the number of trials, the criteria for determining the most probable dissociation direction, and whether the chosen directions are consistent across multiple trials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Calculations using umbrella sampling"
- **Evidence pointer** Methods section, "Calculations using umbrella sampling"; Figure S4
- **Issue** The authors state that a single SMD trajectory was used to generate the starting configurations for 21 umbrella sampling windows. The choice of a single trajectory may introduce bias if the dissociation pathway is not representative of the ensemble of possible pathways.
- **Required correction** Discuss the potential bias from using a single trajectory and consider whether multiple independent SMD trajectories should be used to generate starting configurations for the umbrella sampling windows.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data Availability
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement says "Computing codes available upon request" but does not mention availability of simulation input files, trajectories, or analysis scripts.
- **Required correction** Provide a more detailed data availability statement, including information about simulation input files, force field parameters, and analysis scripts.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion, "Protein-DNA binding free energetics in the respective search vs recognition modes"
- **Evidence pointer** Discussion section
- **Issue** The sentence "It is important to note that the protein spontaneous dissociation is a stochastic 3D process that likely happens at millisecond time scale or over, and along various directions or paths" is followed by a discussion of the enforced dissociation pathway, but the relationship between the enforced pathway and the spontaneous process is not clearly articulated.
- **Required correction** Clarify how the enforced dissociation pathway relates to the spontaneous dissociation process and whether the computed binding free energy is expected to be independent of the chosen pathway.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "PMF and protein dissociation kinetics from simplified spherical protein model"
- **Evidence pointer** Results section, "PMF and protein dissociation kinetics from simplified spherical protein model"; Figure 6
- **Issue** The simplified model results are presented with limited detail. The number of stochastic simulations, the integration time step, the temperature, and the criteria for defining dissociation events are not described.
- **Required correction** Provide sufficient methodological detail for the simplified model simulations to be reproducible.

## Risk / unsupported claims
- The claim that the binding free energy difference between specific and non-specific DNA binding is approximately 10 kBT cannot be fully evaluated because the numerical values are missing from the text.
- The claim that "search and recognition modes are distinguished only by protein orientations on the DNA" is not fully supported, as the authors do not rule out other contributing factors such as changes in hydrogen bonding patterns or electrostatic interactions that may accompany the orientational change.
- The hypothesis that flanking DNA sequences explain the discrepancy between computational and experimental binding free energy differences is plausible but not quantitatively established, as the simplified model predicts a value (3.2 kBT) that does not match the experimental estimate (4-5 kBT).
- The statement that the protein in the non-specific system "starts rotating as early as ξ = 0.5 nm" while the specific system "starts freely rotating at ξ ≈ 1 nm" is presented without statistical analysis or error estimates.
- The comparison between the computed binding free energy difference and the experimental value relies on experimental data from prior work [19, 20] that is not described in sufficient detail to assess the validity of the comparison.