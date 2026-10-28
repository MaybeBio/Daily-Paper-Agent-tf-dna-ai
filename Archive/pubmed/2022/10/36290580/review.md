## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusions.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the claims as presented. No external literature verification or replication of experiments was performed.
- **Shared manuscript claim summary** The authors report that artemisinin, identified via high-throughput screening of an FDA-approved drug library, inhibits Candida glabrata growth. They propose that artemisinin targets the transcription factor PDR1, leading to upregulation of drug efflux pump and ergosterol biosynthesis genes, and that this results in mitochondrial dysfunction characterized by membrane depolarization, increased membrane viscosity, and elevated ROS levels. PDR1 mutant strains and an NDI1 knockout strain are used to support the mechanism.
- **Visible evidence base** Figures 1–5, Tables 1–2, and supplementary tables referenced (Table S1, S2). Methods sections for screening, growth assays, qPCR, ROS measurement, mitochondrial membrane potential, viscosity, and molecular dynamics simulations.
- **Missing materials affecting confidence** Raw data for growth curves, qPCR quantification values, statistical outputs, molecular dynamics trajectory details, and validation of the PDR1-artemisinin physical interaction (e.g., binding assays, mutagenesis beyond in silico). Supplementary figures and tables not provided.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant clinical problem and presents a plausible screening approach. However, the central mechanistic claim that artemisinin directly targets PDR1 is supported only by indirect evidence, including mutant phenotype correlations and molecular dynamics simulations. The causal link between PDR1 regulation, ergosterol synthesis, and mitochondrial dysfunction is not fully established. Several experimental details and controls are missing, and some conclusions extend beyond the data presented.
- **Who would be interested in the results, and why** Researchers in antifungal drug discovery, Candida biology, drug repurposing, and mitochondrial physiology. The potential repurposing of artemisinin for antifungal therapy is of interest to clinical microbiologists and infectious disease specialists.
- **Major strengths** The study addresses an urgent clinical need with a drug repurposing strategy. The use of multiple assays (growth, qPCR, mitochondrial function) provides a broad phenotypic characterization. The inclusion of PDR1 mutant strains and NDI1 knockout adds genetic evidence for the proposed pathway.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality is moderate; the finding that artemisinin has antifungal activity is not entirely novel, and the mechanistic claim of direct PDR1 targeting is not convincingly demonstrated. Scientific importance is potentially high given drug repurposing implications, but the evidence is insufficient to establish a new mechanism. Interdisciplinary readership is possible, but the manuscript is largely specialized. Technical soundness is weakened by missing controls and incomplete data presentation. Readability for nonspecialists is acceptable but could be improved with clearer mechanistic schematics.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the direct PDR1-artemisinin interaction is experimentally validated and the mitochondrial dysfunction link is strengthened.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** The manuscript claims that artemisinin targets transcription factor PDR1, implying a direct physical interaction.
- **Evidence pointer** Section 3.3, Figure 3F, Table 2
- **Concern** The only evidence for direct targeting is molecular dynamics simulation and correlation with mutant phenotypes. No biochemical or biophysical experiments (e.g., surface plasmon resonance, isothermal titration calorimetry, cellular thermal shift assay, or pull-down) are presented to demonstrate direct binding between artemisinin and PDR1.
- **Why it matters** The title and central conclusion depend on a direct target claim. Without experimental validation, the mechanism remains speculative and could be indirect, such as through membrane effects or upstream signaling.
- **Resolution test** Provide direct binding data (e.g., ITC, MST, or CETSA) or genetic evidence such as suppressor mutations in PDR1 that abolish artemisinin binding and resistance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link
- **Claim pointer** The manuscript states that PDR1 regulates drug efflux pump and ergosterol biosynthesis pathway, leading to mitochondrial dysfunction.
- **Evidence pointer** Sections 3.4 and 3.5, Figures 4 and 5
- **Concern** The causal chain from PDR1 to ergosterol synthesis to mitochondrial dysfunction is not directly tested. For example, no experiments show that ergosterol depletion or supplementation rescues the mitochondrial phenotype. The NDI1 knockout results are presented as supporting evidence, but the connection between PDR1 and NDI1 is not established.
- **Why it matters** The proposed pathway is a key novelty. Without causal testing, alternative explanations, such as artemisinin directly affecting mitochondria or membrane integrity, remain plausible.
- **Resolution test** Perform ergosterol supplementation or genetic rescue experiments, and measure NDI1 expression in PDR1 mutants. Use epistasis analysis to order the pathway.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data completeness
- **Claim pointer** The manuscript reports quantitative growth inhibition and qPCR data, but the actual values and statistical comparisons are not fully presented.
- **Evidence pointer** Sections 3.2 and 3.4, Figures 2 and 4
- **Concern** Growth curves are shown, but the statistical analysis is only described for selected time points. qPCR data are presented as fold changes without error bars or statistical tests in the text. The number of biological replicates is stated as three, but individual data points are not shown.
- **Why it matters** Reproducibility and quantitative rigor are essential for supporting the conclusions. Incomplete data presentation prevents independent assessment of effect sizes and variability.
- **Resolution test** Provide full statistical details, including error bars, p-values, and effect sizes for all quantitative assays. Include raw data or dot plots for qPCR and growth measurements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental controls
- **Claim pointer** The manuscript claims that artemisinin specifically impairs mitochondrial function in C. glabrata.
- **Evidence pointer** Section 3.5, Figure 5
- **Concern** The mitochondrial assays (membrane potential, viscosity, ROS) are performed only under one condition (artemisinin concentration and time). No dose-response or time-course experiments are shown. The specificity of the effect is not tested with other antifungal drugs or structurally related compounds.
- **Why it matters** Without appropriate controls, the observed mitochondrial changes could be a general stress response rather than a specific mechanism of artemisinin action.
- **Resolution test** Include dose-response and time-course experiments for mitochondrial assays. Test a structurally related but inactive compound as a negative control.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Molecular dynamics simulation validity
- **Claim pointer** The manuscript uses molecular dynamics simulations to support the claim that PDR1 mutations reduce artemisinin binding affinity.
- **Evidence pointer** Section 2.10, Section 3.3, Table 2
- **Concern** The simulation methods are described briefly, and no validation of the PDR1 model (e.g., from AlphaFold) is provided. The binding free energy values are presented without error estimates or convergence analysis. The functional relevance of the calculated distances is not established.
- **Why it matters** The simulation is a key piece of evidence for the direct target claim. Without rigorous validation, the results may be artifacts of the modeling approach.
- **Resolution test** Provide detailed simulation parameters, convergence checks, and replicate runs. Validate the model against known PDR1 structures or experimental data. Show that the calculated binding affinities correlate with experimental resistance phenotypes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that artemisinin "targets" PDR1, which overstates the evidence presented in the manuscript.
- **Required correction** Rephrase to "modulates PDR1 activity" or "acts through PDR1" to reflect the indirect evidence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2
- **Issue** The screening method uses YPG medium, which is a non-fermentable carbon source. This may pre-dispose cells to mitochondrial dependence and could bias the identification of compounds affecting mitochondrial function.
- **Required correction** Justify the choice of YPG medium or discuss its potential impact on the screening results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The selection criteria for the 197 hits from the initial screen are not clearly defined. The threshold for "inhibition rate more than 20%" is mentioned, but the reproducibility of the screen is not discussed.
- **Required correction** Provide details on hit selection criteria, including statistical thresholds and confirmation steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.4
- **Evidence pointer** Figure 4
- **Issue** The upregulation of ergosterol biosynthesis genes is interpreted as a compensatory response, but this is not tested. It could also be a direct effect of artemisinin on gene expression.
- **Required correction** Clarify the interpretation and suggest experiments to distinguish between these possibilities.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** Some sentences are overly long and complex, which may hinder readability for a general audience.
- **Required correction** Simplify sentence structure and use more direct language.

## Risk / unsupported claims
- The claim that artemisinin directly targets PDR1 is unsupported by direct binding evidence.
- The causal link between PDR1-regulated ergosterol synthesis and mitochondrial dysfunction is not experimentally established.
- The functional significance of the NDI1 knockout in relation to artemisinin's mechanism is not fully explored.
- The molecular dynamics simulation results are presented without sufficient validation to support quantitative conclusions.
- The generalizability of the findings to clinical C. glabrata isolates is not tested.