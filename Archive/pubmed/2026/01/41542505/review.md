## Review setup
- **Input scope** Title, author list, journal/platform, date, DOI/ID, URL, and the abstract/teaser text only. Full manuscript text, figures, tables, and supplementary materials were not provided.
- **Assessment boundary** Assessment is limited to the claims explicitly stated in the supplied title and teaser. No experimental details, methods, or results beyond the teaser are available for evaluation.
- **Shared manuscript claim summary** The manuscript claims that AlphaFold3 predictions identify novel GLI-SUFU interfaces, and that these predictions, combined with experimental validation, identify SUFU missense variants from medulloblastoma and Gorlin Syndrome patients that are binding-defective.
- **Visible evidence base** Title, author list, journal/platform, date, DOI/ID, URL, and the teaser text. No abstract, main text, figures, tables, or supplementary data were provided.
- **Missing materials affecting confidence** Full abstract, main text, all figures and tables, methods description, experimental validation data, AlphaFold3 model details, variant lists, and any statistical analyses. Without these, the core claims cannot be independently assessed.

## Reviewer
- **Overall assessment** The manuscript addresses a potentially important question in Hedgehog signaling biology, namely the molecular basis of GLI-SUFU interactions and the functional impact of disease-associated SUFU variants. The combination of AI-based structural prediction with experimental validation is timely and could be of interest to a broad audience. However, the supplied material is insufficient to evaluate the technical soundness, the validity of the predictions, or the strength of the experimental evidence. The claims as stated are plausible but currently not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in Hedgehog signaling, developmental biology, and cancer genetics would be interested. Clinically oriented geneticists studying medulloblastoma or Gorlin Syndrome may also find the variant-level functional annotations useful. The methodological angle, using AlphaFold3 for interface prediction, could attract computational structural biologists.
- **Major strengths** The topic is of clear biological and clinical relevance. The use of AlphaFold3 to predict novel interfaces is a modern and potentially powerful approach. The inclusion of patient-derived variants adds translational significance. The teaser promises experimental validation, which is essential for credibility.
- **Major Concerns** None can be fully articulated because the evidence base is limited to a teaser. However, the following concerns are raised based on what is visible.
- **Minor Comments** None can be fully articulated because the evidence base is limited to a teaser. However, the following comments are raised based on what is visible.
- **Technical failings that need to be addressed before the case is established** The absence of any methodological detail, experimental data, or model validation means that the core claims are unverifiable from the supplied material. Specific technical failings cannot be identified without the full manuscript.
- **Assessment against Nature-style criteria** Originality cannot be assessed without knowing whether these interfaces or variants have been previously reported. Scientific importance is potentially high given the disease relevance, but this is not yet demonstrated. Interdisciplinary readership is plausible, but the teaser does not provide enough detail to judge accessibility. Technical soundness is unassessable. Readability for nonspecialists cannot be evaluated from the teaser alone.
- **Recommendation posture** Currently not established from the provided evidence. A supportive posture would require the full manuscript to be made available for review.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that AlphaFold3 predictions identify novel GLI-SUFU interfaces and that these are experimentally validated.
- **Evidence pointer** Teaser only. Location not provided.
- **Concern** The teaser states that AI-powered modeling plus experimental validation reveal new interfaces, but no experimental data, model confidence metrics, or validation protocols are shown. Without the full text, it is impossible to verify that the predicted interfaces are novel, that the experimental validation is robust, or that the variants are indeed binding-defective.
- **Why it matters** The central claim of the manuscript rests on the combination of prediction and validation. If the experimental evidence is weak or the predictions are not properly benchmarked, the conclusions may be overstated. The novelty claim also requires a literature comparison that is not visible.
- **Resolution test** Provide the full manuscript with methods, results, and supplementary data. Specifically, show AlphaFold3 confidence scores, experimental binding assays, and a comparison with known GLI-SUFU structures or prior predictions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Variant interpretation
- **Claim pointer** The manuscript claims that SUFU missense variants from medulloblastoma and Gorlin Syndrome patients are binding-defective.
- **Evidence pointer** Teaser only. Location not provided.
- **Concern** The teaser implies a direct link between patient-derived variants and binding defects, but no variant list, functional assay data, or statistical significance is provided. It is unclear how many variants were tested, whether controls were included, or whether the binding defects correlate with clinical severity.
- **Why it matters** The clinical relevance of the findings depends on the strength of the variant functional data. Without clear evidence, the claim that these variants are binding-defective may be premature or overgeneralized.
- **Resolution test** Include a table of variants with their source, predicted impact, and experimental binding results. Provide statistical analysis comparing variant effects to wild-type and to benign controls.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The manuscript relies on AlphaFold3 predictions as a central tool.
- **Evidence pointer** Teaser only. Location not provided.
- **Concern** AlphaFold3 is a powerful tool, but its predictions for protein-protein interfaces, especially for novel or dynamic interactions, require careful validation. The teaser does not indicate whether the predictions were cross-validated with experimental structures, mutagenesis, or other computational methods.
- **Why it matters** If the predicted interfaces are not robust, the downstream variant interpretation may be built on a weak foundation. The novelty claim also depends on the reliability of the model.
- **Resolution test** Provide model confidence metrics, such as ipTM and pLDDT scores, and show that the predicted interfaces are stable across multiple runs or are supported by independent experimental evidence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Teaser wording
- **Evidence pointer** Teaser
- **Issue** The phrase "AI-powered modeling plus experimental validation" is vague. It is unclear what specific experimental methods were used.
- **Required correction** Specify the experimental techniques, such as co-immunoprecipitation, surface plasmon resonance, or cellular assays, in the abstract or teaser.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scope
- **Affected element** Variant selection
- **Evidence pointer** Teaser
- **Issue** The teaser mentions medulloblastoma and Gorlin Syndrome, but it is unclear whether the variants are germline or somatic, and whether they are all missense.
- **Required correction** Clarify the variant types and their inheritance patterns in the abstract.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Teaser
- **Evidence pointer** Teaser
- **Issue** The teaser assumes familiarity with GLI-SUFU biology. A brief context sentence would help nonspecialist readers.
- **Required correction** Add one sentence explaining the role of GLI-SUFU in Hedgehog signaling and its relevance to disease.

## Risk / unsupported claims
- The claim that AlphaFold3 predictions identify novel GLI-SUFU interfaces is unsupported because no model details or comparison to existing structures are provided.
- The claim that patient-derived SUFU variants are binding-defective is unsupported because no experimental data or variant list is provided.
- The claim that experimental validation was performed is unverifiable from the supplied material.
- The overall novelty of the findings cannot be assessed without a literature comparison.