## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure descriptions
- **Assessment boundary** Technical soundness of the AlphaFill algorithm, validity of the transplantation approach, quality of the presented examples, and suitability of the resource for the stated purpose
- **Shared manuscript claim summary** The authors present AlphaFill, an algorithm that transplants small molecules, cofactors, and ions from experimentally determined structures (PDB-REDO) into AlphaFold-predicted protein models based on sequence and structural similarity. The resulting AlphaFill databank contains 21,899 models with at least one transplanted compound, totaling 108,997 compounds. The authors claim this resource helps interpret biological function and design experiments.
- **Visible evidence base** Full manuscript text, methods section, table descriptions, figure descriptions, and web resource description
- **Missing materials affecting confidence** Actual figures and tables are not viewable in the provided text. Quantitative validation metrics beyond counts of transplanted compounds are not provided. No comparison against alternative approaches or experimental validation of transplanted ligand poses is presented.

## Reviewer
- **Overall assessment** The manuscript describes a conceptually straightforward and potentially useful resource for the structural biology community. The idea of enriching AlphaFold models with biologically relevant small molecules and ions from homologous experimental structures is sensible and addresses a genuine gap in the current AlphaFold database. However, the manuscript as presented lacks rigorous quantitative validation of the transplantation accuracy, does not systematically assess false positives or negatives, and the examples provided are largely qualitative. The technical approach is reasonable but several parameters are set based on empirical judgment without sensitivity analysis. The resource itself appears functional and well-designed from a user perspective, but the scientific claims about utility and accuracy are not fully substantiated by the evidence presented.
- **Who would be interested in the results, and why** Structural biologists, computational biologists, and researchers using AlphaFold models for hypothesis generation would find this resource valuable. The ability to quickly add cofactors and ligands to predicted structures could aid in interpreting function, designing mutagenesis experiments, and setting up molecular dynamics simulations. The resource is particularly relevant given the widespread adoption of AlphaFold models across the life sciences.
- **Major strengths** The manuscript addresses a clear and important gap in the AlphaFold database. The approach is pragmatic and computationally efficient. The web interface appears user-friendly and provides important provenance information. The authors acknowledge limitations appropriately, particularly regarding quantitative accuracy of ligand interactions.
- **Major Concerns** The manuscript lacks quantitative validation of transplantation accuracy. The choice of the 70% sequence identity threshold is not rigorously justified. The handling of conformational flexibility and multiple ligand binding states is not addressed. The error case described for MSH2 illustrates a systematic problem that may be more widespread than acknowledged.
- **Minor Comments** The compound selection criteria are described but the rationale for specific cutoffs is not fully explained. The discussion of future work is somewhat speculative. The manuscript would benefit from clearer guidance on how to interpret the RMSD values provided.
- **Technical failings that need to be addressed before the case is established** Lack of quantitative accuracy assessment for transplanted ligand positions; absence of sensitivity analysis for key parameters; insufficient validation that transplanted ligands do not clash with the protein model.
- **Assessment against Nature-style criteria** Originality: moderate. The concept of transplanting ligands from homologs is not entirely novel but the systematic application to the entire AlphaFold database is a useful contribution. Scientific importance: moderate to high. The resource could be widely used, but the lack of validation limits confidence in its outputs. Interdisciplinary readership: the resource is relevant to a broad range of life scientists, but the manuscript is written primarily for a structural biology audience. Technical soundness: the approach is technically reasonable but insufficiently validated. Readability for nonspecialists: the manuscript is generally clear but assumes familiarity with structural biology concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The resource has clear potential value, but the manuscript needs additional validation and sensitivity analysis before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that AlphaFill "transplants" small molecules and ions to AlphaFold models, implying these placements are reliable enough for biological interpretation.
- **Evidence pointer** Results section, Examples subsection; location not provided
- **Concern** The manuscript provides no quantitative assessment of how accurately the transplanted ligands are positioned relative to what would be expected in a true experimental structure. The examples shown are qualitative visual inspections. There is no systematic evaluation of whether the local structural alignment procedure reliably places ligands in chemically sensible positions, nor any analysis of steric clashes or unfavorable interactions between transplanted ligands and the AlphaFold model.
- **Why it matters** Without quantitative validation, users cannot assess the reliability of individual ligand placements. The stated purpose of helping scientists "interpret biological function and design experiments" requires confidence in the positional accuracy of the transplanted compounds. A systematic error in ligand placement could lead to incorrect biological conclusions.
- **Resolution test** Provide a validation set where AlphaFill predictions are compared against experimentally determined structures of the same protein with bound ligands, reporting RMSD distributions for ligand positions, clash rates, and success rates for recovering known binding sites.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that a 70% sequence identity cutoff is used to filter homologous structures, described as "consistent with our other software that employs homology."
- **Evidence pointer** Results section, "A procedure for transplanting small molecules and ions to AlphaFold models"; location not provided
- **Concern** The choice of 70% sequence identity is presented without sensitivity analysis. It is unclear how this threshold affects the number and quality of transplants. A more permissive threshold might increase coverage but introduce more false positives, while a stricter threshold might miss relevant homologs. The manuscript does not explore this trade-off.
- **Why it matters** The threshold directly determines which ligands are transplanted and which are not. If the threshold is too permissive, users may be misled by incorrect ligand placements from distantly related proteins. If too strict, the resource may miss many biologically relevant annotations. The lack of analysis undermines confidence in the resource's completeness and accuracy.
- **Resolution test** Perform a sensitivity analysis varying the sequence identity threshold (e.g., 50%, 60%, 70%, 80%) and report the number of models with transplants, the number of compounds transplanted, and a qualitative assessment of transplant quality at each threshold.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript describes transplanting ligands based on local structural alignment of backbone atoms within 6Å of the compound, using the RMSD of this alignment as a quality metric.
- **Evidence pointer** Results section, "A procedure for transplanting small molecules and ions to AlphaFold models"; location not provided
- **Concern** The manuscript does not address how conformational heterogeneity in ligand binding is handled. Many proteins adopt multiple conformations with different ligand binding modes, and AlphaFold typically predicts a single conformation. The approach appears to assume a single static binding mode, which may not capture the range of biologically relevant states. The example of kinases, where active and inactive states differ substantially, is mentioned but not systematically analyzed.
- **Why it matters** Users may incorrectly assume that the transplanted ligand represents the only or primary binding mode. For proteins with multiple conformational states, the ligand placement may be misleading. The resource should either provide information about conformational variability or clearly state its limitations in this regard.
- **Resolution test** For a set of proteins known to adopt multiple ligand-bound conformations, compare AlphaFill placements against the range of experimentally observed binding modes and report how often the transplanted position matches a known binding mode.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that AlphaFill "can help scientists to better understand and use predicted structure models to answer relevant scientific questions."
- **Evidence pointer** Discussion section; location not provided
- **Concern** The examples provided are illustrative but do not demonstrate that the resource leads to new biological insights that would not be readily obtainable by other means. The MSH2 example, where an erroneous ligand placement is described, actually highlights a limitation rather than a success. The manuscript would benefit from a case study where AlphaFill enabled a specific biological hypothesis or experiment that would have been difficult without it.
- **Why it matters** The stated value proposition of the resource is its utility for biological research. Without a compelling demonstration of this utility, the resource may be seen as a convenience rather than a significant scientific contribution.
- **Resolution test** Provide a detailed case study where AlphaFill annotations led to a specific, testable biological hypothesis, ideally with some preliminary experimental or computational validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Compound selection criteria
- **Evidence pointer** Methods section, "Input data"; location not provided
- **Issue** The criteria for including compounds in the AlphaFill list are described as based on occurrence frequency and CoFactor database presence, but the specific frequency cutoff (1600 occurrences) is not justified.
- **Required correction** Provide a brief rationale for the 1600 occurrence cutoff or show that results are not sensitive to this choice.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure descriptions
- **Evidence pointer** Results section, Examples subsection; location not provided
- **Issue** The figure descriptions are detailed but would benefit from a summary figure showing the overall workflow of the AlphaFill algorithm in a single schematic.
- **Required correction** Add a workflow diagram as a new figure or as part of an existing figure to help nonspecialist readers understand the method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** RMSD thresholds
- **Evidence pointer** Results section, "A web-based user interface for the AlphaFill databank"; location not provided
- **Issue** The manuscript states that transplants with global Cα alignment RMSD > 5.0Å or local alignment RMSD > 1.0Å are marked as low confidence, but the basis for these specific thresholds is not explained.
- **Required correction** Provide justification for these thresholds or cite prior work establishing them.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Comparison with existing resources
- **Evidence pointer** Discussion section; location not provided
- **Issue** The manuscript does not compare AlphaFill with existing resources that provide ligand annotations for protein models, such as the PDBe-Knowledge Base or other functional annotation databases.
- **Required correction** Add a brief comparison with existing resources, highlighting what AlphaFill adds beyond current offerings.

## Risk / unsupported claims
- The claim that transplanted ligands are suitable for "qualitative analysis in terms of heme-protein interactions" is not supported by quantitative validation.
- The claim that AlphaFill models can help "design experiments" is plausible but not demonstrated with specific examples.
- The statement that the 70% sequence identity threshold is "consistent with our other software" does not establish its appropriateness for this specific application.
- The assertion that the resource "can help scientists to better understand and use predicted structure models" is a reasonable expectation but is not backed by user studies or systematic evaluation.
- The claim that the AlphaFill database contains 21,899 models with at least one transplanted compound is a factual statement, but the biological significance of this number is not contextualized.