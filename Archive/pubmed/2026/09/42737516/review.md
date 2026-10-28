## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and internal consistency of the claims as presented; no external data verification performed
- **Shared manuscript claim summary** The authors report the first genome-wide identification of 15 RGF genes in hexaploid wheat, classified into five homeologous groups on chromosomes 2 and 6. They describe root-enriched expression of TaRGF5, drought-induced repression of TaRGF5 homeologs, a unique BES1 cis-element in TaRGF5B, and computational evidence for TaRGF5–TaRGI3 interaction via docking and molecular dynamics simulations.
- **Visible evidence base** Results sections 2.1–2.10, Figures 1–11 (referenced), Tables 1 and S1–S5 (referenced), Supplementary Data S1–S4 (referenced), Materials and Methods sections 4.1–4.8
- **Missing materials affecting confidence** Figures, tables, and supplementary data files were not provided; only the manuscript text was available for review. This limits verification of all quantitative results, sequence alignments, phylogenetic trees, expression data, and structural models.

## Reviewer
- **Overall assessment** This manuscript presents a descriptive bioinformatics analysis of the RGF gene family in wheat, with additional computational predictions of receptor interactions. The work addresses a genuine gap in wheat peptide signaling research and provides a useful catalog of gene family members. However, the study is largely computational and descriptive, with no experimental validation of any predicted function, interaction, or regulatory mechanism. The evidence for the central claims regarding TaRGF5's role in drought-associated root signaling is circumstantial and based entirely on in silico predictions. Several methodological details are unclear or potentially problematic, and the absence of key figures and supplementary data prevents full evaluation. The manuscript would benefit from substantial revision and additional experimental support before publication in a high-impact venue.
- **Who would be interested in the results, and why** Researchers studying plant peptide hormones, root development, and abiotic stress responses in cereals would find this work relevant. The gene family inventory and expression patterns provide a foundation for future functional studies in wheat. The computational prediction of the TaRGF5–TaRGI3 interaction may interest those working on peptide-receptor pairs in monocots. However, the lack of experimental validation limits the audience to those seeking initial descriptive data rather than mechanistic insights.
- **Major strengths** The study addresses a previously unexplored gene family in an important crop species. The identification of 15 members with homeologous relationships is systematically presented. The combination of phylogenetic, expression, promoter, and structural analyses provides a multi-faceted descriptive framework. The authors appropriately acknowledge limitations of computational predictions in the discussion.
- **Major Concerns** The concerns below identify issues that must be addressed before the claims can be considered established.
- **Minor Comments** The minor comments below identify issues that should be corrected to improve clarity and rigor.
- **Technical failings that need to be addressed before the case is established** R1-M1 (expression data provenance and analysis), R1-M2 (docking methodology and interpretation), R1-M3 (MD simulation validation), R1-M4 (BES1 cis-element claim), R1-M5 (phylogenetic methodology)
- **Assessment against Nature-style criteria** Originality: moderate. The gene family identification is novel for wheat, but the approach is standard and the conceptual advance is limited. Scientific importance: moderate. The work provides a resource but does not establish functional significance. Interdisciplinary readership: limited. The content is specialized to plant molecular biology and may not attract broad attention. Technical soundness: questionable in several areas as detailed in the concerns below. Readability for nonspecialists: acceptable but with room for improvement in explaining the significance of findings.
- **Recommendation posture** Currently not established from the provided evidence. The descriptive gene family analysis may be publishable in a specialized journal after revision, but the stronger claims regarding TaRGF5 function and receptor interaction require experimental validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that RNA-seq data revealed root-enriched expression for all TaRGF genes and that TaRGF5 exhibited the most root-preferential expression, with drought-induced downregulation.
- **Evidence pointer** Section 2.3, Figure 5, Section 4.3
- **Concern** The RNA-seq analysis combines data from three different BioProjects (PRJDB38512, PRJNA925925, PRJNA369686) with different cultivars, sequencing platforms, and presumably different experimental conditions. The methods do not describe how batch effects were handled, how normalization was performed across datasets, or whether the drought treatment conditions were comparable. The expression values are presented as log2(TPM) with a threshold of −49.8 for non-detection, which is an unusual transformation that needs justification. The statistical analysis for differential expression under drought is not described.
- **Why it matters** The central claim of root-enriched TaRGF5 expression and drought repression depends entirely on the validity of this cross-dataset analysis. Without proper batch correction and statistical testing, the observed patterns could be artifacts of technical variation rather than biological signal.
- **Resolution test** Provide a detailed description of the bioinformatics pipeline including quality filtering, alignment parameters, quantification method, and normalization strategy. Describe how batch effects across the three BioProjects were addressed. Include statistical tests for differential expression with appropriate multiple testing correction. Show that the drought treatment conditions are comparable across datasets or justify their combination.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that molecular docking predicts a potential TaRGF5–TaRGI3 interaction with favorable energetics and conserved sulfotyrosine-mediated binding.
- **Evidence pointer** Section 2.9, Table 1, Section 4.7
- **Concern** The docking methodology has several issues. First, the active residues for TaRGI3 are stated as "205, 207, 208, 228, 230, 232, 254, and 256" but the rationale for selecting these specific residues is not provided. Second, the HADDOCK score for the wheat complex (−105.3 ± 2.8) is substantially less favorable than the Arabidopsis reference (−202.4 ± 1.2), yet the authors interpret this as supporting an interaction. Third, the manuscript does not report whether the docking results were validated by comparison with the known crystal structure (PDB 5HZ3) beyond reproducing the complex. Fourth, the statement that the wheat score "remains well below the threshold for non-specific interactions" requires a cited threshold value.
- **Why it matters** The predicted TaRGF5–TaRGI3 interaction is a key claim of the manuscript. If the docking methodology is not rigorously justified and the results not properly benchmarked, the interaction prediction is not reliable.
- **Resolution test** Justify the selection of active residues with structural or sequence conservation evidence. Provide a benchmark of the docking protocol against the known Arabidopsis complex with quantitative metrics. Report the HADDOCK score distribution for decoy or negative control complexes to demonstrate specificity. Cite and justify the threshold used to distinguish specific from non-specific interactions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that molecular dynamics simulations demonstrate stable interaction between TaRGF5 and TaRGI3 over 100 ns.
- **Evidence pointer** Section 2.10, Figure 11, Section 4.8
- **Concern** The MD simulation section reports only RMSD, RMSF, and hydrogen bond analyses. No information is provided on the equilibration protocol beyond "3 ns of equilibration," the number of replicate simulations, the choice of water model and salt concentration, or the criteria for determining that the system reached equilibrium. The manuscript does not report binding free energy calculations (e.g., MM-PBSA or MM-GBSA) that would provide a more quantitative measure of binding affinity. A single 100 ns trajectory is generally considered insufficient to establish stable binding for a peptide-receptor complex.
- **Why it matters** The claim of a stable interaction is based on a single trajectory with limited analysis. Without replicates, free energy calculations, or longer timescales, the stability claim is not robust.
- **Resolution test** Provide details on the number of replicate simulations and the convergence criteria. Report binding free energy estimates using established methods. Show that the key interactions (e.g., sulfotyrosine-arginine salt bridge) are maintained throughout the simulation with appropriate distance and angle analyses. If replicates are not feasible, justify why a single trajectory is sufficient.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that a unique BES1 transcription factor binding site was predicted exclusively in the TaRGF5B promoter, linking brassinosteroid signaling to peptide-mediated root regulation.
- **Evidence pointer** Section 2.7, Figure 8, Section 4.6
- **Concern** The promoter analysis relies on computational prediction tools (BDGP, Promoter 2.0, PLACE, PlantRegMap) without experimental validation. The claim of a "unique" BES1 site is based on the absence of this site in other TaRGF promoters, but the statistical significance of this uniqueness is not assessed. The functional relevance of a predicted cis-element is speculative without experimental evidence such as ChIP-seq, electrophoretic mobility shift assays, or reporter gene constructs.
- **Why it matters** The BES1 finding is presented as a notable result linking brassinosteroid signaling to RGF function. If this is based solely on a computational prediction with no experimental support, the claim is overstated.
- **Resolution test** Provide the prediction scores and thresholds used for BES1 site identification. Assess whether the BES1 site is statistically overrepresented in TaRGF5B compared to other promoters. Clearly state that this is a computational prediction requiring experimental validation, and temper the language in the discussion accordingly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that phylogenetic analysis revealed TaRGF5 homeologs show the highest similarity to Arabidopsis thaliana RGF5.
- **Evidence pointer** Section 2.2, Figure 4, Section 4.2
- **Concern** The phylogenetic analysis methods are described only briefly. The manuscript states that "mature protein sequences were analyzed as the full-length precursors following signal-peptide cleavage" which is contradictory. The alignment method, model selection, and tree inference approach are not described in sufficient detail. The bootstrap support values for the key clade containing TaRGF5 and AtRGF5 are not reported in the text.
- **Why it matters** The phylogenetic placement of TaRGF5 is used to justify the functional hypothesis regarding receptor interaction. If the tree topology is not robustly supported, the evolutionary inference is weakened.
- **Resolution test** Clarify whether full-length or mature sequences were used. Provide details on alignment software, model selection (e.g., ModelFinder), and tree inference method (e.g., IQ-TREE or RAxML). Report bootstrap support values for key nodes, particularly the clade uniting TaRGF5 with AtRGF5.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states "identifying 15 genes" but the results section describes "five putative TaRGFs" representing "15 RGF gene family members." This distinction between genes and members is confusing.
- **Required correction** Clarify the relationship between the five putative TaRGFs and the 15 gene family members. Specify whether the five are unique genes with homeologs counted separately.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.3.1
- **Evidence pointer** Section 4.3.1, dataset list
- **Issue** The BioProject accessions are provided but the specific sample accessions, number of replicates, and tissue types for each dataset are not listed.
- **Required correction** Provide a supplementary table listing all sample accessions, tissue types, developmental stages, and treatment conditions used in the analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1, paragraph 1
- **Issue** The text states "a total of five putative TaRGFs were identified, representing the full complement of 15 RGF gene family members." This is ambiguous regarding whether five or 15 genes were identified.
- **Required correction** Rewrite to clearly state that 15 gene models were identified, corresponding to five homeologous groups.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, Figure 5
- **Issue** The text mentions "expression values of −49.8 (threshold for non-detection)" which is an unusual way to represent undetectable expression. This value appears to be an artifact of the log2 transformation of very small TPM values.
- **Required correction** Explain the transformation clearly and justify why this threshold was chosen. Consider using standard TPM values or a different visualization approach.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.7.3
- **Evidence pointer** Section 4.7.3, docking parameters
- **Issue** The manuscript states that HADDOCK "easy-interface default settings" were used but does not specify the version or the exact parameters for the active and passive residues.
- **Required correction** Provide the HADDOCK version and a detailed list of parameters used, including the definition of active and passive residues for both receptor and ligand.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.8
- **Evidence pointer** Section 2.8, paragraph 1
- **Issue** The text states "the fact that TaRGF5 homeologs together with AtRGF5 suggests that both peptides may share analogous receptor-binding mechanisms." This sentence is grammatically incomplete.
- **Required correction** Rewrite the sentence to be grammatically correct, e.g., "the fact that TaRGF5 homeologs cluster with AtRGF5 suggests..."

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 4.2
- **Evidence pointer** Section 4.2, sequence alignment
- **Issue** The text states "mature protein sequences were analyzed as the full-length precursors following signal-peptide cleavage" which is contradictory.
- **Required correction** Clarify whether the analysis used full-length sequences or mature sequences after signal peptide removal.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.8.1
- **Evidence pointer** Section 4.8.1, parameterization
- **Issue** The custom parameterization of sulfotyrosine is described but no validation of the parameters is provided.
- **Required correction** Provide validation of the custom parameters (e.g., comparison with quantum mechanical calculations or published parameters) or cite a source for the parameter set.

## Risk / unsupported claims
- The claim that TaRGF5 is a "putative component of root-associated signaling" is not supported by functional evidence; it is inferred from expression patterns and computational predictions.
- The claim of a "unique BES1 transcription factor binding site" in TaRGF5B is based solely on computational prediction without experimental validation.
- The predicted TaRGF5–TaRGF5–TaRGI3 interaction is based on docking and MD simulations without experimental confirmation (e.g., co-immunoprecipitation, surface plasmon resonance, or yeast two-hybrid).
- The statement that drought stress "strongly inhibits TaRGF5 transcription" is based on qRT-PCR data from a single cultivar (Sids-13) without biological replicates described in the methods.
- The claim that TaRGF5 homeologs "showed the highest similarity to Arabidopsis thaliana RGF5" is based on phylogenetic inference, but the statistical support for this specific relationship is not reported.
- The assertion that "the wheat score remains well below the threshold for non-specific interactions" is unsupported without a cited threshold or negative control docking experiments.
- The functional significance of the predicted phosphorylation sites within the mature peptide region is speculative and not experimentally tested.