## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, acknowledgments) from bioRxiv preprint
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors propose a novel RNA-mediated mechanism for DNA melting in CRISPR-Cas9, based on long-timescale molecular dynamics simulations and supporting biochemical/cell-based experiments. They report that sgRNA can intercalate into dsDNA via Mg²⁺-mediated interactions, promote local base-pair breaks, and that unidirectional RNA-DNA hybrid formation initiates from the PAM +1 position, with an apparent proofreading mechanism involving Cas9 conformational dynamics.
- **Visible evidence base** Simulation results (free-binding, PAM-restrained, and enhanced sampling runs), cell-based editing assays with SpCas9 variants, differential scanning fluorimetry melting experiments, and Boltz-1 structure predictions
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; Table 1 and Table 2 (sequence information) not provided; Supplementary Discussion not provided; Supplementary Videos not provided; full Methods details for TSS implementation partially described but validation metrics not shown

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental and timely question in CRISPR biology: the atomic-level mechanism of DNA melting preceding R-loop formation. The authors combine state-of-the-art long-timescale MD simulations with experimental validation, which is a powerful approach. The central claim, that sgRNA directly participates in DNA melting via base intercalation, is novel and potentially significant. However, the evidence as presented has several critical gaps. The simulation evidence for the proposed mechanism is based on a small number of observed events (5 of 20 simulations for intercalation), and the enhanced sampling protocol's validity for the specific conclusions drawn is not fully established. The experimental support is indirect, and the connection between the proposed mechanism and the observed mutational effects on editing efficiency is not rigorously demonstrated. The manuscript would benefit from clearer presentation of the simulation statistics, convergence assessments, and a more direct experimental test of the proposed RNA-intercalation mechanism.
- **Who would be interested in the results, and why** Researchers in CRISPR biology, genome editing, nucleic acid biophysics, and molecular dynamics simulation communities. The proposed mechanism has implications for understanding Cas9 function, engineering improved Cas9 variants, and potentially for other Cas proteins. The methodological approach (long-timescale MD with enhanced sampling) will interest computational biologists.
- **Major strengths** 1) Addresses a fundamental, unresolved question in CRISPR biology with a plausible and novel mechanistic hypothesis. 2) Combines multiple complementary approaches (simulation, cell-based assays, biophysical measurements). 3) Uses state-of-the-art long-timescale MD simulations on Anton hardware, which is a significant technical achievement. 4) The observation of Mg²⁺-mediated RNA-DNA interactions is unexpected and could have broad implications. 5) The proposed proofreading mechanism is an interesting and testable hypothesis.
- **Major Concerns**
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "sgRNA entered into Mg²⁺-mediated interactions with the DNA, allowing sgRNA bases to intercalate into the DNA and induce local and reversible DNA base-pair breaks" (Abstract); "we observed a direct role for the RNA in facilitating DNA melting events through a mechanism in which RNA bases intercalated within the DNA and promoted strand separation" (Abstract)
- **Evidence pointer** Results section "In simulations, sgRNA interacts with dsDNA through Mg²⁺-mediated interactions and promotes transient dsDNA base-pair breaks"; Figure 2
- **Concern** The central mechanistic claim rests on observations from 5 of 20 simulations (4 for SpCas9, 1 for SaCas9). This is a low frequency of occurrence, and the manuscript does not provide sufficient statistical analysis or convergence assessment to establish that these events are representative of the mechanism rather than rare, potentially non-physiological fluctuations. The authors state that "individual sgRNA nucleotides flip from their original REC-domain-facing positions" but do not provide quantitative details on the free energy landscape, the residence times of intercalated states, or whether these events would be observed with different force fields or starting conditions. The claim that this is a "mechanism" requires more than anecdotal observation of a few events.
- **Why it matters** The entire paper's novelty and significance hinge on this proposed RNA-mediated melting mechanism. If the intercalation events are rare artifacts of the simulation setup or force field, the central conclusion is unsupported. The current evidence does not convincingly establish that this is a dominant or even significant pathway for DNA melting in Cas9.
- **Resolution test** Provide a quantitative analysis of the intercalation events: frequency of occurrence across all simulations, free energy profiles for base flipping and intercalation, comparison with control simulations (e.g., without Mg²⁺, with mutated RNA bases), and convergence assessments. Demonstrate that the observed events are statistically significant and robust to simulation parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of enhanced sampling approach
- **Claim pointer** "Using this enhanced sampling protocol, we initiated 30 simulations... In the tempering simulations, we observed various partially and reversibly melted dsDNA structures" and "we identified six simulations... in which at least three in-register tsDNA-sgRNA base pairs were formed starting at PAM +1"
- **Evidence pointer** Results section "In simulations, unidirectional, sequential DNA-DNA hybrid formation initiates from partially melted dsDNA structures at the PAM +1 position"; Methods section "Simulation details"
- **Concern** The enhanced sampling protocol (Times Square sampling) is used to temper interactions between DNA strands, but the manuscript does not provide sufficient validation that this approach preserves the correct physics for the specific question of RNA-DNA hybrid formation. The authors state that "the overall shape of the histograms of first base-pair break events under TSS resembles what we observed in general non-tempering simulations," but this is a qualitative comparison. There is no demonstration that the TSS approach correctly samples the free energy landscape for hybrid formation, nor is there a discussion of potential artifacts introduced by tempering DNA-DNA interactions while leaving RNA-DNA interactions unchanged. The observation of hybrid formation in only 6 of 30 simulations, with progression only to +3 or +4, raises questions about whether the full mechanism is being captured.
- **Why it matters** The conclusions about the sequence and directionality of hybrid formation, and the proposed proofreading mechanism, depend critically on the validity of the enhanced sampling simulations. If the TSS approach biases the system toward certain pathways or fails to capture relevant states, the mechanistic conclusions could be incorrect.
- **Resolution test** Provide validation of the TSS approach for this system: comparison with long unbiased simulations for at least one case, calculation of free energy profiles for hybrid formation, demonstration that the observed pathways are independent of the TSS parameters (e.g., λ_min values), and a discussion of potential artifacts.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental support for proposed mechanism
- **Claim pointer** "mutation of certain residues that mediated DNA binding in our simulations impacted editing efficiency in our cell-based assays" and "we found experimental evidence that an ssRNA, in the absence of Cas9, can significantly lower the melting temperature of dsDNA"
- **Evidence pointer** Results sections "Mutation of residues that mediated the bent DNA-Cas9 encounter complexes in simulations altered SpCas9 editing efficiency in cells" and "In simulations, an ssRNA promotes dsDNA separation in simulations and alters the melting profile of dsDNA in biophysical experiments"; Figures 1E, 1F, 3B-D
- **Concern** The experimental data provide only indirect support for the proposed mechanism. The mutational analysis identifies residues important for editing but does not directly test whether the RNA-intercalation mechanism is responsible for the observed effects. The DSF experiments show that ssRNA can lower the melting temperature of dsDNA, but this is a bulk equilibrium measurement that does not demonstrate the specific intercalation mechanism proposed. The connection between the simulation-observed intercalation events and the experimental observations is correlative, not causal. Additionally, the DSF experiments use a 21-base ssRNA that is complementary to the target sequence, which could promote DNA melting through simple strand invasion rather than the specific intercalation mechanism proposed.
- **Why it matters** The manuscript claims "supporting experimental work" for the simulation findings, but the experimental evidence does not specifically validate the RNA-intercalation mechanism. Stronger experimental support would significantly strengthen the paper's conclusions.
- **Resolution test** Design experiments that directly test the proposed mechanism, such as: (1) mutations in the sgRNA that specifically disrupt the intercalation capability while maintaining complementarity, (2) single-molecule FRET or optical tweezers experiments to directly observe RNA-induced DNA melting, (3) structural studies (e.g., cryo-EM) of the encounter complex capturing the intercalated state.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed mechanism
- **Claim pointer** "suggest a novel RNA-dependent mechanism for DNA melting that may be conserved in other Cas proteins" (Abstract); "Binding of dsDNA in the interlobe space, where the DNA is adjacent to the sgRNA, could thus be a common feature of Cas-dsDNA encounter complexes formed across the entire Cas family of enzymes" (Discussion)
- **Evidence pointer** Discussion section
- **Concern** The claim of conservation across Cas proteins is speculative and not supported by direct evidence. The authors only studied SpCas9 and SaCas9, which are both Class 2 Type II systems. The structural arguments for conservation are based on the interlobe architecture, but the authors themselves note that SaCas9 lacks a REC2 domain, indicating structural diversity within the family. The extension to Cas12 and Cascade is based on structural similarity of the binding cleft, but the functional significance of this similarity for the proposed RNA-intercalation mechanism is not established.
- **Why it matters** The broader significance of the work depends on whether the mechanism is general or specific to certain Cas9 variants. Overclaiming conservation could mislead the field.
- **Resolution test** Either provide additional simulations or experiments with other Cas proteins (e.g., Cas12) to test the mechanism's generality, or temper the claims to be specific to the studied systems.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** "we applied a distance restraint to maintain the PAM sequences in close proximity (<5 Å) to the corresponding arginine residues in the PI domain" and "The initial conformations in our simulations of SpCas9-sgRNA were built from a crystal structure of the pre-target protein-sgRNA complex (PDB ID 4ZT0)"
- **Evidence pointer** Methods section "Structure preparation" and "Simulation details"
- **Concern** The Methods section lacks sufficient detail for reproducibility. Key parameters are not specified: the exact restraint force constants, the criteria for selecting "representative" encounter complexes for subsequent simulations, the number of simulations that were discarded or failed, and the specific analysis protocols for defining "base-pair breaks" and "hybrid formation." The description of the TSS implementation is incomplete, and the manuscript does not provide the input files or a clear description of the simulation workflow that would allow others to reproduce the results.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without sufficient methodological detail, the results cannot be independently verified, which undermines confidence in the conclusions.
- **Resolution test** Provide a complete description of all simulation parameters, analysis protocols, and the TSS implementation. Make input files and analysis scripts available. Include a detailed workflow diagram.

- **Minor Comments**
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1B
- **Evidence pointer** Results section "Cas9 binds and bends linear dsDNA in the cleft between the REC lobe and NUC lobes"
- **Issue** The description of the "number of protein residues contacting the DNA" as a metric for encounter complex stability is not well-defined. The threshold for "contact" (3.5 Å) is stated, but the time-dependence of this metric and how it was used to identify "stable" complexes is unclear.
- **Required correction** Clarify the analysis protocol for the contact metric, including how stability was defined and how representative structures were selected.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Cell-based editing assay results
- **Evidence pointer** Results section "Mutation of residues that mediated the bent DNA-Cas9 encounter complexes in simulations altered SpCas9 editing efficiency in cells"; Figure 1E-F
- **Issue** The editing efficiency data are presented as mean ± standard deviation from three independent experiments, but the number of biological replicates and the statistical tests used are not specified. The significance of the differences between mutants and WT is not quantified.
- **Required correction** Provide details on the number of replicates, the statistical tests used, and the p-values for the reported differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of DSF data
- **Affected element** Figure 3B-D
- **Evidence pointer** Results section "An ssRNA promotes dsDNA separation in simulations and alters the melting profile of dsDNA in biophysical experiments"
- **Issue** The DSF experiments show a decrease in T_m in the presence of ssRNA, but the interpretation that this reflects RNA-mediated DNA melting is not the only possible explanation. The ssRNA could also affect the fluorescence signal through other mechanisms (e.g., by binding to the dye or altering the buffer conditions).
- **Required correction** Include appropriate control experiments (e.g., with non-complementary ssRNA, with dye alone) and discuss alternative interpretations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The manuscript does not adequately discuss the limitations of the simulation approach, particularly the use of a single force field (DES-Amber 3.20) and the potential force field artifacts in studying nucleic acid dynamics.
- **Required correction** Add a paragraph discussing the limitations of the computational approach and the potential impact of force field choice on the conclusions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction and Discussion sections
- **Issue** The manuscript does not cite or discuss recent experimental work on Cas9 DNA melting mechanisms, particularly single-molecule studies that have probed the kinetics and thermodynamics of R-loop formation. This limits the context for the proposed mechanism.
- **Required correction** Add citations to relevant recent experimental studies and discuss how the proposed mechanism relates to or extends these findings.

- **Technical failings that need to be addressed before the case is established** R1-M1 (insufficient evidence for central claim), R1-M2 (inadequate validation of enhanced sampling), R1-M5 (insufficient methodological detail for reproducibility)
- **Assessment against Nature-style criteria** 
  - Originality: The proposed RNA-mediated DNA melting mechanism is novel and challenges the prevailing view that DNA melting in Cas9 is primarily driven by protein-induced strain and base-flipping. The idea that the guide RNA itself participates in melting via intercalation is creative and unexpected. However, the originality is tempered by the limited direct evidence presented.
  - Scientific importance: If the mechanism is correct, it would have significant implications for understanding Cas9 function, engineering improved variants, and potentially for other CRISPR systems. The work addresses a fundamental question in the field. However, the importance is currently not fully established given the evidence gaps.
  - Interdisciplinary readership: The topic is of interest to CRISPR biologists, genome editing researchers, biophysicists, and computational biologists. The findings could have broad appeal, but the presentation is heavily simulation-focused, which may limit accessibility to experimental biologists.
  - Technical soundness: The use of long-timescale MD simulations on Anton is technically impressive. However, the validation of the enhanced sampling approach is insufficient, and the statistical analysis of the key events is lacking. The experimental support is indirect. Technical soundness is currently not fully established.
  - Readability for nonspecialists: The manuscript is generally well-written and the logic is clear. However, the Methods section is dense and assumes significant expertise in MD simulations. The abstract and introduction are accessible, but the results section may be challenging for non-specialists.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a novel and potentially important hypothesis, but the central claim is not sufficiently supported by the evidence as presented. The simulation evidence is based on a small number of events without adequate statistical analysis, the enhanced sampling approach lacks validation, and the experimental support is indirect. Major revisions are required to address these concerns before the case for the proposed mechanism can be considered established.

## Risk / unsupported claims
- The claim that "sgRNA has a direct role in DNA melting" is not fully supported; the simulation evidence is based on 5 of 20 simulations, and the experimental data do not directly test this mechanism.
- The claim that the mechanism "may be conserved in other Cas proteins" is speculative and not supported by direct evidence.
- The claim of a "proofreading mechanism" based on the closed-to-open conformational transition is an interesting hypothesis but is not directly tested.
- The claim that "the simulations provide the first dynamic view of Cas9-mediated heteroduplex formation at the atomic level" is difficult to verify without a comprehensive literature review.
- The quantitative details of the TSS-enhanced sampling (e.g., free energy estimates, convergence metrics) are not provided, making the validity of the approach unassessable.
- The connection between the specific residues mutated in the cell-based assays and the proposed RNA-intercalation mechanism is not established.