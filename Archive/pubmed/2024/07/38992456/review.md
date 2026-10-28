## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that ponatinib and tofacitinib are AhR ligands based on molecular docking and simulations, that ponatinib acts as an AhR antagonist in vitro, and that both compounds impair AhR-regulated CYP1A1 enzyme activity induced by potent AhR agonists. They propose these findings provide insights into therapeutic roles in AhR-associated diseases and the relationship between kinase inhibitors and AhR.
- **Visible evidence base** Molecular docking analyses, molecular dynamics simulations, binding energy calculations, and in vitro assays (as described in the abstract). Specific data values, statistical analyses, and methodological details are not provided.
- **Missing materials affecting confidence** Full methods, all numerical results, statistical parameters, experimental replicates, positive and negative controls, compound concentrations, cell lines used, and any structural validation of docking poses. Without these, the quantitative and mechanistic claims cannot be independently assessed.

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting finding that two FDA-approved kinase inhibitors may modulate AhR activity, which could have therapeutic implications. However, the evidence as summarized is insufficient to establish the core claims. The docking and simulation results are described qualitatively, and the in vitro data are presented without quantitative detail. The mechanistic distinction between antagonism and enzyme activity impairment is not clearly resolved. The work may be of interest to researchers in drug repurposing and AhR biology, but the current abstract does not provide enough evidence to support the strength of the conclusions.
- **Who would be interested in the results, and why** Researchers in drug repurposing, kinase inhibitor pharmacology, and aryl hydrocarbon receptor biology would be interested. The potential for approved drugs to modulate AhR signaling could inform new therapeutic applications and safety considerations. Clinicians and translational scientists studying chronic myeloid leukemia, rheumatoid arthritis, or AhR-associated diseases may also find relevance.
- **Major strengths** The study addresses a clinically relevant question by examining approved drugs for off-target activity on a key transcription factor. The combination of computational and experimental approaches is appropriate for initial ligand identification. The focus on a specific binding domain (PAS-B) and a regulatory loop provides a plausible structural framework for the proposed interactions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that ponatinib and tofacitinib are AhR ligands and that ponatinib functions as an AhR antagonist.
  - **Evidence pointer** Abstract sections on molecular docking, simulations, and in vitro data; specific figures and tables not provided
  - **Concern** The abstract provides no quantitative data. No binding affinities, IC50 values, dose-response curves, or statistical comparisons are reported. The statement that ponatinib is an antagonist is based on blocking TCDD and B[a]P induced signaling, but the extent of blockade, the concentrations used, and the specificity of the effect are not described.
  - **Why it matters** Without quantitative evidence, it is impossible to determine whether the observed effects are physiologically relevant or merely artifacts of high compound concentrations. The claim of antagonism requires demonstration of dose-dependent inhibition and selectivity over other pathways.
  - **Resolution test** Provide dose-response data for ponatinib and tofacitinib on AhR-mediated reporter activity, with IC50 values and comparison to known AhR antagonists. Include statistical analysis and appropriate controls.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic clarity
  - **Claim pointer** The abstract states that both tofacitinib and ponatinib cause impairment in AhR-regulated CYP1A1 enzyme activity induced by potent AhR agonists.
  - **Evidence pointer** Abstract in vitro data section; specific assays not described
  - **Concern** The relationship between AhR antagonism and CYP1A1 enzyme activity impairment is unclear. CYP1A1 activity could be reduced through transcriptional inhibition, direct enzyme inhibition, or cytotoxicity. The abstract does not distinguish between these mechanisms. If the compounds directly inhibit CYP1A1 enzyme activity, the claim of AhR antagonism is weakened.
  - **Why it matters** The central conclusion that these compounds modulate AhR depends on demonstrating that the observed effects occur at the receptor level rather than downstream enzyme inhibition. Without this distinction, the mechanistic interpretation is ambiguous.
  - **Resolution test** Include assays that separate AhR transcriptional activity (e.g., reporter gene or CYP1A1 mRNA) from CYP1A1 enzyme activity (e.g., EROD assay). Show whether the compounds affect CYP1A1 activity in the absence of AhR agonist stimulation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Computational validation
  - **Claim pointer** The abstract claims that docking and simulations show good stability and that F295 is a crucial residue for interaction.
  - **Evidence pointer** Abstract molecular modelling section; structural figures and simulation parameters not provided
  - **Concern** The computational results are described qualitatively. No binding free energy values, RMSD or RMSF data, or comparison to known ligands are provided. The claim that F295 is crucial is not supported by mutagenesis or alanine scanning data.
  - **Why it matters** Computational predictions require experimental validation to be meaningful. Without quantitative metrics or mutational confirmation, the structural claims remain speculative and do not strengthen the biological conclusions.
  - **Resolution test** Provide binding energy values with errors, simulation stability metrics, and ideally site-directed mutagenesis of F295 to confirm its role in ligand binding.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract title and text
  - **Issue** The term "modulation" is vague. The abstract later specifies antagonism for ponatinib but does not clearly define the mode of action for tofacitinib.
  - **Required correction** Specify whether tofacitinib is also an antagonist or acts through a different mechanism, and use consistent terminology throughout.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Experimental context
  - **Evidence pointer** Abstract in vitro section
  - **Issue** The cell types and assay conditions are not mentioned. AhR activity can vary significantly across cell lines.
  - **Required correction** State the cell lines used and the concentrations of compounds and agonists tested.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Clinical relevance
  - **Evidence pointer** Abstract concluding statement
  - **Issue** The claim that these findings provide "valuable insights into their therapeutic roles" is overstated given the preliminary nature of the data.
  - **Required correction** Temper the conclusion to reflect that these are initial findings requiring further validation in relevant disease models.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The lack of quantitative in vitro data and the unresolved mechanism of CYP1A1 activity impairment prevent the core claims from being established. R1-M3, while not blocking, requires additional validation to support the structural interpretations.
- **Assessment against Nature-style criteria** Originality: moderate. The finding that approved kinase inhibitors may interact with AhR is novel but not surprising given the known promiscuity of kinase inhibitors. Scientific importance: potentially relevant for drug repurposing and understanding off-target effects, but the clinical significance is not established. Interdisciplinary readership: the topic bridges pharmacology, structural biology, and toxicology, which could attract a broad audience if the evidence is robust. Technical soundness: cannot be fully assessed from the abstract; the computational methods appear standard but lack validation, and the in vitro data are not described in sufficient detail. Readability for nonspecialists: the abstract is generally clear but uses domain-specific terms without explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis but lacks the quantitative and mechanistic detail required to support the claims. The authors should provide full experimental data, clarify the mechanism of CYP1A1 impairment, and validate the computational predictions before the case can be made.

## Risk / unsupported claims

- The claim that ponatinib and tofacitinib are AhR ligands is unsupported without binding affinity data or validated experimental binding assays.
- The claim that ponatinib functions as an AhR antagonist is unsupported without dose-response data and demonstration of receptor-level specificity.
- The claim that F295 is a crucial residue for interaction is unsupported without mutagenesis or other experimental validation.
- The claim that these findings provide insights into therapeutic roles in AhR-associated diseases is speculative and not supported by the data presented.
- The clinical relevance of the observed effects cannot be assessed without information on achievable drug concentrations relative to the effective concentrations in the assays.