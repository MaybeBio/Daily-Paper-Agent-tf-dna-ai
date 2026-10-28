## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full-text methods, figures, or statistical details
- **Shared manuscript claim summary** The abstract proposes that the plastidial metabolite MEcPP orchestrates stress-responsive transcriptional reprogramming through a dual mechanism: (1) dismantling a suppressor network comprising HAT1, TPL, and IMPalpha-9 via 26S proteasomal degradation and reduced auxin-dependent HAT1 expression, and (2) activating CAMTA3 through enhanced Ca(2+) influx, enabling RSRE binding and stress gene transcription.
- **Visible evidence base** Yeast one-hybrid assays, genetic analyses (overexpression and knockdown), interaction assays, AlphaFold modeling, and stress-condition experiments as described in the abstract
- **Missing materials affecting confidence** Full methods, experimental replicates and statistics, figure panels, construct details, plant growth conditions, stress treatment protocols, AlphaFold confidence metrics, and any validation of proteasomal degradation and Ca(2+) influx measurements

## Reviewer
- **Overall assessment** The abstract presents a mechanistically coherent model for MEcPP-mediated retrograde signaling, integrating transcriptional repression, protein degradation, and calcium-dependent activation. The proposed dual mechanism is conceptually interesting and potentially significant for the plant stress signaling field. However, the abstract alone provides insufficient detail to evaluate the robustness of the key claims, particularly the proteasomal degradation of TPL and IMPalpha-9, the reduction in auxin-dependent HAT1 expression, and the causal link between MEcPP-enhanced Ca(2+) influx and CAMTA3 activation. The genetic and interaction data are described but not quantitatively assessable from the supplied material.
- **Who would be interested in the results, and why** Plant stress biologists, particularly those studying retrograde signaling, transcriptional regulation, and the general stress response network. Researchers working on HD-Zip transcription factors, CAMTA family proteins, and calcium signaling in plants would also find the results relevant. The identification of a metabolite-driven dual mechanism linking plastid status to nuclear transcriptional output has broad implications for understanding cellular homeostasis under environmental stress.
- **Major strengths** The study addresses a fundamental question in plastid-to-nucleus communication with a clear mechanistic framework. The identification of HAT1 as a negative regulator of RSRE and the delineation of a suppressor network involving TPL and IMPalpha-9 provide a novel layer of regulatory complexity. The integration of AlphaFold modeling with experimental interaction data is a modern approach that strengthens the structural claims. The dual mechanism, combining suppressor dismantling and activator engagement, offers a compelling explanation for how a single metabolite can coordinate rapid and robust transcriptional responses.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide quantitative evidence for the proteasomal degradation claim, the reduction in HAT1 expression, or the Ca(2+) influx measurements. Without these data, the central dual mechanism cannot be fully evaluated. Additionally, the AlphaFold modeling is mentioned without confidence metrics or experimental validation of the predicted interfaces.
- **Assessment against Nature-style criteria** Originality: The proposed dual mechanism is novel in the context of MEcPP signaling and adds to the understanding of retrograde regulation. Scientific importance: The findings have potential significance for plant stress biology and could inform broader studies on metabolite-mediated transcriptional control. Interdisciplinary readership: The work bridges plant metabolism, transcriptional regulation, and calcium signaling, which may attract readers from multiple subdisciplines, though the specialized nature of the topic may limit broader appeal. Technical soundness: Cannot be fully assessed from the abstract alone; the described methods are appropriate but the data supporting key claims are not visible. Readability for nonspecialists: The abstract is dense and assumes familiarity with plant signaling terminology, which may limit accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is promising, but the abstract-level evidence is insufficient to establish the core claims. Full experimental details and quantitative data are required to validate the dual mechanism.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Under stress condition, MEcPP accumulation promotes the 26S proteasomal degradation of TPL and IMPalpha-9"
- **Evidence pointer** Abstract, stress condition experiments; location not provided
- **Concern** The abstract states that MEcPP promotes 26S proteasomal degradation of TPL and IMPalpha-9, but no experimental evidence is described to support this specific degradation pathway. The use of proteasome inhibitors, ubiquitination assays, or degradation kinetics is not mentioned.
- **Why it matters** The proteasomal degradation of the suppressor network is a central pillar of the proposed dual mechanism. Without direct evidence for 26S proteasome involvement, alternative degradation pathways or indirect effects cannot be excluded, which would weaken the mechanistic conclusion.
- **Resolution test** Provide data from proteasome inhibitor treatments, cycloheximide chase assays, and ubiquitination analyses demonstrating that MEcPP specifically enhances 26S proteasome-dependent degradation of TPL and IMPalpha-9.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "MEcPP enhances Ca(2+) influx, activating CAMTA3 and enabling it to bind RSRE"
- **Evidence pointer** Abstract, stress condition experiments; location not provided
- **Concern** The abstract claims that MEcPP enhances Ca(2+) influx, which activates CAMTA3, but no direct measurements of Ca(2+) levels or CAMTA3 activation status are described. The causal chain from MEcPP to Ca(2+) to CAMTA3 activation to RSRE binding is asserted without visible supporting data.
- **Why it matters** Calcium signaling is highly dynamic and context-dependent. Without direct evidence linking MEcPP to Ca(2+) changes and subsequent CAMTA3 activation, the proposed mechanism remains speculative and could be confounded by other stress-induced signals.
- **Resolution test** Include Ca(2+) imaging or fluorescent reporter data showing MEcPP-dependent Ca(2+) increases, and demonstrate CAMTA3 activation through phosphorylation, nuclear localization, or direct binding assays under these conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** "MEcPP reduces auxin-dependent HAT1 expression"
- **Evidence pointer** Abstract, genetic analyses; location not provided
- **Concern** The abstract states that MEcPP reduces auxin-dependent HAT1 expression, but no quantitative data on transcript or protein levels are provided. The distinction between auxin-dependent and auxin-independent effects is not clarified.
- **Why it matters** The reduction of HAT1 expression is a key component of the suppressor dismantling mechanism. Without quantitative evidence, it is unclear whether this reduction is significant, specific, or sufficient to relieve RSRE suppression.
- **Resolution test** Provide transcript and protein quantification for HAT1 under control, stress, and auxin-treated conditions, with statistical analysis demonstrating MEcPP-specific effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation
- **Claim pointer** "AlphaFold modeling provided insights into the architecture of the HAT1-RSRE complex and HAT-CAMTA3 interaction, supported by conserved domains across plant species"
- **Evidence pointer** Abstract, AlphaFold modeling; location not provided
- **Concern** AlphaFold predictions are mentioned as supporting the interaction architecture, but no confidence scores, validation experiments, or mutagenesis data are described. The abstract does not clarify whether the predicted interfaces were experimentally tested.
- **Why it matters** AlphaFold models are predictive and require experimental validation, especially for protein-DNA and protein-protein interfaces. Without such validation, the structural claims remain speculative and do not strengthen the mechanistic model.
- **Resolution test** Provide AlphaFold confidence metrics (pLDDT, PAE) and experimental validation through mutagenesis of predicted interface residues followed by interaction assays.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, first sentence
- **Issue** The term "bimodal retrograde signaling" in the title is not explicitly defined or elaborated in the abstract. The dual mechanism is described, but the "bimodal" framing is not directly connected to the presented data.
- **Required correction** Define "bimodal" in the context of the study, either in the abstract or by explicitly linking the two modes of action to the term.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental details
- **Evidence pointer** Abstract, genetic analyses and interaction assays; location not provided
- **Issue** The abstract does not specify the plant species, tissue types, or developmental stages used for the genetic and interaction assays. This limits the ability to assess the generalizability of the findings.
- **Required correction** Include species and relevant experimental context in the abstract or ensure these details are clearly stated in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Suppressor network
- **Evidence pointer** Abstract, interaction assays
- **Issue** The abstract mentions a suppressor network involving HAT1, TPL, and IMPalpha-9, but the functional relationship among these components is not fully explained. It is unclear whether they act in a linear pathway or as a complex.
- **Required correction** Clarify the hierarchical or cooperative relationship among HAT1, TPL, and IMPalpha-9 in suppressing RSRE activity.

## Risk / unsupported claims
- The claim that MEcPP promotes 26S proteasomal degradation of TPL and IMPalpha-9 is unsupported by visible evidence in the abstract.
- The claim that MEcPP enhances Ca(2+) influx leading to CAMTA3 activation is unsupported by visible evidence in the abstract.
- The claim that MEcPP reduces auxin-dependent HAT1 expression is unsupported by quantitative data in the abstract.
- The structural insights from AlphaFold modeling are not validated experimentally and should be treated as predictive rather than confirmed.
- The overall dual mechanism is presented as established, but the abstract-level evidence is insufficient to fully support this conclusion.