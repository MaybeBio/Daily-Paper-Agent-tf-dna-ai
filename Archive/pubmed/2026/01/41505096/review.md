## Review setup
- **Input scope** Full manuscript text including abstract, materials and methods, results, discussion, and supplementary figure references
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that Lsr2, a nucleoid-associated protein from Mycobacterium tuberculosis, compacts DNA through sequence-dependent co-condensation with AT-rich regions, mediated by multivalent binding and intrinsically disordered regions, and that this mechanism explains Lsr2-mediated gene regulation and genome organization
- **Visible evidence base** Biochemical assays (EMSA, turbidity), fluorescence microscopy of phase-separated condensates, single-molecule TIRF imaging of DNA compaction, FRAP analysis, coarse-grained Brownian dynamics simulations, and confocal imaging of eGFP-tagged Lsr2 in Mtb cells
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (Figs S1–S10, Tables S1–S5) were not provided; detailed simulation parameters and validation metrics are not fully described in the main text; raw data and statistical details for quantitative claims are not available

## Reviewer
- **Overall assessment** This manuscript addresses an important question in bacterial chromosome biology: how a nucleoid-associated protein achieves genome-wide compaction and gene regulation. The combination of biochemical, single-molecule, and computational approaches is ambitious and potentially impactful. The central claim that Lsr2 undergoes sequence-dependent co-condensation with AT-rich DNA, rather than simple sequence-specific binding, is conceptually novel and would be of broad interest. However, several technical concerns must be addressed before the case is fully established. The quantitative analysis of single-molecule data lacks sufficient detail, the simulation model requires more rigorous validation against experimental observables, and the in vivo imaging data are presented without adequate controls or statistical treatment. The manuscript is well-written and accessible, but the current evidence base does not fully support all claims made in the abstract and discussion.

- **Who would be interested in the results, and why** Researchers studying bacterial nucleoid organization, nucleoid-associated proteins, phase separation in biology, and mycobacterial pathogenesis would find these results of direct interest. The work also speaks to the broader community investigating how sequence-dependent protein-DNA interactions give rise to higher-order chromatin structures. The proposed mechanism of "sensing" average binding energy landscapes rather than individual motifs could have implications for understanding gene regulation in other bacteria and potentially eukaryotic systems.

- **Major strengths** The combination of multiple orthogonal approaches (biochemistry, single-molecule imaging, simulations, and in vivo imaging) is a significant strength. The single-molecule assay design with sequence-controlled DNA constructs is elegant and directly tests the sequence-dependence hypothesis. The inclusion of mutant analysis to dissect molecular determinants of phase separation is thorough. The connection between in vitro observations and in vivo relevance through eGFP-tagged Lsr2 imaging in Mtb is valuable. The physical model provides a framework for understanding how base-pair-level interactions scale to kilobase-level condensation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of single-molecule data analysis
- **Claim pointer** The authors claim that Lsr2 forms condensates preferentially at AT-rich regions based on single-molecule imaging, with a reported Pearson correlation of 0.9 between DNA sequence and compaction position.
- **Evidence pointer** Results section "Lsr2 forms sequence-dependent co-condensates with DNA at AT-rich regions"; Figure 4
- **Concern** The threshold-based method for identifying condensate regions from intensity profiles is described, but the choice of threshold parameter (x = 0.5) is not justified. The manuscript states that ">75 snapshots" were analyzed per molecule, but the total number of molecules analyzed, the variability between molecules, and the statistical significance of the reported correlation are not provided. The Pearson correlation of 0.9 is reported without confidence intervals or a null hypothesis comparison. Additionally, the method for converting intensity profiles to probability profiles involves binary classification of each base pair as either in or out of a condensate, which may introduce artifacts depending on the threshold choice.
- **Why it matters** The central claim of sequence-dependent co-condensation rests on the quantitative analysis of single-molecule data. Without proper statistical treatment, including error estimates and appropriate controls, the strength of the correlation and the specificity of the effect cannot be rigorously evaluated. This is particularly important given that the authors argue against a simple sequence-specific binding model.
- **Resolution test** Provide a detailed description of the number of molecules analyzed, the distribution of correlation coefficients across individual molecules, and a statistical comparison against a null model (e.g., random placement of condensates). Justify the threshold choice and demonstrate that results are robust to reasonable variations in the threshold parameter. Include confidence intervals for the reported correlation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation model validation
- **Claim pointer** The authors state that coarse-grained Brownian dynamics simulations "recapitulate the key features of sequence-dependent co-condensation" and report a Pearson correlation of approximately 0.75 between simulated and experimental condensation patterns.
- **Evidence pointer** Results section "Lsr2 forms sequence-dependent co-condensates with DNA at AT-rich regions"; Figure 4e and 4j; Supplementary Information
- **Concern** The simulation model parameters are listed in Supplementary Tables S1–S4, but the main text does not describe how these parameters were determined or whether they were fitted to experimental data. The agreement between simulations and experiments (correlation of 0.75) is reported without error bars or sensitivity analysis. It is unclear whether the model is predictive or merely descriptive. The manuscript also does not discuss potential limitations of the coarse-grained approach, such as the neglect of sequence-specific DNA flexibility or the simplified representation of Lsr2 as a dimer with two binding sites.
- **Why it matters** The simulations are presented as a key validation of the proposed mechanism. If the model parameters are tuned to reproduce the experimental observations, the agreement is less compelling. The claim that the model "allows us to connect base pair level binding with emergent co-condensation" requires that the model be shown to make robust predictions beyond the specific conditions tested.
- **Resolution test** Describe how simulation parameters were chosen, including whether they were derived from independent measurements or fitted to experimental data. Provide a sensitivity analysis showing how the results depend on key parameters. Report the variability of the correlation across independent simulation runs. Discuss the limitations of the model and what specific predictions it makes that could be tested experimentally.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo imaging controls and quantification
- **Claim pointer** The authors claim that in vivo imaging of eGFP-tagged Lsr2 in Mtb cells reveals punctate structures that co-localize with DAPI-stained DNA, and that Lsr2 knockout leads to more homogeneous DNA distribution, supporting a role for Lsr2 in DNA compaction.
- **Evidence pointer** Results section "Mtb cells exhibit Lsr2–DNA condensates"; Figure 5; Supplementary Fig. S5
- **Concern** The in vivo imaging data are presented qualitatively. The manuscript states that "distinct punctate structures" were observed and that DNA distribution is "more homogenous" in the knockout strain, but no quantitative analysis is provided. The number of cells analyzed, the criteria for identifying puncta, and the statistical significance of the difference between wild-type and knockout strains are not reported. Additionally, the eGFP tagging strategy is described in the methods, but the functionality of the tagged protein is not verified (e.g., whether it complements the lsr2 knockout phenotype). The use of chemically crosslinked cells raises questions about whether the observed puncta are physiological or artifacts of fixation.
- **Why it matters** The in vivo data are critical for establishing physiological relevance. Without quantitative analysis and appropriate controls, the claim that Lsr2 forms condensates in cells and compacts DNA cannot be rigorously evaluated. The lack of functional validation of the eGFP-tagged Lsr2 is a particular concern, as tagging could interfere with protein function.
- **Resolution test** Provide quantitative analysis of puncta number, size, and intensity per cell, with statistical comparison between wild-type and knockout strains. Include the number of cells analyzed and the criteria for puncta identification. Verify that eGFP-tagged Lsr2 is functional by complementation assays. Discuss the potential artifacts of chemical fixation and, if possible, include live-cell imaging data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of FRAP data
- **Claim pointer** The authors report FRAP recovery for Lsr2 condensates and co-condensates, and state that recovery was observed, indicating dynamic exchange.
- **Evidence pointer** Results section "Lsr2 and DNA together undergo phase separation"; Figure 1g; Supplementary Fig. S1d
- **Concern** The FRAP data are described qualitatively. The manuscript states that Lsr2 displayed FRAP to original fluorescence levels, but the recovery kinetics, mobile fraction, and comparison between conditions are not quantified. The statement that recovery was "at a higher rate" in the presence of DNA is not supported by quantitative data. The FRAP methodology (bleach region size, imaging parameters, analysis method) is not described in sufficient detail.
- **Why it matters** FRAP is a key assay for demonstrating liquid-like properties of condensates. Quantitative FRAP analysis would strengthen the claim that Lsr2-DNA co-condensates are dynamic and liquid-like, which is important for the proposed mechanism.
- **Resolution test** Provide quantitative FRAP curves with recovery half-times and mobile fractions for each condition, with statistical comparison. Describe the FRAP methodology in detail, including the bleach region size, imaging parameters, and normalization method.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed mechanism
- **Claim pointer** The authors propose that sequence-dependent co-condensation is a general mechanism for NAP-mediated genome organization in bacteria, and that Lsr2 "senses" the average binding energy landscape.
- **Evidence pointer** Discussion section
- **Concern** The manuscript extrapolates from Lsr2 to other NAPs and proposes a general mechanism. While this is an interesting hypothesis, the evidence presented is specific to Lsr2. The claim that this represents a "novel mechanism" for gene silencing in bacteria is not directly tested. The relationship between co-condensation and gene regulation is inferred but not demonstrated functionally (e.g., by showing that specific genes are silenced through co-condensation).
- **Why it matters** The broader claims in the discussion go beyond the data presented. While speculation is appropriate in a discussion, the framing of these claims as established findings could be misleading. The connection between co-condensation and gene regulation is the most significant biological implication but is not directly tested.
- **Resolution test** Either temper the claims in the discussion to more clearly distinguish speculation from established findings, or provide additional evidence linking co-condensation to gene regulation (e.g., transcriptomic analysis of Lsr2 condensate-associated genes).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Phase separation assay description
- **Evidence pointer** Materials and methods, "Analysis of condensate area"
- **Issue** The sentence describing condensate area analysis is incomplete: "The percentage of area covered by condensates measured as follows:" with no formula or description following.
- **Required correction** Complete the description of the condensate area quantification method, including the formula used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Quantitative claims throughout
- **Evidence pointer** Results sections; Figures 1, 3, 4
- **Issue** Several quantitative claims are made without error bars or statistical tests, including the concentration dependence of condensate formation, the correlation between sequence and condensation position, and the comparison between wild-type and mutant proteins.
- **Required correction** Add error bars and statistical tests to all quantitative comparisons, and report the number of independent replicates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Figure 2
- **Evidence pointer** Results section "Both multivalent binding and intrinsically disordered regions are required for phase separation of Lsr2"
- **Issue** Figure 2 is referenced in the introduction (Fig. 1a and b) and in the results section, but the specific panels showing the domain structure and mutant locations are not clearly described in the text.
- **Required correction** Clearly describe which panels of Figure 2 show the domain structure, mutant locations, and the results of the mutant experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Co-condensation" vs. "condensation"
- **Evidence pointer** Throughout
- **Issue** The term "co-condensation" is used to describe Lsr2-DNA assemblies, but the distinction from simple protein-DNA aggregation or non-specific binding is not always clear.
- **Required correction** Define "co-condensation" operationally and discuss how the observed assemblies are distinguished from non-specific aggregates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of H-NS and Rok
- **Evidence pointer** Discussion section
- **Issue** The comparison with H-NS and Rok is brief and does not fully engage with the existing literature on these proteins. The statement that H-NS "is only shown to bridge DNA" is an oversimplification given the extensive literature on H-NS-DNA interactions.
- **Required correction** Expand the discussion of H-NS and Rok to provide a more nuanced comparison and acknowledge the complexity of their mechanisms.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Simulation code and analysis scripts
- **Evidence pointer** Data availability section
- **Issue** The data availability statement only mentions that data are available in the article and supplementary material. No mention is made of simulation code or analysis scripts.
- **Required correction** State whether simulation code and analysis scripts will be made available, and if so, where.

## Risk / unsupported claims
- The claim that Lsr2 co-condensation "senses" the average binding energy landscape rather than individual motifs is presented as a key finding but is not directly tested; it is an interpretation of the observed correlation between AT-content and condensation position.
- The statement that "selective sequestration of only a subset of the genome by Lsr2 condensates further suggests a regulatory mechanism whereby Lsr2 targets specific genes" is speculative and not directly supported by functional data.
- The claim that this is the "first experimental evidence for DNA sequence-dependent co-condensation of protein and DNA" is difficult to evaluate without a comprehensive literature search; the authors should verify this claim carefully.
- The in vivo conclusion that Lsr2 is "responsible for DNA compaction in Mycobacterium" is based on qualitative comparison of DNA distribution in wild-type versus knockout strains and lacks quantitative support.
- The extrapolation to a general mechanism for NAP-mediated genome organization in bacteria is not supported by the data presented, which are specific to Lsr2.