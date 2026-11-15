## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose that integrative network pharmacology, transcriptomic analysis, single-cell RNA sequencing, regulatory-network analysis, and molecular docking prioritize CCR1 and C5AR1 as convergent candidate thromboinflammatory targets shared by Panax notoginseng saponins (PNS) and a panel of 16 stroke-relevant drugs in ischemic stroke.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or statistical outputs provided
- **Missing materials affecting confidence** Full methods, all figures and tables, dataset identifiers beyond GSE56267, docking parameters and validation, single-cell analysis details, statistical thresholds, and any sensitivity or robustness analyses

## Reviewer

- **Overall assessment** The abstract presents a systematic bioinformatics pipeline that is plausible in design and yields a clear prioritized output. The authors are appropriately cautious in framing the findings as hypothesis-generating. However, the abstract alone does not provide sufficient detail to evaluate the technical rigor of the analyses, the validity of the prioritization criteria, or the biological significance of the docking results. The core claim that CCR1 and C5AR1 are convergent candidate targets is supported by the described workflow in outline, but the evidentiary strength cannot be fully assessed from the supplied material.
- **Who would be interested in the results, and why** Researchers in stroke biology, neuroinflammation, and thromboinflammation would find the prioritized targets relevant for hypothesis generation. Investigators working on network pharmacology and multi-omics integration for drug repurposing in neurological disorders may also be interested in the methodological framework. The identification of CCR1 and C5AR1 as shared nodes between a natural product and conventional agents could inform future experimental studies on combination therapies.
- **Major strengths** The study integrates multiple complementary data types, which is appropriate for a prioritization exercise. The authors explicitly acknowledge the hypothesis-generating nature of the findings and do not overclaim causal or mechanistic relationships. The use of independent cross-dataset expression assessment and single-cell sub-clustering adds layers of evidence beyond simple target prediction. The docking step provides a structural dimension that strengthens the plausibility of direct receptor-ligand interactions.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not report any statistical thresholds, multiple-testing corrections, or validation metrics for the network and transcriptomic analyses. The docking affinity scores are presented without comparison to known binders or decoy sets, and no structural validation is described. The single-cell sub-clustering results are stated without cell-type marker definitions or statistical support. These omissions prevent assessment of whether the prioritization is robust or could arise from analytical artifacts.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The combination of network pharmacology with transcriptomic and single-cell data is not entirely novel, but the specific focus on PNS and stroke-relevant drug convergence is a distinctive angle.  
  - Scientific importance: Moderate. The findings are hypothesis-generating and could inform future experimental work, but the abstract does not establish a new biological mechanism or therapeutic principle.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biologists and stroke researchers; the clinical or translational implications are not developed in the abstract.  
  - Technical soundness: Not assessable from the abstract alone. Key methodological details and validation steps are absent.  
  - Readability for nonspecialists: The abstract is dense and assumes familiarity with network pharmacology, single-cell analysis, and docking terminology. A nonspecialist would struggle to follow the logic of prioritization.
- **Recommendation posture** Currently not established from the provided evidence. The abstract outlines a reasonable pipeline, but the absence of methodological detail and validation metrics means the core claims cannot be evaluated. A supportive posture would require access to the full manuscript and evidence of technical rigor.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The screening framework yielded 79 shared predicted pharmacological targets and 10 disease-associated candidates, with CCR1 and C5AR1 prioritized based on network connectivity, consistent disease-associated expression, and links to thromboinflammatory pathways.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract does not report the criteria or thresholds used to define "shared predicted pharmacological targets," "disease-associated candidates," or the prioritization of CCR1 and C5AR1 over the other eight candidates. No statistical metrics, enrichment scores, or connectivity measures are provided.  
- **Why it matters** Without explicit thresholds and ranking criteria, the prioritization could be arbitrary or driven by analytical choices rather than biological signal. The reader cannot determine whether the selection of CCR1 and C5AR1 is robust or a consequence of parameter selection.  
- **Resolution test** Provide the full prioritization criteria, including statistical thresholds, network metrics, and the comparative scores for all 10 candidates. Show that CCR1 and C5AR1 are separated from the remaining candidates by predefined and justified cutoffs.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** BATF2 and SPI1 expression positively correlated with both C5AR1 and CCR1 in GSE56267.  
- **Evidence pointer** GSE56267; location not provided  
- **Concern** The abstract states a correlation result but does not report the correlation coefficients, significance levels, or the number of samples in GSE56267. It is unclear whether this correlation is specific to ischemic stroke conditions or reflects general co-expression patterns.  
- **Why it matters** The transcription-factor correlation is presented as supporting evidence for regulatory links. Without effect sizes and significance, the claim is unverifiable and could be a spurious correlation driven by a small sample or confounding variables.  
- **Resolution test** Report correlation coefficients, p-values or confidence intervals, sample sizes, and a demonstration that the correlation is specific to stroke-relevant conditions rather than a generic expression pattern.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** Myeloid sub-clustering showed that C5ar1 was broadly distributed across stroke-associated microglial and monocyte/macrophage states, whereas Ccr1 was more restricted to activated inflammatory and infiltrating myeloid populations.  
- **Evidence pointer** Single-cell RNA sequencing sub-clustering; location not provided  
- **Concern** The abstract does not describe the single-cell dataset, the clustering method, the number of cells or clusters, or the statistical basis for the differential distribution of C5ar1 and Ccr1 across cell states. No marker genes or cluster annotations are provided.  
- **Why it matters** The differential cell-type distribution is a key part of the biological interpretation. Without details on clustering quality, cell-state definitions, and statistical comparisons, the claim that C5ar1 is broad and Ccr1 is restricted cannot be evaluated.  
- **Resolution test** Provide the single-cell dataset source, clustering parameters, cluster annotations with marker genes, and statistical tests comparing the distribution of C5ar1 and Ccr1 across identified cell states.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** GN docking of all fourteen network-defined receptor-ligand systems identified five complexes with docking affinity scores between -8.06 and -10.94 kcal/mol.  
- **Evidence pointer** GN docking; location not provided  
- **Concern** The abstract reports docking scores but does not provide a baseline for interpretation. No comparison to known active compounds, decoy molecules, or experimental binding data is given. The selection of the five complexes from fourteen is not justified.  
- **Why it matters** Docking scores are highly dependent on the scoring function, receptor preparation, and ligand conformations. Without a threshold for what constitutes a meaningful binding affinity or a comparison to validated binders, the scores are not interpretable as evidence of functional interaction.  
- **Resolution test** Provide the docking protocol, a justification for the affinity threshold, comparison to known binders or decoys, and ideally experimental validation or at least a discussion of the limitations of computational binding predictions.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Candidate list  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract lists 10 candidates but does not explain why ITK, CDK2, VDR, S1PR2, KIF11, FAP, PRKCD, and MAOA were deprioritized relative to CCR1 and C5AR1.  
- **Required correction** Briefly state the comparative criteria that led to the exclusion of the other eight candidates, or refer to a table that provides this information.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Dataset identifiers  
- **Evidence pointer** GSE56267; location not provided  
- **Issue** Only one dataset identifier is mentioned. The abstract refers to "independent cross-dataset expression assessment" but does not name the other datasets.  
- **Required correction** List all dataset identifiers used in the study, including those for bulk transcriptomic and single-cell analyses.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretability  
- **Affected element** Docking score units  
- **Evidence pointer** GN docking; location not provided  
- **Issue** The docking scores are reported in kcal/mol, which is standard, but the abstract does not state whether these are binding free energies or scoring function outputs.  
- **Required correction** Clarify the nature of the reported scores and the software version used for docking.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Thromboinflammatory targets"  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The term "thromboinflammatory targets" is used without a definition of how a target is classified as thromboinflammatory versus merely inflammatory or thrombotic.  
- **Required correction** Define the criteria used to classify targets as thromboinflammatory, or state that this is an interpretive label applied post hoc.

## Risk / unsupported claims

- The claim that CCR1 and C5AR1 are "convergent candidate thromboinflammatory nodes" is supported only in outline by the abstract; the underlying network and expression evidence cannot be verified without full data.
- The correlation between BATF2 and SPI1 expression and CCR1/C5AR1 is reported without statistical detail and is therefore not assessable.
- The differential distribution of C5ar1 and Ccr1 across myeloid cell states is stated without supporting single-cell statistics or cluster annotations.
- The docking scores are presented without a baseline or validation, so the claim of five favorable complexes is not interpretable as evidence of binding.
- The abstract explicitly disclaims pharmacological synergy, direct receptor coupling, and causal mechanisms, which is appropriate, but the absence of these claims does not compensate for the lack of technical detail needed to assess the prioritization itself.