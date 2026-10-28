## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, methodological soundness, evidence consistency, and interpretation within the provided manuscript only
- **Shared manuscript claim summary** The authors propose that the pioneer transcription factor Sox can bind to nucleosomal DNA when its cognate motif is on the solvent-facing strand, and that this binding is sequence-specific only at SHL2, with partial shape reading at SHL4 and no reading at the dyad, based on molecular dynamics simulations and footprinting experiments
- **Visible evidence base** MD simulation analyses (P-RMSD, minor groove width, interaction profiles), hydroxyl radical footprinting gels, UV laser footprinting gels, binding affinity quantifications, structural models
- **Missing materials affecting confidence** Raw simulation trajectories, replicate-level data for all systems, full footprinting gel images, statistical details for interaction frequency comparisons, Sox6 homology model validation, PDB validation reports for generated models, experimental replicates for footprinting

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in pioneer transcription factor biology, namely whether Sox can read its cognate sequence when positioned on the solvent-facing strand of nucleosomal DNA. The combination of computational and experimental approaches is commendable in principle. However, the evidence presented does not fully establish the central claims. The MD simulation analyses rely on short timescales and limited sampling, the interaction frequency data are presented without statistical treatment, and the footprinting experiments show weak protection at SHL2 and SHL4 that is interpreted as specific binding without adequate controls. The claim that SHL2 acts "transparently" for Sox binding is not convincingly supported by the data shown. The manuscript would benefit from additional replicates, clearer quantification, and a more cautious interpretation of the simulation results.
- **Who would be interested in the results, and why** Researchers studying pioneer transcription factors, chromatin structure and dynamics, nucleosome positioning, and protein-DNA recognition mechanisms would find this work relevant. The methodological framework combining MD simulations with footprinting could interest computational biologists working on protein-nucleosome interactions. The findings on position-dependent DNA reading could inform studies on gene regulation and chromatin remodeling.
- **Major strengths** The study addresses a specific and important gap in understanding Sox-nucleosome interactions, namely the solvent-facing binding mode. The combination of computational and experimental approaches provides complementary perspectives. The systematic comparison of three SHL positions is a useful design. The authors acknowledge limitations of their approach, including force field concerns and the use of Sox6 as a proxy for Sox11.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The question of solvent-facing Sox binding is a reasonable extension of prior work, but the conceptual advance is incremental given existing structural and biochemical data on Sox-nucleosome interactions. Scientific importance: The findings could inform understanding of PTF function, but the conclusions are not yet robust enough to have broad impact. Interdisciplinary readership: The work bridges computational biophysics and experimental biochemistry, which could appeal to multiple communities, but the presentation is somewhat specialized. Technical soundness: The MD simulations are underpowered for the claims made, and the footprinting data lack quantitative rigor. Readability for nonspecialists: The manuscript is generally well organized, but some methodological details and figure interpretations require domain expertise.
- **Recommendation posture** Currently not established from the provided evidence. The central claims regarding sequence-specific reading at SHL2 and the absence of reading at the dyad require stronger experimental and computational support.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that at SHL2, Sox binds to nucleosomal DNA with the same base-specific interaction profile as in free DNA, and that SHL2 acts "transparently" for Sox binding
- **Evidence pointer** Figure 1D, Figure 1E, Table S1, Results section "Sox Can Exert Its Fingerprint Base and Shape DNA Reading at SHL2"
- **Concern** The claim of transparent binding at SHL2 is based on MD simulations of a single modeled complex, with two 500 ns replicas. The P-RMSD values shown in Figure 1E indicate that the SHL2 nucleosome rarely samples the Sox-bound DNA conformation during the free nucleosome simulation, and the authors selected the "best-fitting" frame for modeling. This selection bias, combined with short simulation times, does not establish that SHL2 is intrinsically permissive for Sox binding. The interaction frequency data in Table S1 are presented as percentages without error bars or replicate-level breakdowns, making it impossible to assess variability.
- **Why it matters** The central conclusion of the paper, that SHL2 permits sequence-specific Sox binding in a solvent-facing orientation, rests on this simulation evidence. If the sampling is inadequate or the selection biased, the conclusion is not supported.
- **Resolution test** Provide replicate-level interaction frequency data with statistical comparisons, extend simulation times or show convergence of key metrics, and demonstrate that the "best-fitting" frame selection does not bias the subsequent binding analysis. Ideally, independent simulations starting from different initial conformations should be shown.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that hydroxyl radical footprinting confirms Sox binding at all three SHL positions, and that UV laser footprinting confirms shape reading at SHL2 and SHL4 but not at the dyad
- **Evidence pointer** Figure 3A, Figure 3B, Results section "Solvent-Facing Sox Binding Is Confirmed by the •OH Footprinting Experiments" and "UV Laser Footptinting Validates That DNA Shape Reading Is Realized at SHL2 and SHL4 but Not at the Dyad"
- **Concern** The footprinting data are presented as gel images with densitometric traces, but the protection at SHL2 and SHL4 in the nucleosome context is described as "not so well visible." The quantification shown in the insets is not described with statistical measures, and no replicate experiments are mentioned. The Kdapp values in Table 2 are derived from fits to a biexponential function, but the authors acknowledge that these are apparent values and that true Kd determination was precluded. The claim that identical footprinting profiles were observed for single-site constructs is stated but not shown.
- **Why it matters** The experimental data are intended to validate the computational predictions. If the footprinting protection is weak and not quantified with replicates, the validation is not convincing.
- **Resolution test** Show replicate footprinting experiments with quantified protection values and error estimates. Provide statistical comparison of protection at SHL2, SHL4, and dyad. Show the single-site construct data referenced in the text. Clarify how the Kdapp values were derived and whether the fits are robust.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model construction
- **Claim pointer** The authors constructed Sox-nucleosome models by inserting the Sox consensus sequence into the 601 nucleosome at three SHL positions and docking Sox11 onto the best-fitting frames
- **Evidence pointer** Methods section "Dynamic Integrative Modeling", Figure S2, Figure S11
- **Concern** The modeling procedure relies on selecting frames from free nucleosome simulations that best match the Sox-bound DNA conformation, then docking Sox11. This approach assumes that the nucleosome can adopt the Sox-bound conformation without Sox present, which is the very question under investigation. The authors do not provide validation of the resulting models, such as comparison to the experimental Sox-nucleosome structure (PDB 6T7A/6T7B) or assessment of steric clashes beyond the HADDOCK refinement. The use of a modified 601 sequence with three inserted Sox sites simultaneously may introduce artifacts.
- **Why it matters** The structural models are the basis for all interaction analyses. If the models are not validated or the construction procedure biases the outcomes, the conclusions about interaction profiles are unreliable.
- **Resolution test** Validate the models against known Sox-nucleosome structures where possible. Show that the inserted Sox sites do not perturb the overall nucleosome structure. Provide evidence that the docking procedure reproduces known Sox-DNA interactions in control cases.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The authors claim that SHL4 permits only shape reading and the dyad allows no reading mechanism, and that this is due to histone interactions
- **Evidence pointer** Figure 4, Table S2, Discussion section
- **Concern** The interpretation that SHL4 permits shape reading is based on the observation that the Sox-nucleosome complex at SHL4 shows some DNA deformation but loses base-specific contacts. However, the simulation data show that SHL4 rarely samples the Sox-bound conformation (Figure 2B), and the interaction analysis is based on a single modeled complex. The claim that histone interactions at SHL4 interfere with Sox binding is supported by analysis of contacts, but this is only shown for one simulation. The comparison to the dyad, where no reading is observed, is complicated by the fact that the dyad has the strongest histone-DNA interactions, making it difficult to separate the contributions of histone-DNA versus Sox-histone interactions.
- **Why it matters** The mechanistic interpretation of position-dependent Sox binding is a key contribution of the paper. If the underlying data are not robust, the interpretation is speculative.
- **Resolution test** Provide additional simulations or experimental data that directly test the role of histone interactions at SHL4 and the dyad. For example, simulations with histone tail truncations or mutations could support the proposed mechanism.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1E
- **Evidence pointer** Figure 1E
- **Issue** The P-RMSD distributions in Figure 1E are difficult to compare across conditions because the panel labels are small and the color scheme is not described in the legend.
- **Required correction** Increase font size of panel labels, add a clear legend describing each distribution, and consider using distinct line styles in addition to color for accessibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "MD Simulations of Sox:DNA Complex Reveals the Essential Protein–DNA Interaction Dynamics"
- **Evidence pointer** Methods section, Table S3
- **Issue** The equilibration times differ between systems (200 ns for most, 350 ns for free 601), but the rationale for this difference is not explained.
- **Required correction** Justify the different equilibration times or use consistent criteria for all systems.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** The Kdapp values are reported without confidence intervals or the number of independent experiments.
- **Required correction** Add confidence intervals and specify the number of replicates for each measurement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section, paragraph 3
- **Evidence pointer** Discussion section
- **Issue** The statement that "different HMG proteins could be able to efficiently bind in vivo to the dyad without requiring the presence of recognition" is speculative and goes beyond the data presented.
- **Required correction** Soften this claim or provide additional evidence to support it.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Sox6 HMG Domain Cloning and Purification"
- **Evidence pointer** Methods section
- **Issue** The purity of the Sox6 HMG domain is stated to be analyzed by SDS-PAGE, but no gel image or purity percentage is provided.
- **Required correction** Include a representative gel image or state the estimated purity.

## Risk / unsupported claims
- The claim that SHL2 acts "transparently" for Sox binding is not fully supported by the simulation data, which show limited sampling and potential selection bias
- The claim that identical footprinting profiles were observed for single-site constructs is stated but not shown
- The claim that different HMG proteins could bind to the dyad in vivo without sequence recognition is speculative
- The Kdapp values are acknowledged as apparent and not true dissociation constants, limiting their quantitative interpretation
- The transferability of findings from modified 601 sequences to natural nucleosomal sequences is acknowledged as unexplored