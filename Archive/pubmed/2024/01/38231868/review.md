## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) without supplementary material or figures
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive logic as presented in the main text; figure and table contents are referenced but not directly inspectable
- **Shared manuscript claim summary** The authors use extensive unbiased and enhanced sampling MD simulations to evaluate the functional impact of hotspot mutations in the TetR repressor, showing that non-inducible phenotypes arise from distinct perturbations in inter-domain coupling and/or intra-domain conformational properties, and that free energy landscapes can rank mutation severity and rescuability.
- **Visible evidence base** Main text descriptions of metadynamics and unbiased simulation results, including free energy profiles along a DBD distance collective variable, KL divergence analyses, binding pocket structural analyses, and comparisons to prior DMS data
- **Missing materials affecting confidence** All figures, tables, supplementary information, simulation parameter details, convergence analyses, and force field specifications are referenced but not provided; these are essential for full technical evaluation

## Reviewer
- **Overall assessment** This manuscript presents a substantial computational effort to dissect the molecular mechanisms by which hotspot mutations disrupt allostery in TetR. The central idea, that the same non-inducible phenotype can arise from mechanistically distinct perturbations, is well motivated and supported by the described results. The combination of long unbiased simulations with metadynamics is appropriate and represents a methodological advance over the authors' prior WT-only study. However, the manuscript as provided cannot be fully evaluated because all quantitative evidence resides in figures and tables that were not supplied. The claims of semi-quantitative ranking and rescuability correlation with DMS data rest on comparisons that are described but not directly verifiable from the text alone. The writing is generally clear, though some mechanistic interpretations would benefit from more explicit connection to the presented data.

- **Who would be interested in the results, and why** Researchers in computational biophysics and allostery, particularly those studying transcription factors and ligand-induced conformational changes. The work also speaks to the protein engineering and synthetic biology communities interested in rational design of allosteric regulators, and to experimentalists using DMS who seek mechanistic interpretation of mutational phenotypes. The methodological framework for evaluating hotspot mutations via free energy calculations could be transferable to other multi-domain allosteric proteins.

- **Major strengths** The study addresses a question of genuine importance: whether computational simulations can distinguish mechanistically distinct routes to the same functional phenotype. The design, comparing mutants across multiple structural regions and functional states, is thoughtful. The use of both unbiased and enhanced sampling methods is appropriate, and the collective variable choice (DBD distance) is well justified by prior structural and simulation work. The connection to DMS data provides an experimental anchor that strengthens the relevance of the findings. The thermodynamic model proposed in prior work is usefully extended by showing that realistic mutations mix type 1 and type 2 effects.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that metadynamics simulations reveal a doubly-bound basin in all hotspot mutants, with relative stabilities that correlate with DMS-derived rescuability.
- **Evidence pointer** Figure 2, Table 1, Figure S3 (convergence), location not provided
- **Concern** The central quantitative results, including the free energy profiles, basin stabilities, and KL divergence values, are presented only as figure and table references. Without access to these data, the core claims cannot be assessed. Specifically, the claim that G102D shows near-equal stability of the two basins, and that this correlates with its low rescuability, requires inspection of the actual free energy curves and error estimates.
- **Why it matters** The entire argument for semi-quantitative ranking of mutation impact rests on these data. If the basin stabilities are within statistical error of each other, or if the KL divergence values do not clearly separate mutants, the conclusions would be substantially weakened.
- **Resolution test** Provide the figures and tables, including error bars or confidence intervals on the free energy profiles and KL divergence values, and demonstrate that the differences between mutants exceed the estimated uncertainties.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors state that multi-walker well-tempered metadynamics simulations converge adequately within 110–140 ns per walker, and that the chosen collective variable is sufficient to capture the functionally relevant conformational change.
- **Evidence pointer** Computational Methods, Figure S3, location not provided
- **Concern** The manuscript does not provide details on how convergence was assessed beyond referencing a block-average analysis. For a system as large as TetR, 110–140 ns per walker is short, and it is unclear whether the free energy surface is fully explored, particularly for mutants that may have altered energy barriers. The choice of a single collective variable (DBD distance) may also be insufficient if the conformational change involves orthogonal degrees of freedom.
- **Why it matters** If the simulations are not converged, or if the collective variable misses important conformational states, the computed free energy profiles could be misleading. This is especially critical for the claim that the doubly-bound basin is genuinely stabilized in mutants versus an artifact of incomplete sampling.
- **Resolution test** Show convergence plots (e.g., free energy difference as a function of simulation time), provide a comparison of the metadynamics results with unbiased simulations where possible, and discuss whether additional collective variables were tested or considered.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive rigor
- **Claim pointer** The authors conclude that reduced inter-domain coupling in hotspot mutants is a general mechanism underlying the non-inducible phenotype, and that this is supported by the free energy landscapes of the apo states.
- **Evidence pointer** Results section "Inter-Domain Coupling Is Reduced in Hotspot Mutants", Figures 4 and 5, location not provided
- **Concern** The interpretation of the apo-state free energy landscapes relies on a thermodynamic model with a coupling free energy parameter γ. The manuscript states that G102D and R49A show a third basin corresponding to the low-affinity conformation, but it is not clear how this is quantitatively distinguished from the WT landscape, which also shows multiple basins. The claim that γ is reduced in mutants is inferred rather than directly measured.
- **Why it matters** The distinction between reduced coupling and altered intra-domain stability is central to the authors' mechanistic classification. If the apo-state differences are within statistical noise, or if the third basin is present but less populated in the WT, the interpretation would need revision.
- **Resolution test** Provide a quantitative comparison of the apo-state free energy landscapes, including the relative populations of the identified basins for WT and each mutant, and show how the thermodynamic model parameters are extracted from the data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** The manuscript claims that the computational results provide a "semi-quantitative rationale" for the different degrees of rescuability observed in DMS experiments, specifically the order N129D > G196D > D53V > R49A > G102D.
- **Evidence pointer** Discussion section "Rescuability of Allostery Hotspots", Table 1, location not provided
- **Concern** The manuscript discusses rescuability for G102D, R49A, and G196D, but does not appear to address N129D or D53V, which are part of the DMS-derived ranking. The claim of semi-quantitative agreement is therefore based on a subset of the available data. It is unclear whether the authors' framework would correctly predict the rescuability of the other two mutants.
- **Why it matters** A semi-quantitative correlation based on three of five data points is weak support for the claim. If the framework cannot distinguish N129D from G102D, for example, the predictive value is limited.
- **Resolution test** Either include simulations of N129D and D53V, or clearly state the limitations of the current dataset and avoid overgeneralizing the rescuability correlation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that effects are evaluated "qualitatively and semi-quantitatively" but does not specify what is meant by semi-quantitative in this context.
- **Required correction** Define the semi-quantitative metric (e.g., relative free energy differences, ranking of basin stabilities) in the abstract or early in the introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Computational Methods
- **Evidence pointer** Computational Methods, location not provided
- **Issue** The force field, water model, and simulation temperature are not stated in the main text. These are essential for reproducibility.
- **Required correction** Add the force field and water model specifications to the Computational Methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section "Doubly-Bound States Are Better Stabilized in Hotspot Mutants"
- **Evidence pointer** Results, location not provided
- **Issue** The term "doubly-bound basin" is introduced to describe a conformation that is competent for both ligand and DNA binding, but the simulations only include the ligand. The terminology may overstate what is actually computed.
- **Required correction** Clarify that the "doubly-bound basin" refers to a conformation expected to favor DNA binding based on structural criteria, not a state with both ligands bound in the simulation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 1
- **Evidence pointer** Table 1, location not provided
- **Issue** The KL divergence values are presented without confidence intervals or a statement of how many independent simulations were used.
- **Required correction** Report the number of simulations and provide error estimates for the KL divergence values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The introduction cites DMS studies of TetR but does not discuss whether any experimental structural data exist for the specific mutants studied here.
- **Required correction** Briefly note whether experimental structures or binding data are available for any of the studied mutants, and if so, how they compare to the simulation predictions.

## Risk / unsupported claims
- The claim that the doubly-bound basin is "better stabilized" in all hotspot mutants cannot be verified without the free energy profiles.
- The claim of a semi-quantitative correlation with DMS rescuability is based on a subset of the five DMS-analyzed mutants and is therefore not fully supported.
- The assertion that the thermodynamic model with reduced γ explains the apo-state landscapes of G102D and R49A is inferred from the data but not directly demonstrated.
- The statement that the computational framework is "scalable to other allostery systems" is a reasonable extrapolation but is not demonstrated in this work.
- The claim that the chosen collective variable is sufficient to capture the functionally relevant conformational change is plausible but not rigorously justified against alternative variables.