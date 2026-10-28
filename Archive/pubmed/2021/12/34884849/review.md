## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Computational structural biology analysis of HIF1-HRE interaction at the −964G>A polymorphism site of the HLA-G promoter
- **Shared manuscript claim summary** The authors used homology modeling, protein-DNA docking, and molecular dynamics simulations to compare HIF1 binding to HRE sequences containing either the −964G or −964A allele. They report that the G allele forms more hydrogen bonds and van der Waals contacts, yields a more stable complex, and is therefore bound more specifically by HIF1.
- **Visible evidence base** Abstract, Introduction, Results and Discussion, Materials and Methods, Tables 1 and 2, Figures 1 through 9 (referenced but not all visible in the provided text), Supplementary material references
- **Missing materials affecting confidence** Figures 1 through 9 are referenced but not provided in the submitted text; Supplementary Figures S1 through S4 are referenced but not provided; Table 1 and Table 2 contents are described but not fully visible; no experimental validation data (e.g., EMSA, ChIP, reporter assays) are included

## Reviewer
- **Overall assessment** This manuscript presents a computational analysis of HIF1 binding to the HLA-G promoter HRE containing either the −964G or −964A allele. The work addresses a biologically relevant question regarding how a common polymorphism may affect transcription factor binding and downstream HLA-G expression under hypoxic conditions. The computational pipeline is standard and generally well described. However, the central claim that the G allele confers more stable and specific HIF1 binding rests entirely on in silico predictions without experimental validation. Several methodological details are insufficiently justified, and the interpretation of the molecular dynamics results is somewhat overextended relative to the evidence presented. The manuscript is of moderate interest to specialists in structural bioinformatics and HLA-G biology, but the lack of experimental corroboration limits the strength of the conclusions.

- **Who would be interested in the results, and why** Researchers studying HLA-G regulation, particularly in the context of hypoxia and immune modulation, would find the results relevant. Computational biologists working on protein-DNA docking and molecular dynamics of transcription factor complexes may also be interested in the methodological approach. Clinicians or geneticists investigating the −964G>A polymorphism in relation to pregnancy complications, transplantation outcomes, or cancer prognosis could find the structural rationale useful for interpreting association studies.

- **Major strengths** The study addresses a clinically and biologically relevant polymorphism with a clear hypothesis. The computational workflow is comprehensive, including homology modeling, docking, and 200 ns molecular dynamics simulations. The authors made a reasonable choice of template (mouse HIF2-DNA complex) with appropriate sequence identity justification. The analysis of intermolecular contacts at the atom-pair level provides a detailed mechanistic perspective. The discussion appropriately acknowledges the limitation of excluding the exon 2 HRE and cofactors.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors conclude that "HIF1 binds in a more stable and specific manner at the HRE with G allele" based solely on computational predictions.
- **Evidence pointer** Abstract; Section 2.3; Section 2.4; Table 2; Figures 3 through 6
- **Concern** The central conclusion is derived entirely from in silico methods. No experimental validation (e.g., electrophoretic mobility shift assay, surface plasmon resonance, chromatin immunoprecipitation, or reporter gene assays) is provided to confirm that HIF1 indeed binds the −964G allele with higher affinity or specificity than the −964A allele. Computational docking scores and molecular dynamics stability metrics are predictive but not definitive evidence of biological binding preferences.
- **Why it matters** The manuscript's primary claim has direct implications for understanding how a common genetic variant affects HLA-G expression under hypoxia. If the computational prediction is incorrect, the conclusions could mislead subsequent functional studies or clinical interpretations. The Nature-style standard requires that strong mechanistic claims be supported by experimental evidence or at minimum clearly framed as hypotheses.
- **Resolution test** Provide experimental binding data (e.g., EMSA or surface plasmon resonance) comparing HIF1 affinity for the −964G and −964A HRE probes, or temper the conclusion to state that computational predictions suggest a potential binding preference that requires experimental confirmation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the model with the lowest RMSD (0.39 Å) was selected as the best HIF1 structure, but also report an all-atom RMSD of 6.29 Å without outlier rejection.
- **Evidence pointer** Section 2.1; Supplementary Figures S2 and S3
- **Concern** The RMSD values reported are inconsistent and the selection criterion is unclear. An RMSD of 0.39 Å with five cycles of outlier rejection is exceptionally low and likely reflects overfitting to a subset of well-aligned residues. The all-atom RMSD of 6.29 Å without outlier rejection suggests substantial structural divergence from the template. The authors attribute this to loop regions, but the domain-specific RMSD values (0.64 to 0.96 Å) are also surprisingly low for homology models. The manuscript does not clarify how many residues were excluded during outlier rejection or whether the final model retains correct domain packing.
- **Why it matters** The quality of the HIF1 model directly affects the reliability of the docking results and all subsequent conclusions. If the model is not accurately representing the true HIF1 structure, the observed differences in binding between the two alleles may be artifacts of the modeling procedure rather than genuine biological properties.
- **Resolution test** Provide a detailed description of the model selection process, including the number of residues used for RMSD calculation, the distribution of outlier rejections, and a superposition figure showing the full model against the template. Consider using additional validation metrics such as MolProbity or ProSA to support model quality.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "no HIF1 residue formed hydrogen bridges directly with the G/A variation site, only VdW forces act at the interaction of these bases."
- **Evidence pointer** Section 2.3; Figure 3
- **Concern** This observation is presented as a key finding, but the mechanistic interpretation is underdeveloped. If the polymorphic base itself is not directly hydrogen-bonded by HIF1 residues, the authors should explain more thoroughly how the G-to-A change at position −964 alters binding stability. The indirect effects through altered DNA conformation, changes in the complementary strand interactions, or long-range electrostatic effects are mentioned only superficially.
- **Why it matters** The manuscript aims to explain the differential binding at the atom-pair level. If the direct contact analysis does not reveal a clear mechanism, the reader is left without a satisfying explanation for why the G allele binds more stably. A more detailed analysis of the structural consequences of the polymorphism is needed.
- **Resolution test** Provide a more detailed structural analysis of how the −964A allele alters the local DNA conformation, base stacking, or electrostatic potential, and how these changes propagate to affect HIF1 binding. Consider analyzing the full contact network, including water-mediated interactions and backbone contacts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors describe the molecular dynamics simulation protocol but do not provide sufficient details for replication.
- **Evidence pointer** Section 3.4
- **Concern** The methods section states that simulations were performed using GROMACS v.2019 with the AMBER-99SB force field and AMBER-Parmbsc1 parameters for DNA, but several critical parameters are missing. The equilibration protocol is described only as "NVT" and "NPT" without specifying temperature coupling methods, pressure coupling algorithms, or the duration of each equilibration phase. The number of replicates (if any) is not stated. The analysis of trajectories is described only in terms of RMSD, RMSF, and RoG, but the specific tools and settings used for these calculations are not provided.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without complete methodological details, other researchers cannot replicate the simulations or verify the results. This is particularly important given that the conclusions depend entirely on the simulation outcomes.
- **Resolution test** Provide a complete description of the simulation protocol, including all force field parameters, equilibration steps with durations, temperature and pressure coupling schemes, integration time steps, and analysis tools with version numbers. Consider depositing the simulation input files and trajectories in a public repository.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that "the −964A allele altered HRE geometry in the complex HIF1-HRE-964A, resulting in interaction loss between partner molecules."
- **Evidence pointer** Section 2.3; Figure 3
- **Concern** The causal direction of this observation is not clearly established. The authors imply that the altered geometry is a consequence of the A allele, but it could also be that the docking procedure produced a different binding mode for the A allele complex that is not biologically relevant. The manuscript does not discuss whether the docking results were validated against known HIF1-DNA complex structures or whether the observed conformational differences are within the range of thermal fluctuations.
- **Why it matters** The interpretation of the structural differences between the two complexes is central to the manuscript's conclusions. If the observed differences are artifacts of the docking procedure rather than genuine biological effects, the conclusions would be invalid.
- **Resolution test** Perform additional docking runs with different initial conditions or use an alternative docking method to confirm that the observed differences are robust. Compare the docking poses with known experimental structures of HIF1-DNA complexes to validate the binding mode.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "Human Antigen Leukocyte-G" which is an unusual ordering of the HLA-G name. The standard nomenclature is "Human Leukocyte Antigen-G."
- **Required correction** Correct the nomenclature to "Human Leukocyte Antigen-G" throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The manuscript states "the template chosen for modeling must be a protein-DNA complex, in which the protein has at least 30% of identity to HIF1." This is presented as a general rule, but the 30% threshold is not a universally accepted standard for homology modeling. The justification for this threshold is not provided.
- **Required correction** Either provide a reference for the 30% threshold or rephrase to indicate that this was the authors' criterion for template selection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3; Table 2
- **Issue** The manuscript states that "the second-best classified cluster for HIF1-HRE-964G (cluster 20) and the fourth-best classified cluster for HIF1-HRE-964A (cluster 2) presented the most similar poses to the reference complex." The rationale for selecting these clusters over the top-ranked clusters is not fully explained. The RMSD values to the reference complex are mentioned but not shown.
- **Required correction** Provide the RMSD values for the selected clusters and explain why the top-ranked clusters were rejected despite having better HADDOCK scores.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4; Figures 4 through 6
- **Issue** The manuscript reports RMSD, RoG, and RMSF values but does not provide statistical measures of uncertainty or comparisons across replicate simulations. The figures are described as showing differences between complexes, but no statistical tests are mentioned.
- **Required correction** Provide standard deviations or confidence intervals for the reported metrics and, if appropriate, perform statistical comparisons between the two complexes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1
- **Evidence pointer** Section 1
- **Issue** The introduction cites several references but does not discuss previous computational studies of HIF1-DNA interactions or previous structural analyses of the −964G>A polymorphism. This limits the reader's ability to assess the novelty of the approach.
- **Required correction** Add a brief discussion of prior computational or structural studies of HIF1-DNA binding and any previous analyses of the −964G>A polymorphism.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The manuscript states that "HIF1 has higher structural stability when bound to the HRE containing the −964G allele" based on RMSD values, but the absolute RMSD values are not reported in the text. The reader must interpret the figures without knowing the numerical values.
- **Required correction** Report the numerical RMSD values in the text or in a table for clarity.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The manuscript contains several instances of awkward phrasing and minor grammatical errors. For example, "the gene may be induced in hypoxic conditions by the interaction with the hypoxia inducible factor-1" could be more clearly phrased. The phrase "pair-atom level" is unusual and could be clarified.
- **Required correction** Perform a thorough language edit to improve clarity and readability.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 3
- **Evidence pointer** Section 3
- **Issue** The manuscript does not state whether the structural models, docking results, or simulation trajectories are available in a public repository. This limits the ability of other researchers to verify or build upon the results.
- **Required correction** Provide a data availability statement and consider depositing the models and trajectories in a public repository such as Zenodo or Figshare.

## Risk / unsupported claims
- The claim that "HIF1 binds in a more stable and specific manner at the HRE with the −964G allele" is unsupported by experimental evidence and should be framed as a computational prediction.
- The statement that "the −964A allele altered HRE geometry" implies a causal relationship that is not established by the docking and simulation data alone.
- The claim that the selected docking poses are representative of the biologically relevant binding mode is not validated against experimental structures or alternative docking methods.
- The assertion that the homology model accurately represents the HIF1 quaternary structure is not fully supported given the inconsistent RMSD values reported.
- The biological significance of the observed differences in hydrogen bond counts (16 vs. 11) and van der Waals contacts (81 vs. 87) is not established, as the relationship between these metrics and binding affinity is not quantified.
- The statement that "the G allele showed higher affinity for HIF1 than the A allele" in the discussion of prior experimental data is attributed to reference 23, but the specific experimental evidence is not described in the manuscript.