## Review setup
- **Input scope** Full manuscript text, including Significance, Results, Methods, and Discussion sections. Figures and supplementary information referenced but not fully provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and conclusions as presented in the provided text. No assessment of formatting, grammar, or editorial style.
- **Shared manuscript claim summary** The authors propose that paraspeckle assembly is driven by competitive RNA binding between immiscible core (FUS, NONO) and shell (TDP-43) proteins, rather than by preferential binding of core proteins to the NEAT1 middle region as previously proposed. They support this with in vitro binding and condensation assays on NEAT1 fragments, FRAP experiments, and coarse-grained simulations.
- **Visible evidence base** Text descriptions of results from EMSA binding assays, in vitro condensate formation experiments, FRAP recovery measurements, and coarse-grained molecular dynamics simulations. Figures and supplementary figures are referenced but not directly viewable.
- **Missing materials affecting confidence** Figures, supplementary figures, and supplementary tables are referenced but not provided. This limits verification of quantitative claims, image quality, and statistical analyses. The full NEAT1 sequence and exact fragment coordinates are not given in the text.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially important revision to the current model of paraspeckle assembly. The combination of in vitro biochemistry, biophysics, and simulation is well conceived. The central finding, that core proteins bind preferentially to NEAT1 ends rather than the middle region, directly challenges existing assumptions and is supported by multiple independent approaches. However, the manuscript would be strengthened by more direct evidence linking the in vitro observations to the in vivo context, and by addressing several technical concerns regarding the EMSA and condensate experiments. The simulation component, while useful for hypothesis generation, relies on parameters inferred from the same experiments it is used to validate, creating some circularity. Overall, this is a thoughtful and rigorous study that merits consideration, but the case would be strengthened by addressing the concerns below.

- **Who would be interested in the results, and why** Researchers studying biomolecular condensates, phase separation, RNA-binding proteins, nuclear organization, and gene regulation. The findings are also relevant to those interested in the molecular mechanisms of neurodegenerative diseases involving FUS and TDP-43, and to computational biologists developing coarse-grained models of condensate formation. The conceptual advance, that competitive binding and immiscibility rather than simple affinity differences can generate layered structures, has broad implications for understanding the organization of other multiphase condensates.

- **Major strengths** The study directly challenges a prevailing model with carefully designed experiments. The use of multiple NEAT1 fragments spanning the full transcript is thorough. The combination of binding assays, condensate formation, FRAP, and simulation provides complementary perspectives. The finding that TDP-43 competes with core proteins for NEAT1 ends and can displace them is a novel and mechanistically satisfying explanation for layer formation. The authors are appropriately cautious in their interpretations and acknowledge limitations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that "all proteins prefer to bind portions of the RNA that localize to the same shell layer" and that core proteins FUS and NONO show stronger binding to NEAT1 ends (E1, E2) than to middle fragments (C1, C2, C3).
- **Evidence pointer** Figure 2B, SI Appendix Fig. S2 B-F, location not provided
- **Concern** The EMSA experiments use only 1 kb fragments of NEAT1 rather than the full-length transcript. It is well established that RNA structure and long-range interactions can strongly influence protein binding. A protein that binds a fragment in isolation may not bind the same sequence when it is embedded in the full-length RNA, where competing structures or other bound proteins may occlude the site. The authors do not address whether binding preferences observed on fragments are recapitulated with full-length NEAT1.
- **Why it matters** The central conclusion, that core proteins prefer NEAT1 ends, is based entirely on fragment experiments. If binding preferences differ in the context of the full transcript, the proposed model would be substantially weakened. This is a testable prediction that is critical for the validity of the model.
- **Resolution test** Repeat key EMSA experiments (at minimum FUS and NONO with E1, E2, and C2) using full-length NEAT1 or a larger construct spanning multiple domains. Alternatively, perform competitive binding experiments where full-length NEAT1 is incubated with both core and shell proteins simultaneously and binding locations are mapped (e.g., by crosslinking or footprinting).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report apparent Kd values for FUS binding to NEAT1 fragments, including a claim that FUS binds E1 with approximately 10-fold higher affinity than C2 (65 nM vs 771 nM).
- **Evidence pointer** Figure 2B, SI Appendix Fig. S2 B-C, location not provided
- **Concern** The EMSA analysis relies on quantifying disappearance of free RNA bands. This approach assumes that all bound RNA-protein complexes are either retained in the well or migrate as distinct shifted bands that are not quantified. For proteins like FUS that can form large oligomers or aggregates, bound complexes may be lost during electrophoresis, leading to overestimation of binding affinity. Additionally, the Hill equation fit with variable Hill coefficients can produce apparent Kd values that are not directly comparable between different RNAs if the cooperativity differs. The authors do not report Hill coefficients or goodness-of-fit statistics.
- **Why it matters** The quantitative comparison of binding affinities across NEAT1 fragments is a key piece of evidence. If the Kd values are not reliable due to technical artifacts, the conclusion that FUS prefers ends over middle is weakened.
- **Resolution test** Validate EMSA results with an orthogonal binding assay that does not rely on gel electrophoresis, such as fluorescence anisotropy, microscale thermophoresis, or filter binding. Report Hill coefficients and fit statistics for all Kd determinations. Show representative full gel images including wells to demonstrate that no material is retained.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that "TDP-43 was excluded from condensates assembled with most RNAs, forming TDP-43-rich shells surrounding FUS-rich cores" and interpret this as evidence of immiscibility between TDP-43 and FUS.
- **Evidence pointer** Figure 4B, SI Appendix Fig. S6E-F, location not provided
- **Concern** The observation that TDP-43 forms shells around FUS condensates could be explained by several mechanisms other than immiscibility. For example, TDP-43 may simply not bind strongly to the RNA in the condensate and therefore partitions to the dilute phase, or the shell may form due to interfacial tension effects unrelated to specific protein-protein immiscibility. The authors do not provide control experiments with a protein known to be miscible with FUS, nor do they measure the saturation concentration of TDP-43 in FUS condensates as a function of TDP-43 concentration.
- **Why it matters** The immiscibility of core and shell proteins is a central pillar of the proposed model. If the shell formation is due to other factors, the model would need revision.
- **Resolution test** Perform titration experiments where TDP-43 concentration is varied while FUS and RNA are held constant, and measure the partition coefficient of TDP-43 into FUS condensates. Include a control protein (e.g., a non-interacting RBP) to demonstrate that shell formation is specific to TDP-43. If possible, measure the interfacial tension between FUS-rich and TDP-43-rich phases.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model validity
- **Claim pointer** The authors use coarse-grained simulations to show that their revised interaction network "can give rise to paraspeckle-like, layered assemblies" and that TDP-43 depletion reduces core enrichment of the NEAT1 middle region.
- **Evidence pointer** Figure 5, SI Appendix Fig. S9, location not provided
- **Concern** The simulation parameters are inferred from the same experiments used to validate the model. The interaction strengths in the revised model are set to reproduce the observed phase behavior, and the simulations are then shown to produce layered assemblies. This circularity limits the predictive power of the model. Additionally, the model represents proteins as spherical monomers without sequence-specific features, which may not capture the multivalent, domain-specific interactions that are likely important for paraspeckle assembly.
- **Why it matters** The simulations are presented as supporting evidence for the proposed mechanism. If the parameters are tuned to match the experimental outcomes, the simulations do not provide independent validation.
- **Resolution test** Perform a sensitivity analysis showing how the model output depends on each interaction parameter. Test whether the layered assembly is robust to parameter variation or only occurs in a narrow regime. If possible, make a falsifiable prediction from the model that can be tested experimentally (e.g., the effect of specific mutations on layer organization).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors propose that "competitive RNA binding and protein immiscibility can give rise to layered condensates" as a general principle.
- **Evidence pointer** Discussion section, location not provided
- **Concern** The study is limited to paraspeckle proteins and NEAT1 fragments. The generality of the proposed mechanism is not tested in other condensate systems. While the authors discuss the nucleolus, they do not provide evidence that competitive binding and immiscibility operate there. The claim of generality is therefore speculative.
- **Why it matters** The title and significance statement imply a general principle. If the mechanism is specific to paraspeckles, the framing is overstated.
- **Resolution test** Either temper the claims of generality in the title and significance statement, or provide evidence from at least one additional condensate system that competitive binding and immiscibility contribute to layer formation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, EMSA analysis
- **Evidence pointer** Methods section, location not provided
- **Issue** The equation for B(C) is written as B(C)=I(0)-I(C)/I(0), which is ambiguous. It should be B(C) = (I(0) - I(C)) / I(0).
- **Required correction** Correct the equation formatting to remove ambiguity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, condensate experiments
- **Evidence pointer** Methods section, location not provided
- **Issue** The text states that "TEV protease was added last to each mixture, to a final concentration of 1.5 µM, to cleave the MBP tag and initiate condensation." It is not clear whether the MBP tag was cleaved from all proteins in all experiments, and whether the efficiency of cleavage was verified.
- **Required correction** State explicitly which proteins were used with MBP tags uncleaved and which were cleaved, and describe how cleavage efficiency was assessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 2C, SI Appendix Fig. S2G
- **Evidence pointer** Figure 2C, location not provided
- **Issue** The linear relationship between ∆∆G and motif abundance is reported with a slope of -0.03 kcal/mol/motif, but no confidence intervals or goodness-of-fit statistics are provided.
- **Required correction** Report the R-squared value and confidence intervals for the linear fit.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph 2
- **Evidence pointer** Discussion section, location not provided
- **Issue** The authors state that "TDP-43 competes less effectively with FUS and NONO for the middle region, leading to TDP-43 shells surrounding FUS and NONO cores." This is presented as a conclusion, but the data show that TDP-43 binds weakly to middle fragments. It is not clear whether the mechanism is competition for RNA binding or simply that TDP-43 does not bind the middle region well.
- **Required correction** Clarify whether the data support active competition or simply differential binding affinities.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, section "A Revised Model"
- **Evidence pointer** Results section, location not provided
- **Issue** The simulations of TDP-43 mutations and aging-associated clearance are described only briefly. The specific mutations modeled and the rationale for their choice are not given.
- **Required correction** Provide details on which TDP-43 mutations were modeled and why, or refer to a supplementary table with this information.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, coarse-grained simulations
- **Evidence pointer** Methods section, location not provided
- **Issue** The Lennard-Jones potential parameters are said to be provided in SI Appendix Table S1, but the criteria used to choose these values are not described in the main text.
- **Required correction** Briefly describe the parameterization strategy in the main text, even if full details are in the SI.

## Risk / unsupported claims
- The claim that "all proteins prefer to bind portions of the RNA that localize to the same shell layer" is based on fragment binding experiments and may not hold for the full-length NEAT1 transcript. This is a testable prediction that should be verified.
- The claim that TDP-43 immiscibility with FUS/NONO is the primary mechanism for shell formation is supported by the data but alternative explanations (e.g., differential RNA binding affinity, interfacial tension) are not fully excluded.
- The generality of the proposed mechanism ("competitive RNA binding and protein immiscibility can give rise to layered condensates") is not established beyond the paraspeckle system studied here.
- The simulation results are presented as supporting evidence, but the circularity of parameter inference from the same experiments limits their independent confirmatory value.
- The claim that "transcriptional bursts are required to form paraspeckle-like clusters containing many copies of NEAT1" is based on simulations only and is not directly tested experimentally.