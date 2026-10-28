## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors propose that three ParAF dimers cooperatively assemble on the type Ia partition promoter of plasmid F, binding to overlapping inverted repeat motifs, and that this organization may be conserved across related plasmid partition systems.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions, figure legends referenced in text
- **Missing materials affecting confidence** Figures, tables, and supplementary materials referenced but not provided; raw SPR, MST, EMSA, and MD simulation data not available for independent verification

## Reviewer
- **Overall assessment** The manuscript presents a well-structured investigation into ParAF-DNA interactions on the F plasmid partition promoter, combining quantitative biophysical approaches with computational modeling. The central claim of three ParAF dimers binding to overlapping IR motifs is supported by SPR stoichiometry data and is an interesting departure from the previously proposed four-monomer model. However, the absence of key figures and raw data limits full evaluation of the evidence. The modeling and MD simulation components are suggestive but not definitive, and the evolutionary conservation argument relies on sequence analysis that is only partially presented. The work is of interest to the plasmid biology and bacterial cell division communities, but the strength of the conclusions relative to the evidence needs careful scrutiny.

- **Who would be interested in the results, and why** Researchers studying bacterial plasmid segregation, ParA/ParB partition systems, transcriptional autoregulation, and protein-DNA interactions. The proposed cooperative binding model and the potential conservation across type Ia systems would interest those working on plasmid evolution and comparative genomics. The methodological combination of SPR, MST, and MD simulations may also appeal to biophysicists studying protein-DNA recognition.

- **Major strengths** The combination of multiple quantitative techniques (SPR, MST, EMSA) to address stoichiometry is rigorous. The identification of a perfect IR motif as the primary binding site is a clear, testable hypothesis. The inclusion of MD simulations to explore protein flexibility adds a dynamic perspective often missing in such studies. The comparative analysis across related plasmids provides evolutionary context.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that three ParAF dimers bind to the PparABF promoter region with a stoichiometry of 3:1 is central to the paper.
  - **Evidence pointer** Section 3.1, Figure 2C
  - **Concern** The stoichiometry determination relies entirely on SPR signal ratios. The authors acknowledge variability in binding isotherms (Table S1) and do not provide raw sensorgrams or detailed calculations. The assumption that SPR signal is directly proportional to bound protein mass requires validation, especially given the reported aggregation at high concentrations. The discrepancy with the earlier four-monomer model is attributed to mutation differences, but the authors do not directly compare their constructs with those used previously.
  - **Why it matters** The entire model of three dimers binding to overlapping motifs depends on this stoichiometry. If the stoichiometry is incorrect, the proposed binding organization and the conservation argument collapse.
  - **Resolution test** Provide raw SPR data with detailed calculation methods, including how the active protein fraction was determined. Perform independent stoichiometry validation using a technique such as analytical ultracentrifugation or native mass spectrometry. Directly test the previous constructs to resolve the discrepancy.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model validation
  - **Claim pointer** The proposal that three ParAF dimers bind to overlapping IR motifs (IR3-4, IR2-2′, and motif #1) is presented as a structural model.
  - **Evidence pointer** Section 3.3, Figure 5A-C
  - **Concern** The docking and modeling are based on a homology model of ParAF built from ParAP1, with low sequence identity (22%). The authors state that the best docking was observed with a specific DNA curvature, but no scoring metrics, alternative models, or validation of the docking procedure are provided. The claim that motif #1 is bound by only one wHTH of a dimer is speculative and not directly tested.
  - **Why it matters** The proposed overlapping binding model is the core conceptual advance. Without robust structural validation, it remains a hypothesis. The model must be consistent with all biochemical data, including the EMSA results showing no binding when motif #4 is absent.
  - **Resolution test** Provide detailed docking scores, alternative conformations tested, and validation of the homology model. Perform mutagenesis of specific residues in the wHTH and test binding to each IR motif individually. Use techniques such as hydroxyl radical footprinting or FRET to test the proposed overlapping arrangement.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evolutionary claim support
  - **Claim pointer** The statement that similar promoter organization is found in other type Ia partition systems, suggesting a conserved mechanism.
  - **Evidence pointer** Section 3.3, Figure 5C-E, Figure S5
  - **Concern** The comparative analysis is based on sequence similarity searches and logo analysis, but the number of sequences analyzed, the statistical significance of the conservation, and the functional validation in these other systems are not presented. The claim of a "common ancestor" is evolutionary speculation without phylogenetic analysis.
  - **Why it matters** The generality of the proposed model is a key selling point. If the conservation is not robustly demonstrated, the broader significance is diminished.
  - **Resolution test** Provide a clear phylogenetic tree of the analyzed sequences, statistical measures of motif conservation, and ideally functional data (e.g., binding assays) for at least one additional system.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic interpretation
  - **Claim pointer** The MD simulations are used to support the idea that wHTH flexibility is important for cooperative binding.
  - **Evidence pointer** Section 3.5, Figure 4C, Figure S6
  - **Concern** The MD simulations were performed on the apo form of the protein, not on the DNA-bound complex. The relevance of the observed flexibility to DNA binding is inferred but not directly demonstrated. The simulations were run for 40 ns, which may be insufficient to sample relevant conformational states. No free energy calculations or comparisons with a DNA-bound state are provided.
  - **Why it matters** The flexibility argument is used to explain how dimers can adapt to overlapping motifs. Without demonstrating that this flexibility is functionally important for DNA binding, the connection is weak.
  - **Resolution test** Perform MD simulations of the ParAF dimer bound to the IR3-4 DNA motif. Compare the flexibility of the free and bound states. Use mutational analysis to test whether restricting wHTH flexibility affects cooperative binding.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.2
  - **Evidence pointer** "Surface Plasmon Resonance Assays"
  - **Issue** The description of SPR data analysis is brief. The authors mention "survey's recommendations" but do not specify which recommendations or how the fitting was validated.
  - **Required correction** Provide a more detailed description of the SPR data analysis, including the specific model used, goodness-of-fit parameters, and how the stoichiometry was calculated from the signal ratios.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 2.6
  - **Evidence pointer** "Modeling of ParAF Structure and Docking on DNA"
  - **Issue** The parameters for the HADDOCK docking are not fully described. The authors state that the best docking was observed with a 3° angle, but do not specify how this was determined or whether other angles were tested systematically.
  - **Required correction** Provide a table of docking scores for different angles and describe the selection criteria for the best model.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Section 3.1, Figure 2C
  - **Evidence pointer** "Three ParAF Dimers Bind to the Para Promoter Region"
  - **Issue** The stoichiometry plot in Figure 2C is described but not shown. The reader cannot assess the quality of the data or the scatter.
  - **Required correction** Include the stoichiometry plot with error bars and the number of independent experiments.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Section 3.7, Table 1
  - **Evidence pointer** "ADP Stabilizes ParAF but Does Not Increase Its Affinity to PparABF"
  - **Issue** The melting temperature increase of 1.5 °C with ADP is presented as stabilization, but the biological significance of this small change is not discussed.
  - **Required correction** Discuss whether a 1.5 °C shift is physiologically relevant and how it relates to the observed lack of affinity change.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.8
  - **Evidence pointer** "ParBF Increases ParAF Binding Affinity to the Promoter Region"
  - **Issue** The mechanism by which ParBF stimulates ParAF binding is not explored. The authors suggest a conformational change but provide no direct evidence.
  - **Required correction** Add a brief discussion of alternative mechanisms (e.g., ParBF-induced DNA bending) and suggest experiments to distinguish them.

## Risk / unsupported claims
- The claim that three ParAF dimers bind to the promoter with 3:1 stoichiometry is supported by SPR but requires independent validation given the acknowledged variability and aggregation issues.
- The proposed overlapping binding model (IR3-4, IR2-2′, motif #1) is not directly tested and relies on homology modeling with low sequence identity.
- The MD simulation results are used to infer functional relevance of wHTH flexibility without simulations of the DNA-bound state.
- The evolutionary conservation claim across type Ia systems is based on limited sequence analysis without phylogenetic or functional validation.
- The statement that the promoter organization "may have evolved from a common ancestor" is speculative and not supported by the data presented.
- The claim that ParBF induces a conformational change in ParAF is hypothetical and not directly tested.
- The KD values from MST and EMSA are reported but the variability and number of replicates are not fully disclosed.
- The statement that "no band shift was observed when the DNA fragment did not harbor the motif #4, whatever the combination tested" is presented without showing the corresponding gels.