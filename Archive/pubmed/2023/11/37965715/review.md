## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full methods, figures, or supplementary data
- **Shared manuscript claim summary** The authors use molecular dynamics simulations of MazE7, MazF7, MazEF7, MazEF7-DNA, and MazE7-DNA complexes to show that the MazE7 antitoxin dimer is disordered, that one monomer is stabilized by toxin binding, that both monomers are stabilized by DNA binding, that MazE7 sterically inhibits tRNA binding to MazF7, and that the MazEF7-DNA mechanism resembles AtaRT from E. coli. They hypothesize that disordered antitoxins enable tighter toxin and DNA binding to prevent accidental toxin activation.
- **Visible evidence base** Abstract text only. No figures, tables, methods, simulation parameters, or structural coordinates are provided.
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, structural figures, quantitative stability metrics (RMSD, RMSF, binding free energies), and comparative analysis details are not available.

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting computational study of a toxin-antitoxin system in Mycobacterium tuberculosis. The central claims regarding conformational stabilization of MazE7 upon toxin and DNA binding are consistent with known trends in TA systems, but the abstract provides no quantitative evidence to support these assertions. The comparative claim with AtaRT is intriguing but cannot be evaluated without structural alignments or interaction analyses. The steric inhibition claim regarding tRNA is particularly under-supported. The hypothesis about disordered antitoxins is speculative and presented without mechanistic detail. The work may be of interest to the TA and structural biology communities, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Researchers studying toxin-antitoxin systems, bacterial persistence, Mycobacterium tuberculosis biology, and intrinsically disordered proteins. The comparative analysis with AtaRT may interest those working on TA system evolution and functional conservation. The potential therapeutic angle for targeting TA systems in tuberculosis could attract drug discovery groups.
- **Major strengths** The study addresses a relevant biological question with potential clinical implications. The use of multiple simulation systems (five complexes) suggests a systematic approach. The comparative analysis with another TA system adds a broader perspective. The hypothesis regarding disordered antitoxins is conceptually interesting and testable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The absence of any quantitative simulation data in the abstract means that the central claims regarding stability changes cannot be verified. The steric inhibition claim requires direct evidence of a binding interface. The comparative claim with AtaRT requires structural or dynamic evidence of mechanistic similarity.
- **Assessment against Nature-style criteria** Originality: moderate, as MD studies of TA systems exist, though the specific focus on MazE7 conformational dynamics may be novel. Scientific importance: potentially relevant to understanding persistence in Mtb, but the abstract does not establish translational significance. Interdisciplinary readership: limited, as the abstract is written for a specialist structural biology audience. Technical soundness: cannot be assessed from the abstract alone. Readability for nonspecialists: the abstract assumes familiarity with TA systems and MD terminology, limiting broader accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible narrative but lacks the quantitative and methodological detail required to assess the validity of the claims. A full manuscript with simulation data would be needed to evaluate the work properly.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that the MazE7 dimer is disordered and that one monomer (Chain C) attains stability after binding to MazF7, while both monomers are stabilized upon DNA binding.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract states these stability changes as findings but provides no quantitative metrics such as RMSD, RMSF, radius of gyration, or binding free energies. No simulation lengths, force fields, or convergence criteria are mentioned. Without these data, the claim of differential stabilization cannot be evaluated.
- **Why it matters** The central thesis of the paper rests on the differential stability of MazE7 monomers under different binding conditions. If the simulation data do not robustly support these differences, the entire narrative collapses.
- **Resolution test** Provide quantitative stability metrics for each complex, including error bars or replicate analysis, and demonstrate that the observed differences are statistically significant and converged.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The claim that MazE7 sterically inhibits tRNA from binding to MazF7.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract asserts steric inhibition of tRNA binding without describing any simulation of a MazEF7-tRNA complex or any binding free energy calculation. The mechanism of steric inhibition is not explained, and no structural evidence is presented.
- **Why it matters** This is a functional claim with potential biological significance. If unsupported, it overstates the findings and could mislead readers about the mechanism of toxin neutralization.
- **Resolution test** Provide simulation data of a ternary complex or binding calculations showing that MazE7 occupancy on MazF7 prevents tRNA access, with structural analysis of the putative steric clash.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative validity
- **Claim pointer** The claim that the MazEF7-DNA mechanism is similar to AtaRT from E. coli, based on comparative structural analysis and simulations of AtaR, AtaT, AtaRT, AtaRT-DNA, and AtaR-DNA.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract states that the mechanism is similar but provides no details on the comparison. No structural alignments, interaction fingerprints, or dynamic correlation analyses are described. The basis for claiming mechanistic similarity is unclear.
- **Why it matters** The comparative claim extends the study's relevance beyond a single system. If the comparison is superficial, the claim of mechanistic conservation is overstated.
- **Resolution test** Provide quantitative comparison metrics such as structural superposition RMSD, contact maps, or principal component analysis showing that the DNA binding modes and conformational changes are indeed similar.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Hypothesis support
- **Claim pointer** The hypothesis that disordered antitoxins enable tighter toxin and DNA binding, thus preventing accidental toxin activation.
- **Evidence pointer** Abstract only, location not provided
- **Concern** This hypothesis is presented as a conclusion but is not directly tested. The abstract does not describe any experiments or simulations that compare ordered versus disordered antitoxins or that measure binding affinities in a way that would support this claim.
- **Why it matters** The hypothesis is the conceptual take-home message of the study. If it is not supported by direct evidence, it should be framed as speculation rather than a finding.
- **Resolution test** Provide comparative binding free energy calculations or experimental binding data for disordered versus ordered antitoxin variants, or clearly reframe the statement as a hypothesis in the discussion.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "one monomer (Chain C) attains stability" is ambiguous. It is unclear whether this refers to a specific chain in a specific PDB structure or a general observation across simulations.
- **Required correction** Clarify which structure and simulation the chain designation refers to, and specify the stability metric used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "disordered" is used without qualification. It is unclear whether this refers to intrinsic disorder predicted from sequence, disorder observed in the crystal structure, or conformational flexibility observed in simulations.
- **Required correction** Define the operational meaning of "disordered" in the context of this study.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract content
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention the simulation length, number of replicates, or force field used. These are standard details expected in a computational study abstract.
- **Required correction** Add brief methodological details to the abstract or ensure they are prominently presented in the full manuscript.

## Risk / unsupported claims
- The claim that MazE7 sterically inhibits tRNA binding to MazF7 is unsupported by any described evidence in the abstract.
- The claim of mechanistic similarity between MazEF7-DNA and AtaRT is not substantiated by any comparative data in the abstract.
- The hypothesis that disordered antitoxins enable tighter binding is presented as a conclusion but is not directly tested.
- The differential stabilization of MazE7 monomers is asserted without quantitative simulation data.
- The overall statement that the study "provides a basis for targeting this TA system" is an extrapolation not supported by the abstract's content.