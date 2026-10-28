## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, structural evidence, functional validation, and model proposed in the manuscript
- **Shared manuscript claim summary** The authors report cryo-EM structures of DNA polymerase lambda (Pol λ) bound to the Ku70/80 heterodimer within the DNA-PK holoenzyme in a long-range synaptic complex. They identify a specific interaction between the Pol λ BRCT domain and a site at the Ku70/80 interface, validate this interaction through mutagenesis and two orthogonal cellular assays, and propose a unified model for how BRCT-bearing Pol X family members engage Ku70/80.
- **Visible evidence base** Cryo-EM maps and models (Figures 1, S2-S5), mutagenesis and recruitment data (Figures 2, S6), gap-filling reporter assays (Figures 4, S7), survival assays (Figure 4), structural comparisons and AlphaFold predictions (Figure 5)
- **Missing materials affecting confidence** Figure panels referenced but not fully described in text; resolution and validation statistics for cryo-EM maps not provided in text; exact numerical data for recruitment and survival assays not provided; sequence alignments and conservation analysis not shown; AlphaFold prediction details not described

## Reviewer
- **Overall assessment** This manuscript addresses a significant gap in the NHEJ field by providing the first structural description of how a Pol X family polymerase engages the core NHEJ machinery. The cryo-EM structures are potentially valuable, and the identification of a specific BRCT:Ku70/80 interface is a meaningful advance. However, the manuscript as presented has several limitations that temper enthusiasm. The structural resolution is modest (4.26-4.53 Å), and the authors themselves note that only the BRCT domain could be modelled, with no density for the catalytic domain. The functional validation is thoughtful but relies on overexpression and reporter assays that may not fully recapitulate endogenous NHEJ. The claim of a unified model for all three BRCT-bearing Pol X members is supported by AlphaFold predictions but lacks direct experimental validation for Pol μ and TdT. The manuscript would be strengthened by additional validation of the structural model, clearer presentation of quantitative data, and more direct evidence for the proposed conserved binding mode.

- **Who would be interested in the results, and why** Researchers studying DNA double-strand break repair, particularly NHEJ mechanism and regulation, will find this work of direct interest. The structural biology community focused on DNA repair complexes will value the new cryo-EM structures. Those studying Pol X family polymerases and their roles in DNA repair will be interested in the proposed conserved interaction mechanism. The work may also appeal to investigators interested in Ku70/80 as a central scaffolding hub in NHEJ.

- **Major strengths** 1) First structural characterization of a Pol X polymerase bound to the NHEJ synaptic complex, filling a notable gap in the field. 2) Identification of a specific, previously uncharacterized interaction interface between Pol λ BRCT and Ku70/80. 3) Use of two orthogonal cellular assays to validate the functional importance of the identified interface. 4) Proposal of a unified model for Pol X family engagement with Ku70/80 that generates testable hypotheses. 5) The work builds logically on prior studies and provides mechanistic insight into how end-processing enzymes are positioned within the NHEJ complex.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The authors claim that the cryo-EM structures reveal a specific interaction site between Ku70/80 and the Pol λ BRCT domain, and that this represents the molecular basis for Pol λ recruitment to the NHEJ complex.
- **Evidence pointer** Figures 1, S2-S5; resolution values stated in text (4.53 Å and 4.26 Å)
- **Concern** The overall resolution of the cryo-EM maps is modest (4.26-4.53 Å), and the authors state that only the BRCT domain could be modelled, with no density for the catalytic domain of Pol λ. At these resolutions, the confidence in the specific side-chain interactions described (e.g., Arg57, Leu60) is limited. The manuscript does not provide local resolution estimates, map-to-model correlation statistics, or validation metrics (e.g., Q-scores, B-factors) that would allow assessment of the reliability of the interaction interface. Furthermore, the authors note that when Ku70/80 alone was used with Pol λ, no density for the BRCT domain was observed, suggesting the interaction may be weak or stabilized by other components. This raises questions about whether the identified interface is the primary determinant of Pol λ recruitment in cells.
- **Why it matters** The central structural claim of the manuscript rests on the reliability of the cryo-EM density at the BRCT:Ku70/80 interface. Without robust validation metrics, readers cannot assess whether the proposed interaction is confidently determined or potentially influenced by model bias or map interpretation at limited resolution.
- **Resolution test** Provide local resolution maps, FSC curves for the focused refinement, map-to-model cross-correlation, and per-residue Q-scores or similar metrics for the BRCT:Ku70/80 interface. If possible, perform focused refinement of the BRCT region to improve local resolution. Alternatively, validate the interface using cross-linking mass spectrometry or hydrogen-deuterium exchange to confirm the interaction surface.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that mutations at the Pol λ BRCT:Ku70/80 interface impair Pol λ recruitment to DNA damage sites and reduce gap-filling activity, and that this interaction is essential for cell survival to ionizing radiation.
- **Evidence pointer** Figures 2, 3, 4, S6-S8
- **Concern** The functional data are presented qualitatively in the text without quantitative details. For the recruitment assays, the text states that mutations "impaired" or "nearly abolished" recruitment but does not provide numerical values, statistical tests, or the number of independent experiments. Similarly, the gap-filling assay results are described as showing "~70% reduction" for Pol λ KO, but the effects of specific BRCT mutations are not quantified. The survival data in Figure 4E-F are described but not presented with statistical analysis. The authors also note that some Ku70/80 mutations (e.g., Ku70 L310R, Ku80 E304A) affected PAXX recruitment, suggesting these mutations may compromise Ku:DNA stability rather than specifically disrupting the Pol λ interaction. This complicates the interpretation of the functional data.
- **Why it matters** The functional validation is essential to establish that the structurally identified interface is biologically relevant. Without quantitative data and appropriate controls, the strength of the conclusion that this specific interaction is required for Pol λ function in NHEJ is weakened. The potential confounding effects of mutations on Ku stability or DNA binding need to be addressed.
- **Resolution test** Provide quantitative data for all recruitment and gap-filling experiments, including mean values, standard deviations, number of replicates, and statistical significance. Include controls demonstrating that Ku70/80 mutants do not affect Ku expression, stability, or DNA binding. For the survival assays, provide dose-response curves with statistical analysis. Consider complementation experiments with wild-type and mutant Pol λ to demonstrate specificity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model generalizability
- **Claim pointer** The authors propose a unified model for the interaction of the three BRCT-bearing Pol X family members (Pol λ, Pol μ, TdT) with the same site on Ku70/80.
- **Evidence pointer** Figure 5B-D; AlphaFold predictions referenced in text
- **Concern** The unified model is based on AlphaFold predictions of Pol μ and TdT BRCT domains with Ku70/80, but no experimental validation is provided for these interactions. The sequence conservation analysis supporting the model is not shown. The authors do not discuss potential differences in binding affinity or specificity among the three polymerases, nor do they address whether the proposed model is consistent with known functional differences between these enzymes in NHEJ.
- **Why it matters** The unified model is a significant conceptual advance that extends beyond the direct experimental data. If the model is incorrect or oversimplified, it could mislead future studies on Pol X family function in NHEJ. Experimental validation for at least one additional family member would substantially strengthen the model.
- **Resolution test** Provide experimental evidence (e.g., co-immunoprecipitation, pull-down, or mutagenesis) demonstrating that Pol μ and/or TdT interact with Ku70/80 through the predicted interface. Show the sequence alignment and conservation analysis supporting the model. Discuss any known functional differences between Pol λ, Pol μ, and TdT that might be explained by differences in their Ku70/80 interactions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the structures reveal "a specific interaction site between Ku70/80 and the Pol λ BRCT domain" but does not mention the modest resolution or the fact that only the BRCT domain was observed, with no density for the catalytic domain. This could overstate the completeness of the structural model.
- **Required correction** Add a brief statement in the abstract noting that the catalytic domain was not observed in the density, and consider tempering the language to reflect the resolution limitations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figures 2-4
- **Evidence pointer** Figures 2, 3, 4
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to interpret the data presented. For example, it is unclear what the error bars represent in the recruitment and survival assays, and whether the data are from representative experiments or pooled analyses.
- **Required correction** Provide complete figure legends with detailed descriptions of the data presentation, including error bars, statistical tests, and the number of independent experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Cryo-EM data processing
- **Evidence pointer** Methods section, Table S1
- **Issue** The methods section describes the data collection and processing but does not provide details on the number of particles, the classification strategy, or the refinement procedures used to obtain the final maps. The resolution values are stated but not accompanied by gold-standard FSC curves or other validation metrics.
- **Required correction** Include a more detailed description of the cryo-EM data processing pipeline, including particle numbers at each stage, classification approaches, and refinement parameters. Provide FSC curves and other validation statistics in the supplementary materials.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential role of the Pol λ catalytic domain in the NHEJ complex is speculative. The authors suggest that the catalytic domain may be flexibly tethered and sample conformations to access DNA ends, but no experimental evidence is provided to support this. The discussion would benefit from a clearer distinction between what is directly supported by the data and what is speculative.
- **Required correction** Clearly label speculative statements as such and consider adding a brief section on limitations of the current study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not discuss recent structural studies of Pol μ or other Pol X family members in complex with NHEJ factors, if any exist. A more thorough comparison with the existing literature would help position this work in the field.
- **Required correction** Add a brief discussion of any relevant prior structural or biochemical studies of Pol X family interactions with NHEJ proteins, and explicitly state how the current work advances beyond these.

## Risk / unsupported claims
- The claim that the identified BRCT:Ku70/80 interface is "essential" for Pol λ recruitment and activity is not fully supported by the data, as the quantitative effects of mutations are not provided and some mutations may affect Ku stability or DNA binding.
- The unified model for all three BRCT-bearing Pol X family members is based on AlphaFold predictions without experimental validation and should be presented as a hypothesis rather than an established finding.
- The statement that the catalytic domain of Pol λ "has no stable interaction with DNA with the LRC" is based on the absence of density in the cryo-EM maps, which could reflect flexibility or weak binding rather than a true lack of interaction.
- The claim that the interaction occurs "early during the NHEJ process" is inferred from the structural data but is not directly tested experimentally.
- The suggestion that Pol λ dead exerts a dominant negative effect by occupying a common Ku70/80 site is plausible but not directly demonstrated.