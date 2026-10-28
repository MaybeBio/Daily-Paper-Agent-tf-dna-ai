## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report a combined structure-based virtual screening and molecular dynamics simulation approach to identify aryl hydrocarbon receptor (AhR) modulators from the DrugBank repository of clinically approved drugs. Ten compounds were identified as promising hits based on binding affinity, complex stability, and binding site interactions. In vitro experiments reportedly showed that nine of these compounds reduce AhR activity, while luliconazole enhances it. The authors conclude that computational modelling can serve as a rapid screening tool for predicting new AhR modulators from large drug libraries, with therapeutic potential for AhR-associated disorders.
- **Visible evidence base** Abstract text only; no methodological details, numerical results, figures, tables, or experimental protocols are provided
- **Missing materials affecting confidence** Full manuscript, computational screening parameters, molecular dynamics simulation details, scoring functions, in vitro assay protocols, dose-response data, statistical analyses, compound concentrations, cell lines used, and any validation of the screening approach against known AhR modulators

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of computational screening combined with in vitro validation for drug repurposing targeting the AhR. The concept is timely given the growing interest in AhR as a therapeutic target. However, the abstract provides insufficient methodological detail and quantitative evidence to assess the robustness of the screening pipeline, the validity of the in vitro findings, or the strength of the conclusions. The claim that ten compounds were identified and validated experimentally is not supported by the data presented in the abstract alone. The work may be of interest to the drug repurposing and AhR research communities, but the current evidence base is too limited to establish the case.
- **Who would be interested in the results, and why** Researchers in the fields of drug repurposing, computational drug discovery, and aryl hydrocarbon receptor biology would be interested. The identification of approved drugs as AhR modulators could have direct translational relevance for conditions involving AhR dysregulation, such as inflammatory diseases, cancer, and metabolic disorders. The combined computational and experimental approach may also appeal to methodologists developing virtual screening workflows.
- **Major strengths** The combination of structure-based virtual screening with molecular dynamics simulations and in vitro validation represents a rigorous multi-step approach. The focus on clinically approved drugs enhances translational relevance and repurposing potential. The identification of both agonists and an antagonist among the hits suggests the screening protocol can capture diverse modes of modulation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that "ten promising hits" were identified and that experimental studies "illuminated their modulation of AhR signaling" showing consistent reduction except for luliconazole.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract provides no quantitative data to support the identification of the ten hits or the in vitro results. No binding affinity values, simulation stability metrics, dose-response curves, or statistical significance measures are reported. The claim that the compounds "consistently reduce" AhR activity is presented without any experimental detail.
  - **Why it matters** Without quantitative evidence, the reader cannot evaluate the strength of the screening filters, the reliability of the in vitro assays, or the biological relevance of the observed effects. The core conclusion that these compounds are genuine AhR modulators is not verifiable from the abstract.
  - **Resolution test** Provide binding free energy values, simulation stability data, in vitro assay details including cell lines, compound concentrations, positive and negative controls, and statistical analysis with effect sizes and significance levels.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological transparency
  - **Claim pointer** The abstract states that the screening protocol included "binding affinities calculations, complex stability, and interactions within the binding site as a filtering method."
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** No details are given on the docking software, scoring functions, simulation length, force field parameters, or the criteria used to define "promising" hits. The threshold for what constitutes a "very low binding free energy" is not defined.
  - **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without methodological specifics, the screening pipeline cannot be replicated or compared with existing approaches, and the reliability of the hit selection cannot be assessed.
  - **Resolution test** Specify all software versions, parameters, validation steps, and selection criteria. Include a description of how the screening protocol was benchmarked against known AhR modulators.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim consistency
  - **Claim pointer** The abstract states that nine compounds reduce AhR activity while luliconazole enhances it, yet the title and framing emphasize "modulators" without specifying the direction of modulation.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The functional significance of the observed modulation is unclear. The abstract does not state whether the reduction or enhancement of AhR activity is beneficial or detrimental in a therapeutic context, nor does it address the potency or efficacy of the compounds relative to known AhR modulators.
  - **Why it matters** The therapeutic potential claim requires context. A compound that weakly reduces AhR activity may not be clinically meaningful, and the direction of modulation may be context-dependent. Without comparative data, the translational significance cannot be evaluated.
  - **Resolution test** Provide dose-response data, compare with known AhR agonists and antagonists, and discuss the therapeutic implications of the observed modulation direction in the context of specific diseases.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Title
  - **Evidence pointer** Title
  - **Issue** The title states "Identifying novel aryl hydrocarbon receptor (AhR) modulators" but the abstract reports that the compounds are clinically approved drugs. The term "novel" may be misleading since the compounds themselves are not novel, only their AhR modulatory activity is newly identified.
  - **Required correction** Consider revising the title to "Identifying clinically approved drugs as aryl hydrocarbon receptor (AhR) modulators" or similar to accurately reflect the drug repurposing context.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract results
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The abstract lists the ten compound names but provides no information on their chemical classes, structural diversity, or any structure-activity relationships that might explain the differential effects on AhR activity.
  - **Required correction** Add a brief statement on the structural features or chemical classes represented among the hits and any observed structure-activity trends.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Conclusion
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The conclusion that "computational modelling" can be used as a "quick screening tool" is not fully supported by the abstract, as the in vitro validation step is essential to the findings. The abstract does not clarify whether the computational approach alone would have been sufficient to identify the modulators.
  - **Required correction** Clarify the relative contribution of the computational and experimental components and discuss any limitations of the computational screening in isolation.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative data, methodological details, and comparative context means the central claims of hit identification and functional modulation cannot be verified from the supplied material.

## Risk / unsupported claims
- The claim that ten compounds are "promising hits" is unsupported without quantitative binding and stability data.
- The claim that the compounds "consistently reduce" AhR activity is unsupported without experimental details and statistical analysis.
- The claim that luliconazole "intriguingly enhances" AhR activity is unsupported without dose-response and specificity data.
- The claim of "immense therapeutic potential" is overstated given the lack of functional context and comparative potency data.
- The claim that computational modelling can serve as a "quick screening tool" is not fully established without benchmarking against known modulators and discussion of false positive rates.

## Assessment against Nature-style criteria
- **Originality** The application of virtual screening to approved drugs for AhR modulation is not entirely novel, as similar drug repurposing screens have been reported for other targets. The specific focus on the PAS-B binding pocket and the combination with molecular dynamics may offer some methodological novelty, but this cannot be fully assessed from the abstract.
- **Scientific importance** AhR is a relevant therapeutic target, and identifying approved drugs that modulate its activity could have translational value. However, the abstract does not demonstrate that the identified compounds have sufficient potency or selectivity to be clinically meaningful, limiting the perceived importance.
- **Interdisciplinary readership** The work bridges computational chemistry, pharmacology, and toxicology, which could attract readers from multiple disciplines. The abstract is written in a way that is broadly accessible, though the lack of methodological detail may limit engagement from specialists.
- **Technical soundness** The technical soundness cannot be evaluated from the abstract alone. The absence of methodological parameters, validation steps, and quantitative results prevents assessment of the reliability of the screening and experimental data.
- **Readability for nonspecialists** The abstract is generally readable and clearly states the approach and findings. However, terms such as "PAS-B binding pocket" and "binding free energy" may require some background knowledge, and the lack of context for the therapeutic implications reduces accessibility.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents a plausible workflow and interesting preliminary findings, but the absence of quantitative data, methodological transparency, and comparative context means the core claims cannot be verified. The manuscript may become publishable if the full text provides the necessary details and the experimental results are robust, but based on the abstract alone, the case is not made.