## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) with figure and table legends; no supplementary material provided.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to evidence, and clarity of presentation. No assessment of editorial fit or scope decisions.
- **Shared manuscript claim summary** The authors use docking, 100 ns MD simulation, and MM-PBSA analysis to propose that curcumin can associate near the DNA-recognition interface of the NF-κB p50 homodimer, with favorable binding energetics and localized stabilization of the protein structure.
- **Visible evidence base** Docking scores and interaction residues (Table 1); RMSD, RMSF, Rg, SASA, hydrogen-bond, and contact analyses (Figs. 4, 5); MM-PBSA energy components (Table 2); FEL analysis (Fig. 7).
- **Missing materials affecting confidence** No PDB validation metrics, no force-field parameter details for the ligand, no block-averaging methodology description, no error estimates for docking scores, no replica simulations, no explicit DNA-bound control simulations, no experimental validation data.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward computational study of curcumin binding to the NF-κB p50 homodimer. The work is technically competent in its execution of standard protocols, but the scientific advance is modest. The central claims are largely supported by the data presented, though several methodological details are missing and some interpretations overreach the evidence. The study would benefit from additional validation steps and a more cautious framing of the biological implications.
- **Who would be interested in the results, and why** Researchers studying NF-κB regulation by natural compounds, computational chemists interested in protein-ligand interactions of polyphenols, and groups working on anti-inflammatory drug design. The residue-level mapping of a putative curcumin interaction site could inform future mutagenesis or experimental binding studies.
- **Major strengths** The study addresses a relevant question with a clear rationale. The use of multiple complementary computational methods (docking, MD, MM-PBSA, PCA/FEL) is appropriate. The authors are appropriately cautious in several places, explicitly noting the protein-only model and the absence of entropy in free-energy estimates. The discussion of limitations is honest and reasonably comprehensive.
- **Major Concerns** See items below.
- **Minor Comments** See items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (docking validation), R1-M2 (force-field choice), R1-M3 (trajectory convergence), R1-M4 (overinterpretation of biological relevance).
- **Assessment against Nature-style criteria**  
  *Originality*: Low to moderate. The application of standard computational methods to a well-studied target with a widely studied ligand does not represent a conceptual advance. The specific focus on the DNA-recognition interface is a minor novelty.  
  *Scientific importance*: Moderate. The findings are hypothesis-generating but do not establish a new mechanism or resolve a significant controversy. The biological relevance is speculative without experimental validation.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to computational biophysicists and NF-κB researchers. The methods are standard and the findings are unlikely to attract broad attention.  
  *Technical soundness*: Adequate but with notable gaps. The simulations appear to be run with reasonable parameters, but the lack of docking validation, the questionable force-field choice, and the absence of convergence analysis weaken the technical foundation.  
  *Readability for nonspecialists*: Acceptable. The manuscript is clearly written, though some sections (e.g., the methods) assume familiarity with computational techniques. The figures are generally clear, though the FEL figure lacks sufficient annotation.
- **Recommendation posture** Supportive if technical concerns are resolved. The core computational work is plausible, but the manuscript requires substantial revision to address methodological gaps and to temper overinterpreted claims before the case is established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that docking identified a preferred pose with a Vina score of −6.0 kcal/mol and that this represents a plausible binding mode.
- **Evidence pointer** Methods (Molecular docking), Results (Docking analysis), Table 1
- **Concern** The docking protocol lacks any form of validation. The authors note that PDB ID 1SVC does not contain a co-crystallized ligand, making redocking validation impossible, but they do not provide any alternative validation strategy. There is no cross-docking against a related NF-κB structure with a bound ligand, no comparison with known binding-site mapping data, and no discussion of how the docking grid was defined relative to the DNA-recognition interface. The Vina score of −6.0 kcal/mol is weak and within the range of nonspecific binding. Without validation, the selection of the "preferred pose" appears arbitrary.
- **Why it matters** The entire downstream analysis (MD, MM-PBSA) depends on the initial docking pose. If the starting pose is incorrect or not representative, all subsequent conclusions about binding stability and energetics are compromised. A docking score alone, without validation, is insufficient to establish a credible binding hypothesis.
- **Resolution test** Provide a validation strategy, such as cross-docking with a related NF-κB-ligand complex, comparison with mutagenesis data from the literature, or at minimum a discussion of how the grid box was positioned relative to known DNA-contacting residues and why the selected pose is chemically reasonable. Alternatively, perform docking with multiple search algorithms and show convergence to the same pose.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the GROMOS96 force field was used for the protein and that the ligand topology was generated using SwissParam, with PME for electrostatics.
- **Evidence pointer** Methods (MD simulation)
- **Concern** The GROMOS96 force field was originally developed for use with reaction-field electrostatics, not PME. The authors acknowledge this but do not justify why PME was chosen beyond stating it is "widely applied." This is a significant methodological concern because the combination of GROMOS96 with PME can lead to artifacts in protein dynamics and ligand binding energetics. Furthermore, SwissParam is parameterized for the CHARMM force field, not GROMOS. Using SwissParam-generated ligand parameters with GROMOS96 protein parameters is a mismatch that could introduce systematic errors in the ligand-protein interactions.
- **Why it matters** Force-field consistency is critical for reliable MD simulations. Mixing parameter sets from different force-field families can lead to incorrect interaction energies, biased conformational sampling, and unreliable free-energy estimates. The MM-PBSA results, which are central to the paper's conclusions, are directly affected by the quality of the underlying MD trajectory.
- **Resolution test** Justify the force-field choice with appropriate citations or benchmark data, or re-run the simulations with a consistent force-field combination (e.g., GROMOS96 with reaction-field electrostatics, or CHARMM36 with CHARMM-compatible ligand parameters). At minimum, provide a sensitivity analysis showing that the conclusions are robust to the choice of electrostatic treatment.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the 100 ns simulation is "sufficient for assessing local binding stability and residue-level dynamical trends."
- **Evidence pointer** Methods (MD simulation), Results (MD-based stability and flexibility analysis)
- **Concern** The manuscript provides no evidence of trajectory convergence. The authors mention block averaging of RMSD values but do not report the block-averaged values or show that the system reached a stable plateau. The RMSD of the complex shows a sharp increase between 95 and 100 ns, which is not adequately explained. A single 100 ns trajectory without replicas is generally insufficient to draw robust conclusions about binding stability, especially for a protein-ligand complex where conformational transitions can occur on longer timescales. The authors acknowledge the lack of replicas as a limitation, but they do not address the convergence issue directly.
- **Why it matters** Without demonstrated convergence, the reported RMSD, RMSF, Rg, and SASA values may reflect transient states rather than equilibrium behavior. The MM-PBSA free-energy estimate, which is averaged over the trajectory, could be biased by non-equilibrium sampling. The claim that the complex is "stable" is not supported without convergence analysis.
- **Resolution test** Provide block-averaged RMSD values with standard deviations, show that the system reached a plateau before the end of the simulation, and explain the late-stage RMSD increase. If possible, extend the simulation or run additional replicas to confirm the observed trends.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that the observed binding "may eventually result in impaired DNA recognition or altered interaction with cofactors" and that the results "indicate inhibition of NF-κB function."
- **Evidence pointer** Discussion
- **Concern** The manuscript repeatedly suggests that the computational findings have functional implications for NF-κB inhibition, but the study uses a protein-only model with DNA removed. The authors correctly note that the results do not demonstrate competition with DNA, but the framing in the Discussion and Conclusion still leans toward functional claims. The leap from "local stabilization near the DNA-recognition region" to "inhibition of NF-κB function" is not supported by the data. The authors also cite prior studies suggesting curcumin inhibits NF-κB, but these are not directly connected to the present computational model.
- **Why it matters** Overinterpretation of computational results as functional evidence can mislead readers and overstate the significance of the work. The manuscript should clearly separate the computational hypothesis from any biological claims, and should avoid language that implies functional inhibition without experimental support.
- **Resolution test** Revise the Discussion and Conclusion to explicitly state that the results provide a computational hypothesis only, and remove or soften any language suggesting functional inhibition. Add a clear statement that experimental validation is required before any biological conclusions can be drawn.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the complex "showed a compact structural profile" and "lower solvent-accessible surface area relative to the apo model," but no numerical values are provided. The abstract also does not mention the PCA/FEA analysis, which is a significant component of the results.
- **Required correction** Include key numerical values (e.g., average Rg and SASA for both systems) and briefly mention the PCA/FEA analysis to accurately represent the scope of the study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods (MD simulation)
- **Evidence pointer** Methods (MD simulation)
- **Issue** The methods state that "missing atoms or residues were added" to the PDB structure, but no details are provided on how this was done or which residues were missing. The protonation state assignment is described as "based on physiological pH" but the specific tool or method is not named.
- **Required correction** Provide details on the structure preparation steps, including which residues were missing, how they were modeled, and which tool was used for protonation state assignment.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results (Docking analysis)
- **Evidence pointer** Table 1
- **Issue** Table 1 lists three docking poses with different scores and interaction residues, but the text only discusses the most favorable pose in detail. The relationship between the poses is unclear, and the reader cannot determine whether the poses represent distinct binding modes or minor variations of the same mode.
- **Required correction** Clarify whether the poses in Table 1 represent distinct binding modes or are clustered variations. If they are distinct, discuss the implications for the subsequent MD analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results (Contact analysis)
- **Evidence pointer** Results (Contact analysis)
- **Issue** The contact analysis section defines a contact as occurring when any atom of the ASP-GLU group is within 0.6 nm of any atom of the LYS-ARG group, but the rationale for this specific grouping is not explained. The relevance of these contacts to the binding site is unclear.
- **Required correction** Explain why the ASP-GLU and LYS-ARG groups were chosen for contact analysis and how these contacts relate to the predicted binding region.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results (MM-PBSA)
- **Evidence pointer** Table 2
- **Issue** Table 2 reports the MM-PBSA results but does not specify how many frames were used for the analysis or over which time window the averaging was performed. The table also does not report the standard error of the mean (SEM) for the total binding free energy.
- **Required correction** Specify the number of frames and the time window used for the MM-PBSA calculation, and report the SEM for the total binding free energy.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results (FEA)
- **Evidence pointer** Fig. 7
- **Issue** The FEA figure is described as showing "energy minima" but the figure itself is not shown in the manuscript text provided. The text does not describe the topology of the free-energy landscape or how the minima differ between the apo and complex systems.
- **Required correction** Provide a description of the FEA results, including the number and location of energy minima, and how they differ between the two systems.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods (General)
- **Evidence pointer** Methods
- **Issue** The methods do not specify the software versions for GROMACS, AutoDock Vina, or gmx_MMPBSA. This information is essential for reproducibility.
- **Required correction** Provide the software versions used for all major tools.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The Discussion cites references 40, 41, and 57 in the first sentence, but the reference list is not provided in the manuscript text. The reader cannot verify the relevance of these citations.
- **Required correction** Ensure the reference list is complete and that all citations are relevant to the claims they support.

## Risk / unsupported claims
- The claim that curcumin binding "may eventually result in impaired DNA recognition" is unsupported, as no DNA-bound simulations or experimental binding assays were performed.
- The claim that the complex is "dynamically stable" is not fully supported without convergence analysis or replicate simulations.
- The claim that the MM-PBSA binding free energy of −15.75 kcal/mol indicates "favorable relative binding energetics" is weakened by the omission of entropic contributions and the lack of error estimates.
- The biological relevance of the predicted binding site is speculative, as the simulations were performed on a protein-only model with DNA removed.
- The docking pose selection is not validated, and the Vina score of −6.0 kcal/mol is within the range of weak, potentially nonspecific binding.