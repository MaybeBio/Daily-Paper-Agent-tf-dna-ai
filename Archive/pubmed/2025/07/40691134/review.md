## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that ubiquitylation of DNA-protein crosslinks (DPCs) allosterically activates the SPRTN protease through a newly identified ubiquitin-binding interface at the back of the protease domain, independent of known ubiquitin-binding domains. This activation is proposed to be critical for DPC repair and genome stability, particularly in the context of Ruijs-Aalfs syndrome patient variants.
- **Visible evidence base** In vitro DPC cleavage assays with defined ubiquitylated substrates; protein structure prediction (ColabFold); molecular dynamics simulations; NMR spectroscopy; cellular assays including SPRTN autocleavage, micronuclei, chromatin bridges, and cell cycle analysis; mass spectrometry for ubiquitin linkage analysis
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; source data files not available; NMR assignment details incomplete; statistical details for some quantifications not fully described; details of the synthetic ubiquitylation system efficiency and specificity not fully provided

## Reviewer
- **Overall assessment** This manuscript presents a potentially important advance in understanding how SPRTN protease activity is regulated during DPC repair. The identification of a ubiquitin-binding interface on the protease domain that allosterically activates SPRTN is novel and mechanistically interesting. The combination of biochemical reconstitution, computational approaches, and cellular validation is commendable. However, several technical concerns need to be addressed to fully support the conclusions, particularly regarding the quantitative claims of activation, the structural basis of the allosteric mechanism, and the physiological relevance of the observed effects.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, genome stability, ubiquitin signaling, and protease regulation would find these results of interest. The work provides a new paradigm for how ubiquitin can act as an allosteric activator of a protease, which has broader implications for understanding enzyme regulation by post-translational modifications. Clinically, the findings may inform understanding of Ruijs-Aalfs syndrome pathology.
- **Major strengths**
  1. The reconstitution of DPC ubiquitylation in vitro with defined chain types and lengths is technically impressive and allows for rigorous mechanistic dissection.
  2. The identification of a novel ubiquitin-binding interface on the protease domain, distinct from known ubiquitin-binding domains, is a significant conceptual advance.
  3. The combination of computational predictions (ColabFold, MD simulations) with experimental validation (NMR, mutagenesis, cellular assays) provides a multi-layered approach to support the proposed mechanism.
  4. The cellular experiments using patient-derived SPRTNΔC variants add translational relevance and demonstrate the physiological importance of the identified regulatory mechanism.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of quantitative activation claim
- **Claim pointer** The abstract and results state that DPC ubiquitylation activates SPRTN "more than one hundred-fold" and that this activation is "strongly" dependent on the ubiquitin modification.
- **Evidence pointer** Figure 1e, f; quantification described in figure legends; location not provided for specific data points
- **Concern** The claim of >100-fold activation is based on comparisons of cleavage efficiency between ubiquitylated and unmodified DPCs. However, the quantification methodology is not fully described. It is unclear whether the comparison is based on initial rates, endpoint product formation, or enzyme titrations. The figure legends mention "mean ± SD of three independent experiments" but do not specify how the fold-activation was calculated. Additionally, the presence of the ubiquitin moiety on the DPC substrate could affect substrate recognition or processivity independent of the proposed allosteric mechanism, confounding the interpretation of the activation magnitude.
- **Why it matters** The quantitative claim of >100-fold activation is a central finding of the paper and is used to support the physiological significance of the mechanism. If the activation is overestimated due to methodological issues, the biological importance of the allosteric regulation may be overstated.
- **Resolution test** Provide a clear description of the quantification method, including how fold-activation was calculated. Show dose-response curves for SPRTN activity on ubiquitylated versus unmodified substrates. Include statistical analysis comparing the activation levels across multiple substrate preparations. Consider using single-turnover or initial-rate measurements to more accurately quantify the activation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural basis of allosteric activation
- **Claim pointer** The manuscript claims that ubiquitin binding to the USD interface "promotes an open SPRTN conformation" and that this open conformation is required for activity.
- **Evidence pointer** Figure 2a–i; MD simulation data; NMR data in Figure 3
- **Concern** The structural model relies heavily on ColabFold predictions, which are not experimentally validated. The MD simulations show that the predicted open conformation is stable in the presence of ubiquitin, but the starting structures were generated computationally. The NMR data show only subtle changes upon ubiquitin binding, and the interpretation that these changes represent a conformational shift to an open state is not directly demonstrated. No experimental structure of the SPRTN-ubiquitin complex is provided. The claim that ubiquitin "promotes" the open conformation implies a dynamic equilibrium shift, but the data presented are largely static snapshots from simulations.
- **Why it matters** The proposed allosteric mechanism is the core conceptual advance of the paper. Without experimental validation of the open conformation and its stabilization by ubiquitin, the mechanistic model remains speculative.
- **Resolution test** Provide experimental evidence for the conformational change, such as SAXS, FRET, or hydrogen-deuterium exchange mass spectrometry. Alternatively, validate the ColabFold predictions with mutagenesis experiments that disrupt the predicted interface and show loss of ubiquitin binding and activation. Consider performing NMR relaxation dispersion experiments to directly demonstrate conformational exchange between open and closed states.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance of the USD interface
- **Claim pointer** The manuscript claims that the USD interface is "critical to maintain fitness and genome stability in cells expressing truncated RJALS patient variants" and that this is due to ubiquitin-dependent activation.
- **Evidence pointer** Figure 5g, h; Figure 6a–e; Supplementary Figure 6a, b
- **Concern** The cellular experiments show that SPRTNΔC-L99S has reduced ability to cleave DNMT1-DPCs and causes genomic instability. However, the L99S mutation may affect protein stability, folding, or other functions of SPRTN beyond ubiquitin binding. The manuscript does not provide evidence that the L99S mutation specifically disrupts ubiquitin binding in cells without affecting other SPRTN functions. Additionally, the experiments are performed in cells that already express endogenous SPRTNΔC, and the complementation with exogenous variants may not fully recapitulate physiological conditions.
- **Why it matters** The conclusion that ubiquitin-dependent activation via the USD is essential for genome stability in patients relies on the specificity of the L99S mutation. If the mutation has pleiotropic effects, the interpretation is confounded.
- **Resolution test** Perform pull-down or co-immunoprecipitation experiments to demonstrate that L99S specifically disrupts ubiquitin binding in cells. Assess protein stability and folding of the L99S variant. Use a complementary approach, such as a ubiquitin-binding-deficient mutation in a different residue or a chemical inhibitor of the USD-ubiquitin interaction, to confirm the specificity of the phenotype.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the activation mechanism
- **Claim pointer** The manuscript proposes a "triple-lock" model in which ubiquitin binding to the USD, DNA binding, and UBZ-mediated recruitment collectively control SPRTN activity.
- **Evidence pointer** Figure 7; Discussion section
- **Concern** The triple-lock model is presented as a unifying framework, but the experimental evidence for the model is incomplete. The model implies that all three mechanisms are required for full activity, but the manuscript does not systematically test the contribution of each mechanism in isolation or in combination. The model is largely based on the observation that SPRTNΔC-L99S has a stronger phenotype than either mutation alone, but the quantitative contributions of each "lock" are not defined.
- **Why it matters** The triple-lock model is a conceptual framework that may guide future research, but it needs to be supported by more direct experimental evidence to be convincing.
- **Resolution test** Design experiments that systematically vary the presence of each regulatory element (UBZ, USD, DNA binding) and measure SPRTN activity. Use a combination of mutants and substrates to test the predicted synergies. Provide quantitative data on the contribution of each mechanism to overall activity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1e, f
- **Evidence pointer** Figure 1e, f; figure legends
- **Issue** The figure legends state that "All samples derive from the same experiment and gels were processed in parallel" but the gels appear to be cropped from different exposures. The quantification of cleavage products is not clearly described, and it is unclear how the "Cleaved DPC*" products were distinguished from other cleavage products.
- **Required correction** Provide full gel images or clearly indicate cropping. Describe the quantification method in detail, including how the different cleavage products were identified and quantified. Consider showing representative full gels in the supplementary material.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Figure 6d, e; Supplementary Figure 7e–h
- **Evidence pointer** Figure 6d, e; Supplementary Figure 7e–h
- **Issue** The statistical analysis for the micronuclei and chromatin bridge quantifications is not fully described. The figure legends mention p-values from a two-way ANOVA with Dunnett's multiple comparison test, but the number of independent experiments, the number of cells counted, and the criteria for identifying micronuclei and chromatin bridges are not specified.
- **Required correction** Provide detailed statistical methods, including the number of independent experiments, the number of cells scored, and the criteria for scoring. Consider including a supplementary table with all statistical comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** NMR data interpretation
- **Affected element** Figure 3; Supplementary Figure 3
- **Evidence pointer** Figure 3; Supplementary Figure 3
- **Issue** The NMR data show only subtle changes upon ubiquitin binding, and the interpretation that these changes represent a conformational shift is not fully supported. The authors state that "the effects of ubiquitin addition were reduced" in the L99S variant, but the quantitative analysis of these changes is not provided.
- **Required correction** Provide quantitative analysis of the NMR spectral changes, including chemical shift perturbation values for all affected residues. Consider performing titration experiments to determine the binding affinity of ubiquitin for SPRTN.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological details for MD simulations
- **Affected element** Methods section, Molecular dynamics simulations
- **Evidence pointer** Methods section, Molecular dynamics simulations
- **Issue** The MD simulation methods are described, but some details are missing, including the force field parameters for the ubiquitin-SPRTN complex, the equilibration protocol, and the criteria for determining convergence. The choice of starting structures and the number of replicates are described, but the analysis of the simulations is not fully detailed.
- **Required correction** Provide complete details of the MD simulation setup, including force field parameters, equilibration protocol, and convergence criteria. Consider providing the simulation trajectories as supplementary data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The term "USD" is introduced in the Results section but is not defined in the abstract. The term "SPRTNΔC" is used to describe both the patient variant and the truncated construct, which may cause confusion.
- **Required correction** Define "USD" at first use in the abstract. Use consistent terminology for the SPRTN variants, such as "SPRTNΔC (patient variant)" and "SPRTNΔC (recombinant construct)".

## Risk / unsupported claims
- The claim that ubiquitin binding to the USD "promotes an open SPRTN conformation" is not directly supported by experimental structural data; it is inferred from MD simulations and indirect NMR observations.
- The claim that the USD interface is "critical" for genome stability in RJALS patients is based on experiments with a single point mutation (L99S) and may be confounded by potential pleiotropic effects of the mutation.
- The quantitative claim of "more than one hundred-fold" activation by ubiquitylation is not fully supported by the described methodology, as the basis for this calculation is not clearly explained.
- The "triple-lock" model is presented as a unifying framework but is not systematically tested; the relative contributions of each proposed mechanism are not quantitatively defined.
- The physiological relevance of the in vitro findings to the in vivo situation is inferred but not directly demonstrated, particularly regarding the kinetics of DPC ubiquitylation and SPRTN activation in cells.