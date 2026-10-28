## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusions, and supplementary information descriptions
- **Assessment boundary** Scientific validity, methodological soundness, claim-evidence alignment, and clarity of the reported computational study on c-MYC conformational drugging pockets
- **Shared manuscript claim summary** The authors report that all-atom Molecular Dynamics and well-tempered Metadynamics simulations of a c-MYC motif in aqueous ionic solution reveal stable conformations with druggable pockets, that these pockets bind the known MYC inhibitor 10074-G5 with excellent electrostatic and docking complementarity, and that the inhibitor remains stably bound over 500 ns simulations, providing a structural basis for targeting c-MYC.
- **Visible evidence base** Abstract, Introduction, Methods (partial), Results and discussion sections, Conclusions, Data availability statement, Supplementary information descriptions
- **Missing materials affecting confidence** Full Methods section (only partial text provided), all figures and tables referenced but not visible, complete simulation parameters, force field validation details, docking protocol specifics, and the full supplementary information

## Reviewer
- **Overall assessment** The manuscript addresses a significant problem in cancer drug discovery, namely the identification of druggable pockets on the intrinsically disordered c-MYC oncoprotein. The combination of MD and WTM simulations to map the conformational landscape is a reasonable approach, and the identification of stable basins with potential drugging pockets is potentially interesting. However, the manuscript as presented has several critical weaknesses. The evidence base is incomplete, with all figures and tables absent from the provided material, making it impossible to verify the central claims. The description of the collective variables contains an apparent error (both CV1 and CV2 are described as "d1"), and the relationship between the simulated 82-residue motif and the full-length c-MYC protein is not adequately justified. The claim that the crystal structure is approximately 75 kJ/mol higher in free energy than the most stable basin is striking and would require rigorous validation, particularly given that the crystal structures were obtained in complex with MAX and DNA, not as isolated monomers. The docking and 500 ns MD validation of inhibitor binding is presented as preliminary but is used to support a strong conclusion about druggability. The manuscript would benefit from clearer articulation of the novelty relative to existing computational studies of MYC, and from a more careful discussion of the limitations of using a truncated motif.

- **Who would be interested in the results, and why** Computational biophysicists and structural biologists studying intrinsically disordered proteins, particularly those focused on conformational ensembles and free energy landscapes. Cancer researchers interested in direct targeting of MYC, especially those working on small-molecule inhibitors of transcription factors. Drug discovery scientists employing computational methods for target identification and validation on "undruggable" proteins. The methodological approach combining MD, WTM, and docking could also interest method developers in the enhanced sampling community.

- **Major strengths**
  1. The study addresses a clinically important and technically challenging target, namely the intrinsically disordered c-MYC oncoprotein, which is implicated in up to 70% of human cancers.
  2. The combination of unbiased MD and enhanced sampling WTM simulations is an appropriate and sophisticated approach for exploring conformational landscapes of disordered proteins.
  3. The authors demonstrate awareness of technical pitfalls in enhanced sampling, particularly the careful treatment of periodic boundary conditions in distance-based collective variables, which is a nontrivial methodological detail.
  4. The integration of multiple validation criteria for WTM convergence (hills evolution, cumulative free energy profiles, block analysis) reflects good scientific practice.
  5. The study goes beyond static structure prediction by validating candidate pockets through docking and subsequent MD simulation of inhibitor-bound complexes.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims identification of stable conformations with druggable pockets at the surface of c-MYC, supported by MD and WTM simulations, electrostatic calculations, and docking analyses.
- **Evidence pointer** All figures and tables referenced in the text (Figures 1-7, Tables 1-3) are not provided in the submitted material
- **Concern** The central claims of this manuscript cannot be evaluated without access to the figures and tables. The text refers to Figure 3 for cluster populations, Figure 4 for the 2D free energy surface, Figure 6 for electrostatic potential maps, Figure 7 for inhibitor binding stability, and Tables 1-3 for simulation parameters and free energy values. None of these are visible in the provided material. The reader cannot verify the existence of the claimed stable basins, the free energy differences, the electrostatic complementarity, or the stability of inhibitor binding. This is a fundamental barrier to assessment.
- **Why it matters** The entire scientific case rests on these visual and tabular data. Without them, the claims are unverifiable assertions. A reviewer cannot determine whether the conclusions follow from the data, whether the analysis is correct, or whether the interpretations are justified.
- **Resolution test** Provide all figures and tables with appropriate legends and axis labels. Ensure that the free energy surfaces are shown with clear contour levels, that cluster populations are quantified, that electrostatic maps are shown with appropriate scales, and that docking poses and MD trajectories are presented with sufficient detail for independent evaluation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The manuscript states that two collective variables were selected for WTM simulations, described as "the distance (d1) between the residue ASN907 within the alpha-helix close to the C-terminal of MYC and the residue HIS976 within the second alpha-helix, close to the N-terminal of MYC" and "the distance (d1) between residues LEU951 and LEU966, both located at the central part of the second alpha-helix of MYC."
- **Evidence pointer** Section "Collective Variables", paragraph 2
- **Concern** Both collective variables are labeled as "d1" in the text. This is either a typographical error or a fundamental confusion in the definition of the collective variables. If both CVs are indeed the same distance, the 2D free energy surface would be meaningless. If this is a typo, the correct labeling must be provided. Additionally, the residue numbering (ASN907, HIS976, LEU951, LEU966) does not correspond to the 82-residue sequence provided in the Methods section, which appears to be numbered from 1. The relationship between the residue numbers used in the CV definitions and the simulated sequence must be clarified.
- **Why it matters** The collective variables are the foundation of the WTM simulation. If they are incorrectly defined or described, the entire free energy surface and all subsequent analysis are called into question. The residue numbering discrepancy raises concerns about whether the correct sequence was simulated and whether the CVs are physically meaningful.
- **Resolution test** Correct the CV labeling to distinguish d1 and d2. Provide a clear mapping between the residue numbers used in the CV definitions and the sequence of the simulated construct. Clarify whether the residue numbers refer to the full-length c-MYC sequence or the truncated motif, and if the former, provide the correspondence explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript claims that "the selected energy-minimised structures exhibit stable conformations and drug pockets" and that "MYC maintained steady binding to 10074-G5 throughout the 500 ns simulation."
- **Evidence pointer** Section "Location of potential drugging pockets at the surface of MYC", Figure 7
- **Concern** The claim of stable drug pockets is based on the identification of stable basins in the free energy surface and subsequent docking and MD validation. However, the text also states that "state B tends to exhibit significant fluctuations, reflecting transient departures of the inhibitor from the center of mass of MYC followed by occasional returns on short timescales." This description suggests that the inhibitor does not maintain stable binding to state B, which is one of the three primary candidate states. The manuscript does not adequately address whether this instability undermines the claim of druggability for state B. Furthermore, the statement that "at least two drugging pockets reported in the present work are able to host this drug in a stable way" is based on only 500 ns of simulation, which is a relatively short timescale for assessing binding stability, particularly for a disordered protein.
- **Why it matters** The central translational claim of the manuscript is that stable druggable pockets exist on c-MYC. If one of the three primary candidate states shows unstable inhibitor binding, and if the stability assessment is based on a short simulation, the strength of the conclusion is weakened. The reader needs to understand the criteria for "stable binding" and whether 500 ns is sufficient to support the claim.
- **Resolution test** Provide quantitative measures of binding stability, such as root-mean-square deviation of the inhibitor within the pocket, contact persistence analysis, or binding free energy estimates from the MD trajectories. Discuss the timescale limitations explicitly and justify why 500 ns is sufficient to support the druggability claim. Address the apparent instability of state B directly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The manuscript states that "the selected energy-minimised structures exhibit stable conformations and drug pockets, providing structural foundations for targetting c-MYC" and concludes that these findings "provide a previously uncharacterized structural foundation for the design of innovative therapeutic interventions."
- **Evidence pointer** Abstract, Conclusions
- **Concern** The study simulates an 82-residue motif of c-MYC in isolation, in aqueous solution. The full-length c-MYC protein is approximately 439 residues and functions within the nucleus, where it interacts with MAX, DNA, and numerous cofactors. The relevance of conformations adopted by an isolated motif in solution to the biologically active states of c-MYC within the cellular environment is not adequately justified. The authors note that the crystal structures were obtained from MYC-MAX-DNA complexes, but the simulated construct is the isolated MYC motif. The manuscript does not discuss how the absence of MAX, DNA, and other interaction partners might affect the conformational landscape and the accessibility of the identified pockets.
- **Why it matters** The translational relevance of the findings depends on whether the identified pockets are accessible and druggable in the context of the full-length protein within cells. If the pockets are only present in the isolated motif and are occluded or absent in the biologically relevant complex, the therapeutic implications are limited.
- **Resolution test** Discuss the relationship between the simulated motif and the full-length protein, including whether the identified pockets are conserved in the full-length context. Address how the absence of binding partners might affect the conformational landscape. If possible, compare the identified pockets with known interaction interfaces or previously reported MYC structures.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and context
- **Claim pointer** The manuscript claims to provide "a previously uncharacterized structural foundation for the design of innovative therapeutic interventions" targeting c-MYC.
- **Evidence pointer** Introduction, Conclusions
- **Concern** The introduction mentions that MYC has been considered "undruggable" and that direct inhibitors have not been approved, but it does not provide a comprehensive review of prior computational or experimental efforts to identify druggable sites on MYC. The claim of "previously uncharacterized" structural foundations requires a clear statement of what is new relative to existing literature. Several studies have reported on MYC conformational dynamics, intrinsically disordered regions, and potential inhibitor binding sites. The manuscript should explicitly differentiate its findings from prior work.
- **Why it matters** The novelty claim is central to the manuscript's significance. Without a clear articulation of what is new, the contribution to the field is unclear. The reader cannot assess whether this work represents a genuine advance or an incremental addition to a crowded field.
- **Resolution test** Expand the introduction and discussion to include a systematic comparison with prior computational and experimental studies of MYC druggability. Explicitly state what new insights the current study provides beyond existing knowledge.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, last sentence
- **Evidence pointer** Abstract
- **Issue** The sentence "These findings provide a previously uncharacterized structural foundation for the design of innovative therapeutic interventions, such as small-molecule inhibitors or peptides aimed at disrupting oncogenic MYC activity" is somewhat redundant with the earlier statement about "providing structural foundations for targetting c-MYC." The abstract could be tightened to avoid repetition.
- **Required correction** Revise the abstract to remove redundancy and sharpen the final take-home message.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "One-dimensional free energy landscapes of MYC"
- **Evidence pointer** Section "One-dimensional free energy landscapes of MYC", paragraph 1
- **Issue** The text states that 1D free-energy profiles can be compared to "experimental binding free energies ΔG bind" but does not provide the actual comparison or discuss how such a comparison would be made. The reference to Jämbeck et al. is mentioned but the relevance is not explained.
- **Required correction** Either provide the comparison to experimental data or clarify that this is a methodological note for future work, not a result of the current study.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Location of potential drugging pockets at the surface of MYC"
- **Evidence pointer** Section "Location of potential drugging pockets at the surface of MYC", paragraph 1
- **Issue** The text mentions "Fig. ?? in SI" when referring to the stability of higher-energy minima. This placeholder reference should be corrected to the actual figure number.
- **Required correction** Replace "Fig. ??" with the correct figure reference.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section "Two-dimensional free energy landscapes of MYC"
- **Evidence pointer** Section "Two-dimensional free energy landscapes of MYC", paragraph 1
- **Issue** The text states "we can distinguish several deep basins located around values of d1 between 0.79 and 2.17 nm and distances d2 between 1.08 and 3.90 nm" but Table 2 is not visible. The reader cannot verify these values or understand the relationship between the basins and the collective variable ranges.
- **Required correction** Ensure Table 2 is provided and that the text clearly references the table for the basin coordinates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Section "Location of potential drugging pockets at the surface of MYC", last paragraph
- **Evidence pointer** Section "Location of potential drugging pockets at the surface of MYC", last paragraph
- **Issue** The sentence "Furthermore, It highlights the pivotal role of conformational dynamics in the evaluation of poorly druggable targets" has an unnecessary capital "I" in "It" and could be rephrased for clarity.
- **Required correction** Correct the capitalization and rephrase for smoother reading.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section "Location of potential drugging pockets at the surface of MYC", paragraph 1
- **Evidence pointer** Section "Location of potential drugging pockets at the surface of MYC", paragraph 1
- **Issue** The text mentions "Autodock Vina" with a citation placeholder "? ?" and also "10074-G5" with a citation placeholder "67 ?". These should be properly cited.
- **Required correction** Complete all citation placeholders with appropriate references.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section "Stable structures from Principal Component Analysis"
- **Evidence pointer** Section "Stable structures from Principal Component Analysis", paragraph 1
- **Issue** The text states that "structure '4' is clearly the most populated of the ten detected ones" and that five structures are "qualitatively different of the CS of c-MYC published at RCSB PDB, more similar to structures '6', '10' and '3'". Without Figure 3, it is difficult to understand the structural differences being described. The text would benefit from a more explicit description of the structural features that distinguish these clusters.
- **Required correction** Provide a more detailed textual description of the structural characteristics of the identified clusters, independent of the figure.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Section "System preparation and setups"
- **Evidence pointer** Section "System preparation and setups", paragraph 1
- **Issue** The text states that "three long 3 µs simulations and three replicas of length 2 µs" were performed, but the total simulation time is not clearly stated. The text also mentions that "MD trajectories were used to feed the initial configurations of the WTM runs" but does not specify how many WTM simulations were performed or their total length.
- **Required correction** Clarify the total simulation time for both MD and WTM runs, and specify the number of independent WTM simulations performed.

## Risk / unsupported claims
1. The claim that the crystal structure of c-MYC is approximately 75 kJ/mol higher in free energy than the most stable basin (state A) is unsupported without the free energy surface figure and the methodology for calculating this difference.
2. The claim that "the selected energy-minimised structures exhibit stable conformations and drug pockets" is unverifiable without the structural figures and cluster analysis data.
3. The claim that "MYC maintained steady binding to 10074-G5 throughout the 500 ns simulation" is unverifiable without the time-dependent distance plots shown in Figure 7.
4. The claim that the identified pockets represent "previously uncharacterized" druggable sites is unsupported without a comprehensive literature comparison.
5. The claim that electrostatic potential differences of approximately 2 kBT/e (approximately 53 mV) indicate druggability is not adequately justified, as the relationship between surface electrostatics and druggability is not established in the text.
6. The statement that "molecules with scores below −7.0 kcal/mol are generally considered to possess strong binding potential" is presented as a general criterion but is not referenced, and the docking scores for states A-G are not provided in the visible material.
7. The relevance of the simulated 82-residue motif to the full-length c-MYC protein in its biological context is asserted but not demonstrated, making the translational claims unsupported.