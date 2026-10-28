## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report isolation of 56 actinomycete strains from *Alpinia purpurata* roots, identification of strain AL024 as *Streptomyces mutabilis*, purification of actinomycin V and actinomycin D from its crude extract, cytotoxicity evaluation against three cancer cell lines and one non-cancerous cell line, molecular docking of both compounds with GpC DNA, and *in silico* ADMET predictions. They conclude that AL024 is a valuable source of these actinomycins with promising *in vitro* anticancer activity but with general cytotoxicity and predicted hepatotoxicity requiring further safety assessment.
- **Visible evidence base** Abstract text only; no experimental details, numerical data beyond IC50 ranges and yields, docking scores, ADMET parameter values, or statistical analyses are provided
- **Missing materials affecting confidence** Full methods, all figures and tables, compound characterization spectra, docking poses and scores, ADMET output values, statistical analysis details, and any supplementary information

## Reviewer

- **Overall assessment** The abstract reports a straightforward natural product discovery and characterization study. The isolation of actinomycin-producing *Streptomyces* from a plant endophyte is not novel in itself, as actinomycins are well-known metabolites from multiple *Streptomyces* species. The key claims of cytotoxicity and DNA intercalation are consistent with the established pharmacology of actinomycin D, which limits the conceptual advance. The study appears technically competent based on the abstract, but the evidence base is insufficient to evaluate rigor. The conclusion that these compounds show "promising anticancer activity" is weakened by the acknowledged general cytotoxicity against non-cancerous Vero cells, and the therapeutic window appears narrow based on the reported IC50 values. The manuscript may be of interest to a specialized audience in natural product drug discovery, but its significance for a broad readership is limited.
- **Who would be interested in the results, and why** Researchers in natural product discovery, microbial secondary metabolite chemistry, and anticancer drug development may find the isolation of actinomycin V from a new endophytic source of interest. Those working on actinomycin analogs and their DNA-binding properties may also take note of the comparative docking data. The study is unlikely to attract readers beyond these specialized groups given the well-established nature of actinomycin biology.
- **Major strengths** The study combines isolation, structural characterization, biological evaluation, and computational analysis in a single workflow. The use of multiple cancer cell lines and a non-cancerous comparator is appropriate for initial cytotoxicity screening. The inclusion of ADMET predictions provides an early safety profile that is often missing in similar natural product studies. The comparative analysis of two actinomycin analogs from the same strain adds some value.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that both compounds "were cytotoxic to cancer cells (IC50: 2.45-8.45 mug/mL) but also affected normal Vero cells (IC50: 7.43-8.46 mug/mL)" and that docking "showed both intercalate into GpC DNA, with actinomycin V exhibiting stronger binding."
  - **Evidence pointer** Results section, abstract only; location not provided
  - **Concern** The abstract provides no experimental replication information, no statistical measures of variability, no positive or negative controls for the MTT assays, and no docking scores or binding energy values. The IC50 ranges overlap substantially between cancer and normal cells, yet the abstract frames the activity as "promising." The docking claim of "stronger binding" for actinomycin V is presented without any quantitative metric.
  - **Why it matters** Without replication data, error estimates, and quantitative docking results, the reliability of the cytotoxicity and binding claims cannot be assessed. The overlapping IC50 ranges raise the question of whether any selective anticancer activity actually exists, which is central to the stated conclusion of "promising anticancer activity."
  - **Resolution test** Provide full experimental details including number of replicates, standard deviations or confidence intervals for all IC50 values, statistical comparisons between cancer and normal cell sensitivities, and docking scores (e.g., binding free energies) with appropriate error estimates for both compounds.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim-conclusion alignment
  - **Claim pointer** The conclusion states that "These compounds show promising anticancer activity *in vitro* but also exhibit general cytotoxicity and predicted hepatotoxicity."
  - **Evidence pointer** Conclusion section, abstract only; location not provided
  - **Concern** The reported IC50 values for cancer cells (2.45-8.45 mug/mL) and Vero cells (7.43-8.46 mug/mL) show substantial overlap. For several cancer cell lines, the IC50 may be higher than or comparable to that of Vero cells, indicating no selective toxicity. The term "promising" is therefore not supported by the data as presented.
  - **Why it matters** The central translational claim of the study depends on demonstrating a therapeutic window. If the compounds are equally toxic to normal and cancer cells, the anticancer potential is severely limited, and the conclusion overstates the findings.
  - **Resolution test** Present per-cell-line IC50 values with statistical comparisons between cancer and Vero cells. Calculate and report selectivity indices. If no significant selectivity exists, revise the conclusion to reflect the lack of selective cytotoxicity.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Novelty and contextualization
  - **Claim pointer** The background states that "Actinomycins, like actinomycin D, are known anticancer agents that inhibit transcription by binding to DNA" and the study aims to "isolate and characterize new actinomycete strains."
  - **Evidence pointer** Background section, abstract only; location not provided
  - **Concern** Actinomycin D is an established clinical anticancer drug, and actinomycin V is a known actinomycin analog. The abstract does not articulate what is scientifically new beyond the specific source strain. The identification of a new producing strain of a known compound class is a incremental contribution unless the compounds show unexpected properties or the strain offers a biosynthetic or production advantage.
  - **Why it matters** For a study to be significant, the novelty must be explicit. If the only new element is the endophytic source, the contribution is limited. The abstract should clarify what new biological or chemical insight is provided.
  - **Resolution test** Revise the abstract to explicitly state the novel contribution, whether it is a new analog, a new biosynthetic insight, a substantially improved production yield, or an unexpected biological property. If none applies, the significance claim should be moderated.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods description
  - **Evidence pointer** Materials and Methods section, abstract only; location not provided
  - **Issue** The abstract states compounds were "purified from AL024's crude extract using TLC" but does not specify the chromatographic system, detection method, or purity assessment. TLC alone is typically insufficient for purification to the level required for structural characterization and bioassay.
  - **Required correction** Clarify whether preparative TLC was used, specify the solvent system, and state how purity was verified (e.g., HPLC, NMR purity assessment).
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** ADMET reporting
  - **Evidence pointer** Results section, abstract only; location not provided
  - **Issue** The abstract states "ADMET predictions indicated good water solubility and Caco-2 permeability but low oral absorption and potential hepatotoxicity" without providing any quantitative values or the specific computational platforms used.
  - **Required correction** Name the ADMET prediction tools used and provide the key predicted values in the results or a table.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Compound naming
  - **Evidence pointer** Title and Results section, abstract only; location not provided
  - **Issue** The title lists "Actinomycin D and Actinomycin V" but the results section states "actinomycin V (compound 1) and actinomycin D (compound 2)." The order is inconsistent between title and results.
  - **Required correction** Standardize the order of compound presentation throughout the manuscript.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Units and precision
  - **Affected element** IC50 reporting
  - **Evidence pointer** Results section, abstract only; location not provided
  - **Issue** IC50 values are reported in mug/mL, which is acceptable for crude comparisons, but molar concentrations would be more informative for known compounds with defined molecular weights.
  - **Required correction** Report IC50 values in molar units (e.g., muM) in addition to mass units, or state molecular weights to allow conversion.
- **Technical failings that need to be addressed before the case is established** R1-M1 (evidence sufficiency for cytotoxicity and docking claims) and R1-M2 (claim-conclusion alignment regarding "promising" activity) must be resolved. Without per-cell-line data, statistical measures, and quantitative docking results, the central claims cannot be evaluated. R1-M3 on novelty must also be addressed to establish the significance of the contribution.
- **Assessment against Nature-style criteria** 
  - Originality: Limited. Actinomycin D and V are known compounds with established mechanisms. The endophytic source is a minor variation on extensive prior work on actinomycin-producing streptomycetes.
  - Scientific importance: Moderate for specialized natural product and drug discovery audiences. The findings do not challenge or extend current understanding of actinomycin biology or anticancer mechanisms.
  - Interdisciplinary readership: Low. The study sits within natural product chemistry and cancer pharmacology but does not bridge to broader biological or chemical questions that would attract readers outside these fields.
  - Technical soundness: Not assessable from the abstract. The methods are described at a summary level, and no data quality metrics are provided.
  - Readability for nonspecialists: The abstract is clearly written and accessible, with appropriate use of standard terminology. However, the significance of the findings is overstated relative to the data presented.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a competent but incremental study. The central claims of promising anticancer activity and differential DNA binding cannot be evaluated without full data. The authors should be invited to resubmit a revised version that addresses the evidence sufficiency concerns, provides quantitative docking results, and moderates or substantiates the "promising" conclusion with selectivity data.

## Risk / unsupported claims

- The claim that the compounds show "promising anticancer activity" is unsupported because the IC50 ranges for cancer and normal cells overlap substantially, and no selectivity index is provided.
- The claim that "actinomycin V exhibiting stronger binding" in docking is unsupported without quantitative binding scores or energies.
- The claim that AL024 showed "the best antibacterial activity" among 56 isolates is unverifiable without data on the other strains.
- The structural identification of the compounds as actinomycin V and actinomycin D is not verifiable from the abstract alone; full NMR and MS data are required.
- The ADMET predictions are reported qualitatively without naming the platforms or providing values, making them unverifiable.
- The statement that the compounds "intercalate into GpC DNA" is presented as a finding but is consistent with known actinomycin behavior; whether this is a new observation or a confirmation of prior knowledge is unclear.