## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions, limitations)
- **Assessment boundary** Computational findings only; no experimental validation data provided
- **Shared manuscript claim summary** The authors report a structure-based virtual screening and molecular dynamics workflow to identify FDA-approved drugs as candidate stabilizers of mutant p53. They nominate DB09280 as a lead candidate based on docking scores, interaction fingerprint density, and 500 ns MD simulations showing reduced structural drift and fluctuation in the holo state relative to apo.
- **Visible evidence base** Docking scores (range, top candidates), PLIP interaction counts, residue-level interaction fingerprints, MD-derived RMSD/RMSF/PCA metrics, free-energy landscape projections, control docking results
- **Missing materials affecting confidence** No experimental validation (thermal shift, DNA binding, cell-based assays); no co-crystal structures; no replicate MD simulations; no explicit treatment of zinc coordination; no raw trajectory data or convergence diagnostics beyond stated metrics

## Reviewer
- **Overall assessment** This manuscript presents a computationally rigorous and internally consistent pipeline for nominating FDA-approved drugs as candidate stabilizers of mutant p53. The authors are appropriately cautious in framing their findings as hypothesis-generating rather than definitive. The docking, interaction fingerprinting, and MD analyses are technically sound in their execution, and the control experiments for grid placement and selectivity are thoughtful. However, the central claim of "rescue" rests entirely on in silico metrics that have not been experimentally validated, and the single-replicate MD design limits the strength of the stabilization conclusions. The manuscript would be strengthened by additional replicates, enhanced sampling, and explicit acknowledgment of the gap between structural stabilization and functional rescue, which the authors do provide in their limitations section.

- **Who would be interested in the results, and why** Researchers in cancer biology, specifically those working on p53 reactivation strategies; computational chemists and structural biologists interested in drug repurposing workflows; medicinal chemists seeking starting points for mutant p53 stabilizers. The methodological pipeline may also interest groups developing virtual screening protocols for intrinsically disordered or partially destabilized protein targets.

- **Major strengths** The authors employ a multi-stage computational workflow that appropriately layers docking, interaction profiling, and MD simulation, with clear criteria for candidate prioritization. The use of two controls (arsenic pose recovery and PhiKan083 selectivity) demonstrates methodological rigor. The explicit acknowledgment of limitations, including single-replica MD and the distinction between structural stabilization and functional rescue, is commendable. The interaction fingerprint analysis identifying His19 engagement provides a mechanistically plausible hypothesis for zinc-coordination rescue.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The ligand-bound (holo) system exhibited substantially reduced global structural drift (RMSD) and attenuated local residue fluctuation (RMSF) within the core domain compared to the highly unstable apo state."
- **Evidence pointer** Section 2.3.1, Figure 6; Section 2.3.2, Figure 7
- **Concern** The stabilization claim rests on a single 500 ns MD replicate per system. The authors acknowledge this in the limitations section, but the Results and Discussion sections present the RMSD/RMSF differences as robust findings. With n=1, the observed differences could reflect initial velocity artifacts or incomplete sampling rather than genuine ligand-induced stabilization. The reported standard deviations (3.09 ± 0.69 Å vs 2.18 ± 0.39 Å) describe temporal fluctuations within one trajectory, not uncertainty across independent simulations.
- **Why it matters** The central conclusion of the paper is that DB09280 acts as a conformational stabilizer. Without replicate simulations, the statistical basis for this claim is not established. A reviewer cannot determine whether the observed stabilization is reproducible or a single-trajectory artifact.
- **Resolution test** Provide at least three independent 500 ns replicates per system (apo and holo) and report mean ± SEM across replicates. Alternatively, perform enhanced sampling (e.g., Gaussian-accelerated MD or replica exchange) to demonstrate convergence of the conformational ensembles. If computational cost is prohibitive, the claims should be explicitly downgraded to "preliminary observations from a single trajectory."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim scope
- **Claim pointer** "Together, these computational findings nominate DB09280 as a promising candidate structural stabilizer of mutant p53 worthy of experimental follow-up."
- **Evidence pointer** Abstract; Section 4 (Conclusions)
- **Concern** The manuscript title and abstract frame this as a "rescue candidates" study, and the conclusions state DB09280 is "worthy of experimental follow-up." However, the evidence base is entirely computational, and the authors themselves note that "in silico stabilization observed here is not equivalent to functional rescue." The gap between the title's implication and the actual evidence is substantial. The term "rescue" in the title may overstate what the data can support.
- **Why it matters** Readers and potential experimental collaborators may be misled about the strength of the evidence. The title should accurately reflect the hypothesis-generating nature of the work, or the authors should provide at least one experimental validation point (e.g., thermal shift assay) to support the "rescue" framing.
- **Resolution test** Either (a) revise the title to reflect the computational screening nature of the study (e.g., "Computational Identification of FDA-Approved Drugs as Candidate p53 Mutant Stabilizers"), or (b) include a minimal experimental validation (e.g., differential scanning fluorimetry or cellular thermal shift assay) demonstrating that DB09280 stabilizes at least one mutant p53 protein in vitro.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical completeness
- **Claim pointer** "DB09280 uniquely engages His19, a crucial residue for zinc coordination, and forms stabilizing contacts with adjacent flexible loop residues, including ASN35 and PRO32."
- **Evidence pointer** Section 2.2, Figures 4 and 5
- **Concern** The His19 engagement is presented as a key mechanistic finding, but the manuscript does not describe how the zinc ion was treated in the docking and MD simulations. The methods section (3.1) states that protonation states were assigned and crystallographic waters removed, but does not specify whether the structural zinc ion was retained in the receptor model. If the zinc was removed, the relevance of His19 engagement to zinc coordination is unclear. If retained, the force field parameters for zinc are not described.
- **Why it matters** The mechanistic interpretation depends critically on the zinc coordination environment. Without explicit description of zinc treatment, the significance of His19 engagement cannot be evaluated.
- **Resolution test** Specify in the methods whether the zinc ion was retained in the receptor structure for docking and MD. If retained, describe the zinc parameters used in the CHARMM36m force field. If removed, discuss the implications for interpreting His19 engagement as relevant to zinc coordination.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "The prioritized candidates demonstrated consistent, multi-conformer binding affinities."
- **Evidence pointer** Section 2.1, Table 1
- **Concern** The docking scores are reported as a range (−6.8 to −8.3 kcal/mol for top candidates), but the manuscript does not provide a statistical comparison against a decoy set or a known inactive compound. The statement that these candidates are in the "top ~1% of the distribution" is presented without a clear definition of the distribution or the total number of compounds screened. The enrichment factor is not quantified.
- **Why it matters** Without a proper decoy set or statistical enrichment analysis, the significance of the docking scores cannot be assessed. The reader cannot determine whether these scores represent genuine binding or are typical of the scoring function's behavior on this target.
- **Resolution test** Provide the full distribution of docking scores for the entire FDA-approved library, the number of compounds screened, and a statistical enrichment analysis (e.g., AUC of ROC curve or BEDROC) using a validated decoy set. Alternatively, compare docking scores of the prioritized candidates against a set of known non-binders to demonstrate separation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1, Table 2
- **Evidence pointer** Section 3.1
- **Issue** The methods section states that structures were selected based on "high-resolution transmembrane domains" and "fenestration pathways," which are terms relevant to membrane proteins, not soluble p53. This appears to be a copy-paste error from a different study.
- **Required correction** Replace the selection criteria with accurate descriptors for p53 DNA-binding domain structures, such as "high-resolution crystal structures with resolved zinc-coordination geometry and defined DNA-binding interface."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The docking grid center coordinates are provided, but the manuscript does not state which specific residues define the allosteric pocket or how the grid was positioned relative to the arsenic-binding site. The "measure center" command applied to the arsenic site is described, but the relationship between the arsenic site and the allosteric pocket is not explicitly defined.
- **Required correction** Provide the specific residue numbers that define the allosteric pocket and describe how the grid center was positioned relative to these residues. State whether the arsenic site and the allosteric pocket are the same or distinct.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3.1
- **Evidence pointer** Figure 6
- **Issue** The RMSD analysis reports mean values over the 100–500 ns interval, but the manuscript does not state the equilibration time or how the 100 ns cutoff was determined. The choice of equilibration period affects the reported statistics.
- **Required correction** State the equilibration time explicitly and justify the 100 ns cutoff for the production analysis window. Provide RMSD traces from the start of the simulation to show the equilibration behavior.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.4
- **Evidence pointer** Figure 8
- **Issue** The cosine-content values are reported (0.19 and 0.003 for apo; 0.40 and 0.06 for holo), but the manuscript does not explain the significance of these values or what threshold indicates convergence. The holo PC1 value of 0.40 is notably higher than the apo value, which could indicate poorer sampling.
- **Required correction** Provide a brief explanation of cosine-content analysis and its interpretation. Discuss whether the holo PC1 value of 0.40 raises concerns about sampling convergence.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The text states that "DB09280 was subsequently elevated for detailed dynamic characterization on the basis of its interaction-fingerprint density and its unique engagement of His19," but the criteria for "interaction-fingerprint density" are not defined quantitatively.
- **Required correction** Define the metric used to quantify interaction-fingerprint density (e.g., number of contacts, weighted interaction score) and state the threshold or ranking criterion used to select DB09280.

## Risk / unsupported claims
- The claim that DB09280 "acts as a putative conformational clamp" is supported only by single-replicate MD data and should be considered preliminary.
- The mechanistic interpretation involving His19 and zinc coordination cannot be fully evaluated without explicit description of zinc treatment in the computational protocol.
- The statement that candidates are in the "top ~1% of the distribution" lacks the statistical context needed for assessment.
- The title's use of "Rescue Candidates" overstates the evidence, which is entirely computational and explicitly acknowledged by the authors as not equivalent to functional rescue.
- The selection criteria for p53 structures in Section 3.1 contain terminology inconsistent with soluble protein targets, suggesting an error that undermines confidence in the methods description.