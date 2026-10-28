## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use structure-based computational approaches to characterize 1132 p53 DNA binding domain (DBD) variants, focusing on those with predicted marginal effects on stability, to identify variants that may affect the 207-213 loop locally or allosterically, with potential consequences for cytosolic p53 functions. They validate predictions for 15 variants using enhanced sampling methods and propose the methodology as broadly applicable.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or validation data are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary information, methodological protocols, simulation parameters, validation data, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting computational study addressing an important question in p53 biology, namely how cancer-associated variants with minimal stability effects may influence protein-protein interactions through local or allosteric modulation of a functional loop. However, the abstract provides insufficient detail to evaluate the technical soundness, the robustness of the predictions, or the strength of the validation. The claim of broad methodological applicability is not supported by the evidence presented. The work may be of interest to computational biologists and p53 researchers, but the current abstract does not establish the case convincingly.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists studying allostery and protein dynamics would be interested in the methodological framework. Cancer geneticists and p53 researchers would be interested in the identification of specific variants with potential functional consequences beyond stability. Clinicians interpreting p53 variants in germline or somatic settings might also find the predictions relevant, though clinical utility is not demonstrated.
- **Major strengths** The study addresses a relevant and under-explored aspect of p53 variant biology, namely variants with marginal stability effects that may act through local or long-range conformational modulation. The combination of multiple computational approaches, including coarse-grain allostery models and all-atom molecular dynamics, is reasonable. The inclusion of enhanced sampling validation for a subset of variants is a positive feature.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative results, such as the number of variants identified as having local or long-range effects, the criteria for "marginal effects on structural stability," or the outcomes of the enhanced sampling validation. Without these, the central claims cannot be assessed. The validation for 15 variants is mentioned but no details are given on selection criteria, methods, or results.
- **Assessment against Nature-style criteria** 
  - Originality: The question of local and allosteric effects of p53 variants on a functional loop is not entirely new, but the systematic computational screening of 1132 variants with a focus on stability-neutral variants has some originality. However, the abstract does not clearly differentiate this work from prior computational studies on p53 variants.
  - Scientific importance: The topic is important for understanding p53 variant function, but the abstract does not demonstrate that the findings have broad biological or clinical significance beyond a computational prediction exercise.
  - Interdisciplinary readership: The work may appeal to computational biologists and p53 researchers, but the abstract is written in a way that is accessible to specialists only. The broader significance for cancer biology or clinical genetics is not articulated.
  - Technical soundness: Cannot be evaluated from the abstract. The methods are named but not described in sufficient detail to assess their appropriateness or rigor.
  - Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with p53 structure, DBD, and computational methods. It does not provide sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful computational study, but the lack of quantitative results and methodological detail prevents a supportive recommendation. A revised abstract with concrete findings and validation outcomes could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim to have characterized 1132 variants and identified those with local or long-range effects on the 207-213 region, with validation using enhanced sampling for 15 variants.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no quantitative results. It is unclear how many variants were classified as having marginal stability effects, how many were predicted to act locally or allosterically, and what the outcomes of the enhanced sampling validation were. Without these numbers, the central claims are unverifiable.
- **Why it matters** The core contribution of the study is the identification of specific variants with functional potential. Without reporting the scale and outcomes of the predictions, the reader cannot judge the significance or reliability of the findings.
- **Resolution test** Provide in the abstract the number of variants in each category, the criteria used for classification, and the results of the enhanced sampling validation, including how many of the 15 variants confirmed the predictions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that they used structure-based approaches, a coarse-grain model for allostery, and all-atom molecular dynamics simulations, with validation by enhanced sampling.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the specific methods, parameters, or thresholds used. For example, what defines "marginal effects on structural stability," how the coarse-grain allostery model was parameterized, and what enhanced sampling technique was employed are not stated. This prevents assessment of technical soundness.
- **Why it matters** Computational predictions are highly dependent on methodological choices. Without transparency, the results cannot be reproduced or critically evaluated, and the risk of overinterpretation is high.
- **Resolution test** Include a brief but specific description of the methods and criteria in the abstract, or refer to a methods section with sufficient detail for evaluation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that the methodologies could be broadly applied to other p53 variants or other disease-related proteins with functional loops.
- **Evidence pointer** Abstract, location not provided
- **Concern** This generalizability claim is made without any demonstration of applicability beyond the specific p53 DBD system. No evidence is provided that the approach works on other proteins or that the findings have been experimentally validated.
- **Why it matters** Overstating the scope of the methodology without evidence undermines the credibility of the work and may mislead readers about its utility.
- **Resolution test** Either temper the claim to reflect the specific system studied, or provide evidence of application to at least one additional system or experimental validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Background statement
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that p53 is involved in "transcription-dependent and independent processes" but does not clarify the relevance of the 207-213 loop to these processes beyond mentioning interactor recruitment.
- **Required correction** Briefly specify the functional role of the 207-213 loop in cytosolic p53 functions to strengthen the rationale.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Marginal effects on structural stability"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "marginal" is vague and could be interpreted differently by readers.
- **Required correction** Define the quantitative threshold used to classify variants as having marginal stability effects.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Validation description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions validation with enhanced sampling for 15 variants but does not state whether these were selected randomly, representatively, or based on specific criteria.
- **Required correction** State the selection criteria for the 15 variants and the nature of the validation results.

## Risk / unsupported claims

- The claim that specific variants have local or long-range effects on the 207-213 region is unsupported because no quantitative results are provided.
- The claim that the methodologies are broadly applicable to other p53 variants or other proteins is unsupported by any evidence in the abstract.
- The claim that the study accounts for "protein dynamics" is not substantiated with any details on how dynamics were incorporated.
- The biological relevance of the findings for cytosolic p53 functions is asserted but not demonstrated with any functional data or experimental context.