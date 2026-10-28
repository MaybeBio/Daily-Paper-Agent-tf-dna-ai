## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to propose a mechanistic model for how the R248Q mutation in the p53 core domain enhances aggregation propensity and how resveratrol (RSV) inhibits this aggregation more effectively than pterostilbene (PT). The proposed mechanism involves mutation-induced extension of loop L3, which destabilizes aggregation-prone regions (APRs), and RSV binding that restores a WT-like loop L3 conformation and reduces APR solvent exposure.
- **Visible evidence base** Abstract text only; no simulation details, convergence metrics, force field parameters, binding free energy calculations, or experimental validation are provided
- **Missing materials affecting confidence** Full methods, simulation system setup, force field and water model choices, simulation length and replica counts, convergence and sampling assessments, binding affinity calculations, structural figures, quantitative data on loop L3 extension and APR exposure, and any comparison with experimental aggregation kinetics

## Reviewer

- **Overall assessment** The abstract presents a plausible and mechanistically coherent hypothesis for mutation-enhanced p53 aggregation and differential inhibition by two polyphenolic compounds. The proposed model is internally consistent and aligns with prior experimental observations cited by the authors. However, the abstract alone provides no quantitative evidence, no methodological detail, and no demonstration of sampling convergence, which are essential for establishing the reliability of molecular dynamics-based conclusions. The claim that RSV stabilizes loop L3 to a WT-like conformation and thereby inhibits aggregation is mechanistically attractive but currently rests on simulation observations that cannot be evaluated from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics and molecular simulation of protein aggregation, structural biologists studying p53 misfolding and cancer-associated mutations, and medicinal chemists interested in small-molecule inhibitors of protein aggregation. The work could also interest investigators developing therapeutic strategies for p53 aggregation-associated cancers, particularly those focused on polyphenolic compounds.
- **Major strengths** The study addresses a clinically relevant problem with clear translational implications. The comparative design (WT, R248Q mutant, R248Q with RSV, R248Q with PT) is well suited to dissect mutation effects and inhibitor mechanisms. The proposed mechanism linking loop L3 dynamics to APR stability provides a testable framework that connects local structural changes to global aggregation propensity. The differential analysis of RSV versus PT offers a rational basis for understanding why one compound outperforms the other.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (sampling and convergence), R1-M2 (quantitative support), R1-M3 (binding and self-association claims)
- **Assessment against Nature-style criteria** Originality: the specific mechanistic proposal linking R248Q-induced loop L3 extension to APR destabilization and RSV-mediated rescue is a novel contribution, though it builds on established concepts of APR exposure in p53 aggregation. Scientific importance: the topic is significant given the role of p53 mutations in cancer and the need for aggregation inhibitors, but the advance is incremental and computational in nature. Interdisciplinary readership: the work bridges biophysics, cancer biology, and drug discovery, which could attract broad interest if the evidence is robust. Technical soundness: cannot be assessed from the abstract alone; the absence of methodological detail and convergence analysis is a major limitation. Readability for nonspecialists: the abstract is clearly written and accessible, with logical flow from problem to mechanism to therapeutic implication.
- **Recommendation posture** Supportive if technical concerns are resolved. The mechanistic hypothesis is interesting and potentially valuable, but the current evidence base is insufficient to establish the case. Full assessment requires access to simulation details, convergence metrics, and quantitative analyses.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The simulations reveal that loop L3 remains compact in WT p53C but becomes extended in the R248Q mutant, and that this extension weakens interactions between loop L3 and aggregation-prone regions.
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract provides no information on simulation length, number of replicas, force field parameters, water model, temperature and pressure coupling, or equilibration protocols. Without this information, it is impossible to assess whether the observed conformational differences between WT and R248Q mutant reflect genuine equilibrium properties or artifacts of insufficient sampling. Conformational transitions such as loop extension can occur on timescales that exceed typical simulation lengths, and the absence of convergence metrics is a critical gap.
- **Why it matters** Molecular dynamics conclusions about conformational ensembles are only reliable if sampling is demonstrably converged. If the loop L3 extension in the R248Q mutant is observed in a single or few trajectories without replication, the central mechanistic claim is not established. This concern undermines the entire proposed mechanism.
- **Resolution test** Provide simulation lengths, number of independent replicas, and convergence analyses such as block averaging, RMSD stabilization, or principal component overlap. Show that the loop L3 extension is reproducible across replicas and stable over the simulation timescale. If enhanced sampling methods were used, describe them explicitly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The destabilized APRs in the R248Q mutant are more exposed than in WT p53C, which is conducive to p53C aggregation. RSV binding reduces APRs' solvent exposure.
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract states that APRs are more exposed in the mutant and that RSV reduces this exposure, but no quantitative measures are provided. Solvent accessible surface area calculations, contact probabilities, or free energy estimates are not reported. The claim that RSV binding "stabilizes loop L3 to its WT-like conformation" is presented as a definitive finding, but the abstract does not indicate how this stabilization was quantified or whether it was statistically significant across simulations.
- **Why it matters** The central mechanistic model depends on quantitative differences in APR exposure and loop L3 conformation between WT, mutant, and inhibitor-bound states. Without numerical data and statistical analysis, these claims are qualitative assertions rather than evidence-based conclusions.
- **Resolution test** Report quantitative values for APR solvent accessible surface area, loop L3 extension metrics (e.g., end-to-end distance, radius of gyration), and interaction energies between loop L3 and APRs for all simulated systems. Include error bars and statistical significance tests comparing WT, R248Q, and R248Q with RSV or PT.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** RSV has a higher preference to bind to R248Q p53C than PT. PT exhibits a lower hydrogen-bonding capability and a higher self-association propensity, which would lead to a reduced p53C binding and a weakened inhibitory effect.
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract claims differential binding preferences between RSV and PT and attributes PT's weaker inhibition to lower hydrogen-bonding capability and higher self-association propensity. However, no binding free energy calculations, hydrogen bond occupancy analyses, or self-association assessments are described. The phrase "would lead to" indicates speculation rather than demonstrated causality. The connection between PT self-association and reduced p53C binding is not established.
- **Why it matters** The differential inhibitor mechanism is a key part of the study's contribution. If the binding preference and the reasons for PT's weaker effect are not quantitatively demonstrated, the comparative conclusion is unsupported. This weakens the translational relevance of the work.
- **Resolution test** Provide binding free energy calculations (e.g., MM-PBSA, MM-GBSA, or umbrella sampling) for RSV and PT with R248Q p53C. Report hydrogen bond occupancy statistics for both compounds. If self-association of PT is claimed, provide simulation evidence such as aggregation number or cluster analysis in the simulation box.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses "aggregation-prone regions (APRs)" without defining which specific residues or structural regions these correspond to in p53C. Readers unfamiliar with the p53 aggregation literature may not know which regions are meant.
- **Required correction** Define APRs explicitly, either by residue numbers or by reference to prior structural characterizations, when first mentioned.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Experimental context
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract references a "recent experimental study" showing RSV inhibits R248Q aggregation better than PT, but does not provide the citation or briefly describe the experimental conditions. This makes it difficult to assess whether the simulation conditions are relevant to the experimental context.
- **Required correction** Include the citation for the experimental study and briefly state the experimental aggregation assay conditions (e.g., protein concentration, temperature, buffer) to allow readers to judge the relevance of the simulation setup.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Causal language
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "preventing L3-extension-caused APRs' destabilization" implies a causal chain that is inferred from correlated observations in simulations. The abstract does not demonstrate that preventing L3 extension is the direct cause of APR stabilization, as opposed to other effects of RSV binding.
- **Required correction** Soften the causal language to reflect that the simulations are consistent with this mechanism, for example "consistent with a model in which RSV binding prevents L3 extension and thereby maintains APR stability."

## Risk / unsupported claims

- The claim that loop L3 extension in R248Q weakens interactions with APRs and leads to APR destabilization is unsupported without quantitative interaction energy data and convergence analysis.
- The claim that RSV stabilizes loop L3 to a WT-like conformation is unsupported without quantitative conformational metrics and statistical comparison.
- The claim that RSV has a higher binding preference for R248Q p53C than PT is unsupported without binding free energy calculations.
- The claim that PT's lower hydrogen-bonding capability and higher self-association propensity explain its weaker inhibition is speculative and unsupported by the abstract.
- The overall mechanistic model is plausible but cannot be evaluated for reliability without full methodological details and quantitative results.