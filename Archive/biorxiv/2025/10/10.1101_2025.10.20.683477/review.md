## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, data availability, methods)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency as presented in the supplied text
- **Shared manuscript claim summary** The authors use computational models to argue that mutational robustness of prokaryotic σ70 promoters correlates positively with promoter strength, and that specific architectural features (spacer length, overlapping boxes, nucleotide identity) influence robustness independently of strength
- **Visible evidence base** Figures 1-4 (referenced but not shown), supplementary figures S1-S6 (referenced but not shown), statistical tests reported in text, methods descriptions
- **Missing materials affecting confidence** Figures and supplementary materials not provided; full methods details for the thermodynamic model not included; raw data not accessible in the provided text

## Reviewer
- **Overall assessment** The manuscript presents a computationally driven analysis of promoter mutational robustness with a clear central claim. The core correlation between strength and robustness is plausible and supported by two independent models. However, the absence of figures and supplementary materials limits verification of the statistical analyses and the biological interpretation. The discussion of selection is speculative but appropriately framed. The work is likely of interest to evolutionary biologists and synthetic biologists, though the novelty relative to existing promoter robustness literature needs clearer articulation.
- **Who would be interested in the results, and why** Evolutionary biologists studying mutational robustness and its role in molecular evolution; synthetic biologists designing promoters for predictable expression; microbiologists interested in transcriptional regulation and promoter architecture diversity.
- **Major strengths** The use of two complementary computational models (PWM and thermodynamic) strengthens the central claim. The analysis of promoter architecture diversity (Fig 2) addresses a gap in the literature. The normalization of robustness to strength (Fig 3) is a thoughtful approach to isolate robustness effects independent of strength. The discussion of selection on robustness is well-reasoned and appropriately cautious.
- **Major Concerns** 
  - R1-M1: The central claim relies on computational predictions without experimental validation. The authors acknowledge PWM limitations but do not address whether the thermodynamic model has been experimentally benchmarked for the specific claim of robustness.
  - R1-M2: The selection of 206 promoters from 1,997 based on a model threshold of 0.5 a.u. introduces potential selection bias. The enrichment of "strong" evidence promoters in the subset (Fischer's exact test, p=0.044) suggests the subset may not be representative.
  - R1-M3: The claim that overlapping -10/-35 boxes increase robustness is based on a small number of cases and the mechanism (two distinct binding sites) is inferred, not directly tested.
  - R1-M4: The discussion of direct selection on robustness relies on a population genetics calculation (N_e × µ × L = 21.6) that assumes parameters for E. coli, but the authors do not consider whether the relevant mutational target is truly only 12 bp or whether flanking sequences matter.
- **Minor Comments** 
  - R1-m1: The abstract states "computational modelling" but does not specify the two-model approach; consider mentioning both models for clarity.
  - R1-m2: The term "promoter proportion" is introduced without a formal definition in the main text; the definition appears only in the methods.
  - R1-m3: The statement "To our knowledge, we are not aware of this 'compensation' being described elsewhere in the literature" is awkwardly phrased; consider simplifying.
  - R1-m4: The discussion of overlapping boxes (Fig 4A) would benefit from a clearer explanation of why -10/10 and -10/35 pairs were not found.
  - R1-m5: The authors mention "Data S1, S2, S3" but do not describe the format or content of these files in the data availability section.
- **Technical failings that need to be addressed before the case is established** R1-M1 (experimental validation), R1-M2 (selection bias), R1-M3 (mechanistic inference)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The correlation between strength and robustness has been suggested for other regulatory elements, but the systematic analysis of promoter architecture features is a contribution.
  - Scientific importance: Moderate. The findings have implications for understanding promoter evolution and for synthetic biology, but the computational-only approach limits immediate impact.
  - Interdisciplinary readership: Moderate. The work bridges evolutionary biology and synthetic biology, but the technical nature may limit broader appeal.
  - Technical soundness: The statistical methods are appropriate, but the reliance on computational models without experimental validation weakens the case.
  - Readability for nonspecialists: The abstract and introduction are accessible, but the results section assumes familiarity with PWM and thermodynamic modeling.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for experimental validation and clarification of the selection criteria for the 206 promoters.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "We used computational modelling to show that the mutational robustness of σ70 promoters – the persistence of promoter strength upon mutation – correlates with promoter strength itself."
- **Evidence pointer** Results section, Figure 1
- **Concern** The central claim is based entirely on computational predictions. While the authors use two models, neither is experimentally validated for the specific claim of mutational robustness. The authors acknowledge PWM limitations but do not provide evidence that the thermodynamic model accurately predicts mutational effects on promoter strength in vivo.
- **Why it matters** Without experimental validation, the claim that stronger promoters are more mutationally robust remains a computational prediction, not an established biological property. This limits the confidence in downstream conclusions about selection and evolution.
- **Resolution test** Provide experimental data (e.g., saturation mutagenesis of a subset of promoters with measured expression) that confirms the predicted correlation between strength and robustness.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Selection bias
- **Claim pointer** "We then created in-silico saturation mutagenesis libraries for each promoter sequence... we calculated for each promoter and its respective single point mutants, the proportion of point mutants with promoter scores greater than 0.5 a.u., which we refer to as the promoter proportion."
- **Evidence pointer** Results section, Methods section "Statistical thermodynamic model and the 206 genomic promoters"
- **Concern** The 206 promoters were selected from 1,997 based on a model threshold of 0.5 a.u. The subset is enriched for "strong" evidence promoters (Fischer's exact test, p=0.044). This selection bias may affect the generalizability of the findings, as the analysis is restricted to promoters that the model predicts to be functional.
- **Why it matters** If the subset is not representative of the full promoter population, the conclusions about robustness and architecture may not generalize. The enrichment of "strong" evidence promoters suggests the subset may be biased toward well-characterized, potentially atypical promoters.
- **Resolution test** Repeat the analysis on the full set of 1,997 promoters, or provide a sensitivity analysis showing that the conclusions hold across different thresholds and evidence categories.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic inference
- **Claim pointer** "The most likely explanation for these results is that such promoters comprise two distinct σ70 binding sites, while those with overlapping -10/10 or -35/35 boxes comprise only single σ70 binding sites."
- **Evidence pointer** Results section, Figure 3G
- **Concern** The interpretation that overlapping -10/-35 boxes represent two distinct binding sites is inferred, not directly tested. The authors do not provide evidence that both boxes are functional or that the increased robustness is due to redundancy rather than other sequence features.
- **Why it matters** If the mechanism is incorrect, the conclusion that overlapping boxes increase robustness may be misleading. The distinction between two functional binding sites and a single site with overlapping sequence features has implications for understanding promoter architecture.
- **Resolution test** Provide direct evidence (e.g., mutational analysis that disrupts one box while preserving the other) that both boxes contribute to robustness independently.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Parameter sensitivity
- **Claim pointer** "Population genetics predicts that this occurs when N e ×µ×L>>1, where N e is the effective population size, µ is the per nucleotide mutation rate, and L is the length of the mutational target."
- **Evidence pointer** Discussion section
- **Concern** The calculation of N_e × µ × L = 21.6 assumes specific values for E. coli and a mutational target of 12 bp. The authors do not consider whether flanking sequences or other regulatory elements contribute to the mutational target, nor do they discuss the sensitivity of the conclusion to parameter uncertainty.
- **Why it matters** The argument for direct selection on robustness depends on this calculation. If the mutational target is larger or the parameters are different, the conclusion may not hold.
- **Resolution test** Provide a sensitivity analysis showing how the conclusion changes with different parameter values, or discuss the robustness of the conclusion to parameter uncertainty.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "computational modelling" without specifying the two-model approach. This undersells the methodological strength of the work.
- **Required correction** Mention both the PWM and thermodynamic models in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Definition
- **Affected element** Results section
- **Evidence pointer** Results section, "Mutational robustness positively correlates with predicted promoter strength"
- **Issue** The term "promoter proportion" is used without a formal definition in the main text. The definition appears only in the methods.
- **Required correction** Define "promoter proportion" when first used in the results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Language
- **Affected element** Results section
- **Evidence pointer** Results section, "Mapping promoter architectures"
- **Issue** The phrase "To our knowledge, we are not aware of this 'compensation' being described elsewhere in the literature" is awkwardly worded.
- **Required correction** Simplify to "We are not aware of this 'compensation' being described elsewhere."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results section, "Promoters with overlapping -10 and -35 boxes are more mutationally robust"
- **Issue** The authors report no overlapping pairs for -10/10 and -10/35 boxes but do not explain why this might be the case.
- **Required correction** Add a brief explanation for the absence of these pairs, or note that this is an observation without a clear explanation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability section lists Data S1, S2, and S3 but does not describe their format or content beyond brief mentions in the text.
- **Required correction** Provide a brief description of each data file in the data availability section.

## Risk / unsupported claims
- The claim that "stronger promoters are more mutationally robust" is supported only by computational models and lacks experimental validation.
- The claim that overlapping -10/-35 boxes represent two distinct binding sites is inferred, not directly tested.
- The argument for direct selection on robustness relies on a population genetics calculation with assumed parameters that are not subjected to sensitivity analysis.
- The claim that "promoter robustness may be a selected trait" is speculative and not directly supported by the data presented.
- The statement that "the overrepresentation of 17 bp spacers... may reflect the fact that 17 bp promoters are more robust" is presented as a possible explanation but the authors acknowledge it could be a model bias; this caveat is appropriate but the claim remains unverified.