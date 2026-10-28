## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, experimental procedures, and supporting information description
- **Assessment boundary** Scientific validity, methodological rigor, interpretation of results, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors present a Monte Carlo–Molecular Dynamics simulation framework to investigate whether stochastic interactions between PRC1 bound at PREs and H3K27me3-marked nucleosomes are sufficient to fold chromatin at Polycomb-repressed loci. They report that such interactions reduce the volume of methylated chromatin by approximately half, consistent with super-resolution microscopy measurements, and that this folding leads to spatial clustering of PREs through a probabilistic mechanism. They further show that folding is robust to dilution of methylated nucleosomes mimicking post-replication conditions.
- **Visible evidence base** Figures 1–7, equations 1–26, simulation methodology descriptions, and references to prior experimental measurements
- **Missing materials affecting confidence** Supporting Figure S1 is referenced but not provided; no simulation trajectory data or code availability statement; no quantitative comparison between simulated and experimental chromatin volume distributions beyond mean values

## Reviewer

- **Overall assessment** This manuscript presents a conceptually interesting simulation study addressing a fundamental question in epigenetic regulation: how histone methylation marks are translated into chromatin structural changes. The authors develop a polymer model with calibrated PRC1-H3K27me3 interactions and demonstrate that stochastic binding events can produce chromatin folding and PRE clustering consistent with experimental observations. The work is clearly presented and the methodology is described in sufficient detail for reproduction. However, several technical concerns regarding model calibration, interpretation of the clustering mechanism, and the strength of the connection to experimental data need to be addressed before the conclusions can be fully accepted.

- **Who would be interested in the results, and why** Researchers in chromatin biology, epigenetics, and biophysics would find this work relevant. The study addresses a long-standing question about how histone modifications influence higher-order chromatin structure, and the simulation framework could be adapted to study other epigenetic systems. The finding that PRE clustering can emerge from geometric effects rather than direct PRC1-PRC1 interactions is potentially important for interpreting Hi-C data in Polycomb-repressed domains.

- **Major strengths** The study addresses a mechanistically important question with a tractable computational approach. The two-pronged calibration strategy for the Lennard-Jones potential, combining direct simulation with statistical mechanics derivation, is thoughtful. The authors make a useful distinction between their model, which lacks explicit PRC1-PRC1 interactions, and the observation of PRE clustering, which they attribute to a geometric effect. The post-replication dilution analysis adds practical relevance to the work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the simulated chromatin volume reduction of approximately 50% "agrees well" with super-resolution microscopy measurements of 40–60% volume reduction in Polycomb-repressed genes
- **Evidence pointer** Figure 3, Results section "Interactions between PRE-anchored PRC1 and tri-methylated H3K27 fold the chromatin"
- **Concern** The comparison between simulated and experimental volume reductions is presented as quantitative agreement, but the manuscript does not provide details on how the experimental values were obtained or what exactly is being compared. The simulated volume is calculated from the radius of gyration of a 120-monomer segment, while the experimental measurements likely report volumes of entire chromatin domains. The manuscript does not specify whether the experimental values refer to the same genomic region size, the same chromatin fiber compaction state, or how the experimental volume was defined. Without this information, the claimed agreement could be coincidental.
- **Why it matters** The quantitative match to experimental data is a central pillar of the paper's claim that the model captures biologically relevant behavior. If the comparison is not apples-to-apples, the conclusion that PRC1-H3K27me3 interactions alone can explain observed chromatin compaction is not supported.
- **Resolution test** Provide a detailed description of the experimental measurements being compared, including the genomic region size, the definition of volume used, and the chromatin fiber model assumptions. If possible, simulate a chromatin segment of the same size as the experimentally measured region and compare the distributions of volumes, not just the means.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the two calibration approaches for the Lennard-Jones parameter yield "qualitatively similar albeit not identical results" and that averaging them (ε = 5.1 kBT) is justified
- **Evidence pointer** Figure 2, Equations 14–20, Results section "Interactions between PRE-anchored PRC1 and tri-methylated H3K27 fold the chromatin"
- **Concern** The two calibration methods give ε values of 3.94 kBT and 6.20 kBT, which differ by more than 50%. The authors acknowledge limitations of both approaches but do not provide a rigorous justification for why the arithmetic mean is the appropriate choice. The manuscript does not explore how sensitive the main results are to this choice. Given that the folding behavior likely depends strongly on the interaction strength, the use of an average without sensitivity analysis is a significant gap.
- **Why it matters** The central conclusion that PRC1-H3K27me3 interactions are sufficient to fold chromatin depends critically on the interaction strength used in the simulations. If the true value is closer to either extreme, the folding behavior could be substantially different, potentially eliminating the agreement with experimental data.
- **Resolution test** Perform simulations across the full range of ε values from 3.94 to 6.20 kBT and show that the qualitative conclusions (volume reduction, PRE clustering) are robust. Alternatively, provide a more principled justification for the averaging approach, such as a Bayesian combination of the two estimates with appropriate uncertainties.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The claim that PRE clustering "does not require specific protein-protein interactions" and emerges from a geometric/probabilistic mechanism during chromatin folding
- **Evidence pointer** Figure 7, Results section "Chromatin folding leads to spatial clustering of PREs"
- **Concern** The simple geometric model presented in Figure 7B demonstrates that asymmetric stickiness around anchor points can bias their average distance. However, the connection between this toy model and the full polymer simulations is not rigorously established. The manuscript does not quantify how much of the observed PRE clustering in the full simulations is attributable to the geometric effect versus other factors, such as the specific placement of PREs within the methylated domain. The claim that clustering is "automatic" and does not require PRC1-PRC1 interactions is presented as a general conclusion, but the simulations only test one specific configuration of PREs.
- **Why it matters** The interpretation that PRE clustering in Hi-C data does not necessarily indicate direct PRC1-PRC1 interactions is potentially important for the field. However, if this conclusion is based on a limited set of simulations with specific PRE arrangements, it may not generalize. The manuscript should either demonstrate robustness across different PRE configurations or temper the strength of the claim.
- **Resolution test** Run simulations with different numbers and positions of PREs within the methylated domain and show that the clustering effect persists. Alternatively, provide a quantitative decomposition of the clustering in the full simulations, showing that the geometric effect accounts for the majority of the observed PRE proximity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the simulation results support the hypothesis that H3K27me3 "labels Polycomb-repressed genes for chromatin folding" and that this folding is relevant for epigenetic inheritance
- **Evidence pointer** Figure 6, Results section "Chromatin folding can be re-established shortly after DNA replication"
- **Concern** The post-replication analysis tests the effect of reducing the fraction of methylated nucleosomes from 100% to 50% or 75%. However, the manuscript does not address the transient nature of the post-replication state. During replication, the passing of the replication fork would disrupt chromatin structure entirely, and the reassembly of nucleosomes involves additional factors beyond simple dilution of H3K27me3. The simulation only tests a static reduction in methylation density, not the dynamic process of replication-coupled chromatin assembly.
- **Why it matters** The claim that the model supports epigenetic inheritance of chromatin folding requires that the post-replication state is a reasonable approximation of the actual biological situation. If the dynamic process of replication introduces additional barriers to folding re-establishment, the model's conclusions may be overly optimistic.
- **Resolution test** Acknowledge this limitation explicitly and discuss whether the static dilution is a reasonable first approximation. If possible, incorporate a simple model of replication-coupled nucleosome assembly to test whether folding is re-established under more realistic conditions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2B
- **Evidence pointer** Figure 2B
- **Issue** The calibration curves in Figure 2B show four replicates with the same parameters, but the spread between replicates appears substantial. The manuscript does not report the uncertainty in the estimated ε value at the intersection with pb = 0.5.
- **Required correction** Report the standard error or confidence interval for the estimated ε value and discuss whether the replicate variability affects the calibration.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supporting Figure S1
- **Evidence pointer** Results section "Interactions between PRE-anchored PRC1 and tri-methylated H3K27 fold the chromatin"
- **Issue** Supporting Figure S1 is referenced as showing that the central part of the polymer does not fold without methylated nucleosomes or without PREs, but the figure is not provided in the manuscript.
- **Required correction** Ensure Supporting Figure S1 is included in the submission and referenced appropriately.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Equation 16
- **Evidence pointer** Equation 16 and surrounding text
- **Issue** The derivation of Equation 16 from statistical mechanics is not shown in detail. The text states "From statistical mechanics (19), we have..." but does not explain the assumptions or the steps leading to the final expression.
- **Required correction** Provide a more detailed derivation or a reference that contains the full derivation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that the folding may compete with processes required for transcriptional activity, such as enhancer-promoter looping, but does not elaborate on how this competition might manifest or how it could be tested experimentally.
- **Required correction** Expand this point with specific predictions or experimental approaches that could test the proposed competition.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental procedures
- **Evidence pointer** Experimental procedures, "Equipment" section
- **Issue** The manuscript states that simulations were run on HPC2N but does not provide the specific software versions, random number generator settings, or the number of independent simulations used for each condition beyond the stated 150 polymers.
- **Required correction** Provide additional details on software versions and simulation parameters to facilitate reproduction.

- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative comparison to experiment), R1-M2 (sensitivity to interaction strength), R1-M3 (generality of clustering mechanism)

- **Assessment against Nature-style criteria** 
  - Originality: The work is original in its specific application of a polymer model to test whether PRC1-H3K27me3 interactions alone can explain chromatin folding and PRE clustering. The geometric explanation for PRE clustering is a novel contribution.
  - Scientific importance: The question of how histone modifications translate into chromatin structure is of fundamental importance in epigenetics. The work provides a testable framework for understanding this process.
  - Interdisciplinary readership: The work bridges chromatin biology and computational biophysics, and would be of interest to researchers in both fields. The findings on PRE clustering are relevant to the chromosome conformation capture community.
  - Technical soundness: The simulation methodology is generally sound, but concerns about calibration sensitivity and the quantitative comparison to experiment need to be addressed. The lack of sensitivity analysis for the key interaction parameter is a notable gap.
  - Readability for nonspecialists: The manuscript is clearly written and the main concepts are accessible. The derivation of the binding probability and the geometric clustering model are explained in a way that nonspecialists can follow. However, some simulation details may be challenging for experimental readers.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a plausible mechanism, but the quantitative claims need to be better supported. Specifically, the comparison to experimental data needs to be more rigorous, the sensitivity of results to the interaction strength needs to be demonstrated, and the generality of the clustering mechanism should be tested across different PRE configurations.

## Risk / unsupported claims
- The quantitative agreement between simulated and experimental chromatin volume reduction is not fully supported because the comparison basis is not clearly defined.
- The claim that PRE clustering does not require PRC1-PRC1 interactions is supported only for the specific PRE configuration tested.
- The relevance of the post-replication dilution analysis to actual epigenetic inheritance is not fully established, as the dynamic process of replication is not modeled.
- The statement that the model provides "further insight into mechanisms of epigenetic repression" is somewhat speculative, as the simulations do not directly test repression mechanisms beyond chromatin compaction.