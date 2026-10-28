## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, or supplementary materials were available for evaluation
- **Shared manuscript claim summary** The authors propose that NFkappaB temporal dynamics encode stimulus-response specificity (SRS) in macrophages exposed to multi-ligand mixtures, and that signaling pathway antagonism, particularly endosomal transport competition between TLR9 and TLR3, improves the distinguishability of individual ligands from mixtures.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or statistical details provided
- **Missing materials affecting confidence** Full manuscript, methods description, model equations, parameter values, experimental protocols, microscopy data, quantification details, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially important systems-level hypothesis regarding macrophage discrimination of ligand mixtures. The combination of mathematical modeling with live-cell validation is appropriate in principle. However, the abstract alone does not provide sufficient detail to assess the rigor of the modeling approach, the quality of experimental validation, or the robustness of the central claims. The conclusion that antagonism enhances specificity is intriguing but requires substantially more evidence than is presented here.
- **Who would be interested in the results, and why** Researchers in innate immunology, NFkappaB signaling dynamics, systems biology, and quantitative cell biology would find these results relevant. The work addresses a fundamental gap between single-ligand studies and physiological multi-ligand exposure, which is of broad interest to immunologists studying infection and inflammation. The methodological approach combining modeling and live-cell imaging may also appeal to computational biologists.
- **Major strengths** The abstract addresses a significant and understudied problem, namely how macrophages achieve stimulus specificity under complex multi-ligand conditions. The use of a heterogeneous single-cell model to generate predictions that are then validated experimentally represents a sound overall strategy. The identification of specific mechanistic antagonism, such as endosomal transport competition, provides a concrete and testable hypothesis.
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
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative evidence for the central claims. No effect sizes, statistical measures, or model fitting metrics are reported. The validation of model predictions with live-cell microscopy is mentioned but not described in sufficient detail to assess its adequacy. The claim that antagonism improves distinguishability is not supported by any presented data.
- **Assessment against Nature-style criteria**  
  - Originality: The question of multi-ligand specificity in NFkappaB signaling is relatively novel, and the focus on antagonism as a specificity-enhancing mechanism is a fresh perspective. However, the abstract does not clearly differentiate this work from prior studies on NFkappaB dynamics or ligand discrimination.  
  - Scientific importance: If substantiated, the findings could shift how the field thinks about immune specificity, moving from single-ligand responses to mixture contexts. The potential importance is high, but the abstract does not yet establish the case.  
  - Interdisciplinary readership: The topic bridges immunology and systems biology, and the use of Wasserstein distance and machine learning classification may attract quantitative readers. However, the abstract is written at a level that assumes familiarity with NFkappaB signaling and modeling, which may limit accessibility.  
  - Technical soundness: Cannot be assessed from the abstract alone. The modeling framework, parameter estimation, and experimental validation are not described in sufficient detail.  
  - Readability for nonspecialists: The abstract is concise but uses field-specific terminology without sufficient context. Terms such as "Wasserstein distance," "ultra-sensitive IKK activation," and "stimulus-cofactor CD14" are not explained for a broader audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible and interesting hypothesis, but the absence of quantitative results and methodological detail prevents any assessment of whether the claims are supported. A full manuscript with detailed methods and results would be required to evaluate the case.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims that "NFkappaB temporal coding can partially convey the presence of specific ligands within mixtures" and that "antagonism between TLR9 and TLR3 signaling pathways due to endosomal transport competition may enhance the distinguishability of CpG-pIC from ligand mixtures."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No quantitative results are presented to support these claims. The abstract does not report classification accuracies, Wasserstein distances, statistical significance, or any comparison between conditions. The phrase "may enhance" is appropriately hedged, but the preceding claim of "partially convey" is stated without supporting numbers.  
- **Why it matters** The central thesis of the manuscript depends on demonstrating that NFkappaB dynamics carry sufficient information to identify ligands in mixtures and that antagonism improves this discrimination. Without quantitative evidence, the claims remain speculative.  
- **Resolution test** Provide classification performance metrics with confidence intervals, statistical comparisons between synergy and antagonism conditions, and effect sizes for the distinguishability improvement attributed to endosomal competition.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model validation  
- **Claim pointer** The abstract states that "using a mathematical model that captures heterogeneous single-cell NFkappaB responses, we generated simulation datasets for mixtures of up to five ligands and validated key predictions with live-cell microscopy."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The nature and extent of the validation are not described. It is unclear how many predictions were tested, how many cells or replicates were used, whether the validation was qualitative or quantitative, and whether the model was refined in a way that could introduce overfitting. The phrase "iterative refinement of the model" raises concerns about potential circularity.  
- **Why it matters** The credibility of the modeling results depends on independent validation. If the model was refined until it matched the experimental data, the predictive power of the model is unclear.  
- **Resolution test** Describe the validation protocol in detail, including the number of independent predictions tested, the criteria for success, and the steps taken to avoid overfitting during iterative refinement.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic attribution  
- **Claim pointer** The abstract attributes antagonism to "a limited supply of stimulus-cofactor CD14 or endosomal transport capacity" and synergy to "ultra-sensitive IKK activation in cells with low receptor expression."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** These mechanistic claims are presented without any supporting data. It is not clear how these mechanisms were identified, whether they were directly perturbed experimentally, or whether they emerged from model simulations alone. The distinction between model inference and experimental verification is not made.  
- **Why it matters** The paper's contribution to understanding macrophage biology depends on the validity of these mechanistic explanations. If they are only model inferences, they should be labeled as such and supported by sensitivity analyses or perturbation experiments.  
- **Resolution test** Provide experimental evidence, such as knockdown or overexpression of CD14, or pharmacological inhibition of endosomal transport, showing that these manipulations alter the predicted antagonism or synergy.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The abstract concludes that "antagonism mechanisms in signaling pathways are key to maintaining immune specificity under complex conditions."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** This conclusion is broad and may overreach the specific findings. The abstract only examines up to five ligands and focuses on TLR pathways. Whether this generalizes to other ligand combinations, other cell types, or other signaling pathways is not addressed.  
- **Why it matters** The stated conclusion implies a general principle, but the evidence may only support a pathway-specific observation. Overgeneralization could mislead readers.  
- **Resolution test** Either temper the conclusion to reflect the specific pathways studied, or provide additional evidence from other ligand combinations or signaling modules to support the general claim.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Definition of SRS  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "stimulus-response specificity (SRS)" is introduced but not defined precisely. It is unclear whether SRS refers to the ability to distinguish ligands, the magnitude of response, or the temporal pattern.  
- **Required correction** Provide an explicit operational definition of SRS, including how it is quantified.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Ultra-sensitive IKK activation"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "ultra-sensitive" is used without defining the degree of sensitivity or the Hill coefficient involved. This is a technical term that requires context.  
- **Required correction** Specify the quantitative meaning of "ultra-sensitive" in this context, such as the Hill coefficient or the response curve shape.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Dose range description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "doses spanning the full responsiveness range" but does not specify the range or the number of doses tested.  
- **Required correction** Provide the dose range and the number of dose levels used in the simulations and experiments.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Use of "CpG-pIC"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abbreviation "CpG-pIC" is used without definition. It appears to refer to a mixture of CpG and poly(I:C), but this is not stated.  
- **Required correction** Define the abbreviation at first use, for example, "CpG (TLR9 agonist) and pIC (poly(I:C), TLR3 agonist)."

## Risk / unsupported claims
- The claim that "NFkappaB temporal coding can partially convey the presence of specific ligands within mixtures" is unsupported by any quantitative data in the abstract.
- The claim that "antagonism between TLR9 and TLR3 signaling pathways due to endosomal transport competition may enhance the distinguishability of CpG-pIC from ligand mixtures" is presented as a possibility but is not backed by experimental or simulation results in the abstract.
- The mechanistic attributions to CD14 limitation, endosomal transport capacity, and ultra-sensitive IKK activation are unsupported by any presented evidence.
- The general conclusion that "antagonism mechanisms in signaling pathways are key to maintaining immune specificity under complex conditions" is not supported by the abstract alone and may overgeneralize from the specific TLR9/TLR3 example.
- The validation claim ("validated key predictions with live-cell microscopy") is not assessable without details on the number of predictions, experimental design, and statistical analysis.