## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use all-atom explicit-solvent replica exchange molecular dynamics simulations to compare conformational ensembles of TDP-43(321-340) monomer and dimer with and without the ALS-linked M337V mutation. They report that M337V alters secondary structure propensities, inhibits helix formation in specific regions, promotes beta-sheet formation, disrupts inter-molecular helix-helix and W334-W334 pi-pi stacking interactions, enhances peptide-peptide interactions, and weakens peptide-water interactions, thereby providing mechanistic insight into impaired phase separation and enhanced fibrillization.
- **Visible evidence base** Abstract text only; no simulation details, convergence metrics, force field parameters, system setup, or quantitative results are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation methodology, force field and water model specifications, replica exchange parameters, convergence and equilibration analyses, free energy surfaces, contact maps, and any statistical error estimates

## Reviewer
- **Overall assessment** The abstract presents a plausible and mechanistically interesting hypothesis linking a single ALS-associated mutation to altered conformational ensembles of a key TDP-43 fragment. However, the claims are broad and mechanistic in nature, and the abstract alone provides no quantitative evidence, no methodological validation, and no statistical assessment. The central conclusions cannot be evaluated from the supplied material, and several claims appear to exceed what can be reasonably supported without detailed analysis of the simulation trajectories.
- **Who would be interested in the results, and why** Researchers studying TDP-43 aggregation and phase separation, computational biophysicists interested in mutation effects on intrinsically disordered regions, and investigators focused on ALS pathogenesis at the molecular level. The work could also interest those developing therapeutic strategies targeting TDP-43 aggregation, as understanding mutation-specific conformational changes may inform drug design.
- **Major strengths** The study addresses a clinically relevant mutation in a biologically important protein region. The use of all-atom explicit-solvent replica exchange molecular dynamics is appropriate for exploring conformational ensembles of a peptide system. The abstract connects simulation findings to experimentally reported phenomena, namely LLPS disruption and fibrillization enhancement, which provides a clear biological motivation.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The question of how a single mutation alters conformational ensembles of a TDP-43 fragment is not entirely novel, as prior computational studies have examined TDP-43 peptides and mutations, but the specific focus on the 321-340 region and the dimer interface may offer some new perspective. Scientific importance: The topic is relevant to ALS research and protein phase separation, which are active and important fields. Interdisciplinary readership: The work could appeal to structural biologists, biophysicists, and neuroscientists, but the abstract is written in a specialized manner that may limit broader accessibility. Technical soundness: Cannot be assessed from the abstract alone; no methodological details or validation are provided. Readability for nonspecialists: The abstract assumes familiarity with LLPS, replica exchange simulations, and secondary structure terminology, which may hinder comprehension for a general scientific audience.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a coherent narrative, but the absence of quantitative results, methodological details, and statistical validation means the core claims cannot be verified. A supportive posture would require access to the full manuscript and demonstration that the simulation results are robust and statistically meaningful.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that M337V mutation alters residue regions with high helix/beta-structure propensities and affects conformational ensembles of both monomer and dimer.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no quantitative data, such as secondary structure probabilities, free energy differences, or population shifts, to support the claim that the mutation alters conformational ensembles. No error bars, statistical tests, or convergence assessments are mentioned.  
- **Why it matters** Without quantitative evidence and statistical validation, the claim that the mutation affects conformational ensembles is unsubstantiated. Replica exchange simulations can suffer from insufficient sampling, and the absence of convergence metrics raises the possibility that observed differences are artifacts of inadequate sampling.  
- **Resolution test** Provide secondary structure propensity values with standard errors, show convergence of replica exchange simulations, and demonstrate that observed differences between wild-type and mutant are statistically significant.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that M337V inhibits helix formation in the N-terminal Ala-rich region and the C-terminal mutation site region while facilitating long beta-sheet formation, albeit with minor impact on average probabilities.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The claim that the mutation has a minor impact on average probabilities but a significant impact on specific regions is internally nuanced, but no data are provided to support either assertion. The distinction between "long beta-sheet formation" and average beta-structure probability is not defined, and the criteria for "long" are not stated.  
- **Why it matters** The biological interpretation depends on the specificity of these structural changes. If the average probabilities are barely affected, the functional significance of regional changes must be demonstrated with clear structural definitions and quantitative comparisons.  
- **Resolution test** Define the criteria for "long beta-sheet," provide per-residue secondary structure probabilities for both systems, and show that regional differences are statistically robust and not merely noise.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that M337V disrupts inter-molecular helix-helix interactions and W334-W334 pi-pi stacking interactions while enhancing overall peptide-peptide interactions and weakening peptide-water interactions.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** These are specific mechanistic claims about inter-molecular interactions in the dimer system. The abstract provides no contact maps, interaction energy decompositions, or radial distribution functions to support these assertions. The claim that W334-W334 pi-pi stacking is disrupted is particularly specific and requires direct evidence.  
- **Why it matters** The central mechanistic narrative linking the mutation to LLPS disruption and fibrillization enhancement rests on these interaction-level claims. Without quantitative interaction analyses, the proposed mechanism is speculative.  
- **Resolution test** Provide interaction energy calculations, contact probability maps, and representative structural ensembles for the dimer systems, with statistical comparisons between wild-type and mutant.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Scientific importance  
- **Claim pointer** The authors claim that their study provides mechanistic insights into M337V-mutation-induced impairment of phase separation and facilitation of fibril formation of TDP-43 LCD.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract connects simulation findings to experimental observations of LLPS disruption and fibrillization enhancement, but the link is inferential. The simulations are of a short peptide fragment, and extrapolating to full-length TDP-43 LCD behavior requires justification that the 321-340 region is the dominant driver of these processes.  
- **Why it matters** The broader significance of the work depends on whether the peptide-level findings translate to the full-length protein. Without discussion of limitations or comparison to experimental data on the full-length system, the mechanistic insight claim is overstated.  
- **Resolution test** Discuss the relevance of the peptide model to full-length TDP-43, compare simulation findings to available experimental data on the 321-340 region, and explicitly state the limitations of the fragment-based approach.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract structure  
- **Evidence pointer** Abstract text  
- **Issue** The abstract is dense and uses specialized terminology without definition, such as "liquid-solid phase transition" and "pi-pi stacking interactions," which may not be familiar to all readers.  
- **Required correction** Briefly define or contextualize key terms to improve accessibility for a broader scientific audience.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Simulation methodology  
- **Evidence pointer** Abstract text  
- **Issue** The abstract states that "extensive" replica exchange simulations were performed but provides no details on system size, simulation length, number of replicas, or force field used.  
- **Required correction** Include key simulation parameters in the abstract or refer to a methods section where these details are provided.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Contextualization  
- **Evidence pointer** Abstract text  
- **Issue** The abstract mentions experimental reports on the 321-340 region and the M337V mutation but does not cite specific studies or clarify how the simulation results compare to those experimental findings.  
- **Required correction** Add brief references to key experimental studies and state whether the simulation results are consistent with or extend those findings.

## Risk / unsupported claims
- The claim that M337V alters conformational ensembles is unsupported without quantitative data.
- The claim that M337V disrupts specific inter-molecular interactions (helix-helix and W334-W334 pi-pi stacking) is unsupported without interaction-level analysis.
- The claim that enhanced peptide-peptide interactions and weakened peptide-water interactions are conducive to fibrillization is inferential and not directly demonstrated.
- The claim that the study provides mechanistic insights into full-length TDP-43 LCD behavior is not established from a peptide fragment simulation alone.
- The overall mechanistic narrative linking simulation results to LLPS disruption and fibrillization enhancement is plausible but not verifiable from the abstract.