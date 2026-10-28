## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, technical soundness, structural biology claims, functional validation, and consistency with existing literature
- **Shared manuscript claim summary** The authors present cryo-EM structures of RAD51 mini-filaments bound to homologous dsDNA, capturing five intermediates from dsDNA recruitment to D-loop formation. They propose a stepwise mechanism where the N-terminal domain (NTD) recruits and bends dsDNA, loop L2 and Arg303-Arg306 further bend and open the duplex, and hydrophobic residues insert between strands while S2 sites capture the displaced strand. Molecular dynamics simulations support this model, and mutagenesis experiments validate functional roles of key residues.
- **Visible evidence base** Cryo-EM density maps and atomic models at resolutions of 2.91-4.53 Å, MD simulation trajectories, EMSA and strand exchange activity assays, sequence alignments referenced in supplementary figures
- **Missing materials affecting confidence** Supplementary figures and tables (Supplementary Figs. 1-17, Supplementary Tables 1-3), source data files, Supplementary Movies 1-2, and validation statistics (Table S2, S3) were not provided for review

## Reviewer

- **Overall assessment** This manuscript presents a significant structural biology advance in understanding eukaryotic RAD51-mediated strand exchange. The use of a mini-filament system to capture multiple D-loop intermediates by single-particle cryo-EM is innovative and addresses a key limitation of helical reconstruction approaches. The proposed mechanism, involving NTD-mediated dsDNA recruitment and bending, followed by loop L2 insertion and S2 site capture of the displaced strand, is plausible and well-supported by the presented structures and MD simulations. However, several technical concerns regarding the use of the SEAD mutant, the interpretation of partially mismatched substrates, and the resolution of key functional regions require careful consideration. The functional validation is somewhat limited, and the relationship between the mini-filament structures and full-length filament behavior needs further discussion. Overall, this is a strong contribution with the potential for high impact, but the technical concerns must be addressed to fully establish the case.

- **Who would be interested in the results, and why** Structural biologists studying homologous recombination and DNA repair mechanisms would be the primary audience. Researchers working on RAD51, RecA, and related recombinases will find the mechanistic insights directly relevant. The work also has implications for understanding genome stability, cancer biology, and the development of RAD51 inhibitors as therapeutic agents. The methodological approach of using mini-filaments for cryo-EM may interest structural biologists facing similar challenges with filamentous protein-DNA complexes.

- **Major strengths** 
  1. The mini-filament approach is a creative solution to the challenge of studying D-loop structures by cryo-EM, avoiding the limitations of helical symmetry averaging.
  2. Capturing five distinct intermediates provides a temporal sequence of structural states along the strand exchange pathway.
  3. The combination of cryo-EM with MD simulations offers complementary perspectives on the dynamic process of dsDNA bending and base-pair opening.
  4. The proposed mechanism integrates multiple structural features (NTD, loop L2, S2 site) into a coherent model with testable predictions.
  5. The comparison with RecA mechanisms highlights both conserved and divergent features of eukaryotic RAD51.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that RAD51-SEAD mini-filaments "resemble RAD51 filaments" and that this mutant retains wild-type activity, justifying its use for structural studies.
- **Evidence pointer** Results section "RAD51-SEAD mini-filaments resemble RAD51 filaments"; Fig. 1b
- **Concern** The manuscript relies on the SEAD mutant (S208E/A209D) to generate mini-filaments, but the validation of this mutant as a faithful model for wild-type RAD51 is limited. While the authors state that SEAD retains comparable strand exchange activity (Fig. 1b), the structural comparison with wild-type filaments is based on RMSD values of 0.93-1.04 Å, which, while small, may not capture functionally relevant conformational differences. The S208E/A209D mutations are in the BRC4 interaction region, and it is unclear whether these mutations could subtly alter DNA binding or filament dynamics in ways that affect the strand exchange mechanism. The authors should provide a more thorough structural comparison with wild-type RAD51 filaments, including analysis of the active site geometry and DNA binding interactions.
- **Why it matters** If the SEAD mutant does not faithfully recapitulate wild-type RAD51 behavior, all structural conclusions drawn from these mini-filaments may not be directly applicable to the native system. This is a foundational concern that affects the interpretation of all subsequent results.
- **Resolution test** Provide a more detailed structural comparison between SEAD mini-filaments and wild-type RAD51 filaments, including superposition of active site residues, analysis of DNA binding mode, and functional assays that directly compare strand exchange kinetics and processivity between SEAD and wild-type RAD51.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the five cryo-EM structures represent "five intermediates from dsDNA recruitment to D-loop formation" along the strand exchange pathway.
- **Evidence pointer** Results section "Partially-mismatched ssDNA/dsDNA trap RAD51 mini-filaments at different conformational states"; Fig. 2
- **Concern** The use of partially mismatched dsDNA substrates to trap intermediates is a clever strategy, but the interpretation that these represent sequential intermediates along a single pathway requires careful justification. The five structures were obtained using different substrates with different mismatch positions and lengths. It is not clear whether these represent true sequential states of the same reaction or distinct states that may not be on a linear pathway. The authors should provide evidence that these states are kinetically or thermodynamically connected, perhaps through additional time-resolved experiments or by demonstrating that the structural changes are monotonic along a plausible reaction coordinate.
- **Why it matters** The central claim of the paper is that these structures reveal the mechanism of strand exchange. If the intermediates are not sequentially related, the proposed mechanism may not accurately reflect the actual reaction pathway.
- **Resolution test** Provide additional experimental evidence supporting the sequential relationship between the five intermediates, such as time-resolved experiments, single-molecule studies, or a more detailed analysis of how the structural changes correlate with the position of the mismatch relative to the strand exchange site.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations "suggest a stepwise mechanism" and provide "structural snapshots of D-loop initiation and propagation."
- **Evidence pointer** Results section "Molecular dynamics simulation for base pair break"; Figs. 4-5
- **Concern** The MD simulations are relatively short (48 ns and 180 ns) and may not be sufficient to capture the full conformational landscape of the strand exchange process. The simulations start from specific structural models and may be biased by the initial conditions. The authors should provide more details on the convergence of the simulations, the number of replicates, and the statistical significance of the observed base-pair opening events. Additionally, the force field parameters for the non-hydrolyzable ATP analog (AMP-PNP) and the DNA modifications should be validated.
- **Why it matters** The MD simulations are used to support the mechanistic model derived from the cryo-EM structures. If the simulations are not well-converged or are biased, the conclusions drawn from them may not be reliable.
- **Resolution test** Provide evidence of simulation convergence (e.g., RMSD plots, multiple independent runs), validate force field parameters, and perform additional control simulations to ensure the observed base-pair opening is not an artifact of the simulation setup.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "the conserved N-terminal domain (NTD) recruits and bends the dsDNA, weakening base pairing near the exchange site" and that this is a key mechanistic insight.
- **Evidence pointer** Results section "Structural basis of D-loop formation by RAD51"; Fig. 3
- **Concern** The functional validation of the proposed mechanism is limited. The authors test three mutants (P83G, K284A, R306A) in strand exchange assays, but the effects are modest (approximately 50% reduction) and the interpretation is complicated by the fact that these mutations also affect ssDNA binding affinity (Fig. 6a). The authors should provide more direct evidence that the NTD, loop L2, and Arg303-Arg306 region specifically contribute to dsDNA bending and base-pair opening, rather than having a general effect on filament stability or DNA binding.
- **Why it matters** The functional validation is critical to support the mechanistic model. If the mutants have pleiotropic effects, the specific roles of these regions in strand exchange cannot be clearly established.
- **Resolution test** Design more specific mutants that disrupt dsDNA binding or bending without affecting ssDNA binding, or use biochemical assays that directly measure dsDNA bending and base-pair opening (e.g., FRET-based assays, DNA footprinting).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the 8-nt microhomology tract is the minimal unit required for stable D-loop formation, based on their structural analysis.
- **Evidence pointer** Results section "Structural basis of RAD51 D-loop formation and pairing propagation"; Supplementary Fig. 13
- **Concern** The claim that 8-nt is the minimal microhomology required for stable D-loop formation is based on a single cryo-EM reconstruction with a 7-bp tract that failed to form a stable heteroduplex. This is a limited dataset to support such a general conclusion. The authors should provide more systematic evidence, such as a series of constructs with varying microhomology lengths and quantitative measurements of D-loop stability.
- **Why it matters** This claim has implications for understanding the requirements for homologous recombination in vivo. If the conclusion is based on limited data, it may not be generalizable.
- **Resolution test** Perform a systematic analysis of D-loop formation with varying microhomology lengths (e.g., 5, 6, 7, 8, 9, 10 bp) using biochemical assays and/or additional cryo-EM structures.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that strand exchange occurs "in an ATP hydrolysis-independent manner," but this is not clearly explained in the main text. The role of ATP binding versus hydrolysis in the strand exchange mechanism should be clarified.
- **Required correction** Add a brief explanation in the introduction or results about the ATP-dependence of the strand exchange reaction and how the presented structures relate to the ATP-bound state.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods
- **Evidence pointer** Methods section "Cryo-EM sample preparation and data acquisition"
- **Issue** The manuscript mentions that the SEAD mutant was used to avoid the formation of extended filaments, but the rationale for why this mutant forms mini-filaments is not fully explained. The authors should provide more detail on the biochemical characterization of the SEAD mutant, including any biophysical characterization of filament length distribution.
- **Required correction** Add a brief discussion of the mechanism by which the S208E/A209D mutations promote mini-filament formation, and provide data on the size distribution of the mini-filaments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Structural basis of D-loop formation by RAD51"
- **Evidence pointer** Fig. 3
- **Issue** The description of the base-pair triplet nomenclature (e.g., "5'-1-1/3-3'") is confusing and not clearly defined in the text or figure legends.
- **Required correction** Provide a clear definition of the triplet nomenclature and a schematic diagram explaining how the triplets are counted and labeled.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "Functional analysis of structure-based mutants"
- **Evidence pointer** Fig. 6
- **Issue** The strand exchange assays for the mutants are performed at two protein concentrations, but the statistical analysis is not described. It is unclear whether the observed differences between wild-type and mutants are statistically significant.
- **Required correction** Provide statistical analysis of the strand exchange data, including the number of replicates and appropriate statistical tests.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the polarity of strand exchange (3' to 5' relative to the invading ssDNA) is brief and would benefit from a more detailed explanation of how this was determined and its implications.
- **Required correction** Expand the discussion of polarity determination, including a clear description of how the cryo-EM structures were used to establish the directionality of strand exchange.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Molecular dynamics simulations"
- **Evidence pointer** Methods section
- **Issue** The MD simulation methods lack details on the equilibration protocol, the number of replicates, and the criteria used to determine when the simulations were considered converged.
- **Required correction** Provide a more detailed description of the MD simulation protocol, including the number of replicates, the equilibration time, and the convergence criteria.

## Risk / unsupported claims
- The claim that the five cryo-EM structures represent sequential intermediates along a single strand exchange pathway is not fully supported by the data, as the structures were obtained using different substrates and may not be kinetically or thermodynamically connected.
- The claim that the 8-nt microhomology is the minimal unit required for stable D-loop formation is based on limited data (a single 7-bp construct) and requires more systematic validation.
- The functional significance of the NTD, loop L2, and Arg303-Arg306 region in dsDNA bending and base-pair opening is supported by mutagenesis, but the mutants also affect ssDNA binding, making it difficult to attribute the observed phenotypes specifically to defects in dsDNA manipulation.
- The MD simulation results are used to support the mechanistic model, but the simulations are relatively short and may not be fully converged, limiting the strength of the conclusions drawn from them.
- The comparison with the recently published human RAD51 D-loop structure by Joudeh et al. is mentioned but not discussed in detail; the authors should provide a more thorough comparison to address the apparent discrepancy in polarity determination.